---
title: "Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 829e9f2bcf909bee41f53b4b7cabbb0803e77963
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="28afb-102">Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="28afb-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="28afb-103">Czasami deweloperzy musi mieć pełną kontrolę nad jak dane są zwracane z operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="28afb-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="28afb-104">Dotyczy to sytuacji, gdy operacji usługi musi zwrócić dane w formacie nie jest obsługiwana przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28afb-104">This is the case when a service operation must return data in a format not supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="28afb-105">W tym temacie omówiono przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu programowania pakietu sieci WEB HTTP do tworzenia takiej usługi.</span><span class="sxs-lookup"><span data-stu-id="28afb-105">This topic discusses using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="28afb-106">Ta usługa ma jedną operację, która zwraca strumienia.</span><span class="sxs-lookup"><span data-stu-id="28afb-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="28afb-107">Aby zaimplementować kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="28afb-107">To implement the service contract</span></span>  
  
1.  <span data-ttu-id="28afb-108">Definiowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="28afb-108">Define the service contract.</span></span> <span data-ttu-id="28afb-109">Kontrakt jest nazywany `IImageServer` i jedną metodę o nazwie `GetImage` zwracającą <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="28afb-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="28afb-110">Ponieważ metoda zwraca <xref:System.IO.Stream>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] założono, że operacja ma pełną kontrolę nad bajtów, które zostaną zwrócone z operacji usługi i dotyczy bez formatowania danych, która jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="28afb-110">Because the method returns a <xref:System.IO.Stream>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2.  <span data-ttu-id="28afb-111">Implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="28afb-111">Implement the service contract.</span></span> <span data-ttu-id="28afb-112">Kontrakt ma tylko jedną operację (`GetImage`).</span><span class="sxs-lookup"><span data-stu-id="28afb-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="28afb-113">Ta metoda generuje mapę bitową, a następnie zapisz go na <xref:System.IO.MemoryStream> w formacie jpg.</span><span class="sxs-lookup"><span data-stu-id="28afb-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="28afb-114">Następnie operacja zwraca strumieniu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="28afb-114">The operation then returns that stream to the caller.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="28afb-115">Zwróć uwagę drugiego do ostatniego wiersza kodu:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="28afb-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="28afb-116">To ustawienie nagłówek typu zawartości `"image/jpeg"`.</span><span class="sxs-lookup"><span data-stu-id="28afb-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="28afb-117">Chociaż ten przykład przedstawia sposób zwrócenia pliku jpg, może być modyfikowany do zwrócenia dowolnego typu danych, który jest wymagany, w dowolnym formacie.</span><span class="sxs-lookup"><span data-stu-id="28afb-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="28afb-118">Operacja musi pobrać lub wygenerowane dane i zapisać go do strumienia.</span><span class="sxs-lookup"><span data-stu-id="28afb-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="28afb-119">Do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="28afb-119">To host the service</span></span>  
  
1.  <span data-ttu-id="28afb-120">Utwórz aplikację konsoli do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="28afb-120">Create a console application to host the service.</span></span>  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  <span data-ttu-id="28afb-121">Utwórz zmienną do przechowywania adres podstawowy usługi w ramach `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="28afb-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  <span data-ttu-id="28afb-122">Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienia klasy usługi i adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="28afb-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4.  <span data-ttu-id="28afb-123">Dodawanie punktu końcowego za pomocą <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="28afb-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  <span data-ttu-id="28afb-124">Otworzyć hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="28afb-124">Open the service host.</span></span>  
  
    ```  
    host.Open()  
    ```  
  
6.  <span data-ttu-id="28afb-125">Poczekaj, aż użytkownik naciśnie klawisz ENTER, aby zakończyć usługi.</span><span class="sxs-lookup"><span data-stu-id="28afb-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="28afb-126">Do wywołania tej usługi pierwotnych przy użyciu programu Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="28afb-126">To call the raw service using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="28afb-127">Uruchom usługę, powinny zostać wyświetlone następujące dane wyjściowe z usługi.</span><span class="sxs-lookup"><span data-stu-id="28afb-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2.  <span data-ttu-id="28afb-128">Otwórz program Internet Explorer, a następnie wpisz w `http://localhost:8000/Service/GetImage?width=50&height=40` powinna zostać wyświetlona żółta prostokąt z niebieskim linii ukośnych za pomocą Centrum.</span><span class="sxs-lookup"><span data-stu-id="28afb-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28afb-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="28afb-129">Example</span></span>  
 <span data-ttu-id="28afb-130">Poniżej znajduje się pełna lista kod w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="28afb-130">The following is a complete listing of the code for this topic.</span></span>  
  
```  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="28afb-131">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="28afb-131">Compiling the Code</span></span>  
  
-   <span data-ttu-id="28afb-132">W przypadku kompilowania kodu próbki kodu odwołania System.ServiceModel.dll i System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="28afb-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28afb-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28afb-133">See Also</span></span>  
 [<span data-ttu-id="28afb-134">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="28afb-134">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
