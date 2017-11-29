---
title: Bezpieczne sesje
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 724ea72c52296c448ead80a8f357235d625f5842
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="secure-sessions"></a><span data-ttu-id="ebac1-102">Bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="ebac1-102">Secure Sessions</span></span>
<span data-ttu-id="ebac1-103">Funkcja [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to niezawodnej sesji, które gwarantują, komunikaty są odbierane w kolejności wysłania.</span><span class="sxs-lookup"><span data-stu-id="ebac1-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="ebac1-104">Tematy w tej sekcji omówiono wpływ zabezpieczenia wziąć pod uwagę podczas tworzenia niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="ebac1-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ebac1-105">niezawodne sesje, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="ebac1-105"> reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebac1-106">Jeśli wymagane jest personifikacji w systemie Windows XP, należy użyć bezpiecznej sesji bez token kontekstu zabezpieczeń stanową (SCT).</span><span class="sxs-lookup"><span data-stu-id="ebac1-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="ebac1-107">Gdy stanowe SCTs są używane z personifikacji, <xref:System.InvalidOperationException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="ebac1-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ebac1-108">[Nieobsługiwanych scenariuszy](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="ebac1-108"> [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ebac1-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ebac1-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="ebac1-110">Bezpieczne konwersacje i bezpieczne sesje</span><span class="sxs-lookup"><span data-stu-id="ebac1-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="ebac1-111">Bezpieczne konwersacje i bezpieczne sesje to samo.</span><span class="sxs-lookup"><span data-stu-id="ebac1-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="ebac1-112">W tym temacie opisano sposób bezpiecznej konwersacji działa, oraz kiedy i dlaczego używać ze wzorcem.</span><span class="sxs-lookup"><span data-stu-id="ebac1-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="ebac1-113">Porady: tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="ebac1-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="ebac1-114">Przedstawiono tworzenie bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="ebac1-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="ebac1-115">Porady: tworzenie kontekstu zabezpieczeń tokenu dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="ebac1-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="ebac1-116">Przeprowadzi Cię przez kroki tworzenia kolektywu serwerów sieci Web, które mają być przechowywane w stan i sesje z klientami.</span><span class="sxs-lookup"><span data-stu-id="ebac1-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="ebac1-117">Zagadnienia dotyczące zabezpieczeń dla bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="ebac1-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="ebac1-118">W tym artykule opisano uwagi dotyczące bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="ebac1-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="ebac1-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ebac1-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="ebac1-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ebac1-120">Related Sections</span></span>  
 [<span data-ttu-id="ebac1-121">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="ebac1-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="ebac1-122">Projektowanie i Implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="ebac1-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="ebac1-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebac1-123">See Also</span></span>  
 [<span data-ttu-id="ebac1-124">Porady: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="ebac1-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="ebac1-125">Ataki</span><span class="sxs-lookup"><span data-stu-id="ebac1-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="ebac1-126">Porady: Tworzenie usługi wymagającej użycia sesji</span><span class="sxs-lookup"><span data-stu-id="ebac1-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
