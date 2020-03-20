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
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="34d34-102">Jak: Inspekcja zdarzeń zabezpieczeń programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="34d34-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="34d34-103">Program Windows Communication Foundation (WCF) umożliwia rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows, które można wyświetlać za pomocą Podglądu zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="34d34-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="34d34-104">W tym temacie wyjaśniono, jak skonfigurować aplikację, tak aby rejestrowała zdarzenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="34d34-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="34d34-105">Aby uzyskać więcej informacji na temat inspekcji WCF, zobacz [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="34d34-105">For more information about WCF auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="34d34-106">Aby przeprowadzić inspekcję zdarzeń zabezpieczeń w kodzie</span><span class="sxs-lookup"><span data-stu-id="34d34-106">To audit security events in code</span></span>  
  
1. <span data-ttu-id="34d34-107">Określ lokalizację dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="34d34-107">Specify the audit log location.</span></span> <span data-ttu-id="34d34-108">Aby to zrobić, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> należy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> ustawić właściwość <xref:System.ServiceModel.AuditLogLocation> klasy na jedną z wartości wyliczenia, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34d34-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="34d34-109">Wyliczenie <xref:System.ServiceModel.AuditLogLocation> ma trzy `Application`wartości: , `Security`, lub `Default`.</span><span class="sxs-lookup"><span data-stu-id="34d34-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="34d34-110">Wartość określa jeden z dzienników widocznych w Podglądzie zdarzeń, dziennik zabezpieczeń lub dziennik aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34d34-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="34d34-111">Jeśli używasz `Default` wartości, rzeczywisty dziennik będzie zależeć od systemu operacyjnego, na który działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="34d34-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="34d34-112">Jeśli inspekcja jest włączona, a lokalizacja dziennika nie `Security` jest określona, domyślnym jest dziennik dla platform, które obsługują zapisywanie w dzienniku zabezpieczeń; w przeciwnym razie zostanie `Application` wpisać do dziennika.</span><span class="sxs-lookup"><span data-stu-id="34d34-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="34d34-113">Tylko systemy Windows Server 2003 i Windows Vista domyślnie obsługują zapisywanie w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="34d34-113">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="34d34-114">Konfigurowanie typów zdarzeń do inspekcji.</span><span class="sxs-lookup"><span data-stu-id="34d34-114">Set up the types of events to audit.</span></span> <span data-ttu-id="34d34-115">Można jednocześnie inspekcji zdarzeń na poziomie usługi lub zdarzenia autoryzacji na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="34d34-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="34d34-116">Aby to zrobić, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> należy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> ustawić właściwość <xref:System.ServiceModel.AuditLevel> lub właściwość do jednej z wartości wyliczenia, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34d34-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="34d34-117">Określ, czy należy pominąć lub udostępnić błędy aplikacji dotyczące zdarzeń inspekcji dziennika.</span><span class="sxs-lookup"><span data-stu-id="34d34-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="34d34-118">Ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwość na `true` `false`jedną lub , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34d34-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="34d34-119">Domyślną `SuppressAuditFailure` właściwością jest `true`, dzięki czemu niepowodzenie inspekcji nie wpływa na aplikację.</span><span class="sxs-lookup"><span data-stu-id="34d34-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="34d34-120">W przeciwnym razie jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="34d34-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="34d34-121">Dla każdego pomyślnego audytu jest zapisywany pełny ślad.</span><span class="sxs-lookup"><span data-stu-id="34d34-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="34d34-122">W przypadku niepowodzenia inspekcji śledzenia jest zapisywany na poziomie błędu.</span><span class="sxs-lookup"><span data-stu-id="34d34-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="34d34-123">Usuń istniejące <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekcji zachowań znalezionych <xref:System.ServiceModel.ServiceHost>w opisie pliku .</span><span class="sxs-lookup"><span data-stu-id="34d34-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="34d34-124">Kolekcja zachowania jest dostępna <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> dla właściwości, która z kolei <xref:System.ServiceModel.ServiceHostBase.Description%2A> jest dostępna z właściwości.</span><span class="sxs-lookup"><span data-stu-id="34d34-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="34d34-125">Następnie dodaj <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> nowy do tej samej kolekcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34d34-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="34d34-126">Aby skonfigurować inspekcję w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="34d34-126">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="34d34-127">Aby skonfigurować inspekcję [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) w konfiguracji, dodaj element zachowania>do sekcji [ \<zachowania>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="34d34-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="34d34-128">Następnie dodaj [ \<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element i ustawić różne atrybuty, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34d34-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2. <span data-ttu-id="34d34-129">Należy określić zachowanie usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34d34-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="34d34-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="34d34-130">Example</span></span>  
 <span data-ttu-id="34d34-131">Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy i <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> dodaje nowy do swojej kolekcji zachowań.</span><span class="sxs-lookup"><span data-stu-id="34d34-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="34d34-132">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="34d34-132">.NET Framework Security</span></span>  
 <span data-ttu-id="34d34-133">Ustawienie <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości `true`na , pomija wszelkie niepowodzenie generowania inspekcji `false`zabezpieczeń (jeśli jest ustawiona na , wyjątek).</span><span class="sxs-lookup"><span data-stu-id="34d34-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="34d34-134">Jeśli jednak włączysz następującą właściwość **Ustawienia zabezpieczeń lokalnych** systemu Windows, niepowodzenie generowania zdarzeń inspekcji spowoduje natychmiastowe zamknięcie systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="34d34-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="34d34-135">**Inspekcja: zamknij system natychmiast, jeśli nie można rejestrować wyników inspekcji**</span><span class="sxs-lookup"><span data-stu-id="34d34-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="34d34-136">Aby ustawić właściwość, otwórz okno dialogowe **Lokalne ustawienia zabezpieczeń.**</span><span class="sxs-lookup"><span data-stu-id="34d34-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="34d34-137">W obszarze **Ustawienia zabezpieczeń**kliknij pozycję **Zasady lokalne**.</span><span class="sxs-lookup"><span data-stu-id="34d34-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="34d34-138">Następnie kliknij pozycję **Opcje zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="34d34-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="34d34-139">Jeśli <xref:System.ServiceModel.AuditLogLocation> właściwość jest <xref:System.ServiceModel.AuditLogLocation.Security> ustawiona na i **Inspekcja dostępu do obiektu** nie jest ustawiona w **zasadach zabezpieczeń lokalnych,** zdarzenia inspekcji nie zostaną zapisane w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="34d34-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="34d34-140">Należy zauważyć, że nie jest zwracany błąd, ale wpisy inspekcji nie są zapisywane w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="34d34-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d34-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34d34-141">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="34d34-142">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="34d34-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
