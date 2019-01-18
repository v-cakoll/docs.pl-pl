---
title: Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017
description: Tworzenie aplikacji .NET Core, która wywołuje członków innego biblioteki klas w programie Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 7689d45b341dbe9dbfae40beec3a7663e2bd0366
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362395"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a>Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017

Po utworzeniu biblioteki klas .NET Standard, wykonując kroki opisane w [tworzenia biblioteki klas C# za pomocą programu .NET Core w programie Visual Studio 2017](./library-with-visual-studio.md) lub [Tworzenie biblioteki klas w języku Visual Basic z platformą .NET Core w programie Visual Studio 2017 ](vb-library-with-visual-studio.md), przetestowane w [testowanie biblioteki klas w języku .NET Core w programie Visual Studio 2017](testing-library-with-visual-studio.md), a wbudowane wersji biblioteki, następnym krokiem jest być udostępniana dla kodu wywołującego. Można to zrobić na dwa sposoby:

* Jeśli biblioteka będzie używany przez jedno rozwiązanie (na przykład, jeśli jest on składnikiem w jednej aplikacji duże), możesz dołączyć go jako projekt w rozwiązaniu.

* Jeśli biblioteka będzie ogólnie dostępna, można rozprowadzić ją jako pakiet NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>W tym bibliotekę jako projekt w rozwiązaniu

Tak, jak testy jednostkowe są zawarte w tym samym rozwiązaniu jako biblioteki klas, można umieścić aplikację w ramach tego rozwiązania. Na przykład można użyć biblioteki klas w aplikacji konsoli, który monituje użytkownika o podanie ciągu i raporty, czy jego pierwszy znak jest wielką literą:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Otwórz `ClassLibraryProjects` rozwiązanie utworzone w [tworzenia biblioteki klas C# za pomocą programu .NET Core w programie Visual Studio 2017](./library-with-visual-studio.md) tematu. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt** z menu kontekstowe.

1. W **Dodaj nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** a następnie wybierz węzeł **platformy .NET Core** węzła następuje **Aplikacja konsoli (.NET Core)** szablon projektu. W **nazwa** pole tekstowe, wpisz "Pokaz", a następnie wybierz **OK** przycisku.

   ![Visual Studio Dodaj nowy projekt okno dialogowe-C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokaz** projektu, a następnie wybierz **Ustaw jako projekt startowy** w menu kontekstowym.

   ![Visual Studio projektu menu kontekstowego można ustawić projekt startowy-C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Początkowo projektu nie ma dostępu do biblioteki klas. Aby umożliwić go do wywoływania metody w bibliotece klasy, należy utworzyć odwołanie do biblioteki klas. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.

   ![Projektu programu Visual Studio Dodaj odwołanie do menu kontekstowego-C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. W **Menadżer odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projekt biblioteki klas, a następnie wybierz **OK** przycisku.

   ![Zarządzanie Visual Studio odwołuje się do okna dialogowego —C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. W oknie kodu *Program.cs* pliku, Zastąp cały kod następującym kodem:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Kod używa `row` zmiennej do utrzymywania licznika liczby wierszy danych zapisanych w oknie konsoli. Zawsze, gdy jest mniejsza niż 25, kod Czyści okno konsoli i zostanie wyświetlony komunikat dla użytkownika.

   Monituje użytkownika o podanie ciągu. Oznacza to, czy ciąg rozpoczyna się od wielkiej litery. Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciągu, kończy działanie aplikacji i zamyka okno konsoli.

1. W razie potrzeby zmień narzędzi do kompilowania **debugowania** wersji `ShowCase` projektu. Skompilować i uruchomić program, wybierając zieloną strzałkę na **pokaz** przycisku.

   ![Przycisk debugowania przedstawiający narzędzi projektu programu Visual Studio —C#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Otwórz `ClassLibraryProjects` rozwiązanie utworzone w [tworzenia klasy biblioteki w języku Visual Basic i .NET Core w programie Visual Studio 2017](vb-library-with-visual-studio.md) tematu. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt** z menu kontekstowe.

1. W **Dodaj nowy projekt** okna dialogowego, rozwiń węzeł **języka Visual Basic** a następnie wybierz węzeł **platformy .NET Core** węzła następuje **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** pole tekstowe, wpisz "Pokaz", a następnie wybierz **OK** przycisku.

   ![Visual Studio Dodaj okno dialogowe Nowy projekt - Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokaz** projektu, a następnie wybierz **Ustaw jako projekt startowy** w menu kontekstowym. 

   ![Visual Studio projektu menu kontekstowego można ustawić projekt startowy - Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Początkowo projektu nie ma dostępu do biblioteki klas. Aby umożliwić go do wywoływania metody w bibliotece klasy, należy utworzyć odwołanie do biblioteki klas. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.

   ![Projektu programu Visual Studio Dodaj odwołanie do menu kontekstowego - Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. W **Menadżer odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projekt biblioteki klas, a następnie wybierz **OK** przycisku.

   ![Zarządzanie Visual Studio odwołuje się do okna dialogowego - Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. W oknie kodu *Program.vb* pliku, Zastąp cały kod następującym kodem:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod używa `row` zmiennej do utrzymywania licznika liczby wierszy danych zapisanych w oknie konsoli. Zawsze, gdy jest mniejsza niż 25, kod Czyści okno konsoli i zostanie wyświetlony komunikat dla użytkownika.

   Monituje użytkownika o podanie ciągu. Oznacza to, czy ciąg rozpoczyna się od wielkiej litery. Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciągu, kończy działanie aplikacji i zamyka okno konsoli.

1. W razie potrzeby zmień narzędzi do kompilowania **debugowania** wersji `ShowCase` projektu. Skompilować i uruchomić program, wybierając zieloną strzałkę na **pokaz** przycisku.

   ![Debugowanie na pasku narzędzi - Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)
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
