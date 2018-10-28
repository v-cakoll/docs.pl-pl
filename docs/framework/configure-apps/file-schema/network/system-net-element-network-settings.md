---
title: '&lt;przestrzeni nazw system.Net&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 82e022e28d3559791be3236fb80081807426a456
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192541"
---
# <a name="ltsystemnetgt-element-network-settings"></a><span data-ttu-id="9d578-102">&lt;przestrzeni nazw system.Net&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="9d578-102">&lt;system.Net&gt; Element (Network Settings)</span></span>
<span data-ttu-id="9d578-103">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="9d578-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="9d578-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="9d578-104">\<configuration></span></span>  
<span data-ttu-id="9d578-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9d578-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d578-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d578-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d578-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d578-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9d578-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d578-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d578-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d578-109">Attributes</span></span>  
 <span data-ttu-id="9d578-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="9d578-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d578-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d578-111">Child Elements</span></span>  
  
|<span data-ttu-id="9d578-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="9d578-112">**Element**</span></span>|<span data-ttu-id="9d578-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9d578-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9d578-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="9d578-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="9d578-115">Określa moduły używane do uwierzytelniania żądań internetowych.</span><span class="sxs-lookup"><span data-stu-id="9d578-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="9d578-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="9d578-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="9d578-117">Określa maksymalną liczbę połączeń do hostów w Internecie.</span><span class="sxs-lookup"><span data-stu-id="9d578-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="9d578-118">defaultProxy —</span><span class="sxs-lookup"><span data-stu-id="9d578-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="9d578-119">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="9d578-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="9d578-120">mailSettings —</span><span class="sxs-lookup"><span data-stu-id="9d578-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="9d578-121">Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="9d578-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="9d578-122">requestCaching —</span><span class="sxs-lookup"><span data-stu-id="9d578-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="9d578-123">Określa mechanizm buforowania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="9d578-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="9d578-124">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="9d578-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="9d578-125">Konfiguruje opcje sieciowe podstawowe dla klas w <xref:System.Net> i powiązane podrzędne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="9d578-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="9d578-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="9d578-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="9d578-127">Określa moduły do użycia na żądanie informacji z hostów w Internecie.</span><span class="sxs-lookup"><span data-stu-id="9d578-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d578-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d578-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9d578-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="9d578-129">**Element**</span></span>|<span data-ttu-id="9d578-130">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9d578-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9d578-131">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="9d578-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="9d578-132">Zawiera ustawienia dla wszystkich przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9d578-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d578-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d578-133">Remarks</span></span>  
 <span data-ttu-id="9d578-134">[ \<Przestrzeni nazw system.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element zawiera ustawienia dla klas w <xref:System.Net> i powiązane podrzędne przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="9d578-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="9d578-135">Ustawienia skonfiguruj moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty e-mail, serwer proxy i moduły żądania internetowe odbieranie informacji z hostów w Internecie.</span><span class="sxs-lookup"><span data-stu-id="9d578-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d578-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d578-136">Example</span></span>  
 <span data-ttu-id="9d578-137">W poniższym przykładzie pokazano typową konfigurację posługują się <xref:System.Net> klasy.</span><span class="sxs-lookup"><span data-stu-id="9d578-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d578-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d578-138">See Also</span></span>  
- [<span data-ttu-id="9d578-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9d578-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
