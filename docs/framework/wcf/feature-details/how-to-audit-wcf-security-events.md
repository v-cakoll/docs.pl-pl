---
title: 'Instrukcje: inspekcja zdarzeń zabezpieczeń systemu Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 35d884c0e772deafdaa2326a47903e90691f8106
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45969668"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Instrukcje: inspekcja zdarzeń zabezpieczeń systemu Windows Communication Foundation
Windows Communication Foundation (WCF) umożliwia rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń Windows, które można przeglądać za pomocą Podglądu zdarzeń Windows. W tym temacie wyjaśniono, jak skonfigurować aplikację tak, aby go dzienników zdarzeń zabezpieczeń. Aby uzyskać więcej informacji na temat inspekcji WCF, zobacz [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Inspekcja zdarzeń zabezpieczeń w kodzie  
  
1.  Określ lokalizację dziennika inspekcji. Aby to zrobić, należy ustawić <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> klasy do jednego z <xref:System.ServiceModel.AuditLogLocation> wartości wyliczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation> Wyliczenie ma trzy wartości: `Application`, `Security`, lub `Default`. Wartość określa jednym z dzienników, które są widoczne w Podglądzie zdarzeń, albo w dzienniku zabezpieczeń lub w dzienniku aplikacji. Jeśli używasz `Default` wartości rzeczywistej dziennika będzie zależeć od systemu operacyjnego, w której działa aplikacja na. Jeśli nie określono lokalizacji dziennika inspekcji jest włączona, wartość domyślna to `Security` dziennika dla platform, które obsługują pisanie w dzienniku zabezpieczeń; w przeciwnym razie będą zapisywane do `Application` dziennika. Tylko [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wv](../../../../includes/wv-md.md)] domyślnie obsługują zapisywanie w dzienniku zabezpieczeń.  
  
2.  Skonfiguruj typy zdarzeń inspekcji. Jednocześnie można przeprowadzać inspekcję uwierzytelnianie na poziomie komunikatu lub poziomu usługi zdarzenia. Aby to zrobić, należy ustawić <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> właściwości lub <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> jedną z właściwości <xref:System.ServiceModel.AuditLevel> wartości wyliczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  Określ, czy pominąć lub udostępnić błędów aplikacji dotyczące zdarzenia inspekcji w dzienniku. Ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości albo `true` lub `false`, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Wartość domyślna `SuppressAuditFailure` właściwość `true`, dzięki czemu Niepowodzenie inspekcji nie ma wpływu na aplikację. W przeciwnym razie jest zgłaszany wyjątek. Dla dowolnego pomyślne inspekcji pełnego śledzenia są zapisywane. Jakiekolwiek niepowodzenie inspekcji, aby uzyskać dane śledzenia są zapisywane na poziomie błędu.  
  
4.  Usuń istniejącą <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekcji zachowań odnaleziona w opisie elementu <xref:System.ServiceModel.ServiceHost>. Kolekcja zachowanie odbywa się przez <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> właściwość, która z kolei jest dostępny z <xref:System.ServiceModel.ServiceHostBase.Description%2A> właściwości. Następnie dodaj nową <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do tej samej kolekcji, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Aby skonfigurować inspekcję w konfiguracji  
  
1.  Aby skonfigurować inspekcję w konfiguracji, należy dodać [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) sekcja pliku web.config. Następnie dodaj [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element i ustaw różne atrybuty, jak pokazano w poniższym przykładzie.  
  
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
  
2.  Zachowanie usługi, należy określić, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy i dodaje nowy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do swojej kolekcji zachowań.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Ustawienie <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości `true`, pomija wszelkie niespełnienie Generuj inspekcje zabezpieczeń (jeśli równa `false`, zgłaszany jest wyjątek). Jednak jeśli włączysz następujące Windows **Ustawianie zabezpieczeń lokalnych** właściwości nie można wygenerować zdarzeń inspekcji spowoduje, że Windows natychmiast zamknie:  
  
 **Inspekcja: Zamknij system natychmiast, jeśli nie można rejestrować wyników inspekcji**  
  
 Aby ustawić właściwości, otwórz **ustawienia zabezpieczeń lokalnych** okno dialogowe. W obszarze **ustawienia zabezpieczeń**, kliknij przycisk **zasady lokalne**. Następnie kliknij przycisk **opcje zabezpieczeń**.  
  
 Jeśli <xref:System.ServiceModel.AuditLogLocation> właściwość jest ustawiona na <xref:System.ServiceModel.AuditLogLocation.Security> i **inspekcji dostępu do obiektów** nie jest ustawiona w **zasady zabezpieczeń lokalnych**, zdarzenia inspekcji nie będą zapisywane w dzienniku zabezpieczeń. Należy pamiętać, że zwracany jest bez błędów, ale wpisy inspekcji nie są zapisywane w dzienniku zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
