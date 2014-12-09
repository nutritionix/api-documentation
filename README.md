api-documentation
=================

Nutritionix API Documentation

#### Publishing Changes to Gist


Install `gist-up` also requires `pip` or `easy_install`.
```
# may require sudo depending on your setup
pip install gist-up
```

Once you've made changes to the documentation you need to use `gistup publish` command in the directory of the docs you want to publish.

Ex. `./v2/` should contain a `.gistup.yml` file which will tell it where to push the documentation to.

It will prompt you to login using a personal access token.
![login](http://take.ms/FR8HZ)


Nutritionix staff already have a personal access token for the account that holds the documentation. Please ask an admin about the `gistup` personal access token for the docs.

If for some reason another one needs to be generated.
![generate personal access token](http://take.ms/R4DR2)


If you created new documents before you published you can run `gistup scripts` to get html script tags for the files you created to embed them.