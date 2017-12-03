---
title: "Ataki oparte na metodzie powtórzeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd96404adea7fb8e7d59dcea322b2d3832f2bfe4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="replay-attacks"></a><span data-ttu-id="5427d-102">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="5427d-102">Replay Attacks</span></span>
<span data-ttu-id="5427d-103">A *powtarzania ataku* występuje, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarzaniem strumienia do jednego lub więcej stron.</span><span class="sxs-lookup"><span data-stu-id="5427d-103">A *replay attack* occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="5427d-104">Chyba że skorygowane, komputery mogą ulec ataku przetworzyć strumienia jako istotnych wiadomości, co w zakresie zły konsekwencje, takie jak nadmiarowe zamówień elementu.</span><span class="sxs-lookup"><span data-stu-id="5427d-104">Unless mitigated, the computers subject to the attack process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a><span data-ttu-id="5427d-105">Powiązania mogą być narażone na ataki odbicia</span><span class="sxs-lookup"><span data-stu-id="5427d-105">Bindings May Be Subject to Reflection Attacks</span></span>  
 <span data-ttu-id="5427d-106">*Odbicie ataków* są odtworzenie nadawcy wiadomości tak, jakby pochodzą od odbiornika jako odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="5427d-106">*Reflection attacks* are replays of messages back to a sender as if they came from the receiver as the reply.</span></span> <span data-ttu-id="5427d-107">Standardowe *wykrywania powtarzania* w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanizmu nie automatycznie obsługuje to.</span><span class="sxs-lookup"><span data-stu-id="5427d-107">The standard *replay detection* in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanism does not automatically handle this.</span></span>  
  
 <span data-ttu-id="5427d-108">Odbicie ataków zostały skorygowane domyślnie, ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model usługi dodaje identyfikator podpisanej wiadomości do komunikatów żądań i oczekuje zalogowany `relates-to` nagłówka wiadomości odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="5427d-108">Reflection attacks are mitigated by default because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service model adds a signed message ID to request messages and expects a signed `relates-to` header on response messages.</span></span> <span data-ttu-id="5427d-109">W związku z tym komunikat żądania nie może być powtórzone w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="5427d-109">Consequently, the request message cannot be replayed as a response.</span></span> <span data-ttu-id="5427d-110">W scenariuszach zabezpieczoną wiadomość niezawodnej (RM) odbicia ataki są niewielkie, ponieważ:</span><span class="sxs-lookup"><span data-stu-id="5427d-110">In secure reliable message (RM) scenarios, reflection attacks are mitigated because:</span></span>  
  
-   <span data-ttu-id="5427d-111">Tworzenie sekwencji i Utwórz sekwencji odpowiedzi komunikat schematy są różne.</span><span class="sxs-lookup"><span data-stu-id="5427d-111">The create sequence and create sequence response message schemas are different.</span></span>  
  
-   <span data-ttu-id="5427d-112">Jednostronne sekwencji komunikatów sekwencji, których klient wysyła nie odtwarzany powrotu do tego, ponieważ klient nie może zrozumieć takich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5427d-112">For simplex sequences, sequence messages the client sends cannot be replayed back to it because the client cannot understand such messages.</span></span>  
  
