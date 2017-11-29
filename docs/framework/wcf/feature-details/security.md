---
title: Zabezpieczenia programu WCF (Windows Communication Foundation)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
caps.latest.revision: "21"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 38f62a6ccc0c9291f3963173475f99d5800feb39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="14658-102">Zabezpieczenia programu WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="14658-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="14658-103">W tematach w tej sekcji opisano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcje zabezpieczeń i sposób ich użycia, aby ułatwić zabezpieczonych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="14658-103">The topics in this section describe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security features and how to use them to help secure messages.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="14658-104">Windows Server AppFabric i zabezpieczeń, zobacz [Model zabezpieczeń dla systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="14658-104"> Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14658-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="14658-105">In This Section</span></span>  
 [<span data-ttu-id="14658-106">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="14658-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="14658-107">Zawiera opis funkcji zabezpieczeń w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14658-107">Describes the security features in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="14658-108">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="14658-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="14658-109">Zawiera opis podstawowych terminów i pojęć używanych w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="14658-109">Describes the basic terminology and concepts used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security.</span></span>  
  
 [<span data-ttu-id="14658-110">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="14658-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="14658-111">W tym artykule opisano scenariusze i topologii można skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14658-111">Describes scenarios and topologies you can configure with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="14658-112">Zachowania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="14658-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="14658-113">Zawiera omówienie zachowania usługi WCF, które mają wpływ na zabezpieczenia, takie jak Ustawianie poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="14658-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="14658-114">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="14658-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="14658-115">Widok zorientowane na zabezpieczeń powiązań, w tym tematów, które pokazują, jak utworzyć niestandardowe zabezpieczeń powiązania.</span><span class="sxs-lookup"><span data-stu-id="14658-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="14658-116">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="14658-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="14658-117">Opis sposobu zabezpieczania komunikatów za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="14658-117">Describes how to secure messages using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security features.</span></span>  
  
 [<span data-ttu-id="14658-118">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="14658-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="14658-119">Pokazuje typowe zadania dotyczące uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="14658-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="14658-120">Autoryzacji</span><span class="sxs-lookup"><span data-stu-id="14658-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="14658-121">W tym artykule opisano typowe scenariusze autoryzacji z zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="14658-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="14658-122">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="14658-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="14658-123">W tym artykule opisano podstawy federacyjnego oraz sposobu tworzenia klientów komunikujących się z serwerów federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="14658-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="14658-124">Częściowa relacja zaufania</span><span class="sxs-lookup"><span data-stu-id="14658-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="14658-125">Opisuje sposób uruchamiania scenariuszach częściowo zaufanych i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ograniczenia podczas uruchamiania częściowo zaufany.</span><span class="sxs-lookup"><span data-stu-id="14658-125">Describes how to run partially-trusted scenarios and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="14658-126">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="14658-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="14658-127">Informacje dotyczące inspekcji zdarzeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="14658-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="14658-128">Wskazówki dotyczące zabezpieczeń i najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="14658-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="14658-129">Wytyczne dotyczące tworzenia bezpiecznego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="14658-129">Guidelines for creating secure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="14658-130">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="14658-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="14658-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="14658-131">Related Sections</span></span>  
 [<span data-ttu-id="14658-132">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="14658-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="14658-133">Programowanie podstawowe usługi WCF</span><span class="sxs-lookup"><span data-stu-id="14658-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="14658-134">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="14658-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="14658-135">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="14658-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="14658-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14658-136">See Also</span></span>  
 [<span data-ttu-id="14658-137">Konfigurowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="14658-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
