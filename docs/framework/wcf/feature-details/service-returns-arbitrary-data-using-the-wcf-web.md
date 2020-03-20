---
title: 'Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: c85ab6725876a2d523a18c817ce3fd89f0d2285a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184484"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="446cd-102">Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="446cd-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="446cd-103">Czasami deweloperzy muszą mieć pełną kontrolę nad tym, jak dane są zwracane z operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="446cd-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="446cd-104">Ma to miejsce, gdy operacja usługi musi zwracać dane w formacie nie obsługiwanym przez WCF.</span><span class="sxs-lookup"><span data-stu-id="446cd-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="446cd-105">W tym temacie omówiono przy użyciu WCF WEB HTTP Model programowania do tworzenia takiej usługi.</span><span class="sxs-lookup"><span data-stu-id="446cd-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="446cd-106">Ta usługa ma jedną operację, która zwraca strumień.</span><span class="sxs-lookup"><span data-stu-id="446cd-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="446cd-107">Aby wdrożyć umowę serwisową</span><span class="sxs-lookup"><span data-stu-id="446cd-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="446cd-108">Zdefiniuj umowę serwisową.</span><span class="sxs-lookup"><span data-stu-id="446cd-108">Define the service contract.</span></span> <span data-ttu-id="446cd-109">Kontrakt jest `IImageServer` wywoływany i `GetImage` ma jedną <xref:System.IO.Stream>metodę o nazwie, która zwraca .</span><span class="sxs-lookup"><span data-stu-id="446cd-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="446cd-110">Ponieważ metoda zwraca <xref:System.IO.Stream>, WCF zakłada, że operacja ma pełną kontrolę nad bajtami, które są zwracane z operacji usługi i nie stosuje formatowania do zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="446cd-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="446cd-111">Zaimplementuj umowę serwisową.</span><span class="sxs-lookup"><span data-stu-id="446cd-111">Implement the service contract.</span></span> <span data-ttu-id="446cd-112">Umowa ma tylko jedną`GetImage`operację ( ).</span><span class="sxs-lookup"><span data-stu-id="446cd-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="446cd-113">Ta metoda generuje mapę bitową, <xref:System.IO.MemoryStream> a następnie zapisać ją w formacie jpg.</span><span class="sxs-lookup"><span data-stu-id="446cd-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="446cd-114">Operacja następnie zwraca ten strumień do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="446cd-114">The operation then returns that stream to the caller.</span></span>  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     <span data-ttu-id="446cd-115">Zwróć uwagę na odsuwnik od drugiego do ostatniego wiersza kodu:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="446cd-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="446cd-116">Spowoduje to ustawienie nagłówka typu zawartości na `"image/jpeg"`.</span><span class="sxs-lookup"><span data-stu-id="446cd-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="446cd-117">Chociaż w tym przykładzie pokazano, jak zwrócić plik jpg, można go zmodyfikować, aby zwrócić dowolny typ danych, który jest wymagany, w dowolnym formacie.</span><span class="sxs-lookup"><span data-stu-id="446cd-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="446cd-118">Operacja musi pobrać lub wygenerować dane, a następnie zapisać je do strumienia.</span><span class="sxs-lookup"><span data-stu-id="446cd-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="446cd-119">Aby hostować usługę</span><span class="sxs-lookup"><span data-stu-id="446cd-119">To host the service</span></span>  
  
1. <span data-ttu-id="446cd-120">Utwórz aplikację konsoli do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="446cd-120">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. <span data-ttu-id="446cd-121">Utwórz zmienną do przechowywania adresu podstawowego usługi w ramach `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="446cd-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="446cd-122">Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie usługi określające klasę usługi i adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="446cd-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="446cd-123">Dodaj punkt końcowy <xref:System.ServiceModel.WebHttpBinding> za <xref:System.ServiceModel.Description.WebHttpBehavior>pomocą i .</span><span class="sxs-lookup"><span data-stu-id="446cd-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="446cd-124">Otwórz hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="446cd-124">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="446cd-125">Poczekaj, aż użytkownik naciśnie klawisz ENTER, aby zakończyć działanie usługi.</span><span class="sxs-lookup"><span data-stu-id="446cd-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="446cd-126">Aby wywołać usługę nieprzetworzoną przy użyciu programu Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="446cd-126">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="446cd-127">Uruchom usługę, powinny zostać wyświetlene następujące dane wyjściowe z usługi.</span><span class="sxs-lookup"><span data-stu-id="446cd-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="446cd-128">Otwórz program Internet `http://localhost:8000/Service/GetImage?width=50&height=40` Explorer i wpisz żółty prostokąt z niebieską ukośną linią przez środek.</span><span class="sxs-lookup"><span data-stu-id="446cd-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="446cd-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="446cd-129">Example</span></span>  
 <span data-ttu-id="446cd-130">Poniżej znajduje się pełna lista kodu dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="446cd-130">The following is a complete listing of the code for this topic.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="446cd-131">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="446cd-131">Compiling the Code</span></span>  
  
- <span data-ttu-id="446cd-132">Podczas kompilowania przykładowego kodu odwołania System.ServiceModel.dll i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="446cd-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446cd-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="446cd-133">See also</span></span>

- [<span data-ttu-id="446cd-134">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="446cd-134">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
