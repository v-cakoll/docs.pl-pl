---
title: <ipv6>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: d89c2e2c6943aca38f8a71092ba3121447a77574
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664099"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="f578a-102">\<> IPv6, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="f578a-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="f578a-103">Włącza odpowiedzi protokołu internetowego w wersji 6 (IPv6) od przestarzałych elementów <xref:System.Net.Dns> członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="f578a-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="f578a-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f578a-104">\<configuration></span></span>  
<span data-ttu-id="f578a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f578a-105">\<system.net></span></span>  
<span data-ttu-id="f578a-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="f578a-106">\<settings></span></span>  
<span data-ttu-id="f578a-107">\<> IPv6</span><span class="sxs-lookup"><span data-stu-id="f578a-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f578a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f578a-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f578a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f578a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f578a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f578a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f578a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f578a-111">Attributes</span></span>  
  
|<span data-ttu-id="f578a-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="f578a-112">**Attribute**</span></span>|<span data-ttu-id="f578a-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f578a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="f578a-114">Określa, czy elementy członkowskie <xref:System.Net.Dns> klasy zwracają adresy protokołu internetowego w wersji 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="f578a-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="f578a-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f578a-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f578a-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f578a-116">Child Elements</span></span>  
 <span data-ttu-id="f578a-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="f578a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f578a-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f578a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f578a-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="f578a-119">**Element**</span></span>|<span data-ttu-id="f578a-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f578a-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f578a-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="f578a-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="f578a-122">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f578a-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f578a-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f578a-123">Remarks</span></span>  
 <span data-ttu-id="f578a-124">To ustawienie umożliwia obsługę protokołu IPv6 dla przestarzałych elementów członkowskich <xref:System.Net.Dns> klasy: <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Net.Dns.GetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A> <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A>,,, i <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="f578a-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="f578a-125">W przypadku innych elementów członkowskich <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw adresy IPv6 mogą być zwracane, jeśli w systemie operacyjnym jest włączony protokół IPv6.</span><span class="sxs-lookup"><span data-stu-id="f578a-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f578a-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f578a-126">Configuration Files</span></span>  
 <span data-ttu-id="f578a-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f578a-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f578a-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="f578a-128">Example</span></span>  
 <span data-ttu-id="f578a-129">Poniższy przykład pokazuje, jak włączyć obsługę protokołu IPv6 dla <xref:System.Net.Dns> klasy.</span><span class="sxs-lookup"><span data-stu-id="f578a-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f578a-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f578a-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f578a-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f578a-131">Network Settings Schema</span></span>](index.md)
