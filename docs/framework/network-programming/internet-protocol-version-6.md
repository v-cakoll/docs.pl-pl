---
title: "Protokół internetowy w wersji 6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e8ac63cae9d70f0249533848fa472da77f04b807
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="7a9c0-102">Protokół internetowy w wersji 6</span><span class="sxs-lookup"><span data-stu-id="7a9c0-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="7a9c0-103">Internet Protocol w wersji 6 (IPv6) to nowy zestaw standardowych protokołów warstwy sieciowej Internetu.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="7a9c0-104">Protokół IPv6 jest przeznaczona do rozwiązuje wiele problemów w bieżącej wersji pakietu protokołu internetowego (nazywane IPv4) w odniesieniu do adresów wyczerpanie, zabezpieczeń, automatycznej konfiguracji, rozszerzalności i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="7a9c0-105">IPv6 rozszerza możliwości Internet umożliwiające nowych typów aplikacji, w tym aplikacje peer-to-peer i przenośnych.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="7a9c0-106">Poniżej przedstawiono główne kwestie bieżącego protokołu IPv4:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
-   <span data-ttu-id="7a9c0-107">Szybkie wyczerpania przestrzeni adresowej.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="7a9c0-108">Powodowało to korzystanie z translatorami adresów sieciowych (NAT), który mapowania wielu adresów prywatnych jeden publiczny adres IP.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="7a9c0-109">Głównych problemów utworzone przez ten mechanizm przetwarzania koszty i braku łączności end-to-end.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
-   <span data-ttu-id="7a9c0-110">Brak obsługi hierarchii.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="7a9c0-111">Ze względu na jego organizacji związanego z używaniem klasy wstępnie zdefiniowanych IPv4 nie ma wartość true, hierarchicznych pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="7a9c0-112">Nie jest możliwe struktury adresów IP w taki sposób, aby rzeczywiście mapy topologii sieci.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="7a9c0-113">Ta luka ważnych projekt tworzy potrzebę dużych tabel routingu w celu dostarczenia pakietów IPv4 do dowolnej lokalizacji w Internecie.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
-   <span data-ttu-id="7a9c0-114">Konfiguracja złożoną siecią.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="7a9c0-115">Przez protokół IPv4, adresy muszą być przypisane statycznie lub przy użyciu protokołu konfiguracji, takie jak DHCP.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="7a9c0-116">W sytuacji idealnej hosty nie musi ufać zarządzanie infrastrukturą DHCP.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="7a9c0-117">Zamiast tego czy one może skonfigurować oparte na segmencie sieci, w którym znajdują się.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
-   <span data-ttu-id="7a9c0-118">Brak wbudowane uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="7a9c0-119">IPv4 nie wymaga obsługi dowolny mechanizm udostępniający uwierzytelniania i szyfrowania w ramach wymiany danych.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="7a9c0-120">Spowoduje to zmianę w przypadku adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-120">This changes with IPv6.</span></span> <span data-ttu-id="7a9c0-121">Zabezpieczenia protokołu internetowego (IPSec) musi być spełniony obsługi protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="7a9c0-122">Nowy pakiet protokołów musi spełniać następujące wymagania podstawowe:</span><span class="sxs-lookup"><span data-stu-id="7a9c0-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
-   <span data-ttu-id="7a9c0-123">Na dużą skalę routingu i adresy z małym obciążeniem.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-123">Large-scale routing and addressing with low overhead.</span></span>  
  
-   <span data-ttu-id="7a9c0-124">Automatyczna konfiguracja w różnych sytuacjach nawiązującego połączenie.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-124">Auto-configuration for various connecting situations.</span></span>  
  
-   <span data-ttu-id="7a9c0-125">Wbudowane uwierzytelnianie i poufności.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="7a9c0-126">Aby uzyskać więcej informacji, zobacz [adresowanie IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [autokonfiguracji IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Włączanie i wyłączanie IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), i [Porady: modyfikowanie pliku konfiguracji komputera, aby włączyć obsługę protokołu IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="7a9c0-127">Odwołania</span><span class="sxs-lookup"><span data-stu-id="7a9c0-127">References</span></span>  
 <span data-ttu-id="7a9c0-128">Poniżej znajdują się wybrane dokumenty RFC, które można znaleźć w witrynie Internet Engineering Task Force ([http://www.ietf.org](http://www.ietf.org/)):</span><span class="sxs-lookup"><span data-stu-id="7a9c0-128">The following are selected RFC documents that you can find at the Internet Engineering Task Force site ([http://www.ietf.org](http://www.ietf.org/)):</span></span>  
  
-   <span data-ttu-id="7a9c0-129">RFC 1287, kierunku architektura przyszłych internetowych.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
-   <span data-ttu-id="7a9c0-130">RFC 1454, porównanie propozycje następnej wersji adresu IP.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
-   <span data-ttu-id="7a9c0-131">RFC 2373, adresu IP w wersji 6 adresowania architektury.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
-   <span data-ttu-id="7a9c0-132">RFC 2374, Format kumulowalnego adresu globalnego emisji pojedynczej protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="7a9c0-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="7a9c0-133">Można również znaleźć informacje dotyczące IPv6 na [obszaru protokołu IPv6 w witrynie Technet](http://go.microsoft.com/fwlink/?LinkID=179658).</span><span class="sxs-lookup"><span data-stu-id="7a9c0-133">You can also find IPv6-related information on the [IPv6 area on Technet](http://go.microsoft.com/fwlink/?LinkID=179658).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a9c0-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a9c0-134">See Also</span></span>  
 [<span data-ttu-id="7a9c0-135">IPv6 Sockets próbki</span><span class="sxs-lookup"><span data-stu-id="7a9c0-135">IPv6 Sockets Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179568)  
 [<span data-ttu-id="7a9c0-136">Przykłady programowania w języku sieci</span><span class="sxs-lookup"><span data-stu-id="7a9c0-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="7a9c0-137">Gniazda</span><span class="sxs-lookup"><span data-stu-id="7a9c0-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
