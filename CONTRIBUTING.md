# Contributing to Public APIs

Thank you for considering contributing to this project! We welcome contributions in the form of new APIs, fixes to existing documentation, or any other improvements.

## How to Contribute

1. **Check Existing APIs**: Before submitting a new API, check the existing list to avoid duplicates.
2. **Fork the Repository**: Fork this [repo](https://github.com/gdsc-uoem/public-apis) to your own GitHub account.
3. **Add Your API**: 
   - Go to the appropriate category folder (e.g., `categories/weather`) or create a new folder if the category does not exist.
   - Add a markdown file with the API details (name, description, authentication info, example usage).
4. **Create a Pull Request**: Once you're done, submit a pull request to this repository.

### API File Format

Each API should have a `.md` file with the following structure:


# API Name

**Description**: Brief description of the API.

**Authentication**: Describe if and what kind of authentication is required (e.g., API Key, OAuth).

**Base URL**: `https://api.example.com/v1/`

**Endpoints**:
- `/endpoint1`: Description of what this endpoint does.
- `/endpoint2`: Description of what this endpoint does.

**Example Request**:
```bash
curl -X GET "https://api.example.com/v1/endpoint1" -H "Authorization: Bearer API_KEY"

```

**Example Response**:

```json
{
  "key": "value",
  "data": "sample response"
}
```

**Rate Limits**: Mention any rate limits or restrictions.

---

#### LICENSE
```text
MIT License