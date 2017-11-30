---
title: "Zarządzanie pamięci podręcznej dla aplikacji sieciowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b960942d17e402b333354bbd932cf63d11b1209f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="b968a-102">Zarządzanie pamięci podręcznej dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="b968a-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="b968a-103">Ten temat i jego tematy pokrewne podrzędne opisują buforowanie zasobów uzyskany przy użyciu <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> klasy.</span><span class="sxs-lookup"><span data-stu-id="b968a-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="b968a-104">Pamięć podręczna zawiera magazyn tymczasowy zasobów, które zostały żądany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="b968a-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="b968a-105">Jeśli aplikacja żąda tego samego zasobu więcej niż raz, zasób może być zwracany z pamięci podręcznej umożliwia uniknięcie przeciążenia ponownie żąda od serwera.</span><span class="sxs-lookup"><span data-stu-id="b968a-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="b968a-106">Buforowanie może poprawić wydajność aplikacji, skracając czas wymagany do pobrania żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="b968a-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="b968a-107">Buforowanie można także zmniejszyć obciążenie sieci dzięki zmniejszeniu liczby rund do serwera.</span><span class="sxs-lookup"><span data-stu-id="b968a-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="b968a-108">Gdy buforowanie zwiększa wydajność, zwiększa ryzyko, że zasób zwracana do aplikacji jest przestarzała, co oznacza, że nie jest identyczny zasobem, który będzie zostało wysłane przez serwer, jeśli buforowanie nie były używane.</span><span class="sxs-lookup"><span data-stu-id="b968a-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="b968a-109">Buforowanie mogą zezwolić nieautoryzowanymi użytkownikami lub procesami, które można odczytać danych poufnych.</span><span class="sxs-lookup"><span data-stu-id="b968a-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="b968a-110">Uwierzytelnioną buforowaną odpowiedź mogą pobrać z pamięci podręcznej bez dodatkowych autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="b968a-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="b968a-111">Jeśli jest włączone buforowanie, zmień <xref:System.Net.WebRequest.CachePolicy%2A> do <xref:System.Net.Cache.RequestCacheLevel.BypassCache> lub <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> wyłączenie buforowania dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="b968a-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="b968a-112">Ze względów bezpieczeństwa buforowanie jest **nie** zalecane w przypadku scenariuszy warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="b968a-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b968a-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b968a-113">In This Section</span></span>  
 [<span data-ttu-id="b968a-114">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="b968a-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 <span data-ttu-id="b968a-115">Wyjaśniono, jakie zasady pamięci podręcznej oraz sposób definiowania jeden.</span><span class="sxs-lookup"><span data-stu-id="b968a-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="b968a-116">Zasady oparte na lokalizacji pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="b968a-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 <span data-ttu-id="b968a-117">Definiuje każdego typu zasad na podstawie lokalizacji pamięci podręcznej dostępnych zasobów Hypertext Transfer Protocol (protokół http i https).</span><span class="sxs-lookup"><span data-stu-id="b968a-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="b968a-118">Zasady na podstawie czasu pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="b968a-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 <span data-ttu-id="b968a-119">Zawiera opis kryteriów, które mogą służyć do konfigurowania zasad na podstawie czasu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b968a-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="b968a-120">Konfigurowanie buforowanie w aplikacjach sieci</span><span class="sxs-lookup"><span data-stu-id="b968a-120">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 <span data-ttu-id="b968a-121">Opisuje sposób programowego tworzenia zasady pamięci podręcznej i żądania, które używają buforowania.</span><span class="sxs-lookup"><span data-stu-id="b968a-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b968a-122">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b968a-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="b968a-123">Określa typy oraz wyliczenia używane do definiowania zasad buforowania zasobów uzyskany przy użyciu <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> klasy.</span><span class="sxs-lookup"><span data-stu-id="b968a-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
