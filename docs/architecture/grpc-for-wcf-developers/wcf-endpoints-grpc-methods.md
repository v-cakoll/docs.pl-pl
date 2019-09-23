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
# <a name="wcf-endpoints-and-grpc-methods"></a>Punkty końcowe WCF i metody gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W programie WCF podczas pisania kodu aplikacji należy użyć jednej z następujących metod:

- Kod aplikacji można napisać w metodach klasy i dekorować z atrybutem [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .
- Deklarujesz interfejs dla usługi i dodajesz atrybuty [OperationContract](xref:System.ServiceModel.OperationContractAttribute) do interfejsu.

Na przykład, odpowiednik `greet.proto` WCF usługi Greeter może być zapisany w następujący sposób:

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

Rozdział 3 wykazał, że definicje komunikatów protobuf są używane do generowania klas danych. Deklaracje usług i metod są używane do generowania klas podstawowych, które dziedziczą z w celu zaimplementowania usługi. Wystarczy zadeklarować metody do zaimplementowania w `.proto` pliku, a kompilator generuje klasę bazową z metodami wirtualnymi, które należy przesłonić.

## <a name="operationcontract-properties"></a>Właściwości OperationContract

Atrybut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) ma właściwości do kontroli lub udoskonalania sposobu działania. Metody gRPC nie oferują tego typu formantu. W poniższej tabeli wymieniono te `OperationContract` właściwości oraz sposób ich działania (lub nie jest) w gRPC:

| `OperationContract`wartość | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | Identyfikator URI służący do identyfikowania operacji. gRPC `package`używa nazwy `service` i `rpc` z pliku.`.proto` |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Wszystkie metody usługi gRPC zwracają `Task` obiekty. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Zobacz uwagę poniżej. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Jednokierunkowe metody gRPC zwracają `Empty` wyniki lub używają przesyłania strumieniowego przez klienta. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Zobacz uwagę poniżej. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | Powiązane z protokołem SOAP, brak znaczenia w gRPC. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | Brak szyfrowania wiadomości; szyfrowanie sieciowe jest obsługiwane w warstwie transportowej (TLS za pośrednictwem protokołu HTTP/2). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | Powiązane z protokołem SOAP, brak znaczenia w gRPC. |

Właściwość umożliwia wskazanie, że metoda w ramach elementu [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) nie może być pierwszą metodą wywoływaną w ramach sesji. `IsInitiating` `IsTerminating` Właściwość powoduje, że serwer zamyka sesję po wywołaniu operacji (lub klienta, jeśli jest używany na kliencie wywołania zwrotnego). W gRPC strumienie są tworzone przez pojedyncze metody i zamknięte jawnie. Zobacz [gRPC Streaming](rpc-types.md#grpc-streaming).

Aby uzyskać więcej informacji na temat zabezpieczeń i szyfrowania gRPC, zobacz [rozdział 6](security.md).

>[!div class="step-by-step"]
>[Poprzedni](wcf-services-to-grpc-comparison.md)
>[Następny](wcf-bindings.md)
