---
title: '&lt;Serwer proxy&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b0b397e66e0f73d10f482bc9151a6fbacf3e774d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltproxygt-element-network-settings"></a><span data-ttu-id="ac7cc-102">&lt;Serwer proxy&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="ac7cc-102">&lt;proxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="ac7cc-103">Definiuje serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="ac7cc-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ac7cc-104">\<configuration></span></span>  
<span data-ttu-id="ac7cc-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="ac7cc-105">\<system.net></span></span>  
<span data-ttu-id="ac7cc-106">\<defaultProxy — ></span><span class="sxs-lookup"><span data-stu-id="ac7cc-106">\<defaultProxy></span></span>  
<span data-ttu-id="ac7cc-107">\<Serwer proxy ></span><span class="sxs-lookup"><span data-stu-id="ac7cc-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac7cc-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac7cc-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac7cc-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ac7cc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ac7cc-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac7cc-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ac7cc-111">Attributes</span></span>  
  
|<span data-ttu-id="ac7cc-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="ac7cc-112">**Attribute**</span></span>|<span data-ttu-id="ac7cc-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="ac7cc-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="ac7cc-114">Określa, czy serwer proxy jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="ac7cc-115">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="ac7cc-116">Określa, czy serwer proxy jest pomijana dla zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="ac7cc-117">Zasobów lokalnych obejmują serwer lokalny (http://localhost, http://loopback lub http://127.0.0.1) i identyfikator URI bez kropki (http://webserver).</span><span class="sxs-lookup"><span data-stu-id="ac7cc-117">Local resources include the local server (http://localhost, http://loopback, or http://127.0.0.1) and a URI without a period (http://webserver).</span></span> <span data-ttu-id="ac7cc-118">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="ac7cc-119">Określa identyfikator URI do użycia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="ac7cc-120">Określa lokalizację skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-120">Specifies the location of the configuration script.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="ac7cc-121">Określa, czy ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-121">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="ac7cc-122">Jeśli ustawiono `true`, kolejne atrybuty spowoduje zastąpienie ustawień serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-122">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="ac7cc-123">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-123">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac7cc-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ac7cc-124">Child Elements</span></span>  
 <span data-ttu-id="ac7cc-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac7cc-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ac7cc-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ac7cc-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="ac7cc-127">**Element**</span></span>|<span data-ttu-id="ac7cc-128">**Opis**</span><span class="sxs-lookup"><span data-stu-id="ac7cc-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ac7cc-129">defaultProxy —</span><span class="sxs-lookup"><span data-stu-id="ac7cc-129">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="ac7cc-130">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="ac7cc-130">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="ac7cc-131">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="ac7cc-131">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac7cc-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac7cc-132">Remarks</span></span>  
 <span data-ttu-id="ac7cc-133">`proxy` Element definiuje serwera proxy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-133">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="ac7cc-134">W przypadku braku tego elementu z pliku konfiguracji programu .NET Framework będzie używać ustawień serwera proxy w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-134">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="ac7cc-135">Wartość `proxyaddress` atrybutu powinna być poprawnie sformułowanym wskaźnik URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="ac7cc-135">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="ac7cc-136">`scriptLocation` Odnosi się do automatycznego wykrywania skryptów konfiguracji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-136">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="ac7cc-137"><xref:System.Net.WebProxy> Klasy będzie podejmować próby zlokalizowania skryptu konfiguracji (zazwyczaj nazwanego Wpad.dat) po **Użyj skryptu automatycznej konfiguracji** opcja jest zaznaczona w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-137">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span>  
  
 <span data-ttu-id="ac7cc-138">Użyj `usesystemdefault` atrybutu dla aplikacji programu .NET Framework w wersji 1.1, które migracji do wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="ac7cc-139">Jeśli jest zgłaszany wyjątek `proxyaddress` atrybut określa nieprawidłowy domyślny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="ac7cc-140"><xref:System.Exception.InnerException%2A> Na wyjątku powinna mieć więcej informacji na temat przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ac7cc-141">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ac7cc-141">Configuration Files</span></span>  
 <span data-ttu-id="ac7cc-142">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ac7cc-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac7cc-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac7cc-143">Example</span></span>  
 <span data-ttu-id="ac7cc-144">Poniższy przykład używa ustawień domyślnych z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwera proxy dla lokalnych.</span><span class="sxs-lookup"><span data-stu-id="ac7cc-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac7cc-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac7cc-145">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="ac7cc-146">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="ac7cc-146">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
