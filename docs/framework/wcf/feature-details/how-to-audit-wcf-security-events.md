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
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="5aa84-102">Instrukcje: Inspekcja Windows Communication Foundation zdarzeń zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5aa84-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="5aa84-103">Windows Communication Foundation (WCF) umożliwia rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows, który można wyświetlić za pomocą Podgląd zdarzeń systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5aa84-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="5aa84-104">W tym temacie wyjaśniono, jak skonfigurować aplikację tak, aby rejestrowała zdarzenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5aa84-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="5aa84-105">Aby uzyskać więcej informacji na temat inspekcji WCF, zobacz [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="5aa84-105">For more information about WCF auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="5aa84-106">Aby przeprowadzić inspekcję zdarzeń zabezpieczeń w kodzie</span><span class="sxs-lookup"><span data-stu-id="5aa84-106">To audit security events in code</span></span>  
  
1. <span data-ttu-id="5aa84-107">Określ lokalizację dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="5aa84-107">Specify the audit log location.</span></span> <span data-ttu-id="5aa84-108">W tym celu należy ustawić właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> klasy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> na jedną z wartości wyliczenia <xref:System.ServiceModel.AuditLogLocation>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5aa84-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="5aa84-109">Wyliczenie <xref:System.ServiceModel.AuditLogLocation> ma trzy wartości: `Application`, `Security`lub `Default`.</span><span class="sxs-lookup"><span data-stu-id="5aa84-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="5aa84-110">Wartość określa jeden z dzienników widocznych w Podgląd zdarzeń, dziennik zabezpieczeń lub dziennik aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5aa84-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="5aa84-111">W przypadku użycia wartości `Default` rzeczywisty dziennik będzie zależeć od systemu operacyjnego, w którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="5aa84-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="5aa84-112">Jeśli inspekcja jest włączona, a lokalizacja dziennika nie jest określona, domyślnym dziennikiem `Security` dla platform, które obsługują zapisywanie w dzienniku zabezpieczeń; w przeciwnym razie nastąpi zapis do dziennika `Application`.</span><span class="sxs-lookup"><span data-stu-id="5aa84-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="5aa84-113">Tylko [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i Windows Vista obsługują zapisywanie w dzienniku zabezpieczeń domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5aa84-113">Only [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="5aa84-114">Skonfiguruj typy zdarzeń do inspekcji.</span><span class="sxs-lookup"><span data-stu-id="5aa84-114">Set up the types of events to audit.</span></span> <span data-ttu-id="5aa84-115">Można jednocześnie przeprowadzać inspekcję zdarzeń na poziomie usługi lub zdarzeń autoryzacji na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5aa84-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="5aa84-116">W tym celu należy ustawić właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> lub właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> na jedną z <xref:System.ServiceModel.AuditLevel> wartości wyliczenia, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5aa84-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="5aa84-117">Określ, czy pominąć lub uwidocznić błędy aplikacji dotyczące zdarzeń inspekcji dzienników.</span><span class="sxs-lookup"><span data-stu-id="5aa84-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="5aa84-118">Ustaw właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> na `true` lub `false`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5aa84-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="5aa84-119">Domyślna właściwość `SuppressAuditFailure` jest `true`, w związku z czym Niepowodzenie inspekcji nie ma wpływu na aplikację.</span><span class="sxs-lookup"><span data-stu-id="5aa84-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="5aa84-120">W przeciwnym razie jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5aa84-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="5aa84-121">W przypadku każdej pomyślnej inspekcji zostanie zapisany pełny ślad.</span><span class="sxs-lookup"><span data-stu-id="5aa84-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="5aa84-122">W przypadku wszelkich niepowodzeń inspekcji, ślad jest zapisywana na poziomie błędu.</span><span class="sxs-lookup"><span data-stu-id="5aa84-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="5aa84-123">Usuń istniejące <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekcji zachowań znalezionych w opisie <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="5aa84-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="5aa84-124">Dostęp do kolekcji zachowań uzyskuje się za pomocą właściwości <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>, która z kolei jest dostępna ze właściwości <xref:System.ServiceModel.ServiceHostBase.Description%2A>.</span><span class="sxs-lookup"><span data-stu-id="5aa84-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="5aa84-125">Następnie Dodaj nowe <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do tej samej kolekcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5aa84-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="5aa84-126">Aby skonfigurować inspekcję w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5aa84-126">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="5aa84-127">Aby skonfigurować inspekcję w konfiguracji, Dodaj [\<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu do sekcji [zachowania\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="5aa84-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="5aa84-128">Następnie Dodaj element [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) i Ustaw różne atrybuty, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5aa84-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2. <span data-ttu-id="5aa84-129">Należy określić zachowanie usługi, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5aa84-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5aa84-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aa84-130">Example</span></span>  
 <span data-ttu-id="5aa84-131">Poniższy kod tworzy wystąpienie klasy <xref:System.ServiceModel.ServiceHost> i dodaje nowy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do kolekcji zachowań.</span><span class="sxs-lookup"><span data-stu-id="5aa84-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="5aa84-132">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5aa84-132">.NET Framework Security</span></span>  
 <span data-ttu-id="5aa84-133">Ustawienie właściwości <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> na `true`powoduje pominięcie wszelkich niepowodzeń generowania inspekcji zabezpieczeń (Jeśli zostanie ustawiony na `false`, zgłaszany jest wyjątek).</span><span class="sxs-lookup"><span data-stu-id="5aa84-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="5aa84-134">Jeśli jednak zostanie włączona następująca Właściwość **Ustawienia zabezpieczeń lokalnych** systemu Windows, Niepowodzenie generowania zdarzeń inspekcji spowoduje natychmiastowe wyłączenie systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="5aa84-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="5aa84-135">**Inspekcja: Zamknij system natychmiast, jeśli nie można rejestrować inspekcji zabezpieczeń**</span><span class="sxs-lookup"><span data-stu-id="5aa84-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="5aa84-136">Aby ustawić właściwość, Otwórz okno dialogowe **Ustawienia zabezpieczeń lokalnych** .</span><span class="sxs-lookup"><span data-stu-id="5aa84-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="5aa84-137">W obszarze **Ustawienia zabezpieczeń**kliknij pozycję **Zasady lokalne**.</span><span class="sxs-lookup"><span data-stu-id="5aa84-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="5aa84-138">Następnie kliknij pozycję **Opcje zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="5aa84-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="5aa84-139">Jeśli właściwość <xref:System.ServiceModel.AuditLogLocation> jest ustawiona na <xref:System.ServiceModel.AuditLogLocation.Security> i **Inspekcja dostępu do obiektów** nie jest ustawiona w **lokalnych zasadach zabezpieczeń**, zdarzenia inspekcji nie będą zapisywane w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5aa84-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="5aa84-140">Zwróć uwagę, że nie jest zwracana żadna awaria, ale wpisy inspekcji nie są zapisywane w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5aa84-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa84-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5aa84-141">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="5aa84-142">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="5aa84-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
