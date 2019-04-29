---
title: Włączanie i wyłączanie protokołu IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 73dee0cb57674c8a2fa4ba2246162870ab1e3a10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643104"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="47b9d-102">Włączanie i wyłączanie protokołu IPv6</span><span class="sxs-lookup"><span data-stu-id="47b9d-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="47b9d-103">Aby skorzystać z protokołu IPv6, upewnij się, że używasz wersji systemu operacyjnego, który obsługuje protokół IPv6, a następnie upewnij się, że system operacyjny i klasy sieciowe są poprawnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="47b9d-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="47b9d-104">Kroki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="47b9d-104">Configuration Steps</span></span>  
 <span data-ttu-id="47b9d-105">W poniższej tabeli wymieniono różne konfiguracje</span><span class="sxs-lookup"><span data-stu-id="47b9d-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="47b9d-106">System operacyjny jest włączony protokół IPv6?</span><span class="sxs-lookup"><span data-stu-id="47b9d-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="47b9d-107">Sieć klasy włączony protokół IPv6?</span><span class="sxs-lookup"><span data-stu-id="47b9d-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="47b9d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="47b9d-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="47b9d-109">Nie</span><span class="sxs-lookup"><span data-stu-id="47b9d-109">No</span></span>|<span data-ttu-id="47b9d-110">Nie</span><span class="sxs-lookup"><span data-stu-id="47b9d-110">No</span></span>|<span data-ttu-id="47b9d-111">Można analizować adresów IPv6.</span><span class="sxs-lookup"><span data-stu-id="47b9d-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="47b9d-112">Nie</span><span class="sxs-lookup"><span data-stu-id="47b9d-112">No</span></span>|<span data-ttu-id="47b9d-113">Tak</span><span class="sxs-lookup"><span data-stu-id="47b9d-113">Yes</span></span>|<span data-ttu-id="47b9d-114">Można analizować adresów IPv6.</span><span class="sxs-lookup"><span data-stu-id="47b9d-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="47b9d-115">Tak</span><span class="sxs-lookup"><span data-stu-id="47b9d-115">Yes</span></span>|<span data-ttu-id="47b9d-116">Nie</span><span class="sxs-lookup"><span data-stu-id="47b9d-116">No</span></span>|<span data-ttu-id="47b9d-117">Można przeanalizować adresy IPv6 i rozpoznać adresów IPv6 za pomocą metody rozpoznawania nazw, nie oznaczony jako przestarzały.</span><span class="sxs-lookup"><span data-stu-id="47b9d-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="47b9d-118">Tak</span><span class="sxs-lookup"><span data-stu-id="47b9d-118">Yes</span></span>|<span data-ttu-id="47b9d-119">Tak</span><span class="sxs-lookup"><span data-stu-id="47b9d-119">Yes</span></span>|<span data-ttu-id="47b9d-120">Można przeanalizować i rozpoznać adresów IPv6 za pomocą wszystkich metod, łącznie z tymi oznaczony jako przestarzały.</span><span class="sxs-lookup"><span data-stu-id="47b9d-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="47b9d-121">Należy pamiętać, że aby włączyć obsługę protokołu IPv6 dla wszystkich klas w przestrzeni nazw System.Net, należy zmodyfikować plik konfiguracji komputera lub w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47b9d-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="47b9d-122">Plik konfiguracyjny aplikacji ma priorytet nad plikiem konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="47b9d-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="47b9d-123">Aby uzyskać przykład sposobu modyfikowania pliku konfiguracji komputera *machine.config*, aby włączyć Ipv6 pomocy technicznej, zobacz temat [jak: Zmodyfikuj plik konfiguracji komputera, aby włączyć obsługę protokołu Ipv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="47b9d-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="47b9d-124">Ponadto upewnij się, że włączono obsługę protokołu IPv6, systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="47b9d-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="47b9d-125">.NET Framework ma przełącznik konfiguracji ustawione w pliku konfiguracji w następujący sposób</span><span class="sxs-lookup"><span data-stu-id="47b9d-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
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
  
 <span data-ttu-id="47b9d-126">Dla programu .NET Framework w wersji 1.1 i starszych wartość **włączony protokół ipv6** konfiguracji przełącznik określa czy członkowie <xref:System.Net.Dns?displayProperty=nameWithType> klasy zwracać adresów IPv6.</span><span class="sxs-lookup"><span data-stu-id="47b9d-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="47b9d-127">Dla programu .NET Framework w wersji 2.0 lub nowszej, jeśli Windows obsługuje protokół IPv6, a następnie elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy, (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), będzie zwracać adresów IPv6 z jednym z ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="47b9d-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="47b9d-128">Przestarzali członkowie DNS <xref:System.Net.Dns?displayProperty=nameWithType> (na przykład <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) odczytuje i rozpoznać wartości w pliku konfiguracji dla ustawienia włączony protokół ipv6.</span><span class="sxs-lookup"><span data-stu-id="47b9d-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b9d-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47b9d-129">See also</span></span>

- [<span data-ttu-id="47b9d-130">Protokół IPv6</span><span class="sxs-lookup"><span data-stu-id="47b9d-130">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [<span data-ttu-id="47b9d-131">Gniazda</span><span class="sxs-lookup"><span data-stu-id="47b9d-131">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
- [<span data-ttu-id="47b9d-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="47b9d-132">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="47b9d-133">\<Protokół IPv6 >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="47b9d-133">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
