---
title: Formaty ścieżek plików w systemie Windows
description: Ten artykuł zawiera informacje o formatach ścieżek plików w systemach Windows, takich jak tradycyjne ścieżki DOS, ścieżki urządzeń systemu DOS i ścieżki UNC (Universal Naming Convention).
ms.date: 06/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
ms.openlocfilehash: 2d3ede97b372dd8922a10a377f69155a12f88bda
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447137"
---
# <a name="file-path-formats-on-windows-systems"></a>Formaty ścieżek plików w systemie Windows

Elementy członkowskie wielu typów w <xref:System.IO> przestrzeni nazw zawierają `path` parametr, który pozwala określić ścieżkę bezwzględną lub względną do zasobu systemu plików. Ta ścieżka jest następnie przesyłana do [interfejsów API systemu plików Windows](/windows/desktop/fileio/file-systems). W tym temacie omówiono formaty ścieżek plików, których można używać w systemach Windows.

## <a name="traditional-dos-paths"></a>Tradycyjne ścieżki DOS

Standardowa ścieżka DOS może składać się z trzech składników:

- Litera woluminu lub dysku, po którym następuje separator woluminu ( `:` ).
- Nazwa katalogu. [Znak separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela podkatalogi w hierarchii katalogów zagnieżdżonych.
- Opcjonalna nazwa pliku. [Znak separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela ścieżkę pliku i nazwę pliku.

Jeśli wszystkie trzy składniki są obecne, ścieżka jest bezwzględna. Jeśli nie określono woluminu ani litery dysku, a nazwa katalogu rozpoczyna się od [znaku separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>), ścieżka jest określana względem katalogu głównego bieżącego dysku. W przeciwnym razie ścieżka jest określana względem bieżącego katalogu. W poniższej tabeli przedstawiono niektóre możliwe ścieżki katalogów i plików.

|Ścieżka  |Opis  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Bezwzględna ścieżka pliku z katalogu głównego dysku C: |
| `\Program Files\Custom Utilities\StringFinder.exe` | Ścieżka bezwzględna z katalogu głównego bieżącego dysku. |
| `2018\January.xlsx` | Ścieżka względna do pliku w podkatalogu bieżącego katalogu. |
| `..\Publications\TravelBrochure.pdf` | Ścieżka względna do pliku w katalogu, który jest elementem równorzędnym bieżącego katalogu. |
| `C:\Projects\apilibrary\apilibrary.sln` | Ścieżka bezwzględna do pliku z katalogu głównego dysku C: |
| `C:Projects\apilibrary\apilibrary.sln` | Ścieżka względna z bieżącego katalogu dysku C:. |

> [!IMPORTANT]
> Zwróć uwagę na różnicę między ostatnimi dwiema ścieżkami. Oba określają opcjonalny specyfikator woluminu (C: w obu przypadkach), ale pierwszy zaczyna się od elementu głównego określonego woluminu, a drugi nie. W związku z tym pierwsza jest ścieżką bezwzględną z katalogu głównego dysku C:, a druga jest ścieżką względną z bieżącego katalogu dysku C:. Użycie drugiego formularza, gdy pierwszy jest zamierzony, jest wspólnym źródłem błędów, które obejmują ścieżki plików systemu Windows.

Można określić, czy ścieżka pliku jest w pełni kwalifikowana (to znaczy, czy ścieżka jest niezależna od bieżącego katalogu i nie ulega zmianie, gdy bieżący katalog ulegnie zmianie) przez wywołanie <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> metody. Należy zauważyć, że taka ścieżka może zawierać względne segmenty katalogów ( `.` i `..` ) i nadal być w pełni kwalifikowane, jeśli rozpoznana ścieżka zawsze wskazuje tę samą lokalizację.

Poniższy przykład ilustruje różnicę między ścieżkami bezwzględnymi i względnymi. Przyjęto założenie, że katalog D:\FY2018\ istnieje i nie ustawił bieżącego katalogu dla D:\ w wierszu polecenia przed uruchomieniem przykładu.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="unc-paths"></a>Ścieżki UNC

Ścieżki Universal Naming Convention (UNC), które są używane do uzyskiwania dostępu do zasobów sieciowych, mają następujący format:

- Nazwa serwera lub hosta, który jest poprzedzony przez \\ \\ . Nazwa serwera może być nazwą maszyny NetBIOS lub adresem IP/FQDN (obsługiwane są również adresy IPv4 i V6).
- Nazwa udziału, która jest oddzielona od nazwy hosta przez \\ . Razem serwer i nazwa udziału tworzą wolumin.
- Nazwa katalogu. [Znak separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela podkatalogi w hierarchii katalogów zagnieżdżonych.
- Opcjonalna nazwa pliku. [Znak separatora katalogu](<xref:System.IO.Path.DirectorySeparatorChar>) oddziela ścieżkę pliku i nazwę pliku.

Poniżej przedstawiono kilka przykładów ścieżek UNC:

|Ścieżka  |Opis  |
| -- | -- |
| `\\system07\C$\` | Katalog główny dysku C: na `system07` . |
| `\\Server2\Share\Test\Foo.txt` | Plik foo. txt w katalogu testu \\ \\ \\ woluminu udziału serwer2.|

Ścieżki UNC muszą zawsze być w pełni kwalifikowane. Mogą one zawierać względne segmenty katalogów ( `.` i `..` ), ale muszą być częścią w pełni kwalifikowanej ścieżki. Ścieżek względnych można używać tylko przez mapowanie ścieżki UNC na literę dysku.

## <a name="dos-device-paths"></a>Ścieżki urządzeń DOS

System operacyjny Windows ma ujednolicony model obiektów, który wskazuje na wszystkie zasoby, w tym pliki. Te ścieżki obiektów są dostępne z okna konsoli i są widoczne dla warstwy Win32 za pośrednictwem specjalnego folderu linków symbolicznych, do których są mapowane starsze ścieżki DOS i UNC. Dostęp do tego folderu specjalnego uzyskuje się za pośrednictwem składni ścieżki urządzenia DOS, która jest jedną z:

`\\.\C:\Test\Foo.txt`
`\\?\C:\Test\Foo.txt`

Oprócz identyfikowania dysku za pomocą jego litery dysku, można zidentyfikować wolumin przy użyciu identyfikatora GUID woluminu. Ma to formę:

`\\.\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`
`\\?\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`

> [!NOTE]
> Składnia ścieżki urządzenia DOS jest obsługiwana w implementacjach platformy .NET działających w systemie Windows, począwszy od platformy .NET Core 1,1 i .NET Framework 4.6.2.

Ścieżka urządzenia DOS składa się z następujących składników:

- Specyfikator ścieżki urządzenia ( `\\.\` lub `\\?\` ), który identyfikuje ścieżkę jako ścieżkę urządzenia DOS.

   > [!NOTE]
   > `\\?\`Jest obsługiwane we wszystkich wersjach programu .NET Core i w .NET Framework, począwszy od wersji 4.6.2.

- Symboliczny link do obiektu urządzenia "Real" (C: w przypadku nazwy dysku lub woluminu {b75e2c83-0000-0000-0000-602f00000000} w przypadku identyfikatora GUID woluminu).

   Pierwszy segment ścieżki urządzenia DOS po specyfikator ścieżki urządzenia identyfikuje wolumin lub dysk. (Na przykład `\\?\C:\` i `\\.\BootPartition\` .)

   Istnieje konkretne łącze dla UNCs o nazwie, a nie Surprisingly, `UNC` . Przykład:

  `\\.\UNC\Server\Share\Test\Foo.txt`
  `\\?\UNC\Server\Share\Test\Foo.txt`

    W przypadku urządzenia UNCs część serwer/udział tworzy wolumin. Na przykład, w programie `\\?\server1\e:\utilities\\filecomparer\` , część serwer/udział jest server1\utilities. Jest to istotne w przypadku wywołania metody, takiej jak <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> w przypadku względnych segmentów katalogu; nigdy nie jest możliwe przechodzenie poza wolumin.

Ścieżki urządzeń systemu DOS są w pełni kwalifikowane według definicji. Względne segmenty katalogu ( `.` i `..` ) są niedozwolone. Bieżące katalogi nigdy nie są wprowadzane do ich użycia.

## <a name="example-ways-to-refer-to-the-same-file"></a>Przykład: sposoby odwoływania się do tego samego pliku

Poniższy przykład ilustruje niektóre sposoby odwoływania się do pliku w przypadku używania interfejsów API w <xref:System.IO> przestrzeni nazw. Przykład tworzy wystąpienie <xref:System.IO.FileInfo> obiektu i używa jego <xref:System.IO.FileInfo.Name> właściwości i, <xref:System.IO.FileInfo.Length> Aby wyświetlić nazwę pliku i długość plików.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Normalizacja ścieżki

Prawie wszystkie ścieżki przesyłane do interfejsów API systemu Windows są znormalizowane. Podczas normalizacji system Windows wykonuje następujące czynności:

- Identyfikuje ścieżkę.
- Stosuje bieżący katalog do częściowo kwalifikowanych (względnych) ścieżek.
- Separatory składników Canonicalizes i katalogów.
- Oblicza składniki katalogu względnego ( `.` dla bieżącego katalogu i `..` dla katalogu nadrzędnego).
- Przycina określone znaki.

Ta normalizacja występuje niejawnie, ale można ją jawnie, wywołując <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> metodę, która zawija wywołanie [funkcji GetFullPathName ()](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea). Możesz również wywołać [funkcję GetFullPathName systemu Windows ()](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) bezpośrednio przy użyciu metody P/Invoke.

### <a name="identifying-the-path"></a>Identyfikowanie ścieżki

Pierwszy krok w normalizacji ścieżki identyfikuje typ ścieżki. Ścieżki mieszczą się w jednej z kilku kategorii:

- Są to ścieżki urządzeń; oznacza to, że zaczynają się od dwóch separatorów i znaku zapytania lub kropki ( `\\?` lub `\\.` ).
- Są to ścieżki UNC; oznacza to, że zaczynają się od dwóch separatorów bez znaku zapytania lub kropki.
- Są to w pełni kwalifikowane ścieżki DOS; oznacza to, że zaczynają się literą dysku, separatorem woluminu i separatorem składników ( `C:\` ).
- Wyznaczy starsze urządzenie ( `CON` , `LPT1` ).
- Są one względne dla katalogu głównego bieżącego dysku; oznacza to, że zaczynają się od pojedynczego separatora składnika ( `\` ).
- Są one względne wobec bieżącego katalogu określonego dysku; oznacza to, że zaczynają się literą dysku, separatorem woluminów i bez separatora składników ( `C:` ).
- Są one względne wobec bieżącego katalogu; oznacza to, że zaczynają się one jakimkolwiek innym ( `temp\testfile.txt` ).

Typ ścieżki Określa, czy bieżący katalog jest stosowany w jakiś sposób. Określa również, jak "root" ścieżki.

### <a name="handling-legacy-devices"></a>Obsługa starszych urządzeń

Jeśli ścieżka to starsze urządzenie systemu DOS, takie jak `CON` , `COM1` lub, `LPT1` jest konwertowane na ścieżkę urządzenia, w zależności od tego `\\.\` i zwraca.

Ścieżka rozpoczynająca się od starszej nazwy urządzenia jest zawsze interpretowana jako starsze urządzenie przez <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> metodę. Na przykład ścieżka urządzenia DOS dla systemu `CON.TXT` ma wartość `\\.\CON` , a ścieżka urządzenia DOS dla systemu `COM1.TXT\file1.txt` to `\\.\COM1` .

### <a name="applying-the-current-directory"></a>Stosowanie bieżącego katalogu

Jeśli ścieżka nie jest w pełni kwalifikowana, system Windows stosuje bieżący katalog. UNCs i ścieżki urządzeń nie mają zastosowanego bieżącego katalogu. Ani nie pełni dysku z separatorem C: \\ .

Jeśli ścieżka rozpoczyna się od pojedynczego separatora składnika, zostanie zastosowany dysk z bieżącego katalogu. Na przykład jeśli ścieżka pliku jest `\utilities` i bieżącym katalogiem jest `C:\temp\` , normalizacja produkuje `C:\utilities` .

Jeśli ścieżka rozpoczyna się od litery dysku, separatora woluminu i bez separatora składników, zostanie zastosowany ostatni bieżący zestaw katalogów z powłoki poleceń dla określonego dysku. Jeśli ostatni bieżący katalog nie został ustawiony, tylko dysk zostanie zastosowany. Na przykład, jeśli ścieżka pliku to `D:sources` , bieżący katalog jest `C:\Documents\` i ostatni bieżący katalog na dysku D: `D:\sources\` is, wynik to `D:\sources\sources` . Te ścieżki "względne" dysku są typowym źródłem błędów logiki programu i skryptów. Przy założeniu, że ścieżka rozpoczynająca się od litery i dwukropka nie jest poprawna.

Jeśli ścieżka zaczyna się od czegoś innego niż separator, zostanie zastosowany bieżący dysk i bieżący katalog. Na przykład jeśli ścieżka jest `filecompare` i bieżącym katalogiem jest `C:\utilities\` , wynik jest `C:\utilities\filecompare\` .

> [!IMPORTANT]
> Ścieżki względne są niebezpieczne w aplikacjach wielowątkowych (czyli większości aplikacji), ponieważ bieżący katalog jest ustawieniem dla procesu. Dowolny wątek może zmienić bieżący katalog w dowolnym momencie. Począwszy od platformy .NET Core 2,1, można wywołać <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> metodę, aby uzyskać ścieżkę bezwzględną ze ścieżki względnej i ścieżkę bazową (bieżący katalog), dla której chcesz rozwiązać ten problem.

### <a name="canonicalizing-separators"></a>Separatory formę kanoniczną działa

Wszystkie ukośniki ( `/` ) są konwertowane na standardowy separator systemu Windows, ukośnik odwrotny ( `\` ). Jeśli są obecne, Seria ukośników, które są zgodne z dwoma ukośnikami, jest zwiniętych na pojedynczy ukośnik.

### <a name="evaluating-relative-components"></a>Ocenianie składników względnych

W miarę przetwarzania ścieżki są oceniane wszystkie składniki lub segmenty składające się z pojedynczego lub podwójnego okresu ( `.` lub `..` ):

- W przypadku pojedynczego okresu bieżący segment jest usuwany, ponieważ odnosi się do bieżącego katalogu.

- W przypadku podwójnego okresu bieżący segment i segment nadrzędny są usuwane, ponieważ podwójny okres odwołuje się do katalogu nadrzędnego.

   Katalogi nadrzędne są usuwane tylko wtedy, gdy nie znajdują się poza katalogiem głównym ścieżki. Katalog główny ścieżki zależy od typu ścieżki. Jest to dysk ( `C:\` ) dla ścieżek DOS, serwer/udział dla UNCs ( `\\Server\Share` ) oraz prefiks ścieżki urządzenia dla ścieżek urządzeń ( `\\?\` lub `\\.\` ).

### <a name="trimming-characters"></a>Przycinanie znaków

Wraz z uruchomieniami separatorów i segmentów względnych usuniętych wcześniej niektóre dodatkowe znaki są usuwane podczas normalizacji:

- Jeśli segment zostanie zakończony w pojedynczym okresie, ten okres jest usuwany. (Segment pojedynczego lub podwójnego okresu jest znormalizowany w poprzednim kroku. Segment trzech lub więcej okresów nie jest znormalizowany i jest w rzeczywistości prawidłową nazwą pliku/katalogu.

- Jeśli ścieżka nie kończy się separatorem, wszystkie końcowe kropki i spacje (U + 0020) są usuwane. Jeśli ostatni segment jest po prostu pojedynczym lub podwójnym okresem, jest on objęty powyższą regułą składników względnych.

   Ta reguła oznacza, że można utworzyć nazwę katalogu z końcowym miejscem, dodając separator końcowy po odstępie.

   > [!IMPORTANT]
   > **Nigdy nie** należy tworzyć katalogów ani nazw plików z końcowym miejscem. Spacje końcowe mogą być trudne lub niemożliwe do uzyskania dostępu do katalogu, a aplikacje często kończą się niepowodzeniem podczas próby obsługi katalogów lub plików, których nazwy zawierają spacje końcowe.

## <a name="skipping-normalization"></a>Pomijanie normalizacji

Zwykle wszystkie ścieżki przesłane do interfejsu API systemu Windows są (efektywnie) przesyłane do [funkcji GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) i znormalizowane. Istnieje jeden ważny wyjątek: ścieżka urządzenia rozpoczynająca się od znaku zapytania zamiast kropki. Chyba że ścieżka zaczyna się dokładnie od `\\?\` (należy zwrócić uwagę na użycie kanonicznego ukośnika odwrotnego), jest znormalizowana.

Dlaczego chcesz pominąć normalizację? Istnieją trzy główne przyczyny:

1. Aby uzyskać dostęp do ścieżek, które są zwykle niedostępne, ale są dozwolone. Plik lub katalog o nazwie `hidden.` , na przykład, jest niemożliwe do uzyskania dostępu w inny sposób.

1. Aby poprawić wydajność dzięki pominięciu normalizacji, jeśli został już znormalizowany.

1. Tylko na .NET Framework, aby pominąć `MAX_PATH` Sprawdzanie długości ścieżki, aby umożliwić używanie ścieżek, które są dłuższe niż 259 znaków. Większość interfejsów API zezwala na to, z pewnymi wyjątkami.

> [!NOTE]
> Program .NET Core obsługuje długie ścieżki niejawnie i nie `MAX_PATH` sprawdza. `MAX_PATH`Sprawdzanie dotyczy tylko .NET Framework.

Pomijanie normalizacji i maksymalne sprawdzanie ścieżki jest jedyną różnicą między dwiema składnią ścieżki urządzenia; są one identyczne. Należy zachować ostrożność w przypadku pominięcia normalizacji, ponieważ można łatwo tworzyć ścieżki, które są trudne do rozpatrzenia "normalnych" aplikacji.

Ścieżki rozpoczynające `\\?\` się od są ciągle znormalizowane, jeśli zostały jawnie przekazane do [funkcji GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).

Można przekazać ścieżki zawierające więcej niż `MAX_PATH` znaków do [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) bez `\\?\` . Obsługuje ona dowolne ścieżki długości do maksymalnego rozmiaru ciągu, który może obsłużyć system Windows.

## <a name="case-and-the-windows-file-system"></a>Wielkość liter i system plików Windows

Specyficzna dla systemu Windows system plików, który nie jest przeznaczony dla użytkowników i deweloperów, jest mylący, ponieważ nazwy ścieżek i katalogów nie uwzględniają wielkości liter. Oznacza to, że nazwy katalogów i plików odzwierciedlają wielkość liter ciągów używanych podczas tworzenia. Na przykład wywołanie metody

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

tworzy katalog o nazwie TeStDiReCtOrY. Jeśli zmienisz nazwę katalogu lub pliku, aby zmienić jego wielkość liter, nazwa katalogu lub pliku odzwierciedla wielkość liter w ciągu używanym podczas zmiany nazwy. Na przykład poniższy kod zmienia nazwę pliku o nazwie test. txt na test. txt:

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

Jednak porównania nazw katalogów i plików nie uwzględniają wielkości liter. W przypadku wyszukiwania pliku o nazwie "test. txt" interfejsy API systemu plików platformy .NET ignorują wielkość liter w porównaniu. Test. txt, TEST. TXT, test. TXT i wszystkie inne kombinacje wielkich i małych liter będą zgodne z "test. txt".
