---
title: '&lt;Serwer proxy&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 3a6d5b080c74fbd3f6ebca9882c1667951cfcb91
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183676"
---
# <a name="ltproxygt-element-network-settings"></a><span data-ttu-id="d71c8-102">&lt;Serwer proxy&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="d71c8-102">&lt;proxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="d71c8-103">Określa serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="d71c8-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="d71c8-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d71c8-104">\<configuration></span></span>  
<span data-ttu-id="d71c8-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d71c8-105">\<system.net></span></span>  
<span data-ttu-id="d71c8-106">\<defaultProxy — ></span><span class="sxs-lookup"><span data-stu-id="d71c8-106">\<defaultProxy></span></span>  
<span data-ttu-id="d71c8-107">\<Serwer proxy ></span><span class="sxs-lookup"><span data-stu-id="d71c8-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71c8-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d71c8-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d71c8-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d71c8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d71c8-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d71c8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d71c8-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d71c8-111">Attributes</span></span>  
  
|<span data-ttu-id="d71c8-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="d71c8-112">**Attribute**</span></span>|<span data-ttu-id="d71c8-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d71c8-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="d71c8-114">Określa, czy serwer proxy jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="d71c8-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="d71c8-115">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="d71c8-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="d71c8-116">Określa, czy serwer proxy jest pomijane dla zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="d71c8-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="d71c8-117">Lokalne zasoby obejmują serwer lokalny (`http://localhost`, `http://loopback`, lub `http://127.0.0.1`) i identyfikator URI bez kropki (`http://webserver`).</span><span class="sxs-lookup"><span data-stu-id="d71c8-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="d71c8-118">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="d71c8-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="d71c8-119">Określa identyfikator URI do użycia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="d71c8-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="d71c8-120">Określa lokalizację skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d71c8-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="d71c8-121">Nie używaj `bypassonlocal` atrybutu z tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d71c8-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="d71c8-122">Określa, czy ma być używany program Internet Explorer, ustawienia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="d71c8-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="d71c8-123">Jeśli ustawiono `true`, kolejne atrybutów spowoduje przesłonięcie ustawień serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d71c8-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="d71c8-124">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="d71c8-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d71c8-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d71c8-125">Child Elements</span></span>  
 <span data-ttu-id="d71c8-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="d71c8-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d71c8-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d71c8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d71c8-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="d71c8-128">**Element**</span></span>|<span data-ttu-id="d71c8-129">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d71c8-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d71c8-130">defaultProxy —</span><span class="sxs-lookup"><span data-stu-id="d71c8-130">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="d71c8-131">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="d71c8-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="d71c8-132">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="d71c8-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d71c8-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d71c8-133">Remarks</span></span>  
 <span data-ttu-id="d71c8-134">`proxy` Element definiuje serwera proxy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d71c8-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="d71c8-135">W przypadku braku tego elementu z pliku konfiguracji .NET Framework będą używać ustawień serwera proxy w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d71c8-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="d71c8-136">Wartość `proxyaddress` atrybut powinien być poprawnie sformułowany Uniform Resource Indicator (URI).</span><span class="sxs-lookup"><span data-stu-id="d71c8-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="d71c8-137">`scriptLocation` Atrybut odwołuje się do automatycznego wykrywania skrypty konfiguracji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="d71c8-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="d71c8-138"><xref:System.Net.WebProxy> Klasy będzie podejmować próby zlokalizowania skryptu konfiguracji (zwykle o nazwie Wpad.dat) po **Użyj skryptu automatycznej konfiguracji** opcja jest zaznaczona w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="d71c8-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="d71c8-139">Jeśli `bypassonlocal` jest ustawiona na jakąkolwiek wartość `scriptLocation` jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="d71c8-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="d71c8-140">Użyj `usesystemdefault` atrybutu dla aplikacji w wersji 1.1 programu .NET Framework, które jest przeprowadzana migracja do wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="d71c8-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="d71c8-141">Wyjątek jest generowany, jeśli `proxyaddress` atrybut określa nieprawidłowy domyślny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="d71c8-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="d71c8-142"><xref:System.Exception.InnerException%2A> Właściwość w drodze wyjątku powinien mieć więcej informacji na temat przyczyny błędu.</span><span class="sxs-lookup"><span data-stu-id="d71c8-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d71c8-143">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d71c8-143">Configuration Files</span></span>  
 <span data-ttu-id="d71c8-144">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d71c8-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d71c8-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="d71c8-145">Example</span></span>  
 <span data-ttu-id="d71c8-146">Poniższy przykład używa ustawień domyślnych z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwera proxy dla dostępu do lokalnego.</span><span class="sxs-lookup"><span data-stu-id="d71c8-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d71c8-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d71c8-147">See Also</span></span>  
- <xref:System.Net.WebProxy?displayProperty=nameWithType>  
- [<span data-ttu-id="d71c8-148">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="d71c8-148">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
