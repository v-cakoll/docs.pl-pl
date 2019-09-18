---
title: Włączanie i wyłączanie protokołu IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048560"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="c3354-102">Włączanie i wyłączanie protokołu IPv6</span><span class="sxs-lookup"><span data-stu-id="c3354-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="c3354-103">Aby korzystać z protokołu IPv6, należy się upewnić, że uruchomiono wersję systemu operacyjnego, która obsługuje protokół IPv6, i upewnić się, że system operacyjny i klasy sieciowe są prawidłowo skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="c3354-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="c3354-104">Kroki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c3354-104">Configuration Steps</span></span>  
 <span data-ttu-id="c3354-105">W poniższej tabeli wymieniono różne konfiguracje</span><span class="sxs-lookup"><span data-stu-id="c3354-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="c3354-106">System operacyjny IPv6 — włączony?</span><span class="sxs-lookup"><span data-stu-id="c3354-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="c3354-107">Czy są włączone klasy sieci IPv6?</span><span class="sxs-lookup"><span data-stu-id="c3354-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="c3354-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c3354-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="c3354-109">Nie</span><span class="sxs-lookup"><span data-stu-id="c3354-109">No</span></span>|<span data-ttu-id="c3354-110">Nie</span><span class="sxs-lookup"><span data-stu-id="c3354-110">No</span></span>|<span data-ttu-id="c3354-111">Może analizować adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="c3354-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="c3354-112">Nie</span><span class="sxs-lookup"><span data-stu-id="c3354-112">No</span></span>|<span data-ttu-id="c3354-113">Tak</span><span class="sxs-lookup"><span data-stu-id="c3354-113">Yes</span></span>|<span data-ttu-id="c3354-114">Może analizować adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="c3354-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="c3354-115">Tak</span><span class="sxs-lookup"><span data-stu-id="c3354-115">Yes</span></span>|<span data-ttu-id="c3354-116">Nie</span><span class="sxs-lookup"><span data-stu-id="c3354-116">No</span></span>|<span data-ttu-id="c3354-117">Może analizować adresy IPv6 i rozwiązywać adresy IPv6 przy użyciu metod rozpoznawania nazw nieoznaczonych jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="c3354-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="c3354-118">Tak</span><span class="sxs-lookup"><span data-stu-id="c3354-118">Yes</span></span>|<span data-ttu-id="c3354-119">Tak</span><span class="sxs-lookup"><span data-stu-id="c3354-119">Yes</span></span>|<span data-ttu-id="c3354-120">Można analizować i rozwiązywać adresy IPv6 przy użyciu wszystkich metod, w tym tych, które zostały oznaczone jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="c3354-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="c3354-121">Należy pamiętać, że aby włączyć obsługę protokołu IPv6 dla wszystkich klas w przestrzeni nazw System.Net, należy zmodyfikować plik konfiguracji komputera lub plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3354-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="c3354-122">Plik konfiguracyjny aplikacji ma pierwszeństwo przed plikiem konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="c3354-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="c3354-123">Aby zapoznać się z przykładem sposobu modyfikowania pliku konfiguracji komputera, *Machine. config*w celu włączenia obsługi protokołu IPv6, [Zobacz: Zmodyfikuj plik konfiguracji komputera, aby włączyć obsługę](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="c3354-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="c3354-124">Upewnij się również, że obsługa protokołu IPv6 jest włączona dla systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c3354-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="c3354-125">.NET Framework ma ustawiony przełącznik konfiguracji w pliku konfiguracji w następujący sposób</span><span class="sxs-lookup"><span data-stu-id="c3354-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
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
  
 <span data-ttu-id="c3354-126">W przypadku .NET Framework w wersji 1,1 i wcześniejszych wartość przełącznika konfiguracja **obsługująca protokół IPv6** określa, czy elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy zwracają adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="c3354-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="c3354-127">W przypadku .NET Framework w wersji 2,0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, <xref:System.Net.Dns?displayProperty=nameWithType> wówczas elementy członkowskie klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) będą zwracały adresy IPv6 z jednym ograniczeniem.</span><span class="sxs-lookup"><span data-stu-id="c3354-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="c3354-128">Przestarzałe elementy członkowskie DNS <xref:System.Net.Dns?displayProperty=nameWithType> (na przykład <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) odczytają i rozpoznają wartość w pliku konfiguracyjnym dla ustawienia włączony protokół IPv6.</span><span class="sxs-lookup"><span data-stu-id="c3354-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3354-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3354-129">See also</span></span>

- [<span data-ttu-id="c3354-130">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="c3354-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="c3354-131">Gniazda</span><span class="sxs-lookup"><span data-stu-id="c3354-131">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="c3354-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c3354-132">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="c3354-133">\<> IPv6, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="c3354-133">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
