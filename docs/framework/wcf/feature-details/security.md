---
title: Zabezpieczenia programu WCF (Windows Communication Foundation)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
caps.latest.revision: 21
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 6b93bfff2cd97e10d9c0dba4373839337f36aacb
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="d01a9-102">Zabezpieczenia programu WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="d01a9-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="d01a9-103">W tematach w tej sekcji opisano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcje zabezpieczeń i sposób ich użycia, aby ułatwić zabezpieczonych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d01a9-103">The topics in this section describe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="d01a9-104">Aby uzyskać więcej informacji o systemie Windows Server AppFabric i zabezpieczeń, zobacz [Model zabezpieczeń dla systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="d01a9-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d01a9-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d01a9-105">In This Section</span></span>  
 [<span data-ttu-id="d01a9-106">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d01a9-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="d01a9-107">Zawiera opis funkcji zabezpieczeń w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d01a9-107">Describes the security features in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="d01a9-108">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d01a9-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="d01a9-109">Zawiera opis podstawowych terminów i pojęć używanych w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d01a9-109">Describes the basic terminology and concepts used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security.</span></span>  
  
 [<span data-ttu-id="d01a9-110">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d01a9-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="d01a9-111">W tym artykule opisano scenariusze i topologii można skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d01a9-111">Describes scenarios and topologies you can configure with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="d01a9-112">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="d01a9-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="d01a9-113">Zawiera omówienie zachowania usługi WCF, które mają wpływ na zabezpieczenia, takie jak Ustawianie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="d01a9-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="d01a9-114">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="d01a9-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="d01a9-115">Widok zorientowane na zabezpieczeń powiązań, w tym tematów, które pokazują, jak utworzyć niestandardowe zabezpieczeń powiązania.</span><span class="sxs-lookup"><span data-stu-id="d01a9-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="d01a9-116">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d01a9-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="d01a9-117">Opis sposobu zabezpieczania komunikatów za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d01a9-117">Describes how to secure messages using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security features.</span></span>  
  
 [<span data-ttu-id="d01a9-118">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="d01a9-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="d01a9-119">Pokazuje typowe zadania dotyczące uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="d01a9-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="d01a9-120">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="d01a9-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="d01a9-121">W tym artykule opisano typowe scenariusze autoryzacji z zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="d01a9-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="d01a9-122">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="d01a9-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="d01a9-123">W tym artykule opisano podstawy federacyjnego oraz sposobu tworzenia klientów komunikujących się z serwerów federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="d01a9-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="d01a9-124">Zaufanie częściowe</span><span class="sxs-lookup"><span data-stu-id="d01a9-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="d01a9-125">Opisuje sposób uruchamiania scenariuszach częściowo zaufanych i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ograniczenia podczas uruchamiania częściowo zaufany.</span><span class="sxs-lookup"><span data-stu-id="d01a9-125">Describes how to run partially-trusted scenarios and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="d01a9-126">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="d01a9-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="d01a9-127">Informacje dotyczące inspekcji zdarzeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d01a9-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="d01a9-128">Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d01a9-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="d01a9-129">Wytyczne dotyczące tworzenia bezpiecznego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d01a9-129">Guidelines for creating secure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d01a9-130">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d01a9-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="d01a9-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d01a9-131">Related Sections</span></span>  
 [<span data-ttu-id="d01a9-132">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="d01a9-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="d01a9-133">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="d01a9-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="d01a9-134">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="d01a9-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="d01a9-135">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="d01a9-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="d01a9-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d01a9-136">See Also</span></span>  
 [<span data-ttu-id="d01a9-137">Konfigurowanie własnej aplikacji</span><span class="sxs-lookup"><span data-stu-id="d01a9-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
