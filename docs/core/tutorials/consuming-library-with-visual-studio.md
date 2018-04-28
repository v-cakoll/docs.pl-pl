---
title: Korzystanie z biblioteki klas z platformą .NET Core w Visual Studio 2017 r.
description: Dowiedz się, jak wywołać elementów członkowskich w bibliotece klas z programu Visual Studio 2017 r.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: conceptual
ms.prod: dotnet-core
dev_langs:
- csharp
- vb
ms.workload:
- dotnetcore
ms.openlocfilehash: 7364f9a4dadf7c4a28dab0cff2fca80d0f3af62c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a>Korzystanie z biblioteki klas z platformą .NET Core w Visual Studio 2017 r.

Po utworzeniu biblioteki klas, wykonując kroki opisane w [tworzenia biblioteki klas C# z platformą .NET Core w Visual Studio 2017](./library-with-visual-studio.md) lub [tworzenia biblioteki klas języka Visual Basic z platformą .NET Core w Visual Studio 2017](vb-library-with-visual-studio.md), testowane w [testowanie biblioteki klas z platformą .NET Core w Visual Studio 2017](testing-library-with-visual-studio.md), i wbudowane wersji biblioteki, następnym krokiem jest udostępnić obiekty wywołujące. Można to zrobić na dwa sposoby:

* Jeśli biblioteki będą używane przez pojedyncze rozwiązanie (na przykład, jeśli jest on składnikiem w pojedynczej dużych aplikacji), można dołączyć ją jako projekt w rozwiązaniu.

* Jeśli biblioteki będą zazwyczaj dostępny, można rozpowszechniać go jako pakietu NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>W tym biblioteki jako projekt w rozwiązaniu

Tak samo, jak testy jednostkowe są dołączane do tego samego rozwiązania co biblioteki klas, mogą obejmować aplikacji w ramach tego rozwiązania. Na przykład można użyć w aplikacji konsoli, które monituje użytkownika o podanie ciągu i raporty, czy jego pierwszy znak jest wielką biblioteki klasy:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Otwórz `ClassLibraryProjects` rozwiązania utworzone w [tworzenia biblioteki klas C# z platformą .NET Core w Visual Studio 2017](./library-with-visual-studio.md) tematu. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązania i wybierz **Dodaj** > **nowy projekt** z menu kontekstowe.

1. W **Dodawanie nowego projektu** okna dialogowego, rozwiń węzeł **Visual C#** a następnie wybierz węzeł **.NET Core** węzła następuje **aplikacji konsoli (.NET Core)** szablon projektu. W **nazwa** polu tekstowym, wpisz "Pokazy" i wybierz **OK** przycisku.

   ![Dodaj okno dialogowe Nowy projekt](./media/consuming-library-with-visual-studio/addnewproject.png)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokazy** projekt i wybierz **Ustaw jako projekt startowy** w menu kontekstowym. 

   ![Menu kontekstowe pokazy](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Początkowo projektu nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.

   ![Menu kontekstowe pokazy zależności](./media/consuming-library-with-visual-studio/addreference.png)

1. W **Menedżera odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projektu biblioteki klas, a następnie wybierz **OK** przycisku.

   ![Menedżera odwołań](./media/consuming-library-with-visual-studio/referencemanager.png)

1. W oknie Kod *Program.cs* pliku, Zastąp cały kod z następującym kodem:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   W kodzie użyto [Console.WindowHeight](xref:System.Console.WindowHeight) właściwości, aby określić liczbę wierszy w oknie konsoli. Zawsze, gdy [Console.CursorTop](xref:System.Console.CursorTop) właściwości jest większa lub równa liczbie wierszy w oknie konsoli, kod Czyści okno konsoli i komunikat dla użytkownika.

   Program monituje użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg rozpoczyna się wielką literę. Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciąg, kończy aplikacji i zamyka okno konsoli.

1. W razie potrzeby zmień narzędzi, aby skompilować **debugowania** wydanie `ShowCase` projektu. Kompilowanie i uruchamianie programu wybierając zieloną strzałkę na **pokazy** przycisku.

   ![Obraz](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Otwórz `ClassLibraryProjects` rozwiązania utworzone w [Tworzenie klasy biblioteki z Visual Basic i .NET Core w Visual Studio 2017](vb-library-with-visual-studio.md) tematu. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązania i wybierz **Dodaj** > **nowy projekt** z menu kontekstowe.

1. W **Dodawanie nowego projektu** okna dialogowego, rozwiń węzeł **Visual Basic** a następnie wybierz węzeł **.NET Core** węzła następuje **aplikacji konsoli (.NET Core)** szablonu projektu. W **nazwa** polu tekstowym, wpisz "Pokazy" i wybierz **OK** przycisku.

   ![Dodaj okno dialogowe Nowy projekt](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokazy** projekt i wybierz **Ustaw jako projekt startowy** w menu kontekstowym. 

   ![Menu kontekstowe pokazy](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Początkowo projektu nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.

   ![Menu kontekstowe pokazy zależności](./media/consuming-library-with-visual-studio/addreference.png)

1. W **Menedżera odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projektu biblioteki klas, a następnie wybierz **OK** przycisku.

   ![Menedżera odwołań](./media/consuming-library-with-visual-studio/referencemanager.png)

1. W oknie Kod *Program.vb* pliku, Zastąp cały kod z następującym kodem:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   W kodzie użyto [Console.WindowHeight](xref:System.Console.WindowHeight) właściwości, aby określić liczbę wierszy w oknie konsoli. Zawsze, gdy [Console.CursorTop](xref:System.Console.CursorTop) właściwości jest większa lub równa liczbie wierszy w oknie konsoli, kod Czyści okno konsoli i komunikat dla użytkownika.

   Program monituje użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg rozpoczyna się wielką literę. Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciąg, kończy aplikacji i zamyka okno konsoli.

1. W razie potrzeby zmień narzędzi, aby skompilować **debugowania** wydanie `ShowCase` projektu. Kompilowanie i uruchamianie programu wybierając zieloną strzałkę na **pokazy** przycisku.

   ![Obraz](./media/consuming-library-with-visual-studio/toolbar.png)
---

Można debugować i opublikować aplikację, która korzysta z tej biblioteki, wykonując kroki opisane w [debugowania aplikacji Hello World z programu Visual Studio 2017](debugging-with-visual-studio.md) i [publikowania aplikacji Hello World z programem Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Dystrybucja biblioteki w pakiecie NuGet

Można udostępnić biblioteki klasy powszechnie publikując go jako pakietu NuGet. Program Visual Studio nie obsługuje tworzenia pakietów NuGet. Aby utworzyć bramę, należy użyć [ `dotnet` narzędzia wiersza polecenia](../../core/tools/dotnet.md):

1. Otwórz okno konsoli. Na przykład w **Pytaj niczego** tekst pola na pasku zadań systemu Windows, wprowadź `Command Prompt` (lub `cmd` skrócie) i Otwórz okno konsoli wybierając **wiersza polecenia** aplikacji komputerowej lub naciskając klawisz Enter, jeśli jest zaznaczona w wynikach wyszukiwania.

1. Przejdź do katalogu projektu biblioteki. O ile nie zostało ponownie skonfigurować lokalizację pliku typowe, znajduje się on w *2017\Projects\ClassLibraryProjects\StringLibrary Documents\Visual Studio* katalogu. Katalog zawiera kod źródłowy i plik projektu *StringLibrary.csproj*.

1. Należy wydać polecenie `dotnet pack --no-build`. `dotnet` Narzędzie generuje pakiet o *.nupkg* rozszerzenia.

   > [!TIP]
   > Jeśli katalog zawierający *dotnet.exe* jest nie znajduje się w ŚCIEŻCE, można znaleźć lokalizacji, wprowadzając `where dotnet.exe` w oknie konsoli.

Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [Tworzenie pakietu NuGet narzędziami Cross Platform](../../core/deploying/creating-nuget-packages.md).
