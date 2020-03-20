---
title: <proxy>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154793"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="e3e8c-102">\<element> serwera proxy (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="e3e8c-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="e3e8c-103">Definiuje serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-103">Defines a proxy server.</span></span>  

<span data-ttu-id="e3e8c-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3e8c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3e8c-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e3e8c-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e3e8c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e3e8c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="e3e8c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>proxy**</span><span class="sxs-lookup"><span data-stu-id="e3e8c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e3e8c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3e8c-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3e8c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e3e8c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e3e8c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3e8c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e3e8c-111">Attributes</span></span>  
  
|<span data-ttu-id="e3e8c-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="e3e8c-112">**Attribute**</span></span>|<span data-ttu-id="e3e8c-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e3e8c-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="e3e8c-114">Określa, czy serwer proxy jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="e3e8c-115">Wartością domyślną jest `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="e3e8c-116">Określa, czy serwer proxy jest pomijany dla zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="e3e8c-117">Zasoby lokalne obejmują serwer`http://localhost` `http://loopback`lokalny `http://127.0.0.1`( , , lub )`http://webserver`i identyfikator URI bez kropki ( ).</span><span class="sxs-lookup"><span data-stu-id="e3e8c-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="e3e8c-118">Wartością domyślną jest `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="e3e8c-119">Określa identyfikator URI serwera proxy do użycia.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="e3e8c-120">Określa lokalizację skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="e3e8c-121">Nie należy `bypassonlocal` używać atrybutu z tym atrybutem.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="e3e8c-122">Określa, czy mają być używane ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="e3e8c-123">Jeśli ustawiona na `true`, kolejne atrybuty zastąpią ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="e3e8c-124">Wartością domyślną jest `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3e8c-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e3e8c-125">Child Elements</span></span>  
 <span data-ttu-id="e3e8c-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3e8c-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e3e8c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e3e8c-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="e3e8c-128">**Element**</span></span>|<span data-ttu-id="e3e8c-129">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e3e8c-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e3e8c-130">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="e3e8c-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="e3e8c-131">Konfiguruje serwer proxy Protokołu transferu hipertekstu (HTTP).</span><span class="sxs-lookup"><span data-stu-id="e3e8c-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="e3e8c-132">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="e3e8c-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3e8c-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3e8c-133">Remarks</span></span>  
 <span data-ttu-id="e3e8c-134">Element `proxy` definiuje serwer proxy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="e3e8c-135">Jeśli w pliku konfiguracyjnym brakuje tego elementu, program .NET Framework użyje ustawień serwera proxy w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="e3e8c-136">Wartość atrybutu `proxyaddress` powinna być dobrze sformułowanym wskaźnikiem jednolitego zasobu (URI).</span><span class="sxs-lookup"><span data-stu-id="e3e8c-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="e3e8c-137">Atrybut `scriptLocation` odnosi się do automatycznego wykrywania skryptów konfiguracji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="e3e8c-138">Klasa <xref:System.Net.WebProxy> spróbuje zlokalizować skrypt konfiguracji (zwykle o nazwie Wpad.dat) po wybraniu opcji **Użyj skryptu konfiguracji automatycznej** w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="e3e8c-139">Jeśli `bypassonlocal` jest ustawiona `scriptLocation` na dowolną wartość, jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="e3e8c-140">Użyj `usesystemdefault` atrybutu dla aplikacji .NET Framework w wersji 1.1, które są migrowane do wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="e3e8c-141">Wyjątek jest zgłaszany, `proxyaddress` jeśli atrybut określa nieprawidłowy domyślny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="e3e8c-142">Właściwość <xref:System.Exception.InnerException%2A> na wyjątek powinien mieć więcej informacji na temat głównej przyczyny błędu.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e3e8c-143">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e3e8c-143">Configuration Files</span></span>  
 <span data-ttu-id="e3e8c-144">Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e3e8c-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3e8c-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3e8c-145">Example</span></span>  
 <span data-ttu-id="e3e8c-146">W poniższym przykładzie użyto wartości domyślnych z serwera proxy programu Internet Explorer, określono adres serwera proxy i pominięto serwer proxy dostępu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="e3e8c-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3e8c-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3e8c-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e3e8c-148">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e3e8c-148">Network Settings Schema</span></span>](index.md)
