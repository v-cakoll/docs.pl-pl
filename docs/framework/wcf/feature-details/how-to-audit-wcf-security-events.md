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
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="30703-102">Instrukcje: Inspekcja Windows Communication Foundation zdarzeń zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="30703-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="30703-103">Windows Communication Foundation (WCF) umożliwia rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows, który można wyświetlić za pomocą Podgląd zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="30703-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="30703-104">W tym temacie wyjaśniono, jak skonfigurować aplikację tak, aby rejestrowała zdarzenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="30703-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="30703-105">Aby uzyskać więcej informacji na temat inspekcji WCF, zobacz [Inspekcja](auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="30703-105">For more information about WCF auditing, see [Auditing](auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="30703-106">Aby przeprowadzić inspekcję zdarzeń zabezpieczeń w kodzie</span><span class="sxs-lookup"><span data-stu-id="30703-106">To audit security events in code</span></span>  
  
1. <span data-ttu-id="30703-107">Określ lokalizację dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="30703-107">Specify the audit log location.</span></span> <span data-ttu-id="30703-108">W tym celu należy ustawić <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> Właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> klasy na jedną z <xref:System.ServiceModel.AuditLogLocation> wartości wyliczenia, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="30703-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="30703-109"><xref:System.ServiceModel.AuditLogLocation>Wyliczenie ma trzy wartości: `Application` , `Security` , lub `Default` .</span><span class="sxs-lookup"><span data-stu-id="30703-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="30703-110">Wartość określa jeden z dzienników widocznych w Podgląd zdarzeń, dziennik zabezpieczeń lub dziennik aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30703-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="30703-111">W przypadku użycia `Default` wartości rzeczywisty dziennik będzie zależeć od systemu operacyjnego, w którym jest uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="30703-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="30703-112">Jeśli inspekcja jest włączona i lokalizacja dziennika nie zostanie określona, domyślnie jest to `Security` Dziennik dla platform, które obsługują zapisywanie w dzienniku zabezpieczeń. w przeciwnym razie zapis w dzienniku zostanie zapisany `Application` .</span><span class="sxs-lookup"><span data-stu-id="30703-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="30703-113">Tylko systemy Windows Server 2003 i Windows Vista domyślnie obsługują zapisywanie w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="30703-113">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="30703-114">Skonfiguruj typy zdarzeń do inspekcji.</span><span class="sxs-lookup"><span data-stu-id="30703-114">Set up the types of events to audit.</span></span> <span data-ttu-id="30703-115">Można jednocześnie przeprowadzać inspekcję zdarzeń na poziomie usługi lub zdarzeń autoryzacji na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30703-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="30703-116">W tym celu należy ustawić <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> Właściwość lub <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> Właściwość na jedną z <xref:System.ServiceModel.AuditLevel> wartości wyliczenia, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="30703-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="30703-117">Określ, czy pominąć lub uwidocznić błędy aplikacji dotyczące zdarzeń inspekcji dzienników.</span><span class="sxs-lookup"><span data-stu-id="30703-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="30703-118">Ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> Właściwość na albo `true` `false` , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="30703-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="30703-119">Właściwość domyślna `SuppressAuditFailure` to `true` , więc Niepowodzenie inspekcji nie ma wpływu na aplikację.</span><span class="sxs-lookup"><span data-stu-id="30703-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="30703-120">W przeciwnym razie jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="30703-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="30703-121">W przypadku każdej pomyślnej inspekcji zostanie zapisany pełny ślad.</span><span class="sxs-lookup"><span data-stu-id="30703-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="30703-122">W przypadku wszelkich niepowodzeń inspekcji, ślad jest zapisywana na poziomie błędu.</span><span class="sxs-lookup"><span data-stu-id="30703-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="30703-123">Usuń istniejące <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekcji zachowań znalezionych w opisie <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="30703-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="30703-124">Dostęp do kolekcji zachowań uzyskuje się za pomocą <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> właściwości, która z kolei jest dostępna z <xref:System.ServiceModel.ServiceHostBase.Description%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="30703-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="30703-125">Następnie Dodaj nową <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do tej samej kolekcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="30703-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="30703-126">Aby skonfigurować inspekcję w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="30703-126">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="30703-127">Aby skonfigurować inspekcję w konfiguracji, Dodaj [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element do [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) sekcji pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="30703-127">To set up auditing in configuration, add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="30703-128">Następnie Dodaj [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) element i Ustaw różne atrybuty, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="30703-128">Then add a [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2. <span data-ttu-id="30703-129">Należy określić zachowanie usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="30703-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="30703-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="30703-130">Example</span></span>  
 <span data-ttu-id="30703-131">Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy i dodaje nową <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do kolekcji zachowań.</span><span class="sxs-lookup"><span data-stu-id="30703-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="30703-132">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="30703-132">.NET Framework Security</span></span>  
 <span data-ttu-id="30703-133">Ustawienie <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości na `true` , pomija wszelkie niepowodzenie generowania inspekcji zabezpieczeń (jeśli jest ustawiona na `false` , zgłaszany jest wyjątek).</span><span class="sxs-lookup"><span data-stu-id="30703-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="30703-134">Jeśli jednak zostanie włączona następująca Właściwość **Ustawienia zabezpieczeń lokalnych** systemu Windows, Niepowodzenie generowania zdarzeń inspekcji spowoduje natychmiastowe wyłączenie systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="30703-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="30703-135">**Inspekcja: zamknij system natychmiast, jeśli nie można rejestrować wyników inspekcji**</span><span class="sxs-lookup"><span data-stu-id="30703-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="30703-136">Aby ustawić właściwość, Otwórz okno dialogowe **Ustawienia zabezpieczeń lokalnych** .</span><span class="sxs-lookup"><span data-stu-id="30703-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="30703-137">W obszarze **Ustawienia zabezpieczeń**kliknij pozycję **Zasady lokalne**.</span><span class="sxs-lookup"><span data-stu-id="30703-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="30703-138">Następnie kliknij pozycję **Opcje zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="30703-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="30703-139">Jeśli <xref:System.ServiceModel.AuditLogLocation> Właściwość jest ustawiona na <xref:System.ServiceModel.AuditLogLocation.Security> i **Inspekcja dostępu do obiektów** nie jest ustawiona w **lokalnych zasadach zabezpieczeń**, zdarzenia inspekcji nie będą zapisywane w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="30703-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="30703-140">Zwróć uwagę, że nie jest zwracana żadna awaria, ale wpisy inspekcji nie są zapisywane w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="30703-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30703-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30703-141">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="30703-142">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="30703-142">Auditing</span></span>](auditing-security-events.md)