-   <span data-ttu-id="5427d-113">Dupleks sekwencji dwóch sekwencji identyfikatory muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="5427d-113">For duplex sequences, the two sequence IDs must be unique.</span></span> <span data-ttu-id="5427d-114">W związku z tym wiadomości wychodzącej sekwencji nie może być powtórzone zwrotnym w formie wiadomości przychodzących sekwencji (wszystkie nagłówki sekwencji i treść są podpisywane, zbyt).</span><span class="sxs-lookup"><span data-stu-id="5427d-114">Thus, an outgoing sequence message cannot be replayed back as an incoming sequence message (all sequence headers and bodies are signed, too).</span></span>  
  
 <span data-ttu-id="5427d-115">Tylko powiązania, które są narażone na ataki odbicia są bez WS-Addressing: niestandardowego powiązania, które WS-Addressing wyłączone i użyj symetrycznego opartego na kluczach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5427d-115">The only bindings that are susceptible to reflection attacks are those without WS-Addressing: custom bindings that have WS-Addressing disabled and use the symmetric key-based security.</span></span> <span data-ttu-id="5427d-116"><xref:System.ServiceModel.BasicHttpBinding> Nie jest używana WS-Addressing domyślnie, ale nie używa zabezpieczenia oparte na klucza symetrycznego w taki sposób, który pozwala być narażone na atak.</span><span class="sxs-lookup"><span data-stu-id="5427d-116">The <xref:System.ServiceModel.BasicHttpBinding> does not use WS-Addressing by default, but it does not use symmetric key-based security in a way that allows it to be vulnerable to this attack.</span></span>  
  
 <span data-ttu-id="5427d-117">Środki zaradcze dla niestandardowego powiązania jest ustanawia kontekstu zabezpieczeń lub wymagają nagłówków WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="5427d-117">The mitigation for custom bindings is to not establish security context or to require WS-Addressing headers.</span></span>  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a><span data-ttu-id="5427d-118">Kolektywu serwerów sieci Web: Żądanie odtworzenie atakująca wiele węzłów</span><span class="sxs-lookup"><span data-stu-id="5427d-118">Web Farm: Attacker Replays Request to Multiple Nodes</span></span>  
 <span data-ttu-id="5427d-119">Klient używa usługi, która jest zaimplementowana na farmie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5427d-119">A client uses a service that is implemented on a Web farm.</span></span> <span data-ttu-id="5427d-120">Osoba atakująca odtwarzaniem żądanie wysłane do jednego węzła w farmie do innego węzła w farmie.</span><span class="sxs-lookup"><span data-stu-id="5427d-120">An attacker replays a request that was sent to one node in the farm to another node in the farm.</span></span> <span data-ttu-id="5427d-121">Ponadto po uruchomieniu usługi pamięci podręcznej powtórzeń jest opróżniany, co pozwala osobie atakującej powtarzania żądania.</span><span class="sxs-lookup"><span data-stu-id="5427d-121">In addition, if a service is restarted, the replay cache is flushed, allowing an attacker to replay the request.</span></span> <span data-ttu-id="5427d-122">(Pamięć podręczna zawiera wartości podpisu używane wcześniej widziany komunikat i uniemożliwia odtworzenie, więc te podpisy mogą być użyte tylko raz.</span><span class="sxs-lookup"><span data-stu-id="5427d-122">(The cache contains used, previously seen message signature values and prevents replays so those signatures can be used only once.</span></span> <span data-ttu-id="5427d-123">Pamięci podręczne powtarzania nie są udostępniane na farmie sieci Web.)</span><span class="sxs-lookup"><span data-stu-id="5427d-123">Replay caches are not shared across a Web farm.)</span></span>  
  
 <span data-ttu-id="5427d-124">Następujące czynniki:</span><span class="sxs-lookup"><span data-stu-id="5427d-124">Mitigations include:</span></span>  
  
-   <span data-ttu-id="5427d-125">Komunikat tryb zabezpieczeń za pomocą tokenów kontekstów zabezpieczeń stanową (z lub bez bezpiecznej konwersacji włączona).</span><span class="sxs-lookup"><span data-stu-id="5427d-125">Use message mode security with stateful security context tokens (with or without secure conversation enabled).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="5427d-126">[Jak: utworzyć kontekstu zabezpieczeń dla bezpiecznej sesji tokenu](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="5427d-126"> [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
-   <span data-ttu-id="5427d-127">Skonfiguruj usługę, aby użyć zabezpieczeń na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="5427d-127">Configure the service to use transport-level security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5427d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5427d-128">See Also</span></span>  
 [<span data-ttu-id="5427d-129">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5427d-129">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="5427d-130">Ujawnienie informacji</span><span class="sxs-lookup"><span data-stu-id="5427d-130">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="5427d-131">Podniesienie uprawnień</span><span class="sxs-lookup"><span data-stu-id="5427d-131">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="5427d-132">Odmowa usługi</span><span class="sxs-lookup"><span data-stu-id="5427d-132">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="5427d-133">Manipulowanie</span><span class="sxs-lookup"><span data-stu-id="5427d-133">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [<span data-ttu-id="5427d-134">Nieobsługiwane scenariusze</span><span class="sxs-lookup"><span data-stu-id="5427d-134">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
