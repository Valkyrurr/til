- https://austinlasseter.medium.com/build-a-password-protected-website-using-aws-lambda-and-cloudfront-3743cc4d09b6
- https://stackoverflow.com/questions/55874983/basic-user-authentication-for-static-site-using-aws-s3-bucket
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-edge-how-it-works-tutorial.html  

        'use strict';
        exports.handler = (event, context, callback) => {
            // Get request and request headers
            const request = event.Records[0].cf.request;
            const headers = request.headers;

            // Configure authentication
            const authUser = 'authUserName'; // EDIT THIS
            const authPass = 'authUserPass'; // EDIT THIS   

            // Construct the Basic Auth string
            const authString = 'Basic ' + new Buffer(authUser + ':' + authPass).toString('base64');

            // Require Basic authentication
            if (typeof headers.authorization == 'undefined' || headers.authorization[0].value != authString) {
                const body = 'Unauthorized';
                const response = {
                    status: '401',
                    statusDescription: 'Unauthorized',
                    body: body,
                    headers: {
                        'www-authenticate': [{key: 'WWW-Authenticate', value:'Basic'}]
                    },
                };
            callback(null, response);
            }

            // Continue request processing if authentication passed
            callback(null, request);
        };
