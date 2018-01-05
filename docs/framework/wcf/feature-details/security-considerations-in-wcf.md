---
title: "Zagadnienia dotyczące zabezpieczeń w programie WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
caps.latest.revision: "49"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f35bd56bdc69f8c57a7e46984778051b57b7a06a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="41925-102">Zagadnienia dotyczące zabezpieczeń w programie WCF</span><span class="sxs-lookup"><span data-stu-id="41925-102">Security Considerations in WCF</span></span>
<span data-ttu-id="41925-103">Tematy w tej sekcji listy różne elementy związane z zabezpieczeniami wziąć pod uwagę podczas projektowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41925-103">The topics in this section list various security-related items to consider when designing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41925-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="41925-104">In This Section</span></span>  
 [<span data-ttu-id="41925-105">Ujawnianie informacji</span><span class="sxs-lookup"><span data-stu-id="41925-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="41925-106">W tym artykule omówiono różne sposoby, czy informacje mogą być ujawniane lub ataku i jak zaradzić.</span><span class="sxs-lookup"><span data-stu-id="41925-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="41925-107">Podniesienie uprawnień</span><span class="sxs-lookup"><span data-stu-id="41925-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="41925-108">Omówienie skutków nadanie uprawnień autoryzacji atakująca poza tymi, które początkowo przyznawane i sposobu zaradzić.</span><span class="sxs-lookup"><span data-stu-id="41925-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="41925-109">Odmowa usługi</span><span class="sxs-lookup"><span data-stu-id="41925-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="41925-110">W tym artykule omówiono, co się stanie, gdy system jest nie można przetworzyć wiadomości odpowiednio i sposobie jej unikania.</span><span class="sxs-lookup"><span data-stu-id="41925-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="41925-111">Manipulowanie</span><span class="sxs-lookup"><span data-stu-id="41925-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="41925-112">W tym artykule omówiono zmiany wiadomości lub dostarczenia komunikatów i sposobie jej unikania.</span><span class="sxs-lookup"><span data-stu-id="41925-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="41925-113">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="41925-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="41925-114">W tym artykule omówiono, co się stanie, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarzaniem strumienia do co najmniej jednej strony oraz sposób ograniczenia tego.</span><span class="sxs-lookup"><span data-stu-id="41925-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="41925-115">Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji</span><span class="sxs-lookup"><span data-stu-id="41925-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="41925-116">W tym artykule omówiono następujące elementy, które mają wpływ na zabezpieczeń podczas implementowania bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="41925-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="41925-117">Nieobsługiwane scenariusze</span><span class="sxs-lookup"><span data-stu-id="41925-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="41925-118">Wyświetla listę różnych scenariuszy, które nie obsługują określonej proporcji zabezpieczeń i powinna być unikać lub uznane za.</span><span class="sxs-lookup"><span data-stu-id="41925-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="41925-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="41925-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="41925-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="41925-120">Related Sections</span></span>  
 [<span data-ttu-id="41925-121">Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="41925-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="41925-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41925-122">See Also</span></span>  
 [<span data-ttu-id="41925-123">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="41925-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
