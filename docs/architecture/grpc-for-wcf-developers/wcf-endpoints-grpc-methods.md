---
title: Punkty końcowe WCF i metody gRPC — gRPC dla deweloperów WCF
description: Porównanie punktów końcowych WCF zadeklarowanych z atrybutami ServiceContract i OperationContract oraz metodami gRPC zadeklarowanymi w protobuf
ms.date: 09/02/2019
ms.openlocfilehash: 763862a363afc6aab72335050cf4822754816c7a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966934"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>Punkty końcowe WCF i metody gRPC

W programie WCF podczas pisania kodu aplikacji należy użyć jednej z następujących metod:

- Kod aplikacji można napisać w metodach klasy i dekorować z atrybutem [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .
- Deklarujesz interfejs dla usługi i dodajesz atrybuty [OperationContract](xref:System.ServiceModel.OperationContractAttribute) do interfejsu.

Na przykład w programie WCF odpowiednikiem usługi `greet.proto` Greeter można napisać w następujący sposób:

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

Rozdział 3 wykazał, że definicje komunikatów protobuf są używane do generowania klas danych. Deklaracje usług i metod są używane do generowania klas podstawowych, które dziedziczą z w celu zaimplementowania usługi. Po prostu deklarujesz metody do zaimplementowania w pliku `.proto`, a kompilator generuje klasę bazową z metodami wirtualnymi, które należy przesłonić.

## <a name="operationcontract-properties"></a>Właściwości OperationContract

Atrybut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) ma właściwości do kontroli lub udoskonalania sposobu działania. Metody gRPC nie oferują tego typu formantu. W poniższej tabeli przedstawiono te `OperationContract` właściwości oraz sposób ich działania (lub nie jest) w gRPC:

| `OperationContract` Właściwość | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | Identyfikator URI służący do identyfikowania operacji. gRPC używa nazwy `package`, `service` i `rpc` z pliku `.proto`. |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Wszystkie metody usługi gRPC zwracają `Task` obiektów. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Zobacz uwagę poniżej. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Jednokierunkowe metody gRPC zwracają wyniki `Empty` lub używają przesyłania strumieniowego przez klienta. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Zobacz uwagę poniżej. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | Powiązane z protokołem SOAP, brak znaczenia w gRPC. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | Brak szyfrowania wiadomości; szyfrowanie sieciowe jest obsługiwane w warstwie transportowej (TLS za pośrednictwem protokołu HTTP/2). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | Powiązane z protokołem SOAP, brak znaczenia w gRPC. |

Właściwość `IsInitiating` umożliwia wskazanie, że metoda w ramach elementu [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) nie może być pierwszą metodą wywoływaną w ramach sesji. Właściwość `IsTerminating` powoduje, że serwer zamyka sesję po wywołaniu operacji (lub klienta, jeśli jest używany na kliencie wywołania zwrotnego). W gRPC strumienie są tworzone przez pojedyncze metody i zamknięte jawnie. Zobacz [gRPC Streaming](rpc-types.md#grpc-streaming).

Aby uzyskać więcej informacji na temat zabezpieczeń i szyfrowania gRPC, zobacz [rozdział 6](security.md).

>[!div class="step-by-step"]
>[Poprzedni](wcf-services-to-grpc-comparison.md)
>[Następny](wcf-bindings.md)
