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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698208"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="0897e-102">\<defaultProxy>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="0897e-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="0897e-103">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="0897e-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="0897e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0897e-104">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0897e-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0897e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0897e-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0897e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0897e-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0897e-107">Attributes</span></span>  
  
|<span data-ttu-id="0897e-108">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="0897e-108">**Element**</span></span>|<span data-ttu-id="0897e-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="0897e-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="0897e-110">Określa, czy używany jest serwer proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0897e-110">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="0897e-111">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="0897e-111">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="0897e-112">Określa, czy domyślne poświadczenia dla tego hosta są używane w celu uzyskania dostępu do serwera proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0897e-112">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="0897e-113">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="0897e-113">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0897e-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0897e-114">Child Elements</span></span>  
  
|<span data-ttu-id="0897e-115">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="0897e-115">**Element**</span></span>|<span data-ttu-id="0897e-116">**Opis**</span><span class="sxs-lookup"><span data-stu-id="0897e-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0897e-117">bypasslist</span><span class="sxs-lookup"><span data-stu-id="0897e-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="0897e-118">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="0897e-118">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="0897e-119">elementu</span><span class="sxs-lookup"><span data-stu-id="0897e-119">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="0897e-120">Dodaje nowy moduł proxy do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0897e-120">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="0897e-121">proxy</span><span class="sxs-lookup"><span data-stu-id="0897e-121">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="0897e-122">Definiuje serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="0897e-122">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0897e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0897e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0897e-124">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="0897e-124">**Element**</span></span>|<span data-ttu-id="0897e-125">**Opis**</span><span class="sxs-lookup"><span data-stu-id="0897e-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0897e-126">system.net</span><span class="sxs-lookup"><span data-stu-id="0897e-126">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="0897e-127">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="0897e-127">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0897e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0897e-128">Remarks</span></span>  
 <span data-ttu-id="0897e-129">Jeśli element defaultProxy jest pusty, zostaną użyte ustawienia serwera proxy z programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0897e-129">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="0897e-130">To zachowanie różni się od wersji 1,1 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0897e-130">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="0897e-131">Wyjątek jest zgłaszany, jeśli element [module](module-element-network-settings.md) określa typ niepubliczny, typ nie jest wyprowadzany z <xref:System.Net.IWebProxy> klasy, wystąpił wyjątek z konstruktora bez parametrów tego obiektu lub wystąpił wyjątek podczas pobierania domyślnego serwera proxy określonego przez system.</span><span class="sxs-lookup"><span data-stu-id="0897e-131">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="0897e-132"><xref:System.Exception.InnerException%2A>Właściwość wyjątku powinna zawierać więcej informacji o głównej przyczynie błędu.</span><span class="sxs-lookup"><span data-stu-id="0897e-132">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0897e-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0897e-133">Configuration Files</span></span>  
 <span data-ttu-id="0897e-134">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="0897e-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0897e-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="0897e-135">Example</span></span>  
 <span data-ttu-id="0897e-136">W poniższym przykładzie używane są wartości domyślne z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwer proxy na potrzeby lokalnego dostępu i contoso.com.</span><span class="sxs-lookup"><span data-stu-id="0897e-136">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0897e-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0897e-137">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="0897e-138">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="0897e-138">Network Settings Schema</span></span>](index.md)
