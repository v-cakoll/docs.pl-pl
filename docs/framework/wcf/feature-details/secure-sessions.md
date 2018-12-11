---
title: Bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 1f3a1e23f7cac2540216365acfca5c23cddfce71
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126695"
---
# <a name="secure-sessions"></a><span data-ttu-id="c259d-102">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="c259d-102">Secure Sessions</span></span>
<span data-ttu-id="c259d-103">Funkcja Windows Communication Foundation (WCF) jest niezawodne sesje, które gwarantuje, że komunikaty są odbierane w kolejności, w której zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="c259d-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="c259d-104">W tematach w tej sekcji omówiono skutki dla bezpieczeństwa wziąć pod uwagę podczas tworzenia niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="c259d-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="c259d-105">Aby uzyskać więcej informacji o sesjach niezawodnych, zobacz [przy użyciu sesji](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="c259d-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c259d-106">Podczas personifikacji jest wymagane w systemie Windows XP, należy użyć bezpiecznej sesji bez tokenu kontekstu zabezpieczeń stanową (SCT).</span><span class="sxs-lookup"><span data-stu-id="c259d-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="c259d-107">Stosowania stanowych SCTs personifikacji, <xref:System.InvalidOperationException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="c259d-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="c259d-108">Aby uzyskać więcej informacji, zobacz [nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="c259d-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c259d-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c259d-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="c259d-110">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="c259d-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="c259d-111">Bezpieczne konwersacje i bezpieczne sesje oznaczają to samo.</span><span class="sxs-lookup"><span data-stu-id="c259d-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="c259d-112">W tym temacie opisano sposób działania bezpiecznej konwersacji, a kiedy i dlaczego używać wzorca.</span><span class="sxs-lookup"><span data-stu-id="c259d-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="c259d-113">Jak: Tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="c259d-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="c259d-114">Przedstawiono tworzenie bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="c259d-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="c259d-115">Jak: Utwórz kontekst zabezpieczeń tokenu dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="c259d-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="c259d-116">Opisano kroki tworzenia kolektywu serwerów sieci Web, który będzie utrzymywać stan i sesje z klientami.</span><span class="sxs-lookup"><span data-stu-id="c259d-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="c259d-117">Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji</span><span class="sxs-lookup"><span data-stu-id="c259d-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="c259d-118">W tym artykule opisano specjalne zagadnienia dotyczące bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="c259d-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="c259d-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c259d-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="c259d-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c259d-120">Related Sections</span></span>  
 [<span data-ttu-id="c259d-121">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="c259d-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="c259d-122">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="c259d-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="c259d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c259d-123">See Also</span></span>  
 [<span data-ttu-id="c259d-124">Jak: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="c259d-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="c259d-125">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="c259d-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="c259d-126">Jak: Tworzenie usługi wymagającej użycia sesji</span><span class="sxs-lookup"><span data-stu-id="c259d-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
