---
title: '&lt;defaultProxy —&gt; — Element (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a91775ff9f46eba772a959cfac3115c9720ac5ab
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742721"
---
# <a name="ltdefaultproxygt-element-network-settings"></a><span data-ttu-id="f8742-102">&lt;defaultProxy —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="f8742-102">&lt;defaultProxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f8742-103">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="f8742-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="f8742-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f8742-104">\<configuration></span></span>  
<span data-ttu-id="f8742-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f8742-105">\<system.net></span></span>  
<span data-ttu-id="f8742-106">\<defaultProxy — ></span><span class="sxs-lookup"><span data-stu-id="f8742-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8742-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8742-107">Syntax</span></span>  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8742-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f8742-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f8742-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f8742-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8742-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f8742-110">Attributes</span></span>  
  
|<span data-ttu-id="f8742-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="f8742-111">**Element**</span></span>|<span data-ttu-id="f8742-112">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f8742-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="f8742-113">Określa, czy jest używany serwer proxy sieci web.</span><span class="sxs-lookup"><span data-stu-id="f8742-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="f8742-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="f8742-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="f8742-115">Określa, czy dostępu do serwera proxy sieci web są używane domyślne poświadczenia dla tego hosta.</span><span class="sxs-lookup"><span data-stu-id="f8742-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="f8742-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f8742-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8742-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f8742-117">Child Elements</span></span>  
  
|<span data-ttu-id="f8742-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="f8742-118">**Element**</span></span>|<span data-ttu-id="f8742-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f8742-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f8742-120">bypasslist —</span><span class="sxs-lookup"><span data-stu-id="f8742-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="f8742-121">Zawiera zestaw wyrażeń regularnych, opisujących adresów, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="f8742-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="f8742-122">Moduł</span><span class="sxs-lookup"><span data-stu-id="f8742-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="f8742-123">Dodaje nowy moduł serwera proxy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8742-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="f8742-124">Serwer proxy</span><span class="sxs-lookup"><span data-stu-id="f8742-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="f8742-125">Definiuje serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="f8742-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8742-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f8742-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f8742-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="f8742-127">**Element**</span></span>|<span data-ttu-id="f8742-128">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f8742-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f8742-129">System.NET</span><span class="sxs-lookup"><span data-stu-id="f8742-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="f8742-130">Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="f8742-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8742-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8742-131">Remarks</span></span>  
 <span data-ttu-id="f8742-132">Jeśli defaultProxy — element jest pusta, ustawienia serwera proxy w programie Internet Explorer będzie używany.</span><span class="sxs-lookup"><span data-stu-id="f8742-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="f8742-133">To zachowanie różni się od programu .NET Framework w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="f8742-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f8742-134">Jest zwracany wyjątek, jeśli [modułu](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element określa niepublicznego typu, nie jest pochodny typ <xref:System.Net.IWebProxy> klasy wystąpił wyjątek z domyślny konstruktor obiektu lub wystąpił wyjątek podczas Pobieranie określony system domyślny serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="f8742-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the default constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="f8742-135"><xref:System.Exception.InnerException%2A> Na wyjątku powinna mieć więcej informacji na temat przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="f8742-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f8742-136">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f8742-136">Configuration Files</span></span>  
 <span data-ttu-id="f8742-137">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f8742-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8742-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8742-138">Example</span></span>  
 <span data-ttu-id="f8742-139">Poniższy przykład używa ustawień domyślnych z serwera proxy programu Internet Explorer, określa adres serwera proxy i pomija serwera proxy na potrzeby dostępu lokalnego i contoso.com.</span><span class="sxs-lookup"><span data-stu-id="f8742-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8742-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8742-140">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="f8742-141">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f8742-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
