---
title: Opcje kompilatora C# w rozbiciu na kategorie
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95c5c3d1c7ea2461e9bda9a1d58464e97ccc688
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="c-compiler-options-listed-by-category"></a>Opcje kompilatora C# w rozbiciu na kategorie
Następujące opcje kompilatora są sortowane według kategorii. Aby uzyskać alfabetyczną listę, zobacz [C# kompilatora opcje wymienione alfabetycznie](../../../csharp/language-reference/compiler-options/listed-alphabetically.md).  
  
### <a name="optimization"></a>Optymalizacja  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|Określa rozmiar sekcji w pliku wyjściowym.|  
|[/ optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|Włącza/wyłącza optymalizacje.|  
  
### <a name="output-files"></a>Pliki wyjściowe  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|Określa plik XML, których komentarzy do dokumentacji przetworzonych do zapisania.|  
|[/ out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|Określa plik wyjściowy.|  
|[/ PDB](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|Określa nazwę pliku i lokalizację pliku PDB.|  
|[/ platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|Określ platformę danych wyjściowych.|  
|[/ preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|Określanie języka danych wyjściowych kompilatora.|  
|[/refout](refout-compiler-option.md)|Wygeneruj zestaw odwołania, oprócz podstawowego zestawu.|  
|[/refonly](refonly-compiler-option.md)|Wygeneruj zestaw odwołania, a nie podstawowy zestaw.|  
|[/ TARGET](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|Określa format pliku wyjściowego przy użyciu jednej z pięciu opcji: [/target: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md), [/target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md), [/target: Library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md),  [ /target: module ](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md), lub [/target: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md).|  
|/modulename:\<ciąg >|Określ nazwę modułu źródła|  
  
### <a name="net-framework-assemblies"></a>Zestawów platformy .NET framework  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|Określa co najmniej jednego modułu należeć do tego zestawu.|  
|[/ DelaySign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|Instruuje kompilator, aby dodać klucz publiczny, ale pozostawić zestawu bez znaku.|  
|[/ KeyContainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|Określa nazwę kontenera kluczy kryptograficznych.|  
|[/ KeyFile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|Określa nazwę pliku zawierającego klucz kryptograficzny.|  
|[/ lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|Określa lokalizację zestawy, do których odwołuje się za pomocą klasy [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).|  
|[/ nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|Instruuje kompilator, aby nie Importuj biblioteki standardowej (mscorlib.dll).|  
|[/ Reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|Importuje metadane z pliku, który zawiera zestaw.|  
|/Analyzer|Uruchom analizatorów z tego zestawu (krótka wersja: /)|  
|/additionalfile|Nazwy dodatkowych plików bezpośrednio nie wpływają na generowanie kodu, które mogą być używane przez analizatory do produkcji błędy lub ostrzeżenia.|  
  
### <a name="debuggingerror-checking"></a>Sprawdzanie Debugowanie błędów  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|Tworzy plik zawierający informacje, które ułatwia zgłosić usterkę.|  
|[/ checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|Określa, czy liczba całkowita arytmetyczne, który przepełnienie granic o typie danych spowoduje, że wystąpił wyjątek w czasie wykonywania.|  
|[/ Debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|Poinstruuj kompilator Emituj informacje debugowania.|  
|[/ errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|Ustawia zachowanie raportowania błędów.|  
|[/ fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|Określa bezwzględną ścieżkę do pliku w danych wyjściowych kompilatora.|  
|[/ nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|Pomija generację określonych ostrzeżeń kompilatora.|  
|[/ warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|Ustawia poziom ostrzeżeń.|  
|[/ warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|Zamienia ostrzeżenia błędy.|  
|/ RuleSet:\<pliku >|Określ plik zestaw reguł, który powoduje wyłączenie diagnostyczne zależne.|  
  
### <a name="preprocessor"></a>Preprocesor  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|Definiuje symbole preprocesora.|  
  
### <a name="resources"></a>Resources  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ Link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|Udostępnia informacje o typie modelu COM w określonych zestawów do projektu.|  
|[/ linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|Tworzy łącze do zasobów zarządzanych.|  
|[/ Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|Osadza zasobu .NET Framework do pliku wyjściowego.|  
|[/ win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|Określa plik .ico, aby wstawić do pliku wyjściowego.|  
|[/ win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|Określa zasób Win32 do wstawienia do pliku wyjściowego.|  
  
### <a name="miscellaneous"></a>Inne  
  
|Opcja|Cel|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|Określa plik odpowiedzi.|  
|[/?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Wyświetla listę opcji kompilatora stdout.|  
|[/ BaseAddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL.|  
|[/ CodePage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|Określa stronę kodową do używania wszystkich plików kodu źródłowego w kompilacji.|  
|[/ Help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|Wyświetla listę opcji kompilatora stdout.|  
|[/ highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|Określa, że plik wykonywalny obsługuje randomizacji układu przestrzeni adresowej (ASLR).|  
|[/ langversion](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|Określ tryb wersji języka: domyślny, ISO-1, ISO-2, 3, 4, 5, 6, 7, 7.1 lub najnowsze |  
|[/ main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|Określa lokalizację **Main** metody.|  
|[/ noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|Instruuje kompilator, aby nie kompilacji z csc.rsp.|  
|[/ nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|Pomija informacje transparentu kompilatora.|  
|[/ recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|Podkatalogi wyszukiwania dla plików źródłowych do skompilowania.|  
|[/ subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|Określa minimalną wersję podsystemu, który można użyć pliku wykonywalnego.|  
|[/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|Włącza kompilację kodu korzystającego z [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe.|  
|[/ utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|Wyświetla kompilatora, dane wyjściowe przy użyciu kodowania UTF-8.|  
|/ równoległe [+ &#124;-]|Określa, czy używać współbieżnych kompilacji (+).|  
|/checksumalgorithm:\<alg >|Określ algorytm oblicza sumę kontrolną pliku źródłowego, przechowywane w pliku PDB.  Obsługiwane są następujące wartości: SHA1 (ustawienie domyślne) lub SHA256.|  
  
## <a name="obsolete-options"></a>Opcje przestarzałe  
  
|Opcja|Cel|  
|---|---|  
|/ incremental|Włącza kompilację przyrostową.|  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Opcje kompilatora C# alfabetycznym](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Porady: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
