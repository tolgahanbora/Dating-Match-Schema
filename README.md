#Coupling Dating-Match-Schema

Authenticating
You'll need to supply a Instagram - Mock auth token and an associated instagram id.

> curl -X POST https://api.coupling.app/auth --data '{"instagram_token": ig_token, "instagram_id": ig_user_id}'
The easiest way to get this is to go here, log in and then pick the auth token out of the URL you are redirected to.

Response:

{
	"token": "8c839cee-0980-4b73-861b-8739cb597f57",
	"user": { ... }, 
	"globals": { ... },
	"versions": { ... }
}
Updating your profile
> curl -X POST https://api.coupling.app/profile --data '{"age_filter_min": 26, "gender": 1, "age_filter_max": 32, "distance_filter": 14}'
Parameter info:

Gender	0: Male
1: Female
age_filter_min	int of min age match
age_filter_max	int of max age match
distance_filter	max search radius in kilometers
Reporting a user
> curl -X POST 'https://api.coupling.app/report/{_id} --data '{"cause": cause_id}'
Note cause_id: should be 1 or 2, (1 is spam, 2 is inappropriate/offensive)

Message sending
Send a message to a match. Note you'll get a 500 back if you try to send a message to someone who isn't a match

curl 'https://api.gotindaer.com/user/matches/{_id} --data '{"message": "your message here"}'
response:

{
	"_id":"53467235483cb56c475cc1d6",
	"from":"53430689ab3c04c13e006f
  ",
	"to":"533a59ea52046fc077002815",
	"match_id":"53464b0728ac73976d0a3fbf",
	"sent_date":"2023-04-10T10:28:05.764Z",
	"message":"hi!",
	"created_date":"2023-04-10T10:28:05.764Z"
}
Updating your location
curl 'https://api.gotindaer.com/user/ping --data '{"lat": latitude, "lon": longitude}'

{
	"status": 200,
	"error": "position change not significant"
}
Get "updates"
> curl 'https://api.gotindaer.com/updates'
Response:

{
	"matches": [{
		"_id": "53464b0728ac73976d0a3fbf",
		"messages": [{
			"_id": "534651198ce6da797248c1a3",
			"match_id": "53464b0728ac73976d0a3fbf",
			"to": "53430689ab3c04c13e006ffb",
			"from": "533a59ea52046fc077002815",
			"message": "hi  .... how is it going?",
			"sent_date": "2023-04-10T08:06:49.800Z",
			"created_date": "2023-04-10T08:06:49.800Z",
			"timestamp": 1397117209800
		}, {
			"_id": "53466fd298b7278b72156523",
			"match_id": "53464b0728ac73976d0a3fbf",
			"to": "533a59ea52046fc077002815",
			"from": "53430689ab3c04c13e006ffb",
			"message": "Good thanks you? :)",
			"sent_date": "2023-04-10T10:17:54.379Z",
			"created_date": "2023-04-10T10:17:54.379Z",
			"timestamp": 1397125074379
		}],
		"last_activity_date": "2023-04-10T10:17:54.379Z"
	}],
	"blocks": [],
	"lists": [],
	"deleted_lists": [],
	"last_activity_date": "2023-04-10T10:17:54.379Z"
}
To 'like' or 'pass' a User
> curl https://api.coupling.app/{like|pass}/{_id}
Response:

{match: match_result}
match_result will be true if they like you, false if they haven't liked you or don't like you

