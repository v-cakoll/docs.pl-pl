---
title: Zabezpieczenia programu WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: fb48ae39d269f21a7120ecf143dc4c4680efe39d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499092"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="0bd23-102">Zabezpieczenia programu WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="0bd23-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="0bd23-103">W tematach w tej sekcji opisano funkcje zabezpieczeń systemu Windows Communication Foundation (WCF) oraz sposób ich użycia, aby ułatwić zabezpieczonych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0bd23-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="0bd23-104">Aby uzyskać więcej informacji o systemie Windows Server AppFabric i zabezpieczeń, zobacz [Model zabezpieczeń dla systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="0bd23-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0bd23-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0bd23-105">In This Section</span></span>  
 [<span data-ttu-id="0bd23-106">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0bd23-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="0bd23-107">Zawiera opis funkcji zabezpieczeń w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="0bd23-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="0bd23-108">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0bd23-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="0bd23-109">Zawiera opis podstawowych terminów i pojęć używanych w zabezpieczeniach WCF.</span><span class="sxs-lookup"><span data-stu-id="0bd23-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="0bd23-110">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0bd23-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="0bd23-111">W tym artykule opisano scenariusze i topologii, które można skonfigurować z programem WCF.</span><span class="sxs-lookup"><span data-stu-id="0bd23-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="0bd23-112">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0bd23-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="0bd23-113">Zawiera omówienie zachowania usługi WCF, które mają wpływ na zabezpieczenia, takie jak Ustawianie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="0bd23-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="0bd23-114">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="0bd23-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="0bd23-115">Widok zorientowane na zabezpieczeń powiązań, w tym tematów, które pokazują, jak utworzyć niestandardowe zabezpieczeń powiązania.</span><span class="sxs-lookup"><span data-stu-id="0bd23-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="0bd23-116">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="0bd23-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="0bd23-117">Opis sposobu zabezpieczania komunikatów przy użyciu funkcji zabezpieczeń programu WCF.</span><span class="sxs-lookup"><span data-stu-id="0bd23-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="0bd23-118">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="0bd23-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="0bd23-119">Pokazuje typowe zadania dotyczące uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="0bd23-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="0bd23-120">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="0bd23-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="0bd23-121">W tym artykule opisano typowe scenariusze autoryzacji z zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="0bd23-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="0bd23-122">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0bd23-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="0bd23-123">W tym artykule opisano podstawy federacyjnego oraz sposobu tworzenia klientów komunikujących się z serwerów federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="0bd23-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="0bd23-124">Zaufanie częściowe</span><span class="sxs-lookup"><span data-stu-id="0bd23-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="0bd23-125">Opisuje sposób uruchamiania częściowo zaufane scenariuszach i ograniczeniach WCF podczas uruchamiania częściowo zaufany.</span><span class="sxs-lookup"><span data-stu-id="0bd23-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="0bd23-126">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="0bd23-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="0bd23-127">Informacje dotyczące inspekcji zdarzeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0bd23-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="0bd23-128">Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="0bd23-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="0bd23-129">Wytyczne dotyczące tworzenia bezpiecznych aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="0bd23-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0bd23-130">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="0bd23-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="0bd23-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0bd23-131">Related Sections</span></span>  
 [<span data-ttu-id="0bd23-132">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="0bd23-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="0bd23-133">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="0bd23-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="0bd23-134">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="0bd23-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="0bd23-135">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="0bd23-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="0bd23-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bd23-136">See Also</span></span>  
 [<span data-ttu-id="0bd23-137">Konfigurowanie własnej aplikacji</span><span class="sxs-lookup"><span data-stu-id="0bd23-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
