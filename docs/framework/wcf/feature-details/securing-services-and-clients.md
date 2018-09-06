---
title: Zabezpieczanie usług i klientów
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 60aa4da95666de01daa087c4c8e826c8cf72ba85
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43788652"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="ec7d2-102">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="ec7d2-102">Securing Services and Clients</span></span>
<span data-ttu-id="ec7d2-103">Informacje przedstawione w tej sekcji skupiono się na programowaniu zabezpieczeń w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ec7d2-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ec7d2-104">Ogólnie rzecz biorąc w tym wybranie odpowiedniego powiązania dostarczane przez system, ustawienie właściwości elementu zabezpieczeń, a następnie ustawić właściwości zachowania usług, które określają sposób, jak pobrać poświadczenia do użycia przez usługę lub klienta.</span><span class="sxs-lookup"><span data-stu-id="ec7d2-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="ec7d2-105">Techniki te obejmują wymagania dotyczące zabezpieczeń większości użytkowników w przypadku większości scenariuszy, jak pokazano na [typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="ec7d2-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="ec7d2-106">Jeśli dany scenariusz wymaga więcej funkcji, należy najpierw sprawdzić [możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); Jeśli rozwiązanie nie jest widoczny, zobacz [rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md).</span><span class="sxs-lookup"><span data-stu-id="ec7d2-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="ec7d2-107">Jeśli tworzysz (lub współdziałanie z) system, który korzysta z zaawansowanych oświadczeń, zobacz Tematy w [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="ec7d2-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec7d2-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ec7d2-108">In This Section</span></span>  
 [<span data-ttu-id="ec7d2-109">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="ec7d2-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="ec7d2-110">Omówienie modelu programowania, używany do zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ec7d2-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="ec7d2-111">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="ec7d2-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="ec7d2-112">Omówienie sposobu Zabezpieczanie komunikatów za pośrednictwem warstwy transportowej.</span><span class="sxs-lookup"><span data-stu-id="ec7d2-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="ec7d2-113">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="ec7d2-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="ec7d2-114">Zawiera podsumowanie powody do korzystania z zabezpieczeń na poziomie komunikatu w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ec7d2-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="ec7d2-115">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="ec7d2-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="ec7d2-116">Omówienie zagadnień, wymagany, gdy zabezpieczania sesji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="ec7d2-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="ec7d2-117">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="ec7d2-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="ec7d2-118">Wyjaśnienie niektórych typowych zadań, które są wymagane podczas korzystania z certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="ec7d2-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ec7d2-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ec7d2-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="ec7d2-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ec7d2-120">Related Sections</span></span>  
 [<span data-ttu-id="ec7d2-121">Pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ec7d2-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="ec7d2-122">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ec7d2-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="ec7d2-123">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ec7d2-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="ec7d2-124">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ec7d2-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="ec7d2-125">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="ec7d2-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="ec7d2-126">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ec7d2-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="ec7d2-127">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="ec7d2-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec7d2-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec7d2-128">See Also</span></span>  
 [<span data-ttu-id="ec7d2-129">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="ec7d2-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="ec7d2-130">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="ec7d2-130">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
