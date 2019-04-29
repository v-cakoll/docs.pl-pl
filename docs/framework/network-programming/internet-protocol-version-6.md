---
title: Protokół IPv6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 135d87f126dcdb9689c23adbaaa4786bc69a3e09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642324"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="3506f-102">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="3506f-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="3506f-103">Protokołu internetowego w wersji 6 (IPv6) to nowy zestaw standardowych protokołów służący do warstwy sieci Internet.</span><span class="sxs-lookup"><span data-stu-id="3506f-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="3506f-104">Protokół IPv6 pozwala rozwiązać wiele problemów w bieżącej wersji pakietu Internet Protocol (nazywane IPv4) w odniesieniu do adresów wyczerpanie, zabezpieczeń, konfiguracji automatycznego, rozszerzalność i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3506f-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="3506f-105">Protokół IPv6 rozszerza możliwości Internetu, aby włączyć nowych rodzajów aplikacji, w tym aplikacji peer-to-peer i na urządzeniach przenośnych.</span><span class="sxs-lookup"><span data-stu-id="3506f-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="3506f-106">Oto główne kwestie bieżącego protokołu IPv4:</span><span class="sxs-lookup"><span data-stu-id="3506f-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="3506f-107">Szybkie wyczerpania przestrzeni adresowej.</span><span class="sxs-lookup"><span data-stu-id="3506f-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="3506f-108">Doprowadziło to do korzystania z translatorami adresów sieciowych (NAT), które mapowania wielu adresów prywatnych do jednego publicznego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="3506f-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="3506f-109">Głównych problemów, które są tworzone przez ten mechanizm przetwarzania kosztów i braku łączności end-to-end.</span><span class="sxs-lookup"><span data-stu-id="3506f-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="3506f-110">Brak obsługi hierarchii.</span><span class="sxs-lookup"><span data-stu-id="3506f-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="3506f-111">Ze względu na swojej organizacji związane klasę wstępnie zdefiniowanych IPv4 brakuje true obsługi hierarchicznych.</span><span class="sxs-lookup"><span data-stu-id="3506f-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="3506f-112">Nie jest możliwe struktury adresów IP w taki sposób, że naprawdę mapy topologii sieci.</span><span class="sxs-lookup"><span data-stu-id="3506f-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="3506f-113">Ta luka kluczowe znaczenie podczas projektowania tworzy potrzebę dużych tabel routingu w celu dostarczenia pakietów IPv4 do dowolnej lokalizacji w Internecie.</span><span class="sxs-lookup"><span data-stu-id="3506f-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="3506f-114">Konfiguracja sieci złożonych.</span><span class="sxs-lookup"><span data-stu-id="3506f-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="3506f-115">Za pomocą protokołu IPv4, adresy muszą być statycznie przypisane lub przy użyciu protokołu konfiguracji, takie jak DHCP.</span><span class="sxs-lookup"><span data-stu-id="3506f-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="3506f-116">W sytuacji idealnej hosty nie musi opierać się na zarządzanie infrastrukturą DHCP.</span><span class="sxs-lookup"><span data-stu-id="3506f-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="3506f-117">Zamiast tego będzie one możliwość skonfigurowania oparte na segmencie sieci, w którym znajdują się.</span><span class="sxs-lookup"><span data-stu-id="3506f-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="3506f-118">Brak wbudowanego uwierzytelniania i poufnością.</span><span class="sxs-lookup"><span data-stu-id="3506f-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="3506f-119">IPv4 nie wymaga obsługi dla dowolnego mechanizm, który zapewnia uwierzytelniania i szyfrowania w ramach wymiany danych.</span><span class="sxs-lookup"><span data-stu-id="3506f-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="3506f-120">Spowoduje to zmianę przy użyciu protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="3506f-120">This changes with IPv6.</span></span> <span data-ttu-id="3506f-121">Zabezpieczenia protokołu internetowego (IPSec) jest wymaganie obsługi protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="3506f-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="3506f-122">Nowy pakiet protokołów musi spełniać następujące wymagania podstawowe:</span><span class="sxs-lookup"><span data-stu-id="3506f-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="3506f-123">Na dużą skalę usługa routing i adresowanie z niskie obciążenie.</span><span class="sxs-lookup"><span data-stu-id="3506f-123">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="3506f-124">Automatyczna konfiguracja w różnych sytuacjach nawiązującego połączenie.</span><span class="sxs-lookup"><span data-stu-id="3506f-124">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="3506f-125">Wbudowane uwierzytelnianie i poufnością.</span><span class="sxs-lookup"><span data-stu-id="3506f-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="3506f-126">Aby uzyskać więcej informacji, zobacz [adresowanie IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [automatyczna konfiguracja IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Włączanie i wyłączanie protokołu IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), i [Jak: Zmodyfikuj plik konfiguracji komputera, aby włączyć obsługę protokołu IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="3506f-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="3506f-127">Odwołania</span><span class="sxs-lookup"><span data-stu-id="3506f-127">References</span></span>  
 <span data-ttu-id="3506f-128">Poniżej przedstawiono wybrane dokumenty RFC, które znajdują się w [Internet Engineering Task Force (IETF)](https://www.ietf.org/) witryny sieci Web:</span><span class="sxs-lookup"><span data-stu-id="3506f-128">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="3506f-129">RFC 1287, kierunku architektura przyszłych internetowych.</span><span class="sxs-lookup"><span data-stu-id="3506f-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="3506f-130">RFC 1454, porównanie propozycje następnej wersji adresu IP.</span><span class="sxs-lookup"><span data-stu-id="3506f-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="3506f-131">RFC 2373, adresów IP w wersji 6 adresowania architektury.</span><span class="sxs-lookup"><span data-stu-id="3506f-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="3506f-132">RFC 2374, Format się agregowaniu globalnego adresu emisji pojedynczej protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="3506f-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="3506f-133">Można również znaleźć informacje dotyczące protokołu IPv6 na [adresów IP w wersji 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span><span class="sxs-lookup"><span data-stu-id="3506f-133">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3506f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3506f-134">See also</span></span>

- [<span data-ttu-id="3506f-135">Przykładowe gniazda IPv6</span><span class="sxs-lookup"><span data-stu-id="3506f-135">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="3506f-136">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="3506f-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
- [<span data-ttu-id="3506f-137">Gniazda</span><span class="sxs-lookup"><span data-stu-id="3506f-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
