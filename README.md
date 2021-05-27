# Translate books with Google Translate for free to any language with Python 📚

Here you have the bear minimum if you know Python. Tutorial with additional information about the process, copyrights and lawful bindings for translations can be found [on my blog][5].

The following code generates 2 docx files of text scanned from photos.
Photos have to be located within a folder placed next to this script. The flow of work is:

- OCR scanning all photos with [pytesseract][8]
- Using pure [requests][7] to translate via Google API (__not__ using _google-cloud-translate_)
- Using [python-docx][6] to generate docx documents for original and translated books.

In order to make it work a few steps have to be fulfilled:

1. Install __requirements.txt__ by running 
```
pip install -r requirements.txt
```
2. [Google Service Account Credentials][0] have to be generated.
3. [Google SDK package][1] installed.
4. [Credentials][2] loaded into terminal
```
export GOOGLE_APPLICATION_CREDENTIALS="/path-to-credentials/credentials.json"
```
5. Terminal [authenticated][10]

```
gcloud auth login
```

Then we need to [get auth token][3] obtained from command line. In order to do that run:
```
gcloud auth application-default print-access-token
```

You should recieve something like:
```
ya29.c.Kp8BAQhYC2hyHsFuRlpjrJnT0XkT[...]axi0Z_3y1-xdUaodmnnjkmlquF3ol8CInVDYPdJO8jMr3h-alcQUayKAJD_e7cuw
```

Using this token update **GOOGLE_API_TOKEN** variable in **main.py** and run it.

```
python3 main.py
```

You will be prompted for folder name, you can type _herman_hesse_ which is a name of example folder that comes with this repo.

```
> python3 main.py
Enter name of the folder with images of scanned book: herman_hesse
```

You can run the script within a folder with multiple books to translate. For example:

    ├── herman_hesse/             # Folder with pictures of pages from example book
    ├── another_book/            # Folder with pictures of pages from another book
    ├── main.py                   
    ├── LICENSE
    └── README.md

## Results

Two docx documents opened next to each other:

![Siddhartha](./translation_result.png 'translation_result')


## Remember

Books are protected with copyrights! Translate only books that are on the public domain. If you want to thank me and/or know more, visit [blog post for this code][5].

If you have questions or request feel free to reach me via [contact form][4].


[0]: https://cloud.google.com/translate/docs/setup#creating_service_accounts_and_keys
[1]: https://cloud.google.com/translate/docs/setup#sdk
[2]: https://cloud.google.com/translate/docs/setup#using_the_service_account_key_file_in_your_environment
[3]: https://cloud.google.com/translate/docs/setup#test_the_sdk_and_authentication
[4]: https://hvitis.dev/contact
[5]: https://hvitis.dev/how-to-translate-books-for-free-to-any-language-with-python
[6]: https://python-docx.readthedocs.io/en/latest/index.html
[7]: https://docs.python-requests.org/en/master/index.html
[8]: https://pypi.org/project/pytesseract/
[10]: https://cloud.google.com/sdk/docs/initializing