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
ms.openlocfilehash: 94858f141e7d540454fca9c151c760c37f9ebbb0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697947"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="325c7-102">\<proxy >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="325c7-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="325c7-103">Definiuje serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="325c7-103">Defines a proxy server.</span></span>  
  
[<span data-ttu-id="325c7-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="325c7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="325c7-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="325c7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="325c7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="325c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="325c7-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<proxy >**</span><span class="sxs-lookup"><span data-stu-id="325c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="325c7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="325c7-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="325c7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="325c7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="325c7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="325c7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="325c7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="325c7-111">Attributes</span></span>  
  
|<span data-ttu-id="325c7-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="325c7-112">**Attribute**</span></span>|<span data-ttu-id="325c7-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="325c7-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="325c7-114">Określa, czy serwer proxy jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="325c7-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="325c7-115">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="325c7-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="325c7-116">Określa, czy serwer proxy jest pomijany dla zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="325c7-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="325c7-117">Zasoby lokalne obejmują serwer lokalny (`http://localhost`, `http://loopback` lub `http://127.0.0.1`) i identyfikator URI bez kropki (`http://webserver`).</span><span class="sxs-lookup"><span data-stu-id="325c7-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="325c7-118">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="325c7-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="325c7-119">Określa identyfikator URI serwera proxy do użycia.</span><span class="sxs-lookup"><span data-stu-id="325c7-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="325c7-120">Określa lokalizację skryptu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="325c7-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="325c7-121">Nie należy używać atrybutu `bypassonlocal` z tym atrybutem.</span><span class="sxs-lookup"><span data-stu-id="325c7-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="325c7-122">Określa, czy mają być używane ustawienia serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="325c7-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="325c7-123">Ustawienie wartości `true` spowoduje zastąpienie ustawień serwera proxy programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="325c7-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="325c7-124">Wartość domyślna to `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="325c7-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="325c7-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="325c7-125">Child Elements</span></span>  
 <span data-ttu-id="325c7-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="325c7-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="325c7-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="325c7-127">Parent Elements</span></span>  
  
|<span data-ttu-id="325c7-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="325c7-128">**Element**</span></span>|<span data-ttu-id="325c7-129">**Opis**</span><span class="sxs-lookup"><span data-stu-id="325c7-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="325c7-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="325c7-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="325c7-131">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="325c7-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="325c7-132">Wartość tekstowa</span><span class="sxs-lookup"><span data-stu-id="325c7-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="325c7-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="325c7-133">Remarks</span></span>  
 <span data-ttu-id="325c7-134">Element `proxy` definiuje serwer proxy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="325c7-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="325c7-135">Jeśli w pliku konfiguracji brakuje tego elementu, .NET Framework będzie używać ustawień serwera proxy w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="325c7-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="325c7-136">Wartość atrybutu `proxyaddress` powinna być poprawnie sformułowanym jednolitym wskaźnikiem zasobów (URI).</span><span class="sxs-lookup"><span data-stu-id="325c7-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="325c7-137">Atrybut `scriptLocation` odnosi się do automatycznego wykrywania skryptów konfiguracji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="325c7-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="325c7-138">Klasa <xref:System.Net.WebProxy> podejmie próbę zlokalizowania skryptu konfiguracji (o nazwie WPAD. dat) w przypadku wybrania opcji **Użyj skryptu automatycznej konfiguracji** w programie Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="325c7-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="325c7-139">Jeśli `bypassonlocal` jest ustawiona na dowolną wartość, `scriptLocation` jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="325c7-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="325c7-140">Użyj atrybutu `usesystemdefault` dla aplikacji .NET Framework w wersji 1,1, które są migrowane do wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="325c7-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="325c7-141">Wyjątek jest generowany, jeśli atrybut `proxyaddress` określa nieprawidłowy domyślny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="325c7-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="325c7-142">Właściwość <xref:System.Exception.InnerException%2A> tego wyjątku powinna zawierać więcej informacji o głównej przyczynie błędu.</span><span class="sxs-lookup"><span data-stu-id="325c7-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="325c7-143">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="325c7-143">Configuration Files</span></span>  
 <span data-ttu-id="325c7-144">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="325c7-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="325c7-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="325c7-145">Example</span></span>  
 <span data-ttu-id="325c7-146">W poniższym przykładzie używane są wartości domyślne z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwer proxy na potrzeby dostępu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="325c7-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="325c7-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="325c7-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="325c7-148">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="325c7-148">Network Settings Schema</span></span>](index.md)
