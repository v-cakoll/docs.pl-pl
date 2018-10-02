---
title: Schemat ustawień sieci
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5783e63d81c8951afb6b1646b595fc619d51549c
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028787"
---
# <a name="network-settings-schema"></a><span data-ttu-id="6c059-102">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="6c059-102">Network Settings Schema</span></span>
<span data-ttu-id="6c059-103">Ustawienia sieci Określ, jak .NET Framework łączy się z Internetem.</span><span class="sxs-lookup"><span data-stu-id="6c059-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="6c059-104">W poniższej tabeli opisano funkcję każdego elementu podrzędnego konfiguracji, w obszarze [ \<przestrzeni nazw system.Net >, Element (ustawienia sieci)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6c059-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="6c059-105">Element</span><span class="sxs-lookup"><span data-stu-id="6c059-105">Element</span></span>|<span data-ttu-id="6c059-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6c059-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c059-107">\<authenticationModules >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="6c059-107">\<authenticationModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="6c059-108">Określa moduły używane do uwierzytelniania żądań internetowych.</span><span class="sxs-lookup"><span data-stu-id="6c059-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="6c059-109">\<connectionManagement >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="6c059-109">\<connectionManagement> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="6c059-110">Określa maksymalną liczbę połączeń na hostach w Internecie.</span><span class="sxs-lookup"><span data-stu-id="6c059-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="6c059-111">\<defaultProxy — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="6c059-111">\<defaultProxy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="6c059-112">Określa serwer proxy dla żądań HTTP w Internecie.</span><span class="sxs-lookup"><span data-stu-id="6c059-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="6c059-113">\<mailSettings — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="6c059-113">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="6c059-114">Zawiera ustawienia dla opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="6c059-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="6c059-115">\<requestCaching — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="6c059-115">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="6c059-116">Określa mechanizm buforowania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="6c059-116">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="6c059-117">\<webRequestModules >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="6c059-117">\<webRequestModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="6c059-118">Określa moduły używane do żądania informacji z hostów w Internecie.</span><span class="sxs-lookup"><span data-stu-id="6c059-118">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="6c059-119">Ustawienia identyfikatorów URI Określ, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="6c059-119">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="6c059-120">W poniższej tabeli opisano funkcję każdego elementu podrzędnego konfiguracji, w obszarze [ \<Uri >, Element (ustawienia identyfikatora Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="6c059-120">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="6c059-121">Element</span><span class="sxs-lookup"><span data-stu-id="6c059-121">Element</span></span>|<span data-ttu-id="6c059-122">Opis</span><span class="sxs-lookup"><span data-stu-id="6c059-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c059-123">\<IDN >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="6c059-123">\<idn> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="6c059-124">Określa, jeśli analizy Zinternacjonalizowanych nazw domen (IDN) są stosowane do nazw domen.</span><span class="sxs-lookup"><span data-stu-id="6c059-124">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="6c059-125">\<iriParsing >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="6c059-125">\<iriParsing> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="6c059-126">Określa, jeśli analizy międzynarodowego identyfikatora zasobów (IRI) są stosowane do <xref:System.Uri> , czy powinna być stosowana IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="6c059-126">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="6c059-127">\<schemeSettings >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="6c059-127">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="6c059-128">Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="6c059-128">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c059-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c059-129">See Also</span></span>  
 [<span data-ttu-id="6c059-130">Konfigurowanie aplikacji internetowych</span><span class="sxs-lookup"><span data-stu-id="6c059-130">Configuring Internet Applications</span></span>](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [<span data-ttu-id="6c059-131">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6c059-131">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
