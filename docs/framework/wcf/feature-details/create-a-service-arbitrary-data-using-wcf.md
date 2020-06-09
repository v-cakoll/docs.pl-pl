---
title: 'Instrukcje: tworzenie usługi przyjmującej dowolne dane w modelu programowania REST programu WCF'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: d908651f7815c102b45ea106f5bec4c07d869950
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601338"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Instrukcje: tworzenie usługi przyjmującej dowolne dane w modelu programowania REST programu WCF
Czasami deweloperzy muszą mieć pełną kontrolę nad sposobem zwracania danych z operacji usługi. Dzieje się tak w przypadku, gdy operacja usługi musi zwrócić dane w formacie nieobsługiwany byWCF. W tym temacie omówiono korzystanie z modelu programowania REST WCF w celu utworzenia usługi, która odbiera dowolne dane.  
  
### <a name="to-implement-the-service-contract"></a>Aby zaimplementować kontrakt usługi  
  
1. Zdefiniuj kontrakt usługi. Operacja, która odbiera dowolne dane, musi mieć parametr typu <xref:System.IO.Stream> . Ponadto ten parametr musi być jedynym parametrem przekazaną w treści żądania. Operacja opisana w tym przykładzie pobiera również parametr filename. Ten parametr jest przesyłany w adresie URL żądania. Można określić, że parametr w adresie URL jest przesyłany przez określenie elementu <xref:System.UriTemplate> w <xref:System.ServiceModel.Web.WebInvokeAttribute> . W takim przypadku identyfikator URI używany do wywołania tej metody zostanie zakończony "UploadFile/trochę-filename". Część "{filename}" szablonu identyfikatora URI Określa, że parametr filename dla operacji jest przesyłany w identyfikatorze URI używanym do wywoływania operacji.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. Zaimplementuj kontrakt usługi. Kontrakt ma tylko jedną metodę, `UploadFile` która odbiera plik dowolnych danych w strumieniu. Operacja odczytuje strumień zliczania bajtów odczytywanych, a następnie wyświetla nazwę pliku i liczbę odczytanych bajtów.  
  
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
  
### <a name="to-host-the-service"></a>Aby hostować usługę  
  
1. Utwórz aplikację konsolową do hostowania usługi.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. Utwórz zmienną do przechowywania adresu podstawowego dla usługi w ramach `Main` metody.  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie dla usługi, która określa klasę usługi i adres podstawowy.  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. Dodaj punkt końcowy, który określa kontrakt, <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior> .  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Otwórz hosta usługi. Usługa jest teraz gotowa do odbierania żądań.  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>Aby programowo wywołać usługę  
  
1. Utwórz obiekt <xref:System.Net.HttpWebRequest> o identyfikatorze URI używanym do wywoływania usługi. W tym kodzie adres podstawowy jest połączony z `"/UploadFile/Text"` . `"UploadFile"`Część identyfikatora URI Określa operację do wywołania. `"Test.txt"`Część identyfikatora URI Określa parametr filename, który ma zostać przekazany do `UploadFile` operacji. Oba te elementy są mapowane na <xref:System.UriTemplate> zastosowany do kontraktu operacji.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. Ustaw <xref:System.Net.HttpWebRequest.Method%2A> Właściwość <xref:System.Net.HttpWebRequest> na `POST` i <xref:System.Net.HttpWebRequest.ContentType%2A> Właściwość na `"text/plain"` . Oznacza to, że usługa wysyła dane przez kod, a dane są w postaci zwykłego tekstu.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. Wywołaj, <xref:System.Net.HttpWebRequest.GetRequestStream%2A> Aby pobrać strumień żądania, utworzyć dane do wysłania, zapisać je w strumieniu żądania i zamknąć strumień.  
  
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
  
4. Pobierz odpowiedź z usługi, wywołując <xref:System.Net.HttpWebRequest.GetResponse%2A> i wyświetlając dane odpowiedzi w konsoli.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. Zamknij hosta usługi.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się kompletna lista kodu dla tego przykładu.  
  
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
  
- Podczas kompilowania kodu referencyjnego system. ServiceModel. dll i system. ServiceModel. Web. dll  
  
## <a name="see-also"></a>Zobacz też

- [Klasy UriTemplate i UriTemplateTable](uritemplate-and-uritemplatetable.md)
- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)
- [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](wcf-web-http-programming-model-overview.md)
