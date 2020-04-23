---
title: 'Łagodzenie: ZipArchiveEntry.FullName Separator ścieżki'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 3f6c7f258fd5dbf01db4d79b73b88ddd7484f9b2
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102622"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Łagodzenie: ZipArchiveEntry.FullName Separator ścieżki

Począwszy od aplikacji, które są przeznaczone dla programu .NET Framework 4.6.1, separator ścieżki używany we <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości został zmieniony z ukośnika odwrotnego ("\\") używanego w poprzednich wersjach programu .NET Framework na ukośnik do przodu ("/"). <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>obiekty są tworzone przez wywołanie jednego <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> z przeciążeń metody.  
  
## <a name="impact"></a>Wpływ  
 Zmiana wprowadza implementację platformy .NET w zgodność z sekcją 4.4.17.1 . [ Zip File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i pozwala . Zip archiwów do dekompresji w systemach innych niż Windows.  
  
 Dekompresji pliku zip utworzonego przez aplikację, która jest przeznaczona dla poprzedniej wersji programu .NET Framework w systemach operacyjnych innych niż Windows, takich jak MacOS, nie można zachować struktury katalogów. Na przykład w systemie MacOS tworzy zestaw plików, których nazwa pliku łączy ścieżkę katalogu, wszelkie znaki ukośnika odwrotnego ("\\") i nazwę pliku. W rezultacie struktura katalogów zdekompresowanych plików nie jest zachowywana.  
  
 Wpływ tej zmiany na . Pliki ZIP, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w obszarze nazw programu .NET Framework <xref:System.IO> powinny być minimalne,\\ponieważ te interfejsy API mogą bezproblemowo obsługiwać ukośnik ("/") lub ukośnik odwrotny (" ") jako znak separatora ścieżki.  
  
## <a name="mitigation"></a>Środki zaradcze  
 Jeśli to zachowanie jest niepożądane, można zrezygnować, dodając [ \<](../configure-apps/file-schema/runtime/runtime-element.md) ustawienie konfiguracji do środowiska wykonawczego>sekcji pliku konfiguracji aplikacji. Poniżej przedstawiono `<runtime>` zarówno sekcję, jak i przełącznik rezygnacji.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ponadto aplikacje przeznaczone dla poprzednich wersji programu .NET Framework, ale są uruchomione w programie .NET Framework 4.6.1 i nowszych wersjach, mogą zdecydować się na to zachowanie, dodając ustawienie konfiguracji do sekcji [ \<>środowiska wykonawczego](../configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji. Poniżej przedstawiono `<runtime>` zarówno sekcję, jak i przełącznik opt-in.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
