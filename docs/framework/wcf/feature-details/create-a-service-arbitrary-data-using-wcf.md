---
title: 'Porady: Tworzenie usługi czy akceptuje dowolne dane za pomocą Model programowania interfejsu REST usługi WCF'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: bc2643672743971da14c8bc4c75ac113f691bf4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="43fea-102">Porady: Tworzenie usługi czy akceptuje dowolne dane za pomocą Model programowania interfejsu REST usługi WCF</span><span class="sxs-lookup"><span data-stu-id="43fea-102">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>
<span data-ttu-id="43fea-103">Czasami deweloperzy musi mieć pełną kontrolę nad jak dane są zwracane z operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="43fea-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="43fea-104">Podczas operacji usługi muszą zwracać dane w formacie nieobsługiwane byWCF jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="43fea-104">This is the case when a service operation must return data in a format not supported byWCF.</span></span> <span data-ttu-id="43fea-105">W tym temacie omówiono, aby utworzyć usługę, która odbiera dowolne dane za pomocą Model programowania interfejsu REST usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="43fea-105">This topic discusses using the WCF REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="43fea-106">Aby zaimplementować kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="43fea-106">To implement the service contract</span></span>  
  
1.  <span data-ttu-id="43fea-107">Definiowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="43fea-107">Define the service contract.</span></span> <span data-ttu-id="43fea-108">Operację, która odbiera dane dowolnego musi mieć parametr typu <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="43fea-108">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="43fea-109">Ponadto ten parametr musi być tylko parametr przekazywany w treści żądania.</span><span class="sxs-lookup"><span data-stu-id="43fea-109">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="43fea-110">Działanie opisane w tym przykładzie również przyjmuje parametr nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="43fea-110">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="43fea-111">Ten parametr jest przekazywany w ramach adresu URL żądania.</span><span class="sxs-lookup"><span data-stu-id="43fea-111">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="43fea-112">Można określić, że parametr jest przekazywany w adresie URL, określając <xref:System.UriTemplate> w <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="43fea-112">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="43fea-113">W tym przypadku identyfikator URI używany do wywołania tej metody kończy się "UploadFile/niektóre-nazwa_pliku".</span><span class="sxs-lookup"><span data-stu-id="43fea-113">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="43fea-114">Część szablon identyfikatora URI "{filename}" Określa, że parametr nazwy pliku dla operacji jest przekazywany w identyfikatorze URI używany do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="43fea-114">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2.  <span data-ttu-id="43fea-115">Implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="43fea-115">Implement the service contract.</span></span> <span data-ttu-id="43fea-116">Kontrakt ma tylko jedną metodę `UploadFile` odbierająca pliku dowolne dane w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="43fea-116">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="43fea-117">Operacja odczytuje strumienia liczby bajtów do odczytu, a następnie wyświetla nazwę pliku i liczba bajtów odczytanych.</span><span class="sxs-lookup"><span data-stu-id="43fea-117">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
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
  
### <a name="to-host-the-service"></a><span data-ttu-id="43fea-118">Do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="43fea-118">To host the service</span></span>  
  
1.  <span data-ttu-id="43fea-119">Utwórz aplikację konsoli do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="43fea-119">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2.  <span data-ttu-id="43fea-120">Utwórz zmienną do przechowywania adres podstawowy usługi w ramach `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="43fea-120">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  <span data-ttu-id="43fea-121">Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie usługi, który określa klasę usługi i adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="43fea-121">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4.  <span data-ttu-id="43fea-122">Dodawanie punktu końcowego, który określa kontrakt <xref:System.ServiceModel.WebHttpBinding>, i <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="43fea-122">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  <span data-ttu-id="43fea-123">Otworzyć hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="43fea-123">Open the service host.</span></span> <span data-ttu-id="43fea-124">Usługa jest teraz gotowa do odbierania żądań.</span><span class="sxs-lookup"><span data-stu-id="43fea-124">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="43fea-125">Aby programowo wywołania tej usługi</span><span class="sxs-lookup"><span data-stu-id="43fea-125">To call the service programmatically</span></span>  
  
1.  <span data-ttu-id="43fea-126">Utwórz <xref:System.Net.HttpWebRequest> o identyfikatorze URI używany do wywołania tej usługi.</span><span class="sxs-lookup"><span data-stu-id="43fea-126">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="43fea-127">W tym kodzie adres podstawowy jest połączona z `"/UploadFile/Text"`.</span><span class="sxs-lookup"><span data-stu-id="43fea-127">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="43fea-128">`"UploadFile"` Część identyfikatora URI określa operacja do wywołania.</span><span class="sxs-lookup"><span data-stu-id="43fea-128">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="43fea-129">`"Test.txt"` Część identyfikatora URI określa parametr nazwy pliku do przekazania do `UploadFile` operacji.</span><span class="sxs-lookup"><span data-stu-id="43fea-129">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="43fea-130">Obie te elementy mapowania <xref:System.UriTemplate> dotyczą kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="43fea-130">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2.  <span data-ttu-id="43fea-131">Ustaw <xref:System.Net.HttpWebRequest.Method%2A> właściwość <xref:System.Net.HttpWebRequest> do `POST` i <xref:System.Net.HttpWebRequest.ContentType%2A> właściwości `"text/plain"`.</span><span class="sxs-lookup"><span data-stu-id="43fea-131">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="43fea-132">Informuje usługi, czy kod jest wysyłanie danych i, że dane są w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="43fea-132">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3.  <span data-ttu-id="43fea-133">Wywołanie <xref:System.Net.HttpWebRequest.GetRequestStream%2A> uzyskanie strumienia żądania tworzenia danych do wysyłania, zapisać danych do strumienia żądania i zamykać strumień.</span><span class="sxs-lookup"><span data-stu-id="43fea-133">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
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
  
4.  <span data-ttu-id="43fea-134">Pobrać odpowiedzi z usługi przez wywołanie metody <xref:System.Net.HttpWebRequest.GetResponse%2A> i wyświetlać dane odpowiedzi do konsoli.</span><span class="sxs-lookup"><span data-stu-id="43fea-134">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5.  <span data-ttu-id="43fea-135">Zamknij hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="43fea-135">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="43fea-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="43fea-136">Example</span></span>  
 <span data-ttu-id="43fea-137">Poniżej znajduje się pełna lista kodu w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="43fea-137">The following is a complete listing of the code for this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="43fea-138">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="43fea-138">Compiling the Code</span></span>  
  
-   <span data-ttu-id="43fea-139">Podczas kompilowania kodu odwołania System.ServiceModel.dll i System.ServiceModel.Web.dll</span><span class="sxs-lookup"><span data-stu-id="43fea-139">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43fea-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43fea-140">See Also</span></span>  
 [<span data-ttu-id="43fea-141">Klasy UriTemplate i UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="43fea-141">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [<span data-ttu-id="43fea-142">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="43fea-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="43fea-143">Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="43fea-143">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
