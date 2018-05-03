# ImageAcquisitionAPI
ChironCode ImageAcquisition API can be used to send files to the ChironCloud Server. 

## Pre-Requisites

- Calling APIs from any language - Java, C#, JavaScript, Swift and others. 
- Basic CRUD operations over HTTP

### Feautres:

- Registration/Login - Authentication
- JWT Tokens for Authentication
- Direct Sync with S3 Bucket

#### Future works

- Use MQs to provide responses post-analysis
- Sophisticated Architecture to handle other client requests
- Bulk Upload of Data


### Documentation

1.Check Server Status: 

```
STATUS URL  - http://chironapi.chironx.cloud/api/chironx/status
```

If the server is correctly configured and running, this will be the response:
```
    {
        status:200,
        message:"Server is Running"
    }
```

2. Authenticate:

```
AUTHENTICATE-URL - http://chironapi.chironx.cloud/api/chironx/authenticate/login
METHOD  - POST
Content-Type: application/x-www-form-urlencoded
email : "REGISTERED EMAIL"
hashedPassword:"REGISTERED PASSWORD"
```

Three responses are possible.
Scenario 1:
```
# IF THE EMAIL IS NOT REGISTERED
{
status:200,
message:"This email is not registered"
}
```
RESPONSE 2
```
# IF PASSWORD IS INCORRECT
{
status:200,
message:"This password is not correct."
 }

```
RESPONSE 3
```
# IF YOU ARE AUTHENTICATED SUCCESSFULLY
{
 status:200,
 token:token,
 message:"You are logged in successfully",
 }
```
# IMPORTANT
```
Note and store the token received in this response.
```

3. BULK UPLOAD OF IMAGES
```
URL - http://chironapi.chironx.cloud/api/chironx/bulkupload/images
METHOD - POST 
REQUEST-HEADER - Authorization: BEARER "TOKEN"
Content-Type - multipart/form-data
Data : FILES, KEY = "images"
```

### Post Successful Upload
```
{
status:200,
message:"Files are  uploaded"
}
```


## Built With

* [EXPRESS] WEB FRAMEWORK
* [MULTER] FILE UPLOADS
* [AWS-SDK] FOR S3 UPLOADS


## Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

(c) ChironX | Advenio TecnoSys Pvt. Ltd.

Maintainer: Shubham Rana | shubham@chironx.ai

SOS: Rito Maitra | rito@chironx.ai

www.chironx.ai
