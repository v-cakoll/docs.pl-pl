---
title: 'Instrukcje: Tworzenie usługi wymagającej użycia sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: c7bcd0c08d00122df86d6682888907712f224a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>Instrukcje: Tworzenie usługi wymagającej użycia sesji
Sesje utworzyć stanu udostępnionego między co najmniej dwa punkty końcowe, które umożliwia przydatne funkcje, takie jak wywołania zwrotne, zabezpieczeń z wieloma przeskokami i skojarzenia między klientami i wystąpień usługi. Aby uzyskać więcej informacji o sesji w aplikacji Windows Communication Foundation (WCF), zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Aby określić, że kontrakt wymaga jego powiązanie obsługuje sesji  
  
1.  Tworzenie kontraktu usługi z co najmniej jedną operację. Na przykład sposobu tworzenia kontraktu usługi zobacz [porady: definiowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Modyfikowanie <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> które deklaruje kontrakt przez ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości albo:  
  
    -   <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> Jeśli tego kontraktu musi być uruchamiane w ramach sesji.  
  
    -   <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> Jeśli tego kontraktu mogą być uruchamiane w ramach sesji.  
  
    -   <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> Jeśli nie wolno uruchamiać tej Umowy w ramach sesji.  
  
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
