---
title: Bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: cb02adc7514e27175088e7664b12e45bc8ca5cd9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590088"
---
# <a name="secure-sessions"></a><span data-ttu-id="e2ef5-102">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="e2ef5-102">Secure Sessions</span></span>
<span data-ttu-id="e2ef5-103">Funkcja programu Windows Communication Foundation (WCF) to niezawodne sesje, które gwarantują otrzymywanie komunikatów w kolejności, w jakiej zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="e2ef5-104">W tematach w tej sekcji omówiono implikacje związane z zabezpieczeniami, które należy wziąć pod uwagę podczas tworzenia niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="e2ef5-105">Aby uzyskać więcej informacji na temat sesji niezawodnych, zobacz [using Sessions](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="e2ef5-105">For more information about reliable sessions, see [Using Sessions](../using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2ef5-106">Jeśli w systemie Windows XP jest wymagana personifikacja, należy użyć bezpiecznej sesji bez tokenu stanu zabezpieczenia stanowe (SCT).</span><span class="sxs-lookup"><span data-stu-id="e2ef5-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="e2ef5-107">Gdy stanowe SCTs są używane z personifikacją, <xref:System.InvalidOperationException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="e2ef5-108">Aby uzyskać więcej informacji, zobacz [scenariusze nieobsługiwane](unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="e2ef5-108">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2ef5-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e2ef5-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="e2ef5-110">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="e2ef5-110">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)|<span data-ttu-id="e2ef5-111">Bezpieczne konwersacje i bezpieczne sesje są synonimami.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="e2ef5-112">W tym temacie wyjaśniono, jak działa bezpieczna konwersacja oraz kiedy i dlaczego należy używać wzorca.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="e2ef5-113">Instrukcje: tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="e2ef5-113">How to: Create a Secure Session</span></span>](how-to-create-a-secure-session.md)|<span data-ttu-id="e2ef5-114">Instruktaż przedstawia podstawy tworzenia bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="e2ef5-115">Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="e2ef5-115">How to: Create a Security Context Token for a Secure Session</span></span>](how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="e2ef5-116">W tym kroku opisano kroki tworzenia kolektywu serwerów sieci Web, które będą obsługiwać stan i sesje z klientami.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="e2ef5-117">Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji</span><span class="sxs-lookup"><span data-stu-id="e2ef5-117">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)|<span data-ttu-id="e2ef5-118">Opisuje specjalne zagadnienia dotyczące bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="e2ef5-119">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="e2ef5-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="e2ef5-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e2ef5-120">Related Sections</span></span>  
 [<span data-ttu-id="e2ef5-121">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="e2ef5-121">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="e2ef5-122">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="e2ef5-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2ef5-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2ef5-123">See also</span></span>

- [<span data-ttu-id="e2ef5-124">Instrukcje: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="e2ef5-124">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="e2ef5-125">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="e2ef5-125">Replay Attacks</span></span>](replay-attacks.md)
- [<span data-ttu-id="e2ef5-126">Instrukcje: tworzenie usługi wymagającej użycia sesji</span><span class="sxs-lookup"><span data-stu-id="e2ef5-126">How to: Create a Service That Requires Sessions</span></span>](how-to-create-a-service-that-requires-sessions.md)
