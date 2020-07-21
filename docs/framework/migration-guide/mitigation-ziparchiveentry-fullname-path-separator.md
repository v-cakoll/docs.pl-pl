---
title: 'Środki zaradcze: separator ścieżki klasy ZipArchiveEntry. FullName'
description: Dowiedz się, w jaki sposób separator ścieżki dla właściwości ZipArchiveEntry. FullName został zmieniony, rozpoczynając od aplikacji, które są przeznaczone dla .NET Framework 4.6.1.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 8cd6362038ce0548681f3d3b44724f3ef9ff62cb
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475297"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Środki zaradcze: separator ścieżki klasy ZipArchiveEntry. FullName

Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1, separator ścieżki używany we <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> Właściwości został zmieniony z ukośnika odwrotnego (" \\ ") użytego w poprzednich wersjach .NET Framework do ukośnika ("/"). <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>obiekty są tworzone przez wywołanie jednego z przeciążeń <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.  
  
## <a name="impact"></a>Wpływ  
 Zmiana powoduje, że implementacja platformy .NET jest zgodna z sekcją 4.4.17.1 [. Specyfikacja formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i zezwala na to. Archiwa ZIP do skompresowania w systemach innych niż Windows.  
  
 Dekompresowanie pliku zip utworzonego przez aplikację, która jest przeznaczona dla starszej wersji .NET Framework w systemach operacyjnych innych niż Windows, takich jak MacOS, nie można zachować struktury katalogów. Na przykład w programie MacOS tworzy zestaw plików, których nazwa pliku łączy ścieżkę katalogu, wszystkie znaki ukośnika odwrotnego (" \\ ") i nazwę pliku. W związku z tym struktura katalogów nieskompresowanych plików nie jest zachowywana.  
  
 Wpływ tej zmiany na. Pliki ZIP, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w .NET Framework <xref:System.IO> przestrzeni nazw powinny być minimalne, ponieważ te interfejsy API mogą bezproblemowo obsługiwać ukośnik ("/") lub ukośnik odwrotny (" \\ ") jako znak separatora ścieżki.  
  
## <a name="mitigation"></a>Ograniczanie ryzyka  
 Jeśli takie zachowanie jest niepożądane, można zrezygnować z dodania ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji. Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i przełącznik rezygnacji.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ponadto aplikacje przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 i nowszych wersjach mogą zrezygnować z tego zachowania przez dodanie ustawienia konfiguracji do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji. Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i przełącznik zgody.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zgodność aplikacji](application-compatibility.md)
