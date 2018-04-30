---
title: Bezpieczne sesje
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 068615510d7e1d73ae260441ccef6536ee6ff317
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="secure-sessions"></a><span data-ttu-id="13b0c-102">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="13b0c-102">Secure Sessions</span></span>
<span data-ttu-id="13b0c-103">Funkcja [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to niezawodnej sesji, które gwarantują, komunikaty są odbierane w kolejności wysłania.</span><span class="sxs-lookup"><span data-stu-id="13b0c-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="13b0c-104">Tematy w tej sekcji omówiono wpływ zabezpieczenia wziąć pod uwagę podczas tworzenia niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="13b0c-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="13b0c-105">Aby uzyskać więcej informacji na temat niezawodnej sesji, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="13b0c-105">For more information about reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13b0c-106">Jeśli wymagane jest personifikacji w systemie Windows XP, należy użyć bezpiecznej sesji bez token kontekstu zabezpieczeń stanową (SCT).</span><span class="sxs-lookup"><span data-stu-id="13b0c-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="13b0c-107">Gdy stanowe SCTs są używane z personifikacji, <xref:System.InvalidOperationException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="13b0c-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="13b0c-108">Aby uzyskać więcej informacji, zobacz [nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="13b0c-108">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13b0c-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="13b0c-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="13b0c-110">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="13b0c-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="13b0c-111">Bezpieczne konwersacje i bezpieczne sesje to samo.</span><span class="sxs-lookup"><span data-stu-id="13b0c-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="13b0c-112">W tym temacie opisano sposób bezpiecznej konwersacji działa, oraz kiedy i dlaczego używać ze wzorcem.</span><span class="sxs-lookup"><span data-stu-id="13b0c-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="13b0c-113">Instrukcje: tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="13b0c-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="13b0c-114">Przedstawiono tworzenie bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="13b0c-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="13b0c-115">Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="13b0c-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="13b0c-116">Przeprowadzi Cię przez kroki tworzenia kolektywu serwerów sieci Web, które mają być przechowywane w stan i sesje z klientami.</span><span class="sxs-lookup"><span data-stu-id="13b0c-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="13b0c-117">Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji</span><span class="sxs-lookup"><span data-stu-id="13b0c-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="13b0c-118">W tym artykule opisano uwagi dotyczące bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="13b0c-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="13b0c-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="13b0c-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="13b0c-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="13b0c-120">Related Sections</span></span>  
 [<span data-ttu-id="13b0c-121">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="13b0c-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="13b0c-122">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="13b0c-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="13b0c-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13b0c-123">See Also</span></span>  
 [<span data-ttu-id="13b0c-124">Instrukcje: włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="13b0c-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="13b0c-125">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="13b0c-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="13b0c-126">Instrukcje: tworzenie usługi wymagającej użycia sesji</span><span class="sxs-lookup"><span data-stu-id="13b0c-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
