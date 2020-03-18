---
title: Testowanie biblioteki klas .NET Standard z .NET Core w programie Visual Studio
description: Utwórz projekt testu jednostkowego dla biblioteki klas .NET Core. Sprawdź, czy biblioteka klas .NET Core działa poprawnie z testami jednostkowym.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156624"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>Testowanie biblioteki standardu .NET z .NET Core w programie Visual Studio

W [tworzenie biblioteki .NET Standard w programie Visual Studio](library-with-visual-studio.md)utworzono prostą <xref:System.String> bibliotekę klas, która dodaje metodę rozszerzenia do klasy. Teraz utworzysz test jednostkowy, aby upewnić się, że działa zgodnie z oczekiwaniami. Dodasz projekt testu jednostkowego do rozwiązania utworzonego w poprzednim artykule.

## <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Aby utworzyć projekt testu jednostkowego, wykonaj następujące czynności:

1. Otwórz `ClassLibraryProjects` rozwiązanie utworzone w artykule [Tworzenie biblioteki standardu .NET w](library-with-visual-studio.md) programie Visual Studio.

1. Dodaj nowy projekt testu jednostkowego o nazwie "StringLibraryTest" do rozwiązania.

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz **polecenie Dodaj** > **nowy projekt**.

   1. Na stronie **Dodaj nowy projekt** wprowadź **mstest** w polu wyszukiwania. Wybierz **c#** lub **Visual Basic** z listy Język, a następnie wybierz pozycję Wszystkie **platformy** z listy Platforma. Wybierz szablon **Projektu testowego Programu MsTest (.NET Core),** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Konfigurowanie nowego projektu** wprowadź **ciąg StringLibraryTest** w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   > [!NOTE]
   > Oprócz mstest, można również utworzyć xUnit i nUnit projektów testowych dla .NET Core w programie Visual Studio.

