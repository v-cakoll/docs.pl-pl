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
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Instrukcje: modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6
W poniższym przykładzie kodu pokazano, jak zmodyfikować plik konfiguracji komputera, *machine.config*, aby włączyć obsługę IPv6. Plik *machine.config* jest przechowywany w folderze *%Windir%\Microsoft.NET\Framework* w katalogu, w którym zainstalowano system Windows. W folderach w obszarze *%Windir%\Microsoft.NET\Framework* znajduje się oddzielny plik *machine.config* dla każdej wersji programu .NET Framework zainstalowanej na komputerze (na przykład *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.  
  
 W przypadku programu .NET Framework w wersji 1.1 i wcześniejszych wartość przełącznika <xref:System.Net.Dns?displayProperty=nameWithType> konfiguracji **obsługującego protokół ipv6** określa, czy członkowie klasy zwracają adresy IPv6.  
  
 W przypadku programu .NET Framework w wersji 2.0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, wszyscy członkowie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda) zwracają adresy IPv6 z jednym ograniczeniem. Przestarzałe <xref:System.Net.Dns?displayProperty=nameWithType> elementy członkowskie klasy <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> (na przykład metoda) będą odczytywać i rozpoznawać wartość w pliku konfiguracyjnym.  
  
> [!NOTE]
> W przypadku programu .NET Framework w wersji 2.0 i nowszej protokół IPv6 jest domyślnie włączony. W przypadku programu .NET Framework w wersji 1.1 i wcześniejszych domyślnie jest wyłączona iPv6.  
  
## <a name="example"></a>Przykład  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Adresowanie IPv6](ipv6-addressing.md)
- [Schemat ustawień sieci](../configure-apps/file-schema/network/index.md)
- [\<element> ipv6 (ustawienia sieciowe)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
