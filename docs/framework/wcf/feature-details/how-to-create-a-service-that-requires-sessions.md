---
title: "Instrukcje: Tworzenie usługi wymagającej użycia sesji"
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
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e238598ccd33d9e6e77a2d09ea3b19fdefcefbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Instrukcje: Tworzenie usługi wymagającej użycia sesji
Sesje utworzyć stanu udostępnionego między co najmniej dwa punkty końcowe, które umożliwia przydatne funkcje, takie jak wywołania zwrotne, zabezpieczeń z wieloma przeskokami i skojarzenia między klientami i wystąpień usługi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Sesje w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Aby określić, że kontrakt wymaga jego powiązanie obsługuje sesji  
  
1.  Tworzenie kontraktu usługi z co najmniej jedną operację. Na przykład sposobu tworzenia kontraktu usługi zobacz [porady: definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Modyfikowanie <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> które deklaruje kontrakt przez ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości albo:  
  
    -   <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>Jeśli tego kontraktu musi być uruchamiane w ramach sesji.  
  
    -   <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType>Jeśli tego kontraktu mogą być uruchamiane w ramach sesji.  
  
    -   <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType>Jeśli nie wolno uruchamiać tej Umowy w ramach sesji.  
  
3.  Konfigurowanie punktu końcowego usługi do użycia powiązania, które obsługuje sesji. W poniższym przykładzie konfiguracji pokazano sposób użycia <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, który obsługuje WS`-`ReliableMessaging sesji.  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób określić wymaganie poziomie umowy sesji i przy użyciu pliku konfiguracji w celu spełnienia tego wymagania z <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> powiązania.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
