Frontend Integration with a Secure API

## 1. Introduction
In this documentation, we will explore how to integrate a frontend with a secure API for listing movie documents and their corresponding PDF notes. The API is built using Django REST Framework and provides endpoints to fetch documents and their details. We will focus on fetching and displaying data on the frontend, including styling and handling the API responses.

## 2. Main Objective
The primary goal is to demonstrate how to:

- #### Fetch Data: 
Connect to the API to retrieve a list of movie documents and their details.

- #### Display Data: 
Present the data in an interactive and user-friendly format using Bootstrap's accordion component.

- #### Handle Security: 
Ensure that API requests are securely made using authentication methods.

## 3. Specific Objective

- **Fetch and Display Documents:** Retrieve a list of movie documents and their details.
- **Interactive Accordion:** Use Bootstrap accordion to display the documents and their details in a collapsible format.
- **Handle PDF Downloads:** Provide users with the option to download PDF notes associated with each document.
  
## 4. Methodologies (Required Technologies)
**Required Technologies`**

- **HTML/CSS:** For structuring and styling the webpage.
- **JavaScript/jQuery:** To make asynchronous requests to the API and dynamically update the webpage.
- **Bootstrap:** For responsive design and UI components like the accordion.
- **API:** A secure Django REST Framework API to fetch document data.

## 5. Data Types [ API calling variable ]

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

## 6. API KEY & URLS

```javascript
const API_KEY = 'vlWnzo3b.LzCsbJisS4JxZvFA9IqM5Z0udtSgjnpq';
//const DOCUMENT_API_URL = 'http://127.0.0.1:8000/api/documents/';
//const DETAILS_API_URL = 'http://127.0.0.1:8000/api/document-details/';
const DOCUMENT_API_URL = 'https://openkey.pythonanywhere.com/api/documents/';
const DETAILS_API_URL = 'https://openkey.pythonanywhere.com/api/document-details/';
```
