---
title: Opcje kompilatora Visual Basic według kategorii
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 9c46d557df35d575b28cc5843f82670613f62f91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551621"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Opcje kompilatora Visual Basic według kategorii
Kompilator wiersza polecenia programu Visual Basic jest dostarczany jako alternatywę do kompilowania programów z w ramach programu Visual Studio zintegrowane środowisko programistyczne (IDE). Oto lista opcje wiersza polecenia kompilatora Visual Basic, które są sortowane według kategorii funkcji.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Dane wyjściowe kompilatora  
  
|Opcja|Cel|  
|---|---|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Pomija informacji o transparencie kompilatora.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Kompilator wyświetla dane wyjściowe przy użyciu kodowania UTF-8.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Wyświetla dodatkowe informacje podczas kompilacji.|  
|`-modulename:<string>`|Określ nazwę modułu źródła|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Określanie języka danych wyjściowych kompilatora.|
  
## <a name="optimization"></a>Optymalizacja  
  
|Opcja|Cel|  
|---|---|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Określa, gdzie należy wyrównać sekcje pliku wyjściowego.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Włącza/wyłącza optymalizacje.|  
  
## <a name="output-files"></a>Pliki wyjściowe  
  
|Opcja|Cel|  
|---|---|  
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Przetwarzanie komentarzy dokumentacji do pliku XML.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Powoduje, że kompilator do wyjściowego zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Ustawia kompilatora z docelowym [!INCLUDE[Compact](~/includes/compact-md.md)].|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Określa plik wyjściowy.|  
|[-refonly](refonly-compiler-option.md)|Generuje zestaw odwołania.|
|[-refout](refout-compiler-option.md)|Określa ścieżkę wyjściową zestawu odwołania.|
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Określa format danych wyjściowych.|  
  
## <a name="net-assemblies"></a>Zestawów platformy .NET  
  
|Opcja|Cel|  
|---|---|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Powoduje, że kompilator udostępnia wszystkie informacje z określonego pliku lub plików dostępnych do aktualnie kompilowanemu projektowi typu.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importuje przestrzeń nazw z określonego zestawu.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Określa nazwę kontenera kluczy parę kluczy zapewnić zestawu z silną nazwą.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Określa plik zawierający klucz lub parę kluczy, aby zapewnić zestawu z silną nazwą.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Określa lokalizację zestawów odwołuje się [— dokumentacja](../../../visual-basic/reference/command-line-compiler/reference.md) opcji.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importuje metadane z zestawu.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Określa nazwę zestawu, który będzie należeć modułu.|  
|`-analyzer`|Uruchom analizatorów z tego zestawu (skrócona forma: -)|  
|`-additionalfile`|Nazwy dodatkowe pliki, bezpośrednio nie wpływa na generowanie kodu, które mogą być używane przez analizatory do produkcji, błędy lub ostrzeżenia.|  
  
## <a name="debuggingerror-checking"></a>Sprawdzanie Debugowanie błędów  
  
|Opcja|Cel|  
|---|---|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Tworzy plik, który zawiera informacje, które można łatwo Zgłoś usterkę.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Generuje informacje debugowania.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Pomija zdolność kompilatora do generowania ostrzeżeń.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Kompilator uniemożliwia wyświetlanie kodu dotyczące składni błędów i ostrzeżeń.|  
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Wyłącza sprawdzanie przepełnienia liczby całkowitej.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Podwyższa poziom ostrzeżeń do błędów.|  
|`-ruleset:<file>`|Określ plik zestawu reguł, który wyłącza działania diagnostyczne zależne.|  
  
## <a name="help"></a>Pomoc  
  
|Opcja|Cel|  
|---|---|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest taka sama jak określanie `-help` opcji. Kompilacja nie występuje.|  
|[-help](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest taka sama jak określanie `-?` opcji. Kompilacja nie występuje.|  
  
## <a name="language"></a>Język  
  
|Opcja|Cel|  
|---|---|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Określ wersję języka: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Wymusza jawnej deklaracji zmiennych.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Wymusza semantykę typów ścisłych.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Określa, czy porównań ciągów powinny być binarny korzystają bezpośrednio z semantyki tekstu specyficzne dla ustawień regionalnych.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Umożliwia użycie wnioskowania o typie lokalnym w deklaracjach zmiennych.|  
  
## <a name="preprocessor"></a>Preprocesor  
  
|Opcja|Cel|  
|---|---|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definiuje symbole dla kompilacji warunkowej.|  
  
## <a name="resources"></a>Resources  
  
|Opcja|Cel|  
|---|---|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Tworzy łącze do zarządzanego zasobem.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Osadza zasobów zarządzanych w zestawie.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Wstawia plik .ico do pliku wyjściowego.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Wstawia zasób Win32 do pliku wyjściowego.|  
  
## <a name="miscellaneous"></a>Różne  
  
|Opcja|Cel|  
|---|---|  
|[@ (określenie pliku odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Określa plik odpowiedzi.|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Określa adres podstawowy biblioteki dll.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Określa stronę kodową do użycia dla wszystkich plikach kodu źródłowego w kompilacji.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Określa, jak kompilator języka Visual Basic powinno zgłosić wewnętrzne błędy kompilatora.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Informuje jądra Windows czy określonego pliku wykonywalnego obsługuje o wysokiej entropii adres miejsca układ losowe (ASLR).|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Określa klasę, która zawiera `Sub Main` procedury należy użyć przy uruchamianiu.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nie można skompilować przy użyciu Vbc.rsp|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Powoduje, że kompilator, aby nie odwoływać się do standardowych bibliotek.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instruuje kompilator, nie można osadzić manifest dowolnej aplikacji w pliku wykonywalnego.|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Określa platformę procesora kompilatora elementy docelowe pliku wyjściowego.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Podkatalogi wyszukiwania dla plików źródłowych do kompilowania.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Określa obszar nazw dla wszystkich deklaracji typów.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Określa lokalizację Mscorlib.dll i Microsoft.VisualBasic.dll.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Określa, czy kompilator powinien kompilować się bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub odwołanie do biblioteki środowiska uruchomieniowego określonych.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identyfikuje użytkownika aplikacji plik manifestu Win32 osadzanego do projektu przenośnych plików wykonywalnych (PE) pliku.|  
|`-parallel[+&#124;-]`|Określa, czy używać współbieżną kompilację (+).|  
|`-checksumalgorithm:<alg>`|Określić algorytm obliczania sumy kontrolnej pliku źródłowego, które zostały zapisane w pliku PDB.  Obsługiwane są następujące wartości: Algorytm SHA1 (domyślna) lub SHA256.|  
  
## <a name="see-also"></a>Zobacz także
- [Opcje kompilatora Visual Basic w porządku alfabetycznym](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)
- [Wprowadzenie do projektanta projektu](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))
- [Opcje kompilatora C# w porządku alfabetycznym](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
- [Opcje kompilatora C# w rozbiciu na kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)
