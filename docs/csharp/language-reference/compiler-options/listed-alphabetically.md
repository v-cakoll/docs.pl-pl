---
title: Opcje kompilatora C# w porządku alfabetycznym
ms.date: 05/15/2018
helpviewer_keywords:
- compiler options [C#], listed alphabetically
- C# language, compiler options listed alphabetically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: 1e7b19999ab8536e9a1b05c1ad5d548c8da2cbd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662728"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Opcje kompilatora C# w porządku alfabetycznym

Następujące opcje kompilatora są sortowane alfabetycznie. Aby uzyskać listę kategorii, zobacz [C# opcje kompilatora wymienione według kategorii](listed-by-category.md).

|Opcja|Cel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Odczytuje plik odpowiedzi, aby wyświetlić więcej opcji.|
|[-?](help-compiler-option.md)|Wyświetla komunikat o sposobie użycia do strumienia wyjściowego stdout.|
|-additionalfile|Nazwy dodatkowe pliki, bezpośrednio nie wpływa na generowanie kodu, które mogą być używane przez analizatory do produkcji, błędy lub ostrzeżenia.|
|[-addmodule](addmodule-compiler-option.md)|Łączy określone moduły z tym zestawem|
|-analyzer|Uruchom analizatorów z tego zestawu (skrócona forma: -)|
|[-appconfig](appconfig-compiler-option.md)|Określa lokalizację pliku app.config w czasie powiązania zestawu.|
|[-baseaddress](baseaddress-compiler-option.md)|Określa adres podstawowy biblioteki, który ma zostać utworzony.|
|[-bugreport](bugreport-compiler-option.md)|Tworzy plik "Raport o usterce". Ten plik będzie wysyłane wraz z informacjami o awariach, jeśli jest używane z parametrem-errorreport: wiersz lub - errorreport: wysyłanie.|
|[-checked](checked-compiler-option.md)|Powoduje, że kompilatorowi Generowanie sprawdzenia przepełnienia.|
|-checksumalgorithm:\<alg>|Określa algorytm obliczania sumy kontrolnej pliku źródłowego, które zostały zapisane w pliku PDB.  Obsługiwane są następujące wartości: Algorytm SHA1 (domyślna) lub SHA256.<br>Ze względu na problemy kolizji z SHA1 firma Microsoft zaleca SHA256. |
|[-codepage](codepage-compiler-option.md)|Określa stronę kodową do użycia przy otwieraniu plików źródłowych.|
|[-debug](debug-compiler-option.md)|Emituje informacje debugowania.|
|[-define](define-compiler-option.md)|Definiuje symbole kompilacji warunkowej.|
|[-delaysign](delaysign-compiler-option.md)|Podpisuje testowo opóźnienie zestawie, używając tylko publicznej części klucza silnej nazwy.|
|[-deterministic](deterministic-compiler-option.md)|Powoduje, że kompilator do wyjściowego zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-doc](doc-compiler-option.md)|Określa plik dokumentacji XML do wygenerowania.|
|-osadzania|Osadź wszystkich plików źródłowych w pliku PDB.|
|-osadzania:\<lista plików >|Osadzanie plików określonych w pliku PDB.|
|-errorendlocation|Wyprowadź wiersz i kolumnę lokalizacji końcowej dla każdego błędu.|
|— Dziennik błędów:\<pliku >|Określ plik, aby rejestrować wszystkie diagnostyki kompilatora i analizator.|
|[-errorreport](errorreport-compiler-option.md)|Określa sposób obsługiwać wewnętrzne błędy kompilatora: wiersz, Wyślij lub Brak. Domyślna wartość to Brak.|
|[-filealign](filealign-compiler-option.md)|Określa wyrównanie stosowane dla sekcji plików wyjściowych.|
|[-fullpaths](fullpaths-compiler-option.md)|Powoduje, że kompilatorowi Generowanie ścieżek w pełni kwalifikowanych.|
|[-help](help-compiler-option.md)|Wyświetla komunikat o sposobie użycia do strumienia wyjściowego stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Określa, że o wysokiej entropii, obsługiwany jest ASLR.|
|-incremental|Włącza kompilację przyrostową [nieaktualne].|
|[-keycontainer](keycontainer-compiler-option.md)|Określa kontener klucza silnej nazwy.|
|[-keyfile](keyfile-compiler-option.md)|Określa plik klucza o silnej nazwie.|
|[-langversion:\<ciąg >](langversion-compiler-option.md)|Określ wersję języka: Domyślny, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 lub r |
|[-lib](lib-compiler-option.md)|Określa dodatkowe katalogi, w których należy szukać odwołania.|
|[-link](link-compiler-option.md)|Udostępnia informacje o typie modelu COM w określonych zestawach do projektu.|
|[-linkresource](linkresource-compiler-option.md)|Łączy określony zasób do tego zestawu.|
|[-main](main-compiler-option.md)|Określa typ zawierający punkt wejścia (Ignoruj wszystkie pozostałe możliwe punkty wejścia).|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Określa, których typy bez publicznego .netmodule mogą uzyskiwać dostęp do zestawu.|
|-modulename:\<ciąg >|Określ nazwę modułu źródła|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilator, nie można automatycznie dołączyć Centrum obsługi klienta. Plik RSP.|
|[-nologo](nologo-compiler-option.md)|Pomija komunikat o prawach autorskich kompilatora.|
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilator, aby nie odwołanie do biblioteki standardowej (mscorlib.dll).|
|[-nowarn](nowarn-compiler-option.md)|Wyłącza określone ostrzeżenia|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Instruuje kompilator, nie można osadzić manifest aplikacji w pliku wykonywalnym.|
|[-optimize](optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|
|[-out](out-compiler-option.md)|Określa nazwę pliku wyjściowego (domyślne: Nazwa podstawowa pliku z klasą główną lub pierwszym plikiem).|
|-parallel[+&#124;-]|Określa, czy używać współbieżną kompilację (+).|
|[-pathmap](pathmap-compiler-option.md)|Określa mapowania dla źródła danych wyjściowych z nazw ścieżki przez kompilator.|
|[-pdb](pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku .pdb.|
|[-platform](platform-compiler-option.md)|Ograniczenia platform, których można uruchamiać ten kod na: x86, Itanium, x 64, anycpu, lub anycpu32bitpreferred. Wartość domyślna to anycpu.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Określa język, który ma być używany dla danych wyjściowych kompilatora.|
|[-publicsign](publicsign-compiler-option.md)|Zastosuj klucz publiczny bez podpisywania zestawu, ale ustawiony bit w zestawie, wskazujący, że zestaw jest podpisany.|
|[-recurse](recurse-compiler-option.md)|Uwzględnia wszystkie pliki w bieżącym katalogu i jego podkatalogach zgodnie ze specyfikacją symboli wieloznacznych.|
|[-reference](reference-compiler-option.md)|Odwołuje się do metadanych z określonych plików zestawów.|
|[-refout](refout-compiler-option.md)|Generowanie zestawu odwołania oprócz podstawowego zestawu.|
|[-refonly](refonly-compiler-option.md)|Generowanie zestawu odwołania zamiast podstawowego zestawu.|
|-reportanalyzer|Analizator dodatkowych informacji w raporcie, takie jak czas wykonywania.|
|[-resource](resource-compiler-option.md)|Osadza określony zasób.|
|-zestaw reguł:\<pliku >|Określ plik zestawu reguł, który wyłącza działania diagnostyczne zależne.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, którego można użyć pliku wykonywalnego.|
|[-target](target-compiler-option.md)|Określa format pliku wyjściowego przy użyciu jednej z czterech opcji: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [-docelowej: Moduł](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), [-target: winmdobj](target-winmdobj-compiler-option.md).|
|[-unsafe](unsafe-compiler-option.md)|Umożliwia [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kodu.|
|[-utf8output](utf8output-compiler-option.md)|Dane wyjściowe komunikaty kompilatora przy użyciu kodowania UTF-8.|
|-Wersja|Wyświetlanie numeru wersji kompilatora i zakończenia.|
|[-warn](warn-compiler-option.md)|Ustawia poziom ostrzeżeń (0-4).|
|[-warnaserror](warnaserror-compiler-option.md)|Raporty określone ostrzeżenia jako błędy.|
|[-win32icon](win32icon-compiler-option.md)|Używa tej ikony dla danych wyjściowych.|
|[-win32manifest](win32manifest-compiler-option.md)|Określa niestandardowego pliku manifestu win32.|
|[-win32res](win32res-compiler-option.md)|Określa plik zasobów win32 (.res).|

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](index.md)
- [Opcje kompilatora C# w rozbiciu na kategorie](listed-by-category.md)
- [Instrukcje: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
