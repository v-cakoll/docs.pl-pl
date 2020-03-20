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
ms.openlocfilehash: 2ec958cc035ac62086cdd3e2844811accc181d47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048819"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="a5a3d-102">Interakcja z zasadami pamięci podręcznej — maksymalny wiek i minimalna świeżość</span><span class="sxs-lookup"><span data-stu-id="a5a3d-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="a5a3d-103">Aby upewnić się, że najświeższa zawartość jest zwracana do aplikacji klienckiej, interakcja zasad pamięci podręcznej klienta i wymagania dotyczące ponownego licencjonowania serwera zawsze skutkuje najbardziej konserwatywnymi zasadami pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="a5a3d-104">Wszystkie przykłady w tym temacie ilustrują zasady pamięci podręcznej dla zasobu, który jest buforowany w dniu 1 stycznia i wygasa 4 stycznia.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="a5a3d-105">Poniższe przykłady ilustrują zasady pamięci podręcznej wynikające`maxAge`z interakcji maksymalnego`minFresh`wieku ( ) i minimalnej świeżości ( ) wartości.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="a5a3d-106">Jeśli zasady pamięci `maxAge` podręcznej ustawia `minFresh` = 2 dni i nie jest określony, zawartość jest ponownie 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="a5a3d-107">Jeśli ustawia się `maxAge` zasady pamięci `minFresh` podręcznej = 2 `maxAge`dni i = 1 dzień, zgodnie z , zawartość jest świeża do 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="a5a3d-108">Według `minFresh`, zawartość jest świeża do 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="a5a3d-109">W związku z tym zawartość musi zostać ponownie oceniona w dniu 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="a5a3d-110">Jeśli ustawia się `maxAge` zasady pamięci `minFresh` podręcznej = 2 `maxAge`dni i = 2 dni, zgodnie z , zawartość jest świeża do 3 stycznia.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="a5a3d-111">Według `minFresh` treści jest świeże do 2 stycznia.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="a5a3d-112">W związku z tym zawartość musi zostać ponownie oceniona w dniu 2 stycznia.</span><span class="sxs-lookup"><span data-stu-id="a5a3d-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a3d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5a3d-113">See also</span></span>

- [<span data-ttu-id="a5a3d-114">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="a5a3d-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="a5a3d-115">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="a5a3d-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="a5a3d-116">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="a5a3d-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="a5a3d-117">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="a5a3d-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="a5a3d-118">Konfigurowanie pamięci podręcznej w aplikacjach sieciowych</span><span class="sxs-lookup"><span data-stu-id="a5a3d-118">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="a5a3d-119">Interakcja z zasadami pamięci podręcznej — maksymalny wiek i maksymalna nieaktualność</span><span class="sxs-lookup"><span data-stu-id="a5a3d-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
