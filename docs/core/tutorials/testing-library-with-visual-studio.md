---
title: Testowanie biblioteki klas .NET Standard z platformą .NET Core w programie Visual Studio 2017
description: Utwórz projekt testu jednostkowego dla biblioteki klas platformy .NET Core. Sprawdź, czy biblioteki klas platformy .NET Core działa poprawnie przy użyciu testów jednostkowych.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 352599d60a42a034b3d6647b1fe8f1cbf2f4572d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647934"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a>Test biblioteki .NET Standard z platformą .NET Core w programie Visual Studio 2017

W [kompilacji biblioteki .NET Standard z C# i .NET Core w programie Visual Studio 2017](library-with-visual-studio.md) lub [Tworzenie biblioteki .NET Standard, w języku Visual Basic i .NET Core w programie Visual Studio 2017](vb-library-with-visual-studio.md), utworzyć prostą klasę Biblioteka, która dodaje metodę rozszerzenia, aby <xref:System.String> klasy. Teraz utworzysz testu jednostkowego, aby upewnić się, że działa zgodnie z oczekiwaniami. Dodasz projektu testu jednostkowego z rozwiązaniem, utworzonej w poprzednim artykule.

## <a name="creating-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Aby utworzyć projekt testów jednostkowych, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **ClassLibraryProjects** węzła rozwiązania, a następnie wybierz **Dodaj** > **nowy projekt**.

1. W **Dodaj nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła. Następnie wybierz pozycję **platformy .NET Core** węzła następuje **projekt testów MSTest (.NET Core)** szablonu projektu. W **nazwa** tekstu wprowadź "StringLibraryTest" jako nazwę projektu. Wybierz **OK** Aby utworzyć projekt testów jednostkowych.

   ![Dodaj okno dialogowe Nowy projekt z wyświetlane - projekt testów jednostkowychC#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > Oprócz projekt testów MSTest można również użyć programu Visual Studio utworzyć projekt testu xUnit dla platformy .NET Core.

1. Visual Studio tworzy projekt i otworzy *UnitTest1.cs* pliku w oknie kodu.

   ![Visual Studio okna kodu jednostki testowania projektu klasy i metody —C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   Kod źródłowy, utworzona przez szablon testu jednostki wykonuje następujące czynności:

   * Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostki.

   * Ma to zastosowanie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybutu `UnitTest1` klasy. Każdej metody w klasie testowej oznakowane za pomocą \[TestMethod\] atrybutu jest wykonywane automatycznie po uruchomieniu testu jednostkowego.

   * Ma to zastosowanie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut do definiowania `TestMethod1` jako metoda testowa do wykonania automatycznego po uruchomieniu testu jednostkowego.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **zależności** węźle **StringLibraryTest** projektu, a następnie wybierz **Dodaj odwołanie** z menu kontekstowe.

   ![Menu kontekstowe zależności StringLibraryTest-C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. W **Menadżer odwołań** okna dialogowego, rozwiń węzeł **projektów** węzła i zaznacz pole wyboru obok pozycji **StringLibrary**. Dodawanie odwołania do `StringLibrary` zestawu umożliwia kompilatorowi znaleźć **StringLibrary** metody. Wybierz przycisk **OK**. Dodaje to odwołanie do projektu biblioteki klas `StringLibrary`.

   ![Program Visual Studio Dodaj projekt odwołania w oknie dialogowym](./media/testing-library-with-visual-studio/project-reference-manager.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb) 
1. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla **ClassLibraryProjects** węzła rozwiązania, a następnie wybierz **Dodaj** > **nowy projekt**.

1. W **Dodaj nowy projekt** okno dialogowe, wybierz opcję **języka Visual Basic** węzła. Następnie wybierz pozycję **platformy .NET Core** węzła następuje **projekt testów MSTest (.NET Core)** szablonu projektu. W **nazwa** tekstu wprowadź "StringLibraryTest" jako nazwę projektu. Wybierz **OK** Aby utworzyć projekt testów jednostkowych.

   ![Dodaj okno dialogowe Nowy projekt z projektu testu jednostkowego wyświetlane - Visual Basic](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > Oprócz projekt testów MSTest można również użyć programu Visual Studio utworzyć projekt testu xUnit dla platformy .NET Core.

1. Visual Studio tworzy projekt i otworzy *UnitTest1.vb* pliku w oknie kodu.

   ![Visual Studio okna kodu jednostki testowania projektu klasy i metody - Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   Kod źródłowy, utworzona przez szablon testu jednostki wykonuje następujące czynności:

   * Importuje [Microsoft.VisualStudio.TestTools.UnitTesting]<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=namewithType> przestrzeń nazw, która zawiera typy używane do testowania jednostki.

   * Ma to zastosowanie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>) atrybutu `UnitTest1` klasy. Każdej metody w klasie testowej oznakowane za pomocą <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutu jest wykonywane automatycznie po uruchomieniu testu jednostkowego.

   * Ma to zastosowanie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut do definiowania `TestMethod1` jako metoda testowa do wykonania automatycznego po uruchomieniu testu jednostkowego.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **zależności** węźle **StringLibraryTest** projektu, a następnie wybierz **Dodaj odwołanie** z menu kontekstowe.

   ![Menu kontekstowe StringLibraryTest zależności](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. W **Menadżer odwołań** okna dialogowego, rozwiń węzeł **projektów** węzła i zaznacz pole wyboru obok pozycji **StringLibrary**. Dodawanie odwołania do `StringLibrary` zestawu umożliwia kompilatorowi znaleźć **StringLibrary** metody. Wybierz przycisk **OK**. Dodaje to odwołanie do projektu biblioteki klas `StringLibrary`.

   ![Program Visual Studio Dodaj okno dialogowe z odwołania projekt - Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)
---

## <a name="adding-and-running-unit-test-methods"></a>Dodawanie i uruchamianie jednostki metod testowych

Po uruchomieniu programu Visual Studio test jednostkowy wykonuje każda metoda oznaczona za pomocą <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut w klasie testu jednostki, klasy, do którego <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybut jest stosowany. Metody testowej kończy się, gdy zostanie osiągnięty pierwszy błąd lub wszystkie testy znajdujących się w metodzie zakończyły się powodzeniem.

Najczęściej testy wywołanie członkowie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> klasy. Asercja wiele metod zawierać co najmniej dwa parametry: jednym z nich jest wynik testu oczekiwany, a drugi z nich to wyniku testu rzeczywistych. Niektóre z jego najczęściej wywoływanych metod przedstawiono w poniższej tabeli.

Metody Assert | Funkcja
--- | ---
`Assert.AreEqual` | Sprawdza, czy dwie wartości bądź obiekty są równe. Asercja nie powiedzie się, jeśli wartości bądź obiekty nie są równe.
`Assert.AreSame` | Sprawdza, czy dwie zmienne do obiektu odnoszą się do tego samego obiektu. Asercja nie powiedzie się, jeśli zmienne odnoszą się do różnych obiektów.
`Assert.IsFalse` | Sprawdza, czy warunek jest `false`. Asercja kończy się niepowodzeniem, jeśli wynikiem warunku jest `true`.
`Assert.IsNotNull` | Sprawdza, czy obiekt jest nie `null`. Niepowodzenie asercji, jeśli obiekt jest `null`.

Można również zastosować <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atrybutu do metody testowej. Wskazuje typ wyjątku, który powinien zgłosić metody testowej. Test kończy się niepowodzeniem, jeśli określony wyjątek nie zostanie zgłoszony.

Podczas testowania `StringLibrary.StartsWithUpper` metody chcesz podać liczbę ciągów, które zaczynają się od wielkiej litery. Oczekujesz, że metoda zwraca `true` więc w takich przypadkach można wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> metody. Podobnie chcesz udostępnić wiele ciągów, które zaczynają się coś innego niż wielkiej litery. Oczekujesz, że metoda zwraca `false` więc w takich przypadkach można wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> metody.

Ponieważ biblioteki obsługiwała ciągów, chcesz także upewnij się, że pomyślnie obsługi [pusty ciąg (`String.Empty`)](xref:System.String.Empty), prawidłowy ciąg bez znaków i którego <xref:System.String.Length> ma wartość 0, a `null` ciąg który nie został zainicjowany. Jeśli `StartsWithUpper` jest wywoływana jako metoda rozszerzenia w <xref:System.String> wystąpienia, go nie mogą być przekazywane `null` ciągu. Można jednak także wywołać ją bezpośrednio jako metoda statyczna i przekaż jeden <xref:System.String> argumentu.

Należy zdefiniować trzy metody wszystkich, która wywołuje metodę jego <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metoda wielokrotnie dla każdego elementu w tablicy ciągów. Ponieważ metoda testowa nie powiedzie się, jak najszybciej po napotkaniu pierwszego niepowodzenia, będzie wywoływać przeciążenia metody, które umożliwia przekazywanie ciąg, który wskazuje wartość ciągu w wywołaniu metody.

Aby utworzyć metody testowe:

# <a name="ctabcsharp"></a>[C#](#tab/csharp) 
1. W *UnitTest1.cs* okna kodu, Zastąp kod następującym kodem:

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Należy zauważyć, że test z wielkie litery znaków w `TestStartsWithUpper` metoda zawiera alfa greckim wielkiej litery (U + 0391) i uzyskać wielką literę EM (U + 041 C), a test małych liter w `TestDoesNotStartWithUpper` metoda zawiera greckim mała litera alfa (U + 03B1) i mała cyrylica list Ghe (U + 0433).

1. Na pasku menu wybierz **pliku** > **Zapisz UnitTest1.cs jako**. W **Zapisz plik jako** okno dialogowe, wybierz strzałkę obok **Zapisz** przycisk, a następnie wybierz pozycję **Zapisz z kodowaniem**.

   ![Visual Studio Zapisz plik jako okno dialogowe-C#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb) 
1. W *UnitTest1.vb* okna kodu, Zastąp kod następującym kodem:

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Należy zauważyć, że test z wielkie litery znaków w `TestStartsWithUpper` metoda zawiera alfa greckim wielkiej litery (U + 0391) i uzyskać wielką literę EM (U + 041 C), a test małych liter w `TestDoesNotStartWithUpper` metoda zawiera greckim mała litera alfa (U + 03B1) i mała cyrylica list Ghe (U + 0433).

1. Na pasku menu wybierz **pliku** > **Zapisz UnitTest1.vb jako**. W **Zapisz plik jako** okno dialogowe, wybierz strzałkę obok **Zapisz** przycisk, a następnie wybierz pozycję **Zapisz z kodowaniem**.

   ![Visual Studio Zapisz plik jako okno dialogowe - Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)
---

1. W **Potwierdź zapisywanie jako** okno dialogowe, wybierz opcję **tak** przycisk, aby zapisać plik.

1. W **zaawansowane opcje zapisywania** okno dialogowe, wybierz opcję **Unicode (UTF-8 z podpisem) - strona kodowa 65001** z **kodowanie** listy rozwijanej i wybierz pozycję **OK** .

   ![Visual Studio zaawansowane opcje zapisywania okna dialogowego](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Jeśli nie można zapisać kod źródłowy jako plik z kodowaniem UTF8, Visual Studio może ją zapisać jako plik ASCII. Jeśli tak się stanie, środowisko wykonawcze nie dokładnie dekodowania znaków UTF8 poza zakresem ASCII, a wyniki testu nie będzie dokładny.

1. Na pasku menu wybierz **testu** > **Uruchom** > **wszystkie testy**. **Eksplorator testów** okna otwiera się i pokazuje, że testy zostały wykonane pomyślnie. Trzy testy są wymienione w **testy zakończone powodzeniem** sekcji i **Podsumowanie** sekcji raportowane są wynikiem testu.

   ![Testowanie okna Eksploratora z przekazaniem testów](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a>Obsługa niepowodzeń testów

Przebieg testu miał żadne błędy, ale zmień je nieco, tak aby jednej z metod testowych kończy się niepowodzeniem:

1. Modyfikowanie `words` tablicy w `TestDoesNotStartWithUpper` metodę, aby dołączyć ciąg "Error". Nie potrzebujesz zapisać plik, ponieważ program Visual Studio automatycznie zapisuje otwartych plików podczas kompilowania rozwiązania do uruchamiania testów.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Uruchom test, wybierając **Test** > **Uruchom** > **wszystkie testy** z paska menu. **Eksplorator testów** okno wskazuje, że dwóch testów zakończyła się pomyślnie i jeden nie powiodło się.

   ![Okno Eksploratora testów za pomocą testy zakończone niepowodzeniem](./media/testing-library-with-visual-studio/failed-test-window.png)

1. W **testy zakończone niepomyślnie** wybierz test zakończony niepowodzeniem `TestDoesNotStartWith`. **Eksplorator testów** okna wyświetlany jest komunikat generowany przez assert: "Assert.IsFalse nie powiodło się. Oczekiwana dla "Error": false; rzeczywista: True". Wszystkie ciągi w tablicy po "Błąd" nie zostały przetestowane z powodu błędu.

   ![Okno Eksploratora testów, wyświetlane jest False Błąd potwierdzenia](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Cofnij zmiany, które były wykonane w kroku 1, a następnie usuń ciąg "Error". Uruchom ponownie test i testy zostaną przetworzone.

## <a name="testing-the-release-version-of-the-library"></a>Testowanie wersji biblioteki

Działała testów przeciwko wersja do debugowania biblioteki. Teraz, gdy testy wszystkich przeszły i odpowiednio przetestowaniu biblioteki, należy przeprowadzić testy dodatkowy czas dla kompilacji wydania biblioteki. Wiele czynników, takich jak optymalizacje kompilatora, czasami może wygenerować różne zachowanie między kompilacjami Debug i Release.

Aby przetestować kompilacji wydania:

1. Na pasku narzędzi programu Visual Studio, zmień konfigurację kompilacji z **debugowania** do **wersji**.

   ![Visual Studio pasek narzędzi kompilacji wydania wyróżniony](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **StringLibrary** projektu, a następnie wybierz **kompilacji** z menu kontekstowego, aby ponownie skompilować biblioteki.

   ![Menu kontekstowe StringLibrary za pomocą polecenia kompilacji](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Uruchamianie testów jednostkowych, wybierając **testu** > **Uruchom** > **wszystkie testy** z paska menu. Testy zostały zakończone pomyślnie.

Teraz, gdy zakończysz testy biblioteki, następnym krokiem jest być udostępniana dla kodu wywołującego. Istnieje możliwość połączenia z co najmniej jednej aplikacji lub rozpowszechnianie ich jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz [korzystanie z biblioteki klas .NET Standard](./consuming-library-with-visual-studio.md).
