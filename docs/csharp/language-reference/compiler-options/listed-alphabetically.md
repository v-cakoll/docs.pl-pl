---
title: Opcje kompilatora C# w porządku alfabetycznym
ms.date: 05/15/2018
helpviewer_keywords:
- compiler options [C#], listed alphabetically
- C# language, compiler options listed alphabetically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
ms.openlocfilehash: d6d471cd27f35de6325a130e6c909d13cb1dcc85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972741"
---
# <a name="c-compiler-options-listed-alphabetically"></a>Opcje kompilatora C# w porządku alfabetycznym

Następujące opcje kompilatora są sortowane alfabetycznie. Aby uzyskać listę kategorii, zobacz [Opcje kompilatora C# wymienione według kategorii](listed-by-category.md).

|Opcja|Przeznaczenie|
|------------|-------------|
|[@](response-file-compiler-option.md)|Odczytuje plik odpowiedzi, aby uzyskać więcej opcji.|
|[-?](help-compiler-option.md)|Wyświetla komunikat użycia do stdout.|
|-additionalfile|Nazwy dodatkowych plików, które nie mają bezpośredniego wpływu na generowanie kodu, ale mogą być używane przez analizatory do tworzenia błędów lub ostrzeżeń.|
|[-addmodule (moduł addmodule)](addmodule-compiler-option.md)|Łączy określone moduły z tym zespołem|
|-analizator|Uruchom analizatory z tego złożenia (skrócona forma: -a)|
|[-appconfig](appconfig-compiler-option.md)|Określa lokalizację pliku app.config w czasie wiązania zestawu.|
|[-adres bazowy](baseaddress-compiler-option.md)|Określa adres podstawowy dla biblioteki, która ma zostać zbudowana.|
|[-raport błędów](bugreport-compiler-option.md)|Tworzy plik "Raport o błędzie". Ten plik zostanie wysłany wraz z wszelkimi informacjami o awarii, jeśli jest używany z -errorreport:prompt lub -errorreport:send.|
|[-sprawdzone](checked-compiler-option.md)|Powoduje, że kompilator do generowania kontroli przepełnienia.|
|-checksumalgorithm:\<alg>|Określa algorytm obliczania sumy kontrolnej pliku źródłowego przechowywanej w PDB.  Obsługiwane wartości to: SHA256 (domyślnie) lub SHA1.<br>Ze względu na problemy z kolizją z SHA1, Microsoft zaleca SHA256. |
|[-strona kodowa](codepage-compiler-option.md)|Określa stronę kodową, która ma być używana podczas otwierania plików źródłowych.|
|[-debug](debug-compiler-option.md)|Emituje informacje o debugowaniu.|
|[-zdefiniować](define-compiler-option.md)|Definiuje symbole kompilacji warunkowej.|
|[-delaysign](delaysign-compiler-option.md)|Delay-signs zestawu przy użyciu tylko publicznej części klucza silnej nazwy.|
|[-deterministic](deterministic-compiler-option.md)|Powoduje, że kompilator do danych wyjściowych zestawu, którego zawartość binarna jest identyczna w kompilacjach, jeśli dane wejściowe są identyczne.|
|[-doc](doc-compiler-option.md)|Określa plik dokumentacji XML do wygenerowania.|
|-osadzanie|Osadzanie wszystkich plików źródłowych w pdb.|
|-embed:\<lista plików>|Osadzanie określonych plików w pdb.|
|-errorendlocation (lokalizacja)|Linia wyjściowa i kolumna lokalizacji końcowej każdego błędu.|
|-errorlog:\<plik>|Określ plik do rejestrowania wszystkich diagnostyki kompilatora i analizatora.|
|[-raport o błędach](errorreport-compiler-option.md)|Określa sposób obsługi błędów kompilatora wewnętrznego: monit, wyślij lub brak. Wartość domyślna to brak.|
|[-filealign (wyrównanie pliku)](filealign-compiler-option.md)|Określa wyrównanie używane dla sekcji plików wyjściowych.|
|[-fullpaths](fullpaths-compiler-option.md)|Powoduje, że kompilator do generowania ścieżek w pełni kwalifikowane.|
|[-pomoc](help-compiler-option.md)|Wyświetla komunikat użycia do stdout.|
|[-highentropyva](highentropyva-compiler-option.md)|Określa, że wysoka entropia ASLR jest obsługiwana.|
|-przyrostowe|Umożliwia kompilację przyrostową [przestarzałą].|
|[-pojemnik na klucze](keycontainer-compiler-option.md)|Określa kontener kluczy o silnej nazwie.|
|[-plik klucza](keyfile-compiler-option.md)|Określa plik klucza silnej nazwy.|
|[-langversion:\<>naciąganie](langversion-compiler-option.md)|Określ wersję językową: Domyślnie, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1, 7.2, 7.3 lub Najnowsze |
|[-lib](lib-compiler-option.md)|Określa dodatkowe katalogi, w których mają być wyszukiwane odwołania.|
|[-link](link-compiler-option.md)|Udostępnia informacje o typie COM w określonych zestawach do projektu.|
|[-linkresource](linkresource-compiler-option.md)|Łączy określony zasób z tym zestawem.|
|[-main](main-compiler-option.md)|Określa typ, który zawiera punkt wejścia (zignoruj wszystkie inne możliwe punkty wejścia).|
|[-nazwa montażu modułu](moduleassemblyname-compiler-option.md)|Określa zestaw, do którego niepubliczne typy .netmodule mogą uzyskać dostęp.|
|-nazwa modułu:\<ciąg>|Określ nazwę modułu źródłowego|
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilator, aby nie zawierał automatycznie CSC. rsp.|
|[-nologo](nologo-compiler-option.md)|Pomija komunikat o prawach autorskich kompilatora.|
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilator, aby nie odwoływał się do standardowej biblioteki (mscorlib.dll).|
|[-nowarn](nowarn-compiler-option.md)|Wyłącza określone komunikaty ostrzegawcze|
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Instruuje kompilator, aby nie osadzał manifestu aplikacji w pliku wykonywalnym.|
|[-optymalizacja](optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|
|[-na zewnątrz](out-compiler-option.md)|Określa nazwę pliku wyjściowego (domyślnie: nazwa podstawowa pliku z klasą główną lub pierwszym plikiem).|
|-równolegle[+&#124;-]|Określa, czy ma być używana współbieżna kompilacja (+).|
|[-pathmap](pathmap-compiler-option.md)|Określa mapowanie dla nazw ścieżek źródłowych danych wyjściowych przez kompilator.|
|[-pdb](pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku pdb.|
|[-platforma](platform-compiler-option.md)|Limity platform, na których można uruchomić ten kod: x86, Itanium, x64, anycpu lub anycpu32bitpreferred. Wartością domyślną jest dowolnyprocesor.|
|[-preferreduilang](preferreduilang-compiler-option.md)|Określa język, który ma być używany dla danych wyjściowych kompilatora.|
|[-publicsign](publicsign-compiler-option.md)|Zastosuj klucz publiczny bez podpisywania zestawu, ale ustaw bit w złożeniu wskazujący, że zestaw jest podpisany.|
|[-recurse](recurse-compiler-option.md)|Zawiera wszystkie pliki w bieżącym katalogu i podkatalogi zgodnie ze specyfikacjami symboli wieloznacznych.|
|[-odniesienie](reference-compiler-option.md)|Odwołuje się do metadanych z określonych plików zestawu.|
|[-refout](refout-compiler-option.md)|Wygeneruj zespół odniesienia oprócz złożenia podstawowego.|
|[-refonly](refonly-compiler-option.md)|Wygeneruj złożenie odniesienia zamiast zestawu podstawowego.|
|-analizator raportów|Zgłoś dodatkowe informacje o analizatorze, takie jak czas wykonania.|
|[-zasób](resource-compiler-option.md)|Osadza określony zasób.|
|-ruleset:\<plik>|Określ plik zestawu reguł, który wyłącza określoną diagnostykę.|
|[-subsystemversion](subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, z którego może korzystać plik wykonywalny.|
|[-cel](target-compiler-option.md)|Określa format pliku wyjściowego za pomocą jednej z czterech opcji: [-target:appcontainerexe](target-appcontainerexe-compiler-option.md), [-target:exe](target-exe-compiler-option.md), [-target:library](target-library-compiler-option.md), [-target:module](target-module-compiler-option.md), [-target:winexe](target-winexe-compiler-option.md), [-target:winmdobj](target-winmdobj-compiler-option.md).|
|[-niebezpieczne](unsafe-compiler-option.md)|Zezwala na [niebezpieczny](../keywords/unsafe.md) kod.|
|[-utf8output](utf8output-compiler-option.md)|Wygeneruje komunikaty kompilatora w kodowaniu UTF-8.|
|-Wersja|Wyświetla numer wersji kompilatora i wyjście.|
|[-warn](warn-compiler-option.md)|Ustawia poziom ostrzeżenia (0-4).|
|[-warnaserror](warnaserror-compiler-option.md)|Zgłasza określone ostrzeżenia jako błędy.|
|[-win32icon](win32icon-compiler-option.md)|Używa tej ikony dla danych wyjściowych.|
|[-win32manifest](win32manifest-compiler-option.md)|Określa niestandardowy plik manifestu win32.|
|[-win32res](win32res-compiler-option.md)|Określa plik zasobu win32 (.res).|

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](index.md)
- [Opcje kompilatora C# w rozbiciu na kategorie](listed-by-category.md)
- [Porada: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [\<kompilator> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
