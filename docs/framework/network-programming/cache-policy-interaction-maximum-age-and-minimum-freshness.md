---
title: Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: eab50c308441ce73e994313d009588559302671e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199321"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="33da4-102">Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość</span><span class="sxs-lookup"><span data-stu-id="33da4-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="33da4-103">Aby upewnić się, że najnowsza zawartość jest zwracana do aplikacji klienckiej, interakcji klienta pamięci podręcznej zasad serwera ponownego sprawdzania poprawności wymagań i zawsze skutkuje najbardziej umiarkowaną zasad pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="33da4-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="33da4-104">Wszystkie przykłady w tym temacie ilustrują zasad pamięci podręcznej na zasób, który jest buforowany w dniu 1 stycznia i wygasa w dniu 4 stycznia.</span><span class="sxs-lookup"><span data-stu-id="33da4-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="33da4-105">Poniższe przykłady ilustrują zasad pamięci podręcznej, która wynika z interakcji maksymalny wiek (`maxAge`) i minimalna świeżość (`minFresh`) wartości.</span><span class="sxs-lookup"><span data-stu-id="33da4-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
-   <span data-ttu-id="33da4-106">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` nie zostanie określony, zawartość jest ponownie zatwierdzone na 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="33da4-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="33da4-107">Jeśli ustawia zasady pamięci podręcznej `maxAge` = 2 dni i `minFresh` = 1 dzień, zgodnie z opisem w `maxAge`, aż do 3 stycznia od nowa jest zawartość.</span><span class="sxs-lookup"><span data-stu-id="33da4-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="33da4-108">Zgodnie z opisem w `minFresh`, aż do 3 stycznia od nowa jest zawartość.</span><span class="sxs-lookup"><span data-stu-id="33da4-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="33da4-109">W związku z tym należy ponownie zatwierdzone zawartości, na 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="33da4-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="33da4-110">Jeśli zasady pamięci podręcznej ustawia `maxAge` = 2 dni i `minFresh` = 2 dni zgodnie z opisem w `maxAge`, aż do 3 stycznia od nowa jest zawartość.</span><span class="sxs-lookup"><span data-stu-id="33da4-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="33da4-111">Zgodnie z opisem w `minFresh` zawartość jest świeże aż do 2 stycznia.</span><span class="sxs-lookup"><span data-stu-id="33da4-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="33da4-112">W związku z tym zawartość musi być sprawdzony ponownie 2 stycznia.</span><span class="sxs-lookup"><span data-stu-id="33da4-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33da4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33da4-113">See Also</span></span>  
 [<span data-ttu-id="33da4-114">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="33da4-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="33da4-115">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="33da4-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="33da4-116">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="33da4-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="33da4-117">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="33da4-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="33da4-118">Konfigurowanie pamięci podręcznej w aplikacjach sieciowych</span><span class="sxs-lookup"><span data-stu-id="33da4-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="33da4-119">Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność</span><span class="sxs-lookup"><span data-stu-id="33da4-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
