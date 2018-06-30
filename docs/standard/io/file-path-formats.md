---
title: Ścieżka formatów plików w systemie Windows
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
ms.openlocfilehash: a5fccf5ea86469f14963fad8e7d2af0f7c68d2df
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106940"
---
# <a name="file-path-formats-on-windows-systems"></a>Ścieżka formatów plików w systemie Windows

Elementy członkowskie wielu typów w <xref:System.IO> obejmują przestrzeni nazw `path` parametr, który pozwala określić ścieżkę bezwzględną ani względną do zasobu systemu plików. Ta ścieżka są następnie przekazywane do [Windows plik systemowy interfejsów API](https://msdn.microsoft.com/library/windows/desktop/aa364407(v=vs.85).aspx). W tym temacie opisano formaty ścieżki do plików używanych w systemach Windows.

## <a name="traditional-dos-paths"></a>Tradycyjny ścieżki DOS

Standardowa ścieżka DOS może składać się z trzech składników:

- Wolumin lub litery dysku, a następnie separatora woluminu (`:`).
- Nazwa katalogu. [Znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela podkatalogów w ramach hierarchii katalogów zagnieżdżonych.
- Opcjonalna nazwa pliku. [Znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela ścieżkę pliku i nazwa pliku.

W przypadku wszystkich trzech komponentów ścieżka jest bezwzględna. Jeśli określono nie woluminu lub litery dysku i rozpoczyna się od nazwy katalogów [znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>), ścieżka jest względna z katalogu głównego bieżącego dysku. W przeciwnym razie ścieżka jest powiązane z bieżącym katalogiem. W poniższej tabeli przedstawiono niektóre możliwe katalogu i ścieżki plików.

|Ścieżka  |Opis  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Ścieżka bezwzględna do pliku w folderze głównym dysku C: |
| `\Program Files\Custom Utilities\StringFinder.exe` | Ścieżka bezwzględna od głównego bieżącego dysku. |
| `2018\January.xlsx` | Ścieżka względna do pliku w podkatalogu bieżącego katalogu. |
| `..\Publications\TravelBrochure.pdf` | Ścieżka względna do pliku w katalogu, w którym jest element równorzędny bieżącego katalogu. |
| `C:\Projects\apilibrary\apilibrary.sln` | Ścieżka bezwzględna do pliku w folderze głównym dysku C: |
| `C:Projects\apilibrary\apilibrary.sln` | Ścieżka względna od katalogu bieżącego dysku C:. |

> [!IMPORTANT]
> Należy pamiętać, to różnica między ostatnich dwóch ścieżek. Zarówno określić opcjonalne woluminu specyfikator (C: w obu przypadkach), ale pierwszy rozpoczyna się od katalogu głównego określonego woluminu, podczas gdy druga nie. W wyniku pierwszy jest ścieżką bezwzględną z katalogu głównego dysku C:, drugi jest ścieżką względną z bieżącego katalogu dysku C:. Użycie drugiego formularza po pierwszym jest przeznaczona jest wspólne źródło usterki, które obejmują ścieżki plików systemu Windows.

Można określić, czy ścieżka pliku jest w pełni kwalifikowana (oznacza to, że ścieżka jest niezależne od bieżącego katalogu i nie ulega zmianie, gdy zmienia się bieżący katalog) przez wywołanie metody <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> metody. Należy pamiętać, że takie ścieżki może zawierać segmentów względna katalogu (`.` i `..`) i nadal być w pełni kwalifikowana Jeśli rozpoznana ścieżka wskazuje zawsze tej samej lokalizacji.

Poniższy przykład przedstawia różnicę między ścieżki względne i bezwzględne. Przyjęto założenie, że istnieje katalog D:\FY2018\ i nie ustawienie bieżącej wykazu dla D:\ w wierszu polecenia przed uruchomieniem w przykładzie.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

## <a name="unc-paths"></a>Ścieżki UNC

Universal naming convention (UNC) ścieżki, które są używane do dostępu do zasobów sieciowych, mają następujący format:

- Serwera lub nazwę hosta, który jest poprzedzone \\ \\. Nazwa serwera może być nazwą NetBIOS komputera lub adres IP/nazwa FQDN (IPv4 i IPv6 są obsługiwane).
- Nazwa udziału jest oddzielona od nazwy hosta przez \\. Serwer i nazwę udziału składają się woluminu.
- Nazwa katalogu. [Znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela podkatalogów w ramach hierarchii katalogów zagnieżdżonych.
- Opcjonalna nazwa pliku. [Znakiem separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela ścieżkę pliku i nazwa pliku.

Oto kilka przykładów ścieżki UNC:

|Ścieżka  |Opis  |
| -- | -- |
| `\\system07\C$\` | Katalog główny dysku c: dysków na `system07`. |
| `\\Server2\Share\Test\Foo.txt` | Plik Foo.txt w katalogu testu \\ \\Serwer2\\udział woluminu.|

Ścieżki UNC zawsze musi być w pełni kwalifikowana. Obejmują one segmentów względna katalogu (`.` i `..`), ale musi to być część w pełni kwalifikowaną ścieżkę. Używając ścieżek względnych tylko przez mapowanie ścieżką UNC do litery dysku.

## <a name="dos-device-paths"></a>Ścieżki urządzenia systemu DOS

System operacyjny Windows ma ujednoliconego obiektu modelu, który wskazuje wszystkie zasoby, w tym pliki. Te ścieżki obiektu są dostępne z okna konsoli i są widoczne dla warstwy Win32 za pomocą specjalnego folderu linki symboliczne zmapowane do starszej wersji ścieżki DOS i UNC. Ten folder specjalny jest dostępny za pośrednictwem składnia ścieżki DOS urządzenia, które jest jednym z:

`\\.\C:\Test\Foo.txt`  
`\\?\C:\Test\Foo.txt`

> [!NOTE]
> Składnia ścieżki urządzenia systemu DOS jest obsługiwana w implementacji .NET działających w systemie Windows począwszy od programu .NET Core 1.1 i .NET Framework 4.6.2.

Ścieżka urządzenia systemu DOS składa się z następujących składników:

- Specyfikator ścieżka urządzenia (`\\.\` lub `\\?\`), który identyfikuje ścieżkę jako ścieżka urządzenia systemu DOS.

   > [!NOTE]
   > `\\?\` Jest obsługiwane we wszystkich wersjach programu .NET Core i w programie .NET Framework, począwszy od wersji 4.6.2.
   
- Łącze symboliczne do obiektu urządzenia "rzeczywiste" (C: w tym przypadku).

   Pierwszy segment ścieżki urządzenia systemu DOS po specyfikatorze ścieżka urządzenia identyfikuje woluminu lub dysku. (Na przykład `\\?\C:\` i `\\.\BootPartition\`.)

   Ma określonego łącza UNC, które jest wywołane nie zaskakująco `UNC`. Na przykład:

      `\\.\UNC\Server\Share\Test\Foo.txt`
      `\\?\UNC\Server\Share\Test\Foo.txt`

    Dla urządzenia UNC część serwera i udostępniania jest formularze woluminu. Na przykład w `\\?\server1\e:\utilities\\filecomparer\`, część serwera i udostępniania jest server1\utilities. Jest to istotne w wywołaniu metody, takie jak <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> segmentów względna katalogu; nie ma możliwości Przejdź poza woluminu. 

Definicja w pełni kwalifikowana ścieżki urządzenia systemu DOS. Segmenty względna katalogu (`.` i `..`) są niedozwolone. Bieżący katalogów nigdy nie wprowadzają do ich użycia.

## <a name="example-ways-to-refer-to-the-same-file"></a>Przykład: Sposoby odwoływać się do tego samego pliku

Poniższy przykład przedstawia niektóre sposoby, w którym użytkownik może odwoływać się do pliku przy użyciu interfejsów API w <xref:System.IO> przestrzeni nazw. Przykład tworzy <xref:System.IO.FileInfo> obiektu i używa jej <xref:System.IO.FileInfo.Name> i <xref:System.IO.FileInfo.Length> właściwości, aby wyświetlić nazwę pliku i długość pliku.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Ścieżka normalizacji

Znormalizowany są prawie wszystkie ścieżki przekazany do interfejsów API systemu Windows. Podczas normalizacji Windows wykonuje następujące czynności:

- Określa ścieżkę.
- Dotyczy bieżącego katalogu częściowo kwalifikowanej ścieżki (względnej).
- Canonicalizes separatory składnika i katalogu.
- Oblicza składniki względna katalogu (`.` dla bieżącego katalogu i `..` dla katalogu nadrzędnego).
- Przycina niektórych znaków.

Ten normalizacji niejawnie się stanie, ale należy go jawnie przez wywołanie metody <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> metodę, która opakowuje wywołanie [funkcja GetFullPathName()](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx). Możesz także wywołać systemu Windows [funkcja GetFullPathName()](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) bezpośrednio przy użyciu metody P/Invoke. Możesz także wywołać 

### <a name="identifying-the-path"></a>Identyfikowanie ścieżki

Pierwszym etapem normalizacji ścieżki identyfikuje typu ścieżki. Ścieżki dzielą się na kilka kategorii:

- Są one ścieżki urządzenia. oznacza to, Rozpocznij dwa separatory i znak zapytania lub okres (`\\?` lub `\\.`).
- Są one ścieżki UNC. oznacza to, że ich rozpoczynać się od dwóch separatorów bez znaku zapytania lub okres. 
- Są one pełni kwalifikowanej ścieżki DOS. oznacza to, ich rozpoczynać się od litery dysku, separatora woluminu i separatora składnika (`C:\`).
- Wyznaczają starszych urządzeń (`CON`, `LPT1`).
- Są one względem katalogu głównego dysku bieżącego; oznacza to, rozpocząć się separatorem pojedynczego składnika (`\`).
- Są one powiązane z bieżącym katalogiem określony dysk; oznacza to, że ich zaczynać się od litery dysku, separatora woluminu i separatora składnika (`C:`).
- Są one powiązane z bieżącym katalogiem; oznacza to, rozpocząć się inaczej (`temp\testfile.txt`).

Typ ścieżki Określa, czy bieżący katalog jest stosowane w określony sposób. Określa również, co to jest "root" ścieżki.

### <a name="handling-legacy-devices"></a>Obsługa starszych urządzeń

Jeśli ścieżka nie jest starszego urządzenia systemu DOS takich jak `CON`, `COM1`, lub `LPT1`, jest konwertowana na ścieżkę do urządzenia, dołączając `\\.\` i zwrócone. 

Ścieżki, która zaczyna się od nazwy starszych urządzeń zawsze jest interpretowana jako starszego urządzenia przez <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> metody. Na przykład ścieżka urządzenia systemu DOS dla `CON.TXT` jest `\\.\CON`i ścieżkę urządzenia systemu DOS `COM1.TXT\file1.txt` jest `\\.\COM1`.

### <a name="applying-the-current-directory"></a>Stosowanie bieżącego katalogu

Jeśli ścieżki nie jest w pełni kwalifikowana, system Windows stosuje bieżącego katalogu do niego. UNC i ścieżki urządzenia nie mają bieżącego katalogu, które są stosowane. Nie jest pełną dysku z separatorem C:\\.

Jeśli ścieżka rozpoczyna się od separatora pojedynczego składnika, zostanie zastosowane dysku z bieżącego katalogu. Na przykład, jeśli ścieżka pliku jest `\utilities` i bieżący katalog jest `C:\temp\`, i tworzy normalizacji `C:\utilities`.

Jeśli ścieżka rozpoczyna się od litery dysku, separatora woluminu i separatora składnika, zostanie zastosowane ostatniego bieżącego katalogu, ustaw z powłoki poleceń określonego dysku. Jeśli ostatniego bieżącego katalogu nie została ustawiona, zostanie zastosowane samego dysku. Na przykład, jeśli ścieżka pliku jest `D:sources`, bieżący katalog jest `C:\Documents\`, i został ostatniego bieżącego katalogu na dysku D: `D:\sources\`, wynikiem jest `D:\sources\sources`. Te ścieżki "dysk względnej" są wspólne źródło błędów logiki programów i skryptów. Przy założeniu, że ścieżki rozpoczynającej się od litery i dwukropka nie jest względna oczywiście nie jest prawidłowa.

Jeśli ścieżka rozpoczyna się od czegoś innego niż separatora, są stosowane bieżącego dysku i bieżący katalog. Na przykład, jeśli ścieżka jest `filecompare` i bieżący katalog jest `C:\utilities\`, wynikiem jest `C:\utilities\filecompare\`.

> [!IMPORTANT]
> Ścieżki względne są niebezpieczne w aplikacjach wielowątkowych (to znaczy, że większość aplikacji), ponieważ bieżący katalog to ustawienie dla procesu. Którymkolwiek wątku można zmienić bieżący katalog w dowolnym momencie. Począwszy od programu .NET Core 2.1, można wywołać <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> metody można odczytać ścieżki bezwzględnej ścieżki względnej i ścieżki podstawowej (bieżącego katalogu), który chcesz rozwiązać go przed. 

### <a name="canonicalizing-separators"></a>Kanoniczną separatorów

Przekazuj wszystkie ukośniki (`/`) są konwertowane na standardowe separatora systemu Windows, kreski ułamkowej odwróconej (`\`). Jeśli są obecne, szereg ukośniki, które należy wykonać pierwsze dwa ukośniki są zwijane do pojedynczego ukośnika.

### <a name="evaluating-relative-components"></a>Ocena względną składników

W trakcie przetwarzania ścieżki wszystkich składników lub segmentów, które składają się z jedną lub okres double (`.` lub `..`) są oceniane: 

- Dla jednego okresu jak bieżący segment zostanie usunięty, ponieważ odwołuje się do bieżącego katalogu.

- Okres dwa razy segment nadrzędnego, jak bieżący segment są usuwane, ponieważ podwójny okres odwołuje się do katalogu nadrzędnego.

   Katalogi nadrzędne są usuwane tylko, jeśli nie znajdują się one poza główny ścieżki. Główny ścieżki zależy od typu ścieżki. Jest dysku (`C:\`) dla systemu DOS ścieżek, serwera i udostępniania dla UNC (`\\Server\Share`) i prefiksu ścieżka urządzenia dla ścieżki urządzeń (`\\?\` lub `\\.\`).

### <a name="trimming-characters"></a>Przycinanie znaków

Wraz z przebiegów separatorów i segmentów względną usunięte wcześniej niektóre dodatkowe znaki zostaną usunięte podczas normalizacji:

- Jeśli segment kończy się w zadanym przedziale czasu, tego okresu zostanie usunięta. (Segment okresu pojedynczym lub podwójnym znormalizowanych w poprzednim kroku. Segment trzy lub więcej okresów nie jest znormalizowana i jest rzeczywistą nazwą prawidłowego pliku/katalogu.)

- Jeśli ścieżka nie kończyć się separatorem, wszystkie końcowe kropek i spacji (U + 0020) zostaną usunięte. Ostatni segment w przypadku po prostu okres pojedynczym lub podwójnym, podlega zasadę względną składniki powyżej. 

   Ta reguła oznacza, że nazwę katalogu można utworzyć z spacji przez dodanie końcowe separatora po miejsce.  

   > [!IMPORTANT]
   > Należy **nigdy nie** Utwórz nazwę pliku lub katalogu z spacje końcowe. Spacje końcowe może utrudniać lub niemożliwe, aby uzyskać dostęp do katalogu i aplikacje często się niepowodzeniem podczas próby obsługi katalogów lub plików, których nazwy zawierają spacje końcowe.

## <a name="skipping-normalization"></a>Pomijanie normalizacji

Zwykle dowolną ścieżkę przekazany do Windows API (skutecznie) jest przekazywana do [funkcja GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) i znormalizowana. Istnieje jeden wyjątek ważne: ścieżki urządzenia, która rozpoczyna się od znaku zapytania zamiast okres. Jeśli ścieżka rozpoczyna się dokładnie z `\\?\` (Uwaga Użycie canonical ukośnik odwrotny), jest ona znormalizowany.

Dlaczego czy chcesz pominąć normalizacji? Istnieją trzy główne przyczyny:

1. Aby uzyskać dostęp do ścieżki, które nie są zwykle dostępne, ale są prawnych. Plik lub katalog o nazwie `hidden.`, na przykład istnieje możliwość dostępu w inny sposób. 

1. Aby zwiększyć wydajność, pomijając normalizacji, jeśli zostały już znormalizowany.

1. W programie .NET Framework, aby pominąć `MAX_PATH` Sprawdź, czy długość ścieżki do obsługi ścieżek, które są większe niż 259 znaków. Większość interfejsów API Zezwól na to, z pewnymi wyjątkami.

> [!NOTE]
> Oprogramowanie .NET core obsługuje długich ścieżek niejawnie i nie wykonuje `MAX_PATH` Sprawdź. `MAX_PATH` Sprawdzenie jest stosowane tylko dla programu .NET Framework.

Pomijanie normalizacji i max kontroli ścieżki jest jedyną różnicą między składni ścieżki dwóch urządzenia; w przeciwnym razie są one identyczne. Należy zachować ostrożność przy normalizacji zostanie pominięta, ponieważ można łatwo utworzyć ścieżek, które są trudne do postępowania w przypadku aplikacji "normal".

Ścieżki zaczynające się `\\?\` są nadal znormalizowany je, aby jawnie przekazania [funkcja GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx).

Należy pamiętać o możliwości ścieżki z więcej niż `MAX_PATH` znaków [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) bez `\\?\`. Obsługuje ona dowolnego długość ścieżki do maksymalny rozmiar ciągu obsługujący systemu Windows.

## <a name="case-and-the-windows-file-system"></a>Wielkość liter i systemu plików

Cecha systemu plików z systemem innym niż Windows użytkowników i deweloperów znaleźć mylące jest tej ścieżki i nazwy katalogów jest rozróżniana wielkość liter. Oznacza to, że nazwy katalogów i plików odzwierciedlają wielkość liter w wyrazie ciągi używane podczas ich tworzenia. Na przykład wywołanie metody

```csharp
Directory.Create(TeStDiReCtOrY);
```
Tworzy katalog o nazwie TeStDiReCtOrY. Jeśli zmienisz katalog lub plik, aby zmienić jego case, nazwa pliku lub katalogu odzwierciedla przypadku ciąg używany po zmianie nazwy. Na przykład poniższy kod zmienia nazwę pliku o nazwie test.txt do Test.txt:

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

Jednak bez uwzględniania wielkości liter podczas porównywania nazw plików i katalogów. Jeśli wyszukać plik o nazwie "test.txt", interfejsów API systemu plików .NET zignorować liter w porównaniu. Test.txt, testu. TXT, testu. TXT i wszelkich innych kombinacji wielkich i małych liter będą zgodne "test.txt".
