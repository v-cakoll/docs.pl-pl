---
title: Opcje kompilatora C# w rozbiciu na kategorie
ms.date: 05/15/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: 5cd5607c25dabd8f56ebb58366116666e8e649ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972703"
---
# <a name="c-compiler-options-listed-by-category"></a>Opcje kompilatora C# w rozbiciu na kategorie

Następujące opcje kompilatora są sortowane według kategorii. Aby uzyskać listę alfabetyczną, zobacz [Opcje kompilatora C# wymienione alfabetycznie](listed-alphabetically.md).

## <a name="optimization"></a>Optymalizacja

|Opcja|Przeznaczenie|
|------------|-------------|
|[-filealign (wyrównanie pliku)](filealign-compiler-option.md)|Określa rozmiar sekcji w pliku wyjściowym.|
|[-optymalizacja](optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|

## <a name="output-files"></a>Pliki wyjściowe

|Opcja|Przeznaczenie|
|------------|-------------|
|[-deterministic](deterministic-compiler-option.md)|Powoduje, że kompilator do danych wyjściowych zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-doc](doc-compiler-option.md)|Określa plik XML, w którym mają być zapisywane komentarze dotyczące przetworzonej dokumentacji.|
|[-na zewnątrz](out-compiler-option.md)|Określa plik wyjściowy.|
|[-pathmap](pathmap-compiler-option.md)|Określ mapowanie dla nazw ścieżek źródłowych danych wyjściowych przez kompilator|
|[-pdb](pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku pdb.|
|[-platforma](platform-compiler-option.md)|Określ platformę wyjściową.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Określ język danych wyjściowych kompilatora.|
|[-refout](refout-compiler-option.md)|Wygeneruj zespół odniesienia oprócz złożenia podstawowego.|
|[-refonly](refonly-compiler-option.md)|Wygeneruj złożenie odniesienia zamiast zestawu podstawowego.|
|[-cel](target-compiler-option.md)|Określa format pliku wyjściowego przy użyciu jednej z pięciu opcji: [-target:appcontainerexe](target-appcontainerexe-compiler-option.md), [-target:exe](target-exe-compiler-option.md), [-target:library](target-library-compiler-option.md), [-target:module](target-module-compiler-option.md), [-target:winexe](target-winexe-compiler-option.md)lub [-target:winmdobj](target-winmdobj-compiler-option.md).|
|-nazwa modułu:\<ciąg>|Określ nazwę modułu źródłowego|

## <a name="net-framework-assemblies"></a>Zestawy platform .NET Framework

|Opcja|Przeznaczenie|
|------------|-------------|
|[-addmodule (moduł addmodule)](addmodule-compiler-option.md)|Określa jeden lub więcej modułów, które mają być częścią tego zestawu.|
|[-delaysign](delaysign-compiler-option.md)|Instruuje kompilator, aby dodać klucz publiczny, ale pozostawić zestaw bez znaku.|
|[-pojemnik na klucze](keycontainer-compiler-option.md)|Określa nazwę kontenera kluczy kryptograficznych.|
|[-plik klucza](keyfile-compiler-option.md)|Określa nazwę pliku zawierającą klucz kryptograficzny.|
|[-lib](lib-compiler-option.md)|Określa lokalizację złożeń, do których odwołuje się [-reference](reference-compiler-option.md).|
|[-nostdlib](nostdlib-compiler-option.md)|Nakazuje kompilatorowi, aby nie importował biblioteki standardowej (mscorlib.dll).|
|[-publicsign](publicsign-compiler-option.md)|Zastosuj klucz publiczny bez podpisywania zestawu, ale ustaw bit w złożeniu wskazujący, że zestaw jest podpisany.|
|[-odniesienie](reference-compiler-option.md)|Importuje metadane z pliku zawierającego zestaw.|
|-analizator|Uruchom analizatory z tego zestawu (skrócona forma: /a)|
|-additionalfile|Nazwy dodatkowych plików, które nie mają bezpośredniego wpływu na generowanie kodu, ale mogą być używane przez analizatory do tworzenia błędów lub ostrzeżeń.|
|-osadzanie|Osadzanie wszystkich plików źródłowych w pdb.|
|-embed:\<lista plików>|Osadzanie określonych plików w pdb.|
## <a name="debuggingerror-checking"></a>Debugowanie/sprawdzanie błędów

|Opcja|Przeznaczenie|
|------------|-------------|
|[-raport błędów](bugreport-compiler-option.md)|Tworzy plik zawierający informacje, które ułatwiazgłaszanie usterki.|
|[-sprawdzone](checked-compiler-option.md)|Określa, czy arytmetyka całkowita, która przepełnia granice typu danych spowoduje wyjątek w czasie wykonywania.|
|[-debug](debug-compiler-option.md)|Poinstruuj kompilator, aby emitował informacje o debugowaniu.|
|[-raport o błędach](errorreport-compiler-option.md)|Ustawia zachowanie raportowania błędów.|
|[-fullpaths](fullpaths-compiler-option.md)|Określa ścieżkę bezwzględną do pliku w danych wyjściowych kompilatora.|
|[-nowarn](nowarn-compiler-option.md)|Pomija generowanie kompilatora określonych ostrzeżeń.|
|[-warn](warn-compiler-option.md)|Ustawia poziom ostrzeżenia.|
|[-warnaserror](warnaserror-compiler-option.md)|Promuje ostrzeżenia do błędów.|
|-ruleset:\<plik>|Określ plik zestawu reguł, który wyłącza określoną diagnostykę.|

## <a name="preprocessor"></a>Preprocesor

|Opcja|Przeznaczenie|
|------------|-------------|
|[-zdefiniować](define-compiler-option.md)|Definiuje symbole preprocesora.|

## <a name="resources"></a>Zasoby

|Opcja|Przeznaczenie|
|------------|-------------|
|[-link](link-compiler-option.md)|Udostępnia informacje o typie COM w określonych zestawach do projektu.|
|[-linkresource](linkresource-compiler-option.md)|Tworzy łącze do zasobu zarządzanego.|
|[-zasób](resource-compiler-option.md)|Osadza zasób .NET Framework w pliku wyjściowym.|
|[-win32icon](win32icon-compiler-option.md)|Określa plik .ico, który ma zostać wstawiony do pliku wyjściowego.|
|[-win32res](win32res-compiler-option.md)|Określa zasób Win32 do wstawienia do pliku wyjściowego.|

## <a name="miscellaneous"></a>Różne

|Opcja|Przeznaczenie|
|------------|-------------|
|[@](response-file-compiler-option.md)|Określa plik odpowiedzi.|
|[-?](help-compiler-option.md)|Wyświetla listę opcji kompilatora do stdout.|
|[-adres bazowy](baseaddress-compiler-option.md)|Określa preferowany adres podstawowy, pod którym ma zostać załadowana dll.|
|[-strona kodowa](codepage-compiler-option.md)|Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji.|
|[-pomoc](help-compiler-option.md)|Wyświetla listę opcji kompilatora do stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Określa, że plik wykonywalny obsługuje randomizację układu przestrzeni adresowej (ASLR).|
|[-langversion (wypł.](langversion-compiler-option.md)|Określ wersję językową: Domyślnie, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 lub Najnowsze |
|[-main](main-compiler-option.md)|Określa lokalizację metody **Main.**|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilatora, aby nie kompilował z csc.rsp.|
|[-nologo](nologo-compiler-option.md)|Pomija informacje o banerze kompilatora.|
|[-recurse](recurse-compiler-option.md)|Wyszukuje podkatalogi plików źródłowych do skompilowania.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, z którego może korzystać plik wykonywalny.|
|[-niebezpieczne](unsafe-compiler-option.md)|Umożliwia kompilację kodu, który używa [niebezpiecznego](../keywords/unsafe.md) słowa kluczowego.|
|[-utf8output](utf8output-compiler-option.md)|Wyświetla dane wyjściowe kompilatora przy użyciu kodowania UTF-8.|
|-równolegle[+&#124;-]|Określa, czy ma być używana współbieżna kompilacja (+).|
|-checksumalgorithm:\<alg>|Określ algorytm obliczania sumy kontrolnej pliku źródłowego przechowywanej w PDB.  Obsługiwane wartości to: SHA1 (domyślnie) lub SHA256.<br>Ze względu na problemy z kolizją z SHA1, Microsoft zaleca SHA256.|

## <a name="obsolete-options"></a>Przestarzałe opcje

|Opcja|Przeznaczenie|
|---|---|
|-przyrostowe|Włącza kompilację przyrostową.|

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](index.md)
- [Opcje kompilatora C# w porządku alfabetycznym](listed-alphabetically.md)
- [Porada: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
