---
title: Punkty końcowe WCF i metody gRPC — gRPC dla deweloperów WCF
description: Porównanie punktów końcowych WCF zadeklarowanych z atrybutami ServiceContract i OperationContract oraz metodami gRPC zadeklarowanymi w protobuf
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 08f2d0874417c0ca319b0c193e6108536376d693
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184065"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="493ca-103">Punkty końcowe WCF i metody gRPC</span><span class="sxs-lookup"><span data-stu-id="493ca-103">WCF endpoints and gRPC methods</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="493ca-104">W programie WCF podczas pisania kodu aplikacji należy użyć jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="493ca-104">In WCF, when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="493ca-105">Kod aplikacji można napisać w metodach klasy i dekorować z atrybutem [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="493ca-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="493ca-106">Deklarujesz interfejs dla usługi i dodajesz atrybuty [OperationContract](xref:System.ServiceModel.OperationContractAttribute) do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="493ca-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="493ca-107">Na przykład, odpowiednik `greet.proto` WCF usługi Greeter może być zapisany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="493ca-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="493ca-108">Rozdział 3 wykazał, że definicje komunikatów protobuf są używane do generowania klas danych.</span><span class="sxs-lookup"><span data-stu-id="493ca-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="493ca-109">Deklaracje usług i metod są używane do generowania klas podstawowych, które dziedziczą z w celu zaimplementowania usługi.</span><span class="sxs-lookup"><span data-stu-id="493ca-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="493ca-110">Wystarczy zadeklarować metody do zaimplementowania w `.proto` pliku, a kompilator generuje klasę bazową z metodami wirtualnymi, które należy przesłonić.</span><span class="sxs-lookup"><span data-stu-id="493ca-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="493ca-111">Właściwości OperationContract</span><span class="sxs-lookup"><span data-stu-id="493ca-111">OperationContract properties</span></span>

<span data-ttu-id="493ca-112">Atrybut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) ma właściwości do kontroli lub udoskonalania sposobu działania.</span><span class="sxs-lookup"><span data-stu-id="493ca-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="493ca-113">Metody gRPC nie oferują tego typu formantu.</span><span class="sxs-lookup"><span data-stu-id="493ca-113">gRPC methods don’t offer this type of control.</span></span> <span data-ttu-id="493ca-114">W poniższej tabeli wymieniono te `OperationContract` właściwości oraz sposób ich działania (lub nie jest) w gRPC:</span><span class="sxs-lookup"><span data-stu-id="493ca-114">The following table sets out those `OperationContract` properties and how the functionality they specify is (or isn’t) dealt with in gRPC:</span></span>

| <span data-ttu-id="493ca-115">`OperationContract`wartość</span><span class="sxs-lookup"><span data-stu-id="493ca-115">`OperationContract` property</span></span> | <span data-ttu-id="493ca-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="493ca-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="493ca-117">Identyfikator URI służący do identyfikowania operacji.</span><span class="sxs-lookup"><span data-stu-id="493ca-117">URI identifying the operation.</span></span> <span data-ttu-id="493ca-118">gRPC `package`używa nazwy `service` i `rpc` z pliku.`.proto`</span><span class="sxs-lookup"><span data-stu-id="493ca-118">gRPC uses the name of the `package`, `service` and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="493ca-119">Wszystkie metody usługi gRPC zwracają `Task` obiekty.</span><span class="sxs-lookup"><span data-stu-id="493ca-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="493ca-120">Zobacz uwagę poniżej.</span><span class="sxs-lookup"><span data-stu-id="493ca-120">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="493ca-121">Jednokierunkowe metody gRPC zwracają `Empty` wyniki lub używają przesyłania strumieniowego przez klienta.</span><span class="sxs-lookup"><span data-stu-id="493ca-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="493ca-122">Zobacz uwagę poniżej.</span><span class="sxs-lookup"><span data-stu-id="493ca-122">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="493ca-123">Powiązane z protokołem SOAP, brak znaczenia w gRPC.</span><span class="sxs-lookup"><span data-stu-id="493ca-123">SOAP-related, no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="493ca-124">Brak szyfrowania wiadomości; szyfrowanie sieciowe jest obsługiwane w warstwie transportowej (TLS za pośrednictwem protokołu HTTP/2).</span><span class="sxs-lookup"><span data-stu-id="493ca-124">No message encryption; network encryption handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="493ca-125">Powiązane z protokołem SOAP, brak znaczenia w gRPC.</span><span class="sxs-lookup"><span data-stu-id="493ca-125">SOAP-related, no meaning in gRPC.</span></span> |

<span data-ttu-id="493ca-126">Właściwość umożliwia wskazanie, że metoda w ramach elementu [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) nie może być pierwszą metodą wywoływaną w ramach sesji. `IsInitiating`</span><span class="sxs-lookup"><span data-stu-id="493ca-126">The `IsInitiating` property lets you indicate that a method within a [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="493ca-127">`IsTerminating` Właściwość powoduje, że serwer zamyka sesję po wywołaniu operacji (lub klienta, jeśli jest używany na kliencie wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="493ca-127">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if used on a callback client).</span></span> <span data-ttu-id="493ca-128">W gRPC strumienie są tworzone przez pojedyncze metody i zamknięte jawnie.</span><span class="sxs-lookup"><span data-stu-id="493ca-128">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="493ca-129">Zobacz [gRPC Streaming](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="493ca-129">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="493ca-130">Aby uzyskać więcej informacji na temat zabezpieczeń i szyfrowania gRPC, zobacz [rozdział 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="493ca-130">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="493ca-131">[Poprzedni](wcf-services-to-grpc-comparison.md)
>[Następny](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="493ca-131">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
