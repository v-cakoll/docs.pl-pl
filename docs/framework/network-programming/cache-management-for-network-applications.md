---
title: Zarządzanie pamięcią podręczną dla aplikacji sieciowych
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e0b3ed66977dd6587789e3d88f532b699653c6f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195579"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="cdf4c-102">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="cdf4c-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="cdf4c-103">Ten temat i jego powiązane tematy podrzędne opisują, buforowania dla zasobów pobranych przy użyciu <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> klasy.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="cdf4c-104">Pamięć podręczna udostępnia magazyn tymczasowy zasobów, które zostały żądane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="cdf4c-105">Jeśli aplikacja żąda tego samego zasobu więcej niż jeden raz, zasobu mogą być zwracane z pamięci podręcznej, unikając konieczności ponownie żąda od serwera.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="cdf4c-106">Buforowanie może poprawić wydajność aplikacji, skracając czas potrzebny na żądany zasób.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="cdf4c-107">Buforowanie można także zmniejszyć ruch w sieci dzięki zmniejszeniu liczby rund do serwera.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="cdf4c-108">Gdy pamięć podręczna zwiększa wydajność, zwiększa się ryzyko, że zasób powrót do aplikacji jest nieodświeżona, co oznacza, że nie jest taka sama jak zasób, który będzie została wysłana przez serwer pamięci podręcznej nie były używane.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="cdf4c-109">Buforowanie może umożliwić nieautoryzowanych użytkowników lub procesy, które można odczytać danych poufnych.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="cdf4c-110">Uwierzytelniony odpowiedź, która jest buforowana może pobrać z pamięci podręcznej bez autoryzacji dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="cdf4c-111">Jeśli włączone jest buforowanie, zmień <xref:System.Net.WebRequest.CachePolicy%2A> do <xref:System.Net.Cache.RequestCacheLevel.BypassCache> lub <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> wyłączenie buforowania dla tego żądania.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="cdf4c-112">Ze względów bezpieczeństwa buforowanie jest **nie** zalecane w przypadku scenariuszy warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cdf4c-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cdf4c-113">In This Section</span></span>  
 [<span data-ttu-id="cdf4c-114">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="cdf4c-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 <span data-ttu-id="cdf4c-115">Wyjaśnia, jakie zasady pamięci podręcznej jest i jak zdefiniować jedną.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="cdf4c-116">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="cdf4c-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 <span data-ttu-id="cdf4c-117">Definiuje każdego typu zasad na podstawie lokalizacji pamięci podręcznej dostępne dla zasobów Hypertext Transfer Protocol (protokół http i https).</span><span class="sxs-lookup"><span data-stu-id="cdf4c-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="cdf4c-118">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="cdf4c-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 <span data-ttu-id="cdf4c-119">W tym artykule opisano kryteria, które można dostosować zasady na podstawie czasu pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="cdf4c-120">Konfigurowanie pamięci podręcznej w aplikacjach sieciowych</span><span class="sxs-lookup"><span data-stu-id="cdf4c-120">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 <span data-ttu-id="cdf4c-121">W tym artykule opisano, jak programowo utworzyć zasady pamięci podręcznej i żądania, które używają pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cdf4c-122">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="cdf4c-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="cdf4c-123">Określa typy i wyliczenia używane do definiowania zasad buforowania dla zasobów pobranych przy użyciu <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, i <xref:System.Net.FtpWebRequest> klasy.</span><span class="sxs-lookup"><span data-stu-id="cdf4c-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
