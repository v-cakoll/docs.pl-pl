---
title: Formaty ścieżki plików w systemach Windows
ms.date: 06/28/2018
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0efef54abd1da9631b5a560b49c6587d726e9193
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861305"
---
# <a name="file-path-formats-on-windows-systems"></a>Formaty ścieżki plików w systemach Windows

Wiele typów elementów członkowskich <xref:System.IO> obejmują przestrzeni nazw `path` parametr, który pozwala określić ścieżkę bezwzględną lub względną do zasobu systemu plików. Ta ścieżka jest następnie przekazywany do [Windows plik systemowy interfejsów API](https://msdn.microsoft.com/library/windows/desktop/aa364407(v=vs.85).aspx). W tym temacie opisano formaty ścieżki plików, których można użyć w systemach Windows.

## <a name="traditional-dos-paths"></a>Tradycyjne ścieżki DOS

Standardowa ścieżki DOS może składać się z trzech składników:

- Woluminu lub litery dysku, a następnie separator woluminu (`:`).
- Nazwa katalogu. [Znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela podkatalogów w hierarchii katalogów zagnieżdżonych.
- Opcjonalnie nazwy pliku. [Znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela ścieżkę pliku i nazwa pliku.

Jeśli wszystkie trzy składniki są zainstalowane, ścieżka jest bezwzględna. Jeśli nie określono żadnych woluminu lub litery dysku i nazwy katalogów rozpoczyna się od [znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>), ścieżka jest względna od katalogu głównego na bieżącym dysku. W przeciwnym razie ścieżki jest określana względem bieżącego katalogu. W poniższej tabeli przedstawiono niektóre możliwe katalogu i ścieżek plików.

|Ścieżka  |Opis  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Ścieżka bezwzględna do pliku w folderze głównym dysku C: |
| `\Program Files\Custom Utilities\StringFinder.exe` | Ścieżka bezwzględna w katalogu głównym na bieżącym dysku. |
| `2018\January.xlsx` | Ścieżka względna do pliku w podkatalogu bieżącego katalogu. |
| `..\Publications\TravelBrochure.pdf` | Ścieżka względna do pliku w katalogu, który jest równorzędny bieżącego katalogu. |
| `C:\Projects\apilibrary\apilibrary.sln` | Ścieżka bezwzględna do pliku w folderze głównym dysku C: |
| `C:Projects\apilibrary\apilibrary.sln` | Ścieżka względna od bieżącego katalogu na dysku C:. |

> [!IMPORTANT]
> Należy zauważyć różnicę między ostatnich dwóch ścieżek. Zarówno określić specyfikator opcjonalne woluminu (C: w obu przypadkach), ale pierwszy zaczyna się od katalogu głównego określonego woluminu, natomiast druga nie. W wyniku pierwszy jest ścieżką bezwzględną w katalogu głównym dysku C:, natomiast druga jest ścieżką względną z bieżącego katalogu dysku C:. Użyj drugiego formularza po pierwszym jest przeznaczony jest źródłem typowych błędów, które obejmują ścieżki plików Windows.

Można określić, czy ścieżka pliku jest w pełni kwalifikowany (oznacza to, jego ścieżka jest niezależna od bieżącego katalogu i nie ulega zmianie, gdy zmienia bieżący katalog) przez wywołanie metody <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> metody. Należy pamiętać, że znajdzie takiej ścieżki może zawierać segmentów względna katalogu (`.` i `..`) i nadal być w pełni kwalifikowana Jeśli rozpoznana ścieżka zawsze wskazuje w tej samej lokalizacji.

Poniższy przykład ilustruje różnicę między ścieżki względne i bezwzględne. Przyjęto założenie, że katalog D:\FY2018\ istnieje i czy nie został ustawiony dowolny bieżące katalog dla D:\ w wierszu polecenia przed uruchomieniem przykładu.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

## <a name="unc-paths"></a>Ścieżki UNC

Universal naming convention (UNC) ścieżki, które są używane do dostępu do zasobów sieciowych, mają następujący format:

- Nazwa serwera lub hosta, który jest poprzedzony przez \\ \\. Nazwa serwera może być nazwą komputera NetBIOS lub adres IP/nazwę FQDN (IPv4 i IPv6 są obsługiwane).
- Nazwa udziału jest oddzielony od nazwy hosta przez \\. Ze sobą serwera i nazwa udziału tworzą woluminu.
- Nazwa katalogu. [Znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela podkatalogów w hierarchii katalogów zagnieżdżonych.
- Opcjonalnie nazwy pliku. [Znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela ścieżkę pliku i nazwa pliku.

Poniżej przedstawiono kilka przykładów ścieżki UNC:

|Ścieżka  |Opis  |
| -- | -- |
| `\\system07\C$\` | Katalog główny dysku c: dysków na `system07`. |
| `\\Server2\Share\Test\Foo.txt` | Plik Foo.txt w katalogu testu \\ \\Serwer2\\udostępnianie woluminów.|

Musi być zawsze w pełni kwalifikowaną ścieżkę UNC. Mogą zawierać segmentów względna katalogu (`.` i `..`), ale te muszą być częścią w pełni kwalifikowaną ścieżkę. Tylko przez mapowanie ścieżki UNC na literę dysku, można użyć ścieżek względnych.

## <a name="dos-device-paths"></a>Ścieżki urządzenia systemu DOS

System operacyjny Windows ma modelu ujednoliconego obiektu, który wskazuje wszystkie zasoby, łącznie z plikami. Te ścieżki obiektów są dostępne z okna konsoli i są narażone na warstwie systemu Win32 za pośrednictwem specjalnego folderu łączy symbolicznych, które mapowania starszych ścieżek systemu DOS i UNC. Ten specjalny folder jest dostępna za pośrednictwem składnia ścieżki urządzenia systemu DOS, który będzie miał jedną z:

`\\.\C:\Test\Foo.txt`  
`\\?\C:\Test\Foo.txt`

> [!NOTE]
> Składnia ścieżki urządzenia systemu DOS jest obsługiwana w implementacji platformy .NET w systemie Windows, począwszy od programu .NET Core 1.1 i .NET Framework 4.6.2.

Ścieżka urządzenia systemu DOS składa się z następujących składników:

- Specyfikator ścieżki urządzenia (`\\.\` lub `\\?\`), który identyfikuje ścieżkę jako ścieżki urządzenia systemu DOS.

   > [!NOTE]
   > `\\?\` Jest obsługiwana we wszystkich wersjach programu .NET Core i .NET Framework, począwszy od wersji 4.6.2.
   
- Link symboliczny do obiektu urządzenia "członu real" (C: w tym przypadku).

   Pierwszy segment ścieżki urządzenia systemu DOS, po specyfikatorze ścieżki urządzenia identyfikuje woluminu lub dysku. (Na przykład `\\?\C:\` i `\\.\BootPartition\`.)

   Istnieje jedno łącze UNC, która jest wywoływana, nie zaskakująco `UNC`. Na przykład:

      `\\.\UNC\Server\Share\Test\Foo.txt`
      `\\?\UNC\Server\Share\Test\Foo.txt`

    Dla urządzenia UNC fragment serwera/udział jest formularzy woluminu. Na przykład w `\\?\server1\e:\utilities\\filecomparer\`, fragment serwera/udział jest server1\utilities. Jest to istotne podczas wywoływania metody takie jak <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> segmentów względna katalogu; nigdy nie jest możliwe do nawigacji w przeszłości woluminu. 

Ścieżki urządzenia DOS są w pełni kwalifikowane przez definicję. Segmenty względna katalogu (`.` i `..`) nie są dozwolone. Bieżący katalog nigdy nie wprowadzają do ich użycia.

## <a name="example-ways-to-refer-to-the-same-file"></a>Przykład: Sposobów, aby odwołać się do tego samego pliku

W poniższym przykładzie pokazano kilka sposobów, w którym możesz zapoznać się z plikiem przy użyciu interfejsów API w <xref:System.IO> przestrzeni nazw. Przykład tworzy <xref:System.IO.FileInfo> obiektu i zastosowań jego <xref:System.IO.FileInfo.Name> i <xref:System.IO.FileInfo.Length> właściwości, aby wyświetlić nazwę pliku i długość pliku.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Ścieżka normalizacji

Prawie wszystkie ścieżki przekazany do Windows API są znormalizowane. Podczas normalizacji Windows wykonuje następujące czynności:

- Określa ścieżkę.
- Częściowo kwalifikowane (względnej) ścieżki dotyczy bieżącego katalogu.
- Canonicalizes separatory składnika i katalog.
- Ocenia składniki względna katalogu (`.` dla bieżącego katalogu i `..` dla katalogu nadrzędnego).
- Przycina niektórych znaków.

Ta normalizacji lubi niejawnie, ale możesz zrobić to jawnie przez wywołanie metody <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> metody, która zawija wywołanie do [funkcja GetFullPathName()](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).aspx). Można również wywołać Windows [funkcja GetFullPathName()](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).aspx) bezpośrednio przy użyciu metody P/Invoke. Można również wywołać 

### <a name="identifying-the-path"></a>Identyfikowanie ścieżki

Pierwszym krokiem podczas normalizacji ścieżki identyfikuje typ ścieżki. Ścieżki można podzielić na jeden z kilku kategorii:

- Są one ścieżki urządzenia. oznacza to, że zaczynają się z dwóch separatory i znak zapytania lub okres (`\\?` lub `\\.`).
- Są one ścieżki UNC. oznacza to, że ich zaczyna się od dwóch separatory bez znaku zapytania lub okres. 
- Są one w pełni kwalifikowanej ścieżki DOS. oznacza to, że ich zaczynają się od litery dysku, separator woluminu i separator składników (`C:\`).
- Wyznaczają starszego urządzenia (`CON`, `LPT1`).
- Są one względem katalogu głównego na bieżącym dysku; oznacza to, że zaczynają się separatorem pojedynczego składnika (`\`).
- Są one względem bieżącego katalogu określonego dysku; oznacza to, że ich zaczynają się od litery dysku, separator woluminu i nie separator składników (`C:`).
- Są one względem bieżącego katalogu; oznacza to, że zaczynają się inaczej (`temp\testfile.txt`).

Typ ścieżki Określa, czy bieżący katalog jest stosowana w jakiś sposób. Określa również, co to jest "root" ścieżka.

### <a name="handling-legacy-devices"></a>Obsługa starszych urządzeń

Jeśli ścieżka jest starszego urządzenia systemu DOS na takie `CON`, `COM1`, lub `LPT1`, jest konwertowana na ścieżki urządzenia przez poprzedzenie jej `\\.\` i zwrócone. 

Ścieżkę, która zaczyna się od nazwy starszego urządzenia jest zawsze interpretowane jako starszego urządzenia przez <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> metody. Na przykład ścieżka urządzenia systemu DOS dla `CON.TXT` jest `\\.\CON`, ścieżkę urządzenia systemu DOS i `COM1.TXT\file1.txt` jest `\\.\COM1`.

### <a name="applying-the-current-directory"></a>Stosowanie bieżącego katalogu

Jeśli ścieżka nie jest w pełni kwalifikowaną, Windows stosuje bieżący katalog do niego. UNC i ścieżki urządzenia nie ma bieżącego katalogu, które są stosowane. Żadna z nich nie jest pełną dysku z separatorem C:\\.

Jeśli ścieżka zaczyna się od separatora pojedynczego składnika, stosowany jest dysk z bieżącego katalogu. Na przykład, jeśli ścieżka pliku jest `\utilities` i bieżący katalog to `C:\temp\`, tworzy normalizacji `C:\utilities`.

Jeśli ścieżka zaczyna się od litery dysku, separator woluminu i nie separator składników, stosowany jest ostatni bieżącego katalogu z powłoki poleceń określonego dysku. Jeśli nie ustawiono ostatniego bieżącego katalogu, jest stosowana stacji autonomicznej. Na przykład, jeśli ścieżka pliku jest `D:sources`, bieżący katalog to `C:\Documents\`, i był ostatni bieżącego katalogu na dysku D: `D:\sources\`, wynik jest `D:\sources\sources`. Te ścieżki "dysku względna" są wspólne źródło błędy logiczne programów i skryptów. Przy założeniu, że ścieżki rozpoczynającej się od litery i dwukropek jest względna oczywiście nie jest prawidłowy.

Jeśli ścieżka zaczyna się coś innego niż separatora, są stosowane bieżący dysk i katalog bieżący. Na przykład, jeśli ścieżka jest `filecompare` i bieżący katalog to `C:\utilities\`, wynik jest `C:\utilities\filecompare\`.

> [!IMPORTANT]
> Ścieżki względne są niebezpiecznych w aplikacjach wielowątkowych (oznacza to, że większość aplikacji), ponieważ bieżący katalog to ustawienie na proces. Jednym z wątków można zmienić bieżący katalog, w dowolnym momencie. Począwszy od platformy .NET Core 2.1, możesz wywołać <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> metodę, aby uzyskać ścieżkę bezwzględną ścieżką względną i ścieżki podstawowej (bieżący katalog), który chcesz rozwiązać go przed. 

### <a name="canonicalizing-separators"></a>Separatory przekształcania w formę kanoniczną

Wszystkie kreski ułamkowe (`/`) są konwertowane na standardowa separator Windows kreski ułamkowej odwróconej (`\`). Jeśli są obecne, szereg ukośniki, których wykonaj pierwsze dwa ukośniki są zwinięte do pojedynczego ukośnika.

### <a name="evaluating-relative-components"></a>Ocena względne składników

Ścieżka jest przetwarzany, wszelkie składniki i segmentów, które składają się z pojedynczego lub podwójnego kropki (`.` lub `..`) są obliczane: 

- W zadanym przedziale bieżący segment zostanie usunięty, ponieważ odwołuje się on w bieżącym katalogu.

- W okresie double bieżącego segmentu i nadrzędne są usuwane, ponieważ okres double odwołuje się do katalogu nadrzędnego.

   Katalogi nadrzędne są usuwane tylko wtedy, jeśli nie są one poza katalog główny ścieżki. Katalog główny ścieżki zależy od typu ścieżki. Jest dysk (`C:\`) dla ścieżki DOS, serwer/udostępniania dla UNC (`\\Server\Share`) oraz prefiks ścieżki urządzenia dla urządzenia ścieżek (`\\?\` lub `\\.\`).

### <a name="trimming-characters"></a>Przycinanie znaków

Wraz z uruchomienia separatory i segmentów względne usunięty wcześniej występują dodatkowe znaki są usuwane podczas normalizacji:

- Segment kończy się na jednej kropki, tego okresu zostanie usunięta. (Segment okresu pojedynczym lub podwójnym znormalizowane w poprzednim kroku. Segment co najmniej trzy kropki nie jest znormalizowana i jest faktycznie nazwą prawidłową pliku lub katalogu.)

- Jeśli ścieżka nie kończy się separatorem, wszystkie końcowe kropek i spacji (U + 0020), są usuwane. Jeśli ostatni element jest po prostu okres pojedyncze lub podwójne, znajduje się w obszarze reguła względne składniki powyżej. 

   Ta reguła oznacza, że nazwę katalogu można utworzyć ze spacją końcową, dodając końcowe separator po miejsce.  

   > [!IMPORTANT]
   > Należy **nigdy nie** Utwórz nazwę pliku lub katalogu ze spacją końcową. Spacje końcowe może utrudnić lub niemożliwe do dostępu do katalogu i aplikacji często się niepowodzeniem podczas próby obsługi katalogów lub plików, których nazwy zawierają spacje końcowe.

## <a name="skipping-normalization"></a>Pomijanie normalizacji

Zwykle dowolną ścieżkę przekazywane do interfejsu API programu Windows (skutecznie) jest przekazywana do [funkcja GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) i znormalizowana. Istnieje jeden ważny wyjątek: ścieżka urządzenia, która rozpoczyna się od znaku zapytania, a nie przez okres. Chyba, że ścieżka zaczyna dokładnie `\\?\` (Uwaga użytkowania canonical ukośnik odwrotny), jej jest znormalizować.

Dlaczego czy chcesz pominąć normalizacji? Istnieją trzy główne przyczyny:

1. Aby uzyskać dostęp do ścieżki, które są zwykle niedostępne, ale także są dopuszczalne. Plik lub katalog o nazwie `hidden.`, na przykład, istnieje możliwość dostępu w jakikolwiek inny sposób. 

1. Aby zwiększyć wydajność przez pominięcie normalizacji, jeśli została już znormalizowane.

1. Od programu .NET Framework, aby pominąć `MAX_PATH` Sprawdź, czy długość ścieżki umożliwić ścieżek, które są większe niż 259 znaków. Większość interfejsów API Zezwól na to, z pewnymi wyjątkami.

> [!NOTE]
> .NET core obsługuje długich ścieżek niejawnie i nie wykonuje `MAX_PATH` Sprawdź. `MAX_PATH` Sprawdzenie jest stosowane tylko do programu .NET Framework.

Pomijanie kontroli ścieżki normalizacji i maksymalna jest jedyną różnicą między składni ścieżki dwóch urządzeń; w przeciwnym razie są identyczne. Należy zachować ostrożność w przypadku pominięcia normalizacji, ponieważ łatwo można utworzyć ścieżki, które są trudne do przeciwdziałania "normal" aplikacji.

Ścieżki, które zaczyna się `\\?\` nadal są znormalizowane, jeśli jawnie przekażesz je do [funkcja GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).

Należy pamiętać o możliwości ścieżki ponad `MAX_PATH` znaków [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) bez `\\?\`. Obsługuje ona ścieżki dowolnej długości maksymalnie rozmiar maksymalny ciągu, która może obsłużyć Windows.

## <a name="case-and-the-windows-file-system"></a>Wielkość liter i system plików Windows

Cecha systemu plików Windows, który użytkowników innych niż Windows i deweloperów Znajdź mylące jest tej ścieżki i nazwy katalogów jest rozróżniana wielkość liter. Oznacza to, że nazwy katalogów i plików uwzględniają wielkość liter w wyrazie ciągi tekstowe używane podczas ich tworzenia. Na przykład wywołanie metody

```csharp
Directory.Create(TeStDiReCtOrY);
```
Tworzy katalog o nazwie katalog testowy. W przypadku zmiany nazwy, katalog lub plik, aby zmienić jego przypadek, nazwa pliku lub katalogu odzwierciedla wielkość liter w ciągu używany, gdy można zmienić jego nazwę. Na przykład poniższy kod zmienia nazwę pliku o nazwie jako się jako:

```csharp
using System;
using System.IO;

class Example
{
   public static void Main()
   {
      var fi = new FileInfo(@".\test.txt");
      fi.MoveTo(@".\Test.txt");
   }
}
``` 
```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim fi As New FileInfo(".\test.txt")
      fi.MoveTo(".\Test.txt")
   End Sub
End Module
```

Jednak bez uwzględniania wielkości liter podczas porównywania nazw katalogów i plików. Jeśli wyszukasz plik o nazwie "jako" interfejsów API systemu plików .NET zignorować przypadek, w porównaniu. Jako, TEST. TXT, test. TXT i wszelkich innych kombinacji wielkich i małych liter, będą zgodne "jako".
