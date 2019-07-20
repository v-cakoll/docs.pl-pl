---
title: <defaultProxy>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 5947808cd137fc4cd280ac683a3e9a14b0d4644d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363864"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="4317b-102">\<defaultProxy >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="4317b-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="4317b-103">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="4317b-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="4317b-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4317b-104">\<configuration></span></span>  
<span data-ttu-id="4317b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4317b-105">\<system.net></span></span>  
<span data-ttu-id="4317b-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="4317b-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4317b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4317b-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4317b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4317b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4317b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4317b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4317b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4317b-110">Attributes</span></span>  
  
|<span data-ttu-id="4317b-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="4317b-111">**Element**</span></span>|<span data-ttu-id="4317b-112">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4317b-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="4317b-113">Określa, czy używany jest serwer proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4317b-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="4317b-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="4317b-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="4317b-115">Określa, czy domyślne poświadczenia dla tego hosta są używane w celu uzyskania dostępu do serwera proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4317b-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="4317b-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="4317b-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4317b-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4317b-117">Child Elements</span></span>  
  
|<span data-ttu-id="4317b-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="4317b-118">**Element**</span></span>|<span data-ttu-id="4317b-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4317b-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4317b-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="4317b-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="4317b-121">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="4317b-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="4317b-122">module</span><span class="sxs-lookup"><span data-stu-id="4317b-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="4317b-123">Dodaje nowy moduł proxy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4317b-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="4317b-124">serwera proxy</span><span class="sxs-lookup"><span data-stu-id="4317b-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="4317b-125">Definiuje serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="4317b-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4317b-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4317b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="4317b-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="4317b-127">**Element**</span></span>|<span data-ttu-id="4317b-128">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4317b-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4317b-129">system.net</span><span class="sxs-lookup"><span data-stu-id="4317b-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="4317b-130">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="4317b-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4317b-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4317b-131">Remarks</span></span>  
 <span data-ttu-id="4317b-132">Jeśli element defaultProxy jest pusty, zostaną użyte ustawienia serwera proxy z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4317b-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="4317b-133">To zachowanie różni się od wersji 1,1 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4317b-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="4317b-134">Wyjątek jest zgłaszany, jeśli element [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) określa typ niepubliczny, typ nie jest wyprowadzany z <xref:System.Net.IWebProxy> klasy, wystąpił wyjątek z konstruktora bez parametrów tego obiektu lub wystąpił wyjątek podczas pobierania domyślny serwer proxy określony przez system.</span><span class="sxs-lookup"><span data-stu-id="4317b-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="4317b-135"><xref:System.Exception.InnerException%2A> Właściwość wyjątku powinna zawierać więcej informacji o głównej przyczynie błędu.</span><span class="sxs-lookup"><span data-stu-id="4317b-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4317b-136">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4317b-136">Configuration Files</span></span>  
 <span data-ttu-id="4317b-137">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="4317b-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4317b-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="4317b-138">Example</span></span>  
 <span data-ttu-id="4317b-139">W poniższym przykładzie używane są wartości domyślne z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwer proxy na potrzeby lokalnego dostępu i contoso.com.</span><span class="sxs-lookup"><span data-stu-id="4317b-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4317b-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4317b-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="4317b-141">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="4317b-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
