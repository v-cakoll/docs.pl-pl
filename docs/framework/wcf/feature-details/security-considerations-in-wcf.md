---
title: Zagadnienia dotyczące zabezpieczeń w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: 6cc19f7719b9cdbcd3852c99f450c1d728dc833b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745998"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="19934-102">Zagadnienia dotyczące zabezpieczeń w programie WCF</span><span class="sxs-lookup"><span data-stu-id="19934-102">Security Considerations in WCF</span></span>
<span data-ttu-id="19934-103">Tematy w tej sekcji listy różne elementy związane z zabezpieczeniami wziąć pod uwagę podczas projektowania aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="19934-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19934-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="19934-104">In This Section</span></span>  
 [<span data-ttu-id="19934-105">Ujawnianie informacji</span><span class="sxs-lookup"><span data-stu-id="19934-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="19934-106">W tym artykule omówiono różne sposoby, czy informacje mogą być ujawniane lub ataku i jak rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="19934-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="19934-107">Podniesienie uprawnień</span><span class="sxs-lookup"><span data-stu-id="19934-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="19934-108">W tym artykule omówiono wpływ udzielenia uprawnień autoryzacji osoba atakująca poza tymi, które początkowo przyznane i jak rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="19934-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="19934-109">Odmowa usługi</span><span class="sxs-lookup"><span data-stu-id="19934-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="19934-110">W tym artykule omówiono, co się stanie, gdy system jest w stanie odpowiednio przetwarzania komunikatów i sposobu jego wyeliminowania.</span><span class="sxs-lookup"><span data-stu-id="19934-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="19934-111">Manipulowanie</span><span class="sxs-lookup"><span data-stu-id="19934-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="19934-112">W tym artykule omówiono zmiany wiadomości lub dostarczania wiadomości i sposobu jego wyeliminowania.</span><span class="sxs-lookup"><span data-stu-id="19934-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="19934-113">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="19934-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="19934-114">W tym artykule omówiono, co się stanie, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarza strumienia do co najmniej jednej strony i jak rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="19934-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="19934-115">Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji</span><span class="sxs-lookup"><span data-stu-id="19934-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="19934-116">W tym artykule omówiono następujące elementy, które dotyczą zabezpieczeń podczas implementowania bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="19934-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="19934-117">Nieobsługiwane scenariusze</span><span class="sxs-lookup"><span data-stu-id="19934-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="19934-118">Wyświetla listę różnych scenariuszy, które nie obsługują danego aspekt zabezpieczeń i należy unikać lub uznawane za.</span><span class="sxs-lookup"><span data-stu-id="19934-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="19934-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="19934-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="19934-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="19934-120">Related Sections</span></span>  
 [<span data-ttu-id="19934-121">Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="19934-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="19934-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19934-122">See also</span></span>
- [<span data-ttu-id="19934-123">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="19934-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
