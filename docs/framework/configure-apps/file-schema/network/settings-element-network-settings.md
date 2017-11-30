---
title: '&lt;ustawienia&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 07f356c0425b071ac320e702a9ba7cd6b9537341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsettingsgt-element-network-settings"></a><span data-ttu-id="d4b47-102">&lt;ustawienia&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="d4b47-102">&lt;settings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="d4b47-103">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d4b47-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="d4b47-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d4b47-104">\<configuration></span></span>  
<span data-ttu-id="d4b47-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="d4b47-105">\<system.net></span></span>  
<span data-ttu-id="d4b47-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="d4b47-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b47-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4b47-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4b47-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4b47-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d4b47-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4b47-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4b47-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4b47-110">Attributes</span></span>  
 <span data-ttu-id="d4b47-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="d4b47-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d4b47-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4b47-112">Child Elements</span></span>  
  
|<span data-ttu-id="d4b47-113">Element</span><span class="sxs-lookup"><span data-stu-id="d4b47-113">Element</span></span>|<span data-ttu-id="d4b47-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d4b47-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4b47-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="d4b47-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="d4b47-116">Dostosowuje parametry używane przez <xref:System.Net.HttpListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="d4b47-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="d4b47-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="d4b47-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="d4b47-118">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d4b47-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="d4b47-119">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="d4b47-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="d4b47-120">Włącza Internet Protocol w wersji 6 (IPv6) obsługuje.</span><span class="sxs-lookup"><span data-stu-id="d4b47-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="d4b47-121">\<performanceCounter > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="d4b47-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="d4b47-122">Umożliwia sieciowym liczników wydajności.</span><span class="sxs-lookup"><span data-stu-id="d4b47-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="d4b47-123">Element servicePointManager</span><span class="sxs-lookup"><span data-stu-id="d4b47-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="d4b47-124">Służy do konfigurowania połączeń z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="d4b47-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="d4b47-125">gniazda</span><span class="sxs-lookup"><span data-stu-id="d4b47-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="d4b47-126">Określa, czy operacje gniazda używać portów.</span><span class="sxs-lookup"><span data-stu-id="d4b47-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="d4b47-127">\<webproxyscript — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="d4b47-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="d4b47-128">Konfiguruje właściwości skryptu używana do wykrywania, serwer proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d4b47-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4b47-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4b47-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d4b47-130">Element</span><span class="sxs-lookup"><span data-stu-id="d4b47-130">Element</span></span>|<span data-ttu-id="d4b47-131">Opis</span><span class="sxs-lookup"><span data-stu-id="d4b47-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4b47-132">System.NET</span><span class="sxs-lookup"><span data-stu-id="d4b47-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="d4b47-133">Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="d4b47-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4b47-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4b47-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d4b47-135">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d4b47-135">Configuration Files</span></span>  
 <span data-ttu-id="d4b47-136">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d4b47-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b47-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4b47-137">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 [<span data-ttu-id="d4b47-138">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="d4b47-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
