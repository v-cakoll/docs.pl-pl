---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568109"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wejść

Archiwa zip wyświetlają zarówno skompresowany rozmiar, jak i nieskompresowany rozmiar w katalogu centralnym i nagłówku lokalnym.  Dane wpisu również wskazuje jego rozmiar.  W .NET Core 2.2 i wcześniejszych wersjach te wartości nigdy nie zostały sprawdzone pod kątem spójności. Począwszy od .NET Core 3.0, są teraz.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> wcześniejszych wersjach, nawet jeśli nagłówek lokalny nie zgadza się z centralnym nagłówkiem pliku zip. Dane są dekompresowane do momentu osiągnięcia końca skompresowanego strumienia, nawet jeśli jego długość przekracza rozmiar nieskompresowanego pliku wymieniony w centralnym katalogu/nagłówku lokalnym.

Począwszy od .NET Core <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 3.0, metoda sprawdza, czy nagłówek lokalny i nagłówek centralny zgadzają się na skompresowane i nieskompresowane rozmiary wpisu.  Jeśli nie, metoda <xref:System.IO.InvalidDataException> zgłasza, jeśli w lokalnym nagłówku archiwum i/lub rozmiarze listy deskryptora danych, które nie zgadzają się z centralnym katalogiem pliku zip. Podczas odczytywania wpisu dekompresowane dane są obcinane do rozmiaru nieskompresowanego pliku wymienionego w nagłówku.

Ta zmiana została wmazana w celu zapewnienia, że <xref:System.IO.Compression.ZipArchiveEntry> poprawnie reprezentuje rozmiar swoich danych i że tylko ta ilość danych jest odczytywana.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Przepakuj dowolne archiwum zip, które wykazuje te problemy.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
