---
title: <defaultProxy>, element (ustawienia sieci)
description: <defaultProxy>Element ustawienia sieci konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol) w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 915fdc96dbd4d417f9c9e6aa3ff96de3026491ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504605"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="39e94-103">\<defaultProxy>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="39e94-103">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="39e94-104">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="39e94-104">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="39e94-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="39e94-105">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39e94-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39e94-106">Attributes and Elements</span></span>  
 <span data-ttu-id="39e94-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39e94-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39e94-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39e94-108">Attributes</span></span>  
  
|<span data-ttu-id="39e94-109">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="39e94-109">**Element**</span></span>|<span data-ttu-id="39e94-110">**Opis**</span><span class="sxs-lookup"><span data-stu-id="39e94-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="39e94-111">Określa, czy używany jest serwer proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="39e94-111">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="39e94-112">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="39e94-112">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="39e94-113">Określa, czy domyślne poświadczenia dla tego hosta są używane w celu uzyskania dostępu do serwera proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="39e94-113">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="39e94-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="39e94-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39e94-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39e94-115">Child Elements</span></span>  
  
|<span data-ttu-id="39e94-116">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="39e94-116">**Element**</span></span>|<span data-ttu-id="39e94-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="39e94-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="39e94-118">bypasslist</span><span class="sxs-lookup"><span data-stu-id="39e94-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="39e94-119">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="39e94-119">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="39e94-120">elementu</span><span class="sxs-lookup"><span data-stu-id="39e94-120">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="39e94-121">Dodaje nowy moduł proxy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="39e94-121">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="39e94-122">proxy</span><span class="sxs-lookup"><span data-stu-id="39e94-122">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="39e94-123">Definiuje serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="39e94-123">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39e94-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39e94-124">Parent Elements</span></span>  
  
|<span data-ttu-id="39e94-125">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="39e94-125">**Element**</span></span>|<span data-ttu-id="39e94-126">**Opis**</span><span class="sxs-lookup"><span data-stu-id="39e94-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="39e94-127">system.net</span><span class="sxs-lookup"><span data-stu-id="39e94-127">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="39e94-128">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="39e94-128">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39e94-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39e94-129">Remarks</span></span>  
 <span data-ttu-id="39e94-130">Jeśli element defaultProxy jest pusty, zostaną użyte ustawienia serwera proxy z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="39e94-130">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="39e94-131">To zachowanie różni się od wersji 1,1 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39e94-131">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="39e94-132">Wyjątek jest zgłaszany, jeśli element [module](module-element-network-settings.md) określa typ niepubliczny, typ nie jest wyprowadzany z <xref:System.Net.IWebProxy> klasy, wystąpił wyjątek z konstruktora bez parametrów tego obiektu lub wystąpił wyjątek podczas pobierania domyślnego serwera proxy określonego przez system.</span><span class="sxs-lookup"><span data-stu-id="39e94-132">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="39e94-133"><xref:System.Exception.InnerException%2A>Właściwość wyjątku powinna zawierać więcej informacji o głównej przyczynie błędu.</span><span class="sxs-lookup"><span data-stu-id="39e94-133">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="39e94-134">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="39e94-134">Configuration Files</span></span>  
 <span data-ttu-id="39e94-135">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="39e94-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39e94-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="39e94-136">Example</span></span>  
 <span data-ttu-id="39e94-137">W poniższym przykładzie używane są wartości domyślne z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwer proxy na potrzeby lokalnego dostępu i contoso.com.</span><span class="sxs-lookup"><span data-stu-id="39e94-137">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39e94-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39e94-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="39e94-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="39e94-139">Network Settings Schema</span></span>](index.md)
