---
title: 'Instrukcje: Inspekcja Windows Communication Foundation zdarzeń zabezpieczeń'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: b96c68c06099db2f396d16772cfaa8aee37390fe
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838016"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Instrukcje: Inspekcja Windows Communication Foundation zdarzeń zabezpieczeń
Windows Communication Foundation (WCF) umożliwia rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows, który można wyświetlić za pomocą Podgląd zdarzeń systemu Windows. W tym temacie wyjaśniono, jak skonfigurować aplikację tak, aby rejestrowała zdarzenia zabezpieczeń. Aby uzyskać więcej informacji na temat inspekcji WCF, zobacz [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Aby przeprowadzić inspekcję zdarzeń zabezpieczeń w kodzie  
  
1. Określ lokalizację dziennika inspekcji. W tym celu należy ustawić właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> klasy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> na jedną z wartości wyliczenia <xref:System.ServiceModel.AuditLogLocation>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     Wyliczenie <xref:System.ServiceModel.AuditLogLocation> ma trzy wartości: `Application`, `Security`lub `Default`. Wartość określa jeden z dzienników widocznych w Podgląd zdarzeń, dziennik zabezpieczeń lub dziennik aplikacji. W przypadku użycia wartości `Default` rzeczywisty dziennik będzie zależeć od systemu operacyjnego, w którym działa aplikacja. Jeśli inspekcja jest włączona, a lokalizacja dziennika nie jest określona, domyślnym dziennikiem `Security` dla platform, które obsługują zapisywanie w dzienniku zabezpieczeń; w przeciwnym razie nastąpi zapis do dziennika `Application`. Tylko [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i Windows Vista obsługują zapisywanie w dzienniku zabezpieczeń domyślnie.  
  
2. Skonfiguruj typy zdarzeń do inspekcji. Można jednocześnie przeprowadzać inspekcję zdarzeń na poziomie usługi lub zdarzeń autoryzacji na poziomie wiadomości. W tym celu należy ustawić właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> lub właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> na jedną z <xref:System.ServiceModel.AuditLevel> wartości wyliczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Określ, czy pominąć lub uwidocznić błędy aplikacji dotyczące zdarzeń inspekcji dzienników. Ustaw właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> na `true` lub `false`, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Domyślna właściwość `SuppressAuditFailure` jest `true`, w związku z czym Niepowodzenie inspekcji nie ma wpływu na aplikację. W przeciwnym razie jest zgłaszany wyjątek. W przypadku każdej pomyślnej inspekcji zostanie zapisany pełny ślad. W przypadku wszelkich niepowodzeń inspekcji, ślad jest zapisywana na poziomie błędu.  
  
4. Usuń istniejące <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekcji zachowań znalezionych w opisie <xref:System.ServiceModel.ServiceHost>. Dostęp do kolekcji zachowań uzyskuje się za pomocą właściwości <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>, która z kolei jest dostępna ze właściwości <xref:System.ServiceModel.ServiceHostBase.Description%2A>. Następnie Dodaj nowe <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do tej samej kolekcji, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Aby skonfigurować inspekcję w konfiguracji  
  
1. Aby skonfigurować inspekcję w konfiguracji, Dodaj [\<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu do sekcji [zachowania\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) pliku Web. config. Następnie Dodaj element [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) i Ustaw różne atrybuty, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy kod tworzy wystąpienie klasy <xref:System.ServiceModel.ServiceHost> i dodaje nowy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do kolekcji zachowań.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Ustawienie właściwości <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> na `true`powoduje pominięcie wszelkich niepowodzeń generowania inspekcji zabezpieczeń (Jeśli zostanie ustawiony na `false`, zgłaszany jest wyjątek). Jeśli jednak zostanie włączona następująca Właściwość **Ustawienia zabezpieczeń lokalnych** systemu Windows, Niepowodzenie generowania zdarzeń inspekcji spowoduje natychmiastowe wyłączenie systemu Windows:  
  
 **Inspekcja: Zamknij system natychmiast, jeśli nie można rejestrować inspekcji zabezpieczeń**  
  
 Aby ustawić właściwość, Otwórz okno dialogowe **Ustawienia zabezpieczeń lokalnych** . W obszarze **Ustawienia zabezpieczeń**kliknij pozycję **Zasady lokalne**. Następnie kliknij pozycję **Opcje zabezpieczeń**.  
  
 Jeśli właściwość <xref:System.ServiceModel.AuditLogLocation> jest ustawiona na <xref:System.ServiceModel.AuditLogLocation.Security> i **Inspekcja dostępu do obiektów** nie jest ustawiona w **lokalnych zasadach zabezpieczeń**, zdarzenia inspekcji nie będą zapisywane w dzienniku zabezpieczeń. Zwróć uwagę, że nie jest zwracana żadna awaria, ale wpisy inspekcji nie są zapisywane w dzienniku zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
