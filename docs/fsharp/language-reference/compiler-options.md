---
title: Opcje kompilatora (F#)
description: Użyj F# opcje wiersza polecenia kompilatora do kontrolowania kompilacji usługi F# aplikacji i bibliotek.
ms.date: 12/10/2018
ms.openlocfilehash: dafd872a22bf4ec4b36910f28b7c5bfe9370af8d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170876"
---
# <a name="compiler-options"></a>Opcje kompilatora

W tym temacie opisano opcje wiersza polecenia kompilatora dla F# kompilatora, fsc.exe. Środowisko kompilacji można także kontrolować przez ustawienie właściwości projektu.


## <a name="compiler-options-listed-alphabetically"></a>Opcje kompilatora w porządku alfabetycznym
W poniższej tabeli przedstawiono opcje kompilatora w porządku alfabetycznym. Niektóre z F# opcje kompilatora są podobne do C# opcje kompilatora. Jeśli tak jest łącze do C# podano tematu o opcjach kompilatora.



|— Opcja kompilatora|Opis|
|---------------|-----------|
|`-a filename.fs`|Generuje bibliotekę z określonego pliku. Ta opcja jest krótką formą `--target:library filename.fs`.|
|`--baseaddress:address`|Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;baseaddress &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|`--codepage:id`|Określa stronę kodową do użycia podczas kompilacji, jeśli strona wymagany jest bieżący domyślną stroną kodową systemu.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;strony kodowe &#40;C&#35; opcje kompilatora&#41;](../../csharp/language-reference/compiler-options/codepage-compiler-option.md).|
|`--consolecolors`|Określa, że błędy i ostrzeżenia używają kolorowego tekstu na konsoli.|
|`--crossoptimize[+|-]`|Włącza lub wyłącza optymalizacje między modułami.|
|<code>--delaysign[+&#124;-]</code>|Podpisuje testowo opóźnienie zestawie, używając tylko publicznej części klucza silnej nazwy.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;delaysign &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|<code>--checked[+&#124;-]</code>|Włącza lub wyłącza Generowanie sprawdzenia przepełnienia.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;zaznaczone &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|<code>--debug[+&#124;-]</code><br /><br /><code>-g[+&#124;-]</code><br /><br /><code>--debug:[full&#124;pdbonly]</code><br /><br /><code>-g: [full&#124;pdbonly]</code>|Włącza lub wyłącza generowanie informacji debugowania lub określa rodzaj informacji debugowania do wygenerowania. Wartość domyślna jest pełna, co umożliwia dołączanie do uruchomionego programu. Wybierz **pdbonly** uzyskać ograniczone informacje debugowania przechowywane w pliku pdb (bazy danych programu).<br /><br />Odpowiednikiem C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz artykuł<br /><br />[&#47;debugowanie &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/8cw0bt21.aspx).|
|`--define:symbol`<br /><br />`-d:symbol`|Definiuje symbol do użytku w kompilacji warunkowej.|
|<code>--deterministic[+&#124;-]</code>|Tworzy zestaw deterministyczny (w tym identyfikator GUID wersji modułu i sygnaturę czasową). Ta opcja nie można używać symboli wieloznacznych, numery wersji i obsługuje tylko przenośne i osadzone typy debugowania|
|`--doc:xmldoc-filename`|Nakazuje kompilatorowi Generowanie komentarzy dokumentacji XML do określonego pliku. Aby uzyskać więcej informacji, zobacz [dokumentacji XML](xml-documentation.md).<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;doc &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|`--fullpaths`|Nakazuje kompilatorowi Generowanie ścieżek w pełni kwalifikowanych.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;fullpaths — &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/d315xc66.aspx).|
|`--help`<br /><br />`-?`|Wyświetla informacje o użyciu, w tym krótki opis wszystkich opcji kompilatora.|
|<code>--highentropyva[+&#124;-]</code>|Włącz lub wyłącz randomizacji układu przestrzeni adresowej o wysokiej entropii (ASLR), udoskonaloną funkcję zabezpieczeń. System operacyjny wybiera losowo lokalizacje w pamięci, w której są załadowane infrastruktury dla aplikacji (na przykład stos i sterta). Jeśli ta opcja jest włączona, systemów operacyjnych można używać tego generowania losowego używania pełnej 64-bitowej przestrzeni adresowej na komputerze 64-bitowym.|
|`--keycontainer:key-container-name`|Określa kontener klucza silnej nazwy.|
|`--keyfile:filename`|Określa nazwę pliku klucza publicznego do podpisywania wygenerowanego zestawu.|
|`--lib:folder-name`<br /><br />`-I:folder-name`|Określa katalog, które mają być wyszukiwane zestawów, które są określone.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;lib &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|`--linkresource:resource-info`|Łączy określony zasób do zestawu. Format zasobu informacyjnego to <code>filename[name[public&#124;private]]</code><br /><br />Łączenie pojedynczego zasobu z tą opcją jest alternatywą dla osadzania całego pliku zasobu z `--resource` opcji.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;linkresource &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|`--mlcompatibility`|Ignoruje ostrzeżeń, które są wyświetlane, gdy używasz funkcji, które są przeznaczone dla zachowania zgodności z innymi wersjami Metajęzyka.|
|`--noframework`|Wyłącza domyślne odwołanie do zestawu .NET Framework.|
|`--nointerfacedata`|Nakazuje kompilatorowi pominąć zasób zazwyczaj dodawany do zestawu, który zawiera F#-określonych metadanych.|
|`--nologo`|Nie wyświetla tekst transparentu przy uruchamianiu kompilatora.|
|`--nooptimizationdata`|Nakazuje kompilatorowi uwzględnić jedynie optymalizację niezbędną dla wdrożenia wbudowanych konstrukcji. Hamuje Wbudowywanie między wbudowanie, ale poprawia zgodność binarną.|
|`--nowin32manifest`|Nakazuje kompilatorowi pominąć domyślny manifest Win32.|
|`--nowarn:warning-number-list`|Wyłącza określone ostrzeżenia uporządkowane według numerów. Oddzielaj numery ostrzeżenia za pomocą przecinków. Możesz odkryć numer ostrzeżenia dla dowolnego ostrzeżenia z wyników kompilacji.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;nowarn &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|<code>--optimize[+&#124;-][optimization-option-list]</code><br /><br /><code>-O[+&#124;-] [optimization-option-list]</code>|Włącza lub wyłącza optymalizacje. Niektóre opcje optymalizacji może zostać wyłączone lub włączane selektywnie, przez wymienienie ich. Są to: `nojitoptimize`, `nojittracking`, `nolocaloptimize`, `nocrossoptimize`, `notailcalls`.|
|`--out:output-filename`<br /><br />`-o:output-filename`|Określa nazwę skompilowanego zestawu lub modułu.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;się &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|`--pdb:pdb-filename`|Nazywa plik wyjściowy debugowania PDB (bazy danych programu). Ta opcja ma zastosowanie tylko jeśli `--debug` jest włączona.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;pdb &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/ms228625.aspx).|
|`--platform:platform-name`|Określa, że wygenerowany kod będzie działał tylko na określonej platformie (`x86`, `Itanium`, lub `x64`), lub jeśli nazwa platformy `anycpu` jest wybrany, określa, że wygenerowany kod może działać na dowolnej platformie.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;platformy &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|`--preferreduilang:lang`| Określa nazwę preferowanego języka wyjściowego kultury (na przykład `es-ES`, `ja-JP`). |
|`--quotations-debug`|Określa, że dodatkowe informacje dotyczące debugowania powinny być emitowane dla wyrażeń, które są uzyskiwane z F# literałów oferty i odbitych definicje. Informacje debugowania są dodawane do atrybutów niestandardowych F# węzła drzewa wyrażeń. Zobacz [kodu ofert](code-quotations.md) i [Expr.customattributes —](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|`--reference:assembly-filename`<br /><br />`-r:assembly-filename`|Sprawia, że kod z F# lub zestawu .NET Framework, które są dostępne dla kodu kompilowanego.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;odwołania &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|`--resource:resource-filename`|Osadza plik zasobów zarządzanych w generowanym zestawie.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;zasobów &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|`--sig:signature-filename`|Generuje plik podpisu oparty na wygenerowanym zestawie. Aby uzyskać więcej informacji na temat plików sygnatur, zobacz [podpisy](signatures.md).|
|`--simpleresolution`|Określa, że odwołania do zestawów powinny zostać rozpoznany przy użyciu reguły Mono opartej na katalogu, a nie rozdzielczości MSBuild. Wartość domyślna ma używać rozdzielczości MSBuild, z wyjątkiem przypadków uruchomienia w Mono.|
|`--standalone`|Określa, aby utworzyć zestaw, który zawiera wszystkie jego zależności, aby była uruchamiana przez siebie bez konieczności stosowania dodatkowych zestawów, takich jak F# biblioteki.|
|`--staticlink:assembly-name`|Statycznie łączy dany zestaw i wszystkie powiązane biblioteki dll, które są zależne od tego zestawu. Użyj nazwy zestawu, a nie nazwy biblioteki DLL.|
|`--subsystemversion`|Określa numer wersji podsystemu systemu operacyjnego, który będzie używany przez wygenerowany plik wykonywalny. Użyj 6.02 dla Windows 8.1, 6.01 dla Windows 7, 6.00 dla Windows Vista. Ta opcja tylko ma zastosowanie do plików wykonywalnych, nie dll i musi być używana jedynie, jeśli aplikacja jest zależna od specjalnych funkcji zabezpieczeń dostępnych tylko w niektórych wersjach systemu operacyjnego. Jeśli ta opcja jest używana, a użytkownik usiłuje uruchomić aplikację na niższej wersji systemu operacyjnego, zakończy się niepowodzeniem z komunikatem o błędzie.|
|<code>--tailcalls[+&#124;-]</code>|Włącza lub wyłącza korzystanie z fragmentarycznej instrukcji IL, co powoduje, że ramek stosu, można użyć ponownie dla funkcji cyklicznych. Ta opcja jest domyślnie włączona.|
|<code>--target:[exe&#124;winexe&#124;library&#124;module] filename</code>|Określa typ i nazwa pliku wygenerowanego kodu skompilowanego.<ul><li>`exe` oznacza aplikację konsoli.<br /></li><li>`winexe` oznacza aplikację Windows, która różni się od aplikacji konsoli tym, że nie ma standardowych strumieni wejścia/wyjścia (stdin, stdout i stderr) zdefiniowany.<br /></li><li>`library` jest to zestaw bez punktu wejścia.<br /></li><li>`module` jest modułem środowiska .NET Framework (.netmodule), który później może być połączony z innymi modułami w zestaw.<br /></li><ul/>Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;docelowej &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|`--times`|Wyświetla czas kompilowania informacji.|
|`--utf8output`|Umożliwia drukowanie danych wyjściowych kompilatora przy użyciu kodowania UTF-8.|
|`--warn:warning-level`|Ustaw poziom ostrzeżenia (0-5). Poziomem domyślnym jest 3. Każde ostrzeżenie jest generowane w oparciu o jego ważność. Poziom 5 daje więcej, ale mniej surowych, ostrzeżeń niż poziom 1.<br /><br />Ostrzeżeniami poziomu 5 są: 21 (użycie cykliczne sprawdzane w czasie wykonywania), 22 (`let rec` obliczane poza kolejnością), 45 (pełna Abstrakcja) i 52 (kopia obronna). Wszystkie inne ostrzeżenia to poziom 2.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;Ostrzegaj &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|`--warnon:warning-number-list`|Włącz określone ostrzeżenia, które mogą być domyślnie wyłączone lub wyłączone przez inną opcję wiersza polecenia. W F# 3.0 tylko ostrzeżenie 1182 (o nieużywanych zmiennych) jest domyślnie wyłączona.|
|<code>--warnaserror[+&#124;-] [warning-number-list]</code>|Włącza lub wyłącza opcję zgłaszania ostrzeżeń jako błędów. Możesz zapewnić specjalne numery ostrzeżeń, które mają być wyłączone lub włączone. Opcje później w wierszu polecenia zastępują opcje wcześniej w wierszu polecenia. Na przykład, aby określić, które nie mają być zgłaszane jako błędy ostrzeżenia, należy określić `--warnaserror+` `--warnaserror-:warning-number-list`.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;warnaserror &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|`--win32manifest:manifest-filename`|Dodaje plik manifestu Win32 do kompilacji. Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;win32manifest &#40;C&#35; opcje kompilatora&#41;](https://msdn.microsoft.com/library/bb545961.aspx).|
|`--win32res:resource-filename`|Dodaje plik zasobów Win32 do kompilacji.<br /><br />Ta opcja kompilatora jest równoważna C# — opcja kompilatora o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [ &#47;win32res (&#40;k & #35); Opcje kompilatora&#41;](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-articles"></a>Pokrewne artykuły:


|Tytuł|Opis|
|-----|-----------|
|[Opcje F# Interactive](fsharp-interactive-options.md)|W tym artykule opisano opcje wiersza polecenia obsługiwane przez F# interpreter, fsi.exe.|
|[Odwołanie do właściwości projektu](/visualstudio/ide/reference/project-properties-reference)|W tym artykule opisano interfejs użytkownika dla projektów, w tym stron właściwości projektu, które udostępniają opcje budowania.|
