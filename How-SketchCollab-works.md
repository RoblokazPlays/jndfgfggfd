# How does SketchCollab work?

This is an FAQ, because I don't know how I'm going to explain everything in one text :P

_(If you asked something in the issues page, I'll add that question and the answer here)_

---

**How does SketchCollab know which projects are SketchCollab projects?**

<details>
 <summary>View question...</summary>
 
 Project IDs can change over time, making you change the reference to the project manually. But, SketchCollab's approach is different. With our approach, it doesn't matter if the ID gets changed or if the project is removed. SketchCollab stores project keys and project information inside `mysc/list/{project_id}/project`. If the project ID is modified, these keys stay the same. When you upload a SketchCollab project, these keys will still be there unless you remove them.

Here is the [code snippet](https://github.com/Iyxan23/sk-collab/blob/main/app/src/main/java/com/iyxan23/sketch/collab/online/UploadActivity.java#L134-L147) applying those custom keys.
</details>

---

**What are the keys, and what do they do?**

<details>
 <summary>View question...</summary>
 
 **These are the keys used in SketchCollab:**
 - `sk-collab-key` - This key stores your project key. For example, if a project was uploaded to SketchCollab with the key "ybgqwfNUkygfA", then that will be the project key. This is used to access and compare the project from the database with the local project.
 
 - `sk-collab-owner` - This key stores the author of the project. This is used so we check who owns the project. We store the **real and trusted** author key in our database, so you wouldn't be able to create commits if you modified the owner key on your device.
 
 - `sk-collab-latest-commit` - This key stores the ID of the latest commit. This is used so we know if the project has been updated. For example, if a project is at commit number (not the ID) 3, and the server says that the project it at commit number 4, then we know that the local project is outdated and needs to be synced with the server.
 
 - `sk-collab-project-visibility` - This key stores the visibility of the project, which can be public or private. We need this key because public projects are stored in the `/projects` collection, while private projects are stored in the `userdata/{uid}/projects` collection. Note that this key has nothing to do with the project's visibility. If you manually changed this key, SketchCollab would only fail to locate the project. 
 
</details>
