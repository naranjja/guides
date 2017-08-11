# MongoDB for Google Cloud Platform
This is a guide for creating a MongoDB instance on Google Cloud Platform that is publicly accesible from anywhere.

* First, visit the [Google Cloud Platform Console](https://console.cloud.google.com).
* Sign in, create an account, then create a project.
* Next, visit [Bitnami's MongoDB Instance page](https://console.cloud.google.com/launcher/details/bitnami-launchpad/mongodb) and launch one.

![Image](/img/create-mongodb-gcp-1.png)

* Set the desired settings and click on **Deploy**. This will take you to the Deployment Manager and have you waiting a couple of minutes while everything gets set up. Take note of the **Admin user** and **Admin password** of the instance once they are ready.

![Image](/img/create-mongodb-gcp-2.png)

* Now, visit the [Compute Engine](https://console.cloud.google.com/compute/instances) and take note of the external IP assigned to the instance.

![Image](/img/create-mongodb-gcp-3.png)

* This concludes the setting up of the instance. You might also want to [make the external IP static](https://cloud.google.com/compute/docs/ip-addresses/reserve-static-external-ip-address#promote_ephemeral_ip) in order to include it in code.

* To check the connection and authentication, we will use Robo 3T as our MongoDB database visualizer. You can download it [here](https://robomongo.org/download).

* Open Robo 3T and choose to **Create** a new connection.

![Image](/img/create-mongodb-gcp-5.png)

* Give it a name, and type in the external IP address.

![Image](/img/create-mongodb-gcp-6.png)

* Next, click on **Authentication**. Leave the default database as `admin` and the authentication mechanism as `SCRAM-SHA-1`. Add the username and password observed before.

![Image](/img/create-mongodb-gcp-7.png)

* Click on **Save** and then connect to the instance. It will take some seconds to authenticate and connect.

* Now we will try to insert a document to a test database using PyMongo, the MongoDB driver for Python. First, install Python from [here](https://www.python.org/downloads/) and run `pip install pymongo` on some command prompt.

* Next, run `python` and type in the following lines. The `MongoClient` function receives a URI with the following structure: `mongodb://user:pass@external-ip`. The selections (i.e. `['animals']['domesticated']`) after the function refer to the database name and collection respectively.

```python
>>> from pymongo import MongoClient
>>> collection = MongoClient('mongodb://root:e7veSxdv@35.202.18.69')['animals']['domesticated']
>>> collection.insert_one({ 'name': 'dog', 'genus': 'canis' })
>>> collection.insert_one({ 'name': 'cat', 'genus': 'felis' })
>>>
```

* This performs two inserts on the `domesticated` collection. You may check this through Robo 3T.

![Image](/img/create-mongodb-gcp-8.png)
