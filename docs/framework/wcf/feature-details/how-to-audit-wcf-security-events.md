---
title: 'Jak: Inspekcja zdarzeń zabezpieczeń programu Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 62d26b24b5d46427c1871fccf48b063c45781beb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185123"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Jak: Inspekcja zdarzeń zabezpieczeń programu Windows Communication Foundation
Program Windows Communication Foundation (WCF) umożliwia rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows, które można wyświetlać za pomocą Podglądu zdarzeń systemu Windows. W tym temacie wyjaśniono, jak skonfigurować aplikację, tak aby rejestrowała zdarzenia zabezpieczeń. Aby uzyskać więcej informacji na temat inspekcji WCF, zobacz [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Aby przeprowadzić inspekcję zdarzeń zabezpieczeń w kodzie  
  
1. Określ lokalizację dziennika inspekcji. Aby to zrobić, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> należy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> ustawić właściwość <xref:System.ServiceModel.AuditLogLocation> klasy na jedną z wartości wyliczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     Wyliczenie <xref:System.ServiceModel.AuditLogLocation> ma trzy `Application`wartości: , `Security`, lub `Default`. Wartość określa jeden z dzienników widocznych w Podglądzie zdarzeń, dziennik zabezpieczeń lub dziennik aplikacji. Jeśli używasz `Default` wartości, rzeczywisty dziennik będzie zależeć od systemu operacyjnego, na który działa aplikacja. Jeśli inspekcja jest włączona, a lokalizacja dziennika nie `Security` jest określona, domyślnym jest dziennik dla platform, które obsługują zapisywanie w dzienniku zabezpieczeń; w przeciwnym razie zostanie `Application` wpisać do dziennika. Tylko systemy Windows Server 2003 i Windows Vista domyślnie obsługują zapisywanie w dzienniku zabezpieczeń.  
  
2. Konfigurowanie typów zdarzeń do inspekcji. Można jednocześnie inspekcji zdarzeń na poziomie usługi lub zdarzenia autoryzacji na poziomie wiadomości. Aby to zrobić, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> należy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> ustawić właściwość <xref:System.ServiceModel.AuditLevel> lub właściwość do jednej z wartości wyliczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Określ, czy należy pominąć lub udostępnić błędy aplikacji dotyczące zdarzeń inspekcji dziennika. Ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwość na `true` `false`jedną lub , jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Domyślną `SuppressAuditFailure` właściwością jest `true`, dzięki czemu niepowodzenie inspekcji nie wpływa na aplikację. W przeciwnym razie jest zgłaszany wyjątek. Dla każdego pomyślnego audytu jest zapisywany pełny ślad. W przypadku niepowodzenia inspekcji śledzenia jest zapisywany na poziomie błędu.  
  
4. Usuń istniejące <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekcji zachowań znalezionych <xref:System.ServiceModel.ServiceHost>w opisie pliku . Kolekcja zachowania jest dostępna <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> dla właściwości, która z kolei <xref:System.ServiceModel.ServiceHostBase.Description%2A> jest dostępna z właściwości. Następnie dodaj <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> nowy do tej samej kolekcji, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Aby skonfigurować inspekcję w konfiguracji  
  
1. Aby skonfigurować inspekcję [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) w konfiguracji, dodaj element zachowania>do sekcji [ \<zachowania>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) pliku web.config. Następnie dodaj [ \<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element i ustawić różne atrybuty, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"
                serviceAuthorizationAuditLevel="None"
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2. Należy określić zachowanie usługi, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <services>  
        <service type="WCS.Samples.Service.Echo"
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy i <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> dodaje nowy do swojej kolekcji zachowań.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Ustawienie <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości `true`na , pomija wszelkie niepowodzenie generowania inspekcji `false`zabezpieczeń (jeśli jest ustawiona na , wyjątek). Jeśli jednak włączysz następującą właściwość **Ustawienia zabezpieczeń lokalnych** systemu Windows, niepowodzenie generowania zdarzeń inspekcji spowoduje natychmiastowe zamknięcie systemu Windows:  
  
 **Inspekcja: zamknij system natychmiast, jeśli nie można rejestrować wyników inspekcji**  
  
 Aby ustawić właściwość, otwórz okno dialogowe **Lokalne ustawienia zabezpieczeń.** W obszarze **Ustawienia zabezpieczeń**kliknij pozycję **Zasady lokalne**. Następnie kliknij pozycję **Opcje zabezpieczeń**.  
  
 Jeśli <xref:System.ServiceModel.AuditLogLocation> właściwość jest <xref:System.ServiceModel.AuditLogLocation.Security> ustawiona na i **Inspekcja dostępu do obiektu** nie jest ustawiona w **zasadach zabezpieczeń lokalnych,** zdarzenia inspekcji nie zostaną zapisane w dzienniku zabezpieczeń. Należy zauważyć, że nie jest zwracany błąd, ale wpisy inspekcji nie są zapisywane w dzienniku zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
