---
title: '&lt;IPv6&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4a98d1d21d7df4e88c668262e60397029fe44c5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltipv6gt-element-network-settings"></a><span data-ttu-id="35736-102">&lt;IPv6&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="35736-102">&lt;ipv6&gt; Element (Network Settings)</span></span>
<span data-ttu-id="35736-103">Internet Protocol w wersji 6 (IPv6) umożliwia odpowiedzi z przestarzałych elementów członkowskich <xref:System.Net.Dns> klasy.</span><span class="sxs-lookup"><span data-stu-id="35736-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="35736-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="35736-104">\<configuration></span></span>  
<span data-ttu-id="35736-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="35736-105">\<system.net></span></span>  
<span data-ttu-id="35736-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="35736-106">\<settings></span></span>  
<span data-ttu-id="35736-107">\<IPv6 ></span><span class="sxs-lookup"><span data-stu-id="35736-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35736-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="35736-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35736-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="35736-109">Attributes and Elements</span></span>  
 <span data-ttu-id="35736-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="35736-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35736-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="35736-111">Attributes</span></span>  
  
|<span data-ttu-id="35736-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="35736-112">**Attribute**</span></span>|<span data-ttu-id="35736-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="35736-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="35736-114">Określa, czy elementy członkowskie <xref:System.Net.Dns> klasy zwracać Internet Protocol w wersji 6 (IPv6) adresów.</span><span class="sxs-lookup"><span data-stu-id="35736-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="35736-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="35736-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35736-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="35736-116">Child Elements</span></span>  
 <span data-ttu-id="35736-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="35736-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35736-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35736-118">Parent Elements</span></span>  
  
|<span data-ttu-id="35736-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="35736-119">**Element**</span></span>|<span data-ttu-id="35736-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="35736-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="35736-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="35736-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="35736-122">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="35736-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35736-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35736-123">Remarks</span></span>  
 <span data-ttu-id="35736-124">To ustawienie włącza obsługi protokołu IPv6 dla członków przestarzałe <xref:System.Net.Dns> klasy: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, i <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="35736-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="35736-125">Dla innych członków <xref:System.Net?displayProperty=nameWithType> przestrzeni nazw, adresy IPv6 mogą być zwracane w przypadku protokołu IPv6 jest włączona w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="35736-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="35736-126">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="35736-126">Configuration Files</span></span>  
 <span data-ttu-id="35736-127">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="35736-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35736-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="35736-128">Example</span></span>  
 <span data-ttu-id="35736-129">Poniższy przykład przedstawia sposób włączania obsługi protokołu IPv6 dla <xref:System.Net.Dns> klasy.</span><span class="sxs-lookup"><span data-stu-id="35736-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35736-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35736-130">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Dns?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="35736-131">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="35736-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
