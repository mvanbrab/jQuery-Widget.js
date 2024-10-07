# First of all
This is branch **hardcoded-baseurl** of a fork of <https://github.com/comunica/jQuery-Widget.js>.

The purpose is to provide a Docker image to run at a baseURL different from the default baseURL (`https://query.linkeddatafragments.org/`).
It is needed until [this issue](https://github.com/comunica/jQuery-Widget.js/issues/152) is solved.

## Procedure to make a new Docker image

To change the hardcoded baseURL, modify the value of the `-b` parameter in this line in [package.json](package.json).
```
    "build": "node ./bin/generate.js -b <base-url>",
```

Actual values for `<base-url>`, extend as new ones are added:

| `<base-url>`                                   | slug used in labels and tags                |
|------------------------------------------------|---------------------------------------------|
| `https://webclient/`                           | `https-webclient`                           |
| `https://webclient.onto-deside.ilabt.imec.be/` | `https-webclient-onto-deside-ilabt-imec-be` |
| `http://localhost:8080/`                       | `http-localhost-8080`                       |
| `https://sharcs.ilabt.imec.be/webclient/`      | `https-sharcs-ilabt-imec-be-webclient`      |
| `https://onto-deside.ilabt.imec.be/webclient/` | `https-onto-deside-ilabt-imec-be-webclient` |

To create the Docker image with a self-explaining label and push it to Docker hub:
```bash
# choose one, extend as new ones are added:
#docker build -t mvanbrab/jquery-widget.js:v0.0.2.https-webclient .
#docker build -t mvanbrab/jquery-widget.js:v0.0.2.https-webclient-onto-deside-ilabt-imec-be .
#docker build -t mvanbrab/jquery-widget.js:v0.0.2.http-localhost-8080 .
#docker build -t mvanbrab/jquery-widget.js:v0.0.2.https-sharcs-ilabt-imec-be-webclient .
#docker build -t mvanbrab/jquery-widget.js:v0.0.2.https-onto-deside-ilabt-imec-be-webclient .
docker login
# choose one, extend as new ones are added:
#docker push mvanbrab/jquery-widget.js:v0.0.2.https-webclient
#docker push mvanbrab/jquery-widget.js:v0.0.2.https-webclient-onto-deside-ilabt-imec-be
#docker push mvanbrab/jquery-widget.js:v0.0.2.http-localhost-8080
#docker push mvanbrab/jquery-widget.js:v0.0.2.https-sharcs-ilabt-imec-be-webclient
#docker push mvanbrab/jquery-widget.js:v0.0.2.https-onto-deside-ilabt-imec-be-webclient
```

To commit and tag everything nicely in the repository:
```bash
git add .
# choose one, extend as new ones are added:
#git commit --no-verify -m "hardcoded baseURL to https://webclient/"
#git commit --no-verify -m "hardcoded baseURL to https://webclient.onto-deside.ilabt.imec.be/"
#git commit --no-verify -m "hardcoded baseURL to http://localhost:8080/"
#git commit --no-verify -m "hardcoded baseURL to https://sharcs.ilabt.imec.be/webclient/"
#git commit --no-verify -m "hardcoded baseURL to https://onto-deside.ilabt.imec.be/webclient/"
git push
# choose one, extend as new ones are added:
#git tag -a v0.0.2.https-webclient -m "baseURL=https://webclient/"
#git tag -a v0.0.2.https-webclient-onto-deside-ilabt-imec-be -m "baseURL=https://webclient.onto-deside.ilabt.imec.be/"
#git tag -a v0.0.2.http-localhost-8080 -m "baseURL=http://localhost:8080/"
#git tag -a v0.0.2.https-sharcs-ilabt-imec-be-webclient -m "baseURL=https://sharcs.ilabt.imec.be/webclient/"
#git tag -a v0.0.2.https-onto-deside-ilabt-imec-be-webclient -m "baseURL=https://onto-deside.ilabt.imec.be/webclient/"
git push --tags
```

### Usage

Refer to the appropriate Docker image `mvanbrab/jquery-widget.js:v0.0.2.<base-url-slug>`.

