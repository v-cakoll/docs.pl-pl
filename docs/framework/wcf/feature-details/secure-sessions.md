---
title: Bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
author: BrucePerlerMS
ms.openlocfilehash: 09c261afb2c64a46fc1f4619c4ec6b2e87b3fbbf
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847389"
---
# <a name="secure-sessions"></a><span data-ttu-id="50bb0-102">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="50bb0-102">Secure Sessions</span></span>
<span data-ttu-id="50bb0-103">Funkcja Windows Communication Foundation (WCF) jest niezawodne sesje, które gwarantuje, że komunikaty są odbierane w kolejności, w której zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="50bb0-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="50bb0-104">W tematach w tej sekcji omówiono skutki dla bezpieczeństwa wziąć pod uwagę podczas tworzenia niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="50bb0-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="50bb0-105">Aby uzyskać więcej informacji o sesjach niezawodnych, zobacz [przy użyciu sesji](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="50bb0-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50bb0-106">Podczas personifikacji jest wymagane w systemie Windows XP, należy użyć bezpiecznej sesji bez tokenu kontekstu zabezpieczeń stanową (SCT).</span><span class="sxs-lookup"><span data-stu-id="50bb0-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="50bb0-107">Stosowania stanowych SCTs personifikacji, <xref:System.InvalidOperationException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="50bb0-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="50bb0-108">Aby uzyskać więcej informacji, zobacz [nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="50bb0-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50bb0-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="50bb0-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="50bb0-110">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="50bb0-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="50bb0-111">Bezpieczne konwersacje i bezpieczne sesje oznaczają to samo.</span><span class="sxs-lookup"><span data-stu-id="50bb0-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="50bb0-112">W tym temacie opisano sposób działania bezpiecznej konwersacji, a kiedy i dlaczego używać wzorca.</span><span class="sxs-lookup"><span data-stu-id="50bb0-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="50bb0-113">Instrukcje: tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="50bb0-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="50bb0-114">Przedstawiono tworzenie bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="50bb0-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="50bb0-115">Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="50bb0-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="50bb0-116">Opisano kroki tworzenia kolektywu serwerów sieci Web, który będzie utrzymywać stan i sesje z klientami.</span><span class="sxs-lookup"><span data-stu-id="50bb0-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="50bb0-117">Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji</span><span class="sxs-lookup"><span data-stu-id="50bb0-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="50bb0-118">W tym artykule opisano specjalne zagadnienia dotyczące bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="50bb0-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="50bb0-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="50bb0-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="50bb0-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="50bb0-120">Related Sections</span></span>  
 [<span data-ttu-id="50bb0-121">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="50bb0-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="50bb0-122">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="50bb0-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="50bb0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50bb0-123">See Also</span></span>  
 [<span data-ttu-id="50bb0-124">Instrukcje: włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="50bb0-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="50bb0-125">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="50bb0-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="50bb0-126">Instrukcje: tworzenie usługi wymagającej użycia sesji</span><span class="sxs-lookup"><span data-stu-id="50bb0-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
