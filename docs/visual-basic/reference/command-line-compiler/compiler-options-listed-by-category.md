---
title: Opcje kompilatora w rozbiciu na kategorie
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 533d3da2f76854d311262ce97b43f240acab5f7d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408754"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a>Opcje kompilatora Visual Basic wymienione według kategorii
Kompilator wiersza polecenia Visual Basic jest dostarczany jako alternatywa dla kompilowania programów z poziomu zintegrowanego środowiska programistycznego (IDE) programu Visual Studio. Poniżej znajduje się lista opcji kompilatora wiersza polecenia Visual Basic posortowanych według kategorii funkcjonalnej.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a>Dane wyjściowe kompilatora  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[-nologo](nologo.md)|Pomija informacje transparentu kompilatora.|  
|[-utf8output](utf8output.md)|Wyświetla dane wyjściowe kompilatora przy użyciu kodowania UTF-8.|  
|[-verbose](verbose.md)|Wyświetla dodatkowe informacje podczas kompilacji.|  
|`-modulename:<string>`|Określ nazwę modułu źródłowego|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Określ język dla danych wyjściowych kompilatora.|
  
## <a name="optimization"></a>Optymalizacja  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[-filealign](filealign.md)|Określa, gdzie mają być wyrównane sekcje pliku wyjściowego.|  
|[-Optymalizuj](optimize.md)|Włącza/wyłącza optymalizacje.|  
  
## <a name="output-files"></a>Pliki wyjściowe  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[-doc](doc.md)|Przetwarzaj komentarze dokumentacji do pliku XML.|  
|[-deterministic](deterministic.md)|Powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-netcf](netcf.md)|Ustawia kompilator jako docelowy .NET Compact Framework.|  
|[-out](out.md)|Określa plik wyjściowy.|  
|[-refonly](refonly-compiler-option.md)|Wyprowadza tylko zestaw referencyjny.|
|[-refout](refout-compiler-option.md)|Określa ścieżkę wyjściową zestawu odwołania.|
|[-target](target.md)|Określa format danych wyjściowych.|  
  
## <a name="net-assemblies"></a>Zestawy .NET  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[-addmodule](addmodule.md)|Powoduje, że kompilator udostępnił wszystkie informacje o typie z określonych plików dla aktualnie kompilowanego projektu.|  
|[-delaysign](delaysign.md)|Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.|  
|[-imports](imports.md)|Importuje przestrzeń nazw z określonego zestawu.|  
|[-keycontainer](keycontainer.md)|Określa nazwę kontenera kluczy, aby nadać zestawowi silną nazwę.|  
|[-keyfile](keyfile.md)|Określa plik zawierający parę klucz lub klucz, aby nadać zestawowi silną nazwę.|  
|[-libpath](libpath.md)|Określa lokalizację zestawów, do których odwołuje się opcja [-Reference](reference.md) .|  
|[-odwołanie](reference.md)|Importuje metadane z zestawu.|  
|[-moduleassemblyname](moduleassemblyname.md)|Określa nazwę zestawu, którego częścią ma być moduł.|  
|`-analyzer`|Uruchom analizatory z tego zestawu (krótka wersja:-a)|  
|`-additionalfile`|Nazywa dodatkowe pliki, które nie wpływają bezpośrednio na generowanie kodu, ale mogą być używane przez analizatory do tworzenia błędów lub ostrzeżeń.|  
  
## <a name="debuggingerror-checking"></a>Debugowanie/sprawdzanie błędów  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[-bugreport](bugreport.md)|Tworzy plik zawierający informacje, które ułatwiają zgłoszenie błędu.|  
|[-Debuguj](debug.md)|Generuje informacje o debugowaniu.|  
|[-nowarn](nowarn.md)|Pomija możliwość generowania ostrzeżeń przez kompilator.|  
|[-quiet](quiet.md)|Zapobiega wyświetlaniu przez kompilator kodu dla błędów i ostrzeżeń związanych z składnią.|  
|[-removeintchecks](removeintchecks.md)|Wyłącza sprawdzanie przepełnienia liczby całkowitej.|  
|[-warnaserror](warnaserror.md)|Podwyższa poziom ostrzeżeń do błędów.|  
|`-ruleset:<file>`|Określ plik zestawu reguł, który wyłącza określoną diagnostykę.|  
  
