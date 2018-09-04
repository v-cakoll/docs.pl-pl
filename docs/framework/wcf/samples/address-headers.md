---
title: Nagłówki adresów
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: d2e38c674e0a3ea10df2e8363e90f4adf7edc9da
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503079"
---
# <a name="address-headers"></a><span data-ttu-id="4b664-102">Nagłówki adresów</span><span class="sxs-lookup"><span data-stu-id="4b664-102">Address Headers</span></span>
<span data-ttu-id="4b664-103">W przykładzie nagłówki adresów pokazano, jak klienci parametry można przekazać odwołanie do usługi przy użyciu usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4b664-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b664-104">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4b664-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4b664-105">Specyfikacja WS-Addressing definiuje pojęcie odwołania do punktu końcowego jako sposób adresu określonego punktu końcowego usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4b664-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="4b664-106">W programie WCF, odwołania do punktu końcowego są modelowane przy użyciu `EndpointAddress` , klasa — `EndpointAddress` jest typem pola adres `ServiceEndpoint` klasy.</span><span class="sxs-lookup"><span data-stu-id="4b664-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>  
  
 <span data-ttu-id="4b664-107">Część model referencyjny punkt końcowy jest, że każde odwołanie może wykonywać niektóre parametry odwołań, dodających informacje identyfikacyjne dodatkowych.</span><span class="sxs-lookup"><span data-stu-id="4b664-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="4b664-108">W programie WCF, parametry te odwołania są modelowane jako wystąpień obiektu `AddressHeader` klasy.</span><span class="sxs-lookup"><span data-stu-id="4b664-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>  
  
 <span data-ttu-id="4b664-109">W tym przykładzie klient dodaje parametr przekazany przez odwołanie do `EndpointAddress` punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="4b664-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="4b664-110">Usługa szuka tego parametru odwołania i używa jej wartości w logice jego działania usługi "Hello".</span><span class="sxs-lookup"><span data-stu-id="4b664-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>  
  
## <a name="client"></a><span data-ttu-id="4b664-111">Klient</span><span class="sxs-lookup"><span data-stu-id="4b664-111">Client</span></span>  
 <span data-ttu-id="4b664-112">Dla klienta, aby wysyłać parametr przekazany przez odwołanie, należy dodać `AddressHeader` do `EndpointAddress` z `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="4b664-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="4b664-113">Ponieważ `EndpointAddress` klasy jest niezmienny, musi odbywać się modyfikacja adresu punktu końcowego przy użyciu `EndpointAddressBuilder` klasy.</span><span class="sxs-lookup"><span data-stu-id="4b664-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="4b664-114">Poniższy kod inicjuje to klientowi wysłanie parametr przekazany przez odwołanie jako część komunikatu.</span><span class="sxs-lookup"><span data-stu-id="4b664-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 <span data-ttu-id="4b664-115">Ten kod tworzy `EndpointAddressBuilder` przy użyciu oryginalnego `EndpointAddress` jako początkowej wartości.</span><span class="sxs-lookup"><span data-stu-id="4b664-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="4b664-116">Następnie dodaje adres nowoutworzonego nagłówka. wywołanie `CreateAddressHeadercreates` nagłówek o określonej nazwie, przestrzeni nazw i wartości.</span><span class="sxs-lookup"><span data-stu-id="4b664-116">It then adds a newly created address header; the call to `CreateAddressHeadercreates` a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="4b664-117">W tym miejscu wartość "John".</span><span class="sxs-lookup"><span data-stu-id="4b664-117">Here the value is "John".</span></span> <span data-ttu-id="4b664-118">Po dodaniu do konstruktora, nagłówek `ToEndpointAddress()` metoda konwertuje konstruktora (mutable) do adresu punktu końcowego (niezmiennego), która jest przypisana do pola Adres punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="4b664-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>  
  
 <span data-ttu-id="4b664-119">Teraz, kiedy klient wywołuje `Console.WriteLine(client.Hello());`, usługa jest w stanie uzyskać wartość tego parametru adresu jak widać na dane wyjściowe z klienta.</span><span class="sxs-lookup"><span data-stu-id="4b664-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>  
  
 `Hello, John`  
  
## <a name="server"></a><span data-ttu-id="4b664-120">Serwer</span><span class="sxs-lookup"><span data-stu-id="4b664-120">Server</span></span>  
 <span data-ttu-id="4b664-121">Wykonanie operacji usługi `Hello()` używa bieżącej `OperationContext` sprawdzić wartości nagłówków w wiadomości przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="4b664-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>  
  
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
  
 <span data-ttu-id="4b664-122">Kod wykonuje iterację na wszystkie nagłówki dla wiadomości przychodzących, szukasz nagłówki, które są parametrami odwołanie o określonej nazwie i.</span><span class="sxs-lookup"><span data-stu-id="4b664-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="4b664-123">W przypadku odnalezienia parametru odczytuje wartość parametru i zapisuje ją w zmiennej "id".</span><span class="sxs-lookup"><span data-stu-id="4b664-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4b664-124">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="4b664-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4b664-125">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b664-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4b664-126">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b664-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4b664-127">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b664-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4b664-128">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4b664-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4b664-129">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="4b664-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4b664-130">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="4b664-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4b664-131">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4b664-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a><span data-ttu-id="4b664-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b664-132">See Also</span></span>
