---
title: "Porady: deklarowanie błędów w kontraktach usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ebfe56a0e073534840ce81eebb64ce3f5db48a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Porady: deklarowanie błędów w kontraktach usług
W kodzie zarządzanym wyjątki są zgłaszane w przypadku wystąpienia błędów. W [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji, jednak kontraktów usług określ, jakie informacje o błędzie są zwracane do klientów przez zadeklarowanie błędach SOAP w kontrakcie usługi. Omówienie relacji między wyjątków i błędów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Tworzenie kontraktu usługi, która określa błędu protokołu SOAP  
  
1.  Tworzenie kontraktu usługi, który zawiera co najmniej jedną operację. Na przykład zobacz [porady: definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Wybierz operację, która może określony błąd o tym, które klientów można oczekiwać, że użytkownik jest powiadamiany. Aby zdecydować, które błędy justify zwracanie błędach SOAP dla klientów, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
3.  Zastosuj <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> wybranej operacji i przekazywania błędów można serializować typu konstruktora. Aby uzyskać szczegółowe informacje na temat tworzenia i używania typów możliwych do serializacji, zobacz [Określanie transferu danych w kontraktach usług](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Poniższy przykład przedstawia sposób określić, że `SampleMethod` operacji może spowodować `GreetingFault`.  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  Powtórz kroki 2 i 3 dla wszystkich operacji w kontrakcie, które komunikują się warunki błędów do klientów.  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Implementowanie operacji do zwrócenia błędu SOAP określona  
 Po operacji określił, że określonego błędu protokołu SOAP mogą być zwracane (na przykład w poprzedniej procedurze) do komunikacji warunek błędu, aby aplikacja wywołująca, następnym krokiem jest wdrożenie tej specyfikacji.  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Throw określonego błędu protokołu SOAP w operacji  
  
1.  Gdy <xref:System.ServiceModel.FaultContractAttribute>-wystąpienia określonego błędu w operacji zgłosić nową <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> przypadku parametr typu określony błąd protokołu SOAP. Poniższy przykład przedstawia sposób throw `GreetingFault` w `SampleMethod` pokazane w poprzedniej procedurze, a w poniższej sekcji kodu.  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia implementację jednej operacji, która określa `GreetingFault` dla `SampleMethod` operacji.  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
