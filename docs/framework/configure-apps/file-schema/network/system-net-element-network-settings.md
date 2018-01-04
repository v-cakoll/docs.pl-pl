---
title: '&lt;system.Net&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6140a5a66d39cbee3c2a8477dcab88aaa717e745
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemnetgt-element-network-settings"></a><span data-ttu-id="d08e2-102">&lt;system.Net&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="d08e2-102">&lt;system.Net&gt; Element (Network Settings)</span></span>
<span data-ttu-id="d08e2-103">Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="d08e2-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="d08e2-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d08e2-104">\<configuration></span></span>  
<span data-ttu-id="d08e2-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="d08e2-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d08e2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d08e2-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d08e2-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d08e2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d08e2-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d08e2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d08e2-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d08e2-109">Attributes</span></span>  
 <span data-ttu-id="d08e2-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="d08e2-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d08e2-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d08e2-111">Child Elements</span></span>  
  
|<span data-ttu-id="d08e2-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="d08e2-112">**Element**</span></span>|<span data-ttu-id="d08e2-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d08e2-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d08e2-114">authenticationModules —</span><span class="sxs-lookup"><span data-stu-id="d08e2-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="d08e2-115">Określa moduły używane do uwierzytelniania żądań Internet.</span><span class="sxs-lookup"><span data-stu-id="d08e2-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="d08e2-116">connectionmanagement —</span><span class="sxs-lookup"><span data-stu-id="d08e2-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="d08e2-117">Określa maksymalną liczbę połączeń z hostów w Internecie.</span><span class="sxs-lookup"><span data-stu-id="d08e2-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="d08e2-118">defaultProxy —</span><span class="sxs-lookup"><span data-stu-id="d08e2-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="d08e2-119">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="d08e2-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="d08e2-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="d08e2-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="d08e2-121">Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="d08e2-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="d08e2-122">requestCaching —</span><span class="sxs-lookup"><span data-stu-id="d08e2-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="d08e2-123">Określa mechanizm buforowania żądań sieciowych.</span><span class="sxs-lookup"><span data-stu-id="d08e2-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="d08e2-124">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="d08e2-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="d08e2-125">Służy do konfigurowania opcji sieci podstawowej dla klas w <xref:System.Net> i powiązanych podrzędne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="d08e2-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="d08e2-126">webRequestModules —</span><span class="sxs-lookup"><span data-stu-id="d08e2-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="d08e2-127">Określa moduły służące do żądania informacji z Internetu hostów.</span><span class="sxs-lookup"><span data-stu-id="d08e2-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d08e2-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d08e2-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d08e2-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="d08e2-129">**Element**</span></span>|<span data-ttu-id="d08e2-130">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d08e2-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d08e2-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="d08e2-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="d08e2-132">Zawiera ustawienia dla wszystkich obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="d08e2-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d08e2-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d08e2-133">Remarks</span></span>  
 <span data-ttu-id="d08e2-134">[ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element zawiera ustawienia dla klas w <xref:System.Net> i powiązanych podrzędne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="d08e2-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="d08e2-135">Ustawienia skonfigurować moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i Internet modułów żądania odbierania informacji z Internetu hostów.</span><span class="sxs-lookup"><span data-stu-id="d08e2-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d08e2-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="d08e2-136">Example</span></span>  
 <span data-ttu-id="d08e2-137">W poniższym przykładzie przedstawiono typowej konfiguracji używane przez <xref:System.Net> klasy.</span><span class="sxs-lookup"><span data-stu-id="d08e2-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d08e2-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d08e2-138">See Also</span></span>  
 [<span data-ttu-id="d08e2-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="d08e2-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
