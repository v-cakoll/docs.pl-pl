---
title: 'Instrukcje: Modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 98fb57abfff985ab96cb5139f15ae4c29c986a18
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040621"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Instrukcje: Modyfikowanie pliku konfiguracji komputera w celu włączenia obsługi protokołu IPv6
Poniższy przykład kodu pokazuje, jak zmodyfikować plik konfiguracji komputera, *Machine. config*, aby umożliwić obsługę protokołu IPv6. Plik *Machine. config* jest przechowywany w folderze *%windir%\Microsoft.NET\Framework* w katalogu, w którym zainstalowano system Windows. W folderach w obszarze *%windir%\Microsoft.NET\Framework* istnieje osobny plik *Machine. config* dla każdej wersji .NET Framework zainstalowanej na komputerze (na przykład *C:\Windows\Microsoft.NET\Framework\v2.0.50727\ Machine. config*).  
  
 Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.  
  
 W przypadku .NET Framework w wersji 1,1 i wcześniejszych wartość przełącznika konfiguracja **obsługująca protokół IPv6** określa, czy elementy członkowskie klasy <xref:System.Net.Dns?displayProperty=nameWithType> zwracają adresy IPv6.  
  
 W przypadku .NET Framework w wersji 2,0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, wszystkie elementy członkowskie klasy <xref:System.Net.Dns?displayProperty=nameWithType> (na przykład Metoda <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType>) będą zwracać adresy IPv6 z jednym ograniczeniem. Przestarzałe elementy członkowskie klasy <xref:System.Net.Dns?displayProperty=nameWithType> (na przykład Metoda <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType>) odczyta i rozpoznają wartość w pliku konfiguracji.  
  
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
</system.net>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Adresowanie IPv6](ipv6-addressing.md)
- [Schemat ustawień sieci](../configure-apps/file-schema/network/index.md)
- [\<> IPv6, element (Ustawienia sieci)](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
