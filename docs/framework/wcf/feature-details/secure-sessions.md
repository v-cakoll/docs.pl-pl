---
title: Bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: d511a45d990e441c5dcfd8405794ec937c0278d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966073"
---
# <a name="secure-sessions"></a><span data-ttu-id="b535b-102">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="b535b-102">Secure Sessions</span></span>
<span data-ttu-id="b535b-103">Funkcja programu Windows Communication Foundation (WCF) to niezawodne sesje, które gwarantują otrzymywanie komunikatów w kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="b535b-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="b535b-104">W tematach w tej sekcji omówiono implikacje związane z zabezpieczeniami, które należy wziąć pod uwagę podczas tworzenia niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="b535b-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="b535b-105">Aby uzyskać więcej informacji na temat sesji niezawodnych, zobacz [using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="b535b-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b535b-106">Jeśli w systemie Windows XP jest wymagana personifikacja, należy użyć bezpiecznej sesji bez tokenu stanu zabezpieczenia stanowe (SCT).</span><span class="sxs-lookup"><span data-stu-id="b535b-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="b535b-107">Gdy stanowe SCTs są używane z personifikacją <xref:System.InvalidOperationException> , jest generowany.</span><span class="sxs-lookup"><span data-stu-id="b535b-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="b535b-108">Aby uzyskać więcej informacji, zobacz [scenariusze nieobsługiwane](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="b535b-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b535b-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b535b-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="b535b-110">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="b535b-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="b535b-111">Bezpieczne konwersacje i bezpieczne sesje są synonimami.</span><span class="sxs-lookup"><span data-stu-id="b535b-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="b535b-112">W tym temacie wyjaśniono, jak działa bezpieczna konwersacja oraz kiedy i dlaczego należy używać wzorca.</span><span class="sxs-lookup"><span data-stu-id="b535b-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="b535b-113">Instrukcje: Tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="b535b-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="b535b-114">Instruktaż przedstawia podstawy tworzenia bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="b535b-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="b535b-115">Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="b535b-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="b535b-116">W tym kroku opisano kroki tworzenia kolektywu serwerów sieci Web, które będą obsługiwać stan i sesje z klientami.</span><span class="sxs-lookup"><span data-stu-id="b535b-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="b535b-117">Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji</span><span class="sxs-lookup"><span data-stu-id="b535b-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="b535b-118">Opisuje specjalne zagadnienia dotyczące bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="b535b-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="b535b-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b535b-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="b535b-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b535b-120">Related Sections</span></span>  
 [<span data-ttu-id="b535b-121">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="b535b-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="b535b-122">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="b535b-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="b535b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b535b-123">See also</span></span>

- [<span data-ttu-id="b535b-124">Instrukcje: Włącz wykrywanie powtarzania komunikatów</span><span class="sxs-lookup"><span data-stu-id="b535b-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="b535b-125">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="b535b-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [<span data-ttu-id="b535b-126">Instrukcje: Tworzenie usługi wymagającej sesji</span><span class="sxs-lookup"><span data-stu-id="b535b-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
