# GoMarble AI Engineer Assignment

## **Project Overview**
This project implements an API server capable of extracting reviews information from product pages such as Shopify and Amazon. The API dynamically identifies CSS elements for reviews, handles pagination, and retrieves all reviews using browser automation and LLM integration.

---

## **Features**
- **Dynamic CSS Selector Identification**: Leverages LLMs to identify the CSS selectors for review elements dynamically.
- **Pagination Handling**: Retrieves reviews across multiple pages to ensure complete data extraction.
- **Universal Compatibility**: Works with various product review pages, including dynamic content rendering.
- **API Response Format**: Provides well-structured JSON responses with reviews data.
- **Browser Automation**: Uses Playwright for headless browser interactions.
- **LLM Integration**: Integrates OpenAI or free alternatives for dynamic CSS identification.

---

## **System Requirements**
- Python 3.8 or later
- Dependencies (listed in `requirements.txt`)
- OpenAI API Key (for LLM integration)

---

## **Project Structure**
```
.
├── app/
│   └── main.py             # FastAPI application entry point
├── llm_utils/
│   └── css_identifier.py   # Module for dynamic CSS identification using LLMs
├── static/
│   └── example_responses.json  # Sample API response
├── requirements.txt        # Python dependencies
├── README.md               # Project documentation
├── .gitignore              # Ignored files/folders
├── venv/                   # Virtual environment
```

---

## **API Endpoints**

### **1. GET /api/reviews?page={url}**
- **Description**: Extracts all reviews from the given product page URL.
- **Parameters**:
  - `page`: URL of the product page.
- **Response** (Example):
```json
{
  "reviews_count": 100,
  "reviews": [
    {
      "title": "Amazing Product!",
      "body": "The product exceeded my expectations.",
      "rating": 5,
      "reviewer": "John Doe"
    },
    {
      "title": "Not worth it",
      "body": "Poor quality and high price.",
      "rating": 2,
      "reviewer": "Jane Smith"
    }
  ]
}
```

---

## **Installation Guide**

### **Step 1: Clone the Repository**
```bash
git clone https://github.com/yourusername/go_marble_ai.git
cd go_marble_ai
```

### **Step 2: Create a Virtual Environment**
```bash
python -m venv venv
source venv/bin/activate  # For Mac/Linux
venv\Scripts\activate   # For Windows
```

### **Step 3: Install Dependencies**
```bash
pip install -r requirements.txt
playwright install
```

### **Step 4: Set Up Environment Variables**
Create a `.env` file in the root directory and add your OpenAI API key:
```
OPENAI_API_KEY=your_openai_api_key
```

### **Step 5: Run the Server**
```bash
uvicorn app.main:app --reload
```
- Access the API documentation at [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs).

---

## **System Architecture**
1. **Input**: User provides a product page URL via the API endpoint.
2. **Dynamic CSS Identification**: LLM identifies review-specific CSS selectors.
3. **Browser Automation**: Playwright navigates the product page, retrieves reviews, and handles pagination.
4. **Data Parsing**: Extracted reviews are formatted into a structured JSON response.
5. **Output**: JSON response with all reviews and metadata is returned.

---

## **How to Use the API**
1. Start the server using:
   ```bash
   uvicorn app.main:app --reload
   ```
2. Open the API docs at `http://127.0.0.1:8000/docs`.
3. Test the `/api/reviews` endpoint by providing a valid product page URL.

Example:
```bash
GET /api/reviews?page=https://www.amazon.com/product-page
```

---

## **Testing**
- Use tools like **Postman** or **cURL** to test the API endpoints.
- Sample Request:
  ```bash
  curl -X GET "http://127.0.0.1:8000/api/reviews?page=https://www.amazon.com/product-page"
  ```
- Sample Response: Refer to the [Response Format](#response).

---

## **Example Pages for Testing**
- [Samsung Galaxy Ultra on Amazon](https://www.amazon.in/Samsung-Galaxy-Ultra-Green-Storage/dp/B0BT9CXXXX)
- [Bhumi Flannelette Sheet Set](https://www.example.com/sheet-set)
- [LyfeFuel Essentials Nutrition Shake](https://www.example.com/shake)

---

## **Acknowledgments**
Special thanks to GoMarble for providing this engaging assignment opportunity.

---

