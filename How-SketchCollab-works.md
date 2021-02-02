# How does SketchCollab works?

Let's use FAQs because I don't really know how to explain everything in one text :P

_(If you asked something in the issues page, I'll add that question and the answer here)_

**How can a project is marked as a SketchCollab project? If you used a local space (e.g. SharedPreferences) to store project IDs, what happened if one of the project is gone? What happened if the project is moved into another ID?**

This is one of the problem with making SketchCollab, Project IDs can change overtime, making the user need to painstakingly change the reference to the project manually. But, SketchCollab's approach is different. This approach is resistant of ID change and project removal, So, SketchCollab stores it's project key and informations regarding about the project inside `mysc/list/{project_id}/project`, If the project ID is changed, these keys remain unchanged, when you send a SketchCollab project, these keys will still remain, (well except if you removed it :l).

**What are the keys, and what do they do?**

Here are the keys (yes, you can check it out right now on your project):
 - `sk-collab-project-key` - This key stores the project key of that project. For example, if this project is uploaded to SketchCollab with the key "ybgqwfNUkygfA", then the project key will be that key. This is used to access and compare the project from the database with the local project.
 - `sk-collab-author` - This key stores the author of the project itself, This is used so we can check the project is owned by who. Well, at first you might think that the user can just edit the author, yes, we know, But it's not going to be a big of a difference. The **real and trusted** author key is stored in the database. If they changed the author key to be their own UID, they still can't edit the project (create commits) as we checks if the key is the same as the project author in the database, not if the key is the same as the current user uid.
