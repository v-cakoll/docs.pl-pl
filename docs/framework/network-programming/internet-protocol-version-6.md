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
ms.openlocfilehash: 367db4fa4e585d6066009dbd1afacb154829319a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047880"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="f763a-102">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="f763a-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="f763a-103">Protokół internetowy w wersji 6 (IPv6) to nowy zestaw standardowych protokołów dla warstwy sieciowej Internetu.</span><span class="sxs-lookup"><span data-stu-id="f763a-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="f763a-104">Protokół IPv6 został zaprojektowany w celu rozwiązania wielu problemów bieżącej wersji pakietu protokołu internetowego (znanego jako IPv4) w odniesieniu do wyczerpania adresów, zabezpieczeń, automatycznej konfiguracji, rozszerzalności i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="f763a-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="f763a-105">IPv6 rozszerza możliwości Internetu, aby włączyć nowe rodzaje aplikacji, w tym aplikacje peer-to-peer i mobilne.</span><span class="sxs-lookup"><span data-stu-id="f763a-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="f763a-106">Poniżej przedstawiono główne problemy bieżącego protokołu IPv4:</span><span class="sxs-lookup"><span data-stu-id="f763a-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="f763a-107">Szybkie wyczerpywanie się przestrzeni adresowej.</span><span class="sxs-lookup"><span data-stu-id="f763a-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="f763a-108">Doprowadziło to do użycia translatorów adresów sieciowych (NAT), które mapują wiele adresów prywatnych na jeden publiczny adres IP.</span><span class="sxs-lookup"><span data-stu-id="f763a-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="f763a-109">Główne problemy spowodowane przez ten mechanizm są przetwarzanie narzutów i brak łączności end-to-end.</span><span class="sxs-lookup"><span data-stu-id="f763a-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="f763a-110">Brak wsparcia hierarchii.</span><span class="sxs-lookup"><span data-stu-id="f763a-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="f763a-111">Ze względu na jego nieodłączne wstępnie zdefiniowane organizacji klasy IPv4 brakuje prawdziwej obsługi hierarchicznej.</span><span class="sxs-lookup"><span data-stu-id="f763a-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="f763a-112">Nie można uporządkować adresów IP w sposób, który naprawdę mapuje topologię sieci.</span><span class="sxs-lookup"><span data-stu-id="f763a-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="f763a-113">Ta kluczowa wada projektowa powoduje konieczność dostarczania pakietów IPv4 do dowolnej lokalizacji w Internecie przez duże tabele routingu.</span><span class="sxs-lookup"><span data-stu-id="f763a-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="f763a-114">Złożona konfiguracja sieci.</span><span class="sxs-lookup"><span data-stu-id="f763a-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="f763a-115">W przypadku protokołu IPv4 adresy muszą być przypisywane statycznie lub przy użyciu protokołu konfiguracyjnego, takiego jak DHCP.</span><span class="sxs-lookup"><span data-stu-id="f763a-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="f763a-116">W idealnej sytuacji hosty nie musiałyby polegać na administrowaniu infrastrukturą DHCP.</span><span class="sxs-lookup"><span data-stu-id="f763a-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="f763a-117">Zamiast tego będą mogli skonfigurować się na podstawie segmentu sieci, w którym się znajdują.</span><span class="sxs-lookup"><span data-stu-id="f763a-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="f763a-118">Brak wbudowanego uwierzytelniania i poufności.</span><span class="sxs-lookup"><span data-stu-id="f763a-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="f763a-119">IPv4 nie wymaga obsługi żadnego mechanizmu, który zapewnia uwierzytelnianie lub szyfrowanie wymienianych danych.</span><span class="sxs-lookup"><span data-stu-id="f763a-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="f763a-120">To się zmienia w IPv6.</span><span class="sxs-lookup"><span data-stu-id="f763a-120">This changes with IPv6.</span></span> <span data-ttu-id="f763a-121">Zabezpieczenia protokołu INTERNETOWEGO (IPSec) to wymóg obsługi protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="f763a-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="f763a-122">Nowy pakiet protokołów musi spełniać następujące podstawowe wymagania:</span><span class="sxs-lookup"><span data-stu-id="f763a-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="f763a-123">Routing na dużą skalę i adresowanie z niskim obciążeniem.</span><span class="sxs-lookup"><span data-stu-id="f763a-123">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="f763a-124">Automatyczna konfiguracja dla różnych sytuacji łączenia.</span><span class="sxs-lookup"><span data-stu-id="f763a-124">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="f763a-125">Wbudowane uwierzytelnianie i poufność.</span><span class="sxs-lookup"><span data-stu-id="f763a-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="f763a-126">Aby uzyskać więcej informacji, zobacz [Adresowanie IPv6](ipv6-addressing.md), [Routing IPv6,](ipv6-routing.md) [Automatyczna konfiguracja IPv6](ipv6-auto-configuration.md), [Włączanie i wyłączanie IPv6](enabling-and-disabling-ipv6.md)oraz [Jak: Modyfikowanie pliku konfiguracyjnego komputera w celu włączenia obsługi IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="f763a-126">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="f763a-127">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="f763a-127">References</span></span>  
 <span data-ttu-id="f763a-128">Poniżej znajdują się wybrane dokumenty RFC, które można znaleźć w witrynie internetowej [Internet Engineering Task Force (IETF):](https://www.ietf.org/)</span><span class="sxs-lookup"><span data-stu-id="f763a-128">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="f763a-129">RFC 1287, Ku przyszłości Architektura Internetu.</span><span class="sxs-lookup"><span data-stu-id="f763a-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="f763a-130">RFC 1454, Porównanie propozycji dla następnej wersji IP.</span><span class="sxs-lookup"><span data-stu-id="f763a-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="f763a-131">RFC 2373, architektura adresowania IP w wersji 6.</span><span class="sxs-lookup"><span data-stu-id="f763a-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="f763a-132">RFC 2374 — agregowany globalny format emisji pojedynczej IPv6.</span><span class="sxs-lookup"><span data-stu-id="f763a-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="f763a-133">Informacje związane z protokółem IPv6 można również znaleźć na [stronie IP w wersji 6 (IPv6).](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29)</span><span class="sxs-lookup"><span data-stu-id="f763a-133">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f763a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f763a-134">See also</span></span>

- [<span data-ttu-id="f763a-135">Przykład gniazd IPv6</span><span class="sxs-lookup"><span data-stu-id="f763a-135">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="f763a-136">Przykłady programowania sieciowego</span><span class="sxs-lookup"><span data-stu-id="f763a-136">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="f763a-137">Gniazda</span><span class="sxs-lookup"><span data-stu-id="f763a-137">Sockets</span></span>](sockets.md)
