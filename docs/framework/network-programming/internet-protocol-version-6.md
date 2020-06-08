---
title: Protokół IPv6
description: Dowiedz się więcej na temat protokołu IPv6 i różnice między protokołem IPv4. Aplikacje .NET Framework obsługują protokół IPv6, ale mogą wymagać konfiguracji.
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: dd8b0b26e449fba7479d2678aff25ed49e721a90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502395"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="ffab6-104">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="ffab6-104">Internet Protocol Version 6</span></span>
<span data-ttu-id="ffab6-105">Protokół Internet Protocol w wersji 6 (IPv6) to nowy zestaw standardowych protokołów dla warstwy sieciowej Internetu.</span><span class="sxs-lookup"><span data-stu-id="ffab6-105">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="ffab6-106">Protokół IPv6 jest przeznaczony do rozwiązywania wielu problemów z bieżącą wersją internetowego zestawu protokołów (znanego jako IPv4) w odniesieniu do niszczenia, zabezpieczeń, automatycznej konfiguracji, rozszerzalności i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ffab6-106">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="ffab6-107">Protokół IPv6 rozszerza możliwości Internetu w celu umożliwienia korzystania z nowych rodzajów aplikacji, w tym aplikacji równorzędnych i mobilnych.</span><span class="sxs-lookup"><span data-stu-id="ffab6-107">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="ffab6-108">Poniżej przedstawiono główne problemy dotyczące bieżącego protokołu IPv4:</span><span class="sxs-lookup"><span data-stu-id="ffab6-108">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="ffab6-109">Szybka wyczerpanie przestrzeni adresowej.</span><span class="sxs-lookup"><span data-stu-id="ffab6-109">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="ffab6-110">Spowodowało to wykorzystanie translatorów adresów sieciowych (NAT), które mapują wiele adresów prywatnych na jeden publiczny adres IP.</span><span class="sxs-lookup"><span data-stu-id="ffab6-110">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="ffab6-111">Główne problemy stworzone przez ten mechanizm polegają na przetwarzaniu obciążeń i braku kompleksowej łączności.</span><span class="sxs-lookup"><span data-stu-id="ffab6-111">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="ffab6-112">Brak obsługi hierarchii.</span><span class="sxs-lookup"><span data-stu-id="ffab6-112">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="ffab6-113">Ze względu na własną wstępnie zdefiniowaną organizację, w protokole IPv4 brakuje prawdziwej obsługi hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="ffab6-113">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="ffab6-114">Nie jest możliwe tworzenie struktury adresów IP w sposób, który naprawdę mapuje topologię sieci.</span><span class="sxs-lookup"><span data-stu-id="ffab6-114">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="ffab6-115">Ta istotna Luka w projekcie tworzy potrzeby dla dużych tabel routingu do dostarczania pakietów IPv4 do dowolnej lokalizacji w Internecie.</span><span class="sxs-lookup"><span data-stu-id="ffab6-115">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="ffab6-116">Złożona konfiguracja sieci.</span><span class="sxs-lookup"><span data-stu-id="ffab6-116">Complex network configuration.</span></span>  
  
     <span data-ttu-id="ffab6-117">W przypadku protokołu IPv4 adresy muszą być przypisane statycznie lub przy użyciu protokołu konfiguracji, takiego jak DHCP.</span><span class="sxs-lookup"><span data-stu-id="ffab6-117">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="ffab6-118">W idealnej sytuacji hosty nie muszą polegać na administrowaniu infrastrukturą DHCP.</span><span class="sxs-lookup"><span data-stu-id="ffab6-118">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="ffab6-119">Zamiast tego mogą być one konfigurowane na podstawie segmentu sieci, w którym się znajdują.</span><span class="sxs-lookup"><span data-stu-id="ffab6-119">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="ffab6-120">Brak wbudowanego uwierzytelniania i poufności.</span><span class="sxs-lookup"><span data-stu-id="ffab6-120">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="ffab6-121">Protokół IPv4 nie wymaga obsługi żadnego mechanizmu, który zapewnia uwierzytelnianie lub szyfrowanie danych wymienianych.</span><span class="sxs-lookup"><span data-stu-id="ffab6-121">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="ffab6-122">Te zmiany są wprowadzane przy użyciu protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="ffab6-122">This changes with IPv6.</span></span> <span data-ttu-id="ffab6-123">Zabezpieczenia protokołu internetowego (IPSec) są wymagane do obsługi protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="ffab6-123">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="ffab6-124">Nowy pakiet protokołów musi spełniać następujące podstawowe wymagania:</span><span class="sxs-lookup"><span data-stu-id="ffab6-124">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="ffab6-125">Routing i adresowanie na dużą skalę z niskim obciążeniem.</span><span class="sxs-lookup"><span data-stu-id="ffab6-125">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="ffab6-126">Autokonfiguracja w różnych sytuacjach łączących.</span><span class="sxs-lookup"><span data-stu-id="ffab6-126">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="ffab6-127">Wbudowane uwierzytelnianie i poufność.</span><span class="sxs-lookup"><span data-stu-id="ffab6-127">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="ffab6-128">Aby uzyskać więcej informacji, zobacz [adresowanie IPv6](ipv6-addressing.md), [Routing IPv6](ipv6-routing.md), [Autokonfiguracja IPv6](ipv6-auto-configuration.md), [Włączanie i wyłączanie protokołu IPv6](enabling-and-disabling-ipv6.md)oraz [instrukcje: Modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="ffab6-128">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="ffab6-129">Odwołania</span><span class="sxs-lookup"><span data-stu-id="ffab6-129">References</span></span>  
 <span data-ttu-id="ffab6-130">Poniżej przedstawiono wybrane dokumenty RFC, które można znaleźć w witrynie internetowej [Internet Engineering Task Force (IETF)](https://www.ietf.org/) :</span><span class="sxs-lookup"><span data-stu-id="ffab6-130">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="ffab6-131">RFC 1287 w kierunku przyszłej architektury Internetu.</span><span class="sxs-lookup"><span data-stu-id="ffab6-131">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="ffab6-132">RFC 1454, porównanie propozycji dla następnej wersji adresu IP.</span><span class="sxs-lookup"><span data-stu-id="ffab6-132">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="ffab6-133">Architektura adresowania RFC 2373, IP w wersji 6.</span><span class="sxs-lookup"><span data-stu-id="ffab6-133">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="ffab6-134">RFC 2374 — format adresu globalnego emisji pojedynczej IPv6.</span><span class="sxs-lookup"><span data-stu-id="ffab6-134">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="ffab6-135">Informacje dotyczące protokołu IPv6 można także znaleźć w [wersji 6 protokołu IP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span><span class="sxs-lookup"><span data-stu-id="ffab6-135">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffab6-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffab6-136">See also</span></span>

- [<span data-ttu-id="ffab6-137">Przykład protokołu IPv6 Sockets</span><span class="sxs-lookup"><span data-stu-id="ffab6-137">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="ffab6-138">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="ffab6-138">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="ffab6-139">Gniazda</span><span class="sxs-lookup"><span data-stu-id="ffab6-139">Sockets</span></span>](sockets.md)
