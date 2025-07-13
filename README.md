# AscendionAPITestFile

Section 2: API Test
I have used Postman for testing this.
First I navigated to page  : https://gorest.co.in
Steps to do in Postman:
1.	Open Postman and create a new collection.
2.	Pick the access token from here https://gorest.co.in/my-account/access-tokens#google_vignette
3.	Create a new post method.
4.	Select the authorisation as Bearer Token.
5.	Copy the authorisation from the above access token link and paste in authorisation bearer token.
6.	Hit the endpoint https://gorest.co.in/public/v2/users
7.	Add the below request payload.
{
  "name": "Simran Test",
  "gender": "female",
  "email": "11simran.test@ascendion.com",
  "status": "active"
}
8.	Hit the send button
9.	The response should have id present in it and should be a numeric value.
10.	Status should be either active or inactive.



Response Verification: 
{
    "id": 8003246,
    "name": "Simran Test",
    "email": "11simran.test@ascendion.com",
    "gender": "female",
    "status": "active"
}

//Here we can verify in Postman also if the id as numeric value is generated and I also use rest assured for verification like this.
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const body = pm.response.json();
pm.test("ID is numeric", () =>
    pm.expect(typeof body[0].id).to.eql("number"));

const first = pm.response.json()[0];
pm.test("First status is active/inactive", () =>
    pm.expect(["active","inactive"]).to.include(first.status));

    


    
}
