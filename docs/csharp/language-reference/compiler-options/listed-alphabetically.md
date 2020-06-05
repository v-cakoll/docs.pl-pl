---
title: Opcje kompilatora C# w porządku alfabetycznym
ms.date: 06/04/2020
helpviewer_keywords:
- compiler options [C#], listed alphabetically
- C# language, compiler options listed alphabetically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: 9765d13191f862a2e92bb00aa66a92c3a64ac303
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446942"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Opcje kompilatora C# w porządku alfabetycznym

Poniższe opcje kompilatora są sortowane alfabetycznie. Aby uzyskać listę kategorii, zobacz [Opcje kompilatora C# na liście według kategorii](listed-by-category.md).

|Opcja|Przeznaczenie|
|------------|-------------|
|[@](response-file-compiler-option.md)|Odczytuje plik odpowiedzi w celu uzyskania dodatkowych opcji.|
|[-?](help-compiler-option.md)|Wyświetla komunikat użycia do stdout.|
|-additionalfile|Nazywa dodatkowe pliki, które nie wpływają bezpośrednio na generowanie kodu, ale mogą być używane przez analizatory do tworzenia błędów lub ostrzeżeń.|
|[-addmodule](addmodule-compiler-option.md)|Łączy określone moduły z tym zestawem|
|-Analizator|Uruchom analizatory z tego zestawu (krótka wersja:-a)|
|[-appconfig](appconfig-compiler-option.md)|Określa lokalizację pliku App. config w czasie powiązania zestawu.|
|[-baseaddress](baseaddress-compiler-option.md)|Określa adres podstawowy biblioteki, która ma zostać skompilowana.|
|[-bugreport](bugreport-compiler-option.md)|Tworzy plik raportu o usterce. Ten plik zostanie wysłany wraz z informacjami o awarii, jeśli jest używany z-errorReport: Prompt lub-errorReport: Send.|
|[-checked](checked-compiler-option.md)|Powoduje, że kompilator generuje operacje sprawdzania przepełnienia.|
|-checksumalgorithm:\<alg>|Określa algorytm obliczania sumy kontrolnej plików źródłowych przechowywanej w pliku PDB.  Obsługiwane wartości to: SHA256 (wartość domyślna) lub SHA1.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256. |
|[-codepage](codepage-compiler-option.md)|Określa stronę kodową, która ma być używana podczas otwierania plików źródłowych.|
|[-Debuguj](debug-compiler-option.md)|Emituje informacje o debugowaniu.|
|[-define](define-compiler-option.md)|Definiuje symbole kompilacji warunkowej.|
|[-delaysign](delaysign-compiler-option.md)|Opóźnia podpisanie zestawu, używając tylko publicznej części klucza silnej nazwy.|
|[-deterministic](deterministic-compiler-option.md)|Powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-doc](doc-compiler-option.md)|Określa plik dokumentacji XML do wygenerowania.|
|-Osadź|Osadź wszystkie pliki źródłowe w pliku PDB.|
|osadzon\<file list>|Osadź określone pliki w pliku PDB.|
|-errorendlocation|Wiersz i kolumna wyjściowa lokalizacji końcowej każdego błędu.|
|błędów\<file>|Określ plik do rejestrowania wszystkich kompilatorów i diagnostyki analizatora.|
|[-errorreport](errorreport-compiler-option.md)|Określa sposób obsługi wewnętrznych błędów kompilatora: Prompt, Send lub None. Wartość domyślna to brak.|
|[-filealign](filealign-compiler-option.md)|Określa wyrównanie używane dla sekcji plików wyjściowych.|
|[-fullpaths](fullpaths-compiler-option.md)|Powoduje, że kompilator generuje w pełni kwalifikowane ścieżki.|
|[-Pomoc](help-compiler-option.md)|Wyświetla komunikat użycia do stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Określa, że jest obsługiwany ASLR o wysokiej entropii.|
|-przyrostowe|Włącza kompilację przyrostową [przestarzałe].|
|[-keycontainer](keycontainer-compiler-option.md)|Określa kontener klucza o silnej nazwie.|
|[-keyfile](keyfile-compiler-option.md)|Określa plik klucza o silnej nazwie.|
|[langversion\<string>](langversion-compiler-option.md)|Określ wersję języka: default, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7,1, 7,2, 7,3 lub Najnowsza |
|[-lib](lib-compiler-option.md)|Określa dodatkowe katalogi, w których mają zostać wyszukane odwołania.|
|[-Link](link-compiler-option.md)|Sprawia, że informacje o typie COM w określonych zestawach są dostępne dla projektu.|
|[-linkresource](linkresource-compiler-option.md)|Łączy określony zasób z tym zestawem.|
|[-main](main-compiler-option.md)|Określa typ, który zawiera punkt wejścia (Ignoruj wszystkie inne możliwe punkty wejścia).|
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Określa zestaw, którego typy niepubliczne a. module mogą uzyskać dostęp.|
|ModuleName\<string>|Określ nazwę modułu źródłowego|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilator, aby nie dołączał do niego CSC. Plik RSP.|
|[-nologo](nologo-compiler-option.md)|Pomija komunikat o prawach autorskich kompilatora.|
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilator, aby nie odwoływać się do standardowej biblioteki (mscorlib. dll).|
|[-nowarn](nowarn-compiler-option.md)|Wyłącza określone komunikaty ostrzegawcze|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Instruuje kompilator, aby nie osadzał manifestu aplikacji w pliku wykonywalnym.|
|[-Nullable](nullable-compiler-option.md)|Określa opcję kontekstową dopuszczania wartości null.|
|[-Optymalizuj](optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|
|[-out](out-compiler-option.md)|Określa nazwę pliku wyjściowego (domyślnie: nazwa podstawowa pliku z klasą główną lub pierwszym plikiem).|
|-Parallel [+&#124;-]|Określa, czy ma być używana współbieżna kompilacja (+).|
|[-pathmap](pathmap-compiler-option.md)|Określa mapowanie nazw ścieżek źródłowych wyjściowych przez kompilator.|
|[-pdb](pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku. pdb.|
|[-Platforma](platform-compiler-option.md)|Ogranicza platformy, na których można uruchamiać ten kod: x86, Itanium, x64, AnyCPU lub anycpu32bitpreferred. Wartość domyślna to AnyCPU.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Określa język, który ma być używany na potrzeby danych wyjściowych kompilatora.|
|[-publicsign](publicsign-compiler-option.md)|Zastosuj klucz publiczny bez podpisywania zestawu, ale ustaw bit w zestawie wskazujący, że zestaw jest podpisany.|
|[-recurse](recurse-compiler-option.md)|Zawiera wszystkie pliki w bieżącym katalogu i podkatalogach zgodnie ze specyfikacją symboli wieloznacznych.|
|[-odwołanie](reference-compiler-option.md)|Odwołuje się do metadanych z określonych plików zestawu.|
|[-refout](refout-compiler-option.md)|Wygeneruj zestaw referencyjny jako uzupełnienie podstawowego zestawu.|
|[-refonly](refonly-compiler-option.md)|Wygeneruj zestaw odniesienia zamiast zestawu podstawowego.|
|-reportanalyzer|Zgłoś dodatkowe informacje analizatora, takie jak czas wykonywania.|
|[-zasób](resource-compiler-option.md)|Osadza określony zasób.|
|RuleSet\<file>|Określ plik zestawu reguł, który wyłącza określoną diagnostykę.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, który może być używany przez plik wykonywalny.|
|[-target](target-compiler-option.md)|Określa format pliku wyjściowego przy użyciu jednej z czterech opcji: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: Library](target-library-compiler-option.md), [-target: module](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), [-target: winmdobj](target-winmdobj-compiler-option.md).|
|[-unsafe](unsafe-compiler-option.md)|Zezwala na [niebezpieczny](../keywords/unsafe.md) kod.|
|[-utf8output](utf8output-compiler-option.md)|Wyświetla komunikaty kompilatora w kodowaniu UTF-8.|
|-Wersja|Wyświetl numer wersji kompilatora i Zakończ.|
|[-warn](warn-compiler-option.md)|Ustawia poziom ostrzeżeń (0-4).|
|[-warnaserror](warnaserror-compiler-option.md)|Zgłasza określone ostrzeżenia jako błędy.|
|[-win32icon](win32icon-compiler-option.md)|Używa tej ikony dla danych wyjściowych.|
|[-win32manifest](win32manifest-compiler-option.md)|Określa niestandardowy plik manifestu Win32.|
|[-win32res](win32res-compiler-option.md)|Określa plik zasobów Win32 (. res).|

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](index.md)
- [Opcje kompilatora C# w rozbiciu na kategorie](listed-by-category.md)
- [Porada: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<compiler>Postaci](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
