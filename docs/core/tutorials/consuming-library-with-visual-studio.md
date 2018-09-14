---
title: Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017
description: Dowiedz się, jak wywołać składowe w bibliotece klas w programie Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 52ec46c23bb928b49f034270ed1d510d1acf992e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518168"
---
# <a name="consuming-a-net-standard-library-in-visual-studio-2017"></a>Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017

Po utworzeniu biblioteki klas .NET Standard, wykonując kroki opisane w [tworzenia biblioteki klas C# za pomocą programu .NET Core w programie Visual Studio 2017](./library-with-visual-studio.md) lub [Tworzenie biblioteki klas w języku Visual Basic z platformą .NET Core w programie Visual Studio 2017 ](vb-library-with-visual-studio.md), przetestowane w [testowanie biblioteki klas w języku .NET Core w programie Visual Studio 2017](testing-library-with-visual-studio.md), a wbudowane wersji biblioteki, następnym krokiem jest być udostępniana dla kodu wywołującego. Można to zrobić na dwa sposoby:

* Jeśli biblioteka będzie używany przez jedno rozwiązanie (na przykład, jeśli jest on składnikiem w jednej aplikacji duże), możesz dołączyć go jako projekt w rozwiązaniu.

* Jeśli biblioteka będzie ogólnie dostępna, można rozprowadzić ją jako pakiet NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>W tym bibliotekę jako projekt w rozwiązaniu

Tak, jak testy jednostkowe są zawarte w tym samym rozwiązaniu jako biblioteki klas, można umieścić aplikację w ramach tego rozwiązania. Na przykład można użyć biblioteki klas w aplikacji konsoli, który monituje użytkownika o podanie ciągu i raporty, czy jego pierwszy znak jest wielką literą:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Otwórz `ClassLibraryProjects` rozwiązanie utworzone w [tworzenia biblioteki klas C# za pomocą programu .NET Core w programie Visual Studio 2017](./library-with-visual-studio.md) tematu. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt** z menu kontekstowe.

1. W **Dodaj nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** a następnie wybierz węzeł **platformy .NET Core** węzła następuje **Aplikacja konsoli (.NET Core)** szablon projektu. W **nazwa** pole tekstowe, wpisz "Pokaz", a następnie wybierz **OK** przycisku.

   ![Dodaj okno dialogowe Nowy projekt](./media/consuming-library-with-visual-studio/addnewproject.png)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokaz** projektu, a następnie wybierz **Ustaw jako projekt startowy** w menu kontekstowym. 

   ![Menu kontekstowe pokaz](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Początkowo projektu nie ma dostępu do biblioteki klas. Aby umożliwić go do wywoływania metody w bibliotece klasy, należy utworzyć odwołanie do biblioteki klas. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.

   ![Menu kontekstowe zależności pokaz](./media/consuming-library-with-visual-studio/addreference.png)

1. W **Menadżer odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projekt biblioteki klas, a następnie wybierz **OK** przycisku.

   ![Menadżer odwołań](./media/consuming-library-with-visual-studio/referencemanager.png)

1. W oknie kodu *Program.cs* pliku, Zastąp cały kod następującym kodem:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Kod używa `row` zmiennej do utrzymywania licznika liczby wierszy danych zapisanych w oknie konsoli. Zawsze, gdy jest mniejsza niż 25, kod Czyści okno konsoli i zostanie wyświetlony komunikat dla użytkownika.

   Monituje użytkownika o podanie ciągu. Oznacza to, czy ciąg rozpoczyna się od wielkiej litery. Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciągu, kończy działanie aplikacji i zamyka okno konsoli.

1. W razie potrzeby zmień narzędzi do kompilowania **debugowania** wersji `ShowCase` projektu. Skompilować i uruchomić program, wybierając zieloną strzałkę na **pokaz** przycisku.

   ![Obraz](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Otwórz `ClassLibraryProjects` rozwiązanie utworzone w [tworzenia klasy biblioteki w języku Visual Basic i .NET Core w programie Visual Studio 2017](vb-library-with-visual-studio.md) tematu. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt** z menu kontekstowe.

1. W **Dodaj nowy projekt** okna dialogowego, rozwiń węzeł **języka Visual Basic** a następnie wybierz węzeł **platformy .NET Core** węzła następuje **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "Pokaz", a następnie wybierz **OK** przycisku.

   ![Dodaj okno dialogowe Nowy projekt](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokaz** projektu, a następnie wybierz **Ustaw jako projekt startowy** w menu kontekstowym. 

   ![Menu kontekstowe pokaz](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Początkowo projektu nie ma dostępu do biblioteki klas. Aby umożliwić go do wywoływania metody w bibliotece klasy, należy utworzyć odwołanie do biblioteki klas. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.

   ![Menu kontekstowe zależności pokaz](./media/consuming-library-with-visual-studio/addreference.png)

1. W **Menadżer odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projekt biblioteki klas, a następnie wybierz **OK** przycisku.

   ![Menadżer odwołań](./media/consuming-library-with-visual-studio/referencemanager.png)

1. W oknie kodu *Program.vb* pliku, Zastąp cały kod następującym kodem:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod używa `row` zmiennej do utrzymywania licznika liczby wierszy danych zapisanych w oknie konsoli. Zawsze, gdy jest mniejsza niż 25, kod Czyści okno konsoli i zostanie wyświetlony komunikat dla użytkownika.

   Monituje użytkownika o podanie ciągu. Oznacza to, czy ciąg rozpoczyna się od wielkiej litery. Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciągu, kończy działanie aplikacji i zamyka okno konsoli.

1. W razie potrzeby zmień narzędzi do kompilowania **debugowania** wersji `ShowCase` projektu. Skompilować i uruchomić program, wybierając zieloną strzałkę na **pokaz** przycisku.

   ![Obraz](./media/consuming-library-with-visual-studio/toolbar.png)
---

Możesz debugować i publikować aplikacji, która korzysta z tej biblioteki, wykonując kroki opisane w [debugowanie aplikacji Hello World w programie Visual Studio 2017](debugging-with-visual-studio.md) i [publikowanie aplikacji Hello World z programem Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Dystrybucja biblioteki w pakiecie NuGet

Można udostępnić biblioteki klas powszechnie przez opublikowanie go jako pakiet NuGet. Program Visual Studio nie obsługuje tworzenia pakietów NuGet. Aby utworzyć, należy użyć [ `dotnet` narzędzia wiersza polecenia](../../core/tools/dotnet.md):

1. Otwórz okno konsoli. Na przykład w **Zadaj mi dowolne pytanie** tekstu pola na pasku zadań Windows, należy wprowadzić `Command Prompt` (lub `cmd` w skrócie) i Otwórz okno konsoli wybierając **wiersza polecenia** aplikacji klasycznej lub jeśli została wybrana w wynikach wyszukiwania, naciskając klawisz Enter.

1. Przejdź do katalogu projektu biblioteki. O ile nie został ponownie skonfigurowany lokalizacji pliku typowe, jest on *2017\Projects\ClassLibraryProjects\StringLibrary Documents\Visual Studio* katalogu. Katalog zawiera kod źródłowy i plik projektu *StringLibrary.csproj*.

1. Należy wydać polecenie `dotnet pack --no-build`. `dotnet` Narzędzie generuje pakiet z *.nupkg* rozszerzenia.

   > [!TIP]
   > Jeśli katalog, który zawiera *dotnet.exe* jest nie w ŚCIEŻCE, można znaleźć lokalizacji, wprowadzając `where dotnet.exe` w oknie konsoli.

Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [jak utworzyć pakiet NuGet za pomocą wielu narzędzi platformy](../../core/deploying/creating-nuget-packages.md).
