---
title: '&lt;system.Net&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f9098ce379cbaf12f589270729018da399f282b0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemnetgt-element-network-settings"></a><span data-ttu-id="69737-102">&lt;system.Net&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="69737-102">&lt;system.Net&gt; Element (Network Settings)</span></span>
<span data-ttu-id="69737-103">Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="69737-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="69737-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="69737-104">\<configuration></span></span>  
<span data-ttu-id="69737-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="69737-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69737-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="69737-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69737-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69737-107">Attributes and Elements</span></span>  
 <span data-ttu-id="69737-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69737-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69737-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69737-109">Attributes</span></span>  
 <span data-ttu-id="69737-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="69737-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69737-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69737-111">Child Elements</span></span>  
  
|<span data-ttu-id="69737-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="69737-112">**Element**</span></span>|<span data-ttu-id="69737-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="69737-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="69737-114">authenticationModules —</span><span class="sxs-lookup"><span data-stu-id="69737-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="69737-115">Określa moduły używane do uwierzytelniania żądań Internet.</span><span class="sxs-lookup"><span data-stu-id="69737-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="69737-116">connectionmanagement —</span><span class="sxs-lookup"><span data-stu-id="69737-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="69737-117">Określa maksymalną liczbę połączeń z hostów w Internecie.</span><span class="sxs-lookup"><span data-stu-id="69737-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="69737-118">defaultProxy —</span><span class="sxs-lookup"><span data-stu-id="69737-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="69737-119">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="69737-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="69737-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="69737-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="69737-121">Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="69737-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="69737-122">requestCaching —</span><span class="sxs-lookup"><span data-stu-id="69737-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="69737-123">Określa mechanizm buforowania żądań sieciowych.</span><span class="sxs-lookup"><span data-stu-id="69737-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="69737-124">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="69737-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="69737-125">Służy do konfigurowania opcji sieci podstawowej dla klas w <xref:System.Net> i powiązanych podrzędne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="69737-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="69737-126">webRequestModules —</span><span class="sxs-lookup"><span data-stu-id="69737-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="69737-127">Określa moduły służące do żądania informacji z Internetu hostów.</span><span class="sxs-lookup"><span data-stu-id="69737-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69737-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69737-128">Parent Elements</span></span>  
  
|<span data-ttu-id="69737-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="69737-129">**Element**</span></span>|<span data-ttu-id="69737-130">**Opis**</span><span class="sxs-lookup"><span data-stu-id="69737-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="69737-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="69737-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="69737-132">Zawiera ustawienia dla wszystkich obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="69737-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69737-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69737-133">Remarks</span></span>  
 <span data-ttu-id="69737-134">[ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element zawiera ustawienia dla klas w <xref:System.Net> i powiązanych podrzędne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="69737-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="69737-135">Ustawienia skonfigurować moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i Internet modułów żądania odbierania informacji z Internetu hostów.</span><span class="sxs-lookup"><span data-stu-id="69737-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69737-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="69737-136">Example</span></span>  
 <span data-ttu-id="69737-137">W poniższym przykładzie przedstawiono typowej konfiguracji używane przez <xref:System.Net> klasy.</span><span class="sxs-lookup"><span data-stu-id="69737-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69737-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69737-138">See Also</span></span>  
 [<span data-ttu-id="69737-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="69737-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
