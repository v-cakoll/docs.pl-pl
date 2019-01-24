---
title: 'Instrukcje: Zmodyfikuj plik konfiguracji komputera, aby włączyć obsługę protokołu IPv6'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 8427a1641b4d6c782f2b2585ab49d38073567f2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698079"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="f4b35-102">Instrukcje: Zmodyfikuj plik konfiguracji komputera, aby włączyć obsługę protokołu IPv6</span><span class="sxs-lookup"><span data-stu-id="f4b35-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="f4b35-103">Poniższy przykład kodu pokazuje, jak zmodyfikować plik konfiguracji komputera, *machine.config*, aby włączyć obsługę protokołu IPv6.</span><span class="sxs-lookup"><span data-stu-id="f4b35-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="f4b35-104">*Machine.config* plik jest przechowywany w *%Windir%\Microsoft.NET\Framework* folder w katalogu, w którym zainstalowano Windows.</span><span class="sxs-lookup"><span data-stu-id="f4b35-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="f4b35-105">Ma osobnej *machine.config* plików w folderach w ramach *%Windir%\Microsoft.NET\Framework* dla każdej wersji programu .NET Framework zainstalowanej na komputerze (na przykład *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="f4b35-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="f4b35-106">Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.</span><span class="sxs-lookup"><span data-stu-id="f4b35-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="f4b35-107">Dla programu .NET Framework w wersji 1.1 i starszych wartość **włączony protokół ipv6** konfiguracji przełącznik określa czy członkowie <xref:System.Net.Dns?displayProperty=nameWithType> klasy zwracać adresów IPv6.</span><span class="sxs-lookup"><span data-stu-id="f4b35-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="f4b35-108">Dla programu .NET Framework w wersji 2.0 lub nowszej, jeśli Windows obsługuje protokół IPv6, a następnie wszystkie elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), będzie zwracać adresów IPv6 z jednym z ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="f4b35-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="f4b35-109">Przestarzali członkowie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) odczytuje i rozpoznać wartości w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f4b35-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4b35-110">.NET Framework w wersji 2.0 lub nowszej domyślnie był włączony protokół IPv6.</span><span class="sxs-lookup"><span data-stu-id="f4b35-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="f4b35-111">Dla programu .NET Framework w wersji 1.1 i starsze wersje protokołu IPv6 jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="f4b35-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4b35-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4b35-112">Example</span></span>  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4b35-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4b35-113">See also</span></span>
- [<span data-ttu-id="f4b35-114">Adresowanie IPv6</span><span class="sxs-lookup"><span data-stu-id="f4b35-114">IPv6 Addressing</span></span>](../../../docs/framework/network-programming/ipv6-addressing.md)
- [<span data-ttu-id="f4b35-115">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f4b35-115">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="f4b35-116">\<Protokół IPv6 >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="f4b35-116">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
