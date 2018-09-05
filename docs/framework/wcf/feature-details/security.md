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
ms.openlocfilehash: a070800ea15c5a7f16b52ca69c7e454c92618e1a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503335"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="13912-102">Zabezpieczenia programu WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="13912-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="13912-103">Tematy w tej sekcji opisano funkcje zabezpieczeń usługi Windows Communication Foundation (WCF) i jak z nich korzystać, aby ułatwić zabezpieczonych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="13912-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="13912-104">Aby uzyskać więcej informacji na temat systemu Windows Server AppFabric i zabezpieczeń, zobacz [modelu zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="13912-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13912-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="13912-105">In This Section</span></span>  
 [<span data-ttu-id="13912-106">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="13912-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="13912-107">W tym artykule opisano funkcje zabezpieczeń programu WCF.</span><span class="sxs-lookup"><span data-stu-id="13912-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="13912-108">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="13912-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="13912-109">Zawiera opis podstawowej terminologii i pojęć używanych w zabezpieczeniach WCF.</span><span class="sxs-lookup"><span data-stu-id="13912-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="13912-110">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="13912-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="13912-111">W tym artykule opisano scenariuszach i topologiach, które można skonfigurować przy użyciu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="13912-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="13912-112">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="13912-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="13912-113">Zawiera omówienie zachowania usługi WCF, które mają wpływ na zabezpieczenia, takie jak Ustawianie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="13912-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="13912-114">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="13912-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="13912-115">Widok związanych z zabezpieczeniami powiązania, łącznie z tematów, które pokazują, jak utworzyć niestandardowe zabezpieczeń powiązania.</span><span class="sxs-lookup"><span data-stu-id="13912-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="13912-116">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="13912-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="13912-117">Opisuje sposób Zabezpieczanie komunikatów za pomocą funkcji zabezpieczeń programu WCF.</span><span class="sxs-lookup"><span data-stu-id="13912-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="13912-118">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="13912-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="13912-119">Przedstawia typowe zadania związane z uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="13912-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="13912-120">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="13912-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="13912-121">W tym artykule opisano typowe scenariusze autoryzacji za pomocą implementacji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="13912-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="13912-122">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="13912-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="13912-123">W tym artykule opisano podstawy federation oraz sposób tworzenia klientów, które komunikują się przy użyciu serwerów federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="13912-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="13912-124">Zaufanie częściowe</span><span class="sxs-lookup"><span data-stu-id="13912-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="13912-125">Opisano sposób uruchamiania częściowo zaufanych scenariuszach i ograniczeniach usługi WCF, podczas uruchamiania częściowo zaufany.</span><span class="sxs-lookup"><span data-stu-id="13912-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="13912-126">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="13912-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="13912-127">Opisuje sposób Inspekcja zdarzeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="13912-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="13912-128">Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="13912-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="13912-129">Wytyczne dotyczące tworzenia bezpiecznych aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="13912-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="13912-130">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="13912-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="13912-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="13912-131">Related Sections</span></span>  
 [<span data-ttu-id="13912-132">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="13912-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="13912-133">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="13912-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="13912-134">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="13912-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="13912-135">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="13912-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="13912-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13912-136">See Also</span></span>  
 [<span data-ttu-id="13912-137">Konfigurowanie własnej aplikacji</span><span class="sxs-lookup"><span data-stu-id="13912-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
