---
title: 'Instrukcje: modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: af6eb8a334108c988967a555024b524e27d40f58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959077"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Instrukcje: modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6
Poniższy przykład kodu pokazuje, jak zmodyfikować plik konfiguracji komputera, *Machine. config*, aby umożliwić obsługę protokołu IPv6. Plik *Machine. config* jest przechowywany w folderze *%windir%\Microsoft.NET\Framework* w katalogu, w którym zainstalowano system Windows. W folderach w obszarze *%windir%\Microsoft.NET\Framework* istnieje osobny plik *Machine. config* dla każdej wersji .NET Framework zainstalowanej na komputerze (na przykład *C:\Windows\Microsoft.NET\Framework\v2.0.50727\ Machine. config*).  
  
 Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.  
  
 W przypadku .NET Framework w wersji 1,1 i wcześniejszych wartość przełącznika konfiguracja **obsługująca protokół IPv6** określa, czy elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy zwracają adresy IPv6.  
  
 W przypadku .NET Framework w wersji 2,0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, wszystkie <xref:System.Net.Dns?displayProperty=nameWithType> elementy członkowskie klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) będą zwracały adresy IPv6 z jednym ograniczeniem. Przestarzałe elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) odczytają i rozpoznają wartość w pliku konfiguracji.  
  
> [!NOTE]
> W przypadku .NET Framework w wersji 2,0 lub nowszej protokół IPv6 jest domyślnie włączony. W przypadku .NET Framework w wersji 1,1 lub starszej protokół IPv6 jest domyślnie wyłączony.  
  
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
<system.net>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Adresowanie IPv6](../../../docs/framework/network-programming/ipv6-addressing.md)
- [Schemat ustawień sieci](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [\<> IPv6, element (Ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
