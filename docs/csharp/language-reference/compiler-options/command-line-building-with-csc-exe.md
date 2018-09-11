---
title: Kompilacji wiersza polecenia przy użyciu csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 4b6dfdbce131371553fc729206de29794266bfbe
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365596"
---
# <a name="command-line-build-with-cscexe"></a>Kompilacji wiersza polecenia przy użyciu csc.exe
Można wywołać kompilatora języka C#, wpisując nazwę jego pliku wykonywalnego (*csc.exe*) w wierszu polecenia.

Jeśli używasz **wiersz polecenia programisty dla programu Visual Studio** oknie wszystkie potrzebne zmienne środowiskowe są ustawiane dla Ciebie. Aby uzyskać informacje na temat sposobu dostęp do tego narzędzia, zobacz [wiersz polecenia programisty dla programu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) tematu. 

Jeśli używasz standardowego okna wiersza polecenia, należy dostosować swoją ścieżkę przed może wywołać *csc.exe* z wszelkie podkatalogi na tym komputerze. Należy również uruchomić *vsvars32.bat* można ustawić odpowiednie zmienne środowiskowe do obsługi kompilacji z wiersza polecenia. Aby uzyskać więcej informacji na temat *vsvars32.bat*, w tym instrukcje dotyczące sposobu Znajdź i uruchom go, zobacz [porady: Ustawianie zmiennych środowiskowych dla programu Visual Studio wierszu polecenia](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Jeśli pracujesz na komputerze, który ma tylko [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], można użyć kompilatora języka C# w **SDK Command Prompt**, które można otworzyć **Microsoft .NET Framework SDK** opcji menu.

Umożliwia także programu MSBuild do kompilowania programów C#, programowo. Aby uzyskać więcej informacji, zobacz [MSBuild](/visualstudio/msbuild/msbuild).

*Csc.exe* pliku wykonywalnego zwykle znajduje się w Microsoft.NET\Framework\\*\<wersji >* folderze *Windows* katalog. Lokalizacji może się różnić w zależności od dokładnej konfiguracji określonego komputera. Jeśli więcej niż jedna wersja programu .NET Framework jest zainstalowany na komputerze, znajdziesz wiele wersji tego pliku. Aby uzyskać więcej informacji na temat tych instalacji, zobacz [porady: Określanie, które wersje programu .NET Framework są zainstalowane](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).

> [!TIP]
>  Gdy tworzysz projekt za pomocą środowiska IDE programu Visual Studio możesz wyświetlać **csc** polecenia i jego opcji kompilatora skojarzone w **dane wyjściowe** okna. Aby wyświetlić te informacje, postępuj zgodnie z instrukcjami [jak: widoku, zapisywanie i konfigurowanie plików dziennika kompilacji](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) Aby zmienić poziom szczegółowości danych dziennika, aby **normalny** lub **szczegółowe**. Wyszukiwanie po ponownym skompilowaniu projektu **dane wyjściowe** okno **csc** można znaleźć wywołania kompilator języka C#.

 **W tym temacie**

- [Zasady składni wiersza polecenia](#-rules-for-command-line-syntax-for-the-c-compiler)

- [Przykładowe wiersze poleceń](#sample-command-lines-for-the-c-compiler)

- [Różnice między kompilatorem C# i danymi wyjściowymi kompilatora C++](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Zasady składni wiersza polecenia dla kompilatora C#

Kompilator języka C# używa następujących reguł, gdy interpretuje argumenty podane w wierszu polecenia systemu operacyjnego:

- Argumenty są rozdzielone biały znak, który jest spacja lub tabulator.

- Znak daszka (^) nie została rozpoznana jako znak ucieczki lub ogranicznik. Znak jest obsługiwany przez analizator składni wiersza polecenia w systemie operacyjnym, zanim zostanie przekazany do `argv` tablicy w programie.

- Ciąg ujęty w znaki podwójnego cudzysłowu ("string") jest interpretowany jako jeden argument, niezależnie od tego, biały znak znajdującą się wewnątrz. Ciąg w cudzysłowach można osadzać w argumencie.

- Podwójny cudzysłów poprzedzone znakiem ukośnika odwrotnego (\\") jest interpretowany jako znak literału podwójny cudzysłów (").

- Ukośników odwrotnych jest interpretowany dosłownie, chyba że bezpośrednio poprzedzać znak podwójnego cudzysłowu.

- Jeśli parzysta liczba ukośników odwrotnych następuje podwójny cudzysłów, jednej kreski ułamkowej odwróconej jest umieszczany w `argv` tablicy dla każdej pary ukośników odwrotnych i podwójnego cudzysłowu jest interpretowany jako ogranicznik ciągu.

- Jeśli nieparzysta liczba ukośników odwrotnych następuje podwójny cudzysłów, jednej kreski ułamkowej odwróconej jest umieszczany w `argv` tablicy dla każdej pary ukośników odwrotnych i podwójnego cudzysłowu jest "poprzedzone znakiem zmiany znaczenia" przez pozostałe ukośnika odwrotnego. Powoduje to, że literał podwójny cudzysłów (") mają zostać dodane w `argv`.

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

- Kompiluje wszystkie pliki C# w bieżącym katalogu z włączonymi optymalizacjami i definiuje DEBUG symbol. Dane wyjściowe są *File2.exe*:

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- Kompiluje wszystkie pliki C# w bieżącym katalogu, tworzenie wersji debugowania *File2.dll*. Brak logo i żadne ostrzeżenia nie są wyświetlane:

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- Kompiluje wszystkie pliki C# w bieżącym katalogu do *Something.xyz* (DLL):

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Różnice między kompilatorem C# i danymi wyjściowymi kompilatora C++
Istnieją żaden obiekt (*.obj*) pliki utworzone w wyniku wywołania kompilator języka C#; pliki wyjściowe są tworzone bezpośrednio. W efekcie kompilator języka C# nie jest konieczne konsolidatora.

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Opcje kompilatora C# w porządku alfabetycznym](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
- [Opcje kompilatora C# w rozbiciu na kategorie](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
- [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [Argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
- [Porady: wyświetlanie argumentów wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [Instrukcje: uzyskiwanie dostępu do argumentów wiersza polecenia za pomocą instrukcji foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
