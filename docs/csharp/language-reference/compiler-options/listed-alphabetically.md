---
title: "Opcje kompilatora C# w porządku alfabetycznym"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- compiler options [C#], listed alpabetically
- C# language, compiler options listed alphabitically
- Visual C# compiler, options listed alphabetically
- Visual C#, compiler options listed alphabetically
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f4d7f1b122d3481dc8c3c5256ee361965846a830
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2018
---
# <a name="c-compiler-options-listed-alphabetically"></a>Opcje kompilatora C# w porządku alfabetycznym
Następujące opcje kompilatora są sortowane w kolejności alfabetycznej. Lista kategorii, [C# kompilatora opcje rozbiciu na kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md).  
  
|Opcja|Cel|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|Odczytuje plik odpowiedzi, aby wyświetlić więcej opcji.|  
|[-?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Wyświetla komunikat o sposobie użycia stdout.|  
|-additionalfile|Nazwy dodatkowych plików bezpośrednio nie wpływają na generowanie kodu, które mogą być używane przez analizatory do produkcji błędy lub ostrzeżenia.|  
|[-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|Łączy określone moduły z tym zestawem|  
|-analyzer|Uruchom analizatorów z tego zestawu (krótka wersja: -)|  
|[-appconfig](../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)|Określa lokalizację pliku app.config w czasie powiązanie zestawu.|  
|[-baseaddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|Określa adres podstawowy biblioteki, który ma zostać utworzony.|  
|[-bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|Tworzy plik "Usterek — raport". Ten plik zostanie wysłana wraz z informacjami awarii, jeśli jest używana z - errorreport: wiersz lub - errorreport: wysyłania.|  
|[-checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|Umożliwia kompilatorowi Generowanie sprawdzanie nadmiaru dla operacji.|  
|-checksumalgorithm:\<alg >|Określ algorytm oblicza sumę kontrolną pliku źródłowego, przechowywane w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (ustawienie domyślne) lub SHA256.|  
|[-codepage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|Określa stronę kodową do używania podczas otwierania plików źródłowych.|  
|[-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|Emituje informacje o debugowaniu.|  
|[-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|Definiuje symbole kompilacji warunkowej.|  
|[-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|Opóźnienie znaki zestawu za pomocą tylko publicznej części klucza silnej nazwy.|  
|[-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|Określa plik dokumentacji XML do wygenerowania.|  
|[-errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|Określa sposób obsługiwać wewnętrzne błędy kompilatora: wiersza, Wyślij lub none. Domyślna wartość to Brak.|  
|[-filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|Określa wyrównanie używane w sekcjach pliku wyjściowego.|  
|[-fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|Umożliwia kompilatorowi Generowanie pełni kwalifikowane ścieżki.|  
|[-help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Wyświetla komunikat o sposobie użycia stdout.|  
|[-highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|Określa, że wysokiej entropii ASLR jest obsługiwana.|  
|-przyrostowe|Włącza kompilację przyrostową [przestarzały].|  
|[-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|Określa kontener klucza o silnej nazwie.|  
|[-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|Określa plik klucza o silnej nazwie.|  
|[-langversion:\<ciąg >](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|Określ tryb wersji języka: domyślny, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1 lub najnowsze |  
|[-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|Określa dodatkowe katalogi, w których będą poszukiwane odwołań.|  
|[-link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|Udostępnia informacje o typie modelu COM w określonych zestawów do projektu.|  
|[-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|Dołącza określony zasób z tym zestawem.|  
|[-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|Określa typ zawierający punkt wejścia (Ignoruj wszystkie pozostałe możliwe punkty wejścia).|  
|[-moduleassemblyname](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)|Określa, których typy niepublicznych modułu .netmodule mogą uzyskiwać dostęp do zestawu.|  
|-modulename:\<ciąg >|Określ nazwę modułu źródła|  
|[-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|Instruuje kompilator, nie można automatycznie dołączyć CSC. Źródło pliku.|  
|[-nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|Pomija komunikat o prawach autorskich kompilatora.|  
|[-nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|Instruuje kompilator, aby nie odwołanie do biblioteki standardowej (mscorlib.dll).|  
|[-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|Wyłącza określone komunikaty ostrzegawcze|  
|[-nowin32manifest](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)|Instruuje kompilator, aby nie Osadź manifest aplikacji w pliku wykonywalnego.|  
|[-optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|  
|[-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|Określa nazwę pliku wyjściowego (domyślne: Nazwa podstawowa pliku z klasą główną lub pierwszym plikiem).|  
|-równoległe [+ &#124;-]|Określa, czy używać współbieżnych kompilacji (+).|  
|[-pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku PDB.|  
|[-platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|Limity platformy, których można uruchamiać ten kod na: x86, Itanium, x 64, wartość anycpu, lub anycpu32bitpreferred. Wartość domyślna to anycpu.|  
|[-preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Określa język do użycia dla danych wyjściowych kompilatora.|  
|[-recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|Zawiera wszystkie pliki w bieżącym katalogu i jego podkatalogach zgodnie ze specyfikacją symboli wieloznacznych.|  
|[-reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|Odwołania do metadanych z określonych plików zestawów.|  
|[-refout](refout-compiler-option.md)|Wygeneruj zestaw odwołania, oprócz podstawowego zestawu.|  
|[-refonly](refonly-compiler-option.md)|Wygeneruj zestaw odwołania, a nie podstawowy zestaw.|  
|[-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|Osadza określonego zasobu.|  
|zestaw reguł-:\<pliku >|Określ plik zestaw reguł, który powoduje wyłączenie diagnostyczne zależne.|  
|[-subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, który można użyć pliku wykonywalnego.|  
|[-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|Określa format pliku wyjściowego przy użyciu jednej z czterech opcji: [-docelowych: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md), [— docelowych: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md), [— docelowa: Biblioteka](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md), [-docelowych: Moduł](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), [-docelowych: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), [-docelowych: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md).|  
|[-unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|Umożliwia [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kodu.|  
|[-utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|Dane wyjściowe komunikaty kompilatora przy użyciu kodowania UTF-8.|  
|[-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|Ustawia poziom ostrzeżeń (0-4).|  
|[-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|Raporty określone ostrzeżenia jako błędy.|  
|[-win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|Używa tej ikony dla danych wyjściowych.|  
|[-win32manifest](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)|Określa plik manifestu win32 niestandardowych.|  
|[-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|Określa plik zasobów win32 (.res).|  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Opcje kompilatora C# w rozbiciu na kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [Instrukcje: ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [\<Kompilator > — Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)
