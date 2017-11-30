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
ms.openlocfilehash: c0af5a5d96f20b2ba5118909a3f0c5ba405bdb11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="c5d2f-102">Zagadnienia dotyczące zabezpieczeń w programie WCF</span><span class="sxs-lookup"><span data-stu-id="c5d2f-102">Security Considerations in WCF</span></span>
<span data-ttu-id="c5d2f-103">Tematy w tej sekcji listy różne elementy związane z zabezpieczeniami wziąć pod uwagę podczas projektowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5d2f-103">The topics in this section list various security-related items to consider when designing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5d2f-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c5d2f-104">In This Section</span></span>  
 [<span data-ttu-id="c5d2f-105">Ujawnienie informacji</span><span class="sxs-lookup"><span data-stu-id="c5d2f-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="c5d2f-106">W tym artykule omówiono różne sposoby, czy informacje mogą być ujawniane lub ataku i jak zaradzić.</span><span class="sxs-lookup"><span data-stu-id="c5d2f-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="c5d2f-107">Podniesienie uprawnień</span><span class="sxs-lookup"><span data-stu-id="c5d2f-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="c5d2f-108">Omówienie skutków nadanie uprawnień autoryzacji atakująca poza tymi, które początkowo przyznawane i sposobu zaradzić.</span><span class="sxs-lookup"><span data-stu-id="c5d2f-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="c5d2f-109">Odmowa usługi</span><span class="sxs-lookup"><span data-stu-id="c5d2f-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="c5d2f-110">W tym artykule omówiono, co się stanie, gdy system jest nie można przetworzyć wiadomości odpowiednio i sposobie jej unikania.</span><span class="sxs-lookup"><span data-stu-id="c5d2f-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="c5d2f-111">Manipulowanie</span><span class="sxs-lookup"><span data-stu-id="c5d2f-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="c5d2f-112">W tym artykule omówiono zmiany wiadomości lub dostarczenia komunikatów i sposobie jej unikania.</span><span class="sxs-lookup"><span data-stu-id="c5d2f-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="c5d2f-113">Ataki</span><span class="sxs-lookup"><span data-stu-id="c5d2f-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="c5d2f-114">W tym artykule omówiono, co się stanie, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarzaniem strumienia do co najmniej jednej strony oraz sposób ograniczenia tego.</span><span class="sxs-lookup"><span data-stu-id="c5d2f-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="c5d2f-115">Zagadnienia dotyczące zabezpieczeń dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="c5d2f-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="c5d2f-116">W tym artykule omówiono następujące elementy, które mają wpływ na zabezpieczeń podczas implementowania bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="c5d2f-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="c5d2f-117">Nieobsługiwane scenariusze</span><span class="sxs-lookup"><span data-stu-id="c5d2f-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="c5d2f-118">Wyświetla listę różnych scenariuszy, które nie obsługują określonej proporcji zabezpieczeń i powinna być unikać lub uznane za.</span><span class="sxs-lookup"><span data-stu-id="c5d2f-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c5d2f-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c5d2f-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="c5d2f-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c5d2f-120">Related Sections</span></span>  
 [<span data-ttu-id="c5d2f-121">Wskazówki dotyczące zabezpieczeń i najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="c5d2f-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="c5d2f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5d2f-122">See Also</span></span>  
 [<span data-ttu-id="c5d2f-123">Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c5d2f-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
