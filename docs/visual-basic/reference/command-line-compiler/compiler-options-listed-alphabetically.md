---
title: Opcje kompilatora Visual Basic w porządku alfabetycznym
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc25ff282772cc82b8ebe5d59e729a6a48afa8f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Opcje kompilatora Visual Basic w porządku alfabetycznym
Kompilator wiersza polecenia programu Visual Basic podano zamiast kompilowanie programów z programu Visual Studio zintegrowane środowisko programistyczne (IDE). Poniżej znajduje się lista sortowana alfabetycznie opcje wiersza polecenia kompilatora Visual Basic.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Opcja|Cel|  
|------------|-------------|  
|[@ (określenie pliku odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Określa plik odpowiedzi.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest taki sam jak określenie `-help` opcji. Kompilacja nie występuje.|  
|`-additionalfile`|Nazwy dodatkowych plików bezpośrednio nie wpływają na generowanie kodu, które mogą być używane przez analizatory do produkcji błędy lub ostrzeżenia.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Powoduje, że kompilator wszystkie wpisz informacje z określonym dostępnych plików do projektu są obecnie kompilacji.|  
|`-analyzer`|Uruchom analizatorów z tego zestawu (krótka wersja: -)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Określa adres podstawowy biblioteki dll.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Tworzy plik zawierający informacje, które ułatwia zgłosić usterkę.|  
|`-checksumalgorithm:<alg>`|Określ algorytm oblicza sumę kontrolną pliku źródłowego, przechowywane w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (ustawienie domyślne) lub SHA256.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Określa stronę kodową do używania wszystkich plików kodu źródłowego w kompilacji.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Generuje informacje o debugowaniu.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definiuje symbole kompilacji warunkowej.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Powoduje, że kompilator output zestawu, którego zawartość binarna jest identyczna w kompilacji, jeśli dane wejściowe są identyczne.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Przetwarza komentarzy do dokumentacji do pliku XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Określa, jak kompilator Visual Basic powinien zgłosić wewnętrzne błędy kompilatora.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Określa lokalizację były wyrównane w sekcjach pliku wyjściowego.|  
|[-help](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest taki sam jak określenie `-?` opcji. Kompilacja nie występuje.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Wskazuje, czy określonego pliku wykonywalnego obsługuje wysokiej entropii losowe generowanie układu przestrzeni adresów (ASLR).|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importuje przestrzeni nazw z określonego zestawu.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Określa nazwę kontenera kluczy parę kluczy zapewnić silnej nazwy zestawu.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Określa plik, który zawiera klucz lub parę kluczy, aby zapewnić silnej nazwy zestawu.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Określ wersję językową: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Określa lokalizację zestawów odwołuje się [— odwołanie](../../../visual-basic/reference/command-line-compiler/reference.md) opcji.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Tworzy łącze do zasobów zarządzanych.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Określa klasę, która zawiera `Sub Main` procedurę do użycia podczas uruchamiania.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Określa nazwę zestawu, który będzie należeć modułu.|  
|`-modulename:<string>`|Określ nazwę modułu źródła|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Ustawia kompilatora do docelowego [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Kompiluje z Vbc.rsp.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Pomija informacje transparentu kompilatora.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Powoduje, że kompilator nie do standardowych bibliotek.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Pomija możliwość generowania ostrzeżeń kompilatora.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instruuje kompilator, aby nie osadzania manifestu żadnych aplikacji w pliku wykonywalnego.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Włącza/wyłącza kodu optymalizacji.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Określa, czy porównywanie ciągów powinna być binarnego lub korzystają bezpośrednio z semantyki tekst specyficzne dla ustawień regionalnych.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Wymusza jawnej deklaracji zmiennych.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Umożliwia użycie wnioskowania o typie lokalnym w deklaracjach zmiennych.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Wymusza ścisłą semantykę języka.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Określa plik wyjściowy.|  
|`-parallel[+&#124;-]`|Określa, czy używać współbieżnych kompilacji (+).|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Określa platformę procesora kompilatora docelowe pliku wyjściowego.|  
|`-preferreduilang`|Określ nazwę preferowanego języka wyjściowego.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Uniemożliwia wyświetlanie kodu dotyczące składni błędów i ostrzeżeń kompilatora.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Podkatalogi wyszukiwania dla plików źródłowych do skompilowania.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importuje metadane z zestawu.|  
|[-refonly](refonly-compiler-option.md)|Generuje zestaw odwołania.|
|[-refout](refout-compiler-option.md)|Ścieżka danych wyjściowych zestaw odwołania.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Wyłącza sprawdzanie przepełnienia liczby całkowitej.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Osadza zarządzanego zasobu w zestawie.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Określa przestrzeń nazw dla wszystkich deklaracji typów.|  
|`-ruleset:<file>`|Określ plik zestaw reguł, który powoduje wyłączenie diagnostyczne zależne.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Określa lokalizację pliku Mscorlib.dll i pliku Microsoft.VisualBasic.dll.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Określa minimalną wersję podsystemu używanego w wygenerowanym pliku wykonywalnego.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Określa format pliku wyjściowego.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Wyświetla kompilatora, dane wyjściowe przy użyciu kodowania UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Określa, że kompilator powinien kompilować bez odwołanie w Visual Basic Runtime Library lub odwołanie do biblioteki środowiska uruchomieniowego określonych.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Wyświetla dodatkowe informacje podczas kompilacji.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Zamienia ostrzeżenia błędy.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Wstawia plik .ico do pliku wyjściowego.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identyfikuje użytkownika aplikacji plik manifestu Win32 do osadzenia pliku przenośny plik wykonywalny (PE) projektu.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Wstawia zasobów Win32 do pliku wyjściowego.|  
  
## <a name="see-also"></a>Zobacz także  
 [Opcje kompilatora Visual Basic według kategorii](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)  
 [Wprowadzenie do projektanta projektu](http://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7)  
 [Opcje kompilatora C# w porządku alfabetycznym](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Opcje kompilatora C# w rozbiciu na kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)
