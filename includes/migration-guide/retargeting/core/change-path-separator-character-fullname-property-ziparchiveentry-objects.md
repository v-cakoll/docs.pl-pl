---
ms.openlocfilehash: f87d0dbeda6094bd745f5b580772b1161f30d0d5
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86218078"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a>Zmień znak separatora ścieżki w właściwości FullName obiektów klasy ZipArchiveEntry

#### <a name="details"></a>Szczegóły

W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.6.1 i nowszych wersji, znak separatora ścieżki został zmieniony z ukośnika odwrotnego (" \\ ") na ukośnik ("/") we <xref:System.IO.Compression.ZipArchiveEntry.FullName> właściwości <xref:System.IO.Compression.ZipArchiveEntry> obiektów utworzonych przez przeciążenia <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> metody. Zmiana powoduje, że implementacja platformy .NET jest zgodna z sekcją 4.4.17.1 [. Specyfikacja formatu pliku ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) i zezwala na to. Archiwa ZIP do skompresowania w systemach innych niż Windows.<br />Dekompresowanie pliku zip utworzonego przez aplikację, która jest przeznaczona dla starszej wersji .NET Framework w systemach operacyjnych innych niż Windows, takich jak Macintosh, nie można zachować struktury katalogów. Na przykład w systemie Macintosh tworzy zestaw plików, których nazwa pliku łączy ścieżkę katalogu, wraz z dowolnym znakiem ukośnika odwrotnego (" \\ ") i nazwą pliku. W związku z tym struktura katalogów nieskompresowanych plików nie jest zachowywana.

#### <a name="suggestion"></a>Sugestia

Wpływ tej zmiany na. Pliki ZIP, które są dekompresowane w systemie operacyjnym Windows przez interfejsy API w <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw .NET Framework powinny być minimalne, ponieważ te interfejsy API mogą bezproblemowo obsługiwać ukośnik ("/") lub ukośnik odwrotny (" \\ ") jako znak separatora ścieżki.<br />Jeśli ta zmiana jest niepożądana, można zrezygnować z jej przez dodanie ustawienia konfiguracji do [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji. Poniższy przykład pokazuje `<runtime>` sekcję i `Switch.System.IO.Compression.ZipFile.UseBackslash` przełącznik rezygnacji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

Ponadto aplikacje, które są przeznaczone dla poprzednich wersji .NET Framework ale działają w .NET Framework 4.6.1 i nowszych wersjach, mogą zrezygnować z tego zachowania przez dodanie ustawienia konfiguracji do [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracyjnego aplikacji. Poniżej przedstawiono zarówno `<runtime>` sekcję, jak i `Switch.System.IO.Compression.ZipFile.UseBackslash` przełącznik zgody.

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Edge        |
| Wersja | 4.6.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
