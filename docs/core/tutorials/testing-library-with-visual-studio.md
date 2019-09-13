---
title: Testowanie biblioteki klas .NET Standard przy użyciu platformy .NET Core w programie Visual Studio 2017
description: Utwórz projekt testu jednostkowego dla biblioteki klas platformy .NET Core. Sprawdź, czy biblioteka klas .NET Core działa prawidłowo z testami jednostkowymi.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: e8a0d28919d4d26e69fb5a5f926b0e96270a2407
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925888"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a>Testowanie biblioteki .NET Standard na platformie .NET Core w programie Visual Studio 2017

W obszarze [Kompilowanie biblioteki .NET standard C# z programem i .NET Core w programie Visual Studio 2017](library-with-visual-studio.md) lub [kompilowanie biblioteki .NET Standard z Visual Basic i .net core w programie Visual Studio 2017](vb-library-with-visual-studio.md)utworzono prostą bibliotekę klas, która dodaje metodę rozszerzenia do <xref:System.String> Klasa. Teraz utworzysz test jednostkowy, aby upewnić się, że działa zgodnie z oczekiwaniami. Należy dodać projekt testu jednostkowego do rozwiązania utworzonego w poprzednim artykule.

## <a name="creating-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Aby utworzyć projekt testu jednostkowego, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. W **Eksplorator rozwiązań**Otwórz menu kontekstowe dla węzła rozwiązania **ClassLibraryProjects** i wybierz polecenie **Dodaj** > **Nowy projekt**.

1. W oknie dialogowym **Dodawanie nowego projektu** wybierz węzeł **wizualizacji C#**  . Następnie wybierz węzeł **.NET Core** , a następnie szablon projektu **projektu testowego MSTest (.NET Core)** . W polu tekstowym **Nazwa** wprowadź wartość "StringLibraryTest" jako nazwę projektu. Wybierz **przycisk OK** , aby utworzyć projekt testu jednostkowego.

   ![Okno dialogowe Dodawanie nowego projektu z wyświetlonym projektem testów jednostkowych —C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > Oprócz projektu testowego MSTest można także użyć programu Visual Studio do utworzenia projektu testowego xUnit dla platformy .NET Core.

1. Program Visual Studio tworzy projekt i otwiera plik *UnitTest1.cs* w oknie kodu.

   ![Okno programu Visual Studio Code dla klasy projektu testów jednostkowych i metody —C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   Kod źródłowy utworzony przez szablon testu jednostkowego wykonuje następujące czynności:

   * Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostkowego.

   * Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybut`UnitTest1` do klasy. Każda metoda testowa w klasie testowej oznaczona przy użyciu \[atrybutu\] TestMethod jest wykonywana automatycznie po uruchomieniu testu jednostkowego.

   * Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut, aby zdefiniować `TestMethod1` jako metodę testową do automatycznego wykonania podczas działania testu jednostkowego.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **zależności** projektu **StringLibraryTest** i wybierz polecenie **Dodaj odwołanie** z menu kontekstowego.

   ![Menu kontekstowe zależności StringLibraryTest —C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **projekty** i zaznacz pole wyboru obok pozycji **StringLibrary**. Dodanie odwołania do `StringLibrary` zestawu umożliwia kompilatorowi znalezienie metod **StringLibrary** . Wybierz przycisk **OK**. Spowoduje to dodanie odwołania do projektu `StringLibrary`biblioteki klas.

   ![Okno dialogowe Dodawanie odwołania do projektu w programie Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. W **Eksplorator rozwiązań**Otwórz menu kontekstowe dla węzła rozwiązania **ClassLibraryProjects** i wybierz polecenie **Dodaj** > **Nowy projekt**.

1. W oknie dialogowym **Dodaj nowy projekt** wybierz węzeł **Visual Basic** . Następnie wybierz węzeł **.NET Core** , a następnie szablon projektu **projektu testowego MSTest (.NET Core)** . W polu tekstowym **Nazwa** wprowadź wartość "StringLibraryTest" jako nazwę projektu. Wybierz **przycisk OK** , aby utworzyć projekt testu jednostkowego.

   ![Okno dialogowe Dodawanie nowego projektu z wyświetlonym projektem testu jednostkowego — Visual Basic](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > Oprócz projektu testowego MSTest można także użyć programu Visual Studio do utworzenia projektu testowego xUnit dla platformy .NET Core.

1. Program Visual Studio tworzy projekt i otwiera plik *UnitTest1. vb* w oknie kodu.

   ![Okno programu Visual Studio Code dla klasy projektu testów jednostkowych i metody Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   Kod źródłowy utworzony przez szablon testu jednostkowego wykonuje następujące czynności:

   * Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostkowego.

   * Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>atrybut) `UnitTest1` do klasy. Każda metoda testowa w klasie testowej oznaczona przy użyciu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutu jest wykonywana automatycznie, gdy test jednostkowy jest uruchamiany.

   * Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut, aby zdefiniować `TestMethod1` jako metodę testową do automatycznego wykonania podczas działania testu jednostkowego.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **zależności** projektu **StringLibraryTest** i wybierz polecenie **Dodaj odwołanie** z menu kontekstowego.

   ![Menu kontekstowe zależności StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **projekty** i zaznacz pole wyboru obok pozycji **StringLibrary**. Dodanie odwołania do `StringLibrary` zestawu umożliwia kompilatorowi znalezienie metod **StringLibrary** . Wybierz przycisk **OK**. Spowoduje to dodanie odwołania do projektu `StringLibrary`biblioteki klas.

   ![Okno dialogowe Dodawanie odwołania do projektu w programie Visual Studio — Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)

---

## <a name="adding-and-running-unit-test-methods"></a>Dodawanie i uruchamianie metod testów jednostkowych

Gdy program Visual Studio uruchamia test jednostkowy, wykonuje każdą metodę oznaczoną przy użyciu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutu w klasie testów jednostkowych, klasy, do <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> której zastosowano atrybut. Metoda testowa kończy się w momencie napotkania pierwszego błędu lub gdy wszystkie testy zawarte w metodzie zakończyły się powodzeniem.

Najczęstsze testy wywołują elementy członkowskie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> klasy. Wiele metod Assert obejmuje co najmniej dwa parametry, z których jeden jest oczekiwany wynik testu, a drugi jest rzeczywistym wynikiem testu. W poniższej tabeli przedstawiono niektóre z najczęściej wywoływanych metod.

Metody Assert | Funkcja
--- | ---
`Assert.AreEqual` | Sprawdza, czy dwie wartości lub obiekty są równe. Potwierdzenie kończy się niepowodzeniem, jeśli wartości lub obiekty nie są równe.
`Assert.AreSame` | Sprawdza, czy dwie zmienne obiektów odwołują się do tego samego obiektu. Potwierdzenie kończy się niepowodzeniem, jeśli zmienne odwołują się do różnych obiektów.
`Assert.IsFalse` | Sprawdza, czy warunek to `false`. Potwierdzenie kończy się niepowodzeniem, jeśli `true`warunek ma wartość.
`Assert.IsNotNull` | Sprawdza, czy obiekt nie `null`jest. Potwierdzenie kończy się niepowodzeniem, jeśli `null`obiekt jest.

Można również zastosować <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atrybut do metody testowej. Wskazuje typ wyjątku, który metoda testowa powinna zgłosić. Test zakończy się niepowodzeniem, jeśli określony wyjątek nie zostanie zgłoszony.

W testowaniu `StringLibrary.StartsWithUpper` metody, należy podać kilka ciągów zaczynających się od wielkiej litery. Oczekiwano, że metoda zwraca `true` w tych przypadkach, więc można <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> wywołać metodę. Podobnie, chcesz podać kilka ciągów, które zaczynają się od znaku innego niż wielkie litery. Oczekiwano, że metoda zwraca `false` w tych przypadkach, więc można <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> wywołać metodę.

Ponieważ metoda biblioteki obsługuje ciągi, należy również upewnić się, że pomyślnie obsługuje [pusty ciąg (`String.Empty`)](xref:System.String.Empty), prawidłowy ciąg, który nie zawiera znaków i <xref:System.String.Length> ma wartość 0, i `null` ciąg, który nie został Initialize. Jeśli `StartsWithUpper` jest wywoływana jako metoda <xref:System.String> rozszerzająca wystąpienia, nie można przesłać `null` ciągu. Można jednak wywołać go bezpośrednio jako metodę statyczną i przekazać pojedynczy <xref:System.String> argument.

Zdefiniujesz trzy metody, z których każda będzie wielokrotnie wywoływana <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> dla każdego elementu w tablicy ciągów. Ponieważ metoda testowa nie powiedzie się, gdy wystąpi pierwszy błąd, wywoła Przeciążenie metody, która umożliwia przekazywanie ciągu, który wskazuje wartość ciągu używaną w wywołaniu metody.

Aby utworzyć metody testowe:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. W oknie kod *UnitTest1.cs* Zastąp kod następującym kodem:

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Należy zauważyć, że test pisany wielkimi literami w `TestStartsWithUpper` metodzie obejmuje grecką wielką literę alfa (u + 0391) oraz wielką literę pauzy (u + 041C), a test małych znaków `TestDoesNotStartWithUpper` w metodzie zawiera małą literę grecką. Alpha (U + 03B1) i mała litera cyrylicy GHE (U + 0433).

1. Na pasku menu wybierz pozycję **plik** > **Zapisz UnitTest1.cs jako**. W oknie dialogowym **Zapisz plik jako** wybierz strzałkę obok przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem**.

   ![Okno dialogowe zapisywania pliku w programie Visual StudioC#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. W oknie kod *UnitTest1. vb* Zastąp kod następującym kodem:

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Należy zauważyć, że test pisany wielkimi literami w `TestStartsWithUpper` metodzie obejmuje grecką wielką literę alfa (u + 0391) oraz wielką literę pauzy (u + 041C), a test małych znaków `TestDoesNotStartWithUpper` w metodzie zawiera małą literę grecką. Alpha (U + 03B1) i mała litera cyrylicy GHE (U + 0433).

1. Na pasku menu wybierz pozycję **plik** > **Zapisz UnitTest1. vb jako**. W oknie dialogowym **Zapisz plik jako** wybierz strzałkę obok przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem**.

   ![Okno dialogowe Zapisz plik w programie Visual Studio — Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

---

1. W oknie dialogowym **Potwierdzanie zapisywania jako** wybierz przycisk **tak** , aby zapisać plik.

1. W oknie dialogowym **Zaawansowane opcje zapisywania** wybierz pozycję **Unicode (UTF-8 z podpisem)-strona kodowa 65001** z listy rozwijanej **kodowanie** i wybierz **przycisk OK**.

   ![Zaawansowane opcje zapisywania programu Visual Studio — okno dialogowe](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Jeśli kod źródłowy nie zostanie zapisany jako plik zakodowany w formacie UTF8, program Visual Studio może go zapisać jako plik ASCII. Gdy tak się stanie, środowisko uruchomieniowe nie będzie poprawnie zdekodować znaków UTF8 poza zakresem ASCII, a wyniki testu nie będą dokładne.

1. Na pasku menu wybierz kolejno opcje **test** > **Uruchom** > **wszystkie testy**. Zostanie otwarte okno **Eksplorator testów** , które pokazuje, że testy zostały wykonane pomyślnie. Trzy testy są wymienione w sekcji **testy zakończone** , a sekcja **podsumowania** raportuje wynik przebiegu testu.

   ![Okno Eksploratora testów z przekazaniem testów](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a>Obsługa błędów testów

Przebieg testu nie miał błędów, ale nieco zmienia się, tak aby jedna z metod testowych nie powiodła się:

1. Zmodyfikuj tablicę `TestDoesNotStartWithUpper` w metodzie, aby uwzględnić ciąg "Error". `words` Nie musisz zapisywać pliku, ponieważ program Visual Studio automatycznie zapisuje otwarte pliki w przypadku skompilowania rozwiązania do uruchamiania testów.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Uruchom test, wybierając pozycję **test** > **Uruchom** > **wszystkie testy** z paska menu. Okno **Eksplorator testów** wskazuje, że dwa testy zostały wykonane pomyślnie i jeden z nich zakończył się niepowodzeniem.

   ![Okno Eksploratora testów z niepowodzeniem testami](./media/testing-library-with-visual-studio/failed-test-window.png)

1. W sekcji **testy zakończone niepowodzeniem** wybierz test `TestDoesNotStartWith`zakończony niepowodzeniem. Okno **Eksplorator testów** wyświetla komunikat utworzony przez potwierdzenie: "Assert. IsFalse nie powiodło się. Oczekiwano dla elementu "Error": false; właściwą True ". Ze względu na niepowodzenie wszystkie ciągi w tablicy po "Error" nie zostały przetestowane.

   ![Okno Eksploratora testów przedstawiające błąd potwierdzenia jest fałszywy](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Cofnij modyfikację w kroku 1 i usuń ciąg "Error". Ponownie uruchom test i testy zostaną zakończone pomyślnie.

## <a name="testing-the-release-version-of-the-library"></a>Testowanie wersji wydania biblioteki

Uruchomiono testy w odniesieniu do wersji debugowania biblioteki. Teraz, gdy testy zostały zakończone pomyślnie i przetestowano bibliotekę, należy uruchomić testy w dodatkowym czasie w odniesieniu do kompilacji wydania biblioteki. Wiele czynników, w tym Optymalizacja kompilatora, może czasami generować różne zachowanie między kompilacjami w wersji Debug i Release.

Aby przetestować kompilację wydania:

1. Na pasku narzędzi programu Visual Studio Zmień konfigurację kompilacji z **Debuguj** do **Release**.

   ![Pasek narzędzi programu Visual Studio z wyróżnioną kompilacją wydania](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **StringLibrary** i wybierz polecenie **Kompiluj** z menu kontekstowego, aby ponownie skompilować bibliotekę.

   ![Menu kontekstowe StringLibrary z poleceniem Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Uruchom testy jednostkowe, wybierając pozycję **test** > **Uruchom** > **wszystkie testy** z paska menu. Testy zostały zakończone pomyślnie.

Po zakończeniu testowania biblioteki następnym krokiem jest udostępnienie jej do wywoływania. Można powiązać ją z co najmniej jedną lub wieloma aplikacjami lub rozpowszechniać ją jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz [zużywanie biblioteki klas .NET Standard](./consuming-library-with-visual-studio.md).
