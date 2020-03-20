---
title: 'Instrukcje: Tworzenie usługi wymagającej użycia sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184990"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Instrukcje: Tworzenie usługi wymagającej użycia sesji
Sesje utworzyć stan udostępniony między dwoma lub więcej punktów końcowych, który umożliwia przydatne funkcje, takie jak wywołania zwrotne, zabezpieczenia wielu przeskoków i skojarzenia między klientami i wystąpień usługi. Aby uzyskać więcej informacji na temat sesji w aplikacjach Windows Communication Foundation (WCF), zobacz [Korzystanie z sesji](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Aby określić, że umowa wymaga jej powiązania do obsługi sesji  
  
1. Utwórz umowę serwisową przy czym jednej operacji. Na przykład jak utworzyć umowę serwisową, zobacz [Jak: Definiowanie umowy serwisowej](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2. Zmodyfikuj, <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> który <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> deklaruje kontrakt, ustawiając właściwość na jedną z:  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>jeśli umowa ta musi być uruchamiana w ramach sesji.  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>jeśli ten kontrakt może być uruchomiony w ramach sesji.  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>jeśli umowa ta nie może być uruchamiana w ramach sesji.  
  
3. Skonfiguruj punkt końcowy usługi, aby używać powiązania, które obsługuje sesje. Poniższy przykład konfiguracji pokazuje <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>użycie programu ,`-`który obsługuje sesję WS ReliableMessaging.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod pokazuje, jak określić wymagania dotyczące sesji na poziomie <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> kontraktu i użyć pliku konfiguracji do obsługi tego wymagania z powiązaniem.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
