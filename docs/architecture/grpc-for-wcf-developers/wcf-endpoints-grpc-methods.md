---
title: Punkty końcowe WCF i metody gRPC — gRPC dla deweloperów WCF
description: Porównanie punktów końcowych WCF zadeklarowanych z atrybutami ServiceContract i OperationContract oraz metodami gRPC zadeklarowanymi w protobuf
ms.date: 09/02/2019
ms.openlocfilehash: 1bc6ecbc73bfc0a58393e4c28672b897ed6f2f15
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503431"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="b2c3e-103">Punkty końcowe WCF i metody gRPC</span><span class="sxs-lookup"><span data-stu-id="b2c3e-103">WCF endpoints and gRPC methods</span></span>

<span data-ttu-id="b2c3e-104">W Windows Communication Foundation (WCF) podczas pisania kodu aplikacji należy użyć jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="b2c3e-104">In Windows Communication Foundation (WCF), when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="b2c3e-105">Kod aplikacji można napisać w metodach klasy i dekorować z atrybutem [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="b2c3e-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="b2c3e-106">Deklarujesz interfejs dla usługi i dodajesz atrybuty [OperationContract](xref:System.ServiceModel.OperationContractAttribute) do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="b2c3e-107">Na przykład w programie WCF odpowiednikiem usługi `greet.proto` Greeter można napisać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b2c3e-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="b2c3e-108">Rozdział 3 wykazał, że definicje komunikatów protobuf są używane do generowania klas danych.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="b2c3e-109">Deklaracje usług i metod są używane do generowania klas podstawowych, które dziedziczą z w celu zaimplementowania usługi.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="b2c3e-110">Wystarczy zadeklarować metody do zaimplementowania w pliku `.proto`, a kompilator generuje klasę bazową z metodami wirtualnymi, które należy przesłonić.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods that you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="b2c3e-111">Właściwości OperationContract</span><span class="sxs-lookup"><span data-stu-id="b2c3e-111">OperationContract properties</span></span>

<span data-ttu-id="b2c3e-112">Atrybut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) ma właściwości do kontroli lub udoskonalania sposobu działania.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="b2c3e-113">Metody gRPC nie oferują tego typu formantu.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-113">gRPC methods don't offer this type of control.</span></span> <span data-ttu-id="b2c3e-114">W poniższej tabeli wymieniono `OperationContract` właściwości i opisano, w jaki sposób funkcje określone przez nich są (lub nie są) obsługiwane w programie gRPC:</span><span class="sxs-lookup"><span data-stu-id="b2c3e-114">The following table lists those `OperationContract` properties and describes how the functionality that they specify is (or isn't) dealt with in gRPC:</span></span>

| <span data-ttu-id="b2c3e-115">`OperationContract` Właściwość</span><span class="sxs-lookup"><span data-stu-id="b2c3e-115">`OperationContract` property</span></span> | <span data-ttu-id="b2c3e-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="b2c3e-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="b2c3e-117">Identyfikator URI identyfikuje operację.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-117">A URI identifies the operation.</span></span> <span data-ttu-id="b2c3e-118">gRPC używa nazwy `package`, `service`i `rpc` z pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-118">gRPC uses the name of `package`, `service`, and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="b2c3e-119">Wszystkie metody usługi gRPC zwracają `Task` obiektów.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="b2c3e-120">Zapoznaj się z akapitem poniżej tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-120">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="b2c3e-121">Jednokierunkowe metody gRPC zwracają wyniki `Empty` lub używają przesyłania strumieniowego przez klienta.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="b2c3e-122">Zapoznaj się z akapitem poniżej tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-122">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="b2c3e-123">Ta właściwość jest powiązana z protokołem SOAP i nie ma znaczenia w gRPC.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-123">This property is SOAP related and has no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="b2c3e-124">Brak szyfrowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-124">There's no message encryption.</span></span> <span data-ttu-id="b2c3e-125">Szyfrowanie sieciowe jest obsługiwane w warstwie transportowej (TLS za pośrednictwem protokołu HTTP/2).</span><span class="sxs-lookup"><span data-stu-id="b2c3e-125">Network encryption is handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="b2c3e-126">Ta właściwość jest powiązana z protokołem SOAP i nie ma znaczenia w gRPC.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-126">This property is SOAP related and has no meaning in gRPC.</span></span> |

<span data-ttu-id="b2c3e-127">Właściwość `IsInitiating` umożliwia wskazanie, że metoda w ramach elementu [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) nie może być pierwszą metodą wywoływaną w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-127">The `IsInitiating` property lets you indicate that a method within [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="b2c3e-128">Właściwość `IsTerminating` powoduje, że serwer zamyka sesję po wywołaniu operacji (lub kliencie, jeśli właściwość jest używana na kliencie wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="b2c3e-128">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if the property is used on a callback client).</span></span> <span data-ttu-id="b2c3e-129">W gRPC strumienie są tworzone przez pojedyncze metody i zamknięte jawnie.</span><span class="sxs-lookup"><span data-stu-id="b2c3e-129">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="b2c3e-130">Zobacz [gRPC Streaming](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="b2c3e-130">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="b2c3e-131">Aby uzyskać więcej informacji na temat zabezpieczeń i szyfrowania gRPC, zobacz [rozdział 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="b2c3e-131">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b2c3e-132">[Poprzednie](wcf-services-to-grpc-comparison.md)
>[dalej](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b2c3e-132">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
