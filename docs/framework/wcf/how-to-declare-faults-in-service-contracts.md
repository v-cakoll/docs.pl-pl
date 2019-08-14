---
title: 'Instrukcje: Deklarowanie błędów w kontraktach usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 6f08ef6eb62b31b0969779d51d0a068145a23fc0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971965"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Instrukcje: Deklarowanie błędów w kontraktach usługi

W kodzie zarządzanym wyjątki są generowane, gdy wystąpią błędy. W aplikacjach Windows Communication Foundation (WCF), jednak kontrakty usługi określają, jakie informacje o błędzie są zwracane do klientów, deklarując błędy protokołu SOAP w kontrakcie usługi. Omówienie relacji między wyjątkami i błędami można znaleźć [w temacie określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Tworzenie kontraktu usługi określającego błąd protokołu SOAP

1. Utwórz kontrakt usługi, który zawiera co najmniej jedną operację. Aby zapoznać się z przykładem, zobacz [How to: Zdefiniuj kontrakt](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)usługi.

2. Wybierz operację, która może określić warunek błędu informujący o tym, które klienci mogą być powiadamiane. Aby określić, które warunki błędu uzasadniają zwrócenie błędów SOAP do klientów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).

3. <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> Zastosuj do wybranej operacji i przekaż typ błędu serializacji do konstruktora. Aby uzyskać szczegółowe informacje na temat tworzenia i używania typów możliwych do serializacji, zobacz [określanie transfer danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Poniższy przykład pokazuje, jak określić, że `SampleMethod` operacja może skutkować. `GreetingFault`

     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. Powtórz kroki 2 i 3 dla wszystkich operacji w kontrakcie, które komunikują się z warunkami błędów z klientami.

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Implementowanie operacji zwracającej określony błąd protokołu SOAP
 Po określeniu przez operację, że można zwrócić określony błąd protokołu SOAP (na przykład w poprzedniej procedurze) do przekazania warunku błędu do aplikacji wywołującej, następnym krokiem jest wdrożenie tej specyfikacji.

### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Zgłoś błąd protokołu SOAP w operacji

1. Gdy w operacji występuje określony warunek błędu, należy zgłosić nowe <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> miejsce, gdzie określony błąd protokołu SOAP jest parametrem typu. <xref:System.ServiceModel.FaultContractAttribute> Poniższy przykład pokazuje, `GreetingFault` jak zgłosić `SampleMethod` wynik w powyższej procedurze i w poniższej sekcji kodu.

     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje implementację pojedynczej operacji, która określa `GreetingFault` `SampleMethod` dla operacji.

[!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
