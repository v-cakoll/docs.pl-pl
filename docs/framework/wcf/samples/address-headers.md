---
title: Nagłówki adresów
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 276649c17a04822eb27eb4e3ed9cbe711b384edc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="address-headers"></a><span data-ttu-id="68343-102">Nagłówki adresów</span><span class="sxs-lookup"><span data-stu-id="68343-102">Address Headers</span></span>
<span data-ttu-id="68343-103">Przykładowy adres nagłówki pokazano, jak klientów można przekazywać parametrów odwołania do usługi przy użyciu usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="68343-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68343-104">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="68343-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="68343-105">Specyfikacja WS-Addressing definiuje pojęcie odwołanie do punktu końcowego sposobów rozwiązania danego punktu końcowego usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="68343-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="68343-106">W programie WCF, odwołania do punktu końcowego są modelowane przy użyciu `EndpointAddress` klasy - `EndpointAddress` jest typem pola adresu `ServiceEndpoint` klasy.</span><span class="sxs-lookup"><span data-stu-id="68343-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>  
  
 <span data-ttu-id="68343-107">Część model referencyjny punktu końcowego jest, że każde odwołanie może przenosić niektórych parametrów odwołania, które dodać informacje identyfikacyjne bardzo.</span><span class="sxs-lookup"><span data-stu-id="68343-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="68343-108">W programie WCF, te parametry odwołania są modelowane jako wystąpienia `AddressHeader` klasy.</span><span class="sxs-lookup"><span data-stu-id="68343-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>  
  
 <span data-ttu-id="68343-109">W tym przykładzie klient dodaje parametr odwołania do `EndpointAddress` punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="68343-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="68343-110">Usługa szuka tego parametru odwołania i używa jej wartość w logice jego operacji usługi "Hello".</span><span class="sxs-lookup"><span data-stu-id="68343-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>  
  
## <a name="client"></a><span data-ttu-id="68343-111">Klient</span><span class="sxs-lookup"><span data-stu-id="68343-111">Client</span></span>  
 <span data-ttu-id="68343-112">Dla klienta w celu wysyłania parametru odwołania, należy dodać `AddressHeader` do `EndpointAddress` z `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="68343-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="68343-113">Ponieważ `EndpointAddress` klasy nie można modyfikować, należy przeprowadzić modyfikacji adresu punktu końcowego za pomocą `EndpointAddressBuilder` klasy.</span><span class="sxs-lookup"><span data-stu-id="68343-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="68343-114">Poniższy kod inicjuje klientowi wysłanie parametru odwołania jako część komunikatu.</span><span class="sxs-lookup"><span data-stu-id="68343-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 <span data-ttu-id="68343-115">Kod tworzy `EndpointAddressBuilder` za pomocą `EndpointAddress` jako wartości początkowej.</span><span class="sxs-lookup"><span data-stu-id="68343-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="68343-116">Następnie dodaje nagłówek nowo utworzonego adresu; wywołanie `CreateAddressHeadercreates` nagłówka o określonej nazwie, przestrzeni nazw i wartości.</span><span class="sxs-lookup"><span data-stu-id="68343-116">It then adds a newly created address header; the call to `CreateAddressHeadercreates` a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="68343-117">W tym miejscu wartość to "Jan".</span><span class="sxs-lookup"><span data-stu-id="68343-117">Here the value is "John".</span></span> <span data-ttu-id="68343-118">Po dodaniu do konstruktora, nagłówek `ToEndpointAddress()` metoda konwertuje (modyfikowalne) konstruktora do adresu punktu końcowego (niezmienne), który jest przypisany do pola adresu punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="68343-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>  
  
 <span data-ttu-id="68343-119">Teraz, kiedy klient wywołuje `Console.WriteLine(client.Hello());`, usługa jest w stanie uzyskać wartość tego parametru adresu w dane wyjściowe klienta.</span><span class="sxs-lookup"><span data-stu-id="68343-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>  
  
 `Hello, John`  
  
## <a name="server"></a><span data-ttu-id="68343-120">Serwer</span><span class="sxs-lookup"><span data-stu-id="68343-120">Server</span></span>  
 <span data-ttu-id="68343-121">Wykonanie operacji usługi `Hello()` używa bieżącej `OperationContext` sprawdzić wartości nagłówków w komunikacie przychodzącym.</span><span class="sxs-lookup"><span data-stu-id="68343-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>  
  
```csharp   
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 <span data-ttu-id="68343-122">Ten kod przechodzi przez wszystkie nagłówki w komunikacie przychodzącym wyszukiwania dla nagłówków, które są parametry odwołanie o określonej nazwie i.</span><span class="sxs-lookup"><span data-stu-id="68343-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="68343-123">Po znalezieniu parametr wartość parametru odczytuje i zapisuje je w zmiennej "id".</span><span class="sxs-lookup"><span data-stu-id="68343-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="68343-124">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="68343-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="68343-125">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="68343-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="68343-126">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="68343-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="68343-127">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="68343-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68343-128">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="68343-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="68343-129">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="68343-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="68343-130">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="68343-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="68343-131">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="68343-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a><span data-ttu-id="68343-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68343-132">See Also</span></span>
