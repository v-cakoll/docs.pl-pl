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
ms.openlocfilehash: b8969cecf8ffb2ef23522f193bb322b1170e6111
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705067"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="1f3c8-102">\<Protokół IPv6 >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="1f3c8-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="1f3c8-103">Włącza protokołu internetowego w wersji 6 (IPv6) odpowiedzi od przestarzałe elementy członkowskie <xref:System.Net.Dns> klasy.</span><span class="sxs-lookup"><span data-stu-id="1f3c8-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="1f3c8-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1f3c8-104">\<configuration></span></span>  
<span data-ttu-id="1f3c8-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="1f3c8-105">\<system.net></span></span>  
<span data-ttu-id="1f3c8-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="1f3c8-106">\<settings></span></span>  
<span data-ttu-id="1f3c8-107">\<Protokół IPv6 ></span><span class="sxs-lookup"><span data-stu-id="1f3c8-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f3c8-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f3c8-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f3c8-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1f3c8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1f3c8-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1f3c8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f3c8-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1f3c8-111">Attributes</span></span>  
  
|<span data-ttu-id="1f3c8-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="1f3c8-112">**Attribute**</span></span>|<span data-ttu-id="1f3c8-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1f3c8-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="1f3c8-114">Określa, czy członkowie <xref:System.Net.Dns> klasy zwracają protokołu internetowego w wersji 6 (IPv6) adres.</span><span class="sxs-lookup"><span data-stu-id="1f3c8-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="1f3c8-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="1f3c8-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f3c8-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1f3c8-116">Child Elements</span></span>  
 <span data-ttu-id="1f3c8-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="1f3c8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f3c8-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1f3c8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1f3c8-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="1f3c8-119">**Element**</span></span>|<span data-ttu-id="1f3c8-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1f3c8-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1f3c8-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="1f3c8-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="1f3c8-122">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1f3c8-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f3c8-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f3c8-123">Remarks</span></span>  
 <span data-ttu-id="1f3c8-124">To ustawienie włącza obsługę protokołu IPv6 dla członków przestarzałe <xref:System.Net.Dns> klasy: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, i <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f3c8-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="1f3c8-125">Dla innych członków <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw, adresy IPv6 mogą być zwrócone, jeśli był włączony protokół IPv6 w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="1f3c8-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1f3c8-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1f3c8-126">Configuration Files</span></span>  
 <span data-ttu-id="1f3c8-127">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="1f3c8-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f3c8-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f3c8-128">Example</span></span>  
 <span data-ttu-id="1f3c8-129">Poniższy przykład pokazuje, jak włączyć obsługę protokołu IPv6 <xref:System.Net.Dns> klasy.</span><span class="sxs-lookup"><span data-stu-id="1f3c8-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f3c8-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f3c8-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1f3c8-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="1f3c8-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
