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
ms.openlocfilehash: 242234d93bc1b8f9b88749f2e3bcfb37c2bde86d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037966"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a>Testowanie biblioteki .NET Standard na platformie .NET Core w programie Visual Studio 2017

W obszarze [Kompilowanie biblioteki .NET standard C# z programem i .NET Core w programie Visual Studio 2017](library-with-visual-studio.md) lub [kompilowanie biblioteki .NET Standard z Visual Basic i .net core w programie Visual Studio 2017](vb-library-with-visual-studio.md)utworzono prostą bibliotekę klas, która dodaje metodę rozszerzenia do @no__t_ Klasa 3_. Teraz utworzysz test jednostkowy, aby upewnić się, że działa zgodnie z oczekiwaniami. Należy dodać projekt testu jednostkowego do rozwiązania utworzonego w poprzednim artykule.

## <a name="creating-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Aby utworzyć projekt testu jednostkowego, wykonaj następujące czynności:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. W **Eksplorator rozwiązań**Otwórz menu kontekstowe dla węzła rozwiązania **ClassLibraryProjects** i wybierz polecenie **Dodaj** > **Nowy projekt**.

1. W oknie dialogowym **Dodawanie nowego projektu** wybierz węzeł **wizualizacji C#**  . Następnie wybierz węzeł **.NET Core** , a następnie szablon projektu **projektu testowego MSTest (.NET Core)** . W polu tekstowym **Nazwa** wprowadź wartość "StringLibraryTest" jako nazwę projektu. Wybierz **przycisk OK** , aby utworzyć projekt testu jednostkowego.

   ![Okno dialogowe Dodawanie nowego projektu z wyświetlonym projektem testów jednostkowych —C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > Oprócz projektu testowego MSTest można także użyć programu Visual Studio do utworzenia projektu testowego xUnit dla platformy .NET Core.

1. Program Visual Studio tworzy projekt i otwiera plik *UnitTest1.cs* w oknie kodu.

   ![Okno programu Visual Studio Code dla klasy projektu testów jednostkowych i metody —C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   Kod źródłowy utworzony przez szablon testu jednostkowego wykonuje następujące czynności:

   - Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostkowego.

   - Stosuje atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> do klasy `UnitTest1`. Każda metoda testowa w klasie testowej oznaczona przy użyciu atrybutu \[TestMethod\] jest wykonywana automatycznie, gdy test jednostkowy zostanie uruchomiony.

   - Stosuje atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>, aby zdefiniować `TestMethod1` jako metodę testową automatycznego wykonywania podczas działania testu jednostkowego.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **zależności** projektu **StringLibraryTest** i wybierz polecenie **Dodaj odwołanie** z menu kontekstowego.

   ![Menu kontekstowe zależności StringLibraryTest —C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **projekty** i zaznacz pole wyboru obok pozycji **StringLibrary**. Dodanie odwołania do zestawu `StringLibrary` umożliwia kompilatorowi znalezienie metod **StringLibrary** . Wybierz przycisk **OK** . Spowoduje to dodanie odwołania do projektu biblioteki klas `StringLibrary`.

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

   - Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostkowego.

   - Stosuje atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> do klasy `UnitTest1`. Każda metoda testowa w klasie testowej oznaczona przy użyciu atrybutu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> jest wykonywana automatycznie po uruchomieniu testu jednostkowego.

   - Stosuje atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>, aby zdefiniować `TestMethod1` jako metodę testową automatycznego wykonywania podczas działania testu jednostkowego.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **zależności** projektu **StringLibraryTest** i wybierz polecenie **Dodaj odwołanie** z menu kontekstowego.

   ![Menu kontekstowe zależności StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **projekty** i zaznacz pole wyboru obok pozycji **StringLibrary**. Dodanie odwołania do zestawu `StringLibrary` umożliwia kompilatorowi znalezienie metod **StringLibrary** . Wybierz przycisk **OK** . Spowoduje to dodanie odwołania do projektu biblioteki klas `StringLibrary`.

   ![Okno dialogowe Dodawanie odwołania do projektu w programie Visual Studio — Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)

---

## <a name="adding-and-running-unit-test-methods"></a>Dodawanie i uruchamianie metod testów jednostkowych

Gdy program Visual Studio uruchamia test jednostkowy, wykonuje każdą metodę oznaczoną przy użyciu atrybutu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> w klasie testów jednostkowych, klasy, do której zastosowano atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>. Metoda testowa kończy się w momencie napotkania pierwszego błędu lub gdy wszystkie testy zawarte w metodzie zakończyły się powodzeniem.

Najczęstsze testy są wywoływane przez elementy członkowskie klasy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Wiele metod Assert obejmuje co najmniej dwa parametry, z których jeden jest oczekiwany wynik testu, a drugi jest rzeczywistym wynikiem testu. W poniższej tabeli przedstawiono niektóre z najczęściej wywoływanych metod:

Metody Assert | Funkcja
--- | ---
`Assert.AreEqual` | Sprawdza, czy dwie wartości lub obiekty są równe. Potwierdzenie kończy się niepowodzeniem, jeśli wartości lub obiekty nie są równe.
`Assert.AreSame` | Sprawdza, czy dwie zmienne obiektów odwołują się do tego samego obiektu. Potwierdzenie kończy się niepowodzeniem, jeśli zmienne odwołują się do różnych obiektów.
`Assert.IsFalse` | Sprawdza, czy warunek jest `false`. Potwierdzenie kończy się niepowodzeniem, jeśli warunek jest `true`.
`Assert.IsNotNull` | Sprawdza, czy obiekt nie jest `null`. Potwierdzenie kończy się niepowodzeniem, jeśli obiekt jest `null`.

Można również zastosować atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> do metody testowej. Wskazuje typ wyjątku, który metoda testowa powinna zgłosić. Test zakończy się niepowodzeniem, jeśli określony wyjątek nie zostanie zgłoszony.

W testowaniu metody `StringLibrary.StartsWithUpper`, chcesz podać kilka ciągów zaczynających się od wielkiej litery. Oczekujesz, aby Metoda zwracała `true` w takich przypadkach, aby można było wywołać metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>. Podobnie, chcesz podać kilka ciągów, które zaczynają się od znaku innego niż wielkie litery. Oczekujesz, aby Metoda zwracała `false` w takich przypadkach, aby można było wywołać metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.

Ponieważ metoda biblioteki obsługuje ciągi, należy również upewnić się, że pomyślnie obsługuje [pusty ciąg (`String.Empty`)](xref:System.String.Empty), prawidłowy ciąg, który nie zawiera znaków i którego <xref:System.String.Length> to 0, i `null` ciąg, który nie został zainicjowany. Jeśli `StartsWithUpper` jest wywoływana jako Metoda rozszerzenia w wystąpieniu <xref:System.String>, nie można przesłać ciągu `null`. Można jednak wywołać go bezpośrednio jako metodę statyczną i przekazać pojedynczy argument <xref:System.String>.

Zdefiniujesz trzy metody, z których każdy wywoła metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> dla każdego elementu w tablicy ciągów. Ponieważ metoda testowa nie powiedzie się, gdy wystąpi pierwszy błąd, wywoła Przeciążenie metody, która umożliwia przekazywanie ciągu, który wskazuje wartość ciągu używaną w wywołaniu metody.

Aby utworzyć metody testowe:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. W oknie kod *UnitTest1.cs* Zastąp kod następującym kodem:

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   Należy zauważyć, że test dużych znaków w metodzie `TestStartsWithUpper` obejmuje Wielka litera grecka (U + 0391) i Wielka litera cyrylicy (U + 041C), a test małych znaków w metodzie `TestDoesNotStartWithUpper` obejmuje małą literę alfa (U + 03B1) i mała litera cyrylicy GHE (U + 0433).

1. Na pasku menu wybierz pozycję **plik** > **Zapisz UnitTest1.cs jako**. W oknie dialogowym **Zapisz plik jako** wybierz strzałkę obok przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem**.

   ![Okno dialogowe zapisywania pliku w programie Visual StudioC#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. W oknie kod *UnitTest1. vb* Zastąp kod następującym kodem:

    [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Należy zauważyć, że test dużych znaków w metodzie `TestStartsWithUpper` obejmuje Wielka litera grecka (U + 0391) i Wielka litera cyrylicy (U + 041C), a test małych znaków w metodzie `TestDoesNotStartWithUpper` obejmuje małą literę alfa (U + 03B1) i mała litera cyrylicy GHE (U + 0433).

1. Na pasku menu wybierz pozycję **plik** > **Zapisz UnitTest1. vb jako**. W oknie dialogowym **Zapisz plik jako** wybierz strzałkę obok przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem**.

   ![Okno dialogowe Zapisz plik w programie Visual Studio — Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

---

1. W oknie dialogowym **Potwierdzanie zapisywania jako** wybierz przycisk **tak** , aby zapisać plik.

1. W oknie dialogowym **Zaawansowane opcje zapisywania** wybierz pozycję **Unicode (UTF-8 z podpisem)-strona kodowa 65001** z listy rozwijanej **kodowanie** i wybierz **przycisk OK**.

   ![Zaawansowane opcje zapisywania programu Visual Studio — okno dialogowe](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Jeśli kod źródłowy nie zostanie zapisany jako plik zakodowany w formacie UTF8, program Visual Studio może go zapisać jako plik ASCII. Gdy tak się stanie, środowisko uruchomieniowe nie będzie poprawnie zdekodować znaków UTF8 poza zakresem ASCII, a wyniki testu nie będą dokładne.

1. Na pasku menu wybierz kolejno opcje **testuj** > **Uruchom** > **wszystkie testy**. Zostanie otwarte okno **Eksplorator testów** , które pokazuje, że testy zostały wykonane pomyślnie. Trzy testy są wymienione w sekcji **testy zakończone** , a sekcja **podsumowania** raportuje wynik przebiegu testu.

   ![Okno Eksploratora testów z przekazaniem testów](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a>Obsługa błędów testów

Przebieg testu nie miał błędów, ale nieco zmienia się, tak aby jedna z metod testowych nie powiodła się:

1. Zmodyfikuj tablicę `words` w metodzie `TestDoesNotStartWithUpper`, aby uwzględnić ciąg "Error". Nie musisz zapisywać pliku, ponieważ program Visual Studio automatycznie zapisuje otwarte pliki w przypadku skompilowania rozwiązania do uruchamiania testów.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Uruchom test, wybierając **test** > **Run** > **wszystkie testy** z paska menu. Okno **Eksplorator testów** wskazuje, że dwa testy zostały wykonane pomyślnie i jeden z nich zakończył się niepowodzeniem.

   ![Okno Eksploratora testów z niepowodzeniem testami](./media/testing-library-with-visual-studio/failed-test-window.png)

1. W sekcji **testy zakończone niepowodzeniem** wybierz test zakończony niepowodzeniem, `TestDoesNotStartWith`. W oknie **Eksplorator testów** zostanie wyświetlony komunikat utworzony przez potwierdzenie: "Assert. IsFalse nie powiodło się. Oczekiwano dla elementu "Error": false; rzeczywista: true ". Ze względu na niepowodzenie wszystkie ciągi w tablicy po "Error" nie zostały przetestowane.

   ![Okno Eksploratora testów przedstawiające błąd potwierdzenia jest fałszywy](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Cofnij modyfikację w kroku 1 i usuń ciąg "Error". Ponownie uruchom test i testy zostaną zakończone pomyślnie.

## <a name="testing-the-release-version-of-the-library"></a>Testowanie wersji wydania biblioteki

Uruchomiono testy w odniesieniu do wersji debugowania biblioteki. Teraz, gdy testy zostały zakończone pomyślnie i przetestowano bibliotekę, należy uruchomić testy w dodatkowym czasie w odniesieniu do kompilacji wydania biblioteki. Wiele czynników, w tym Optymalizacja kompilatora, może czasami generować różne zachowanie między kompilacjami w wersji Debug i Release.

Aby przetestować kompilację wydania:

1. Na pasku narzędzi programu Visual Studio Zmień konfigurację kompilacji z **Debuguj** do **Release**.

   ![Pasek narzędzi programu Visual Studio z wyróżnioną kompilacją wydania](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **StringLibrary** i wybierz polecenie **Kompiluj** z menu kontekstowego, aby ponownie skompilować bibliotekę.

   ![Menu kontekstowe StringLibrary z poleceniem Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Uruchom testy jednostkowe, wybierając **Test** > **Run** > **wszystkie testy** z paska menu. Testy zostały zakończone pomyślnie.

Po zakończeniu testowania biblioteki następnym krokiem jest udostępnienie jej do wywoływania. Można powiązać ją z co najmniej jedną lub wieloma aplikacjami lub rozpowszechniać ją jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz [zużywanie biblioteki klas .NET Standard](./consuming-library-with-visual-studio.md).
