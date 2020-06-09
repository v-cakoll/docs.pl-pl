---
title: Zabezpieczanie usług i klientów
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: db0a0dcfbe04a7b7dbfabfed59f9b8637d0a2797
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586211"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="060ed-102">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="060ed-102">Securing Services and Clients</span></span>
<span data-ttu-id="060ed-103">Informacje przedstawione w tej sekcji koncentrują się na zabezpieczeniach programistycznych w programie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="060ed-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="060ed-104">Ogólnie rzecz biorąc, obejmuje to wybranie odpowiedniego powiązania dostarczonego przez system, ustawienie właściwości elementu zabezpieczeń, a następnie ustawienie właściwości zachowań usługi, które określają sposób pobierania poświadczeń do użycia przez usługę lub klienta.</span><span class="sxs-lookup"><span data-stu-id="060ed-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="060ed-105">Te techniki obejmują wymagania dotyczące zabezpieczeń większości użytkowników w większości scenariuszy, jak pokazano w [typowych scenariuszach zabezpieczeń](common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="060ed-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](common-security-scenarios.md).</span></span> <span data-ttu-id="060ed-106">Jeśli scenariusz wymaga większej liczby możliwości, należy najpierw zapoznać [się z funkcjami zabezpieczeń i powiązaniami niestandardowymi](security-capabilities-with-custom-bindings.md); Jeśli rozwiązanie nie jest widoczne, zobacz [rozszerzanie zabezpieczeń](../extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="060ed-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../extending/extending-security.md).</span></span> <span data-ttu-id="060ed-107">W przypadku tworzenia (lub współpracy z programem) systemu, który używa rozbudowanych oświadczeń, zapoznaj się z tematami w temacie [autoryzacja](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="060ed-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="060ed-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="060ed-108">In This Section</span></span>  
 [<span data-ttu-id="060ed-109">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="060ed-109">Programming WCF Security</span></span>](programming-wcf-security.md)  
 <span data-ttu-id="060ed-110">Omówienie modelu programowania używanego do zabezpieczania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="060ed-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="060ed-111">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="060ed-111">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="060ed-112">Omówienie sposobów zabezpieczania komunikatów za pomocą warstwy transportowej.</span><span class="sxs-lookup"><span data-stu-id="060ed-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="060ed-113">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="060ed-113">Message Security</span></span>](message-security-in-wcf.md)  
 <span data-ttu-id="060ed-114">Podsumowuje przyczyny używania zabezpieczeń na poziomie komunikatów w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="060ed-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="060ed-115">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="060ed-115">Secure Sessions</span></span>](secure-sessions.md)  
 <span data-ttu-id="060ed-116">Omówienie zagadnień wymaganych podczas zabezpieczania sesji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="060ed-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="060ed-117">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="060ed-117">Working with Certificates</span></span>](working-with-certificates.md)  
 <span data-ttu-id="060ed-118">Wyjaśnienie niektórych typowych zadań wymaganych w przypadku używania certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="060ed-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="060ed-119">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="060ed-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="060ed-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="060ed-120">Related Sections</span></span>  
 [<span data-ttu-id="060ed-121">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="060ed-121">Security Concepts</span></span>](security-concepts.md)  
  
 [<span data-ttu-id="060ed-122">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="060ed-122">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="060ed-123">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="060ed-123">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
 [<span data-ttu-id="060ed-124">Wiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="060ed-124">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="060ed-125">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="060ed-125">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="060ed-126">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="060ed-126">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="060ed-127">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="060ed-127">Authorization</span></span>](authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="060ed-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="060ed-128">See also</span></span>

- [<span data-ttu-id="060ed-129">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="060ed-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- <span data-ttu-id="060ed-130">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="060ed-130">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
