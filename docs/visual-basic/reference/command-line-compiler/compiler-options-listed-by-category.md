---
title: Opcje kompilatora Visual Basic według kategorii
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: d8a1e36c0932de9bf50c109ea979a1e358795388
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331546"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Opcje kompilatora Visual Basic wymienione według kategorii
Kompilator wiersza polecenia Visual Basic jest dostarczany jako alternatywa dla kompilowania programów z poziomu zintegrowanego środowiska programistycznego (IDE) programu Visual Studio. Poniżej znajduje się lista opcji kompilatora wiersza polecenia Visual Basic posortowanych według kategorii funkcjonalnej.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Dane wyjściowe kompilatora  
  
|Opcja|Cel|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Pomija informacje transparentu kompilatora.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Wyświetla dane wyjściowe kompilatora przy użyciu kodowania UTF-8.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Wyświetla dodatkowe informacje podczas kompilacji.|  
|`-modulename:<string>`|Określ nazwę modułu źródłowego|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Określ język dla danych wyjściowych kompilatora.|
  
## <a name="optimization"></a>optymalizacja  
  
|Opcja|Cel|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Określa, gdzie mają być wyrównane sekcje pliku wyjściowego.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Włącza/wyłącza optymalizacje.|  
  
## <a name="output-files"></a>Pliki wyjściowe  
  
|Opcja|Cel|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Przetwarzaj komentarze dokumentacji do pliku XML.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Ustawia kompilator jako docelowy .NET Compact Framework.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Określa plik wyjściowy.|  
|[-refonly](refonly-compiler-option.md)|Wyprowadza tylko zestaw referencyjny.|
|[-refout](refout-compiler-option.md)|Określa ścieżkę wyjściową zestawu odwołania.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Określa format danych wyjściowych.|  
  
## <a name="net-assemblies"></a>Zestawy .NET  
  
|Opcja|Cel|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Powoduje, że kompilator udostępnił wszystkie informacje o typie z określonych plików dla aktualnie kompilowanego projektu.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importuje przestrzeń nazw z określonego zestawu.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Określa nazwę kontenera kluczy, aby nadać zestawowi silną nazwę.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Określa plik zawierający parę klucz lub klucz, aby nadać zestawowi silną nazwę.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Określa lokalizację zestawów, do których odwołuje się opcja [-Reference](../../../visual-basic/reference/command-line-compiler/reference.md) .|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importuje metadane z zestawu.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Określa nazwę zestawu, którego częścią ma być moduł.|  
|`-analyzer`|Uruchom analizatory z tego zestawu (krótka wersja:-a)|  
|`-additionalfile`|Nazywa dodatkowe pliki, które nie wpływają bezpośrednio na generowanie kodu, ale mogą być używane przez analizatory do tworzenia błędów lub ostrzeżeń.|  
  
## <a name="debuggingerror-checking"></a>Debugowanie/sprawdzanie błędów  
  
|Opcja|Cel|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Tworzy plik zawierający informacje, które ułatwiają zgłoszenie błędu.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Generuje informacje o debugowaniu.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Pomija możliwość generowania ostrzeżeń przez kompilator.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Zapobiega wyświetlaniu przez kompilator kodu dla błędów i ostrzeżeń związanych z składnią.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Wyłącza sprawdzanie przepełnienia liczby całkowitej.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Podwyższa poziom ostrzeżeń do błędów.|  
|`-ruleset:<file>`|Określ plik zestawu reguł, który wyłącza określoną diagnostykę.|  
  
## <a name="help"></a>Help  
  
|Opcja|Cel|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest takie samo jak określenie `-help` opcji. Nie wystąpi kompilacja.|  
|[-help](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest takie samo jak określenie `-?` opcji. Nie wystąpi kompilacja.|  
  
## <a name="language"></a>Język  
  
|Opcja|Cel|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Określ wersję języka: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Wymusza jawną deklarację zmiennych.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Wymusza ścisłą semantykę typu.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Określa, czy porównania ciągów powinny być binarne, czy używać semantyki tekstu specyficznego dla ustawień regionalnych.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Umożliwia korzystanie z wnioskowania o typie lokalnym w deklaracjach zmiennych.|  
  
## <a name="preprocessor"></a>Preprocesor  
  
|Opcja|Cel|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definiuje symbole dla kompilacji warunkowej.|  
  
## <a name="resources"></a>Zasoby  
  
|Opcja|Cel|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Tworzy łącze do zarządzanego zasobu.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Osadza zasób zarządzany w zestawie.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Wstawia plik. ico do pliku wyjściowego.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Wstawia zasób Win32 do pliku wyjściowego.|  
  
## <a name="miscellaneous"></a>Różne  
  
|Opcja|Cel|  
|---|---|  
|[@ (określenie pliku odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Określa plik odpowiedzi.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Określa adres podstawowy biblioteki DLL.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Określa sposób, w jaki kompilator Visual Basic powinien raportować wewnętrzne błędy kompilatora.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Informuje jądro systemu Windows o tym, czy określony plik wykonywalny obsługuje losowe generowanie układu przestrzeni adresowej (ASLR).|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Określa klasę, która zawiera `Sub Main` procedurę używaną podczas uruchamiania.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nie Kompiluj z VBC. rsp|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Powoduje, że kompilator nie odwołuje się do bibliotek standardowych.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instruuje kompilator, aby nie osadzał żadnego manifestu aplikacji w pliku wykonywalnym.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Określa platformę procesora, która jest elementem docelowym kompilatora dla pliku wyjściowego.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Wyszukuje w podkatalogach pliki źródłowe do skompilowania.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Określa przestrzeń nazw dla wszystkich deklaracji typu.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Określa lokalizację plików mscorlib. dll i Microsoft. VisualBasic. dll.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Określa, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub z odwołaniem do określonej biblioteki środowiska uruchomieniowego.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identyfikuje zdefiniowany przez użytkownika plik manifestu aplikacji Win32, który ma zostać osadzony w przenośnym pliku wykonywalnym (PE) projektu.|  
|`-parallel[+&#124;-]`|Określa, czy ma być używana współbieżna kompilacja (+).|  
|`-checksumalgorithm:<alg>`|Określ algorytm obliczania sumy kontrolnej plików źródłowych przechowywanej w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (domyślnie) lub SHA256. <br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.|  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora Visual Basic w porządku alfabetycznym](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)
