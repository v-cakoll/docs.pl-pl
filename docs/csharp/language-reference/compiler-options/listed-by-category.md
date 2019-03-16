---
title: Opcje kompilatora C# w rozbiciu na kategorie
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: bceb6283e202dfa699115edd6e0a1a040095783d
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58028706"
---
# <a name="c-compiler-options-listed-by-category"></a>Opcje kompilatora C# w rozbiciu na kategorie

Następujące opcje kompilatora są sortowane według kategorii. Aby uzyskać alfabetyczną listę, zobacz [C# kompilatora opcji na liście alfabetycznie](listed-alphabetically.md).

## <a name="optimization"></a>Optymalizacja

|Opcja|Cel|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Określa rozmiar sekcji w pliku wyjściowym.|
|[-optimize](optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|

## <a name="output-files"></a>Pliki wyjściowe

|Opcja|Cel|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Powoduje, że kompilator do wyjściowego zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-doc](doc-compiler-option.md)|Określa plik XML, gdzie mają być zapisywane komentarzy dokumentacji przetworzone.|
|[-out](out-compiler-option.md)|Określa plik wyjściowy.|
|[-pathmap](pathmap-compiler-option.md)|Określanie mapowania dla źródła danych wyjściowych z nazw ścieżki przez kompilator|
|[-pdb](pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku .pdb.|
|[-platform](platform-compiler-option.md)|Określanie platformy wyjściowej.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Określanie języka danych wyjściowych kompilatora.|
|[-refout](refout-compiler-option.md)|Generowanie zestawu odwołania oprócz podstawowego zestawu.|
|[-refonly](refonly-compiler-option.md)|Generowanie zestawu odwołania zamiast podstawowego zestawu.|
|[-target](target-compiler-option.md)|Określa format pliku wyjściowego przy użyciu jednego z pięciu opcji: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: library](target-library-compiler-option.md), [-target: module ](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md), lub [-target: winmdobj](target-winmdobj-compiler-option.md).|
|-modulename:\<ciąg >|Określ nazwę modułu źródła|

## <a name="net-framework-assemblies"></a>Zestawy .NET framework

|Opcja|Cel|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Określa jeden lub wiele modułów jako część tego zestawu.|
|[-delaysign](delaysign-compiler-option.md)|Instruuje kompilator, Dodaj klucz publiczny, ale pozostawić zestawu bez znaku.|
|[-keycontainer](keycontainer-compiler-option.md)|Określa nazwę kontenera kluczy kryptograficznych.|
|[-keyfile](keyfile-compiler-option.md)|Określa nazwę pliku zawierającego klucz kryptograficzny.|
|[-lib](lib-compiler-option.md)|Określa lokalizację zestawów, do których odwołuje się poprzez [— dokumentacja](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilator, aby nie importuje biblioteki standardowej (mscorlib.dll).|
|[-publicsign](publicsign-compiler-option.md)|Zastosuj klucz publiczny bez podpisywania zestawu, ale ustawiony bit w zestawie, wskazujący, że zestaw jest podpisany.|
|[-reference](reference-compiler-option.md)|Importuje metadane z pliku, który zawiera zestaw.|
|-analyzer|Uruchom analizatorów z tego zestawu (skrócona forma: /)|
|-additionalfile|Nazwy dodatkowe pliki, bezpośrednio nie wpływa na generowanie kodu, które mogą być używane przez analizatory do produkcji, błędy lub ostrzeżenia.|
|-osadzania|Osadź wszystkich plików źródłowych w pliku PDB.|
|-osadzania:\<lista plików >|Osadzanie plików określonych w pliku PDB.|
## <a name="debuggingerror-checking"></a>Sprawdzanie Debugowanie błędów

|Opcja|Cel|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Tworzy plik, który zawiera informacje, które można łatwo Zgłoś usterkę.|
|[-checked](checked-compiler-option.md)|Określa, czy liczba całkowita arytmetyczny, który przepełnienie granic o typie danych spowoduje, że wyjątek w czasie wykonywania.|
|[-debug](debug-compiler-option.md)|Poinstruować kompilator, aby wyemitować informacji debugowania.|
|[-errorreport](errorreport-compiler-option.md)|Ustawienie zachowania raportowania błędów.|
|[-fullpaths](fullpaths-compiler-option.md)|Określa ścieżkę bezwzględną do pliku w danych wyjściowych kompilatora.|
|[-nowarn](nowarn-compiler-option.md)|Pomija generację określonych ostrzeżeń kompilatora.|
|[-warn](warn-compiler-option.md)|Ustawia poziom ostrzeżeń.|
|[-warnaserror](warnaserror-compiler-option.md)|Podwyższa poziom ostrzeżeń do błędów.|
|-zestaw reguł:\<pliku >|Określ plik zestawu reguł, który wyłącza działania diagnostyczne zależne.|

## <a name="preprocessor"></a>Preprocesor

|Opcja|Cel|
|------------|-------------|
|[-define](define-compiler-option.md)|Definiuje symbole preprocesora.|

## <a name="resources"></a>Zasoby

|Opcja|Cel|
|------------|-------------|
|[-link](link-compiler-option.md)|Udostępnia informacje o typie modelu COM w określonych zestawach do projektu.|
|[-linkresource](linkresource-compiler-option.md)|Tworzy łącze do zarządzanego zasobem.|
|[-resource](resource-compiler-option.md)|Osadza zasób .NET Framework do pliku wyjściowego.|
|[-win32icon](win32icon-compiler-option.md)|Określa plik .ico, aby wstawić do pliku wyjściowego.|
|[-win32res](win32res-compiler-option.md)|Określa zasób Win32, aby wstawić do pliku wyjściowego.|

## <a name="miscellaneous"></a>Różne

|Opcja|Cel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Określa plik odpowiedzi.|
|[-?](help-compiler-option.md)|Wyświetla listę opcji kompilatora stdout.|
|[-baseaddress](baseaddress-compiler-option.md)|Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL.|
|[-codepage](codepage-compiler-option.md)|Określa stronę kodową do użycia dla wszystkich plikach kodu źródłowego w kompilacji.|
|[-help](help-compiler-option.md)|Wyświetla listę opcji kompilatora stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Określa, że plik wykonywalny obsługuje randomizacji układu przestrzeni adresowej (ASLR).|
|[-langversion](langversion-compiler-option.md)|Określ wersję języka: Domyślny, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 lub r |
|[-main](main-compiler-option.md)|Określa lokalizację **Main** metody.|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilator, nie można skompilować przy użyciu csc.rsp.|
|[-nologo](nologo-compiler-option.md)|Pomija informacji o transparencie kompilatora.|
|[-recurse](recurse-compiler-option.md)|Podkatalogi wyszukiwania dla plików źródłowych do kompilowania.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, którego można użyć pliku wykonywalnego.|
|[-unsafe](unsafe-compiler-option.md)|Włącza kompilację kodu, który używa [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe.|
|[-utf8output](utf8output-compiler-option.md)|Kompilator wyświetla dane wyjściowe przy użyciu kodowania UTF-8.|
|-parallel[+&#124;-]|Określa, czy używać współbieżną kompilację (+).|
|-checksumalgorithm:\<alg>|Określić algorytm obliczania sumy kontrolnej pliku źródłowego, które zostały zapisane w pliku PDB.  Obsługiwane są następujące wartości: Algorytm SHA1 (domyślna) lub SHA256.<br>Ze względu na problemy kolizji z SHA1 firma Microsoft zaleca SHA256.|

## <a name="obsolete-options"></a>Opcje przestarzałe

|Opcja|Cel|
|---|---|
|-incremental|Włącza kompilację przyrostową.|

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](index.md)
- [Opcje kompilatora C# w porządku alfabetycznym](listed-alphabetically.md)
- [Instrukcje: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