1. Program Visual Studio tworzy projekt i otwiera plik klasy w oknie kodu z następującym kodem:

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace StringLibraryTest
    {
        [TestClass]
        public class UnitTest1
        {
            [TestMethod]
            public void TestMethod1()
            {
            }
        }
    }
    ```

    ```vb
    Imports Microsoft.VisualStudio.TestTools.UnitTesting

    Namespace StringLibraryTest
        <TestClass>
        Public Class UnitTest1
            <TestMethod>
            Sub TestSub()

            End Sub
        End Class
    End Namespace
    ```

   Kod źródłowy utworzony przez szablon testu jednostkowego wykonuje następujące czynności:

   - Importuje obszar <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> nazw, który zawiera typy używane do testowania jednostkowego.

   - Stosuje [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) atrybut do `UnitTest1` klasy. Każda metoda testowa w klasie testowej oznaczona atrybutem [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) jest wykonywana automatycznie po uruchomieniu testu jednostkowego.

   - Stosuje [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) atrybut do `TestMethod1` definiowania `TestSub` w języku C# lub w języku Visual Basic jako metoda testowa do automatycznego wykonywania po uruchomieniu testu jednostkowego.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Zależności** projektu **StringLibraryTest** i wybierz polecenie **Dodaj odwołanie** z menu kontekstowego.

   > [!div class="mx-imgBorder"]
   > ![Menu kontekstowe zależności StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **Projekty** i zaznacz pole wyboru obok **pozycji StringLibrary**. Dodanie odwołania do `StringLibrary` zestawu umożliwia kompilatorowi znajdowanie metod **StringLibrary.** Wybierz przycisk **OK**. Odwołanie zostanie dodane do projektu `StringLibrary`biblioteki klas.

   ![Okno dialogowe Menedżera odwołań w programie Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>Dodawanie i uruchamianie metod testowania jednostkowego

Gdy program Visual Studio uruchamia test jednostkowy, wykonuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> każdą metodę, która jest oznaczona atrybutem w klasie testu jednostkowego, klasy, do której jest stosowany <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybut. Metoda testowa kończy się, gdy zostanie znaleziony pierwszy błąd lub gdy wszystkie testy zawarte w metodzie zakończyły się pomyślnie.

Najczęstsze testy wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> członków klasy. Wiele metod potwierdzenia obejmują co najmniej dwa parametry, z których jeden jest oczekiwany wynik testu, a drugi jest rzeczywisty wynik testu. Niektóre z `Assert` najczęściej wywoływanych metod klasy przedstawiono w poniższej tabeli:

| Metody potwierdzania     | Funkcja |
| ------------------ | -------- |
| `Assert.AreEqual`  | Sprawdza, czy dwie wartości lub obiekty są równe. Assert nie powiedzie się, jeśli wartości lub obiekty nie są równe. |
| `Assert.AreSame`   | Sprawdza, czy dwie zmienne obiektu odnoszą się do tego samego obiektu. Assert nie powiedzie się, jeśli zmienne odnoszą się do różnych obiektów. |
| `Assert.IsFalse`   | Sprawdza, czy warunek `false`jest . Potwierdzenie nie powiedzie `true`się, jeśli warunek jest . |
| `Assert.IsNotNull` | Sprawdza, czy obiekt nie `null`jest . Assert nie powiedzie `null`się, jeśli obiekt jest . |

Można również użyć <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> metody w metodzie testowej, aby wskazać typ wyjątku, który ma zostać zgłoszony. Test nie powiedzie się, jeśli określony wyjątek nie jest generowany.

Podczas testowania `StringLibrary.StartsWithUpper` metody chcesz podać liczbę ciągów, które zaczynają się wielkimi literami. Można oczekiwać, `true` że metoda do zwrócenia <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> w tych przypadkach, dzięki czemu można wywołać metodę. Podobnie chcesz podać szereg ciągów, które zaczynają się od czegoś innego niż wielkie litery. Można oczekiwać, `false` że metoda do zwrócenia <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> w tych przypadkach, dzięki czemu można wywołać metodę.

Ponieważ metoda biblioteki obsługuje ciągi, należy również upewnić się, że pomyślnie obsługuje [pusty ciąg (`String.Empty`)](xref:System.String.Empty), prawidłowy ciąg, który nie ma znaków i którego <xref:System.String.Length> jest 0, oraz `null` ciąg, który nie został zainicjowany. Jeśli `StartsWithUpper` jest wywoływana jako <xref:System.String> metoda rozszerzenia w wystąpieniu, `null` nie można przekazać ciąg. Można jednak również wywołać go bezpośrednio jako metodę <xref:System.String> statyczną i przekazać pojedynczy argument.

Zdefiniujesz trzy metody, z których <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> każda wywołuje metodę wielokrotnie dla każdego elementu w tablicy ciągów. Ponieważ metoda testowa kończy się niepowodzeniem, gdy tylko znajdzie pierwszy błąd, wywołasz przeciążenie metody, które umożliwia przekazanie ciągu, który wskazuje wartość ciągu używanew wywołaniu metody.

Aby utworzyć metody testowe:

1. W oknie kodu *UnitTest1.cs* lub *UnitTest1.vb* zastąp kod następującym kodem:

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Test wielkich liter w `TestStartsWithUpper` metodzie obejmuje grecką literę alfa (U+0391) i literę cyrylicy EM (U+041C). Test małych liter w `TestDoesNotStartWithUpper` metodzie obejmuje grecką małą literę alfa (U +03B1) i cyrylica małą literę Ghe (U +0433).

1. Na pasku menu wybierz pozycję**Zapisz UnitTest1.cs jako** **pliku** > lub **Zapisz plik** > **UnitTest1.vb Jako**. W oknie dialogowym **Zapisywanie pliku jako** zaznacz strzałkę obok przycisku **Zapisz** i wybierz pozycję Zapisz za **pomocą kodowania**.

   > [!div class="mx-imgBorder"]
   > ![Okno dialogowe Zapisywanie pliku w programie Visual Studio jako](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. W oknie dialogowym **Potwierdzanie zapisywania jako** wybierz przycisk **Tak,** aby zapisać plik.

1. W oknie dialogowym **Zaawansowane opcje zapisywania** wybierz pozycję **Unicode (UTF-8 z podpisem) — strona kodowa 65001** z listy rozwijanej **Kodowanie** i wybierz przycisk **OK**.

   > [!div class="mx-imgBorder"]
   > ![Okno dialogowe Zaawansowane opcje zapisywania programu Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Jeśli nie uda się zapisać kodu źródłowego jako pliku zakodowanego w utf8, program Visual Studio może zapisać go jako plik ASCII. W takim przypadku program runtime nie dokładnie dekoduje znaki UTF8 poza zakresem ASCII, a wyniki testu nie będą poprawne.

1. Na pasku menu wybierz **opcję Uruchom** > **testuj** > **wszystkie testy**. Okno **Eksploratora testów** zostanie otwarte i pokaże, że testy zostały pomyślnie przeprowadzone. Trzy testy są wymienione w **sekcji Zdany testy,** a sekcja **Podsumowanie** zgłasza wynik przebiegu testu.

   > [!div class="mx-imgBorder"]
   > ![Okno Eksploratora testów z testami zaliczenia](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Obsługa błędów testów

Przebieg testowy nie miał żadnych błędów, ale zmień go nieznacznie, aby jedna z metod testowych nie powiodła się:

1. Zmodyfikuj tablicę `words` w metodzie, `TestDoesNotStartWithUpper` aby uwzględnić ciąg "Błąd". Nie trzeba zapisywać pliku, ponieważ program Visual Studio automatycznie zapisuje otwarte pliki, gdy rozwiązanie jest zbudowane do uruchamiania testów.

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. Uruchom test, wybierając **opcję Uruchom test** > **Run** > **wszystkie testy** z paska menu. Okno **Eksploratora testów** wskazuje, że dwa testy zakończyły się pomyślnie, a jeden zakończył się niepowodzeniem.

   > [!div class="mx-imgBorder"]
   > ![Okno Eksploratora testów z nieudanym testem](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Wybierz nieudany `TestDoesNotStartWith`test . W oknie **Eksploratora testów** jest wyświetlany komunikat wyprodukowany przez assert: "Assert.IsFalse nie powiodło się. Oczekiwano dla "Błąd": false; rzeczywiste: Prawda". Z powodu awarii wszystkie ciągi w tablicy po "Błąd" nie zostały przetestowane.

   > [!div class="mx-imgBorder"]
   > ![Okno Eksploratora testów z błędem potwierdzenia IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Cofnij modyfikację, którą wykonałeś w kroku 1 i usuń ciąg "Błąd". Uruchom ponownie test, a testy przejdą.

## <a name="test-the-release-version-of-the-library"></a>Testowanie wersji biblioteki

Zostały uruchomione testy przeciwko debugwersji biblioteki. Teraz, gdy wszystkie testy zostały zadane i zostały odpowiednio przetestowane biblioteki, należy uruchomić testy dodatkowy czas przed release kompilacji biblioteki. Wiele czynników, w tym optymalizacji kompilatora, czasami może powodować różne zachowanie między kompilacjami debugowania i wydania.

Aby przetestować kompilację wersji:

1. Na pasku narzędzi programu Visual Studio zmień konfigurację kompilacji z **Debug** na **Release**.

   > [!div class="mx-imgBorder"]
   > ![Pasek narzędzi programu Visual Studio z wyróżnioną kompilacją wersji](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **StringLibrary** i wybierz polecenie **Kompilacja** z menu kontekstowego, aby ponownie skompilować bibliotekę.

   > [!div class="mx-imgBorder"]
   > ![Menu kontekstowe StringLibrary z poleceniem kompilacji](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Uruchom testy jednostkowe, wybierając z paska menu opcję **Uruchom próbę** > **Run** > **wszystkie testy.** Testy zaprzechodzą.

Po zakończeniu testowania biblioteki następnym krokiem jest udostępnienie jej wywołującym. Można połączyć go z jedną lub więcej aplikacji lub można rozpowszechniać go jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz [Korzystanie ze standardowej biblioteki klas .NET](consuming-library-with-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Podstawowe informacje o testach jednostkowych — Visual Studio](/visualstudio/test/unit-test-basics)
