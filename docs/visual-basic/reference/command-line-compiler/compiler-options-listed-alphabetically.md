---
title: Opcje kompilatora w porządku alfabetycznym
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: 85fb07f46c2d885491db7358f24b3b50836c2ca8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937755"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Opcje kompilatora Visual Basic w porządku alfabetycznym
Kompilator Visual Basic wiersza polecenia jest dostępny jako alternatywa dla kompilowania programów z zintegrowanego środowiska programistycznego (IDE) programu Visual Studio. Poniżej znajduje się lista opcji kompilatora wiersza polecenia Visual Basic sortowanych alfabetycznie.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Opcja|Przeznaczenie|  
|------------|-------------|  
|[@ (określenie pliku odpowiedzi)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Określa plik odpowiedzi.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest takie samo jak określenie `-help` opcji. Nie wystąpi kompilacja.|  
|`-additionalfile`|Nazywa dodatkowe pliki, które nie wpływają bezpośrednio na generowanie kodu, ale mogą być używane przez analizatory do tworzenia błędów lub ostrzeżeń.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Powoduje, że kompilator udostępnił wszystkie informacje o typie z określonych plików dla aktualnie kompilowanego projektu.|  
|`-analyzer`|Uruchom analizatory z tego zestawu (krótka wersja:-a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Określa adres podstawowy biblioteki DLL.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Tworzy plik zawierający informacje, które ułatwiają zgłoszenie błędu.|  
|`-checksumalgorithm:<alg>`|Określ algorytm obliczania sumy kontrolnej plików źródłowych przechowywanej w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (domyślnie) lub SHA256. <br>Ze względu na kolizje problemów z algorytmem SHA1 firma Microsoft zaleca SHA256ą lub lepszą.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Generuje informacje o debugowaniu.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definiuje symbole dla kompilacji warunkowej.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Określa, czy zestaw zostanie podpisany całkowicie czy częściowo.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Powoduje, że kompilator wyprowadza zestaw, którego zawartość binarna jest taka sama w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Przetwarza komentarze dokumentacji do pliku XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Określa sposób, w jaki kompilator Visual Basic powinien raportować wewnętrzne błędy kompilatora.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Określa, gdzie mają być wyrównane sekcje pliku wyjściowego.|  
|[-Pomoc](../../../visual-basic/reference/command-line-compiler/help.md)|Wyświetla opcje kompilatora. To polecenie jest takie samo jak określenie `-?` opcji. Nie wystąpi kompilacja.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Wskazuje, czy określony plik wykonywalny obsługuje generowanie losowe układu przestrzeni adresowej o wysokiej entropii (ASLR).|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importuje przestrzeń nazw z określonego zestawu.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Określa nazwę kontenera kluczy, aby nadać zestawowi silną nazwę.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Określa plik, który zawiera parę kluczy lub kluczy, aby nadać zestawowi silną nazwę.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Określ wersję językową: 9&#124;9,0&#124;10&#124;10,0&#124;11&#124;11,0.|  
|[-LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md)|Określa lokalizację zestawów, do których odwołuje się opcja [-Reference](../../../visual-basic/reference/command-line-compiler/reference.md) .|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Tworzy łącze do zarządzanego zasobu.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Określa klasę, która zawiera `Sub Main` procedurę używaną podczas uruchamiania.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Określa nazwę zestawu, którego częścią ma być moduł.|  
|`-modulename:<string>`|Określ nazwę modułu źródłowego|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Ustawia kompilator jako docelowy .NET Compact Framework.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|Nie Kompiluj z VBC. rsp.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Pomija informacje transparentu kompilatora.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Powoduje, że kompilator nie odwołuje się do bibliotek standardowych.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Pomija możliwość generowania ostrzeżeń przez kompilator.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Instruuje kompilator, aby nie osadzał żadnego manifestu aplikacji w pliku wykonywalnym.|  
|[-Optymalizuj](../../../visual-basic/reference/command-line-compiler/optimize.md)|Włącza/wyłącza optymalizację kodu.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Określa, czy porównania ciągów powinny być binarne, czy używać semantyki tekstu specyficznego dla ustawień regionalnych.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Wymusza jawną deklarację zmiennych.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Umożliwia korzystanie z wnioskowania o typie lokalnym w deklaracjach zmiennych.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Wymusza ścisłą semantykę języka.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Określa plik wyjściowy.|  
|<code>-parallel[+&#124;-]</code>|Określa, czy ma być używana współbieżna kompilacja (+).|  
|[-Platforma](../../../visual-basic/reference/command-line-compiler/platform.md)|Określa platformę procesora, która jest elementem docelowym kompilatora dla pliku wyjściowego.|  
|`-preferreduilang`|Określ nazwę preferowanego języka wyjściowego.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Zapobiega wyświetlaniu przez kompilator kodu dla błędów i ostrzeżeń związanych z składnią.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Wyszukuje w podkatalogach pliki źródłowe do skompilowania.|  
|[-odwołanie](../../../visual-basic/reference/command-line-compiler/reference.md)|Importuje metadane z zestawu.|  
|[-refonly](refonly-compiler-option.md)|Wyprowadza tylko zestaw referencyjny.|
|[-refout](refout-compiler-option.md)|Określa ścieżkę wyjściową zestawu odwołania.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Wyłącza sprawdzanie przepełnienia liczby całkowitej.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Osadza zasób zarządzany w zestawie.|  
|[-RootNamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Określa przestrzeń nazw dla wszystkich deklaracji typu.|  
|`-ruleset:<file>`|Określ plik zestawu reguł, który wyłącza określoną diagnostykę.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Określa lokalizację plików mscorlib. dll i Microsoft. VisualBasic. dll.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Określa minimalną wersję podsystemu, która może być używana przez wygenerowany plik wykonywalny.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Określa format pliku wyjściowego.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Wyświetla dane wyjściowe kompilatora przy użyciu kodowania UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Określa, że kompilator ma kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic lub z odwołaniem do określonej biblioteki środowiska uruchomieniowego.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Wyświetla dodatkowe informacje podczas kompilacji.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Podwyższa poziom ostrzeżeń do błędów.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Wstawia plik. ico do pliku wyjściowego.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identyfikuje zdefiniowany przez użytkownika plik manifestu aplikacji Win32, który ma zostać osadzony w przenośnym pliku wykonywalnym (PE) projektu.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Wstawia zasób Win32 do pliku wyjściowego.|  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Visual Basic według kategorii](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
