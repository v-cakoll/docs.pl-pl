---
title: <settings>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: d510c445c585a36005ed415b14188efc4be03984
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089117"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="940dc-102">\<Ustawienia > elementu (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="940dc-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="940dc-103">Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="940dc-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

<span data-ttu-id="940dc-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="940dc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="940dc-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="940dc-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="940dc-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<** ></span><span class="sxs-lookup"><span data-stu-id="940dc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="940dc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="940dc-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="940dc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="940dc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="940dc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="940dc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="940dc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="940dc-110">Attributes</span></span>  
 <span data-ttu-id="940dc-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="940dc-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="940dc-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="940dc-112">Child Elements</span></span>  
  
|<span data-ttu-id="940dc-113">Element</span><span class="sxs-lookup"><span data-stu-id="940dc-113">Element</span></span>|<span data-ttu-id="940dc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="940dc-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="940dc-115">Odbiornika HttpListener</span><span class="sxs-lookup"><span data-stu-id="940dc-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="940dc-116">Dostosowuje parametry używane przez klasę <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="940dc-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="940dc-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="940dc-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="940dc-118">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="940dc-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="940dc-119">If</span><span class="sxs-lookup"><span data-stu-id="940dc-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="940dc-120">Włącza obsługę protokołu internetowego w wersji 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="940dc-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="940dc-121">\<element > performanceCounter (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="940dc-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="940dc-122">Włącza liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="940dc-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="940dc-123">ServicePointManager</span><span class="sxs-lookup"><span data-stu-id="940dc-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="940dc-124">Konfiguruje połączenia z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="940dc-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="940dc-125">używając</span><span class="sxs-lookup"><span data-stu-id="940dc-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="940dc-126">Określa, czy operacje gniazda używają portów zakończenia.</span><span class="sxs-lookup"><span data-stu-id="940dc-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="940dc-127">\<element > webProxyScript (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="940dc-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="940dc-128">Konfiguruje charakterystyki skryptu służącego do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="940dc-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="940dc-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="940dc-129">Parent Elements</span></span>  
  
|<span data-ttu-id="940dc-130">Element</span><span class="sxs-lookup"><span data-stu-id="940dc-130">Element</span></span>|<span data-ttu-id="940dc-131">Opis</span><span class="sxs-lookup"><span data-stu-id="940dc-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="940dc-132">system.net</span><span class="sxs-lookup"><span data-stu-id="940dc-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="940dc-133">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="940dc-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="940dc-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="940dc-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="940dc-135">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="940dc-135">Configuration Files</span></span>  
 <span data-ttu-id="940dc-136">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="940dc-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="940dc-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="940dc-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="940dc-138">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="940dc-138">Network Settings Schema</span></span>](index.md)
