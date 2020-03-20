---
title: 'Instrukcje: modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 73408afe9fcb35daa898c08b087a3411a6cb342b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180805"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="0a83a-102">Instrukcje: modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6</span><span class="sxs-lookup"><span data-stu-id="0a83a-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="0a83a-103">W poniższym przykładzie kodu pokazano, jak zmodyfikować plik konfiguracji komputera, *machine.config*, aby włączyć obsługę IPv6.</span><span class="sxs-lookup"><span data-stu-id="0a83a-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="0a83a-104">Plik *machine.config* jest przechowywany w folderze *%Windir%\Microsoft.NET\Framework* w katalogu, w którym zainstalowano system Windows.</span><span class="sxs-lookup"><span data-stu-id="0a83a-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="0a83a-105">W folderach w obszarze *%Windir%\Microsoft.NET\Framework* znajduje się oddzielny plik *machine.config* dla każdej wersji programu .NET Framework zainstalowanej na komputerze (na przykład *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="0a83a-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="0a83a-106">Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="0a83a-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="0a83a-107">W przypadku programu .NET Framework w wersji 1.1 i wcześniejszych wartość przełącznika <xref:System.Net.Dns?displayProperty=nameWithType> konfiguracji **obsługującego protokół ipv6** określa, czy członkowie klasy zwracają adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="0a83a-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="0a83a-108">W przypadku programu .NET Framework w wersji 2.0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, wszyscy członkowie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda) zwracają adresy IPv6 z jednym ograniczeniem.</span><span class="sxs-lookup"><span data-stu-id="0a83a-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="0a83a-109">Przestarzałe <xref:System.Net.Dns?displayProperty=nameWithType> elementy członkowskie klasy <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> (na przykład metoda) będą odczytywać i rozpoznawać wartość w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="0a83a-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a83a-110">W przypadku programu .NET Framework w wersji 2.0 i nowszej protokół IPv6 jest domyślnie włączony.</span><span class="sxs-lookup"><span data-stu-id="0a83a-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="0a83a-111">W przypadku programu .NET Framework w wersji 1.1 i wcześniejszych domyślnie jest wyłączona iPv6.</span><span class="sxs-lookup"><span data-stu-id="0a83a-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a83a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a83a-112">Example</span></span>  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>
    ……………  
    </settings>  
    ………………  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a83a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a83a-113">See also</span></span>

- [<span data-ttu-id="0a83a-114">Adresowanie IPv6</span><span class="sxs-lookup"><span data-stu-id="0a83a-114">IPv6 Addressing</span></span>](ipv6-addressing.md)
- [<span data-ttu-id="0a83a-115">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="0a83a-115">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="0a83a-116">\<element> ipv6 (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="0a83a-116">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
