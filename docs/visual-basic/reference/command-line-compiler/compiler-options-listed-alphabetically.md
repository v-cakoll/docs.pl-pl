---
title: Opcje kompilatora w porządku alfabetycznym
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: 19e14953c08f90ea1ab245fa3124a462ccba162f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408741"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Opcje kompilatora Visual Basic w porządku alfabetycznym
Kompilator Visual Basic wiersza polecenia jest dostępny jako alternatywa dla kompilowania programów z zintegrowanego środowiska programistycznego (IDE) programu Visual Studio. Poniżej znajduje się lista opcji kompilatora wiersza polecenia Visual Basic sortowanych alfabetycznie.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Opcja|Przeznaczenie|  
|------------|-------------|  
|[@ (określenie pliku odpowiedzi)](specify-response-file.md)|Określa plik odpowiedzi.|  
|[-?](help.md)|Wyświetla opcje kompilatora. To polecenie jest takie samo jak określenie `-help` opcji. Nie wystąpi kompilacja.|  
|`-additionalfile`|Nazywa dodatkowe pliki, które nie wpływają bezpośrednio na generowanie kodu, ale mogą być używane przez analizatory do tworzenia błędów lub ostrzeżeń.|  
|[-addmodule](addmodule.md)|Powoduje, że kompilator udostępnił wszystkie informacje o typie z określonych plików dla aktualnie kompilowanego projektu.|  
|`-analyzer`|Uruchom analizatory z tego zestawu (krótka wersja:-a)|  
|[-baseaddress](baseaddress.md)|Określa adres podstawowy biblioteki DLL.|  
|[-bugreport](bugreport.md)|Tworzy plik zawierający informacje, które ułatwiają zgłoszenie błędu.|  
|`-checksumalgorithm:<alg>`|Określ algorytm obliczania sumy kontrolnej plików źródłowych przechowywanej w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (domyślnie) lub SHA256. <br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.|  
|[-codepage](codepage.md)|Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji.|  
|[-Debuguj](debug.md)|Generuje informacje o debugowaniu.|  
|[-define](define.md)|Definiuje symbole dla kompilacji warunkowej.|  
|[-delaysign](delaysign.md)|Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.|  
|[-deterministic](deterministic.md)|Powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-doc](doc.md)|Przetwarza komentarze dokumentacji do pliku XML.|  
|[-errorreport](errorreport.md)|Określa sposób, w jaki kompilator Visual Basic powinien raportować wewnętrzne błędy kompilatora.|  
|[-filealign](filealign.md)|Określa, gdzie mają być wyrównane sekcje pliku wyjściowego.|  
|[-Pomoc](help.md)|Wyświetla opcje kompilatora. To polecenie jest takie samo jak określenie `-?` opcji. Nie wystąpi kompilacja.|  
|[-highentropyva](highentropyva.md)|Wskazuje, czy określony plik wykonywalny obsługuje generowanie losowe układu przestrzeni adresowej o wysokiej entropii (ASLR).|  
|[-imports](imports.md)|Importuje przestrzeń nazw z określonego zestawu.|  
|[-keycontainer](keycontainer.md)|Określa nazwę kontenera kluczy, aby nadać zestawowi silną nazwę.|  
|[-keyfile](keyfile.md)|Określa plik, który zawiera parę kluczy lub kluczy, aby nadać zestawowi silną nazwę.|  
|[-langversion](langversion.md)|Określ wersję językową: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-libpath](libpath.md)|Określa lokalizację zestawów, do których odwołuje się opcja [-Reference](reference.md) .|  
|[-linkresource](linkresource.md)|Tworzy łącze do zarządzanego zasobu.|  
|[-main](main.md)|Określa klasę, która zawiera `Sub Main` procedurę używaną podczas uruchamiania.|  
|[-moduleassemblyname](moduleassemblyname.md)|Określa nazwę zestawu, którego częścią ma być moduł.|  
|`-modulename:<string>`|Określ nazwę modułu źródłowego|  
|[-netcf](netcf.md)|Ustawia kompilator jako docelowy .NET Compact Framework.|  
|[-noconfig](noconfig.md)|Nie Kompiluj z VBC. rsp.|  
|[-nologo](nologo.md)|Pomija informacje transparentu kompilatora.|  
|[-nostdlib](nostdlib.md)|Powoduje, że kompilator nie odwołuje się do bibliotek standardowych.|  
|[-nowarn](nowarn.md)|Pomija możliwość generowania ostrzeżeń przez kompilator.|  
|[-nowin32manifest](nowin32manifest.md)|Instruuje kompilator, aby nie osadzał żadnego manifestu aplikacji w pliku wykonywalnym.|  
|[-Optymalizuj](optimize.md)|Włącza/wyłącza optymalizację kodu.|  
|[-optioncompare](optioncompare.md)|Określa, czy porównania ciągów powinny być binarne, czy używać semantyki tekstu specyficznego dla ustawień regionalnych.|  
|[-optionexplicit](optionexplicit.md)|Wymusza jawną deklarację zmiennych.|  
|[-optioninfer](optioninfer.md)|Umożliwia korzystanie z wnioskowania o typie lokalnym w deklaracjach zmiennych.|  
|[-optionstrict](optionstrict.md)|Wymusza ścisłą semantykę języka.|  
|[-out](out.md)|Określa plik wyjściowy.|  
|<code>-parallel[+&#124;-]</code>|Określa, czy ma być używana współbieżna kompilacja (+).|  
|[-Platforma](platform.md)|Określa platformę procesora, która jest elementem docelowym kompilatora dla pliku wyjściowego.|  
|`-preferreduilang`|Określ nazwę preferowanego języka wyjściowego.|  
|[-quiet](quiet.md)|Zapobiega wyświetlaniu przez kompilator kodu dla błędów i ostrzeżeń związanych z składnią.|  
|[-recurse](recurse.md)|Wyszukuje w podkatalogach pliki źródłowe do skompilowania.|  
|[-odwołanie](reference.md)|Importuje metadane z zestawu.|  
|[-refonly](refonly-compiler-option.md)|Wyprowadza tylko zestaw referencyjny.|
|[-refout](refout-compiler-option.md)|Określa ścieżkę wyjściową zestawu odwołania.|
|[-removeintchecks](removeintchecks.md)|Wyłącza sprawdzanie przepełnienia liczby całkowitej.|  
|[-zasób](resource.md)|Osadza zasób zarządzany w zestawie.|  
|[-rootnamespace](rootnamespace.md)|Określa przestrzeń nazw dla wszystkich deklaracji typu.|  
|`-ruleset:<file>`|Określ plik zestawu reguł, który wyłącza określoną diagnostykę.|  
|[-sdkpath](sdkpath.md)|Określa lokalizację plików mscorlib. dll i Microsoft. VisualBasic. dll.|  
|[-subsystemversion](subsystemversion.md)|Określa minimalną wersję podsystemu, która może być używana przez wygenerowany plik wykonywalny.|  
|[-target](target.md)|Określa format pliku wyjściowego.|  
|[-utf8output](utf8output.md)|Wyświetla dane wyjściowe kompilatora przy użyciu kodowania UTF-8.|  
|[-vbruntime](vbruntime.md)|Określa, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub z odwołaniem do określonej biblioteki środowiska uruchomieniowego.|  
|[-verbose](verbose.md)|Wyświetla dodatkowe informacje podczas kompilacji.|  
|[-warnaserror](warnaserror.md)|Podwyższa poziom ostrzeżeń do błędów.|  
|[-win32icon](win32icon.md)|Wstawia plik. ico do pliku wyjściowego.|  
|[-win32manifest](win32manifest.md)|Identyfikuje zdefiniowany przez użytkownika plik manifestu aplikacji Win32, który ma zostać osadzony w przenośnym pliku wykonywalnym (PE) projektu.|  
|[-win32resource](win32resource.md)|Wstawia zasób Win32 do pliku wyjściowego.|  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Visual Basic według kategorii](compiler-options-listed-by-category.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
