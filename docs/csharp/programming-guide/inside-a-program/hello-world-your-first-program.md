---
title: Witaj Świecie — pierwszy program (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 90f0ec6b88a2822cb3429948681c76c70f3d3f18
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710930"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Witaj Świecie — pierwszy program (Przewodnik programowania w języku C#)
Poniższa procedura tworzy wersję języka C# tradycyjny "Hello World!" program. Ten program wyświetla ciąg `Hello World!`  
  
 Aby uzyskać więcej przykładów wprowadzających pojęć, zobacz [wprowadzenie do języka Visual C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a>Aby utworzyć i uruchomić aplikację konsoli  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  Rozwiń **zainstalowane**, rozwiń węzeł **szablony**, rozwiń węzeł **Visual C#**, a następnie wybierz **aplikacji konsoli**.  
  
4.  W **nazwa** , określ nazwę dla projektu, a następnie wybierz **OK** przycisku.  
  
     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.  
  
5.  Jeśli plik Program.cs nie został otwarty w **Edytor kodu**, otwórz menu skrótów dla **Program.cs** w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.  
  
6.  Zastąp zawartości Program.cs następującym kodem.  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  Wybierz klawisz F5, aby uruchomić projekt. Zostanie wyświetlone okno wiersza polecenia zawierające następujący wiersz `Hello World!`  
  
 Następnie ważne elementy tego programu są badane.  
  
## <a name="comments"></a>Komentarze  
 Pierwszy wiersz zawiera komentarz. Znaki `//` przekonwertować pozostałą część wiersza komentarza.  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 Możesz również skomentować blok tekstu umieszczając go między `/*` i `*/` znaków. Jest to pokazane w poniższym przykładzie.  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a>Metoda główna  
 Aplikacja konsolowa C# musi zawierać `Main` metody, w której Kontrola rozpoczyna się i kończy. `Main` Metodą jest, gdy tworzysz obiekty i wykonujesz inne metody.  
  
 `Main` Metodą jest [statyczne](../../../csharp/language-reference/keywords/static.md) metodę, która znajduje się wewnątrz klasy lub struktury. W poprzednim "Hello World!" przykład znajduje się on w klasie o nazwie `Hello`. Można zadeklarować `Main` metody w jednym z następujących sposobów:  
  
-   Może zwracać `void`.  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   Może również zwracać liczbę całkowitą.  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   Jeden z typów zwracanych może przebierać argumenty.  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     —lub—  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 Wartość parametru `Main` metody `args`, jest `string` tablica zawierająca argumenty wiersza polecenia używane do wywołania programu. W przeciwieństwie do języka C++, tablica nie zawiera nazwę pliku wykonywalnego (exe).  
  
 Aby uzyskać więcej informacji o tym, jak używać argumentów wiersza polecenia, zobacz przykłady w [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md) i [jak: utworzyć i używać zestawów przy użyciu wiersza polecenia](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
 Wywołanie <xref:System.Console.ReadKey%2A> na końcu `Main` metoda uniemożliwia zamknięcie, zanim użytkownik zdąży odczytać dane wyjściowe, gdy uruchamiasz program w trybie debugowania, naciskając klawisz F5 okna konsoli.  
  
## <a name="input-and-output"></a>Dane wejściowe i wyjściowe  
 C# programy używają zwykle wejścia/wyjścia usług dostarczonych przez biblioteki wykonawczej programu .NET Framework. Wykonywanie instrukcji `System.Console.WriteLine("Hello World!");` używa <xref:System.Console.WriteLine%2A> metody. Jest to jedna z metod wyjścia metod klasy <xref:System.Console> klasy w bibliotece wykonawczej. Wyświetla własny parametr ciągu na standardowym strumieniu wyjściowym znak nowego wiersza. Inne <xref:System.Console> metody są dostępne różne dane wejściowe i dane wyjściowe operacji. Jeśli dołączysz `using System;` dyrektywę na początku programu, możesz bezpośrednio użyć <xref:System> klas i metod bez pełnej ich kwalifikacji. Na przykład, można wywołać `Console.WriteLine` zamiast `System.Console.WriteLine`:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 Aby uzyskać więcej informacji dotyczących metod wejście/wyjście, zobacz <xref:System.IO>.  
  
## <a name="command-line-compilation-and-execution"></a>Wiersz polecenia kompilacji i wykonania  
 Można też kompilować "Hello World!" program przy użyciu wiersza polecenia zamiast zintegrowanego rozwoju środowiska (IDE) Visual Studio.  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a>Aby skompilować i uruchomić z wiersza polecenia  
  
1.  Wklej kod z poprzedniej procedury do dowolnego edytora tekstów, a następnie zapisz plik jako plik tekstowy. Nadaj plikowi nazwę `Hello.cs`. Pliki kodu źródłowego języka C# za pomocą rozszerzenia `.cs`.  
  
2.  Wykonaj jedną z następujących czynności, aby otworzyć okno wiersza polecenia:  
  
    -   W systemie Windows 10 na **Start** menu, wyszukaj `Developer Command Prompt`, a następnie dotknij lub wybierz **wiersz polecenia programisty dla programu VS 2017**.  
  
         Zostanie wyświetlone okno wiersza polecenia dla deweloperów.  
  
    -   Windows 7, otwórz **Start** menu, rozwiń folder dla bieżącej wersji programu Visual Studio, otwórz menu skrótów dla **Visual Studio Tools**, a następnie wybierz **wiersz polecenia dla deweloperów dla programu VS 2017**.  
  
         Zostanie wyświetlone okno wiersza polecenia dla deweloperów.  
  
    -   Włącz kompilację wiersza polecenia od standardowego okna wiersza polecenia.  
  
         Zobacz [porady: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
3.  W oknie wiersza polecenia przejdź do folderu, który zawiera Twoje `Hello.cs` pliku.  
  
4.  Wprowadź następujące polecenie, aby skompilować `Hello.cs`.  
  
     `csc Hello.cs`  
  
     Jeśli program nie ma żadnych błędów kompilacji, plik wykonywalny, który nosi nazwę `Hello.exe` zostanie utworzony.  
  
5.  W oknie wiersza polecenia wprowadź następujące polecenie, aby uruchomić program:  
  
     `Hello`  
  
 Aby uzyskać więcej informacji dotyczących kompilatora C# i jego opcji, zobacz [opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md).
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Konstrukcja programu C#](../../../csharp/programming-guide/inside-a-program/index.md)  
- [Ciągi](../../../csharp/programming-guide/strings/index.md)  
- [\<paveover > C# — przykładowe aplikacje](https://msdn.microsoft.com/library/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [Wprowadzenie do języków Visual C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
