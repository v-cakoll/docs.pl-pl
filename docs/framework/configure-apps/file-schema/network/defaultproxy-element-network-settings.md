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
ms.openlocfilehash: 0945629c1395917bc1cf825f2ba84d20afa99957
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698208"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="271bf-102">\<element > defaultProxy (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="271bf-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="271bf-103">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="271bf-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[<span data-ttu-id="271bf-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="271bf-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="271bf-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="271bf-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="271bf-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultProxy >**</span><span class="sxs-lookup"><span data-stu-id="271bf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="271bf-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="271bf-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="271bf-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="271bf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="271bf-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="271bf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="271bf-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="271bf-110">Attributes</span></span>  
  
|<span data-ttu-id="271bf-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="271bf-111">**Element**</span></span>|<span data-ttu-id="271bf-112">**Opis**</span><span class="sxs-lookup"><span data-stu-id="271bf-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="271bf-113">Określa, czy używany jest serwer proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="271bf-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="271bf-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="271bf-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="271bf-115">Określa, czy domyślne poświadczenia dla tego hosta są używane w celu uzyskania dostępu do serwera proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="271bf-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="271bf-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="271bf-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="271bf-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="271bf-117">Child Elements</span></span>  
  
|<span data-ttu-id="271bf-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="271bf-118">**Element**</span></span>|<span data-ttu-id="271bf-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="271bf-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="271bf-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="271bf-120">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="271bf-121">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="271bf-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="271bf-122">module</span><span class="sxs-lookup"><span data-stu-id="271bf-122">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="271bf-123">Dodaje nowy moduł proxy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="271bf-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="271bf-124">serwera proxy</span><span class="sxs-lookup"><span data-stu-id="271bf-124">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="271bf-125">Definiuje serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="271bf-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="271bf-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="271bf-126">Parent Elements</span></span>  
  
|<span data-ttu-id="271bf-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="271bf-127">**Element**</span></span>|<span data-ttu-id="271bf-128">**Opis**</span><span class="sxs-lookup"><span data-stu-id="271bf-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="271bf-129">system.net</span><span class="sxs-lookup"><span data-stu-id="271bf-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="271bf-130">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="271bf-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="271bf-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="271bf-131">Remarks</span></span>  
 <span data-ttu-id="271bf-132">Jeśli element defaultProxy jest pusty, zostaną użyte ustawienia serwera proxy z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="271bf-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="271bf-133">To zachowanie różni się od wersji 1,1 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="271bf-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="271bf-134">Wyjątek jest zgłaszany, jeśli element [module](module-element-network-settings.md) określa typ niepubliczny, typ nie jest wyprowadzany z klasy <xref:System.Net.IWebProxy>, wystąpił wyjątek z konstruktora bez parametrów tego obiektu lub wystąpił wyjątek podczas pobierania domyślnego serwera proxy określonego przez system.</span><span class="sxs-lookup"><span data-stu-id="271bf-134">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="271bf-135">Właściwość <xref:System.Exception.InnerException%2A> na wyjątku powinna zawierać więcej informacji o głównej przyczynie błędu.</span><span class="sxs-lookup"><span data-stu-id="271bf-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="271bf-136">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="271bf-136">Configuration Files</span></span>  
 <span data-ttu-id="271bf-137">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="271bf-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="271bf-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="271bf-138">Example</span></span>  
 <span data-ttu-id="271bf-139">W poniższym przykładzie używane są wartości domyślne z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwer proxy na potrzeby lokalnego dostępu i contoso.com.</span><span class="sxs-lookup"><span data-stu-id="271bf-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="271bf-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="271bf-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="271bf-141">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="271bf-141">Network Settings Schema</span></span>](index.md)
