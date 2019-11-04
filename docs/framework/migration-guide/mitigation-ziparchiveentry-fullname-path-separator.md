---
title: 'Środki zaradcze: separator ścieżki klasy ZipArchiveEntry. FullName'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 021d22e90ba39a4d01cf7d64588fab2d724b6640
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457734"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Środki zaradcze: separator ścieżki klasy ZipArchiveEntry. FullName
Począwszy od aplikacji, które są przeznaczone dla .NET Framework 4.6.1, separator ścieżki używany we właściwości <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> został zmieniony od ukośnika odwrotnego ("\\") użytego w poprzednich wersjach .NET Framework do ukośnika ("/").   obiekty <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> są tworzone przez wywołanie jednego z przeciążeń metody <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.  
  
## <a name="impact"></a>Wpływ  
 Zmiana powoduje, że implementacja platformy .NET jest zgodna z sekcją 4.4.17.1 [. Specyfikacja formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i zezwala na to. Archiwa ZIP do skompresowania w systemach innych niż Windows.  
  
 Dekompresowanie pliku zip utworzonego przez aplikację, która jest przeznaczona dla starszej wersji .NET Framework w systemach operacyjnych innych niż Windows, takich jak Macintosh, nie można zachować struktury katalogów. Na przykład w systemie Macintosh tworzy zestaw plików, których nazwa pliku łączy ścieżkę katalogu, wraz z dowolnym znakiem ukośnika odwrotnego ("\\") i nazwą pliku. W związku z tym struktura katalogów nieskompresowanych plików nie jest zachowywana.  
  
 Wpływ tej zmiany na. Pliki ZIP, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w .NET Framework <xref:System.IO> przestrzeni nazw powinny być minimalne, ponieważ te interfejsy API mogą bezproblemowo obsługiwać ukośnik ("/") lub ukośnik odwrotny ("\\") jako znak separatora ścieżki.  
  
## <a name="mitigation"></a>Ograniczenie  
 Jeśli takie zachowanie jest niepożądane, można zrezygnować z dodania ustawienia konfiguracji do sekcji [> środowiska uruchomieniowego\<](../configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji. Poniżej przedstawiono sekcję `<runtime>` i przełącznik rezygnacji.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 i nowszych wersjach, mogą zrezygnować z tego zachowania przez dodanie ustawienia konfiguracji do sekcji [> środowiska uruchomieniowego\<](../configure-apps/file-schema/runtime/runtime-element.md) aplikacji plik konfiguracji. Poniżej przedstawiono sekcję `<runtime>` i przełącznik zgody.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](retargeting-changes-in-the-net-framework-4-6-1.md)
- [Zgodność aplikacji](application-compatibility.md)
