# Lab 02 - [AWS - Lambda Using AWS Console](https://learn.acloud.guru/handson/a0645bc3-152d-44c8-8706-bf309f4c846e)

1. Launch the A Cloud Guru lab using the link provided above
1. Click "Start Lab" - feel free to listen to the provided introduction if you wish
1. View the [Lab Diagram](https://labkeep-assets-production.s3.amazonaws.com/vz8dtkovldx13w11jxbttp0d1lxg?response-content-disposition=inline%3B%20filename%3D%22HOL%20-%20Creating%20a%20Lambda%20Function%20Using%20the%20AWS%20Console.png%22%3B%20filename%2A%3DUTF-8%27%27HOL%2520-%2520Creating%2520a%2520Lambda%2520Function%2520Using%2520the%2520AWS%2520Console.png&response-content-type=image%2Fpng&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAVKPCGNLNYCGRI2J5%2F20240910%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240910T215017Z&X-Amz-Expires=12154&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEFQaCXVzLWVhc3QtMSJHMEUCIQCiyBBzFRYkdbTIDZ5HFJS76%2FspqZNyeEfml6nZXcy8yQIgC697Yz4m6wrEury4ByKsWT8Sj5GTWO8Igp%2BWr7h5kPMqgwQIfBADGgwzNjYwODM0Njc5OTUiDItVjwrViH%2BhettKfSrgA9Guu07L6JhYt7FurlQV6rUfAYU1dNSX1XhWfsiZ8dDDhac%2BxUs6IhNLL6BDcPhpF9O7VbdGYEOqJcEVFW9f4QDPG9eHb8rd%2FI%2F9zyynao%2B4bFG%2F6K7XF%2FyA5G%2BWBfmsezyTWIQj5O4KaHCC0GSHizqvXKxlBEvecW6LriDoaCRKGXloGcGvmp3CPOJWmLiDXgr45o29%2BBMuwKPD8Fwh9bMkpoB5OrcHoGfNhlpxp%2Fi0q%2FK6yILzdsl9ZmkEnj3uRlgc5VFKOTZMP5fwMsK6RivtZn9X5d%2FhZgZdm4bxF%2FYm4HITA6yDXThCAoxz9yGhQNwjX3GU4VkL7Bq9%2Fgnqq%2BZZyYyjbUmlf3nzTRGmoEIytdEsklHWDUxdBXzyB8lTeeRtvMDspaAWD08RM3w0LFHL%2FhYvlHIKe2VnKd9i9%2FkGP4sePdbt5qQpv4lv2bj5kISQvIT4eRSsdz3YKWpB8kJvoQ7AW%2BlSgB%2BPPKseZkSTCBcg2OUVm8oRlRp%2Fv1mzGVcx5pMSzwXibafa9jD%2B2go4kAetN6%2FHqTsM%2B2Z0gSl6yq5W3S51WKDt5R5qfH1xoYj5%2FpB2PBXLA21YRc2CwkRB9AX4nE8m%2BPWWLo%2B%2Flojyu5zS0nUslLNXONRYpQjgHDCztIK3BjqlAfHk2jwckf3NAstS6PoOpa%2FuGE7ONYfIjnpaoJB%2BEzzmyybsfVK%2BMbaJ76DFh4uyEVOn%2FxdmrgHcfiiBJVk43dWBIGlVD52kTmwDWnRACKfisWUJn1qtn6tmdiD0OEjb3rOI5zFmOxue%2FdUjeIt3VjdiO%2BFz5HeRdz1aWpPLEosgMk87jKMwemYG6HbBzk1UFmAmu4QDMFQZ%2BzjiPEiAJ1O0FtVTAA%3D%3D&X-Amz-SignedHeaders=host&X-Amz-Signature=f8dfc0c5c68509d6390bcad3f2fbc0f598836df9242dfe30ad49b9a824717284) for a visual of what we will be building in this lab
1. Follow along with the step-by-step instructions provided in the "Guide" tab for the lab
1. After completing the described steps (and prior to checking logs for the function in CloudWatch), update your index.js code to something like the following:

```
const https = require('https');

exports.handler = async function(event) {
    let statusCode;
    await new Promise(function(resolve, reject) {
        https.get(event["url"], (res) => {
            statusCode = res.statusCode;
            resolve(statusCode);
        }).on("error", (e) => {
            reject(Error(e));
        });
    });
    console.log(statusCode);
    return statusCode;
};
```

6. Click "Deploy" to deploy the changes
6. Configure a new test event, give it the name of "myTestEvent2", and use the following for the "Event JSON" section of the test event:

```
{
    "url": "https://www.google.com"
}
```

8. Click "Save"
8. Click the dropdown arrow next to "Test" and make sure "myTestEvent2" is selected
8. Click "Test" and observe the results
8. Configure a new test event, give it the name of "myTestEvent3", and use the following for the "Event JSON" section of the test event:

```
{
    "url": "https://www.blah.com"
}
```

12. Click "Save"
12. Click the dropdown arrow next to "Test" and make sure "myTestEvent3" is selected
12. Click "Test" and observe the results
12. Click the "Configuration" tab (3 tabs over from the "Code" tab) and click "Permissions"
12. Under "Execution role" click the provided link for "Role name" - this will launch a new tab in IAM (Identity and Access Management) allowing you to view the properties for the role
12. Under "Permissions policies", click the "+" sign next to the listed policy to see the permissions associated to the Lambda by default
12. Continue with the outlined steps to view logs for the function in CloudWatch - notice the multiple successful executions as well as the unsuccessful execution
