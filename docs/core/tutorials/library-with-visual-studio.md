---
title: Tworzenie biblioteki klas .NET Standard w programie Visual Studio
description: Dowiedz się, jak utworzyć .NET Standard bibliotekę klas przy użyciu programu Visual Studio.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7d64ca32bdbe20f949ae575bc4c3f9bbb594fffd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283627"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a>Samouczek: Tworzenie biblioteki .NET Standard w programie Visual Studio

*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację. Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard. Po zakończeniu biblioteki klas możesz zdecydować, czy chcesz ją rozpowszechnić jako składnik innej firmy, czy chcesz ją dołączyć jako składnik pakietu z co najmniej jedną aplikacjami.

> [!NOTE]
> Listę wersji .NET Standard i obsługiwanych przez nich platform można znaleźć w temacie [.NET Standard](../../standard/net-standard.md).

W tym samouczku utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów. Implementuje ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim <xref:System.String> klasy.

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2019 w wersji 16,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym **wieloplatformowym obciążeniem programistycznym dla platformy .NET Core** . Zestaw .NET Core 3,1 SDK jest instalowany automatycznie po wybraniu tego obciążenia.

  Aby uzyskać więcej informacji, zobacz sekcję [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie zestaw .NET Core SDK](../install/sdk.md?pivots=os-windows) .

## <a name="create-a-visual-studio-solution"></a>Tworzenie rozwiązania programu Visual Studio

Zacznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas w. Rozwiązanie programu Visual Studio służy jako kontener dla jednego lub wielu projektów. Dodasz kolejne powiązane projekty do tego samego rozwiązania.

Aby utworzyć puste rozwiązanie:

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wprowadź **rozwiązanie** w polu wyszukiwania. Wybierz szablon **pustego rozwiązania** , a następnie wybierz przycisk **dalej**.

   ![Pusty szablon rozwiązania w programie Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Na stronie **Konfiguruj nowy projekt** wprowadź **ClassLibraryProjects** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

## <a name="create-a-class-library-project"></a>Tworzenie projektu biblioteki klas

1. Dodaj nowy projekt biblioteki klas .NET Standard o nazwie "StringLibrary" do rozwiązania.

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

   1. Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania. Wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform. Wybierz szablon **Biblioteka klas (.NET standard)** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibrary** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

1. Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard. Kliknij prawym przyciskiem myszy projekt Biblioteka w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Właściwości**. Pole tekstowe **platformy docelowej** pokazuje, że projekt jest docelowy .NET Standard 2,0.

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. Jeśli używasz Visual Basic, wyczyść tekst w polu tekstowym **główna przestrzeń nazw** .

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/vb/library-project-properties.png)

   Dla każdego projektu Visual Basic automatycznie tworzy przestrzeń nazw, która odnosi się do nazwy projektu. W tym samouczku zdefiniujesz przestrzeń nazw najwyższego poziomu za pomocą [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) słowa kluczowego w pliku kodu.

1. Zastąp kod w oknie kodu dla *Class1.cs* lub *Class1. vb* następującym kodem i Zapisz plik. Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   Biblioteka klas, `UtilityLibraries.StringLibrary` ,,, zawiera metodę o nazwie `StartsWithUpper` . Ta metoda zwraca <xref:System.Boolean> wartość wskazującą, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery. Standard Unicode rozróżnia wielkie litery od małych liter. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda zwraca `true` czy znak jest pisany wielką literą.

1. Na pasku menu wybierz opcję **Kompiluj**  >  **rozwiązanie kompilacji** , aby sprawdzić, czy projekt kompiluje się bez błędu.

## <a name="add-a-console-app-to-the-solution"></a>Dodawanie aplikacji konsolowej do rozwiązania

Użyj biblioteki klas w aplikacji konsolowej, która wyświetla użytkownikowi komunikat, aby wprowadzić ciąg i określić, czy ciąg rozpoczyna się od wielkiej litery.

1. Dodaj nową aplikację konsolową .NET Core do rozwiązania.

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

   1. Na stronie **Dodawanie nowego projektu** wprowadź w polu wyszukiwania **konsolę** . Wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.

   1. Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Konfiguruj nowy projekt** wprowadź wartość **Prezentacja** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **pokazu** i wybierz polecenie **Ustaw jako projekt startowy** w menu kontekstowym.

   ![Menu kontekstowe projektu programu Visual Studio, aby ustawić projekt startowy](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. Początkowo nowy projekt aplikacji konsolowej nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, Utwórz odwołanie do projektu do projektu biblioteki klas. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy `ShowCase` węzeł **zależności** projektu i wybierz polecenie **Dodaj odwołanie do projektu**.

   ![Dodaj menu kontekstowe odwołania w programie Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** wybierz projekt **StringLibrary** , a następnie wybierz **przycisk OK**.

   ![Okno dialogowe programu Reference Manager z wybraną pozycją StringLibrary](media/library-with-visual-studio/manage-project-references.png)

1. W oknie kodu dla pliku *program.cs* lub *program. vb* Zastąp cały kod następującym kodem.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli. Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.

   Program poprosi użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg rozpoczyna się od wielkiej litery. Jeśli użytkownik naciśnie klawisz ENTER bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.

1. W razie potrzeby zmień pasek narzędzi w celu skompilowania wersji **debugowania** `ShowCase` projektu. Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **Pokaz** .

   ![Pasek narzędzi projektu programu Visual Studio z widocznym przyciskiem Debuguj](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. Wypróbuj program, wprowadzając ciągi i naciskając klawisz **Enter**, a następnie naciśnij klawisz **Enter** , aby wyjść.

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Okno konsoli z uruchomionym pokazem":::

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono rozwiązanie, dodano projekt biblioteki i dodano projekt aplikacji konsolowej, który używa biblioteki. W następnym samouczku dodasz projekt testu jednostkowego do rozwiązania.

> [!div class="nextstepaction"]
> [Testowanie biblioteki .NET Standard przy użyciu platformy .NET Core w programie Visual Studio](testing-library-with-visual-studio.md)
