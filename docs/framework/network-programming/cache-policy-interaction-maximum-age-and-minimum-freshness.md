---
title: "Pamięci podręcznej zasad interakcji — maksymalny wiek i świeżości minimalna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 689b8b2d921731ecab2be2a1aa3dee5d1928e8cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="d7592-102">Pamięci podręcznej zasad interakcji — maksymalny wiek i świeżości minimalna</span><span class="sxs-lookup"><span data-stu-id="d7592-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="d7592-103">Aby upewnić się, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcji klienta pamięci podręcznej zasad serwera ponownego sprawdzania poprawności wymagań i zawsze powoduje najbardziej zachowawcze zasady pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7592-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="d7592-104">Wszystkie przykłady w tym temacie przedstawiono zasady z zasobem, który jest buforowana w dniu 1 stycznia i wygaśnie w dniu 4 stycznia w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7592-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="d7592-105">Poniższe przykłady przedstawiają zasady pamięci podręcznej, będącą wynikiem interakcji maksymalny wiek (`maxAge`) i minimalna świeżości (`minFresh`) wartości.</span><span class="sxs-lookup"><span data-stu-id="d7592-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
-   <span data-ttu-id="d7592-106">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` nie zostanie określony, zawartość jest ponownie sprawdzić poprawności na 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="d7592-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="d7592-107">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` = 1 dzień, zgodnie z `maxAge`, zawartość jest pierwszą do 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="d7592-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="d7592-108">Zgodnie z `minFresh`, aż do 3 stycznia jest nowa zawartość.</span><span class="sxs-lookup"><span data-stu-id="d7592-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="d7592-109">W związku z tym zawartości musi być sprawdzony ponownie na 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="d7592-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="d7592-110">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` = 2 dni zgodnie z `maxAge`, zawartość jest pierwszą do 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="d7592-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="d7592-111">Zgodnie z `minFresh` do 2 stycznia jest nowa zawartość.</span><span class="sxs-lookup"><span data-stu-id="d7592-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="d7592-112">W związku z tym zawartości musi być sprawdzony ponownie 2 stycznia.</span><span class="sxs-lookup"><span data-stu-id="d7592-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7592-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7592-113">See Also</span></span>  
 [<span data-ttu-id="d7592-114">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="d7592-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="d7592-115">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="d7592-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="d7592-116">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="d7592-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="d7592-117">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="d7592-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="d7592-118">Konfigurowanie pamięci podręcznej w aplikacjach sieciowych</span><span class="sxs-lookup"><span data-stu-id="d7592-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="d7592-119">Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność</span><span class="sxs-lookup"><span data-stu-id="d7592-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
