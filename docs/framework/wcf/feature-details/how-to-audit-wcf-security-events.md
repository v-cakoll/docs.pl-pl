---
title: 'Porady: inspekcji zdarzeń zabezpieczeń systemu Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ad1cf3dd598a2ec76302c48ae36b45fd0310d69d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493270"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="6674a-102">Porady: inspekcji zdarzeń zabezpieczeń systemu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6674a-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="6674a-103">Windows Communication Foundation (WCF) pozwala na rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows można wyświetlić za pomocą Podglądu zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6674a-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="6674a-104">W tym temacie wyjaśniono, jak skonfigurować aplikację tak, aby go dzienniki zdarzeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6674a-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="6674a-105">Aby uzyskać więcej informacji na temat inspekcji WCF, zobacz [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="6674a-105">For more information about WCF auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="6674a-106">Inspekcja zdarzeń zabezpieczeń w kodzie</span><span class="sxs-lookup"><span data-stu-id="6674a-106">To audit security events in code</span></span>  
  
1.  <span data-ttu-id="6674a-107">Określ lokalizację dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="6674a-107">Specify the audit log location.</span></span> <span data-ttu-id="6674a-108">Aby to zrobić, ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> klasy do jednego z <xref:System.ServiceModel.AuditLogLocation> wartości wyliczenia, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6674a-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="6674a-109"><xref:System.ServiceModel.AuditLogLocation> Wyliczenie ma trzy wartości: `Application`, `Security`, lub `Default`.</span><span class="sxs-lookup"><span data-stu-id="6674a-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="6674a-110">Wartość określa jednym z dzienników, które są widoczne w Podglądzie zdarzeń, albo w dzienniku zabezpieczeń lub dziennika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6674a-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="6674a-111">Jeśli używasz `Default` wartość rzeczywista dziennika zależy od systemu operacyjnego, aplikacja jest uruchomiona na.</span><span class="sxs-lookup"><span data-stu-id="6674a-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="6674a-112">Jeśli jest włączona funkcja inspekcji i lokalizacja dziennika nie jest określony, wartością domyślną jest `Security` dziennika dla platform, które obsługują zapisywanie w dzienniku zabezpieczeń; w przeciwnym razie będą zapisywane do `Application` dziennika.</span><span class="sxs-lookup"><span data-stu-id="6674a-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="6674a-113">Tylko [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wv](../../../../includes/wv-md.md)] domyślnie obsługują zapisywanie w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6674a-113">Only [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wv](../../../../includes/wv-md.md)] support writing to the Security log by default.</span></span>  
  
2.  <span data-ttu-id="6674a-114">Skonfiguruj typy zdarzeń inspekcji.</span><span class="sxs-lookup"><span data-stu-id="6674a-114">Set up the types of events to audit.</span></span> <span data-ttu-id="6674a-115">Jednocześnie można przeprowadzać inspekcję autoryzacji poziom komunikatu lub poziomu usługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6674a-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="6674a-116">Aby to zrobić, ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> właściwości lub <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> jedną z właściwości <xref:System.ServiceModel.AuditLevel> wartości wyliczenia, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6674a-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  <span data-ttu-id="6674a-117">Określ, czy pominąć lub ujawnić błędów aplikacji dotyczące dziennika zdarzeń inspekcji.</span><span class="sxs-lookup"><span data-stu-id="6674a-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="6674a-118">Ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości albo `true` lub `false`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6674a-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="6674a-119">Wartość domyślna `SuppressAuditFailure` właściwość jest `true`, dzięki czemu błąd inspekcji nie wpływa na aplikację.</span><span class="sxs-lookup"><span data-stu-id="6674a-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="6674a-120">W przeciwnym razie jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6674a-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="6674a-121">Dla dowolnego pomyślne inspekcji pełne śledzenia są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="6674a-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="6674a-122">Wszelkie niepowodzenia inspekcji dane śledzenia są zapisywane na poziomie błędu.</span><span class="sxs-lookup"><span data-stu-id="6674a-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4.  <span data-ttu-id="6674a-123">Usuń istniejącą <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekcji zachowań znaleźć w opisie <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6674a-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="6674a-124">Kolekcji zachowań jest dostępny po <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> właściwość, która z kolei jest dostępny z <xref:System.ServiceModel.ServiceHostBase.Description%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6674a-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="6674a-125">Następnie dodaj nowe <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do tej samej kolekcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6674a-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="6674a-126">Aby skonfigurować inspekcję w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6674a-126">To set up auditing in configuration</span></span>  
  
1.  <span data-ttu-id="6674a-127">Aby skonfigurować inspekcję w konfiguracji, należy dodać [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) sekcji w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="6674a-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="6674a-128">Następnie dodaj [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element i ustaw różnych atrybutów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6674a-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2.  <span data-ttu-id="6674a-129">Należy określić zachowanie dla usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6674a-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="6674a-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="6674a-130">Example</span></span>  
 <span data-ttu-id="6674a-131">Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> i dodaje nową <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do swojej kolekcji zachowań.</span><span class="sxs-lookup"><span data-stu-id="6674a-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="6674a-132">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="6674a-132">.NET Framework Security</span></span>  
 <span data-ttu-id="6674a-133">Ustawienie <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości `true`, pomija niezgodności Generuj inspekcje zabezpieczeń (Jeśli ustawiono `false`, jest zgłaszany wyjątek).</span><span class="sxs-lookup"><span data-stu-id="6674a-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="6674a-134">Jednak jeśli włączysz następujące okna **Ustawianie zabezpieczeń lokalnych**właściwości, nie można wygenerować zdarzeń inspekcji spowoduje zamknięcie natychmiast systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="6674a-134">However, if you enable the following Windows **Local Security Setting**property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="6674a-135">**Inspekcja: Zamknij system natychmiast, jeśli nie można rejestrować wyników inspekcji**</span><span class="sxs-lookup"><span data-stu-id="6674a-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="6674a-136">Aby ustawić właściwość, należy otworzyć **ustawienia zabezpieczeń lokalnych** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6674a-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="6674a-137">W obszarze **ustawienia zabezpieczeń**, kliknij przycisk **zasady lokalne**.</span><span class="sxs-lookup"><span data-stu-id="6674a-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="6674a-138">Następnie kliknij przycisk **opcje zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="6674a-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="6674a-139">Jeśli <xref:System.ServiceModel.AuditLogLocation> właściwość jest ustawiona na <xref:System.ServiceModel.AuditLogLocation.Security> i **inspekcji dostępu do obiektów** nie jest ustawiona **zasady zabezpieczeń lokalnych**, zdarzenia inspekcji nie będą zapisywane w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6674a-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="6674a-140">Należy pamiętać, że bez błędów jest zwracany, ale wpisy inspekcji nie są zapisywane w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6674a-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6674a-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6674a-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [<span data-ttu-id="6674a-142">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="6674a-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
