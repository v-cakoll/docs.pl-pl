---
title: Kompilacja wiersza polecenia z csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789868"
---
# <a name="command-line-build-with-cscexe"></a>Kompilacja wiersza polecenia z csc.exe

Kompilator C# można wywołać, wpisując nazwę jego pliku wykonywalnego *(csc.exe)* w wierszu polecenia.

Jeśli używasz **wiersza polecenia dewelopera dla** programu Visual Studio, wszystkie niezbędne zmienne środowiskowe są ustawione dla Ciebie. Aby uzyskać informacje na temat uzyskiwania dostępu do tego narzędzia, zobacz [temat Wiersz polecenia dewelopera dla programu Visual Studio.](../../../framework/tools/developer-command-prompt-for-vs.md)

Jeśli używasz standardowego okna wiersza polecenia, należy dostosować ścieżkę, zanim będzie można wywołać *csc.exe* z dowolnego podkatalogu na komputerze. Należy również uruchomić *vsvars32.bat,* aby ustawić odpowiednie zmienne środowiskowe do obsługi kompilacji wiersza polecenia. Aby uzyskać więcej informacji na temat *vsvars32.bat*, w tym instrukcje dotyczące znajdowania i uruchamiania, zobacz [Jak ustawić zmienne środowiskowe dla wiersza polecenia programu Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).

Jeśli pracujesz na komputerze, który ma tylko zestaw Windows Software Development Kit (SDK), możesz użyć kompilatora C# w **wierszu polecenia zestawu SDK**, który można otworzyć z menu **zestawu Microsoft .NET Framework SDK.**

Można również użyć MSBuild do tworzenia programów C# programowo. Aby uzyskać więcej informacji, zobacz [MSBuild](/visualstudio/msbuild/msbuild).

Plik wykonywalny *programu csc.exe* zwykle znajduje\\się w*\<folderze microsoft.NET\Framework version>* w katalogu systemu *Windows.* Jego lokalizacja może się różnić w zależności od dokładnej konfiguracji określonego komputera. Jeśli na komputerze jest zainstalowana więcej niż jedna wersja programu .NET Framework, znajdziesz wiele wersji tego pliku. Aby uzyskać więcej informacji na temat takich instalacji, zobacz [Jak: określić, które wersje programu .NET Framework są zainstalowane.](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)

> [!TIP]
> Podczas tworzenia projektu przy użyciu programu Visual Studio IDE, można wyświetlić polecenie **csc** i skojarzone z nim opcje kompilatora w oknie **Wyjście.** Aby wyświetlić te informacje, postępuj zgodnie z instrukcjami w [jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji,](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) aby zmienić poziom szczegółowości danych dziennika na **Normalny** lub **Szczegółowy**. Po odbudowie projektu, wyszukaj w oknie **Wyjście** dla **csc,** aby znaleźć wywołanie kompilatora C#.

 **W tym temacie**

- [Reguły składni wiersza polecenia](#rules-for-command-line-syntax-for-the-c-compiler)

- [Przykładowe wiersze polecenia](#sample-command-lines-for-the-c-compiler)

- [Różnice między kompilatorem C# a wyjściem kompilatora C++](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>Reguły składni wiersza polecenia kompilatora C#

Kompilator Języka C# używa następujących reguł, gdy interpretuje argumenty podane w wierszu polecenia systemu operacyjnego:

- Argumenty są rozdzielane przez biały znak, który jest spacjaiem lub tabulatorem.

- Znak karetki (^) nie jest rozpoznawany jako znak ucieczki lub ogranicznik. Znak jest obsługiwany przez analizator wiersza polecenia w systemie operacyjnym, `argv` zanim zostanie przekazany do tablicy w programie.

- Ciąg ujęty w podwójne cudzysłowy ("ciąg") jest interpretowany jako pojedynczy argument, niezależnie od odstępu, który jest zawarty w środku. Cytowany ciąg może być osadzony w argumencie.

- Podwójny cudzysłów poprzedzony ukośnikiem odwrotnym (\\") jest interpretowany jako znak znaku znaku cudzysłowu dwurzędowego (dw.).

- Ukośniki wsteczne są interpretowane dosłownie, chyba że bezpośrednio poprzedzają podwójny cudzysłów.

- Jeśli po parzystej liczbie ukośników wstecznych następuje `argv` podwójny cudzysłów, jeden ukośnik odwrotny jest umieszczany w tablicy dla każdej pary ukośników odwrotnych, a podwójny cudzysłów jest interpretowany jako ogranicznik ciągu.

- Jeśli po nieparzystej liczbie ukośni ków występuje podwójny `argv` cudzysłów, jeden ukośnik odwrotny jest umieszczany w tablicy dla każdej pary ukośników odwrotnych, a podwójny cudzysłów jest "unikany" przez pozostały ukośnik odwrotny. Powoduje to dosłowny podwójny cudzysłów `argv`(") dododania w pliku .

## <a name="sample-command-lines-for-the-c-compiler"></a>Przykładowe wiersze polecenia dla kompilatora C#

- Kompiluje *File.cs* produkując *file.exe:*

  ```console
  csc File.cs
  ```

- Kompiluje *File.cs* produkując *plik File.dll:*

  ```console
  csc -target:library File.cs
  ```

- Kompiluje *File.cs* i tworzy *My.exe*:

  ```console
  csc -out:My.exe File.cs
  ```

- Kompiluje wszystkie pliki C# w bieżącym katalogu z włączonymi optymalizacjami i definiuje symbol DEBUG. Wyjście m. *File2.exe*:

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- Kompiluje wszystkie pliki C# w bieżącym katalogu, tworząc wersję debugowania *pliku File2.dll*. Nie ma logo i nie są wyświetlane ostrzeżenia:

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- Kompiluje wszystkie pliki C# w bieżącym katalogu do *Something.xyz* (DLL):

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>Różnice między kompilatorem C# a wyjściem kompilatora C++

Nie ma żadnych plików obiektu (*obj*) utworzonych w wyniku wywołania kompilatora C#; pliki wyjściowe są tworzone bezpośrednio. W wyniku tego kompilator Języka C# nie wymaga konsolidatora.

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Opcje kompilatora C# w porządku alfabetycznym](./listed-alphabetically.md)
- [Opcje kompilatora C# w rozbiciu na kategorie](./listed-by-category.md)
- [Main() i argumenty wiersza polecenia](../../programming-guide/main-and-command-args/index.md)
- [Argumenty wiersza polecenia](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [Wyświetlanie argumentów wiersza polecenia](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Main() — zwracane wartości](../../programming-guide/main-and-command-args/main-return-values.md)
