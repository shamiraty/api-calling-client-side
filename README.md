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

## 6. API KEY & URLS for localhost

```html
<script>
const API_KEY = 'vlWnzo3b.LzCsbJisS4JxZvFA9IqM5Z0udtSgjnpq';
const DOCUMENT_API_URL = 'http://127.0.0.1:8000/api/documents/';
const DETAILS_API_URL = 'http://127.0.0.1:8000/api/document-details/';
</script>
```


## 7. API KEY & URLS for external server

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
*If you haven't installed Postman, download it from here.*
*Install and launch Postman on your machine.*

- Test the Document API (/api/documents/)
- Open Postman.
- Create a new request:
- Click the + button in the top-left to open a new request tab.
- Set the request type to GET.
- Set the URL:
- Enter the URL of  API: `http://127.0.0.1:8000/api/documents/` (if you run localhost mother table).
- Enter the URL of  API: `https://openkey.pythonanywhere.com/api/documents/` (if you access our online API mother table)
- Enter the URL of  API: `http://127.0.0.1:8000/api/document-details/` (if you run localhost child table).
- Enter the URL of  API: `https://openkey.pythonanywhere.com/api/document-details/` (if you access our online API childmother table)
- Add Authorization:
- Select the Headers tab.
- Add the header field Authorization and use your API key as the value, like this:
```bash
Key: Authorization
Value: Api-Key vlWnzo3b.LzCsbJisS4JxZvFA9IqM5Z0udtSgjnpq (replace with your actual API key).
```
- Then Send the Request: Click the Send button.
- Postman will make a request to your API and show the response data below.
`figure 1`
![aa](https://github.com/user-attachments/assets/f873e851-d9b0-4994-95f3-6e103de6b6a1)
`figure 2`
![bb](https://github.com/user-attachments/assets/e8c0a22d-e343-43e9-b765-3ee01e9b77dd)
`figure 3`
![dd](https://github.com/user-attachments/assets/5f7471f0-5a30-440a-a880-d44a2667bc65)
`figure 4`
![cc](https://github.com/user-attachments/assets/cd57247f-fa28-40f7-8e10-1c805f14943e)
- If the response contains a list of documents or details, you should see the API returning JSON data, such as:
`response example:  child table`
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
`response example:  mother table`
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




 
