---
title: Włączanie i wyłączanie protokołu IPv6
description: Wykonaj te czynności konfiguracyjne, aby włączyć protokół IPv6, w tym modyfikując plik konfiguracji komputera lub aplikacji.
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 7729647b09df20a98d5d639a641cb0a31f557330
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502616"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="cd8aa-103">Włączanie i wyłączanie protokołu IPv6</span><span class="sxs-lookup"><span data-stu-id="cd8aa-103">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="cd8aa-104">Aby korzystać z protokołu IPv6, należy się upewnić, że uruchomiono wersję systemu operacyjnego, która obsługuje protokół IPv6, i upewnić się, że system operacyjny i klasy sieciowe są prawidłowo skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-104">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="cd8aa-105">Kroki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cd8aa-105">Configuration Steps</span></span>  
 <span data-ttu-id="cd8aa-106">W poniższej tabeli wymieniono różne konfiguracje</span><span class="sxs-lookup"><span data-stu-id="cd8aa-106">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="cd8aa-107">System operacyjny IPv6 — włączony?</span><span class="sxs-lookup"><span data-stu-id="cd8aa-107">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="cd8aa-108">Czy są włączone klasy sieci IPv6?</span><span class="sxs-lookup"><span data-stu-id="cd8aa-108">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="cd8aa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="cd8aa-109">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="cd8aa-110">Nie</span><span class="sxs-lookup"><span data-stu-id="cd8aa-110">No</span></span>|<span data-ttu-id="cd8aa-111">Nie</span><span class="sxs-lookup"><span data-stu-id="cd8aa-111">No</span></span>|<span data-ttu-id="cd8aa-112">Może analizować adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-112">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="cd8aa-113">Nie</span><span class="sxs-lookup"><span data-stu-id="cd8aa-113">No</span></span>|<span data-ttu-id="cd8aa-114">Yes</span><span class="sxs-lookup"><span data-stu-id="cd8aa-114">Yes</span></span>|<span data-ttu-id="cd8aa-115">Może analizować adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-115">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="cd8aa-116">Yes</span><span class="sxs-lookup"><span data-stu-id="cd8aa-116">Yes</span></span>|<span data-ttu-id="cd8aa-117">Nie</span><span class="sxs-lookup"><span data-stu-id="cd8aa-117">No</span></span>|<span data-ttu-id="cd8aa-118">Może analizować adresy IPv6 i rozwiązywać adresy IPv6 przy użyciu metod rozpoznawania nazw nieoznaczonych jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-118">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="cd8aa-119">Tak</span><span class="sxs-lookup"><span data-stu-id="cd8aa-119">Yes</span></span>|<span data-ttu-id="cd8aa-120">Tak</span><span class="sxs-lookup"><span data-stu-id="cd8aa-120">Yes</span></span>|<span data-ttu-id="cd8aa-121">Można analizować i rozwiązywać adresy IPv6 przy użyciu wszystkich metod, w tym tych, które zostały oznaczone jako przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-121">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="cd8aa-122">Należy pamiętać, że aby włączyć obsługę protokołu IPv6 dla wszystkich klas w przestrzeni nazw System.Net, należy zmodyfikować plik konfiguracji komputera lub plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-122">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="cd8aa-123">Plik konfiguracyjny aplikacji ma pierwszeństwo przed plikiem konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-123">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="cd8aa-124">Aby zapoznać się z przykładem sposobu modyfikowania pliku konfiguracji komputera, *Machine. config*w celu włączenia obsługi protokołu IPv6, zobacz [: Modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="cd8aa-124">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="cd8aa-125">Upewnij się również, że obsługa protokołu IPv6 jest włączona dla systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-125">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="cd8aa-126">.NET Framework ma ustawiony przełącznik konfiguracji w pliku konfiguracji w następujący sposób</span><span class="sxs-lookup"><span data-stu-id="cd8aa-126">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
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
  
 <span data-ttu-id="cd8aa-127">W przypadku .NET Framework w wersji 1,1 i wcześniejszych wartość przełącznika konfiguracja **obsługująca protokół IPv6** określa, czy elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy zwracają adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-127">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="cd8aa-128">W przypadku .NET Framework w wersji 2,0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, wówczas elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) będą zwracały adresy IPv6 z jednym ograniczeniem.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-128">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="cd8aa-129">Przestarzałe elementy członkowskie DNS <xref:System.Net.Dns?displayProperty=nameWithType> (na przykład <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) odczytają i rozpoznają wartość w pliku konfiguracyjnym dla ustawienia włączony protokół IPv6.</span><span class="sxs-lookup"><span data-stu-id="cd8aa-129">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd8aa-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd8aa-130">See also</span></span>

- [<span data-ttu-id="cd8aa-131">Protokół internetowy w wersji 6</span><span class="sxs-lookup"><span data-stu-id="cd8aa-131">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="cd8aa-132">Gniazda</span><span class="sxs-lookup"><span data-stu-id="cd8aa-132">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="cd8aa-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="cd8aa-133">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="cd8aa-134">\<ipv6>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="cd8aa-134">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
