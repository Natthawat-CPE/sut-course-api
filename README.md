# SUT COURSE API 📚

This project scrapes course data from Reg SUT.


## Getting started 🚀

Clone this repository

```zsh
git clone https://github.com/pandakn/sut-course-api.git

cd sut-course-api
```

Install dependencies using `npm`

```zsh
npm install
```

After this step, you will get `node_modules` folder in the root of the project.

### Start Project
```
npm run dev
```
The applciation will run at [localhost:3000](http://localhost:3000) or you can port change

## API Reference 

#### Get Course

```http
  GET /api/courses
```

| Parameter    | Type     | Description                                                          |
| :----------- | :------- | :------------------------------------------------------------------- |
| `acadyear`   | `string` | The academic year for which you want to retrieve courses (e.g. 2565) |
| `semester`   | `string` | The semester for which you want to retrieve courses (e.g. 3)         |
| `coursecode` | `string` | The course code pattern to filter courses (e.g. ist30 1105)          |
| `coursename` | `string` | The course name to filter courses (e.g. english\*)                   |
| `maxrow`     | `string` | The maximum number of rows to return in the response (e.g. 50)       |

> **Note** : Either one of coursecode or coursename can be entered.

> **Warning** : If coursecode and coursename are not specified, scraping all the data will take a very long time.

> `e.g.: /api/courses?acadyear=2565&semester=3&coursecode=ist30 1105&coursename=&maxrow=50`

## Usage/Examples JSON

```json
"data": {
    "year": "3/2565",
    "courseData": [
        {
            "id": 1,
            "url": "http://reg.sut.ac.th/registrar/class_info_2.asp?backto=home&option=0&courseid=1011782&coursecode=IST301105&acadyear=2565&semester=3&avs434084436=1",
            "courseCode": "IST30 1105",
            "version": "1",
            "courseNameEN": "ENGLISH FOR CAREERS",
            "courseNameTH": "ภาษาอังกฤษเพื่อการทำงาน",
            "faculty": "สำนักวิชาเทคโนโลยีสังคม",
            "department": "ภาษาต่างประเทศ",
            "note": "(FOR INTERNATIONAL PROGRAM)",
            "professors": [
                "ผู้ช่วยศาสตราจารย์จินดาพร แสงกาญจนวนิช",
                "อาจารย์Michael Sinclair Scott"
            ],
            "credit": "3 (3-0-6)",
            "section": "1",
            "status": "เปิดลงปกติ สามารถลงทะเบียนผ่าน WEB ได้",
            "language": "EN ",
            "degree": "ปริญญาตรี",
            "classSchedule": [
                {
                    "day": "Mo",
                    "times": "09:00-10:00",
                    "room": "B1116"
                },
                {
                    "day": "We",
                    "times": "08:00-10:00",
                    "room": "B1114"
                }
            ],
            "seat": {
                "totalSeat": "40",
                "registered": "39",
                "remain": "1"
            },
            "details": {
                "courseStatus": "ใช้งาน",
                "courseCondition": [
                    "IST30 1104",
                    "213204",
                    "203204"
                ],
                "continueCourse": [
                    "224359"
                ],
                "equivalentCourse": [
                    "213305",
                    "IST30 1105"
                ],
                "midExam": null,
                "finalExam": "4 ก.ค. 2566 เวลา 09:00 - 12:00 อาคาร B ห้อง N (สอบตามตารางมหาวิทยาลัย)"
            }
        }
    ]
}
```

## Tech Stack

**Server:** Node, Express

[**Cheerio**](https://cheerio.js.org/) : scrape data

[**Redis**](https://redis.io/) : cache data
