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
ms.openlocfilehash: bf04b16682c2c1bc677fecbd6dc966090c77e1da
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698131"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="23825-102">\<ipv6 >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="23825-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="23825-103">Włącza odpowiedzi protokołu internetowego w wersji 6 (IPv6) od przestarzałych elementów członkowskich klasy <xref:System.Net.Dns>.</span><span class="sxs-lookup"><span data-stu-id="23825-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
[<span data-ttu-id="23825-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="23825-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="23825-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="23825-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="23825-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="23825-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="23825-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<ipv6 >**</span><span class="sxs-lookup"><span data-stu-id="23825-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23825-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="23825-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23825-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23825-109">Attributes and Elements</span></span>  
 <span data-ttu-id="23825-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23825-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23825-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23825-111">Attributes</span></span>  
  
|<span data-ttu-id="23825-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="23825-112">**Attribute**</span></span>|<span data-ttu-id="23825-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="23825-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="23825-114">Określa, czy elementy członkowskie klasy <xref:System.Net.Dns> zwracają adresy protokołu internetowego w wersji 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="23825-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="23825-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="23825-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23825-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23825-116">Child Elements</span></span>  
 <span data-ttu-id="23825-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="23825-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23825-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23825-118">Parent Elements</span></span>  
  
|<span data-ttu-id="23825-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="23825-119">**Element**</span></span>|<span data-ttu-id="23825-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="23825-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="23825-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="23825-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="23825-122">Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="23825-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23825-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23825-123">Remarks</span></span>  
 <span data-ttu-id="23825-124">To ustawienie umożliwia obsługę protokołu IPv6 dla przestarzałych elementów członkowskich klasy <xref:System.Net.Dns>: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A> i <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="23825-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="23825-125">W przypadku innych elementów członkowskich przestrzeni nazw <xref:System.Net?displayProperty=nameWithType> adresy IPv6 mogą być zwracane w przypadku włączenia protokołu IPv6 w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="23825-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="23825-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="23825-126">Configuration Files</span></span>  
 <span data-ttu-id="23825-127">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="23825-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23825-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="23825-128">Example</span></span>  
 <span data-ttu-id="23825-129">Poniższy przykład pokazuje, jak włączyć obsługę protokołu IPv6 dla klasy <xref:System.Net.Dns>.</span><span class="sxs-lookup"><span data-stu-id="23825-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23825-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23825-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="23825-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="23825-131">Network Settings Schema</span></span>](index.md)
