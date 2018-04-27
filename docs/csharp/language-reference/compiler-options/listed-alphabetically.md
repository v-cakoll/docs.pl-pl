---
title: Opcje kompilatora C# w porządku alfabetycznym
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- compiler options [C#], listed alpabetically
- C# language, compiler options listed alphabitically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: deffa6556d02cd5449d4bc91cf051a591b1c333e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="c-compiler-options-listed-alphabetically"></a>Opcje kompilatora C# w porządku alfabetycznym
Następujące opcje kompilatora są sortowane w kolejności alfabetycznej. Lista kategorii, [C# kompilatora opcje rozbiciu na kategorie](listed-by-category.md).  
  
|Opcja|Cel|  
|------------|-------------|  
|[@](response-file-compiler-option.md)|Odczytuje plik odpowiedzi, aby wyświetlić więcej opcji.|  
|[-?](help-compiler-option.md)|Wyświetla komunikat o sposobie użycia stdout.|  
|-additionalfile|Nazwy dodatkowych plików bezpośrednio nie wpływają na generowanie kodu, które mogą być używane przez analizatory do produkcji błędy lub ostrzeżenia.|  
|[-addmodule](addmodule-compiler-option.md)|Łączy określone moduły z tym zestawem|  
|-analyzer|Uruchom analizatorów z tego zestawu (krótka wersja: -)|  
|[-appconfig](appconfig-compiler-option.md)|Określa lokalizację pliku app.config w czasie powiązanie zestawu.|  
|[-baseaddress](baseaddress-compiler-option.md)|Określa adres podstawowy biblioteki, który ma zostać utworzony.|  
|[-bugreport](bugreport-compiler-option.md)|Tworzy plik "Usterek — raport". Ten plik zostanie wysłana wraz z informacjami awarii, jeśli jest używana z - errorreport: wiersz lub - errorreport: wysyłania.|  
|[-checked](checked-compiler-option.md)|Umożliwia kompilatorowi Generowanie sprawdzanie nadmiaru dla operacji.|  
|-checksumalgorithm:\<alg >|Określ algorytm oblicza sumę kontrolną pliku źródłowego, przechowywane w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (ustawienie domyślne) lub SHA256.|  
|[-codepage](codepage-compiler-option.md)|Określa stronę kodową do używania podczas otwierania plików źródłowych.|  
|[-debug](debug-compiler-option.md)|Emituje informacje o debugowaniu.|  
|[-define](define-compiler-option.md)|Definiuje symbole kompilacji warunkowej.|  
|[-delaysign](delaysign-compiler-option.md)|Opóźnienie znaki zestawu za pomocą tylko publicznej części klucza silnej nazwy.|  
|[-deterministyczna](deterministic-compiler-option.md)|Powoduje, że kompilator output zestawu, którego zawartość binarna jest identyczna w kompilacji, jeśli dane wejściowe są identyczne.|
|[-doc](doc-compiler-option.md)|Określa plik dokumentacji XML do wygenerowania.|  
|[-errorreport](errorreport-compiler-option.md)|Określa sposób obsługiwać wewnętrzne błędy kompilatora: wiersza, Wyślij lub none. Domyślna wartość to Brak.|  
|[-filealign](filealign-compiler-option.md)|Określa wyrównanie używane w sekcjach pliku wyjściowego.|  
|[-fullpaths](fullpaths-compiler-option.md)|Umożliwia kompilatorowi Generowanie pełni kwalifikowane ścieżki.|  
|[-help](help-compiler-option.md)|Wyświetla komunikat o sposobie użycia stdout.|  
|[-highentropyva](highentropyva-compiler-option.md)|Określa, że wysokiej entropii ASLR jest obsługiwana.|  
|-przyrostowe|Włącza kompilację przyrostową [przestarzały].|  
|[-keycontainer](keycontainer-compiler-option.md)|Określa kontener klucza o silnej nazwie.|  
|[-keyfile](keyfile-compiler-option.md)|Określa plik klucza o silnej nazwie.|  
|[-langversion:\<ciąg >](langversion-compiler-option.md)|Określ tryb wersji języka: domyślny, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1 lub najnowsze |  
|[-lib](lib-compiler-option.md)|Określa dodatkowe katalogi, w których będą poszukiwane odwołań.|  
|[-link](link-compiler-option.md)|Udostępnia informacje o typie modelu COM w określonych zestawów do projektu.|  
|[-linkresource](linkresource-compiler-option.md)|Dołącza określony zasób z tym zestawem.|  
|[-main](main-compiler-option.md)|Określa typ zawierający punkt wejścia (Ignoruj wszystkie pozostałe możliwe punkty wejścia).|  
|[-moduleassemblyname](moduleassemblyname-compiler-option.md)|Określa, których typy niepublicznych modułu .netmodule mogą uzyskiwać dostęp do zestawu.|  
|-modulename:\<ciąg >|Określ nazwę modułu źródła|  
|[-noconfig](noconfig-compiler-option.md)|Instruuje kompilator, nie można automatycznie dołączyć CSC. Źródło pliku.|  
|[-nologo](nologo-compiler-option.md)|Pomija komunikat o prawach autorskich kompilatora.|  
|[-nostdlib](nostdlib-compiler-option.md)|Instruuje kompilator, aby nie odwołanie do biblioteki standardowej (mscorlib.dll).|  
|[-nowarn](nowarn-compiler-option.md)|Wyłącza określone komunikaty ostrzegawcze|  
|[-nowin32manifest](nowin32manifest-compiler-option.md)|Instruuje kompilator, aby nie Osadź manifest aplikacji w pliku wykonywalnego.|  
|[-optimize](optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|  
|[-out](out-compiler-option.md)|Określa nazwę pliku wyjściowego (domyślne: Nazwa podstawowa pliku z klasą główną lub pierwszym plikiem).|  
|-równoległe [+&#124;—]|Określa, czy używać współbieżnych kompilacji (+).|  
|[-pdb](pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku PDB.|  
|[-platform](platform-compiler-option.md)|Limity platformy, których można uruchamiać ten kod na: x86, Itanium, x 64, wartość anycpu, lub anycpu32bitpreferred. Wartość domyślna to anycpu.|  
|[-preferreduilang](preferreduilang-compiler-option.md)|Określa język do użycia dla danych wyjściowych kompilatora.|  
|[-recurse](recurse-compiler-option.md)|Zawiera wszystkie pliki w bieżącym katalogu i jego podkatalogach zgodnie ze specyfikacją symboli wieloznacznych.|  
|[-reference](reference-compiler-option.md)|Odwołania do metadanych z określonych plików zestawów.|  
|[-refout](refout-compiler-option.md)|Wygeneruj zestaw odwołania, oprócz podstawowego zestawu.|  
|[-refonly](refonly-compiler-option.md)|Wygeneruj zestaw odwołania, a nie podstawowy zestaw.|  
|[-resource](resource-compiler-option.md)|Osadza określonego zasobu.|  
|zestaw reguł-:\<pliku >|Określ plik zestaw reguł, który powoduje wyłączenie diagnostyczne zależne.|  
|[-subsystemversion](subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, który można użyć pliku wykonywalnego.|  
|[-target](target-compiler-option.md)|Określa format pliku wyjściowego przy użyciu jednej z czterech opcji: [-docelowych: appcontainerexe](target-appcontainerexe-compiler-option.md), [— docelowych: exe](target-exe-compiler-option.md), [— docelowa: Biblioteka](target-library-compiler-option.md), [-docelowych: Moduł](target-module-compiler-option.md), [-docelowych: winexe](target-winexe-compiler-option.md), [-docelowych: winmdobj](target-winmdobj-compiler-option.md).|  
|[-unsafe](unsafe-compiler-option.md)|Umożliwia [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kodu.|  
|[-utf8output](utf8output-compiler-option.md)|Dane wyjściowe komunikaty kompilatora przy użyciu kodowania UTF-8.|  
|[-warn](warn-compiler-option.md)|Ustawia poziom ostrzeżeń (0-4).|  
|[-warnaserror](warnaserror-compiler-option.md)|Raporty określone ostrzeżenia jako błędy.|  
|[-win32icon](win32icon-compiler-option.md)|Używa tej ikony dla danych wyjściowych.|  
|[-win32manifest](win32manifest-compiler-option.md)|Określa plik manifestu win32 niestandardowych.|  
|[-win32res](win32res-compiler-option.md)|Określa plik zasobów win32 (.res).|  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](index.md)  
 [Opcje kompilatora C# w rozbiciu na kategorie](listed-by-category.md)  
 [Instrukcje: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [\<Kompilator > — Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
