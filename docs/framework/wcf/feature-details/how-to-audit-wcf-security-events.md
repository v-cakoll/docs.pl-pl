---
title: 'Porady: inspekcji zdarzeń zabezpieczeń systemu Windows Communication Foundation'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
caps.latest.revision: 19
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 72eff4af38636577dc9e3b35af1f1155d5ed892c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Porady: inspekcji zdarzeń zabezpieczeń systemu Windows Communication Foundation
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Umożliwia rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows można wyświetlić za pomocą Podglądu zdarzeń systemu Windows. W tym temacie wyjaśniono, jak skonfigurować aplikację tak, aby go dzienniki zdarzeń zabezpieczeń. Aby uzyskać więcej informacji na temat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inspekcji, zobacz [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Inspekcja zdarzeń zabezpieczeń w kodzie  
  
1.  Określ lokalizację dziennika inspekcji. Aby to zrobić, ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> klasy do jednego z <xref:System.ServiceModel.AuditLogLocation> wartości wyliczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation> Wyliczenie ma trzy wartości: `Application`, `Security`, lub `Default`. Wartość określa jednym z dzienników, które są widoczne w Podglądzie zdarzeń, albo w dzienniku zabezpieczeń lub dziennika aplikacji. Jeśli używasz `Default` wartość rzeczywista dziennika zależy od systemu operacyjnego, aplikacja jest uruchomiona na. Jeśli jest włączona funkcja inspekcji i lokalizacja dziennika nie jest określony, wartością domyślną jest `Security` dziennika dla platform, które obsługują zapisywanie w dzienniku zabezpieczeń; w przeciwnym razie będą zapisywane do `Application` dziennika. Tylko [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wv](../../../../includes/wv-md.md)] domyślnie obsługują zapisywanie w dzienniku zabezpieczeń.  
  
2.  Skonfiguruj typy zdarzeń inspekcji. Jednocześnie można przeprowadzać inspekcję autoryzacji poziom komunikatu lub poziomu usługi zdarzenia. Aby to zrobić, ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> właściwości lub <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> jedną z właściwości <xref:System.ServiceModel.AuditLevel> wartości wyliczenia, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  Określ, czy pominąć lub ujawnić błędów aplikacji dotyczące dziennika zdarzeń inspekcji. Ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości albo `true` lub `false`, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Wartość domyślna `SuppressAuditFailure` właściwość jest `true`, dzięki czemu błąd inspekcji nie wpływa na aplikację. W przeciwnym razie jest zgłaszany wyjątek. Dla dowolnego pomyślne inspekcji pełne śledzenia są zapisywane. Wszelkie niepowodzenia inspekcji dane śledzenia są zapisywane na poziomie błędu.  
  
4.  Usuń istniejącą <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekcji zachowań znaleźć w opisie <xref:System.ServiceModel.ServiceHost>. Kolekcji zachowań jest dostępny po <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> właściwość, która z kolei jest dostępny z <xref:System.ServiceModel.ServiceHostBase.Description%2A> właściwości. Następnie dodaj nowe <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do tej samej kolekcji, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Aby skonfigurować inspekcję w konfiguracji  
  
1.  Aby skonfigurować inspekcję w konfiguracji, należy dodać [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) sekcji w pliku web.config. Następnie dodaj [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element i ustaw różnych atrybutów, jak pokazano w poniższym przykładzie.  
  
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
  
2.  Należy określić zachowanie dla usługi, jak pokazano w poniższym przykładzie.  
  
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
 Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> i dodaje nową <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do swojej kolekcji zachowań.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Ustawienie <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości `true`, pomija niezgodności Generuj inspekcje zabezpieczeń (Jeśli ustawiono `false`, jest zgłaszany wyjątek). Jednak jeśli włączysz następujące okna **Ustawianie zabezpieczeń lokalnych**właściwości, nie można wygenerować zdarzeń inspekcji spowoduje zamknięcie natychmiast systemu Windows:  
  
 **Inspekcja: Zamknij system natychmiast, jeśli nie można rejestrować wyników inspekcji**  
  
 Aby ustawić właściwość, należy otworzyć **ustawienia zabezpieczeń lokalnych** okno dialogowe. W obszarze **ustawienia zabezpieczeń**, kliknij przycisk **zasady lokalne**. Następnie kliknij przycisk **opcje zabezpieczeń**.  
  
 Jeśli <xref:System.ServiceModel.AuditLogLocation> właściwość jest ustawiona na <xref:System.ServiceModel.AuditLogLocation.Security> i **inspekcji dostępu do obiektów** nie jest ustawiona **zasady zabezpieczeń lokalnych**, zdarzenia inspekcji nie będą zapisywane w dzienniku zabezpieczeń. Należy pamiętać, że bez błędów jest zwracany, ale wpisy inspekcji nie są zapisywane w dzienniku zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
