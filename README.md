Nutritionix API Documentation
=============================

#### Publishing Changes to Gist

Install `gist-up` also requires `pip` or `easy_install`.
```
# may require sudo depending on your setup
pip install gist-up
```

Once you've made changes to the documentation you need to use the `gistup publish` command in the directory of the docs you want to publish.

Ex. cd into `./v2/` and it should contain a `.gistup.yml` file which will tell `gistup` where to push the documentation to.

It will prompt you to login using a personal access token if its your first time attempting to upload.
![login](http://take.ms/FR8HZ)


Nutritionix staff should already have a personal access token for the account that holds the documentation. Please ask an admin about the `gistup` personal access token to publish changes.

If for some reason the token is lost you can generate a new one here.
![generate personal access token](http://take.ms/R4DR2)


#### Embeding Gists

You can get a list of html script tags by running `gistup scripts` in the directory of the documentation you want to embed.