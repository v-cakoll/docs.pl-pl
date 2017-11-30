---
title: Opcje kompilatora (F#)
description: "F # kompilatora wiersza polecenia opcje umożliwiają kontrolowanie kompilacji F # aplikacji i bibliotek."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c797cf0b-5953-4053-8626-0558e9eaf10f
ms.openlocfilehash: 0857418141a2383795d736fd507fcab5dbeaba24
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="compiler-options"></a>Opcje kompilatora

W tym temacie opisano opcje wiersza polecenia kompilatora kompilator języka F # fsc.exe. Środowisko kompilacji można także kontrolować przez ustawienie właściwości projektu.


## <a name="compiler-options-listed-alphabetically"></a>Opcje kompilatora w porządku alfabetycznym
W poniższej tabeli przedstawiono opcje kompilatora w porządku alfabetycznym. Niektóre opcje kompilatora F # są podobne do opcje kompilatora C#. Jeśli tak jest, zostanie podane łącze do tematu opcje kompilatora C#.



|— Opcja kompilatora|Opis|
|---------------|-----------|
|**-***&lt;nazwa pliku wyjściowego&gt;**|Generuje biblioteki i określa jego nazwę. Ta opcja jest krótka forma **--docelowych: Biblioteka ***&lt;filename&gt;**.|
|**-baseaddress:&lt;ciągu&gt;**|Określa adres podstawowy biblioteki, który ma zostać utworzony.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; baseaddress &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/2fdbz5xd.aspx).|
|**-codepage:&lt;int&gt;**|Określa stronę kodową używaną do odczytu plików źródłowych.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; codepage &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/w0kyekyh.aspx).|
|**--consolecolors**|Określa, że błędy i ostrzeżenia używać tekstu kolorowania na konsoli.|
|**crossoptimize —**[**+**&#124; **-**]|Włącza lub wyłącza optymalizacje między modułami.|
|**--delaysign**[**+**&#124; **-**]|Znaki opóźnienie zestawie, używając tylko publicznej części klucza silnej nazwy.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; delaysign &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/ta1sxwy8.aspx).|
|**--zaznaczone**[**+**&#124; **-**]|Włącza lub wyłącza Generowanie sprawdzanie nadmiaru dla operacji.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; zaznaczone &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/h25wtyxf.aspx).|
|**--debug**[**+**&#124; **-**]<br /><br />**-g**[**+**&#124; **-**]<br /><br />**--debug**: [**pełne**&#124; **pdbonly**]<br /><br />**-g:** [**pełne**&#124; **pdbonly**]|Włącza lub wyłącza generowanie informacji o debugowaniu lub określa typ informacji o debugowaniu do wygenerowania. Wartość domyślna jest pełna, która umożliwia dołączanie do uruchomionego programu. Wybierz **pdbonly** można uzyskać ograniczone informacje debugowania przechowywane w pliku pdb (bazy danych programu).<br /><br />Odpowiednik opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz<br /><br />[&#47; debugowania &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/8cw0bt21.aspx).|
|**— Zdefiniuj:&lt;ciągu&gt;**<br /><br />**-d:&lt;ciągu&gt;**|Określa symbol do użycia w kompilacji warunkowej.|
|**--deterministyczne**[**+**&#124; **-**]|Tworzy zestaw deterministyczne (w tym identyfikator GUID wersji modułu i sygnatura czasowa).  To nie można używać z symboli wieloznacznych, numery wersji i obsługuje tylko przenośne i osadzone typy debugowania|
|**-doc:&lt;xmldoc filename&gt;**|Instruuje kompilator, aby wygenerować komentarze dokumentacji XML do określonego pliku. Aby uzyskać więcej informacji, zobacz [dokumentacji XML](xml-documentation.md).<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; doc &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/3260k4x7.aspx).|
|**fullpaths —**|Instruuje kompilator, aby wygenerować pełni kwalifikowanej ścieżki.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; fullpaths &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/d315xc66.aspx).|
|**— Pomoc**<br /><br />**-?**|Zawiera informacje dotyczące użycia, w tym krótki opis wszystkich opcji kompilatora.|
|**-highentropyva**[**+**&#124; **-**]|Włącz lub wyłącz randomizacji układu przestrzeni adresowej wysokiej entropii (ASLR), funkcja zwiększonych zabezpieczeń. System operacyjny wybrać losowo lokalizacje w pamięci załadunku infrastruktury dla aplikacji (takich jak stosu i sterty). Jeśli ta opcja jest włączona, systemów operacyjnych umożliwiają losowe użyj pełnego 64-bit — przestrzeni adresowej na komputerze 64-bitowych.|
|**--keycontainer:&lt;ciągu&gt;**|Określa kontener klucza o silnej nazwie.|
|**--keyfile:&lt;filename&gt;**|Określa nazwę pliku klucza publicznego do podpisywania wygenerowanym zestawie.|
|**-lib:&lt;nazwa folderu&gt;**<br /><br />**-I:&lt;nazwa folderu&gt;**|Określa katalog wyszukiwania zestawów, do których istnieją odwołania.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; lib &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/s5bac5fx.aspx).|
|**linkresource —**:**&lt;informacje o zasobie&gt;**|Łącza określonego zasobu do zestawu. Format informacji o zasobów jest *filename*[,*nazwa*[,*publicznego*&#124; *prywatne*]]<br /><br />Łączenie pojedynczego zasobu z tą opcją jest to alternatywa dla Osadzanie pliku zasobów całej z **--zasobów** opcji.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; linkresource &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/xawyf94k.aspx).|
|**--mlcompatibility**|Ignoruje ostrzeżenia, które są wyświetlane, korzystając z funkcji, które są przeznaczone dla zgodności z innymi wersjami uczenia Maszynowego.|
|**noframework —**|Wyłącza domyślne odwołanie do zestawu .NET Framework.|
|**nointerfacedata —**|Instruuje kompilator, aby pominąć zasobów zazwyczaj dodaje do zestawu, który zawiera F #-określonych metadanych.|
|**-nologo**|Nie wyświetla tekst transparentu podczas uruchamiania kompilatora.|
|**--nooptimizationdata**|Instruuje kompilator, aby wyświetlić tylko istotne dla implementacji konstrukcji śródwierszowych optymalizacji. Powstrzymuje między modułami, ale zwiększa zgodność binarną.|
|**-nowin32manifest**|Instruuje kompilator, aby pominąć domyślnego manifestu Win32.|
|**--nowarn:&lt;listy int&gt;**|Wyłącza określone ostrzeżenia, wymienionych według numeru. Numeru ostrzeżenia należy oddzielić przecinkami. Może odnajdywać ostrzeżenie numer ostrzeżenia z danych wyjściowych kompilacji.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; nowarn &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/7f28x9z3.aspx).|
|**--zoptymalizować**[**+**&#124; **-** ]**[&lt;lista ciągów&gt;]**<br /><br />**-O [+ &#124;-] [&lt;lista ciągów&gt;]**|Włącza lub wyłącza optymalizacje. Niektóre opcje optymalizacji mogą zostać wyłączone lub włączone selektywnie, wpisując je. Są to: **nojitoptimize**, **nojittracking**, **nolocaloptimize**, **nocrossoptimize**, **notailcalls**.|
|**-out:&lt;nazwa pliku wyjściowego&gt;**<br /><br />**-o:&lt;nazwa pliku wyjściowego&gt;**|Określa nazwę skompilowanego zestawu lub modułu.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; limit &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/bw3t50f3.aspx).|
|**--pdb:&lt;nazwę pliku pdb&gt;**|Nazwa wyjściowego pliku PDB (bazy danych programu) debugowania. Ta opcja ma zastosowanie tylko podczas **--debug** jest włączona.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; pdb &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/ms228625.aspx).|
|**--platformy:&lt;nazwa platformy&gt;**|Określa, że wygenerowany kod działa tylko w określonej platformy (**x86**, **Itanium**, lub **x64**), lub jeśli nazwa platformy **anycpu**jest wybrana, określa, że wygenerowany kod można uruchomić na dowolnej platformie.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; platform &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/zekwfyz4.aspx).|
|**--ofert debugowania**|Określa, że dodatkowe informacje o debugowaniu powinien wysyłanego dla wyrażeń, które pochodzą z literałów cytatu F # i odzwierciedlone definicje. Informacje debugowania są dodawane do niestandardowych atrybutów węzła drzewa wyrażenia F #. Zobacz [kodu ofert](code-quotations.md) i [Expr.customattributes —](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--odwołania:&lt;nazwa pliku zestawu&gt;**<br /><br />**-r** &lt; **nazwa pliku zestawu&gt;**|Udostępnia kod z zestawu F # lub .NET Framework do kodu kompilowany.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; odwołanie &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/yabyz3h4.aspx).|
|**--resource:&lt;nazwę pliku zasobów&gt;**|Osadza plik zasobu zarządzanego w wygenerowanym zestawie.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#40; &#47; zasobów K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/c0tyye07.aspx).|
|**sig —**:&lt;**nazwę pliku podpisu&gt;**|Generuje plik podpisu na podstawie w wygenerowanym zestawie. Aby uzyskać więcej informacji o plikach podpisu, zobacz [podpisy](signatures.md).|
|**--simpleresolution**|Określa, że odwołania do zestawów mają zostać rozwiązane za pomocą reguł Mono opartych na katalogu, a nie rozpoznawania narzędzia MSBuild. Wartość domyślna to rozdzielczość MSBuild z wyjątkiem podczas uruchamiania Mono.|
|**--autonomiczny**|Określa, aby utworzyć zestaw, który zawiera wszystkie jego zależności, aby został uruchomiony przez samego siebie bez konieczności stosowania dodatkowych zestawów, takiej jak biblioteka języka F #.|
|**staticlink —:&lt;nazwy zestawu**&gt;|Statycznie łączy podany zestaw i wszystkie przywoływane biblioteki dll, które są zależne od tego zestawu. Użyj nazwy zestawu, a nie nazwy biblioteki DLL.|
|**--subsystemversion**|Określa wersję podsystemu systemu operacyjnego mają być używane przez wygenerowanego pliku wykonywalnego. Użyj 6.02 dla Windows 8.1, 6.01 dla systemu Windows 7, 6,00 dla systemu Windows Vista. Ta opcja tylko dotyczy pliki wykonywalne, pliki dll nie i musi być używany jedynie, jeśli aplikacja jest zależna od funkcji zabezpieczeń dostępnych tylko w niektórych wersjach systemu operacyjnego. Jeśli ta opcja jest używana, a użytkownik próbuje uruchomić aplikację w starszej wersji systemu operacyjnego, zakończy się niepowodzeniem z komunikatem o błędzie.|
|**tailcalls —**[**+**&#124; **-**]|Włącza lub wyłącza użycie instrukcji IL tail, co powoduje, że ramka stosu zostanie ponownie tail funkcji cyklicznej. Ta opcja jest domyślnie włączona.|
|**--docelowej**: [**exe** &#124; **winexe** &#124; **biblioteki** &#124; **modułu** ]  **&lt;nazwa pliku wyjściowego&gt;**|Określa typ i nazwa pliku wygenerowanego kodu skompilowanego.<ul><li>**exe** oznacza aplikacji konsoli.<br /></li><li>**winexe** oznacza aplikacji systemu Windows, który różni się od aplikacji konsoli, w tym nie ma standardowych danych wejściowych/wyjściowych strumieni (stdin, stdout i stderr) zdefiniowane.<br /></li><li>**Biblioteka** jest zestawem bez punktu wejścia.<br /></li><li>**Moduł** jest modułem platformy .NET Framework (modułu .netmodule), które później można łączyć z innymi modułami w zestawie.<br /></li><ul/>Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; docelowej &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/6h25dztx.aspx).|
|**--razy**|Wyświetla informacje o chronometrażu dla kompilacji.|
|**-utf8output**|Umożliwia drukowanie dane wyjściowe kompilatora przy użyciu kodowania UTF-8.|
|**— Ostrzeżenie:&lt;poziom ostrzeżeń&gt;**|Ustawia poziom ostrzeżeń (0 – 5). Domyślny poziom to 3. Każdy ostrzeżenie jest wyświetlane na podstawie ich wagi jego poziom. Poziom 5 zapewnia ostrzeżenia poważny, więcej, ale mniej niż poziom 1.<br /><br />Ostrzeżenia poziomu 5: (zaznaczone w czasie wykonywania użycie cykliczne) 21, 22 (**let rec** obliczone poza kolejnością), 45 (abstrakcji pełną) i 52 (obrony kopii). Wszystkie inne ostrzeżenia to poziom 2.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; Ostrzegaj &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/13b90fz7.aspx).|
|**--warnon:&lt;listy int&gt;**|Włącz określone ostrzeżenia, które mogą być wyłączone domyślnie lub wyłączona przez inną opcję wiersza polecenia. W F # 3.0 to ostrzeżenie 1182 (nieużywane zmienne) jest domyślnie wyłączona.|
|**-warnaserror**[**+**&#124; **-** ] [**&lt;listy int&gt;**]|Włącza lub wyłącza możliwość raportu ostrzeżenia jako błędy. Możesz podać określonych numerów ostrzeżeń, które mają być wyłączone lub włączone. Opcje później w wierszu polecenia zastępują opcje wcześniej w wierszu polecenia. Na przykład aby określić ostrzeżenia, które nie mają zgłoszone jako błędy, należy określić **warnaserror — + - warnaserror —:&lt;listy int&gt;**.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; warnaserror &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/406xhdz3.aspx).|
|**--win32manifest:manifest-nazwa pliku**|Dodaje plik manifestu Win32 do kompilacji. Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; win32manifest &#40; K & 35; Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/bb545961.aspx).|
|**--win32res:resource-nazwa pliku**|Dodaje plik zasobów Win32 do kompilacji.<br /><br />Ta opcja kompilatora jest odpowiednikiem opcji kompilatora C# o takiej samej nazwie. Aby uzyskać więcej informacji, zobacz [&#47; win32res (&#40; K & 35); Opcje kompilatora &#41; ](https://msdn.microsoft.com/library/8f2f5x2e.aspx).|

## <a name="related-topics"></a>Tematy pokrewne


|Tytuł|Opis|
|-----|-----------|
|[Opcje interakcyjne F #](../tutorials/fsharp-interactive/fsharp-interactive-options.md)|Opis opcji wiersza polecenia obsługiwane przez język F # interpretera fsi.exe.|
|[Odwołanie do właściwości projektu](https://msdn.microsoft.com/library/16satcwx.aspx)|W tym artykule opisano interfejs użytkownika dla projektów, w tym strony właściwości projektu, które zapewniają opcje kompilacji.|
