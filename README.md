# Overview

This is an implementation of TencentARC
[GFPGAN](https://github.com/TencentARC/GFPGAN). GFPGAN aims at developing a Practical Algorithm for Real-world Face
Restoration. It leverages rich and diverse priors encapsulated in a pretrained face GAN (e.g., StyleGAN2) for
"blind face" restoration.

# Deploying to Baseten

To deploy this Truss on Baseten, first install the Baseten client:

```
$ pip install baseten
```

Then, in a Python shell, you can do the following to have an instance of GFP-GAN deployed
on Baseten:

```python
import baseten
import truss

gfp_gan_handle = truss.load(".")
baseten.deploy(gfp_gan_handle, model_name="GFP-GAN")
```

# Usage

## Inputs
The input should be a dictionary with the following key:
* `image` - the image to be restored, encoded as base64.


## Outputs

The model returns a dictionary containing the base64-encoded restored image:
* `status` - either `success` or `failed`
* `data` - the restored image, encoded as base64
* `message` - will contain details in the case of errors


## Example

You can invoke this model on Baseten with the following cURL command (just fill in the model version ID and API Key):

```
$ curl -X POST https://app.staging.baseten.co/models/gPGD1q4/predict \
    -H 'Authorization: Api-Key BnOM5lyd.KARi5zrp0t58R9EzGdY8D45j9Se9WW8u' \
    -d '{"image": "{BASE_64_INPUT}"}'
{"model_id": "gPGD1q4", "model_version_id": "7qkj8lw", "model_output": {"status": "success", "data": "{BASE_64_OUTPUT}", "message": null}}
```