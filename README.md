# FRONTEND API INTEGRATION DOCUMENTATION
![GG](https://github.com/user-attachments/assets/af82f681-5f1a-49d1-9e9c-4b7478c8a114)
## SECURE API INTEGRATION FOR THE FRONTEND
### OPEN SOURCE TECHNOLOGIES USED: HTML, CSS, JAVASCRIPT, BOOTSTRAP, JQUERY, AJAX

# Creation of Backend API using Django
You can find the backend API creation using Django here: [https://github.com/shamiraty/django-restful](https://github.com/shamiraty/django-restful)

**Online Demo**
open live demo [Click](https://openkey.pythonanywhere.com/)

- `username:  demo`
- `password: demo1234`
---
## 1. INTRODUCTION
In this documentation, we will explore how to integrate a frontend with a secure API for listing movie documents and their corresponding PDF notes. The API is built using Django REST Framework and provides endpoints to fetch documents and their details. We will focus on fetching and displaying data on the frontend, including styling and handling the API responses.

## 2. MAIN OBJECTIVE
The primary goal is to demonstrate how to:

- #### Fetch Data: 
Connect to the API to retrieve a list of movie documents and their details.

- #### Display Data: 
Present the data in an interactive and user-friendly format using Bootstrap's accordion component.

- #### Handle Security: 
Ensure that API requests are securely made using authentication methods.

## 3. SPECIFIC OBJECTIVE

- **Fetch and Display Documents:** Retrieve a list of movie documents and their details.
- **Interactive Accordion:** Use Bootstrap accordion to display the documents and their details in a collapsible format.
- **Handle PDF Downloads:** Provide users with the option to download PDF notes associated with each document.
  
## 4. METHODOLOGIES (REQUIRED TECHNOLOGIES)
**Required Technologies`**

- **HTML/CSS:** For structuring and styling the webpage.
- **JavaScript/jQuery/Ajax:** To make asynchronous requests to the API and dynamically update the webpage.
- **Bootstrap:** For responsive design and UI components like the accordion.
- **API:** A secure Django REST Framework API to fetch document data.

## 5. DATA TYPES [ API CALLING VARIABLE ]

**Document Model:  Mother Model**

- `id (Integer):` Unique ID for the document.
- `title (String):` Title of the document.
- `description (String):` Short description of the document.
- `created_at (DateTime):` Creation timestamp.
- `image (String/URL):` URL to the image.
- `file (String/URL):` URL to the document file.
- `uploaded_by (String):` Username of the uploader.

**Document Detail Model:  Child Model**

- `id (Integer):` Unique ID for the document detail.
- `document (Object):` Related document object with its data.
- `additional_info (String):` Additional information about the document.
- `reference_number (String):` Reference number for the document.
- `status (String):` Status of the document (e.g., new, old).
- category (String): Category of the document.
- `tags (String):` Associated tags.
- `remarks (String):` Remarks about the document.

## 6. API KEY & URLS FOR LOCALHOST

```html
<script>
const API_KEY = 'vlWnzo3b.LzCsbJisS4JxZvFA9IqM5Z0udtSgjnpq';
const DOCUMENT_API_URL = 'http://127.0.0.1:8000/api/documents/';
const DETAILS_API_URL = 'http://127.0.0.1:8000/api/document-details/';
</script>
```

## 7. API KEY & URLS FOR EXTERNAL SERVER

```html
<script>
const API_KEY = 'vlWnzo3b.LzCsbJisS4JxZvFA9IqM5Z0udtSgjnpq';
const DOCUMENT_API_URL = 'https://openkey.pythonanywhere.com/api/documents/';
const DETAILS_API_URL = 'https://openkey.pythonanywhere.com/api/document-details/';
</script>
```

## 8. API TESTING
**Setting Up Postman for API Request:**
To test your API with Postman and verify how data is being returned, follow these steps:

- Install Postman:
- If you haven't installed Postman, download it from here. `https://www.postman.com/`
- Install and launch Postman on your machine.*
- Test the Document API (/api/documents/)
- Open Postman.
- Create a new request:
- Click the + button in the top-left to open a new request tab.
- Set the request type to GET.
- Set the URL: one by one testing
- Enter Local URL of  API: `http://127.0.0.1:8000/api/documents/` 
- Enter Online URL of  API: `https://openkey.pythonanywhere.com/api/documents/`
- Enter local URL of  API: `http://127.0.0.1:8000/api/document-details/` 
- Enter online URL of  API: `https://openkey.pythonanywhere.com/api/document-details/` 
- Add Authorization:
- Select the Headers tab.
- Add the header field Authorization and use your API key as the value, like this:
```bash
Key: Authorization
Value: Api-Key vlWnzo3b.LzCsbJisS4JxZvFA9IqM5Z0udtSgjnpq (replace with your actual API key).
```
- Then Send the Request: Click the Send button.
- Postman will make a request to your API and show the response data below.

**figure 1**
![aa](https://github.com/user-attachments/assets/f873e851-d9b0-4994-95f3-6e103de6b6a1)
**figure 2**
![bb](https://github.com/user-attachments/assets/e8c0a22d-e343-43e9-b765-3ee01e9b77dd)
**figure 3**
![dd](https://github.com/user-attachments/assets/5f7471f0-5a30-440a-a880-d44a2667bc65)
**figure 4**
![cc](https://github.com/user-attachments/assets/cd57247f-fa28-40f7-8e10-1c805f14943e)
- If the response contains a list of documents or details, you should see the API returning JSON data, such as:
**response example:  child table**
```json
[
        {
                "id": 2,
                "document": {
                        "id": 4,
                        "title": "Alice's Adventures in Wonderland",
                        "description": "Lewis Carroll",
                        "created_at": "2024-09-12T13:43:03.815004Z",
                        "image": "https://openkey.pythonanywhere.com/media/images/MV5BMzE5MTViZmYtMWE1YS00MTlkLWEyMzQtMDFkNmM3ZTdiMTQ2XkEyXkFqcGdeQXVyMTIzNTI5NTM1._V1_.jpg",
                        "file": "https://openkey.pythonanywhere.com/media/files/Film-Synopsis-Example-Whiplash.pdf",
                        "uploaded_by": "samir"
                },
                "additional_info": "This list represents a comprehensive and trusted collection of the greatest books. Developed",
                "reference_number": "1",
                "status": "new",
                "category": "adventures",
                "tags": "hollywood",
                "remarks": "good"
        }
]
```
**response example:  mother table**
```json
[
        {
                "id": 4,
                "title": "Alice's Adventures in Wonderland",
                "description": "Lewis Carroll",
                "created_at": "2024-09-12T13:43:03.815004Z",
                "image": "https://openkey.pythonanywhere.com/media/images/MV5BMzE5MTViZmYtMWE1YS00MTlkLWEyMzQtMDFkNmM3ZTdiMTQ2XkEyXkFqcGdeQXVyMTIzNTI5NTM1._V1_.jpg",
                "file": "https://openkey.pythonanywhere.com/media/files/Film-Synopsis-Example-Whiplash.pdf",
                "uploaded_by": "samir"
        },
        {
                "id": 5,
                "title": "The Adventures of Huckleberry Finn",
                "description": "Mark Twain",
                "created_at": "2024-09-12T13:46:12.094662Z",
                "image": "https://openkey.pythonanywhere.com/media/images/the-adventures-of-huckleberry-finn-9781481403757_hr.jpg",
                "file": "https://openkey.pythonanywhere.com/media/files/Film-Synopsis-Example-Whiplash_ZeBkdyV.pdf",
                "uploaded_by": "samir"
        }
]
```

## 9. JavaScript Example
- Here’s an example of how to fetch the documents and their corresponding details using jQuery:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="bootstrap/css/ajax_cloudfare.css" rel="stylesheet">
    <link href="bootstrap/css/fonts.css" rel="stylesheet">
    <link href="bootstrap/css/datatable.css" rel="stylesheet">
    <link href="bootstrap/css/bootstrap.min2.css" rel="stylesheet">
    <link href="bootstrap/css/ajax_jquery.css" rel="stylesheet">
    <link href="bootstrap/awesome/css/all.min.css" rel="stylesheet">
    <link href="bootstrap/awesome/css/fontawesome.min.css" rel="stylesheet">
    <link href="bootstrap/css/awaresome.css" rel="stylesheet">
    <link href="bootstrap/css/bootstrap_buttons.css" rel="stylesheet">
    <style>
        /* Ensure background stays consistent with blur */
        html, body {
            margin: 0;
            padding: 0;
            height: 100%;
            width: 100%;
            background: url('images/q.jpg') no-repeat center center fixed;
            background-size: cover;
        }

        /* Blur effect that covers the entire body */
        .bg-blur {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            backdrop-filter: blur(10px);
            background-color: rgba(0, 0, 0, 0.6); /* Optional dark overlay */
            z-index: 1;
        }

        /* Ensure container sits above the blur layer */
        .content {
            position: relative;
            z-index: 2;
        }

        .accordion-button:focus {
            box-shadow: none;
        }

        .card-header {
            background-color: #343a40;
            color: #fff;
        }

        .accordion-button {
            color: #fff;
            background-color: #343a40;
        }

        .accordion-button.collapsed {
            color: #fff;
            background-color: #343a40;
        }

        .accordion-body {
            background-color: #f8f9fa;
        }
    </style>
</head>
<body>

    <!-- Background Blur Layer -->
    <div class="bg-blur"></div>

    <!-- Main Content Area -->
    <div class="content">
        <!-- Accordion for documents -->
        <div class="container">
            <div class="card bg-secondary mt-5">
                <div class="card-body">
            <div class="accordion" id="documentsAccordion">
                <!-- Dynamic accordion items will be injected here -->
            </div>
        </div>
        </div>
    </div>
    </div>

    <script src="bootstrap/js/jquery.js"></script>
    <script src="bootstrap/js/jquery_ajax.js"></script>
    <script src="bootstrap/js/jquery_datatable.js"></script>
    <script src="bootstrap/js/datatable.js"></script>
    <script src="bootstrap/js/bootstrap.js"></script>
    <script>
        
        $(document).ready(function () {
            const API_KEY = 'vlWnzo3b.LzCsbJisS4JxZvFA9IqM5Z0udtSgjnpq';
            //const DOCUMENT_API_URL = 'http://127.0.0.1:8000/api/documents/';
            //const DETAILS_API_URL = 'http://127.0.0.1:8000/api/document-details/';
            const DOCUMENT_API_URL = 'https://openkey.pythonanywhere.com/api/documents/';
            const DETAILS_API_URL = 'https://openkey.pythonanywhere.com/api/document-details/';

            // Fetch documents and their details from the APIs
            $.when(
                $.ajax({
                    url: DOCUMENT_API_URL,
                    method: 'GET',
                    headers: {
                        'Authorization': 'Api-Key ' + API_KEY
                    }
                }),
                $.ajax({
                    url: DETAILS_API_URL,
                    method: 'GET',
                    headers: {
                        'Authorization': 'Api-Key ' + API_KEY
                    }
                })
            ).done(function (documentsData, detailsData) {
                let documents = documentsData[0];
                let details = detailsData[0];
                let detailsMap = {};

                // Map DocumentDetails by document ID
                details.forEach(detail => {
                    if (!detailsMap[detail.document.id]) {
                        detailsMap[detail.document.id] = [];
                    }
                    detailsMap[detail.document.id].push(detail);
                });

                let output = '';
                documents.forEach((document, index) => {
                    let documentDetails = detailsMap[document.id] || [];
                    let detailsList = '';

                    documentDetails.forEach(detail => {
                        detailsList += `
                            <li class="list-group-item">
                                Additional Info: ${detail.additional_info}
                            </li>
                            <li class="list-group-item">
                                Reference Number: ${detail.reference_number}
                            </li>
                            <li class="list-group-item">
                                Status: ${detail.status}
                            </li>
                            <li class="list-group-item">
                                Category: ${detail.category}
                            </li>
                            <li class="list-group-item">
                                Tags: ${detail.tags}
                            </li>
                            <li class="list-group-item">
                                Remarks: ${detail.remarks}
                            </li>
                        `;
                    });

                    output += `
                        <div class="card mt-2">
                            <div class="card-header" id="heading${index}">
                                <h5 class="mb-0">
                                    <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapse${index}" aria-expanded="false" aria-controls="collapse${index}">
                                        <i class="fas fa-file-alt accordion-icon"></i>     ${document.title}
                                    </button>
                                </h5>
                            </div>

                            <div id="collapse${index}" class="accordion-collapse collapse" aria-labelledby="heading${index}" data-bs-parent="#documentsAccordion">
                                <div class="accordion-body">
                                    <img src="${document.image}" class="img-thumbnail" alt="Document Image" style="max-width: 150px; margin-bottom: 15px;">
                                    <p><strong>Description:</strong> ${document.description}</p>
                                    <p><strong>Uploaded By:</strong> <span class="badge bg-primary">${document.uploaded_by}</span></p>
                                    <p><strong>Created At:</strong> ${new Date(document.created_at).toLocaleDateString()}</p>
                                    <ul class="list-group mb-3">
                                        ${detailsList}
                                    </ul>
                                    <a href="${document.file}" class="btn btn-primary" download>
                                        <i class="fas fa-download"></i> Download File
                                    </a>
                                </div>
                            </div>
                        </div>
                    `;
                });

                // Show document accordion
                $('#documentsAccordion').html(output);
            }).fail(function (error) {
                console.log("Error fetching data: ", error);
            });
        });
    </script>
</body>
</html>
```


---
**My Contacts**

**WhatsApp**  
+255675839840  
+255656848274

**YouTube**  
[Visit my YouTube Channel](https://www.youtube.com/channel/UCjepDdFYKzVHFiOhsiVVffQ)

**Telegram**  
+255656848274  
+255738144353

**PlayStore**  
[Visit my PlayStore Developer Page](https://play.google.com/store/apps/dev?id=7334720987169992827&hl=en_US&pli=1)

**GitHub**  
[Visit my GitHub](https://github.com/shamiraty/)


