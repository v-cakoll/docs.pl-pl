---
title: 'Instrukcje: Tworzenie usługi wymagającej użycia sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 29c2a87daaf763a50aa657c9badc002ff2fa27e1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593337"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Instrukcje: Tworzenie usługi wymagającej użycia sesji
Sesje tworzą współużytkowany stan między dwoma lub więcej punktami końcowymi, które umożliwiają korzystanie z użytecznych funkcji, takich jak wywołania zwrotne, zabezpieczenia z wieloma przeskokami oraz skojarzenia między klientami a wystąpieniami usługi. Aby uzyskać więcej informacji na temat sesji w aplikacjach Windows Communication Foundation (WCF), zobacz [using Sessions](../using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Aby określić, że kontrakt wymaga powiązania z obsługą sesji  
  
1. Utwórz kontrakt usługi z co najmniej jedną operacją. Aby zapoznać się z przykładem sposobu tworzenia kontraktu usługi, zobacz [How to: define a Service Contract](../how-to-define-a-wcf-service-contract.md).  
  
2. Zmodyfikuj <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> , który deklaruje kontrakt, ustawiając <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> Właściwość na wartość:  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Jeśli ta umowa musi być uruchomiona w ramach sesji.  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Jeśli ten kontrakt można uruchomić w ramach sesji.  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Jeśli tego kontraktu nie można uruchomić w ramach sesji.  
  
3. Skonfiguruj punkt końcowy usługi tak, aby korzystał z powiązania, które obsługuje sesje. Poniższy przykład konfiguracji przedstawia użycie programu <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> , który obsługuje `-` sesję WS ReliableMessaging.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod pokazuje, jak określić wymaganie dotyczące sesji na poziomie kontraktu i użyć pliku konfiguracji do obsługi tego wymagania przy użyciu <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> powiązania.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
