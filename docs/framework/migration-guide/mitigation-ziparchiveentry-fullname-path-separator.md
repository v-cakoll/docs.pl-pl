---
title: Środki zaradcze ZipArchiveEntry.FullName Path Separator
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b97436ca2f81fea139689c7c2c2348718827b90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778866"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Środki zaradcze ZipArchiveEntry.FullName Path Separator
Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1, separator ścieżki używany we <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwości został zmieniony od ukośnika odwrotnego (\\"") użytego w poprzednich wersjach .NET Framework do ukośnika ("/").   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType>obiekty są tworzone przez wywołanie jednego z przeciążeń <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.  
  
## <a name="impact"></a>Wpływ  
 Zmiana powoduje, że implementacja platformy .NET jest zgodna z sekcją 4.4.17.1 [. Specyfikacja formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i zezwala na to. Archiwa ZIP do skompresowania w systemach innych niż Windows.  
  
 Dekompresowanie pliku zip utworzonego przez aplikację, która jest przeznaczona dla starszej wersji .NET Framework w systemach operacyjnych innych niż Windows, takich jak Macintosh, nie można zachować struktury katalogów. Na przykład w systemie Macintosh tworzy zestaw plików, których nazwa pliku łączy ścieżkę katalogu, wraz z dowolnym znakiem ukośnika odwrotnego ("\\") i nazwą pliku. W związku z tym struktura katalogów nieskompresowanych plików nie jest zachowywana.  
  
 Wpływ tej zmiany na. Pliki zip, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w przestrzeni <xref:System.IO> nazw .NET Framework powinny być minimalne, ponieważ te interfejsy API mogą bezproblemowo obsługiwać ukośnik ("/") lub ukośnik odwrotny (\\"") jako znak separatora ścieżki.  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli takie zachowanie jest niepożądane, można zrezygnować z dodania ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji. Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i przełącznik rezygnacji.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 i nowszych wersjach, mogą zrezygnować z tego zachowania poprzez dodanie ustawienia konfiguracji do [ \<sekcji > środowiska uruchomieniowego](../configure-apps/file-schema/runtime/runtime-element.md) aplikacji plik konfiguracji. Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i przełącznik zgody.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6-1.md)
- [Zgodność aplikacji w 4.6.1](application-compatibility-in-the-net-framework-4-6-1.md)
