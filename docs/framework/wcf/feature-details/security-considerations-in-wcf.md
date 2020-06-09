---
title: Zagadnienia dotyczące zabezpieczeń w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: ed0f018e0151e68afeb9a4747bf8a260faa184b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601039"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="7a2a5-102">Zagadnienia dotyczące zabezpieczeń w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7a2a5-102">Security Considerations in WCF</span></span>
<span data-ttu-id="7a2a5-103">W tematach w tej sekcji przedstawiono różne elementy związane z zabezpieczeniami, które należy wziąć pod uwagę podczas projektowania aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7a2a5-103">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a2a5-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7a2a5-104">In This Section</span></span>  
 [<span data-ttu-id="7a2a5-105">Ujawnianie informacji</span><span class="sxs-lookup"><span data-stu-id="7a2a5-105">Information Disclosure</span></span>](information-disclosure.md)  
 <span data-ttu-id="7a2a5-106">W tym artykule omówiono różne sposoby, w których informacje mogą być ujawnione lub zaatakowane oraz jak można je złagodzić.</span><span class="sxs-lookup"><span data-stu-id="7a2a5-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="7a2a5-107">Podniesienie uprawnień</span><span class="sxs-lookup"><span data-stu-id="7a2a5-107">Elevation of Privilege</span></span>](elevation-of-privilege.md)  
 <span data-ttu-id="7a2a5-108">W tym artykule omówiono skutki udzielenia uprawnień autoryzacji osoby atakującej poza tymi, które zostały początkowo przyznane i jak można je złagodzić.</span><span class="sxs-lookup"><span data-stu-id="7a2a5-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="7a2a5-109">Odmowa usługi</span><span class="sxs-lookup"><span data-stu-id="7a2a5-109">Denial of Service</span></span>](denial-of-service.md)  
 <span data-ttu-id="7a2a5-110">W tym artykule omówiono, co się dzieje, gdy system nie może prawidłowo przetwarzać komunikatów i jak można je ograniczyć.</span><span class="sxs-lookup"><span data-stu-id="7a2a5-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="7a2a5-111">Manipulowanie</span><span class="sxs-lookup"><span data-stu-id="7a2a5-111">Tampering</span></span>](tampering.md)  
 <span data-ttu-id="7a2a5-112">W tym artykule omówiono zmiany komunikatów lub dostarczania komunikatów oraz sposób ich ograniczania.</span><span class="sxs-lookup"><span data-stu-id="7a2a5-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="7a2a5-113">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="7a2a5-113">Replay Attacks</span></span>](replay-attacks.md)  
 <span data-ttu-id="7a2a5-114">W tym artykule omówiono, co się dzieje, gdy osoba atakująca skopiuje strumień komunikatów między dwiema stronami i odtwarza strumień do jednej lub kilku stron, a także jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="7a2a5-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="7a2a5-115">Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji</span><span class="sxs-lookup"><span data-stu-id="7a2a5-115">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="7a2a5-116">W tym artykule omówiono następujące elementy, które mają wpływ na zabezpieczenia podczas implementowania bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="7a2a5-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="7a2a5-117">Nieobsługiwane scenariusze</span><span class="sxs-lookup"><span data-stu-id="7a2a5-117">Unsupported Scenarios</span></span>](unsupported-scenarios.md)  
 <span data-ttu-id="7a2a5-118">Wyświetla listę różnych scenariuszy, które nie obsługują określonego aspektu zabezpieczeń i należy je unikać lub rozważać.</span><span class="sxs-lookup"><span data-stu-id="7a2a5-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7a2a5-119">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="7a2a5-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="7a2a5-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7a2a5-120">Related Sections</span></span>  
 [<span data-ttu-id="7a2a5-121">Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="7a2a5-121">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="7a2a5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a2a5-122">See also</span></span>

- [<span data-ttu-id="7a2a5-123">Bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="7a2a5-123">Security</span></span>](security.md)
