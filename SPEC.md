# **Webcomic Sharing Protocol (v1)**

This protocol defines how to organize and share webcomics using a JSON file. It enables applications (like mobile apps) to display comics and download them for offline use.



## **Structure of the JSON File**

A comic is described in a JSON file with the following structure:

### **Main File: `comic.json`**
```json
{
  "Name": "ComicName",
  "Description": "This comic is about...",
  "Cover": {},
  "meta": {},
  "Chapters": []
}
```

| Tag         | Type             | Description                                        |
| ----------- | ---------------- | -------------------------------------------------- |
| Name        | string           | The comic's display name.                          |
| Description | string           | A brief description of the comic.                  |
| Cover       | Image            | Details about the cover image (explained below).   |
| meta        | object           | Extra information like tags and reading direction. |
| Chapters    | array of Chapter | A list of all the comic’s chapters.                |

### Details of Each Section
#### Cover

```json
{
    "Img":"https://cover.jpg",
    "Thumb":"https://cover.thumb.jpg"
}
```
| Tag   | Type | Description                        |
| ----- | ---- | ---------------------------------- |
| Img   | url  | URL for the full-size cover image. |
| Thumb | utl  | URL for the smaller thumbnail.     |

#### Metadata (`meta`)
```json
{
    "direction":"le-ri|ri-le|to-bo",
    "supportPage":{},
    "tags":[]
}
```
| Tag         | Type            | Description                                                |
| ----------- | --------------- | ---------------------------------------------------------- |
| direction   | enum            | Reading direction. (Options described below)               |
| supportPage | unknown         | Details about a support page (e.g., for donations or ads). |
| tags        | array of string | Keywords that can be used to search for the comic.         |

- direction: Reading direction. Options:
    - "le-ri": Left-to-right (Western comics)
    - "ri-le": Right-to-left (Mangas) 
    - "to-bo": Top-to-bottom (Webcomics)


#### Chapters
```json
{
    "Nr":1,
    "Name":"Chapter 1",
    "Desc":"This chapter is about...",
    "Img":"https://ch1.cover.jpg",
    "Thumb":"https://ch1.cover.thumb.jpg",
    "Pages":[]
}
```
| Tag   | Type          | Description                                 |
| ----- | ------------- | ------------------------------------------- |
| Nr    | float         | The chapter's number (used for sorting).    |
| Name  | string        | The chapter’s title.                        |
| Desc  | string        | A short description of the chapter.         |
| Img   | url           | URL for the chapter’s cover image.          |
| Thumb | url           | URL for the thumbnail of the chapter cover. |
| Pages | array of Page | A list of pages in this chapter.            |

#### Pages
```json
{
    "Nr":1,
    "Name":"Page 1",
    "Desc":"This page is about...",
    "Img":"https://chapter1/page1.jpg",
    "Thumb":"https://chapter1/page1.thumb.jpg"
}
```

| Tag   | Type   | Description                           |
| ----- | ------ | ------------------------------------- |
| Nr    | float  | The page’s number (used for sorting). |
| Name  | string | The page title or label.              |
| Desc  | string | A short description of the page.      |
| Img   | url    | URL for the page image.               |
| Thumb | url    | URL for the thumbnail of the page.    |

### Example Comic JSON
```json
{
  "Name": "My First Comic",
  "Description": "A journey into JSON comics!",
  "Cover": {
    "Img": "https://example.com/cover.jpg",
    "Thumb": "https://example.com/cover_thumb.jpg"
  },
  "meta": {
    "direction": "le-ri",
    "supportPage": {
      "url": "https://example.com/support"
    },
    "tags": ["adventure", "fantasy"]
  },
  "Chapters": [
    {
      "Nr": 1,
      "Name": "Chapter 1",
      "Desc": "The adventure begins.",
      "Img": "https://example.com/ch1_cover.jpg",
      "Thumb": "https://example.com/ch1_cover_thumb.jpg",
      "Pages": [
        {
          "Nr": 1,
          "Name": "Page 1",
          "Desc": "Meet the hero.",
          "Img": "https://example.com/ch1/page1.jpg",
          "Thumb": "https://example.com/ch1/page1_thumb.jpg"
        }
      ]
    }
  ]
}
```
