---
title: Opcje kompilatora Visual Basic w porządku alfabetycznym
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: 846d033c62d0168bab4661b9ab2b71a2139e2fcb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649819"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Opcje kompilatora Visual Basic w porządku alfabetycznym
Kompilator wiersza polecenia programu Visual Basic jest dostarczany jako alternatywę do kompilowania programów z programu Visual Studio zintegrowane środowisko programistyczne (IDE). Oto lista opcje wiersza polecenia kompilatora języka Visual Basic, sortowana alfabetycznie.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Opcja|Cel|  
|------------|-------------|  
|[@ (określenie pliku odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Określa plik odpowiedzi.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest taka sama jak określanie `-help` opcji. Kompilacja nie występuje.|  
|`-additionalfile`|Nazwy dodatkowe pliki, bezpośrednio nie wpływa na generowanie kodu, które mogą być używane przez analizatory do produkcji, błędy lub ostrzeżenia.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Powoduje, że kompilator udostępnia wszystkie informacje z określonego pliku lub plików dostępnych do aktualnie kompilowanemu projektowi typu.|  
|`-analyzer`|Uruchom analizatorów z tego zestawu (skrócona forma: -)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Określa adres podstawowy biblioteki dll.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Tworzy plik, który zawiera informacje, które można łatwo Zgłoś usterkę.|  
|`-checksumalgorithm:<alg>`|Określić algorytm obliczania sumy kontrolnej pliku źródłowego, które zostały zapisane w pliku PDB.  Obsługiwane są następujące wartości: Algorytm SHA1 (domyślna) lub SHA256.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Określa stronę kodową do użycia dla wszystkich plikach kodu źródłowego w kompilacji.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Generuje informacje debugowania.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definiuje symbole dla kompilacji warunkowej.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Powoduje, że kompilator do wyjściowego zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Przetwarza komentarze dokumentacji do pliku XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Określa, jak kompilator języka Visual Basic powinno zgłosić wewnętrzne błędy kompilatora.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Określa, gdzie należy wyrównać sekcje pliku wyjściowego.|  
|[-help](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest taka sama jak określanie `-?` opcji. Kompilacja nie występuje.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Wskazuje, czy określonego pliku wykonywalnego obsługuje o wysokiej entropii adres miejsca układ losowe (ASLR).|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importuje przestrzeń nazw z określonego zestawu.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Określa nazwę kontenera kluczy parę kluczy zapewnić zestawu z silną nazwą.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Określa plik, który zawiera klucz lub parę kluczy, aby zapewnić zestawu z silną nazwą.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Określ wersję języka: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Określa lokalizację zestawów odwołuje się [— dokumentacja](../../../visual-basic/reference/command-line-compiler/reference.md) opcji.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Tworzy łącze do zarządzanego zasobem.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Określa klasę, która zawiera `Sub Main` procedury należy użyć przy uruchamianiu.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Określa nazwę zestawu, który będzie należeć modułu.|  
|`-modulename:<string>`|Określ nazwę modułu źródła|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Ustawia kompilatora z docelowym [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nie można skompilować przy użyciu Vbc.rsp.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Pomija informacji o transparencie kompilatora.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Powoduje, że kompilator, aby nie odwoływać się do standardowych bibliotek.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Pomija zdolność kompilatora do generowania ostrzeżeń.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instruuje kompilator, nie można osadzić manifest dowolnej aplikacji w pliku wykonywalnego.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Włącza/wyłącza kodu optymalizacji.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Określa, czy porównań ciągów powinny być binarny korzystają bezpośrednio z semantyki tekstu specyficzne dla ustawień regionalnych.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Wymusza jawnej deklaracji zmiennych.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Umożliwia użycie wnioskowania o typie lokalnym w deklaracjach zmiennych.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Wymusza ścisłą semantykę języka.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Określa plik wyjściowy.|  
|`-parallel[+&#124;-]`|Określa, czy używać współbieżną kompilację (+).|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Określa platformę procesora kompilatora elementy docelowe pliku wyjściowego.|  
|`-preferreduilang`|Określ nazwę preferowanego języka wyjściowego.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Kompilator uniemożliwia wyświetlanie kodu dotyczące składni błędów i ostrzeżeń.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Podkatalogi wyszukiwania dla plików źródłowych do kompilowania.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importuje metadane z zestawu.|  
|[-refonly](refonly-compiler-option.md)|Generuje zestaw odwołania.|
|[-refout](refout-compiler-option.md)|Określa ścieżkę wyjściową zestawu odwołania.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Wyłącza sprawdzanie przepełnienia liczby całkowitej.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Osadza zasobów zarządzanych w zestawie.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Określa obszar nazw dla wszystkich deklaracji typów.|  
|`-ruleset:<file>`|Określ plik zestawu reguł, który wyłącza działania diagnostyczne zależne.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Określa lokalizację Mscorlib.dll i Microsoft.VisualBasic.dll.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Określa minimalną wersję podsystemu, którego wygenerowany plik wykonywalny może używać.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Określa format pliku wyjściowego.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Kompilator wyświetla dane wyjściowe przy użyciu kodowania UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Określa, czy kompilator powinien kompilować się bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub odwołanie do biblioteki środowiska uruchomieniowego określonych.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Wyświetla dodatkowe informacje podczas kompilacji.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Podwyższa poziom ostrzeżeń do błędów.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Wstawia plik .ico do pliku wyjściowego.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identyfikuje użytkownika aplikacji plik manifestu Win32 osadzanego do projektu przenośnych plików wykonywalnych (PE) pliku.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Wstawia zasób Win32 do pliku wyjściowego.|  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora Visual Basic według kategorii](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)
