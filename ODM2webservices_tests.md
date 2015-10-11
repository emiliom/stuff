# ODM2 Web Services -- Initial tests

These web services are currently being developed by SDSC (Choonhan and Dave).

## ODM2REST API / web services
- https://github.com/ODM2/ODM2RESTfulWebServices
- ODM2 REST API's. Based on Django Swagger
  - "Production" (original alpha release): http://sis-devel.cloudapp.net/docs/
  - [New dev](https://github.com/ODM2/ODM2RESTfulWebServices/issues/1#issuecomment-132387462), based on my feedback 
  (below); only implemented on JSON response; untested: http://sis-devel.cloudapp.net:9090/docs/
- [Feedback on the alpha release - Part 1](https://github.com/ODM2/ODM2RESTfulWebServices/issues/1)
- [Illustrating the use of ODM2 REST web services with the ODM2 Marchantaria use case (ipython notebook)](http://nbviewer.ipython.org/github/BiG-CZ/BiG-CZ-Toolbox/blob/master/ipynotebooks/ODM2RESTdemo_MarchantariaUseCase.ipynb)

## ODM2 WOFpy WOF 1 endpoint
- https://github.com/ODM2/WOFpy
- From Choonhan: "David and I have worked on WOFpy service with ODM2. Currently, we have released WaterML1.0 format for REST and SOAP service on the github. We continue working on WaterML1.1 format as well so that we have a plan to release it." Test endpoints:
  - REST API: http://sis-devel.cloudapp.net:8080
  - SOAP API: http://sis-devel.cloudapp.net:8080/soap/wateroneflow.wsdl
