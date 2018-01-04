---
title: "Porady: Tworzenie usługi czy akceptuje dowolne dane za pomocą Model programowania interfejsu REST usługi WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 170149f5a6c495b3f22b9fd30f79ecdda87789b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Porady: Tworzenie usługi czy akceptuje dowolne dane za pomocą Model programowania interfejsu REST usługi WCF
Czasami deweloperzy musi mieć pełną kontrolę nad jak dane są zwracane z operacji usługi. Dotyczy to sytuacji, gdy operacji usługi musi zwrócić dane w formacie nie jest obsługiwana przez[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. W tym temacie omówiono przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model programowania interfejsu REST, aby utworzyć usługę, która odbiera dowolne dane.  
  
### <a name="to-implement-the-service-contract"></a>Aby zaimplementować kontrakt usługi  
  
1.  Definiowanie kontraktu usługi. Operację, która odbiera dane dowolnego musi mieć parametr typu <xref:System.IO.Stream>. Ponadto ten parametr musi być tylko parametr przekazywany w treści żądania. Działanie opisane w tym przykładzie również przyjmuje parametr nazwy pliku. Ten parametr jest przekazywany w ramach adresu URL żądania. Można określić, że parametr jest przekazywany w adresie URL, określając <xref:System.UriTemplate> w <xref:System.ServiceModel.Web.WebInvokeAttribute>. W tym przypadku identyfikator URI używany do wywołania tej metody kończy się "UploadFile/niektóre-nazwa_pliku". Część szablon identyfikatora URI "{filename}" Określa, że parametr nazwy pliku dla operacji jest przekazywany w identyfikatorze URI używany do wywołania operacji.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2.  Implementowanie kontraktu usługi. Kontrakt ma tylko jedną metodę `UploadFile` odbierająca pliku dowolne dane w strumieniu. Operacja odczytuje strumienia liczby bajtów do odczytu, a następnie wyświetla nazwę pliku i liczba bajtów odczytanych.  
  
    ```csharp  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
    ```  
  
### <a name="to-host-the-service"></a>Do obsługi usługi  
  
1.  Utwórz aplikację konsoli do obsługi usługi.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2.  Utwórz zmienną do przechowywania adres podstawowy usługi w ramach `Main` metody.  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie usługi, który określa klasę usługi i adres podstawowy.  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4.  Dodawanie punktu końcowego, który określa kontrakt <xref:System.ServiceModel.WebHttpBinding>, i <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  Otworzyć hosta usługi. Usługa jest teraz gotowa do odbierania żądań.  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>Aby programowo wywołania tej usługi  
  
1.  Utwórz <xref:System.Net.HttpWebRequest> o identyfikatorze URI używany do wywołania tej usługi. W tym kodzie adres podstawowy jest połączona z `"/UploadFile/Text"`. `"UploadFile"` Część identyfikatora URI określa operacja do wywołania. `"Test.txt"` Część identyfikatora URI określa parametr nazwy pliku do przekazania do `UploadFile` operacji. Obie te elementy mapowania <xref:System.UriTemplate> dotyczą kontrakt operacji.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2.  Ustaw <xref:System.Net.HttpWebRequest.Method%2A> właściwość <xref:System.Net.HttpWebRequest> do `POST` i <xref:System.Net.HttpWebRequest.ContentType%2A> właściwości `"text/plain"`. Informuje usługi, czy kod jest wysyłanie danych i, że dane są w postaci zwykłego tekstu.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3.  Wywołanie <xref:System.Net.HttpWebRequest.GetRequestStream%2A> uzyskanie strumienia żądania tworzenia danych do wysyłania, zapisać danych do strumienia żądania i zamykać strumień.  
  
    ```csharp  
    Stream reqStream = req.GetRequestStream();  
    byte[] fileToSend = new byte[12345];  
    for (int i = 0; i < fileToSend.Length; i++)  
       {  
           fileToSend[i] = (byte)('a' + (i % 26));  
       }  
    reqStream.Write(fileToSend, 0, fileToSend.Length);  
    reqStream.Close();  
    ```  
  
4.  Pobrać odpowiedzi z usługi przez wywołanie metody <xref:System.Net.HttpWebRequest.GetResponse%2A> i wyświetlać dane odpowiedzi do konsoli.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5.  Zamknij hosta usługi.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista kodu w tym przykładzie.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Net;  
  
namespace ReceiveRawData  
{  
    [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Host opened");  
  
            HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
            req.Method = "POST";  
            req.ContentType = "text/plain";  
            Stream reqStream = req.GetRequestStream();  
            byte[] fileToSend = new byte[12345];  
            for (int i = 0; i < fileToSend.Length; i++)  
            {  
                fileToSend[i] = (byte)('a' + (i % 26));  
            }  
            reqStream.Write(fileToSend, 0, fileToSend.Length);  
            reqStream.Close();  
            HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
            Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Podczas kompilowania kodu odwołania System.ServiceModel.dll i System.ServiceModel.Web.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy UriTemplate i UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
