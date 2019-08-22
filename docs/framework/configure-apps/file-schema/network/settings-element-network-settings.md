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
ms.openlocfilehash: 12797e2f06d03aacd81700eae57d5776c1a6f354
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663994"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="c0486-102">\<Settings >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="c0486-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="c0486-103">Konfiguruje podstawowe opcje sieci dla <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c0486-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="c0486-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0486-104">\<configuration></span></span>  
<span data-ttu-id="c0486-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c0486-105">\<system.net></span></span>  
<span data-ttu-id="c0486-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="c0486-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0486-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0486-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0486-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c0486-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c0486-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c0486-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0486-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c0486-110">Attributes</span></span>  
 <span data-ttu-id="c0486-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="c0486-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0486-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c0486-112">Child Elements</span></span>  
  
|<span data-ttu-id="c0486-113">Element</span><span class="sxs-lookup"><span data-stu-id="c0486-113">Element</span></span>|<span data-ttu-id="c0486-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c0486-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0486-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="c0486-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="c0486-116">Dostosowuje parametry używane przez <xref:System.Net.HttpListener> klasę.</span><span class="sxs-lookup"><span data-stu-id="c0486-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="c0486-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="c0486-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="c0486-118">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c0486-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="c0486-119">If</span><span class="sxs-lookup"><span data-stu-id="c0486-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="c0486-120">Włącza obsługę protokołu internetowego w wersji 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="c0486-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="c0486-121">\<performanceCounter >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="c0486-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="c0486-122">Włącza liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="c0486-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="c0486-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="c0486-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="c0486-124">Konfiguruje połączenia z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="c0486-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="c0486-125">używając</span><span class="sxs-lookup"><span data-stu-id="c0486-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="c0486-126">Określa, czy operacje gniazda używają portów zakończenia.</span><span class="sxs-lookup"><span data-stu-id="c0486-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="c0486-127">\<webProxyScript >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="c0486-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="c0486-128">Konfiguruje charakterystyki skryptu służącego do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c0486-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0486-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c0486-129">Parent Elements</span></span>  
  
|<span data-ttu-id="c0486-130">Element</span><span class="sxs-lookup"><span data-stu-id="c0486-130">Element</span></span>|<span data-ttu-id="c0486-131">Opis</span><span class="sxs-lookup"><span data-stu-id="c0486-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0486-132">system.net</span><span class="sxs-lookup"><span data-stu-id="c0486-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="c0486-133">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="c0486-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0486-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0486-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c0486-135">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0486-135">Configuration Files</span></span>  
 <span data-ttu-id="c0486-136">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="c0486-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0486-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0486-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="c0486-138">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c0486-138">Network Settings Schema</span></span>](index.md)
