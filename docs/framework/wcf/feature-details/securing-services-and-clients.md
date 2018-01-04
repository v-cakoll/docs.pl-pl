---
title: "Zabezpieczanie usług i klientów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 52e07a83f5a1b84abc46f00e6fd6e80e4b9a2622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="6b19e-102">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6b19e-102">Securing Services and Clients</span></span>
<span data-ttu-id="6b19e-103">Informacje przedstawione w tej sekcji koncentruje się na programowania zabezpieczeń w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b19e-103">The information in this section focuses on programming security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="6b19e-104">Ogólnie rzecz biorąc w tym wybranie odpowiedniego powiązania dostarczane przez system, ustawianie właściwości elementu zabezpieczeń, a następnie ustawić właściwości zachowania usługi, które decydują, jak poświadczenia są pobierane do użytku przez usługi lub klienta.</span><span class="sxs-lookup"><span data-stu-id="6b19e-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="6b19e-105">Te techniki obejmować wymagania dotyczące zabezpieczeń większości użytkowników w przypadku większości scenariuszy, jak pokazano w [typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="6b19e-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="6b19e-106">Jeśli dany scenariusz wymaga więcej funkcji, należy najpierw sprawdzić [możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); Jeśli rozwiązanie nie jest widoczna, zobacz [rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="6b19e-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="6b19e-107">Jeśli tworzysz (lub współpracy z) system używający sformatowanego oświadczeń, zobacz Tematy w [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="6b19e-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b19e-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6b19e-108">In This Section</span></span>  
 [<span data-ttu-id="6b19e-109">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="6b19e-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="6b19e-110">Omówienie modelu programowania, używany do zabezpieczania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6b19e-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="6b19e-111">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="6b19e-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="6b19e-112">Przegląd sposobu zabezpieczania komunikatów za pośrednictwem warstwy transportowej.</span><span class="sxs-lookup"><span data-stu-id="6b19e-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="6b19e-113">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="6b19e-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="6b19e-114">Podsumowuje przyczyny przy użyciu zabezpieczeń na poziomie komunikatu w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b19e-114">Summarizes reasons for using message-level security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
 [<span data-ttu-id="6b19e-115">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="6b19e-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="6b19e-116">Omówienie zagadnień wymagana, gdy Zabezpieczanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sesji.</span><span class="sxs-lookup"><span data-stu-id="6b19e-116">A discussion of the considerations required when securing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] session.</span></span>  
  
 [<span data-ttu-id="6b19e-117">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="6b19e-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="6b19e-118">Wyjaśnienie niektórych typowych zadań, które są wymagane podczas korzystania z certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="6b19e-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6b19e-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="6b19e-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="6b19e-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6b19e-120">Related Sections</span></span>  
 [<span data-ttu-id="6b19e-121">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6b19e-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="6b19e-122">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6b19e-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="6b19e-123">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6b19e-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="6b19e-124">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="6b19e-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="6b19e-125">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="6b19e-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="6b19e-126">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6b19e-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="6b19e-127">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="6b19e-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b19e-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b19e-128">See Also</span></span>  
 [<span data-ttu-id="6b19e-129">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="6b19e-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="6b19e-130">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="6b19e-130">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
