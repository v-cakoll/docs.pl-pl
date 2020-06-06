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
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698151"
---
# <a name="network-settings-schema"></a><span data-ttu-id="e37ef-102">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e37ef-102">Network Settings Schema</span></span>
<span data-ttu-id="e37ef-103">Ustawienia sieci określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem.</span><span class="sxs-lookup"><span data-stu-id="e37ef-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="e37ef-104">\<system.net>Ustawienia określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="e37ef-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="e37ef-105">W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [ \<system.Net> elementu (Ustawienia sieci)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e37ef-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="e37ef-106">Element</span><span class="sxs-lookup"><span data-stu-id="e37ef-106">Element</span></span>|<span data-ttu-id="e37ef-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e37ef-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e37ef-108">\<authenticationModules>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="e37ef-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="e37ef-109">Określa moduły używane do uwierzytelniania żądań internetowych.</span><span class="sxs-lookup"><span data-stu-id="e37ef-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="e37ef-110">\<connectionManagement>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="e37ef-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="e37ef-111">Określa maksymalną liczbę połączeń z hostami internetowymi.</span><span class="sxs-lookup"><span data-stu-id="e37ef-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="e37ef-112">\<defaultProxy>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="e37ef-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="e37ef-113">Określa serwer proxy używany przez żądania HTTP do Internetu.</span><span class="sxs-lookup"><span data-stu-id="e37ef-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="e37ef-114">\<mailSettings>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="e37ef-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="e37ef-115">Zawiera ustawienia dla opcji wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="e37ef-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="e37ef-116">\<requestCaching>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="e37ef-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="e37ef-117">Kontroluje mechanizm buforowania dla żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="e37ef-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="e37ef-118">\<webRequestModules>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="e37ef-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="e37ef-119">Określa moduły używane do żądania informacji z hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="e37ef-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="e37ef-120">\<uri>Ustawienia określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="e37ef-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="e37ef-121">W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [ \<uri> elementu (ustawienia identyfikatora URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e37ef-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="e37ef-122">Element</span><span class="sxs-lookup"><span data-stu-id="e37ef-122">Element</span></span>|<span data-ttu-id="e37ef-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e37ef-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e37ef-124">\<idn>— Element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="e37ef-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="e37ef-125">Określa, czy do nazw domen są stosowane analizowanie międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="e37ef-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="e37ef-126">\<iriParsing>— Element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="e37ef-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="e37ef-127">Określa, czy do <xref:System.Uri> i czy należy zastosować analizę IRI (International Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="e37ef-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="e37ef-128">\<schemeSettings>— Element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="e37ef-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="e37ef-129">Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="e37ef-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e37ef-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e37ef-130">See also</span></span>

- [<span data-ttu-id="e37ef-131">Konfigurowanie aplikacji internetowych</span><span class="sxs-lookup"><span data-stu-id="e37ef-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="e37ef-132">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e37ef-132">Configuration File Schema</span></span>](../index.md)
