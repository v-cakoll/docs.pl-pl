---
title: '&lt;Serwer proxy&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b5ae716994f9b8222a633699367c94480179c97b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltproxygt-element-network-settings"></a><span data-ttu-id="0f399-102">&lt;Serwer proxy&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="0f399-102">&lt;proxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="0f399-103">Definiuje serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="0f399-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="0f399-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="0f399-104">\<configuration></span></span>  
<span data-ttu-id="0f399-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0f399-105">\<system.net></span></span>  
<span data-ttu-id="0f399-106">\<defaultProxy — ></span><span class="sxs-lookup"><span data-stu-id="0f399-106">\<defaultProxy></span></span>  
<span data-ttu-id="0f399-107">\<Serwer proxy ></span><span class="sxs-lookup"><span data-stu-id="0f399-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f399-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f399-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f399-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0f399-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0f399-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0f399-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f399-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0f399-111">Attributes</span></span>  
  
|<span data-ttu-id="0f399-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="0f399-112">**Attribute**</span></span>|<span data-ttu-id="0f399-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="0f399-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="0f399-114">Określa, czy serwer proxy jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="0f399-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="0f399-115">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="0f399-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="0f399-116">Określa, czy serwer proxy jest pomijana dla zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0f399-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="0f399-117">Zasobów lokalnych obejmują serwer lokalny (http://localhost, http://loopback, lub http://127.0.0.1) i identyfikator URI bez kropki (http://webserver).</span><span class="sxs-lookup"><span data-stu-id="0f399-117">Local resources include the local server (http://localhost, http://loopback, or http://127.0.0.1) and a URI without a period (http://webserver).</span></span> <span data-ttu-id="0f399-118">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="0f399-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="0f399-119">Określa identyfikator URI do użycia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="0f399-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="0f399-120">Określa lokalizację skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0f399-120">Specifies the location of the configuration script.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="0f399-121">Określa, czy ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0f399-121">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="0f399-122">Jeśli ustawiono `true`, kolejne atrybuty spowoduje zastąpienie ustawień serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0f399-122">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="0f399-123">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="0f399-123">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f399-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0f399-124">Child Elements</span></span>  
 <span data-ttu-id="0f399-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="0f399-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f399-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0f399-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0f399-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="0f399-127">**Element**</span></span>|<span data-ttu-id="0f399-128">**Opis**</span><span class="sxs-lookup"><span data-stu-id="0f399-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0f399-129">defaultProxy —</span><span class="sxs-lookup"><span data-stu-id="0f399-129">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="0f399-130">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="0f399-130">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="0f399-131">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="0f399-131">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f399-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f399-132">Remarks</span></span>  
 <span data-ttu-id="0f399-133">`proxy` Element definiuje serwera proxy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f399-133">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="0f399-134">W przypadku braku tego elementu z pliku konfiguracji programu .NET Framework będzie używać ustawień serwera proxy w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0f399-134">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="0f399-135">Wartość `proxyaddress` atrybutu powinna być poprawnie sformułowanym wskaźnik URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="0f399-135">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="0f399-136">`scriptLocation` Odnosi się do automatycznego wykrywania skryptów konfiguracji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="0f399-136">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="0f399-137"><xref:System.Net.WebProxy> Klasy będzie podejmować próby zlokalizowania skryptu konfiguracji (zazwyczaj nazwanego Wpad.dat) po **Użyj skryptu automatycznej konfiguracji** opcja jest zaznaczona w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0f399-137">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span>  
  
 <span data-ttu-id="0f399-138">Użyj `usesystemdefault` atrybutu dla aplikacji programu .NET Framework w wersji 1.1, które migracji do wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="0f399-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="0f399-139">Jeśli jest zgłaszany wyjątek `proxyaddress` atrybut określa nieprawidłowy domyślny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="0f399-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="0f399-140"><xref:System.Exception.InnerException%2A> Na wyjątku powinna mieć więcej informacji na temat przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="0f399-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0f399-141">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0f399-141">Configuration Files</span></span>  
 <span data-ttu-id="0f399-142">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0f399-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f399-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f399-143">Example</span></span>  
 <span data-ttu-id="0f399-144">Poniższy przykład używa ustawień domyślnych z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwera proxy dla lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0f399-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f399-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f399-145">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="0f399-146">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="0f399-146">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
