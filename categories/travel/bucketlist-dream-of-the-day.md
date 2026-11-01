# Bucketlist.nl Dream of the Day API

**Description**:  
A public JSON feed containing one daily travel, leisure or life-experience idea, with image metadata, a canonical experience URL and source attribution. It can be used in activity-discovery interfaces or inspiration widgets.

**Authentication**:  
No API key, account, OAuth flow or other authentication is required for the public GET endpoint.

**Base URL**:  
`https://bucketlist.nl`

---

## Endpoints

### Get the current daily experience

- **Method**: `GET`
- **Endpoint**: `/api/droom-van-de-dag`
- **Response**: JSON with `date`, `scope`, `language`, `requestedTheme`, `dream` and `attribution`.
- **Scope**: `nederland` (default) or `wereld`.
- **Language**: `nl` (default), `en`, `de`, `fr` or `es`.
- **Theme**: Optional `theme` string, maximum 64 characters; the API can fall back to the complete image-ready selection.

The default response contains Dutch experience text. The endpoint returns one selected item, not a searchable catalogue, booking service or availability/pricing feed. The official specification also documents HTTP 503 when no suitable published item is available.

**Example Request**:

```bash
curl -X GET "https://bucketlist.nl/api/droom-van-de-dag"
```

**Example Response**:

This is an excerpt of the real default response fetched on 1 November 2026. Image metadata, referral information and other properties are omitted here; see the OpenAPI document for the full schema.

```json
{
  "date": "2026-11-01",
  "scope": "nederland",
  "language": "nl",
  "dream": {
    "title": "Een EHBO-cursus afronden",
    "canonicalUrl": "https://bucketlist.nl/ervaringen/een-ehbo-cursus-afronden?scope=nederland"
  },
  "attribution": {
    "name": "Bucketlist.nl",
    "url": "https://bucketlist.nl/"
  }
}
```

## Rate Limits and Restrictions

The official OpenAPI document does not publish a numeric request quota or a reset period. The daily content schedule is not a statement of how many requests are permitted. No uptime SLA is stated.

The feed is public and free to request. Some linked experience pages contain labelled affiliate booking links. This entry does not assert an open-data or image-reuse licence.

## Resources

- [Official OpenAPI specification](https://bucketlist.nl/brand/droom-van-de-dag.openapi.json)
- [Public JSON endpoint](https://bucketlist.nl/api/droom-van-de-dag)

