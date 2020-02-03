---
title: Zabezpieczanie usług i klientów
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 719ab26198bd7b83310025e03e541fa11b109612
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746413"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="7d091-102">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7d091-102">Securing Services and Clients</span></span>
<span data-ttu-id="7d091-103">Informacje przedstawione w tej sekcji koncentrują się na zabezpieczeniach programistycznych w programie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7d091-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="7d091-104">Ogólnie rzecz biorąc, obejmuje to wybranie odpowiedniego powiązania dostarczonego przez system, ustawienie właściwości elementu zabezpieczeń, a następnie ustawienie właściwości zachowań usługi, które określają sposób pobierania poświadczeń do użycia przez usługę lub klienta.</span><span class="sxs-lookup"><span data-stu-id="7d091-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="7d091-105">Te techniki obejmują wymagania dotyczące zabezpieczeń większości użytkowników w większości scenariuszy, jak pokazano w [typowych scenariuszach zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="7d091-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="7d091-106">Jeśli scenariusz wymaga większej liczby możliwości, należy najpierw zapoznać [się z funkcjami zabezpieczeń i powiązaniami niestandardowymi](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); Jeśli rozwiązanie nie jest widoczne, zobacz [rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="7d091-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="7d091-107">W przypadku tworzenia (lub współpracy z programem) systemu, który używa rozbudowanych oświadczeń, zapoznaj się z tematami w temacie [autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="7d091-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d091-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7d091-108">In This Section</span></span>  
 [<span data-ttu-id="7d091-109">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="7d091-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="7d091-110">Omówienie modelu programowania używanego do zabezpieczania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7d091-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="7d091-111">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="7d091-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="7d091-112">Omówienie sposobów zabezpieczania komunikatów za pomocą warstwy transportowej.</span><span class="sxs-lookup"><span data-stu-id="7d091-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="7d091-113">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="7d091-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="7d091-114">Podsumowuje przyczyny używania zabezpieczeń na poziomie komunikatów w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7d091-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="7d091-115">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="7d091-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="7d091-116">Omówienie zagadnień wymaganych podczas zabezpieczania sesji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="7d091-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="7d091-117">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="7d091-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="7d091-118">Wyjaśnienie niektórych typowych zadań wymaganych w przypadku używania certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="7d091-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7d091-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7d091-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="7d091-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7d091-120">Related Sections</span></span>  
 [<span data-ttu-id="7d091-121">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7d091-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="7d091-122">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7d091-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="7d091-123">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7d091-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="7d091-124">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="7d091-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="7d091-125">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="7d091-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="7d091-126">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7d091-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="7d091-127">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="7d091-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="7d091-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d091-128">See also</span></span>

- [<span data-ttu-id="7d091-129">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="7d091-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
- <span data-ttu-id="7d091-130">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7d091-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
