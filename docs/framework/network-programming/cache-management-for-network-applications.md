---
title: Zarządzanie pamięcią podręczną dla aplikacji sieciowych
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048874"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="3cafb-102">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="3cafb-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="3cafb-103">Ten temat i powiązane z nim tematy zawierają opis buforowania zasobów uzyskanych przy użyciu <xref:System.Net.WebClient>klas <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> .</span><span class="sxs-lookup"><span data-stu-id="3cafb-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="3cafb-104">Pamięć podręczna zapewnia tymczasowy magazyn zasobów, które zostały zlecone przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="3cafb-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="3cafb-105">Jeśli aplikacja żąda tego samego zasobu więcej niż jeden raz, można zwrócić zasób z pamięci podręcznej, unikając ponownego zażądania od serwera.</span><span class="sxs-lookup"><span data-stu-id="3cafb-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="3cafb-106">Buforowanie może zwiększyć wydajność aplikacji przez skrócenie czasu wymaganego do uzyskania żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="3cafb-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="3cafb-107">Buforowanie może również zmniejszyć ruch sieciowy, zmniejszając liczbę podróży do serwera.</span><span class="sxs-lookup"><span data-stu-id="3cafb-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="3cafb-108">Buforowanie zwiększa wydajność, ale zwiększa ryzyko, że zasób zwrócony do aplikacji jest nieodświeżony, co oznacza, że nie jest on identyczny z zasobem, który został wysłany przez serwer, Jeśli buforowanie nie było używane.</span><span class="sxs-lookup"><span data-stu-id="3cafb-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="3cafb-109">Buforowanie może umożliwić nieautoryzowanym użytkownikom lub procesom odczytywanie poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="3cafb-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="3cafb-110">Uwierzytelniona odpowiedź w pamięci podręcznej może być pobierana z pamięci podręcznej bez dodatkowej autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="3cafb-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="3cafb-111">Jeśli buforowanie jest włączone, Zmień na <xref:System.Net.WebRequest.CachePolicy%2A> <xref:System.Net.Cache.RequestCacheLevel.BypassCache> lub <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> , aby wyłączyć buforowanie dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="3cafb-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="3cafb-112">Ze względu na kwestie bezpieczeństwa buforowanie **nie** jest zalecane w przypadku scenariuszy warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="3cafb-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3cafb-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3cafb-113">In This Section</span></span>  
 [<span data-ttu-id="3cafb-114">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="3cafb-114">Cache Policy</span></span>](cache-policy.md)  
 <span data-ttu-id="3cafb-115">Wyjaśnia, co to są zasady pamięci podręcznej i jak je definiować.</span><span class="sxs-lookup"><span data-stu-id="3cafb-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="3cafb-116">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="3cafb-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)  
 <span data-ttu-id="3cafb-117">Definiuje każdy typ zasad pamięci podręcznej opartych na lokalizacji dostępnych dla zasobów protokołu HTTP i https.</span><span class="sxs-lookup"><span data-stu-id="3cafb-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="3cafb-118">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="3cafb-118">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)  
 <span data-ttu-id="3cafb-119">Opisuje kryteria, których można użyć do dostosowania zasad pamięci podręcznej opartej na czasie.</span><span class="sxs-lookup"><span data-stu-id="3cafb-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="3cafb-120">Konfigurowanie pamięci podręcznej w aplikacjach sieciowych</span><span class="sxs-lookup"><span data-stu-id="3cafb-120">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)  
 <span data-ttu-id="3cafb-121">Opisuje sposób programistycznego tworzenia zasad pamięci podręcznej i żądań korzystających z buforowania.</span><span class="sxs-lookup"><span data-stu-id="3cafb-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3cafb-122">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="3cafb-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="3cafb-123">Definiuje typy i wyliczenia używane do definiowania zasad pamięci podręcznej dla zasobów uzyskanych <xref:System.Net.WebRequest>przy <xref:System.Net.HttpWebRequest>użyciu klas <xref:System.Net.FtpWebRequest> , i.</span><span class="sxs-lookup"><span data-stu-id="3cafb-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
