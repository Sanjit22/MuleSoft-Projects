# Consume SOAP Web Services and stored the data in a different format : 

1.	Design the ***RAML*** for different Layers. 

2.	Consume the ***SOAP Web Services***.  We need to get the ***WSDL*** of the web service in order to consume it. You will use the ***Country Details web service***.

        http://webservices.oorsprong.org/websamples.countryinfo/CountryInfoService.wso?WSDL

3.	After consume the service, you process the data asynchronously. Asynchronous flows process the message in parallel to the triggered and triggering flow. One flow stored the data into a ***MongoDB database*** and another flow saves the data into a file of ***XML*** format. Collection name and the file name should be ***CountryDetails_CurrentTimeStamp*** like ***CountryDetails_2020-03-06-08-54-48*** and ***CountryDetails_2020-03-06-08-54-48.xml*** respectively.

    Format of data stored in ***MongoDB*** like-
    ```
    {
        "_id":{"$oid":"5e61eb430669040b0870f0d9"},
        "ISOCode":"IN",
        "CountryName":"India",
        "CapitalCity":"New Delhi",
        "PhoneCode":"91",
        "ContinentCode":"AS",
        "CurrencyISOCode":"INR",
        "CountryFlag":"http://www.oorsprong.org/WebSamples.CountryInfo/Flags/India.jpg",
        "Language":{
            "LanguageISOCode":"hin",
            "LanguageName":"Hindi"
        }
    }
    ```

    Format of data stored in ***File***(Using FTP) like-
    ```
    <?xml version='1.0' encoding='UTF-8'?>
    <FullCountryInfoResult>
        <ISOCode>IN</ISOCode>
        <CountryName>India</CountryName>
        <CapitalCity>New Delhi</CapitalCity>
        <PhoneCode>91</PhoneCode>
        <ContinentCode>AS</ContinentCode>
        <CurrencyISOCode>INR</CurrencyISOCode>
        <CountryFlag>http://www.oorsprong.org/WebSamples.CountryInfo/Flags/India.jpg</CountryFlag>
        <Language>
            <LanguageISOCode>hin</LanguageISOCode>
            <LanguageName>Hindi</LanguageName>
        </Language>
    </FullCountryInfoResult>
    ```
    
    End-user output looks like-
    ```
    {
        "ISOCode":"IN",
        "CountryName":"India",
        "CapitalCity":"New Delhi",
        "PhoneCode":"91",
        "ContinentCode":"AS",
        "CurrencyISOCode":"INR",
        "CountryFlag":"http://www.oorsprong.org/WebSamples.CountryInfo/Flags/India.jpg",
        "Language":{
            "LanguageISOCode":"hin",
            "LanguageName":"Hindi"
        }
    }
    ```

4.	Create an ***Experience-Layer*** which is defined to expose the end user to the API. So, we should define and implement the high-level logic in the API. The purpose of this API is to interact with the Process API and process the output to the end user with the process status.

