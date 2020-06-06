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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089117"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="a2c65-102">\<settings>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a2c65-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="a2c65-103">Konfiguruje podstawowe opcje sieci dla <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a2c65-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="a2c65-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2c65-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2c65-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a2c65-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a2c65-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a2c65-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2c65-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a2c65-107">Attributes</span></span>  
 <span data-ttu-id="a2c65-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="a2c65-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a2c65-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a2c65-109">Child Elements</span></span>  
  
|<span data-ttu-id="a2c65-110">Element</span><span class="sxs-lookup"><span data-stu-id="a2c65-110">Element</span></span>|<span data-ttu-id="a2c65-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a2c65-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2c65-112">Odbiornika HttpListener</span><span class="sxs-lookup"><span data-stu-id="a2c65-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="a2c65-113">Dostosowuje parametry używane przez <xref:System.Net.HttpListener> klasę.</span><span class="sxs-lookup"><span data-stu-id="a2c65-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="a2c65-114">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="a2c65-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="a2c65-115">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a2c65-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="a2c65-116">If</span><span class="sxs-lookup"><span data-stu-id="a2c65-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="a2c65-117">Włącza obsługę protokołu internetowego w wersji 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="a2c65-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="a2c65-118">\<performanceCounter>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a2c65-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="a2c65-119">Włącza liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="a2c65-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="a2c65-120">ServicePointManager</span><span class="sxs-lookup"><span data-stu-id="a2c65-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="a2c65-121">Konfiguruje połączenia z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="a2c65-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="a2c65-122">używając</span><span class="sxs-lookup"><span data-stu-id="a2c65-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="a2c65-123">Określa, czy operacje gniazda używają portów zakończenia.</span><span class="sxs-lookup"><span data-stu-id="a2c65-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="a2c65-124">\<webProxyScript>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a2c65-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="a2c65-125">Konfiguruje charakterystyki skryptu służącego do odnajdywania serwerów proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a2c65-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2c65-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a2c65-126">Parent Elements</span></span>  
  
|<span data-ttu-id="a2c65-127">Element</span><span class="sxs-lookup"><span data-stu-id="a2c65-127">Element</span></span>|<span data-ttu-id="a2c65-128">Opis</span><span class="sxs-lookup"><span data-stu-id="a2c65-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2c65-129">system.net</span><span class="sxs-lookup"><span data-stu-id="a2c65-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="a2c65-130">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="a2c65-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2c65-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2c65-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a2c65-132">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a2c65-132">Configuration Files</span></span>  
 <span data-ttu-id="a2c65-133">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a2c65-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c65-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2c65-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="a2c65-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="a2c65-135">Network Settings Schema</span></span>](index.md)
