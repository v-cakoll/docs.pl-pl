---
title: Nagłówki adresów
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 133826bbbea62b660bdcdd884ce657528ad30873
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576008"
---
# <a name="address-headers"></a><span data-ttu-id="74673-102">Nagłówki adresów</span><span class="sxs-lookup"><span data-stu-id="74673-102">Address Headers</span></span>

<span data-ttu-id="74673-103">W przykładach nagłówków adresów pokazano, jak klienci mogą przekazywać parametry odwołania do usługi przy użyciu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="74673-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>

> [!NOTE]
> <span data-ttu-id="74673-104">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="74673-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="74673-105">Specyfikacja WS-Addressing definiuje pojęcie odwołania do punktu końcowego jako sposób adresowania określonego punktu końcowego usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="74673-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="74673-106">W programie WCF odwołania do punktów końcowych są modelowane przy użyciu `EndpointAddress` klasy- `EndpointAddress` jest typem pola Address `ServiceEndpoint` klasy.</span><span class="sxs-lookup"><span data-stu-id="74673-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>

<span data-ttu-id="74673-107">Część modelu referencyjnego punktu końcowego polega na tym, że każde odwołanie może zawierać kilka parametrów referencyjnych, które dodają dodatkowe informacje identyfikacyjne.</span><span class="sxs-lookup"><span data-stu-id="74673-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="74673-108">W programie WCF te parametry odwołania są modelowane jako wystąpienia `AddressHeader` klasy.</span><span class="sxs-lookup"><span data-stu-id="74673-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>

<span data-ttu-id="74673-109">W tym przykładzie klient dodaje parametr Reference do `EndpointAddress` punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="74673-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="74673-110">Usługa szuka tego parametru odwołania i używa jego wartości w logice operacji usługi "Hello".</span><span class="sxs-lookup"><span data-stu-id="74673-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>

## <a name="client"></a><span data-ttu-id="74673-111">Klient</span><span class="sxs-lookup"><span data-stu-id="74673-111">Client</span></span>

<span data-ttu-id="74673-112">Aby klient mógł wysłać parametr referencyjny, musi dodać `AddressHeader` do `EndpointAddress` elementu `ServiceEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="74673-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="74673-113">Ponieważ `EndpointAddress` Klasa jest niezmienna, modyfikowanie adresu punktu końcowego musi być wykonywane przy użyciu `EndpointAddressBuilder` klasy.</span><span class="sxs-lookup"><span data-stu-id="74673-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="74673-114">Poniższy kod inicjuje klienta do wysłania parametru odwołania w ramach jego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="74673-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

<span data-ttu-id="74673-115">Kod tworzy `EndpointAddressBuilder` oryginalny `EndpointAddress` jako wartość początkową.</span><span class="sxs-lookup"><span data-stu-id="74673-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="74673-116">Następnie dodaje nowo utworzony nagłówek adresu; wywołanie `CreateAddressHeader` tworzenia nagłówka z określoną nazwą, przestrzenią nazw i wartością.</span><span class="sxs-lookup"><span data-stu-id="74673-116">It then adds a newly created address header; the call to `CreateAddressHeader` creates a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="74673-117">Oto wartość "Jan".</span><span class="sxs-lookup"><span data-stu-id="74673-117">Here the value is "John".</span></span> <span data-ttu-id="74673-118">Po dodaniu nagłówka do konstruktora `ToEndpointAddress()` Metoda konwertuje Konstruktor (mutable) z powrotem na adres punktu końcowego (niezmienny), który jest przypisywany z powrotem do pola adresu punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="74673-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>

<span data-ttu-id="74673-119">Teraz, gdy klient wywołuje `Console.WriteLine(client.Hello());` usługę, może uzyskać wartość tego parametru adresu, jak pokazano w wynikowym wyjściu klienta.</span><span class="sxs-lookup"><span data-stu-id="74673-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>

`Hello, John`

## <a name="server"></a><span data-ttu-id="74673-120">Serwer</span><span class="sxs-lookup"><span data-stu-id="74673-120">Server</span></span>

<span data-ttu-id="74673-121">Implementacja operacji usługi `Hello()` używa bieżącego `OperationContext` do sprawdzenia wartości nagłówków w komunikacie przychodzącym.</span><span class="sxs-lookup"><span data-stu-id="74673-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>

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

<span data-ttu-id="74673-122">Kod wykonuje iterację wszystkich nagłówków komunikatu przychodzącego, szukając nagłówków, które są parametrami odwołań o określonej nazwie i.</span><span class="sxs-lookup"><span data-stu-id="74673-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="74673-123">Po znalezieniu parametru odczytuje wartość parametru i zapisuje je w zmiennej "ID".</span><span class="sxs-lookup"><span data-stu-id="74673-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="74673-124">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="74673-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="74673-125">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="74673-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="74673-126">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="74673-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="74673-127">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="74673-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74673-128">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="74673-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="74673-129">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="74673-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="74673-130">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="74673-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74673-131">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="74673-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
