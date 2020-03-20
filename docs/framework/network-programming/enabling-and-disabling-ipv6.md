---
title: Włączanie i wyłączanie protokołu IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048560"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="3e25b-102">Włączanie i wyłączanie protokołu IPv6</span><span class="sxs-lookup"><span data-stu-id="3e25b-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="3e25b-103">Aby użyć protokołu IPv6, upewnij się, że używasz wersji systemu operacyjnego obsługującego protokół IPv6 i upewnij się, że system operacyjny i klasy sieciowe są poprawnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="3e25b-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="3e25b-104">Kroki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3e25b-104">Configuration Steps</span></span>  
 <span data-ttu-id="3e25b-105">W poniższej tabeli wymieniono różne konfiguracje</span><span class="sxs-lookup"><span data-stu-id="3e25b-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="3e25b-106">System operacyjny IPv6 włączone?</span><span class="sxs-lookup"><span data-stu-id="3e25b-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="3e25b-107">Klasy sieciowe z włączoną funkcją IPv6?</span><span class="sxs-lookup"><span data-stu-id="3e25b-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="3e25b-108">Opis</span><span class="sxs-lookup"><span data-stu-id="3e25b-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="3e25b-109">Nie</span><span class="sxs-lookup"><span data-stu-id="3e25b-109">No</span></span>|<span data-ttu-id="3e25b-110">Nie</span><span class="sxs-lookup"><span data-stu-id="3e25b-110">No</span></span>|<span data-ttu-id="3e25b-111">Można przeanalizować adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="3e25b-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="3e25b-112">Nie</span><span class="sxs-lookup"><span data-stu-id="3e25b-112">No</span></span>|<span data-ttu-id="3e25b-113">Tak</span><span class="sxs-lookup"><span data-stu-id="3e25b-113">Yes</span></span>|<span data-ttu-id="3e25b-114">Można przeanalizować adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="3e25b-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="3e25b-115">Tak</span><span class="sxs-lookup"><span data-stu-id="3e25b-115">Yes</span></span>|<span data-ttu-id="3e25b-116">Nie</span><span class="sxs-lookup"><span data-stu-id="3e25b-116">No</span></span>|<span data-ttu-id="3e25b-117">Można przeanalizować adresy IPv6 i rozpoznać adresy IPv6 przy użyciu metod rozpoznawania nazw, które nie są oznaczone jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="3e25b-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="3e25b-118">Tak</span><span class="sxs-lookup"><span data-stu-id="3e25b-118">Yes</span></span>|<span data-ttu-id="3e25b-119">Tak</span><span class="sxs-lookup"><span data-stu-id="3e25b-119">Yes</span></span>|<span data-ttu-id="3e25b-120">Można przeanalizować i rozpoznać adresy IPv6 przy użyciu wszystkich metod, w tym te oznaczone przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="3e25b-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="3e25b-121">Należy pamiętać, że aby włączyć obsługę IPv6 dla wszystkich klas w System.Net obszarze nazw, należy zmodyfikować plik konfiguracji komputera lub plik konfiguracyjny dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e25b-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="3e25b-122">Plik konfiguracyjny aplikacji ma pierwszeństwo przed plikiem konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="3e25b-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="3e25b-123">Na przykład jak zmodyfikować plik konfiguracyjny komputera, *machine.config*, aby włączyć obsługę Protokołu Ipv6 zobacz, [Jak: Zmodyfikować plik konfiguracyjny komputera, aby włączyć obsługę Protokołu Ipv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="3e25b-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="3e25b-124">Upewnij się również, że obsługa IPv6 jest włączona dla systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="3e25b-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="3e25b-125">Program .NET Framework ma przełącznik konfiguracji ustawiony w pliku konfiguracyjnym w następujący sposób</span><span class="sxs-lookup"><span data-stu-id="3e25b-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 <span data-ttu-id="3e25b-126">W przypadku programu .NET Framework w wersji 1.1 i wcześniejszych wartość przełącznika <xref:System.Net.Dns?displayProperty=nameWithType> konfiguracji **obsługującego protokół ipv6** określa, czy członkowie klasy zwracają adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="3e25b-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="3e25b-127">W przypadku programu .NET Framework w wersji 2.0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, członkowie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda) zwracają adresy IPv6 z jednym ograniczeniem.</span><span class="sxs-lookup"><span data-stu-id="3e25b-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="3e25b-128">Przestarzałe <xref:System.Net.Dns?displayProperty=nameWithType> elementy członkowskie systemu <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> DNS (na przykład metoda) odczytują i rozpoznają wartość w pliku konfiguracyjnym dla ustawienia obsługującego protokół ipv6.</span><span class="sxs-lookup"><span data-stu-id="3e25b-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e25b-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e25b-129">See also</span></span>

- [<span data-ttu-id="3e25b-130">Protokół internetowy w wersji 6</span><span class="sxs-lookup"><span data-stu-id="3e25b-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="3e25b-131">Gniazda</span><span class="sxs-lookup"><span data-stu-id="3e25b-131">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="3e25b-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="3e25b-132">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="3e25b-133">\<element> ipv6 (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="3e25b-133">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
