---
title: Kompilacji wiersza polecenia z csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 3cd49a17991f3d7606b0364a83be2b2e30ba0cce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-build-with-cscexe"></a>Kompilacji wiersza polecenia z csc.exe
Można wywołać kompilatora C#, wpisując nazwę jego pliku wykonywalnego (*csc.exe*) w wierszu polecenia.

Jeśli używasz **wiersz polecenia dla programu Visual Studio deweloperów** okna, wszystkie zmienne środowiskowe niezbędne są ustawione dla Ciebie. Aby uzyskać informacje na temat tego narzędzia, zobacz [wiersz polecenia dla programu Visual Studio deweloperów](../../../framework/tools/developer-command-prompt-for-vs.md) tematu. 

Jeśli używasz standardowego okno wiersza polecenia, należy dostosować ścieżki można było *csc.exe* z wszelkie podkatalogi na tym komputerze. Należy także uruchomić *vsvars32.bat* można ustawić zmienne środowiskowe odpowiednie do obsługi kompilacji z wiersza polecenia. Aby uzyskać więcej informacji na temat *vsvars32.bat*, w tym instrukcje dotyczące sposobu Znajdź i uruchom go, zobacz [porady: Ustawianie zmiennych środowiskowych dla programu Visual Studio wierszu polecenia](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Jeśli pracujesz na komputerze, który ma tylko [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], można użyć do kompilatora C# w **SDK Command Prompt**, które można otworzyć z **zestawu Microsoft .NET Framework SDK** opcji menu.

Umożliwia także MSBuild do programowego tworzenia programów C#. Aby uzyskać więcej informacji, zobacz [MSBuild](/visualstudio/msbuild/msbuild).

*Csc.exe* pliku wykonywalnego zazwyczaj znajduje się w Microsoft.NET\Framework\\*\<wersji >* folder *Windows* katalog. Lokalizacji mogą się różnić w zależności od dokładnej konfiguracji określonego komputera. Jeśli więcej niż jedna wersja programu .NET Framework jest zainstalowana na komputerze, można znaleźć wiele wersji tego pliku. Aby uzyskać więcej informacji na temat takich instalacji, zobacz [porady: Określanie, które wersje programu .NET Framework są zainstalowane](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
>  Podczas tworzenia projektu za pomocą środowiska IDE programu Visual Studio, możesz wyświetlić **csc** polecenia i jego opcji kompilatora skojarzony w **dane wyjściowe** okna. Aby wyświetlić te informacje, postępuj zgodnie z instrukcjami w [porady: widoku, zapisywanie i konfigurowanie plików dziennika kompilacji](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) Aby zmienić poziom szczegółowości danych dziennika **normalny** lub **szczegółowy**. Po odbudowaniu projektu wyszukiwania **dane wyjściowe** w oknie **csc** można znaleźć wywołanie kompilatora C#.

 **W tym temacie**

- [Zasady składni wiersza polecenia](#-rules-for-command-line-syntax-for-the-c-compiler)

- [Przykładów — wiersze poleceń](#sample-command-lines-for-the-c-compiler)

- [Różnice między kompilatora C# i dane wyjściowe kompilatora C++](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Zasady składni wiersza polecenia dla kompilatora C#

Gdy będą interpretowane przez argumenty podane w wierszu polecenia systemu operacyjnego kompilatora C# stosowane są następujące reguły:

- Argumenty są rozdzielone biały znak, który jest spację lub tabulator.

- Znak daszek (^) nie został rozpoznany jako znak ucieczki lub ogranicznika. Znak jest obsługiwany przez analizator składni wiersza polecenia w systemie operacyjnym, zanim zostanie przekazany do `argv` tablicy w programie.

- Ciąg ujęty w podwójnym cudzysłowie ("string") jest interpretowana jako jeden argument, niezależnie od biały znak, który jest zawarty w. Ciąg w cudzysłowie, można ją osadzić w argumencie.

- Podwójny cudzysłów poprzedzony ukośnikiem (\\") jest interpretowany jako znak literału podwójnego cudzysłowu (").

- Używanie ukośników odwrotnych będą interpretowane jako literału, chyba że bezpośrednio poprzedzać podwójny cudzysłów.

- Jeśli parzystą liczbą ukośników odwrotnych następuje podwójny cudzysłów, jeden ukośnik odwrotny jest umieszczany `argv` tablicy dla każdej pary ukośników odwrotnych i podwójny cudzysłów jest interpretowana jako ogranicznik ciągu.

- Jeśli nieparzystą liczbę ukośników odwrotnych następuje podwójny cudzysłów, jeden ukośnik odwrotny jest umieszczany `argv` tablicy dla każdej pary ukośników odwrotnych i podwójny cudzysłów jest "wpisywany" z pozostałych ukośnika odwrotnego. Powoduje to literału podwójny cudzysłów (") do dodania w `argv`.

## <a name="sample-command-lines-for-the-c-compiler"></a>Przykładowe wiersze poleceń dla kompilatora C#

- Kompiluje *File.cs* produkujących *File.exe*:

```console
csc File.cs 
```

- Kompiluje *File.cs* produkujących *File.dll*:

```console
csc -target:library File.cs
```

- Kompiluje *File.cs* i tworzy *My.exe*:

```console
csc -out:My.exe File.cs
```

- Kompiluje z włączonymi optymalizacjami wszystkie pliki C# w bieżącym katalogu i określa symboli debugowania. Dane wyjściowe *File2.exe*:

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- Kompiluje wszystkie pliki C# w bieżącym katalogu produkujących wersję debugowania *File2.dll*. Brak logo i ostrzeżenia nie są wyświetlane:

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- Kompiluje wszystkie pliki C# w bieżącym katalogu do *Something.xyz* (DLL):

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Różnice między kompilatora C# i dane wyjściowe kompilatora C++
Brak Brak obiektu (*.obj*) pliki tworzone w wyniku wywołania kompilatora C#; pliki wyjściowe są tworzone bezpośrednio. W wyniku tego kompilatora C# nie musi konsolidator.

## <a name="see-also"></a>Zobacz także
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Opcje kompilatora C# w porządku alfabetycznym](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [Opcje kompilatora C# w rozbiciu na kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
 [Porady: wyświetlanie argumentów wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Instrukcje: uzyskiwanie dostępu do argumentów wiersza polecenia za pomocą instrukcji foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
