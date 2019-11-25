---
title: Opcje kompilatora C# w rozbiciu na kategorie
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 5cd5607c25dabd8f56ebb58366116666e8e649ea
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972703"
---
# <a name="c-compiler-options-listed-by-category"></a>Opcje kompilatora C# w rozbiciu na kategorie

Poniższe opcje kompilatora są sortowane według kategorii. Aby zapoznać się z listą alfabetyczną, zobacz [ C# opcje kompilatora w porządku alfabetycznym](listed-alphabetically.md).

## <a name="optimization"></a>optymalizacja

|Opcja|Cel|
|------------|-------------|
|[-filealign](filealign-compiler-option.md)|Określa rozmiar sekcji w pliku wyjściowym.|
|[-optimize](optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|

## <a name="output-files"></a>Pliki wyjściowe

|Opcja|Cel|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-doc](doc-compiler-option.md)|Określa plik XML, w którym mają być zapisywane przetworzone komentarze dokumentacji.|
|[-out](out-compiler-option.md)|Określa plik wyjściowy.|
|[-pathmap](pathmap-compiler-option.md)|Określ Mapowanie nazw ścieżek źródłowych wyjściowych przez kompilator|
|[-pdb](pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku. pdb.|
|[-platform](platform-compiler-option.md)|Określ platformę wyjściową.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Określ język dla danych wyjściowych kompilatora.|
|[-refout](refout-compiler-option.md)|Wygeneruj zestaw referencyjny jako uzupełnienie podstawowego zestawu.|
|[-refonly](refonly-compiler-option.md)|Wygeneruj zestaw odniesienia zamiast zestawu podstawowego.|
|[-target](target-compiler-option.md)|Określa format pliku wyjściowego przy użyciu jednej z pięciu opcji: [-target: appcontainerexe](target-appcontainerexe-compiler-option.md), [-target: exe](target-exe-compiler-option.md), [-target: Library](target-library-compiler-option.md), [-target: module](target-module-compiler-option.md), [-target: winexe](target-winexe-compiler-option.md)lub [-target: winmdobj](target-winmdobj-compiler-option.md).|
|-ModuleName:\<ciąg >|Określ nazwę modułu źródłowego|

## <a name="net-framework-assemblies"></a>Zestawy .NET Framework

|Opcja|Cel|
|------------|-------------|
|[-addmodule](addmodule-compiler-option.md)|Określa co najmniej jeden moduł, który ma być częścią tego zestawu.|
|[-delaysign](delaysign-compiler-option.md)|Nakazuje kompilatorowi dodanie klucza publicznego, ale pozostawienie zestawu bez znaku.|
|[-keycontainer](keycontainer-compiler-option.md)|Określa nazwę kontenera klucza kryptograficznego.|
|[-keyfile](keyfile-compiler-option.md)|Określa nazwę pliku zawierającego klucz kryptograficzny.|
|[-lib](lib-compiler-option.md)|Określa lokalizację zestawów, do których odwołuje się [odwołanie](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilator, aby nie zaimportował biblioteki standardowej (mscorlib. dll).|
|[-publicsign](publicsign-compiler-option.md)|Zastosuj klucz publiczny bez podpisywania zestawu, ale ustaw bit w zestawie wskazujący, że zestaw jest podpisany.|
|[-reference](reference-compiler-option.md)|Importuje metadane z pliku, który zawiera zestaw.|
|-Analizator|Uruchom analizatory z tego zestawu (krótka wersja:/a)|
|-additionalfile|Nazywa dodatkowe pliki, które nie wpływają bezpośrednio na generowanie kodu, ale mogą być używane przez analizatory do tworzenia błędów lub ostrzeżeń.|
|-Osadź|Osadź wszystkie pliki źródłowe w pliku PDB.|
|-Osadź:\<listy plików >|Osadź określone pliki w pliku PDB.|
## <a name="debuggingerror-checking"></a>Debugowanie/sprawdzanie błędów

|Opcja|Cel|
|------------|-------------|
|[-bugreport](bugreport-compiler-option.md)|Tworzy plik zawierający informacje, które ułatwiają zgłoszenie błędu.|
|[-checked](checked-compiler-option.md)|Określa, czy arytmetyczne liczby całkowite, które przepływają granice typu danych, spowodują wyjątek w czasie wykonywania.|
|[-debug](debug-compiler-option.md)|Nakazuje kompilatorowi emitowanie informacji o debugowaniu.|
|[-errorreport](errorreport-compiler-option.md)|Ustawia zachowanie raportowania błędów.|
|[-fullpaths](fullpaths-compiler-option.md)|Określa ścieżkę bezwzględną do pliku w danych wyjściowych kompilatora.|
|[-nowarn](nowarn-compiler-option.md)|Pomija generowanie określonych ostrzeżeń przez kompilator.|
|[-warn](warn-compiler-option.md)|Ustawia poziom ostrzeżeń.|
|[-warnaserror](warnaserror-compiler-option.md)|Podwyższa poziom ostrzeżeń do błędów.|
|-zestaw reguł:\<pliku >|Określ plik zestawu reguł, który wyłącza określoną diagnostykę.|

## <a name="preprocessor"></a>Preprocesor

|Opcja|Cel|
|------------|-------------|
|[-define](define-compiler-option.md)|Definiuje symbole preprocesora.|

## <a name="resources"></a>Resources

|Opcja|Cel|
|------------|-------------|
|[-link](link-compiler-option.md)|Sprawia, że informacje o typie COM w określonych zestawach są dostępne dla projektu.|
|[-linkresource](linkresource-compiler-option.md)|Tworzy łącze do zarządzanego zasobu.|
|[-resource](resource-compiler-option.md)|Osadza zasób .NET Framework w pliku wyjściowym.|
|[-win32icon](win32icon-compiler-option.md)|Określa plik. ico, który ma zostać wstawiony do pliku wyjściowego.|
|[-win32res](win32res-compiler-option.md)|Określa zasób Win32, który ma zostać wstawiony do pliku wyjściowego.|

## <a name="miscellaneous"></a>Różne

|Opcja|Cel|
|------------|-------------|
|[@](response-file-compiler-option.md)|Określa plik odpowiedzi.|
|[-?](help-compiler-option.md)|Wyświetla listę opcji kompilatora do stdout.|
|[-baseaddress](baseaddress-compiler-option.md)|Określa preferowany adres podstawowy, z którego ma zostać załadowana Biblioteka DLL.|
|[-codepage](codepage-compiler-option.md)|Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji.|
|[-Pomoc](help-compiler-option.md)|Wyświetla listę opcji kompilatora do stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Określa, że plik wykonywalny obsługuje generowanie losowe układu przestrzeni adresowej (ASLR).|
|[-langversion](langversion-compiler-option.md)|Określ wersję języka: default, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7,1, 7,2, 7,3 lub Najnowsza |
|[-main](main-compiler-option.md)|Określa lokalizację metody **Main** .|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilator, aby nie kompilować z CSC. rsp.|
|[-nologo](nologo-compiler-option.md)|Pomija informacje transparentu kompilatora.|
|[-recurse](recurse-compiler-option.md)|Wyszukuje w podkatalogach pliki źródłowe do skompilowania.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, który może być używany przez plik wykonywalny.|
|[-unsafe](unsafe-compiler-option.md)|Włącza kompilację kodu, który używa słowa kluczowego [UNSAFE](../keywords/unsafe.md) .|
|[-utf8output](utf8output-compiler-option.md)|Wyświetla dane wyjściowe kompilatora przy użyciu kodowania UTF-8.|
|-Parallel [+&#124;-]|Określa, czy ma być używana współbieżna kompilacja (+).|
|-checksumalgorithm:\<alg >|Określ algorytm obliczania sumy kontrolnej plików źródłowych przechowywanej w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (domyślnie) lub SHA256.<br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256.|

## <a name="obsolete-options"></a>Przestarzałe opcje

|Opcja|Cel|
|---|---|
|-przyrostowe|Włącza kompilację przyrostową.|

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](index.md)
- [Opcje kompilatora C# w porządku alfabetycznym](listed-alphabetically.md)
- [Jak ustawić zmienne środowiskowe dla wiersza polecenia programu Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
