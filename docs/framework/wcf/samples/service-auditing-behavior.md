---
title: "Zachowanie inspekcji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e7e85ac2aa5be9614946418f0df676ea1cb7dd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="de8cf-102">Zachowanie inspekcji usługi</span><span class="sxs-lookup"><span data-stu-id="de8cf-102">Service Auditing Behavior</span></span>
<span data-ttu-id="de8cf-103">W tym przykładzie przedstawiono sposób użycia <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> Aby włączyć inspekcję zdarzeń zabezpieczenia podczas operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="de8cf-103">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="de8cf-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="de8cf-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="de8cf-105">Usługa i klient zostały skonfigurowane przy użyciu [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="de8cf-105">The service and client have been configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="de8cf-106">`mode` Atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) została ustawiona jako `Message` i `clientCredentialType` została ustawiona jako `Windows`.</span><span class="sxs-lookup"><span data-stu-id="de8cf-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="de8cf-107">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="de8cf-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de8cf-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="de8cf-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="de8cf-109">Plik konfiguracji usługi używa `serviceSecurityAudit` element, aby skonfigurować inspekcję.</span><span class="sxs-lookup"><span data-stu-id="de8cf-109">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="de8cf-110">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="de8cf-110">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="de8cf-111">Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="de8cf-111">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="de8cf-112">Wynikowe dzienniki inspekcji będą widoczne przez uruchomienie podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de8cf-112">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="de8cf-113">Domyślnie w systemie Windows XP zdarzeń inspekcji można przejrzeć w dzienniku aplikacji podczas w systemie Windows Server 2003 i Windows Vista można wyświetlić zdarzeń inspekcji w dzienniku zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="de8cf-113">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="de8cf-114">W systemie Windows Server 2008 i Windows 7 zdarzenia inspekcji są widoczne w dziennikach aplikacji i usług.</span><span class="sxs-lookup"><span data-stu-id="de8cf-114">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="de8cf-115">Można określić lokalizację zdarzeń inspekcji przez ustawienie `auditLogLocation` atrybutu "Aplikacja" lub "Zabezpieczenia".</span><span class="sxs-lookup"><span data-stu-id="de8cf-115">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="de8cf-116">Aby uzyskać więcej informacji, zobacz [porady: zdarzenia inspekcji zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="de8cf-116">For more information, see [How to: Audit Security Events](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="de8cf-117">Jeśli zdarzenia są zapisywane w dzienniku zabezpieczeń LocalSecurityPolicy -> Włącz dostęp do obiektów należy ustawić dla "Powodzenie" i "Niepowodzenie".</span><span class="sxs-lookup"><span data-stu-id="de8cf-117">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="de8cf-118">Podczas przeglądania dziennika zdarzeń, źródło zdarzeń inspekcji jest "ServiceModel inspekcji 3.0.0.0".</span><span class="sxs-lookup"><span data-stu-id="de8cf-118">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="de8cf-119">Rekordów inspekcji uwierzytelniania wiadomości ma kategorii "MessageAuthentication", natomiast rekordów inspekcji usługi autoryzacji kategorii "ServiceAuthorization".</span><span class="sxs-lookup"><span data-stu-id="de8cf-119">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="de8cf-120">Zdarzeń inspekcji uwierzytelniania wiadomości obejmuje czy komunikat został zmodyfikowany, czy komunikat wygasł i określa, czy klient może uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="de8cf-120">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="de8cf-121">Zawierają informacje o czy uwierzytelnianie zakończyło się pomyślnie lub nie powiodło się wraz z tożsamością klienta, a punkt końcowy wiadomość została wysłana do wraz z akcję skojarzoną z komunikatem.</span><span class="sxs-lookup"><span data-stu-id="de8cf-121">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="de8cf-122">Zdarzenia inspekcji autoryzacji usługi obejmują decyzję dotyczącą autoryzacji przez Menedżera autoryzacji usługi.</span><span class="sxs-lookup"><span data-stu-id="de8cf-122">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="de8cf-123">Zawierają informacje o czy autoryzacji zakończyło się pomyślnie lub nie powiodło się wraz z tożsamością klienta, punkt końcowy wiadomość została wysłana do, akcję skojarzoną z komunikatem identyfikator kontekst autoryzacji, który został wygenerowany na podstawie Komunikat przychodzący, a typ Menedżera autoryzacji, zgłaszający decyzji dostępu.</span><span class="sxs-lookup"><span data-stu-id="de8cf-123">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="de8cf-124">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="de8cf-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="de8cf-125">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de8cf-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="de8cf-126">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de8cf-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="de8cf-127">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de8cf-127">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de8cf-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de8cf-128">See Also</span></span>  
 [<span data-ttu-id="de8cf-129">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="de8cf-129">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [<span data-ttu-id="de8cf-130">Porady: Przeprowadź inspekcję zdarzeń zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="de8cf-130">How to: Audit Security Events</span></span>](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
