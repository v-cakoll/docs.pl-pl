---
title: "Pamięci podręcznej zasad interakcji — maksymalny wiek i nieaktualności maksymalny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: baec376501feb70e4a9ceb3f33ac66fa76b91ac1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="8e605-102">Pamięci podręcznej zasad interakcji — maksymalny wiek i nieaktualności maksymalny</span><span class="sxs-lookup"><span data-stu-id="8e605-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="8e605-103">Aby upewnić się, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcji klienta pamięci podręcznej zasad serwera ponownego sprawdzania poprawności wymagań i zawsze powoduje najbardziej zachowawcze zasady pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8e605-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="8e605-104">Wszystkie przykłady w tym temacie przedstawiono zasady z zasobem, który jest buforowana w dniu 1 stycznia i wygaśnie w dniu 4 stycznia w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8e605-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="8e605-105">W poniższych przykładach, wartość maksymalna nieaktualności (`maxStale`) jest używany w połączeniu z maksymalny wiek (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="8e605-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
-   <span data-ttu-id="8e605-106">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 5 dni, a nie określa `maxStale` wartość, według `maxAge` wartość, zawartość będzie można używać do 6 stycznia.</span><span class="sxs-lookup"><span data-stu-id="8e605-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="8e605-107">Jednak zgodnie z wymaganiami ponownego sprawdzania poprawności serwera, zawartość wygasa w styczniu 4.</span><span class="sxs-lookup"><span data-stu-id="8e605-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="8e605-108">Ponieważ data wygaśnięcia zawartości jest bardziej zachowawcze (wcześniej), ma pierwszeństwo przed `maxAge` zasad.</span><span class="sxs-lookup"><span data-stu-id="8e605-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="8e605-109">W związku z tym zawartość wygaśnie w dniu 4 stycznia i musi ponownie sprawdzić poprawności nawet, jeśli nie został osiągnięty maksymalny wiek.</span><span class="sxs-lookup"><span data-stu-id="8e605-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
-   <span data-ttu-id="8e605-110">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 5 dni i `maxStale` = 3 dni, zgodnie z `maxAge` wartości, zawartość będzie można używać do 6 stycznia.</span><span class="sxs-lookup"><span data-stu-id="8e605-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="8e605-111">Zgodnie z `maxStale` wartości, zawartość będzie można używać do 7 stycznia.</span><span class="sxs-lookup"><span data-stu-id="8e605-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="8e605-112">W związku z tym zawartość pobiera sprawdzony ponownie na styczeń 6.</span><span class="sxs-lookup"><span data-stu-id="8e605-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
-   <span data-ttu-id="8e605-113">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 5 dni i `maxStale` = 1 dzień, zgodnie z `maxAge` wartości, zawartość będzie można używać do 6 stycznia.</span><span class="sxs-lookup"><span data-stu-id="8e605-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="8e605-114">Zgodnie z `maxStale` wartości, zawartość będzie można używać do 5 stycznia.</span><span class="sxs-lookup"><span data-stu-id="8e605-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="8e605-115">W związku z tym zawartość pobiera sprawdzony ponownie na styczeń 5.</span><span class="sxs-lookup"><span data-stu-id="8e605-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="8e605-116">Maksymalny wiek jest wcześniejsza niż data wygaśnięcia zawartości, zachowanie buforowania w bardziej zachowawcze zawsze obowiązują, a wartość maksymalna nieaktualności nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="8e605-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="8e605-117">Poniższe przykłady przedstawiają wpływu ustawienia nieaktualności maksymalną (`maxStale`) wartość przy maksymalny wiek (`maxAge`) zostanie osiągnięty wygaśnięcia zawartości:</span><span class="sxs-lookup"><span data-stu-id="8e605-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
-   <span data-ttu-id="8e605-118">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 1 dzień, a nie określa wartości `maxStale` wartość, zawartość jest ponownie sprawdzić poprawności 2 stycznia, nawet jeśli nie wygasł.</span><span class="sxs-lookup"><span data-stu-id="8e605-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
-   <span data-ttu-id="8e605-119">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 1 dzień i `maxStale` = 3 dni, zawartość jest ponownie sprawdzić poprawności 2 stycznia do wymuszania bardziej zachowawcze ustawienie zasad.</span><span class="sxs-lookup"><span data-stu-id="8e605-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
-   <span data-ttu-id="8e605-120">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 1 dzień i `maxStale` = 1 dzień, zawartość jest ponownie sprawdzić poprawności 2 stycznia.</span><span class="sxs-lookup"><span data-stu-id="8e605-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e605-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e605-121">See Also</span></span>  
 [<span data-ttu-id="8e605-122">Zarządzanie pamięci podręcznej dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="8e605-122">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="8e605-123">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8e605-123">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="8e605-124">Zasady oparte na lokalizacji pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8e605-124">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="8e605-125">Zasady na podstawie czasu pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8e605-125">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="8e605-126">Konfigurowanie buforowanie w aplikacjach sieci</span><span class="sxs-lookup"><span data-stu-id="8e605-126">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="8e605-127">Pamięci podręcznej zasad interakcji — maksymalny wiek i świeżości minimalna</span><span class="sxs-lookup"><span data-stu-id="8e605-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
