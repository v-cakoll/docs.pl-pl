---
title: 'Instrukcje: Inspekcja Windows Communication Foundation zdarzeń zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 186dd4a7fc2beae848e5cbd167a204352ee6ed4e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601299"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Instrukcje: Inspekcja Windows Communication Foundation zdarzeń zabezpieczeń
Windows Communication Foundation (WCF) umożliwia rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows, który można wyświetlić za pomocą Podgląd zdarzeń systemu Windows. W tym temacie wyjaśniono, jak skonfigurować aplikację tak, aby rejestrowała zdarzenia zabezpieczeń. Aby uzyskać więcej informacji na temat inspekcji WCF, zobacz [Inspekcja](auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Aby przeprowadzić inspekcję zdarzeń zabezpieczeń w kodzie  
  
1. Określ lokalizację dziennika inspekcji. W tym celu należy ustawić <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> Właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> klasy na jedną z <xref:System.ServiceModel.AuditLogLocation> wartości wyliczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation>Wyliczenie ma trzy wartości: `Application` , `Security` , lub `Default` . Wartość określa jeden z dzienników widocznych w Podgląd zdarzeń, dziennik zabezpieczeń lub dziennik aplikacji. W przypadku użycia `Default` wartości rzeczywisty dziennik będzie zależeć od systemu operacyjnego, w którym jest uruchomiona aplikacja. Jeśli inspekcja jest włączona i lokalizacja dziennika nie zostanie określona, domyślnie jest to `Security` Dziennik dla platform, które obsługują zapisywanie w dzienniku zabezpieczeń. w przeciwnym razie zapis w dzienniku zostanie zapisany `Application` . Tylko systemy Windows Server 2003 i Windows Vista domyślnie obsługują zapisywanie w dzienniku zabezpieczeń.  
  
2. Skonfiguruj typy zdarzeń do inspekcji. Można jednocześnie przeprowadzać inspekcję zdarzeń na poziomie usługi lub zdarzeń autoryzacji na poziomie wiadomości. W tym celu należy ustawić <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> Właściwość lub <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> Właściwość na jedną z <xref:System.ServiceModel.AuditLevel> wartości wyliczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Określ, czy pominąć lub uwidocznić błędy aplikacji dotyczące zdarzeń inspekcji dzienników. Ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> Właściwość na albo `true` `false` , jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Właściwość domyślna `SuppressAuditFailure` to `true` , więc Niepowodzenie inspekcji nie ma wpływu na aplikację. W przeciwnym razie jest zgłaszany wyjątek. W przypadku każdej pomyślnej inspekcji zostanie zapisany pełny ślad. W przypadku wszelkich niepowodzeń inspekcji, ślad jest zapisywana na poziomie błędu.  
  
4. Usuń istniejące <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekcji zachowań znalezionych w opisie <xref:System.ServiceModel.ServiceHost> . Dostęp do kolekcji zachowań uzyskuje się za pomocą <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> właściwości, która z kolei jest dostępna z <xref:System.ServiceModel.ServiceHostBase.Description%2A> właściwości. Następnie Dodaj nową <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do tej samej kolekcji, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Aby skonfigurować inspekcję w konfiguracji  
  
1. Aby skonfigurować inspekcję w konfiguracji, Dodaj [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element do [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) sekcji pliku Web. config. Następnie Dodaj [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) element i Ustaw różne atrybuty, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy i dodaje nową <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do kolekcji zachowań.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Ustawienie <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości na `true` , pomija wszelkie niepowodzenie generowania inspekcji zabezpieczeń (jeśli jest ustawiona na `false` , zgłaszany jest wyjątek). Jeśli jednak zostanie włączona następująca Właściwość **Ustawienia zabezpieczeń lokalnych** systemu Windows, Niepowodzenie generowania zdarzeń inspekcji spowoduje natychmiastowe wyłączenie systemu Windows:  
  
 **Inspekcja: zamknij system natychmiast, jeśli nie można rejestrować wyników inspekcji**  
  
 Aby ustawić właściwość, Otwórz okno dialogowe **Ustawienia zabezpieczeń lokalnych** . W obszarze **Ustawienia zabezpieczeń**kliknij pozycję **Zasady lokalne**. Następnie kliknij pozycję **Opcje zabezpieczeń**.  
  
 Jeśli <xref:System.ServiceModel.AuditLogLocation> Właściwość jest ustawiona na <xref:System.ServiceModel.AuditLogLocation.Security> i **Inspekcja dostępu do obiektów** nie jest ustawiona w **lokalnych zasadach zabezpieczeń**, zdarzenia inspekcji nie będą zapisywane w dzienniku zabezpieczeń. Zwróć uwagę, że nie jest zwracana żadna awaria, ale wpisy inspekcji nie są zapisywane w dzienniku zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Inspekcja](auditing-security-events.md)
