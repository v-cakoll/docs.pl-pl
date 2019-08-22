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
ms.openlocfilehash: 0f5d762a2b688bebcb7c027be6c639b6d64c069d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664107"
---
# <a name="network-settings-schema"></a><span data-ttu-id="a65b0-102">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="a65b0-102">Network Settings Schema</span></span>
<span data-ttu-id="a65b0-103">Ustawienia sieci określają, w jaki sposób .NET Framework nawiązuje połączenie z Internetem.</span><span class="sxs-lookup"><span data-stu-id="a65b0-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="a65b0-104">W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [ \<elementu System .net > (ustawienia sieciowe)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a65b0-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="a65b0-105">Element</span><span class="sxs-lookup"><span data-stu-id="a65b0-105">Element</span></span>|<span data-ttu-id="a65b0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a65b0-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a65b0-107">\<authenticationModules >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a65b0-107">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="a65b0-108">Określa moduły używane do uwierzytelniania żądań internetowych.</span><span class="sxs-lookup"><span data-stu-id="a65b0-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="a65b0-109">\<connectionManagement >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a65b0-109">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a65b0-110">Określa maksymalną liczbę połączeń z hostami internetowymi.</span><span class="sxs-lookup"><span data-stu-id="a65b0-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="a65b0-111">\<defaultProxy >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a65b0-111">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="a65b0-112">Określa serwer proxy używany przez żądania HTTP do Internetu.</span><span class="sxs-lookup"><span data-stu-id="a65b0-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="a65b0-113">\<mailSettings >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a65b0-113">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="a65b0-114">Zawiera ustawienia dla opcji wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="a65b0-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="a65b0-115">\<requestCaching >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a65b0-115">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="a65b0-116">Kontroluje mechanizm buforowania dla żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="a65b0-116">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="a65b0-117">\<webRequestModules >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a65b0-117">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="a65b0-118">Określa moduły używane do żądania informacji z hostów internetowych.</span><span class="sxs-lookup"><span data-stu-id="a65b0-118">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="a65b0-119">Ustawienia identyfikatora URI określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="a65b0-119">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="a65b0-120">W poniższej tabeli opisano funkcję każdego podrzędnego elementu konfiguracji w ramach [ \<identyfikatora URI > element (ustawienia identyfikatora URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a65b0-120">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="a65b0-121">Element</span><span class="sxs-lookup"><span data-stu-id="a65b0-121">Element</span></span>|<span data-ttu-id="a65b0-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a65b0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a65b0-123">\<> IDN — element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="a65b0-123">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="a65b0-124">Określa, czy do nazw domen są stosowane analizowanie międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="a65b0-124">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="a65b0-125">\<iriParsing >, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="a65b0-125">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="a65b0-126">Określa <xref:System.Uri> , czy do i czy należy zastosować analizę IRI (International Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="a65b0-126">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="a65b0-127">\<schemeSettings >, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="a65b0-127">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="a65b0-128">Określa, w <xref:System.Uri> jaki sposób będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="a65b0-128">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a65b0-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a65b0-129">See also</span></span>

- [<span data-ttu-id="a65b0-130">Konfigurowanie aplikacji internetowych</span><span class="sxs-lookup"><span data-stu-id="a65b0-130">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="a65b0-131">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a65b0-131">Configuration File Schema</span></span>](../index.md)