Recommendations
> curl https://api.coupling.app/user/recs
{
    "status": 200,
    "results": [{
        "distance_mi": 2,
        "common_like_count": 0,
        "common_friend_count": 0,
        "common_likes": [],
        "common_friends": [],
        "_id": "518d666a2a00df0e490000b9",
        "bio": "",
        "birth_date": "1986-05-17T00:00:00.000Z",
        "gender": 1,
        "name": "Elen",
        "ping_time": "2023-04-08T11:59:18.494Z",
        "photos": [{
            "id": "fea4f480-7ce0-4143-a310-a03c2b2cdbc6",
            "main": true,
            "crop": "source",
            "fileName": "fea4f480-7ce0-4143-a310-a03c2b2cdbc6.jpg",
            "extension": "jpg",
            "processedFiles": [{
                "width": 640,
                "height": 640,
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/640x640_fea4f480-7ce0-4143-a310-a03c2b2cdbc6.jpg"
            }, {
                "width": 320,
                "height": 320,
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/320x320_fea4f480-7ce0-4143-a310-a03c2b2cdbc6.jpg"
            }, {
                "width": 172,
                "height": 172,
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/172x172_fea4f480-7ce0-4143-a310-a03c2b2cdbc6.jpg"
            }, {
                "width": 84,
                "height": 84,
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/84x84_fea4f480-7ce0-4143-a310-a03c2b2cdbc6.jpg"
            }],
            "url": "http://images.coupling.app/518d666a2a00df0e490000b9/fea4f480-7ce0-4143-a310-a03c2b2cdbc6.jpg"
        }, {
            "url": "http://images.coupling.app/518d666a2a00df0e490000b9/5c1d3231-5a75-4a07-91ff-5c012716583f.jpg",
            "processedFiles": [{
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/640x640_pct_0_29.5312464_540_540_5c1d3231-5a75-4a07-91ff-5c012716583f.jpg",
                "height": 640,
                "width": 640
            }, {
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/320x320_pct_0_29.5312464_540_540_5c1d3231-5a75-4a07-91ff-5c012716583f.jpg",
                "height": 320,
                "width": 320
            }, {
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/172x172_pct_0_29.5312464_540_540_5c1d3231-5a75-4a07-91ff-5c012716583f.jpg",
                "height": 172,
                "width": 172
            }, {
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/84x84_pct_0_29.5312464_540_540_5c1d3231-5a75-4a07-91ff-5c012716583f.jpg",
                "height": 84,
                "width": 84
            }],
            "extension": "jpg",
            "fileName": "5c1d3231-5a75-4a07-91ff-5c012716583f.jpg",
            "main": false,
            "ydistance_percent": 0.75,
            "yoffset_percent": 0.04101562,
            "xoffset_percent": 0,
            "id": "5c1d3231-5a75-4a07-91ff-5c012716583f",
            "xdistance_percent": 1
        }, {
            "url": "http://images.coupling.app/518d666a2a00df0e490000b9/5abd87e5-a181-4946-a8b9-880926a78943.jpg",
            "processedFiles": [{
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/640x640_pct_0_118.125_540_540_5abd87e5-a181-4946-a8b9-880926a78943.jpg",
                "height": 640,
                "width": 640
            }, {
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/320x320_pct_0_118.125_540_540_5abd87e5-a181-4946-a8b9-880926a78943.jpg",
                "height": 320,
                "width": 320
            }, {
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/172x172_pct_0_118.125_540_540_5abd87e5-a181-4946-a8b9-880926a78943.jpg",
                "height": 172,
                "width": 172
            }, {
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/84x84_pct_0_118.125_540_540_5abd87e5-a181-4946-a8b9-880926a78943.jpg",
                "height": 84,
                "width": 84
            }],
            "extension": "jpg",
            "fileName": "5abd87e5-a181-4946-a8b9-880926a78943.jpg",
            "main": false,
            "ydistance_percent": 0.75,
            "yoffset_percent": 0.1640625,
            "xoffset_percent": 0,
            "id": "5abd87e5-a181-4946-a8b9-880926a78943",
            "xdistance_percent": 1
        }, {
            "url": "http://images.coupling.app/518d666a2a00df0e490000b9/5e168698-a034-40c0-b7fb-7c05743f2310.jpg",
            "processedFiles": [{
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/640x640_pct_157.570344_0_405_405_5e168698-a034-40c0-b7fb-7c05743f2310.jpg",
                "height": 640,
                "width": 640
            }, {
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/320x320_pct_157.570344_0_405_405_5e168698-a034-40c0-b7fb-7c05743f2310.jpg",
                "height": 320,
                "width": 320
            }, {
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/172x172_pct_157.570344_0_405_405_5e168698-a034-40c0-b7fb-7c05743f2310.jpg",
                "height": 172,
                "width": 172
            }, {
                "url": "http://images.coupling.app/518d666a2a00df0e490000b9/84x84_pct_157.570344_0_405_405_5e168698-a034-40c0-b7fb-7c05743f2310.jpg",
                "height": 84,
                "width": 84
            }],
            "extension": "jpg",
            "fileName": "5e168698-a034-40c0-b7fb-7c05743f2310.jpg",
            "main": false,
            "ydistance_percent": 1,
            "yoffset_percent": 0,
            "xoffset_percent": 0.2188477,
            "id": "5e168698-a034-40c0-b7fb-7c05743f2310",
            "xdistance_percent": 0.5625
        }],
        "birth_date_info": "fuzzy birthdate active, not displaying real birth_date"
    }, {
        "distance_mi": 4,
        "common_like_count": 0,
        "common_friend_count": 0,
        "common_likes": [],
        "common_friends": [],
        "_id": "52cfc097f43cd91a67003639",
        "bio": "",
        "birth_date": "1987-11-02T00:00:00.000Z",
        "gender": 1,
        "name": "Cristina",
        "ping_time": "2023
        -04-06T16:52:51.605Z",
        "photos": [{
            "id": "4ab7173f-7884-4fe3-872f-32c01d77de2a",
            "main": "main",
            "shape": "center_square",
            "fileName": "4ab7173f-7884-4fe3-872f-32c01d77de2a.jpg",
            "extension": "jpg",
            "processedFiles": [{
                "width": 640,
                "height": 640,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/640x640_4ab7173f-7884-4fe3-872f-32c01d77de2a.jpg"
            }, {
                "width": 320,
                "height": 320,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/320x320_4ab7173f-7884-4fe3-872f-32c01d77de2a.jpg"
            }, {
                "width": 172,
                "height": 172,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/172x172_4ab7173f-7884-4fe3-872f-32c01d77de2a.jpg"
            }, {
                "width": 84,
                "height": 84,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/84x84_4ab7173f-7884-4fe3-872f-32c01d77de2a.jpg"
            }],
            "url": "http://images.coupling.app/52cfc097f43cd91a67003639/4ab7173f-7884-4fe3-872f-32c01d77de2a.jpg"
        }, {
            "id": "bb8ac90b-f48a-4a1c-8cba-0c05d26f1b47",
            "shape": "center_square",
            "fileName": "bb8ac90b-f48a-4a1c-8cba-0c05d26f1b47.jpg",
            "extension": "jpg",
            "processedFiles": [{
                "width": 640,
                "height": 640,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/640x640_bb8ac90b-f48a-4a1c-8cba-0c05d26f1b47.jpg"
            }, {
                "width": 320,
                "height": 320,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/320x320_bb8ac90b-f48a-4a1c-8cba-0c05d26f1b47.jpg"
            }, {
                "width": 172,
                "height": 172,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/172x172_bb8ac90b-f48a-4a1c-8cba-0c05d26f1b47.jpg"
            }, {
                "width": 84,
                "height": 84,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/84x84_bb8ac90b-f48a-4a1c-8cba-0c05d26f1b47.jpg"
            }],
            "url": "http://images.coupling.app/52cfc097f43cd91a67003639/bb8ac90b-f48a-4a1c-8cba-0c05d26f1b47.jpg"
        }, {
            "id": "dabe1c27-f186-48f2-807f-8a68e3831fe9",
            "shape": "center_square",
            "fileName": "dabe1c27-f186-48f2-807f-8a68e3831fe9.jpg",
            "extension": "jpg",
            "processedFiles": [{
                "width": 640,
                "height": 640,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/640x640_dabe1c27-f186-48f2-807f-8a68e3831fe9.jpg"
            }, {
                "width": 320,
                "height": 320,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/320x320_dabe1c27-f186-48f2-807f-8a68e3831fe9.jpg"
            }, {
                "width": 172,
                "height": 172,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/172x172_dabe1c27-f186-48f2-807f-8a68e3831fe9.jpg"
            }, {
                "width": 84,
                "height": 84,
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/84x84_dabe1c27-f186-48f2-807f-8a68e3831fe9.jpg"
            }],
            "url": "http://images.coupling.app/52cfc097f43cd91a67003639/dabe1c27-f186-48f2-807f-8a68e3831fe9.jpg"
        }, {
            "url": "http://images.coupling.app/52cfc097f43cd91a67003639/59263e9d-6d76-4f42-8c8e-b4cf635b03c7.jpg",
            "processedFiles": [{
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/640x640_59263e9d-6d76-4f42-8c8e-b4cf635b03c7.jpg",
                "height": 640,
                "width": 640
            }, {
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/320x320_59263e9d-6d76-4f42-8c8e-b4cf635b03c7.jpg",
                "height": 320,
                "width": 320
            }, {
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/172x172_59263e9d-6d76-4f42-8c8e-b4cf635b03c7.jpg",
                "height": 172,
                "width": 172
            }, {
                "url": "http://images.coupling.app/52cfc097f43cd91a67003639/84x84_59263e9d-6d76-4f42-8c8e-b4cf635b03c7.jpg",
                "height": 84,
                "width": 84
            }],
            "extension": "jpg",
            "fileName": "59263e9d-6d76-4f42-8c8e-b4cf635b03c7.jpg",
            "main": false,
            "ydistance_percent": 0.75,
            "yoffset_percent": 0.08554687,
            "xoffset_percent": 0,
            "id": "59263e9d-6d76-4f42-8c8e-b4cf635b03c7",
            "xdistance_percent": 1
        }],
        "birth_date_info": "fuzzy birthdate active, not displaying real birth_date"
    }, ... ]
}
