---
title: "Witaj Świecie — pierwszy program (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17dcce921f3a6ff1a9c547c5ff5d34c3dbbf28d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Witaj Świecie — pierwszy program (Przewodnik programowania w języku C#)
Poniższa procedura tworzy wersję języka C# tradycyjnych "Witaj świecie!" Program. Program wyświetla ciąg`Hello World!`  
  
 Więcej przykładów dotyczących pojęcia wprowadzające, zobacz [wprowadzenie do języka Visual C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a>Aby utworzyć i uruchomić aplikację konsoli  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  Rozwiń węzeł **zainstalowana**, rozwiń węzeł **szablony**, rozwiń węzeł **Visual C#**, a następnie wybierz pozycję **aplikacji konsoli**.  
  
4.  W **nazwa** polu, określ nazwę projektu, a następnie wybierz **OK** przycisku.  
  
     Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
5.  Jeśli Program.cs nie jest otwarty w **edytora kodu**, otwórz menu skrótów dla **Program.cs** w **Eksploratora rozwiązań**, a następnie wybierz pozycję **kod widoku**.  
  
6.  Zastąp zawartość pliku Program.cs następującym kodem.  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  Wybierz klawisz F5, aby uruchomić projekt. Zostanie wyświetlone okno wiersza polecenia zawierający wiersza`Hello World!`  
  
 Następnie badane są ważne części tego programu.  
  
## <a name="comments"></a>Komentarze  
 Pierwszy wiersz zawiera komentarz. Znaki `//` Konwertuj pozostałą część wiersza na komentarz.  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 W bloku tekstu można również komentarz, umieszczając ją między `/*` i `*/` znaków. Przedstawiono to w poniższym przykładzie.  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a>Metoda główna  
 Musi zawierać aplikacji konsolowej C# `Main` metody, w której formant rozpoczyna się i kończy się. `Main` Metoda jest gdzie tworzenia obiektów i wykonywania innych metod.  
  
 `Main` Jest metoda [statycznych](../../../csharp/language-reference/keywords/static.md) metodę, która znajduje się wewnątrz klasy lub struktury. W poprzednich "Witaj świecie!" przykład znajduje się w klasie o nazwie `Hello`. Można zadeklarować `Main` metody w jednym z następujących sposobów:  
  
-   Może on zwrócić `void`.  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   Można także wrócić liczbą całkowitą.  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   Przy użyciu jednej z zwracane typy może upłynąć argumentów.  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     —lub—  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 Parametr `Main` metody `args`, jest `string` tablica, która zawiera argumenty wiersza polecenia używane do wywołania programu. W przeciwieństwie do języka C++, tablica nie zawiera nazwę pliku wykonywalnego (exe).  
  
 Aby uzyskać więcej informacji o sposobie używania argumentów wiersza polecenia, zobacz przykłady w [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md) i [porady: tworzenie i użyj zestawów przy użyciu wiersza polecenia](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
 Wywołanie <xref:System.Console.ReadKey%2A> na końcu `Main` metody uniemożliwia okna konsoli zamykania, aby mieć możliwość odczytu dane wyjściowe po uruchomieniu programu w trybie debugowania, naciskając klawisz F5.  
  
## <a name="input-and-output"></a>Dane wejściowe i wyjściowe  
 C# programy zazwyczaj używają wejścia/wyjścia usług świadczonych przez biblioteki wykonawczej programu .NET Framework. Instrukcja `System.Console.WriteLine("Hello World!");` używa <xref:System.Console.WriteLine%2A> metody. Jest to jedna z danych wyjściowych metody <xref:System.Console> klasy biblioteki czasu wykonywania. Wyświetla jego parametr ciągu na Standardowy strumień wyjściowy znak nowego wiersza. Inne <xref:System.Console> różnych danych wejściowych i wyjściowych operacji dostępnych metod. Jeśli dołączysz `using System;` dyrektywy na początku programu, możesz bezpośrednio użyć <xref:System> klasy i metody bez pełni zakwalifikowanie ich. Na przykład można wywołać `Console.WriteLine` zamiast `System.Console.WriteLine`:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 Aby uzyskać więcej informacji na temat metod wejścia/wyjścia, zobacz <xref:System.IO>.  
  
## <a name="command-line-compilation-and-execution"></a>Wiersz polecenia kompilacji i wykonania  
 Można kompilować "Witaj świecie!" program przy użyciu wiersza polecenia zamiast programu Visual Studio programowanie środowiska IDE (Integrated).  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a>Aby skompilować i uruchomić z wiersza polecenia  
  
1.  Wklej kod z powyższej procedury w edytorze tekstu, a następnie zapisz plik jako plik tekstowy. Nadaj nazwę plikowi `Hello.cs`. Pliki kodu źródłowego C# za pomocą rozszerzenia `.cs`.  
  
2.  Wykonaj jedną z następujących czynności, aby otworzyć okno wiersza polecenia:  
  
    -   W systemie Windows 10 na **Start** menu, wyszukaj `Developer Command Prompt`, a następnie naciśnij lub wybierz **wiersz polecenia dla programu VS 2017 deweloperów**.  
  
         Zostanie wyświetlone okno Wiersz polecenia dla deweloperów.  
  
    -   W systemie Windows 7, należy otworzyć **Start** menu, rozwiń folder z bieżącą wersją programu Visual Studio, otwórz menu skrótów **Visual Studio Tools**, a następnie wybierz pozycję **wiersz polecenia dla deweloperów dla wersji programu VS 2017**.  
  
         Zostanie wyświetlone okno Wiersz polecenia dla deweloperów.  
  
    -   Włącz kompilacji z wiersza polecenia z standardowe okno wiersza polecenia.  
  
         Zobacz [porady: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
3.  W oknie wiersza polecenia przejdź do folderu, który zawiera Twoje `Hello.cs` pliku.  
  
4.  Wprowadź następujące polecenie, aby skompilować `Hello.cs`.  
  
     `csc Hello.cs`  
  
     Jeśli program nie ma błędów kompilacji, plik wykonywalny o nazwie `Hello.exe` jest tworzony.  
  
5.  W oknie wiersza polecenia wprowadź następujące polecenie, aby uruchomić program:  
  
     `Hello`  
  
 Aby uzyskać więcej informacji na temat kompilatora C# i jego opcji, zobacz [opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md).
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [W programie C#](../../../csharp/programming-guide/inside-a-program/index.md)  
 [Ciągi](../../../csharp/programming-guide/strings/index.md)  
 [\<paveover > C# przykładowe aplikacje](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Wprowadzenie do języka Visual C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
