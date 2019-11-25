---
title: 'Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 41d9f0e53401bcd6b57b04a38e76af5ddb9fb4cc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976100"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="c71bf-102">Instrukcje: Tworzenie usługi zwracającej dowolne dane za pomocą modelu programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="c71bf-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="c71bf-103">Czasami deweloperzy muszą mieć pełną kontrolę nad sposobem zwracania danych z operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="c71bf-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="c71bf-104">Dzieje się tak w przypadku, gdy operacja usługi musi zwrócić dane w formacie nieobsługiwanym przez WCF.</span><span class="sxs-lookup"><span data-stu-id="c71bf-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="c71bf-105">W tym temacie omówiono korzystanie z modelu programowania HTTP sieci WEB w programie WCF w celu utworzenia takiej usługi.</span><span class="sxs-lookup"><span data-stu-id="c71bf-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="c71bf-106">Ta usługa ma jedną operację zwracającą strumień.</span><span class="sxs-lookup"><span data-stu-id="c71bf-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="c71bf-107">Aby zaimplementować kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="c71bf-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="c71bf-108">Zdefiniuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="c71bf-108">Define the service contract.</span></span> <span data-ttu-id="c71bf-109">Kontrakt jest nazywany `IImageServer` i ma jedną metodę o nazwie `GetImage`, która zwraca <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="c71bf-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="c71bf-110">Ponieważ metoda zwraca <xref:System.IO.Stream>, WCF zakłada, że operacja ma pełną kontrolę nad bajtami, które są zwracane przez operację usługi i nie ma żadnego formatowania dla zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="c71bf-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="c71bf-111">Zaimplementuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="c71bf-111">Implement the service contract.</span></span> <span data-ttu-id="c71bf-112">Kontrakt ma tylko jedną operację (`GetImage`).</span><span class="sxs-lookup"><span data-stu-id="c71bf-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="c71bf-113">Ta metoda generuje mapę bitową, a następnie zapisuje ją w <xref:System.IO.MemoryStream> w formacie jpg.</span><span class="sxs-lookup"><span data-stu-id="c71bf-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="c71bf-114">Następnie operacja zwraca ten strumień do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c71bf-114">The operation then returns that stream to the caller.</span></span>  
  
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
  
     <span data-ttu-id="c71bf-115">Zwróć uwagę na sekundę do ostatniego wiersza kodu: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="c71bf-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="c71bf-116">Spowoduje to ustawienie nagłówka typu zawartości na `"image/jpeg"`.</span><span class="sxs-lookup"><span data-stu-id="c71bf-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="c71bf-117">Mimo że ten przykład pokazuje, jak zwrócić plik. jpg, można go zmodyfikować w taki sposób, aby zwracał dowolny wymagany typ danych w dowolnym formacie.</span><span class="sxs-lookup"><span data-stu-id="c71bf-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="c71bf-118">Operacja musi pobierać lub generować dane, a następnie zapisywać je w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="c71bf-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="c71bf-119">Aby hostować usługę</span><span class="sxs-lookup"><span data-stu-id="c71bf-119">To host the service</span></span>  
  
1. <span data-ttu-id="c71bf-120">Utwórz aplikację konsolową do hostowania usługi.</span><span class="sxs-lookup"><span data-stu-id="c71bf-120">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2. <span data-ttu-id="c71bf-121">Utwórz zmienną do przechowywania adresu podstawowego dla usługi w ramach metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="c71bf-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="c71bf-122">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> dla usługi określającej klasę usługi i adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="c71bf-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="c71bf-123">Dodaj punkt końcowy przy użyciu <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="c71bf-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="c71bf-124">Otwórz hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="c71bf-124">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="c71bf-125">Poczekaj, aż użytkownik naciśnie klawisz ENTER, aby zakończyć działanie usługi.</span><span class="sxs-lookup"><span data-stu-id="c71bf-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="c71bf-126">Aby wywołać usługę nieprzetworzoną przy użyciu programu Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="c71bf-126">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="c71bf-127">Uruchom usługę, dlatego następujące dane wyjściowe powinny zostać wyświetlone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="c71bf-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="c71bf-128">Otwórz program Internet Explorer i wpisz `http://localhost:8000/Service/GetImage?width=50&height=40` powinien zostać wyświetlony żółty prostokąt z niebieską ukośną linią.</span><span class="sxs-lookup"><span data-stu-id="c71bf-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c71bf-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="c71bf-129">Example</span></span>  
 <span data-ttu-id="c71bf-130">Poniżej znajduje się kompletna lista kodu dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c71bf-130">The following is a complete listing of the code for this topic.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c71bf-131">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c71bf-131">Compiling the Code</span></span>  
  
- <span data-ttu-id="c71bf-132">Podczas kompilowania przykładowego odwołania do kodu system. ServiceModel. dll i system. ServiceModel. Web. dll.</span><span class="sxs-lookup"><span data-stu-id="c71bf-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71bf-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c71bf-133">See also</span></span>

- [<span data-ttu-id="c71bf-134">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="c71bf-134">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
