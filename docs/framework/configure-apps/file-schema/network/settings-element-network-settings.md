---
title: '&lt;ustawienia&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: 87a944eca6ea4158f15c9911c6b13fd4d3c0921d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151203"
---
# <a name="ltsettingsgt-element-network-settings"></a><span data-ttu-id="82106-102">&lt;ustawienia&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="82106-102">&lt;settings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="82106-103">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82106-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="82106-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="82106-104">\<configuration></span></span>  
<span data-ttu-id="82106-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="82106-105">\<system.net></span></span>  
<span data-ttu-id="82106-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="82106-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82106-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="82106-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82106-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="82106-108">Attributes and Elements</span></span>  
 <span data-ttu-id="82106-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="82106-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82106-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="82106-110">Attributes</span></span>  
 <span data-ttu-id="82106-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="82106-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="82106-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="82106-112">Child Elements</span></span>  
  
|<span data-ttu-id="82106-113">Element</span><span class="sxs-lookup"><span data-stu-id="82106-113">Element</span></span>|<span data-ttu-id="82106-114">Opis</span><span class="sxs-lookup"><span data-stu-id="82106-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82106-115">HttpListener</span><span class="sxs-lookup"><span data-stu-id="82106-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="82106-116">Dostosowuje parametrów używanych przez <xref:System.Net.HttpListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="82106-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="82106-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="82106-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="82106-118">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="82106-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="82106-119">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="82106-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="82106-120">Włącza protokołu internetowego w wersji 6 (IPv6) pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="82106-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="82106-121">\<performanceCounter >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="82106-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="82106-122">Liczniki wydajności funkcji sieciowych umożliwia.</span><span class="sxs-lookup"><span data-stu-id="82106-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="82106-123">ServicePointManager —</span><span class="sxs-lookup"><span data-stu-id="82106-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="82106-124">Służy do konfigurowania połączeń z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="82106-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="82106-125">Gniazda</span><span class="sxs-lookup"><span data-stu-id="82106-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="82106-126">Określa, czy operacje gniazda używają portów.</span><span class="sxs-lookup"><span data-stu-id="82106-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="82106-127">\<webproxyscript — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="82106-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="82106-128">Konfiguruje właściwości skryptu używanej do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="82106-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82106-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="82106-129">Parent Elements</span></span>  
  
|<span data-ttu-id="82106-130">Element</span><span class="sxs-lookup"><span data-stu-id="82106-130">Element</span></span>|<span data-ttu-id="82106-131">Opis</span><span class="sxs-lookup"><span data-stu-id="82106-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82106-132">przestrzeni nazw System.NET</span><span class="sxs-lookup"><span data-stu-id="82106-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="82106-133">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="82106-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82106-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82106-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="82106-135">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="82106-135">Configuration Files</span></span>  
 <span data-ttu-id="82106-136">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="82106-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82106-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82106-137">See Also</span></span>  
- <xref:System.Net?displayProperty=nameWithType>  
- [<span data-ttu-id="82106-138">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="82106-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