## <a name="help"></a>Pomoc  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[-?](help.md)|Wyświetla opcje kompilatora. To polecenie jest takie samo jak określenie `-help` opcji. Nie wystąpi kompilacja.|  
|[-Pomoc](help.md)|Wyświetla opcje kompilatora. To polecenie jest takie samo jak określenie `-?` opcji. Nie wystąpi kompilacja.|  
  
## <a name="language"></a>Język  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[-langversion](langversion.md)|Określ wersję językową: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-optionexplicit](optionexplicit.md)|Wymusza jawną deklarację zmiennych.|  
|[-optionstrict](optionstrict.md)|Wymusza ścisłą semantykę typu.|  
|[-optioncompare](optioncompare.md)|Określa, czy porównania ciągów powinny być binarne, czy używać semantyki tekstu specyficznego dla ustawień regionalnych.|  
|[-optioninfer](optioninfer.md)|Umożliwia korzystanie z wnioskowania o typie lokalnym w deklaracjach zmiennych.|  
  
## <a name="preprocessor"></a>Preprocesor  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[-define](define.md)|Definiuje symbole dla kompilacji warunkowej.|  
  
## <a name="resources"></a>Zasoby  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[-linkresource](linkresource.md)|Tworzy łącze do zarządzanego zasobu.|  
|[-zasób](resource.md)|Osadza zasób zarządzany w zestawie.|  
|[-win32icon](win32icon.md)|Wstawia plik. ico do pliku wyjściowego.|  
|[-win32resource](win32resource.md)|Wstawia zasób Win32 do pliku wyjściowego.|  
  
## <a name="miscellaneous"></a>Różne  
  
|Opcja|Przeznaczenie|  
|---|---|  
|[@ (określenie pliku odpowiedzi)](specify-response-file.md)|Określa plik odpowiedzi.|  
|[-baseaddress](baseaddress.md)|Określa adres podstawowy biblioteki DLL.|  
|[-codepage](codepage.md)|Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji.|  
|[-errorreport](errorreport.md)|Określa sposób, w jaki kompilator Visual Basic powinien raportować wewnętrzne błędy kompilatora.|  
|[-highentropyva](highentropyva.md)|Informuje jądro systemu Windows o tym, czy określony plik wykonywalny obsługuje losowe generowanie układu przestrzeni adresowej (ASLR).|  
|[-main](main.md)|Określa klasę, która zawiera `Sub Main` procedurę używaną podczas uruchamiania.|  
|[-noconfig](noconfig.md)|Nie Kompiluj z VBC. rsp|  
|[-nostdlib](nostdlib.md)|Powoduje, że kompilator nie odwołuje się do bibliotek standardowych.|  
|[-nowin32manifest](nowin32manifest.md)|Instruuje kompilator, aby nie osadzał żadnego manifestu aplikacji w pliku wykonywalnym.|  
|[-Platforma](platform.md)|Określa platformę procesora, która jest elementem docelowym kompilatora dla pliku wyjściowego.|  
|[-recurse](recurse.md)|Wyszukuje w podkatalogach pliki źródłowe do skompilowania.|  
|[-rootnamespace](rootnamespace.md)|Określa przestrzeń nazw dla wszystkich deklaracji typu.|  
|[-sdkpath](sdkpath.md)|Określa lokalizację plików mscorlib. dll i Microsoft. VisualBasic. dll.|  
|[-vbruntime](vbruntime.md)|Określa, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub z odwołaniem do określonej biblioteki środowiska uruchomieniowego.|  
|[-win32manifest](win32manifest.md)|Identyfikuje zdefiniowany przez użytkownika plik manifestu aplikacji Win32, który ma zostać osadzony w przenośnym pliku wykonywalnym (PE) projektu.|  
|`-parallel[+&#124;-]`|Określa, czy ma być używana współbieżna kompilacja (+).|  
|`-checksumalgorithm:<alg>`|Określ algorytm obliczania sumy kontrolnej plików źródłowych przechowywanej w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (domyślnie) lub SHA256. <br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.|  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Visual Basic w porządku alfabetycznym](compiler-options-listed-alphabetically.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
