DJango Admin Site
=================

Our next step is to explore the LocalLibrary administration web site that
allows us to create, read, update, and delete data in our database.

https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Admin_site

If you are submitting this assignment to the DJ4E autograder for this assignment,
it would be a good idea to check the autograder for specific instructions that
the autograder requires for this assignment.

Complete the following sections of the Admin tutorial:

* Edit `~/django_projects/locallibrary/catalog/admin.py` and register the four models
* Create a superuser (The autograder will ask you to make a second superuser)
* Reload your application under the `Web` tab in
<a href="https://www.pythonanywhere.com" target="_blank">PythonAnywhere</a>
* Log in to the admin site.  Insead of using http://localhost:8000/admin, simply add `/admin` to the end of 
your PythonAnywhere site (i.e. like 
<a href="http://mdntutorial.pythonanywhere.com/admin" target="_blank">http://mdntutorial.pythonanywhere.com/admin</a>.
* Create some books (The autograder will ask you to create one specific book and author)
* Continue into the Advanced Configuration
* Register a Model Admin class
* Configure the list views - Note that you need to edit `~/django_projects/locallibrary/catalog/models.py` at one point
* Add the list filter
* Organize the detail view layout
* Enable inline editing of associated records

Remember that every time the MDN tutorial tells you to run the server after
making a configuration change:

    python3 manage.py runserver

You need to go into 
<a href="https://www.pythonanywhere.com" target="_blank">PythonAnywhere</a>
under the `Web` tab and `Reload` the web server to re-read your updated configuration.  There is 
not harm in reloading your web application too often.

If you want to wipe out your database and start over, do the following:

    cd ~/django_projects/locallibrary
    rm db.sqlite3
    python3 manage.py migrate

Also reload your application on PythonAnywhere.

This will wipe out all of your tables and the data in those tables and create fresh and empty tables.

If you are using git
--------------------

If you are using `git`, you can see what files have been modified / created:

    git status

The git output would be as follows:

    modified:   catalog/models.py===============
    Untracked files:
        catalog/migrations/0001_initial.py   

If You Are Keeping Your Projects GitHub
---------------------------------------

At this point, once your models are working, you might want to check it into
github and tag it.

    cd ~/django_projects/locallibrary
    git status
    git add catalog/migrations/* =================
    git commit -a -m "Admin tutorial complete"
    git push

You might also want to tag this version of the code in case you need to come back to it:

    git tag admin
    git push origin --tags
