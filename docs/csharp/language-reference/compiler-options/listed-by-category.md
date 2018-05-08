---
title: Opcje kompilatora C# w rozbiciu na kategorie
ms.date: 04/12/2018
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
ms.openlocfilehash: a3352b9f929382c7d5b7d0c62ef4022560caf371
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="c-compiler-options-listed-by-category"></a>Opcje kompilatora C# w rozbiciu na kategorie
Następujące opcje kompilatora są sortowane według kategorii. Aby uzyskać alfabetyczną listę, zobacz [C# kompilatora opcje wymienione alfabetycznie](listed-alphabetically.md).  
  
### <a name="optimization"></a>Optymalizacja  
  
|Opcja|Cel|  
|------------|-------------|  
|[-filealign](filealign-compiler-option.md)|Określa rozmiar sekcji w pliku wyjściowym.|  
|[-optimize](optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|  
  
### <a name="output-files"></a>Pliki wyjściowe  
  
|Opcja|Cel|  
|------------|-------------| 
|[-deterministic](deterministic-compiler-option.md)|Powoduje, że kompilator output zestawu, którego zawartość binarna jest identyczna w kompilacji, jeśli dane wejściowe są identyczne.|
|[-doc](doc-compiler-option.md)|Określa plik XML, których komentarzy do dokumentacji przetworzonych do zapisania.|  
|[-out](out-compiler-option.md)|Określa plik wyjściowy.|  
|[-pdb](pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku PDB.|  
|[-platform](platform-compiler-option.md)|Określ platformę danych wyjściowych.|  
|[-preferreduilang](preferreduilang-compiler-option.md)|Określanie języka danych wyjściowych kompilatora.|  
|[-refout](refout-compiler-option.md)|Wygeneruj zestaw odwołania, oprócz podstawowego zestawu.|  
|[-refonly](refonly-compiler-option.md)|Wygeneruj zestaw odwołania, a nie podstawowy zestaw.|  
|[-target](target-compiler-option.md)|Określa format pliku wyjściowego przy użyciu jednej z pięciu opcji: [-docelowych: appcontainerexe](target-appcontainerexe-compiler-option.md), [-docelowych: exe](target-exe-compiler-option.md), [— docelowa: Biblioteka](target-library-compiler-option.md), [-docelowych: moduł ](target-module-compiler-option.md), [-docelowych: winexe](target-winexe-compiler-option.md), lub [-docelowych: winmdobj](target-winmdobj-compiler-option.md).|  
|-modulename:\<ciąg >|Określ nazwę modułu źródła|  
  
### <a name="net-framework-assemblies"></a>Zestawów platformy .NET framework  
  
|Opcja|Cel|  
|------------|-------------|  
|[-addmodule](addmodule-compiler-option.md)|Określa co najmniej jednego modułu należeć do tego zestawu.|  
|[-delaysign](delaysign-compiler-option.md)|Instruuje kompilator, aby dodać klucz publiczny, ale pozostawić zestawu bez znaku.|  
|[-keycontainer](keycontainer-compiler-option.md)|Określa nazwę kontenera kluczy kryptograficznych.|  
|[-keyfile](keyfile-compiler-option.md)|Określa nazwę pliku zawierającego klucz kryptograficzny.|  
|[-lib](lib-compiler-option.md)|Określa lokalizację zestawy, do których odwołuje się za pomocą klasy [— odwołanie](reference-compiler-option.md).|  
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilator, aby nie Importuj biblioteki standardowej (mscorlib.dll).|  
|[-reference](reference-compiler-option.md)|Importuje metadane z pliku, który zawiera zestaw.|  
|-analyzer|Uruchom analizatorów z tego zestawu (krótka wersja: /)|  
|-additionalfile|Nazwy dodatkowych plików bezpośrednio nie wpływają na generowanie kodu, które mogą być używane przez analizatory do produkcji błędy lub ostrzeżenia.|  
  
### <a name="debuggingerror-checking"></a>Sprawdzanie Debugowanie błędów  
  
|Opcja|Cel|  
|------------|-------------|  
|[-bugreport](bugreport-compiler-option.md)|Tworzy plik zawierający informacje, które ułatwia zgłosić usterkę.|  
|[-checked](checked-compiler-option.md)|Określa, czy liczba całkowita arytmetyczne, który przepełnienie granic o typie danych spowoduje, że wystąpił wyjątek w czasie wykonywania.|  
|[-debug](debug-compiler-option.md)|Poinstruuj kompilator Emituj informacje debugowania.|  
|[-errorreport](errorreport-compiler-option.md)|Ustawia zachowanie raportowania błędów.|  
|[-fullpaths](fullpaths-compiler-option.md)|Określa bezwzględną ścieżkę do pliku w danych wyjściowych kompilatora.|  
|[-nowarn](nowarn-compiler-option.md)|Pomija generację określonych ostrzeżeń kompilatora.|  
|[-warn](warn-compiler-option.md)|Ustawia poziom ostrzeżeń.|  
|[-warnaserror](warnaserror-compiler-option.md)|Zamienia ostrzeżenia błędy.|  
|zestaw reguł-:\<pliku >|Określ plik zestaw reguł, który powoduje wyłączenie diagnostyczne zależne.|  
  
### <a name="preprocessor"></a>Preprocesor  
  
|Opcja|Cel|  
|------------|-------------|  
|[-define](define-compiler-option.md)|Definiuje symbole preprocesora.|  
  
### <a name="resources"></a>Zasoby  
  
|Opcja|Cel|  
|------------|-------------|  
|[-link](link-compiler-option.md)|Udostępnia informacje o typie modelu COM w określonych zestawów do projektu.|  
|[-linkresource](linkresource-compiler-option.md)|Tworzy łącze do zasobów zarządzanych.|  
|[-resource](resource-compiler-option.md)|Osadza zasobu .NET Framework do pliku wyjściowego.|  
|[-win32icon](win32icon-compiler-option.md)|Określa plik .ico, aby wstawić do pliku wyjściowego.|  
|[-win32res](win32res-compiler-option.md)|Określa zasób Win32 do wstawienia do pliku wyjściowego.|  
  
### <a name="miscellaneous"></a>Różne  
  
|Opcja|Cel|  
|------------|-------------|  
|[@](response-file-compiler-option.md)|Określa plik odpowiedzi.|  
|[-?](help-compiler-option.md)|Wyświetla listę opcji kompilatora stdout.|  
|[-baseaddress](baseaddress-compiler-option.md)|Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL.|  
|[-codepage](codepage-compiler-option.md)|Określa stronę kodową do używania wszystkich plików kodu źródłowego w kompilacji.|  
|[-help](help-compiler-option.md)|Wyświetla listę opcji kompilatora stdout.|  
|[-highentropyva](highentropyva-compiler-option.md)|Określa, że plik wykonywalny obsługuje randomizacji układu przestrzeni adresowej (ASLR).|  
|[-langversion](langversion-compiler-option.md)|Określ tryb wersji języka: domyślny, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1 lub najnowsze |  
|[-main](main-compiler-option.md)|Określa lokalizację **Main** metody.|  
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilator, aby nie kompilacji z csc.rsp.|  
|[-nologo](nologo-compiler-option.md)|Pomija informacje transparentu kompilatora.|  
|[-recurse](recurse-compiler-option.md)|Podkatalogi wyszukiwania dla plików źródłowych do skompilowania.|  
|[-subsystemversion](subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, który można użyć pliku wykonywalnego.|  
|[-unsafe](unsafe-compiler-option.md)|Włącza kompilację kodu korzystającego z [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe.|  
|[-utf8output](utf8output-compiler-option.md)|Wyświetla kompilatora, dane wyjściowe przy użyciu kodowania UTF-8.|  
|-równoległe [+&#124;—]|Określa, czy używać współbieżnych kompilacji (+).|  
|-checksumalgorithm:\<alg >|Określ algorytm oblicza sumę kontrolną pliku źródłowego, przechowywane w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (ustawienie domyślne) lub SHA256.|  
  
## <a name="obsolete-options"></a>Opcje przestarzałe  
  
|Opcja|Cel|  
|---|---|  
|-przyrostowe|Włącza kompilację przyrostową.|  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](index.md)  
 [Opcje kompilatora C# w porządku alfabetycznym](listed-alphabetically.md)  
 [Instrukcje: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
