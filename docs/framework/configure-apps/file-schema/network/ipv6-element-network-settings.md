---
title: '&lt;Protokół IPv6&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5b1707d7490de07520603f6fdf6d1ee1a44ffba7
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840491"
---
# <a name="ltipv6gt-element-network-settings"></a><span data-ttu-id="8febd-102">&lt;Protokół IPv6&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="8febd-102">&lt;ipv6&gt; Element (Network Settings)</span></span>
<span data-ttu-id="8febd-103">Włącza protokołu internetowego w wersji 6 (IPv6) odpowiedzi od przestarzałe elementy członkowskie <xref:System.Net.Dns> klasy.</span><span class="sxs-lookup"><span data-stu-id="8febd-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="8febd-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="8febd-104">\<configuration></span></span>  
<span data-ttu-id="8febd-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8febd-105">\<system.net></span></span>  
<span data-ttu-id="8febd-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="8febd-106">\<settings></span></span>  
<span data-ttu-id="8febd-107">\<Protokół IPv6 ></span><span class="sxs-lookup"><span data-stu-id="8febd-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8febd-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="8febd-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8febd-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8febd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8febd-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8febd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8febd-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8febd-111">Attributes</span></span>  
  
|<span data-ttu-id="8febd-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="8febd-112">**Attribute**</span></span>|<span data-ttu-id="8febd-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="8febd-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="8febd-114">Określa, czy członkowie <xref:System.Net.Dns> klasy zwracają protokołu internetowego w wersji 6 (IPv6) adres.</span><span class="sxs-lookup"><span data-stu-id="8febd-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="8febd-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="8febd-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8febd-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8febd-116">Child Elements</span></span>  
 <span data-ttu-id="8febd-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="8febd-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8febd-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8febd-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8febd-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="8febd-119">**Element**</span></span>|<span data-ttu-id="8febd-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="8febd-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8febd-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="8febd-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="8febd-122">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8febd-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8febd-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8febd-123">Remarks</span></span>  
 <span data-ttu-id="8febd-124">To ustawienie włącza obsługę protokołu IPv6 dla członków przestarzałe <xref:System.Net.Dns> klasy: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, i <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="8febd-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="8febd-125">Dla innych członków <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw, adresy IPv6 mogą być zwrócone, jeśli był włączony protokół IPv6 w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="8febd-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8febd-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8febd-126">Configuration Files</span></span>  
 <span data-ttu-id="8febd-127">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8febd-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8febd-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="8febd-128">Example</span></span>  
 <span data-ttu-id="8febd-129">Poniższy przykład pokazuje, jak włączyć obsługę protokołu IPv6 <xref:System.Net.Dns> klasy.</span><span class="sxs-lookup"><span data-stu-id="8febd-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8febd-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8febd-130">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Dns?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8febd-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="8febd-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
