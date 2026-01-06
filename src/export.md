# Jupyter Notebook Export Tutorial

For many assignments in this class, you will need to export a Jupyter Notebook
for submission to Gradescope. Here is a tutorial on how to do so:

**Warning: we do not support local jupyter notebook installations. If this does
not work on your computer, we will ask you to upload it to Google Colab first.**

## Step 1: Add a code cell

Paste the following into the code cell and run it:

```
!pip install nbconvert[webpdf] > /dev/null 2>&1
!playwright install chromium > /dev/null 2>&1
!apt-get install -y libatk1.0-0 libatk-bridge2.0-0 libxcomposite1 > /dev/null 2>&1
import json
from google.colab import _message
nb = _message.blocking_request('get_ipynb')['ipynb']
with open('/content/export.ipynb', 'w') as f:
    json.dump(nb, f)
!jupyter nbconvert --to webpdf --embed-images export.ipynb
```

## Step 2: Download export.pdf

And you are done!