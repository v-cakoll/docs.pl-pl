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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154793"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="f0614-102">\<proxy>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="f0614-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="f0614-103">Definiuje serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="f0614-103">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="f0614-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0614-104">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0614-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f0614-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f0614-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f0614-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0614-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f0614-107">Attributes</span></span>  
  
|<span data-ttu-id="f0614-108">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="f0614-108">**Attribute**</span></span>|<span data-ttu-id="f0614-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f0614-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="f0614-110">Określa, czy serwer proxy jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="f0614-110">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="f0614-111">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="f0614-111">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="f0614-112">Określa, czy serwer proxy jest pomijany dla zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="f0614-112">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="f0614-113">Zasoby lokalne obejmują serwer lokalny ( `http://localhost` , `http://loopback` lub `http://127.0.0.1` ) oraz identyfikator URI bez kropki ( `http://webserver` ).</span><span class="sxs-lookup"><span data-stu-id="f0614-113">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="f0614-114">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="f0614-114">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="f0614-115">Określa identyfikator URI serwera proxy do użycia.</span><span class="sxs-lookup"><span data-stu-id="f0614-115">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="f0614-116">Określa lokalizację skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f0614-116">Specifies the location of the configuration script.</span></span> <span data-ttu-id="f0614-117">Nie należy używać `bypassonlocal` atrybutu z tym atrybutem.</span><span class="sxs-lookup"><span data-stu-id="f0614-117">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="f0614-118">Określa, czy mają być używane ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f0614-118">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="f0614-119">Jeśli jest ustawiona na `true` , kolejne atrybuty zastąpią ustawienia proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f0614-119">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="f0614-120">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="f0614-120">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0614-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f0614-121">Child Elements</span></span>  
 <span data-ttu-id="f0614-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="f0614-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0614-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f0614-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f0614-124">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="f0614-124">**Element**</span></span>|<span data-ttu-id="f0614-125">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f0614-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f0614-126">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="f0614-126">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="f0614-127">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="f0614-127">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="f0614-128">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="f0614-128">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0614-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0614-129">Remarks</span></span>  
 <span data-ttu-id="f0614-130">`proxy`Element definiuje serwer proxy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f0614-130">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="f0614-131">Jeśli w pliku konfiguracji brakuje tego elementu, .NET Framework będzie używać ustawień serwera proxy w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f0614-131">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="f0614-132">Wartość `proxyaddress` atrybutu powinna być poprawnie sformułowanym jednolitym wskaźnikiem zasobów (URI).</span><span class="sxs-lookup"><span data-stu-id="f0614-132">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="f0614-133">Ten `scriptLocation` atrybut odnosi się do automatycznego wykrywania skryptów konfiguracji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="f0614-133">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="f0614-134"><xref:System.Net.WebProxy>Klasa podejmie próbę zlokalizowania skryptu konfiguracji (o nazwie WPAD. dat), gdy opcja **Użyj skryptu automatycznej konfiguracji** jest zaznaczona w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f0614-134">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="f0614-135">Jeśli `bypassonlocal` jest ustawiona na dowolną wartość, `scriptLocation` jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="f0614-135">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="f0614-136">Użyj `usesystemdefault` atrybutu dla aplikacji .NET Framework w wersji 1,1, które są migrowane do wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="f0614-136">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="f0614-137">Wyjątek jest generowany, jeśli `proxyaddress` atrybut określa nieprawidłowy domyślny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="f0614-137">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="f0614-138"><xref:System.Exception.InnerException%2A>Właściwość wyjątku powinna zawierać więcej informacji o głównej przyczynie błędu.</span><span class="sxs-lookup"><span data-stu-id="f0614-138">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f0614-139">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f0614-139">Configuration Files</span></span>  
 <span data-ttu-id="f0614-140">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f0614-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0614-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0614-141">Example</span></span>  
 <span data-ttu-id="f0614-142">W poniższym przykładzie używane są wartości domyślne z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwer proxy na potrzeby dostępu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f0614-142">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f0614-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0614-143">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f0614-144">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f0614-144">Network Settings Schema</span></span>](index.md)
