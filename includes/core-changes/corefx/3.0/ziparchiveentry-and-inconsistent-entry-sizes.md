---
ms.openlocfilehash: 8c8e87c885c99d28aa9a7a5d5a2b48c80d40d7db
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721122"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>Element ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wpisów

Archiwa zip wyświetlają rozmiar skompresowany i nieskompresowany w katalogu centralnym i nagłówku lokalnym.  Dane wejściowe również wskazują jego rozmiar.  W programie .NET Core 2,2 i starszych wersjach te wartości nigdy nie były sprawdzane pod kątem spójności. Począwszy od platformy .NET Core 3,0, są one teraz.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 2,2 i starszych wersjach program <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> kończy się powodzeniem nawet wtedy, gdy nagłówek lokalny nie zgadza się z centralnym nagłówkiem pliku zip. Dane są dekompresowane do momentu osiągnięcia końca skompresowanego strumienia, nawet jeśli jego długość przekracza rozmiar nieskompresowanych plików wymieniony w katalogu centralnym/nagłówku lokalnym.

Począwszy od platformy .NET Core 3,0, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> Metoda sprawdza, czy nagłówek lokalny i nagłówek centralny zgadzają się na skompresowane i nieskompresowane rozmiary wpisu.  Jeśli tak nie jest, metoda zgłasza <xref:System.IO.InvalidDataException> rozmiar i/lub listę deskryptorów danych w archiwum, które nie zgadzają się z katalogiem centralnym pliku zip. Podczas odczytywania wpisu dekompresowane dane są obcinane do rozmiaru nieskompresowanego pliku wymienionego w nagłówku.

Ta zmiana została wprowadzona w celu upewnienia się, że <xref:System.IO.Compression.ZipArchiveEntry> poprawnie reprezentuje rozmiar danych i że tylko ta ilość danych jest odczytywana.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ponownie spakować wszystkie archiwum zip, które wykazuje te problemy.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
