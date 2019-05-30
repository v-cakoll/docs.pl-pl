---
title: 'Środki zaradcze: ZipArchiveEntry.FullName Path Separator'
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
ms.openlocfilehash: 908ac7c441dbb7f6c70b9fafc701d403fc153222
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251075"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Środki zaradcze: ZipArchiveEntry.FullName Path Separator
Począwszy od aplikacji przeznaczonych dla platformy .NET Framework 4.6.1 separatora ścieżki używany w <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> właściwość zmienił się od ukośnika ("\\") używane w poprzednich wersjach programu .NET Framework w celu ukośnika ("/").   <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> obiekty są tworzone przez wywołanie metody jednego z przeciążeń <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> metody.  
  
## <a name="impact"></a>Wpływ  
 Zmiana zapewnia implementacji .NET do zgodności z sekcji 4.4.17.1 [. Specyfikacja formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i umożliwia. Archiwa ZIP można dekompresja w systemach innych niż Windows.  
  
 Podczas dekompresowania pliku zip, utworzone przez aplikację przeznaczonego poprzedniej wersji programu .NET Framework w systemach operacyjnych innych niż Windows, takich jak Macintosh nie powiedzie się, aby zachować strukturę katalogów. Na przykład w przypadku komputerów Macintosh tworzy zbiór plików, których nazwy łączy ścieżki katalogu, wraz z dowolnym ukośnika odwrotnego ("\\") znaki i nazwę pliku. W rezultacie struktura katalogów zdekompresowanych plików nie są zachowywane.  
  
 Wpływ tej zmiany na. Pliki ZIP, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w programie .NET Framework <xref:System.IO> przestrzenią nazw powinna być minimalny, ponieważ te interfejsy API bezproblemowo może obsługiwać ukośnika ("/") lub ukośnika odwrotnego ("\\") jako znaku separatora ścieżki.  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli to zachowanie jest niepożądany, można zrezygnować z przez dodanie ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku konfiguracji aplikacji. Poniżej pokazano oba `<runtime>` sekcji i przełącznik zgody.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ponadto aplikacje poprzedniej wersji programu .NET Framework, które są uruchomione w programie .NET Framework 4.6.1 i nowszych wersjach zgodzić się na to zachowanie przez dodanie ustawienia konfiguracji do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcja pliku konfiguracji aplikacji. Poniżej pokazano oba `<runtime>` sekcji i przełącznik opcjonalna.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
- [Zgodność aplikacji w wersji 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
