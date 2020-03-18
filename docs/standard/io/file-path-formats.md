---
title: Formaty ścieżek plików w systemie Windows
ms.date: 06/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
ms.openlocfilehash: b3510be5d417b555d2db163636eac5ce0c0779e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628049"
---
# <a name="file-path-formats-on-windows-systems"></a>Formaty ścieżek plików w systemie Windows

Elementy członkowskie wielu typów <xref:System.IO> w obszarze `path` nazw zawierają parametr, który umożliwia określenie ścieżki bezwzględnej lub względnej do zasobu systemu plików. Ta ścieżka jest następnie przekazywana do [interfejsów API systemu plików systemu Windows](/windows/desktop/fileio/file-systems). W tym temacie omówiono formaty ścieżek plików, których można używać w systemach Windows.

## <a name="traditional-dos-paths"></a>Tradycyjne ścieżki DOS

Standardowa ścieżka DOS może składać się z trzech komponentów:

- Litera woluminu lub napędu, po której następuje separator głośności (`:`).
- Nazwa katalogu. [Znak separatora katalogów](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela podkatalogi w zagnieżdżonej hierarchii katalogów.
- Opcjonalna nazwa pliku. [Znak separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela ścieżkę pliku od nazwy pliku.

Jeśli wszystkie trzy składniki są obecne, ścieżka jest bezwzględna. Jeśli nie określono litery woluminu lub dysku, a nazwa katalogu zaczyna się od [znaku separatora katalogu,](<xref:System.IO.Path.DirectorySeparatorChar>)ścieżka jest względna od katalogu głównego bieżącego dysku. W przeciwnym razie ścieżka jest względem bieżącego katalogu. W poniższej tabeli przedstawiono niektóre możliwe ścieżki katalogów i plików.

|Ścieżka  |Opis  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Bezwzględna ścieżka pliku z katalogu głównego dysku C: |
| `\Program Files\Custom Utilities\StringFinder.exe` | Ścieżka bezwzględna z katalogu głównego bieżącego dysku. |
| `2018\January.xlsx` | Ścieżka względna do pliku w podkatalogu bieżącego katalogu. |
| `..\Publications\TravelBrochure.pdf` | Ścieżka względna do pliku w katalogu, który jest elementem równorzędnym bieżącego katalogu. |
| `C:\Projects\apilibrary\apilibrary.sln` | Ścieżka bezwzględna do pliku z katalogu głównego dysku C: |
| `C:Projects\apilibrary\apilibrary.sln` | Ścieżka względna z bieżącego katalogu dysku C:. |

> [!IMPORTANT]
> Zwróć uwagę na różnicę między dwiema ostatnimi ścieżkami. Oba określają opcjonalny specyfikator woluminu (C: w obu przypadkach), ale pierwszy zaczyna się od katalogu głównego określonego woluminu, podczas gdy drugi nie. W rezultacie pierwszy jest ścieżką bezwzględną z katalogu głównego dysku C:, podczas gdy drugi jest ścieżką względną z bieżącego katalogu dysku C:. Użycie drugiego formularza, gdy pierwszy jest przeznaczony jest częstym źródłem błędów, które obejmują ścieżki plików systemu Windows.

Można określić, czy ścieżka pliku jest w pełni kwalifikowana (oznacza to, że ścieżka jest niezależna <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> od bieżącego katalogu i nie zmienia się po zmianie bieżącego katalogu), wywołując metodę. Należy zauważyć, że taka ścieżka`.` może `..`zawierać względne segmenty katalogów ( i ) i nadal być w pełni kwalifikowane, jeśli rozwiązana ścieżka zawsze wskazuje na tę samą lokalizację.

W poniższym przykładzie przedstawiono różnicę między ścieżkami bezwzględnymi i względnymi. Zakłada się, że katalog D:\FY2018\ istnieje i że nie ustawiono żadnego bieżącego katalogu dla D:\ z wiersza polecenia przed uruchomieniem przykładu.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="unc-paths"></a>Ścieżki UNC

Ścieżki konwencji nazewnictwa uniwersalnego (UNC), które są używane do uzyskiwania dostępu do zasobów sieciowych, mają następujący format:

- Nazwa serwera lub hosta, która \\ \\jest poprzedzona . Nazwa serwera może być nazwą komputera NetBIOS lub adresem IP/FQDN (obsługiwane są iPv4 oraz v6).
- Nazwa udziału, która jest oddzielona \\od nazwy hosta przez . Razem serwer i nazwa udziału tworzą wolumin.
- Nazwa katalogu. [Znak separatora katalogów](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela podkatalogi w zagnieżdżonej hierarchii katalogów.
- Opcjonalna nazwa pliku. [Znak separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela ścieżkę pliku od nazwy pliku.

Oto kilka przykładów ścieżek UNC:

|Ścieżka  |Opis  |
| -- | -- |
| `\\system07\C$\` | Katalog główny dysku C: `system07`na . |
| `\\Server2\Share\Test\Foo.txt` | Plik Foo.txt w katalogu testowym woluminu \\ \\udziału serwera2.\\|

Ścieżki UNC muszą być zawsze w pełni kwalifikowane. Mogą one obejmować względne`.` `..`segmenty katalogów ( i ), ale muszą one być częścią ścieżki w pełni kwalifikowanej. Ścieżek względnych można używać tylko przez mapowanie ścieżki UNC na literę dysku.

## <a name="dos-device-paths"></a>Ścieżki urządzeń DOS

System operacyjny Windows ma ujednolicony model obiektów, który wskazuje wszystkie zasoby, w tym pliki. Te ścieżki obiektów są dostępne z okna konsoli i są widoczne dla warstwy Win32 za pośrednictwem specjalnego folderu dowiązań symbolicznych, na które są mapowane starsze ścieżki DOS i UNC. Ten folder specjalny jest dostępny za pośrednictwem składni ścieżki urządzenia DOS, która jest jedną z:

`\\.\C:\Test\Foo.txt`
`\\?\C:\Test\Foo.txt`

Oprócz identyfikowania dysku za pomocą litery dysku można zidentyfikować wolumin za pomocą jego identyfikatora GUID woluminu. Ma to formę:

`\\.\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`
`\\?\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`

> [!NOTE]
> Składnia ścieżki urządzenia DOS jest obsługiwana w implementacjach .NET działających w systemie Windows, począwszy od .NET Core 1.1 i .NET Framework 4.6.2.

Ścieżka urządzenia DOS składa się z następujących składników:

- Specyfikator ścieżki`\\.\` `\\?\`urządzenia ( lub ), który identyfikuje ścieżkę jako ścieżkę urządzenia DOS.

   > [!NOTE]
   > Jest `\\?\` obsługiwana we wszystkich wersjach programu .NET Core i w platformie .NET Framework, począwszy od wersji 4.6.2.

- Dowiązanie symboliczne do obiektu urządzenia "prawdziwe" (C: w przypadku nazwy dysku lub Wolumin{b75e2c83-0000-0000-602f00000000000000000} w przypadku identyfikatora GUID woluminu).

   Pierwszy segment ścieżki urządzenia DOS po specyfikarze ścieżki urządzenia identyfikuje wolumin lub dysk. (Na przykład `\\?\C:\` `\\.\BootPartition\`i .)

   Istnieje szczególny link dla UNC, który nazywa `UNC`się, nic dziwnego, . Przykład:

  `\\.\UNC\Server\Share\Test\Foo.txt`
  `\\?\UNC\Server\Share\Test\Foo.txt`

    W przypadku unc urządzenia, serwer/część udziału tworzy wolumin. Na przykład `\\?\server1\e:\utilities\\filecomparer\`w programie , część serwera/udziału jest server1\utilities. Jest to istotne podczas wywoływania metody, takich jak <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> względne segmenty katalogów; nigdy nie jest możliwe przejście poza woluminem.

Ścieżki urządzeń DOS są w pełni kwalifikowane z definicji. Względne segmenty`.` `..`katalogów ( i ) nie są dozwolone. Bieżące katalogi nigdy nie wchodzą w ich użycie.

## <a name="example-ways-to-refer-to-the-same-file"></a>Przykład: Sposoby odwoływania się do tego samego pliku

W poniższym przykładzie przedstawiono niektóre ze sposobów, w jaki można odwoływać <xref:System.IO> się do pliku podczas korzystania z interfejsów API w obszarze nazw. Przykład tworzy <xref:System.IO.FileInfo> obiekt i używa jego <xref:System.IO.FileInfo.Name> <xref:System.IO.FileInfo.Length> i właściwości do wyświetlania nazwy pliku i długości pliku.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Normalizacja ścieżki

Prawie wszystkie ścieżki przekazywane do interfejsów API systemu Windows są znormalizowane. Podczas normalizacji system Windows wykonuje następujące kroki:

- Identyfikuje ścieżkę.
- Stosuje bieżący katalog do ścieżek częściowo kwalifikowanych (względnych).
- Kanonizuje separatory komponentów i katalogów.
- Oblicza względne składniki`.` katalogu (dla `..` bieżącego katalogu i dla katalogu nadrzędnego).
- Przycina niektóre znaki.

Ta normalizacja odbywa się niejawnie, ale można <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> to zrobić jawnie, wywołując metodę, która otacza wywołanie [getFullPathName() funkcji](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea). [Funkcję GetFullPathName()](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) systemu Windows można również wywołać bezpośrednio przy użyciu funkcji P/Invoke.

### <a name="identifying-the-path"></a>Identyfikowanie ścieżki

Pierwszym krokiem w normalizacji ścieżki jest identyfikacja typu ścieżki. Ścieżki dzielą się na jedną z kilku kategorii:

- Są to ścieżki urządzeń; oznacza to, że zaczynają się od dwóch separatorów i znaku zapytania lub kropki (`\\?` lub `\\.`).
- Są to ścieżki UNC; oznacza to, że zaczynają się od dwóch separatorów bez znaku zapytania lub kropki.
- Są to w pełni wykwalifikowane ścieżki DOS; oznacza to, że zaczynają się od litery dysku, separatora głośności i separatora komponentu (`C:\`).
- Wyznaczają one starsze`CON` `LPT1`urządzenie ( , ).
- Są one względem katalogu głównego bieżącego dysku; oznacza to, że zaczynają się od`\`separatora pojedynczego komponentu ( ).
- Są one względem bieżącego katalogu określonego dysku; oznacza to, że zaczynają się od litery dysku, separatora głośności i separatora komponentu (`C:`).
- Są one względem bieżącego katalogu; oznacza to, że zaczynają`temp\testfile.txt`się od czegokolwiek innego ( ).

Typ ścieżki określa, czy bieżący katalog jest stosowany w jakiś sposób. Określa również, co to jest "korzeń" ścieżki.

### <a name="handling-legacy-devices"></a>Obsługa starszych urządzeń

Jeśli ścieżka jest starszym urządzeniem `CON` `COM1`DOS, takim jak , lub `LPT1`, `\\.\` jest konwertowana na ścieżkę urządzenia przez przedwtowienie i zwrócenie.

Ścieżka, która zaczyna się od starszej nazwy urządzenia, <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> jest zawsze interpretowana jako starsze urządzenie za pomocą metody. Na przykład ścieżka urządzenia `CON.TXT` DOS dla jest `\\.\CON`, `COM1.TXT\file1.txt` a `\\.\COM1`ścieżka urządzenia DOS dla jest .

### <a name="applying-the-current-directory"></a>Stosowanie bieżącego katalogu

Jeśli ścieżka nie jest w pełni kwalifikowana, system Windows zastosuje do niej bieżący katalog. UnCs i ścieżki urządzeń nie mają zastosowanego bieżącego katalogu. Nie ma również pełnego napędu\\z separatorem C: .

Jeśli ścieżka zaczyna się od separatora pojedynczego komponentu, zostanie zastosowany dysk z bieżącego katalogu. Na przykład jeśli ścieżka `\utilities` pliku jest `C:\temp\`i bieżący katalog `C:\utilities`jest , normalizacja generuje .

Jeśli ścieżka zaczyna się od litery dysku, separatora woluminu i separatora bez komponentu, stosowany jest ostatni bieżący zestaw katalogów z powłoki poleceń dla określonego dysku. Jeśli ostatni bieżący katalog nie został ustawiony, stosowany jest sam dysk. Na przykład, jeśli ścieżka pliku `D:sources`jest `C:\Documents\`, bieżący katalog jest , `D:\sources\`a ostatni `D:\sources\sources`bieżący katalog na dysku D: był , wynik jest . Te ścieżki "dysku względnego" są częstym źródłem błędów logiki programu i skryptu. Zakładając, że ścieżka rozpoczynająca się literą i dwukropkiem nie jest względna, oczywiście nie jest poprawna.

Jeśli ścieżka zaczyna się od czegoś innego niż separator, stosuje się bieżący dysk i bieżący katalog. Na przykład, jeśli `filecompare` ścieżka jest, `C:\utilities\`a bieżący `C:\utilities\filecompare\`katalog jest , wynik jest .

> [!IMPORTANT]
> Ścieżki względne są niebezpieczne w aplikacjach wielowątkowych (czyli w większości aplikacji), ponieważ bieżący katalog jest ustawieniem dla procesu. Każdy wątek można zmienić bieżący katalog w dowolnym momencie. Począwszy od .NET Core 2.1, można wywołać <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> metodę, aby uzyskać ścieżkę bezwzględną ze ścieżki względnej i ścieżki podstawowej (bieżącego katalogu), który ma zostać rozwiązany.

### <a name="canonicalizing-separators"></a>Separatory kanoniczne

Wszystkie ukośniki`/`do przodu ( ) są konwertowane na`\`standardowy separator systemu Windows, ukośnik tylny ( ). Jeśli są one obecne, seria ukośników, które następują po pierwszych dwóch ukośników są zwinięte w jednym ukośniki.

### <a name="evaluating-relative-components"></a>Ocena składników względnych

Podczas przetwarzania ścieżki oceniane są wszystkie komponenty lub segmenty składające się z pojedynczego lub podwójnego okresu (`.` lub `..`)

- Dla pojedynczego okresu bieżący segment jest usuwany, ponieważ odwołuje się do bieżącego katalogu.

- W przypadku podwójnego okresu bieżący segment i segment nadrzędny są usuwane, ponieważ podwójny okres odnosi się do katalogu nadrzędnego.

   Katalogi nadrzędne są usuwane tylko wtedy, gdy nie są poza katalogiem głównym ścieżki. Katalog główny ścieżki zależy od typu ścieżki. Jest to dysk`C:\`( ) dla ścieżek DOS,`\\Server\Share`serwer / udział dla UNC`\\?\` ( `\\.\`) i prefiks ścieżki urządzenia dla ścieżek urządzenia ( lub ).

### <a name="trimming-characters"></a>Przycinanie znaków

Wraz z przebiegami separatorów i segmentów względnych usuniętych wcześniej, niektóre dodatkowe znaki są usuwane podczas normalizacji:

- Jeśli segment kończy się w jednym okresie, ten okres jest usuwany. (Segment pojedynczego lub podwójnego okresu jest znormalizowany w poprzednim kroku. Segment trzech lub więcej okresów nie jest znormalizowany i w rzeczywistości jest prawidłową nazwą pliku/katalogu).

- Jeśli ścieżka nie kończy się w separatorze, wszystkie końcowe okresy i spacje (U +0020) są usuwane. Jeśli ostatni segment jest po prostu pojedynczylub podwójny okres, podlega względnej reguły składników powyżej.

   Ta reguła oznacza, że można utworzyć nazwę katalogu z spacją końcowe, dodając separator końcowy po spację.

   > [!IMPORTANT]
   > Nigdy **nie** należy tworzyć katalogu lub nazwy pliku z spacją końcowej. Spacje końcowe mogą utrudniać lub uniemożliwiać dostęp do katalogu, a aplikacje często nie mogą obsługiwać katalogów lub plików, których nazwy zawierają spacje końcowe.

## <a name="skipping-normalization"></a>Pomijanie normalizacji

Zwykle każda ścieżka przekazana do interfejsu API systemu Windows jest (skutecznie) przekazywana do [funkcji GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) i znormalizowana. Jest jeden ważny wyjątek: ścieżka urządzenia, która zaczyna się od znaku zapytania zamiast kropki. Chyba że ścieżka `\\?\` zaczyna się dokładnie od (zwróć uwagę na użycie kanonicznego ukośnika odwrotnego), jest znormalizowana.

Dlaczego chcesz pominąć normalizację? Istnieją trzy główne powody:

1. Aby uzyskać dostęp do ścieżek, które są zwykle niedostępne, ale są legalne. Plik lub katalog `hidden.`o nazwie , na przykład, jest niemożliwe do uzyskania dostępu w jakikolwiek inny sposób.

1. Aby zwiększyć wydajność, pomijając normalizację, jeśli już znormalizowano.

1. Tylko w ramach .NET Framework, aby pominąć `MAX_PATH` sprawdzanie długości ścieżki, aby umożliwić ścieżki, które są większe niż 259 znaków. Większość interfejsów API zezwala na to, z pewnymi wyjątkami.

> [!NOTE]
> Program .NET Core obsługuje długie ścieżki `MAX_PATH` niejawnie i nie wykonuje czeku. Sprawdzanie `MAX_PATH` dotyczy tylko .NET Framework.

Pomijanie normalizacji i max sprawdzanie ścieżki jest jedyną różnicą między składnią dwóch ścieżek urządzenia; w przeciwnym razie są identyczne. Należy zachować ostrożność podczas pomijania normalizacji, ponieważ można łatwo tworzyć ścieżki, które są trudne do radzenia sobie z "normalnymi" aplikacjami.

Ścieżki, `\\?\` które zaczynają się nadal są znormalizowane, jeśli jawnie przekazać je do [GetFullPathName funkcji](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).

Ścieżki o więcej `MAX_PATH` niż znakach można `\\?\`przekazywać do [getfullpathname](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) bez . Obsługuje ścieżki dowolnej długości do maksymalnego rozmiaru ciągu, który może obsłużyć system Windows.

## <a name="case-and-the-windows-file-system"></a>Sprawa i system plików Systemu Windows

Osobliwością systemu plików Systemu Windows, że użytkownicy i deweloperzy spoza systemu Windows znaleźć mylące jest to, że ścieżki i nazwy katalogów są bez uwzględniania wielkości liter. Oznacza to, że nazwy katalogów i plików odzwierciedlają obudowę ciągów używanych podczas ich tworzenia. Na przykład wywołanie metody

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

tworzy katalog o nazwie TeStDiReCtOrY. Jeśli zmienisz nazwę katalogu lub pliku, aby zmienić jego sprawę, katalog lub nazwa pliku odzwierciedla przypadek ciągu używanego podczas zmiany jego nazwy. Na przykład poniższy kod zmienia nazwę pliku o nazwie test.txt na Test.txt:

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

Jednak porównania nazw katalogów i plików są niewrażliwe na wielkość liter. Jeśli szukasz pliku o nazwie "test.txt", interfejsy API systemu plików .NET ignorują przypadek w porównaniu. Test.txt, TEST. TXT, test. TXT i każda inna kombinacja wielkich i małych liter będzie zgodna z "test.txt".
