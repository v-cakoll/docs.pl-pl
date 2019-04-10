---
title: 'Instrukcje: Deklarowanie błędów w kontraktach usługi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 0e173f71201d5f98a04d2ad922469e4ff6666681
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327077"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Instrukcje: Deklarowanie błędów w kontraktach usługi
W zarządzanym kodzie są zgłaszane wyjątki, gdy wystąpią błędy. W aplikacjach Windows Communication Foundation (WCF) natomiast kontraktów usług określić informacje o błędach, które są zwracane do klientów przez zadeklarowanie błędach SOAP w kontrakcie usługi. Aby uzyskać przegląd relacji między wyjątków i błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Tworzenie kontraktu usługi, która określa protokołu SOAP  
  
1. Tworzenie kontraktu usługi, która zawiera co najmniej jedną operację. Aby uzyskać przykład, zobacz [jak: Definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2. Wybierz operację, można określić warunek błędu o tym, które klienci mogą oczekiwać otrzymywać powiadomienia. Aby zdecydować, których warunki błędów uzasadnienie, zwracając błędach SOAP dla klientów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
3. Zastosuj <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> wybranej operacji i przekazać typ usterki do serializacji do konstruktora. Aby uzyskać szczegółowe informacje na temat tworzenia i używania typów możliwych do serializacji, zobacz [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Poniższy przykład pokazuje, jak określić, że `SampleMethod` operacji może spowodować `GreetingFault`.  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4. Powtórz kroki 2 i 3 dla wszystkich operacji w kontrakcie, które komunikują się warunki błędu dla klientów.  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Implementowanie operację zwrócenia określonego protokołu SOAP  
 Po operacji określono, że określonego błędu protokołu SOAP mogą być zwracane (takie jak w poprzedniej procedurze) do komunikowania się warunek błędu dla aplikacji wywołującej, następnym krokiem jest do zaimplementowania tej specyfikacji.  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Throw określony błąd protokołu SOAP w operacji  
  
1. Gdy <xref:System.ServiceModel.FaultContractAttribute>— wystąpienia określonego błędu w przypadku operacji zgłosić nową <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> gdzie określony błąd protokołu SOAP jest parametrem typu. Poniższy przykład pokazuje, jak zgłaszać `GreetingFault` w `SampleMethod` pokazano w poprzedniej procedurze, a w poniższej sekcji kodu.  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia implementację jednej operacji, która określa `GreetingFault` dla `SampleMethod` operacji.  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
