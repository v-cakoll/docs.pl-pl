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
ms.openlocfilehash: ba08f630dc602c950da309bf29482d85b41af7ef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697685"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="84591-102">\<settings >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="84591-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="84591-103">Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84591-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
[<span data-ttu-id="84591-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="84591-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="84591-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="84591-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="84591-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<settings >**</span><span class="sxs-lookup"><span data-stu-id="84591-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84591-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="84591-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84591-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="84591-108">Attributes and Elements</span></span>  
 <span data-ttu-id="84591-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="84591-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84591-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="84591-110">Attributes</span></span>  
 <span data-ttu-id="84591-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="84591-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84591-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="84591-112">Child Elements</span></span>  
  
|<span data-ttu-id="84591-113">Element</span><span class="sxs-lookup"><span data-stu-id="84591-113">Element</span></span>|<span data-ttu-id="84591-114">Opis</span><span class="sxs-lookup"><span data-stu-id="84591-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84591-115">Odbiornika HttpListener</span><span class="sxs-lookup"><span data-stu-id="84591-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="84591-116">Dostosowuje parametry używane przez klasę <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="84591-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="84591-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="84591-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="84591-118">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="84591-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="84591-119">If</span><span class="sxs-lookup"><span data-stu-id="84591-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="84591-120">Włącza obsługę protokołu internetowego w wersji 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="84591-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="84591-121">\<performanceCounter >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="84591-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="84591-122">Włącza liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="84591-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="84591-123">ServicePointManager</span><span class="sxs-lookup"><span data-stu-id="84591-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="84591-124">Konfiguruje połączenia z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="84591-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="84591-125">używając</span><span class="sxs-lookup"><span data-stu-id="84591-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="84591-126">Określa, czy operacje gniazda używają portów zakończenia.</span><span class="sxs-lookup"><span data-stu-id="84591-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="84591-127">\<webProxyScript >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="84591-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="84591-128">Konfiguruje charakterystyki skryptu służącego do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="84591-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84591-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="84591-129">Parent Elements</span></span>  
  
|<span data-ttu-id="84591-130">Element</span><span class="sxs-lookup"><span data-stu-id="84591-130">Element</span></span>|<span data-ttu-id="84591-131">Opis</span><span class="sxs-lookup"><span data-stu-id="84591-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84591-132">system.net</span><span class="sxs-lookup"><span data-stu-id="84591-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="84591-133">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="84591-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84591-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84591-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="84591-135">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="84591-135">Configuration Files</span></span>  
 <span data-ttu-id="84591-136">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="84591-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84591-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84591-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="84591-138">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="84591-138">Network Settings Schema</span></span>](index.md)
