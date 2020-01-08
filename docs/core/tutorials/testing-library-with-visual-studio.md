---
title: Testowanie biblioteki klas .NET Standard przy użyciu platformy .NET Core w programie Visual Studio
description: Utwórz projekt testu jednostkowego dla biblioteki klas platformy .NET Core. Sprawdź, czy biblioteka klas .NET Core działa prawidłowo z testami jednostkowymi.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 3a4f25b0d250469102fdac6ee960e42b2d969aed
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559581"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a>Testowanie biblioteki .NET Standard przy użyciu platformy .NET Core w programie Visual Studio

W obszarze [Tworzenie biblioteki .NET standard w programie Visual Studio](library-with-visual-studio.md)utworzono prostą bibliotekę klas, która dodaje metodę rozszerzenia do klasy <xref:System.String>. Teraz utworzysz test jednostkowy, aby upewnić się, że działa zgodnie z oczekiwaniami. Należy dodać projekt testu jednostkowego do rozwiązania utworzonego w poprzednim artykule.

## <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

Aby utworzyć projekt testu jednostkowego, wykonaj następujące czynności:

1. Otwórz rozwiązanie `ClassLibraryProjects` utworzone w [bibliotece kompilacja .NET standard w artykule Visual Studio](library-with-visual-studio.md) .

1. Dodaj nowy projekt testu jednostkowego o nazwie "StringLibraryTest" do rozwiązania.

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **Nowy projekt**.

   1. Na stronie **Dodawanie nowego projektu** wprowadź **MSTest** w polu wyszukiwania. Wybierz **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform. Wybierz szablon **projekt testu MSTest (.NET Core)** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibraryTest** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   > [!NOTE]
   > Oprócz MSTest można także tworzyć projekty testowe xUnit i nUnit dla platformy .NET Core w programie Visual Studio.

1. Program Visual Studio tworzy projekt i otwiera plik klasy w oknie kodu przy użyciu następującego kodu:

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

   - Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostkowego.

   - Stosuje atrybut [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) do klasy `UnitTest1`. Każda metoda testowa w klasie testowej oznaczona przy użyciu atrybutu [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) jest wykonywana automatycznie po uruchomieniu testu jednostkowego.

   - Stosuje atrybut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) , aby zdefiniować `TestMethod1` w C# lub `TestSub` w Visual Basic jako metodę testową do automatycznego wykonania podczas działania testu jednostkowego.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **zależności** projektu **StringLibraryTest** i wybierz polecenie **Dodaj odwołanie** z menu kontekstowego.

   > [!div class="mx-imgBorder"]
   > menu kontekstowe ![zależności StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **projekty** i zaznacz pole wyboru obok pozycji **StringLibrary**. Dodanie odwołania do zestawu `StringLibrary` umożliwia kompilatorowi znalezienie metod **StringLibrary** . Wybierz przycisk **OK**. Odwołanie jest dodawane do projektu biblioteki klas, `StringLibrary`.

   ![Okno dialogowe programu Reference Manager w programie Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a>Dodawanie i uruchamianie metod testów jednostkowych

Gdy program Visual Studio uruchamia test jednostkowy, wykonuje każdą metodę, która jest oznaczona atrybutem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> w klasie testów jednostkowych, klasy, do której zastosowano atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>. Metoda testowa kończy się po znalezieniu pierwszego błędu lub gdy wszystkie testy zawarte w metodzie zakończyły się powodzeniem.

Najczęstsze testy są wywoływane przez elementy członkowskie klasy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Wiele metod Assert obejmuje co najmniej dwa parametry, z których jeden jest oczekiwany wynik testu, a drugi jest rzeczywistym wynikiem testu. W poniższej tabeli przedstawiono niektóre z najczęściej wywoływanych metod klasy `Assert`:

| Metody Assert     | Funkcja |
| ------------------ | -------- |
| `Assert.AreEqual`  | Sprawdza, czy dwie wartości lub obiekty są równe. Potwierdzenie kończy się niepowodzeniem, jeśli wartości lub obiekty nie są równe. |
| `Assert.AreSame`   | Sprawdza, czy dwie zmienne obiektów odwołują się do tego samego obiektu. Potwierdzenie kończy się niepowodzeniem, jeśli zmienne odwołują się do różnych obiektów. |
| `Assert.IsFalse`   | Sprawdza, czy warunek jest `false`. Potwierdzenie kończy się niepowodzeniem, jeśli warunek jest `true`. |
| `Assert.IsNotNull` | Sprawdza, czy obiekt nie jest `null`. Potwierdzenie kończy się niepowodzeniem, jeśli obiekt jest `null`. |

Można również użyć metody <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> w metodzie testowej, aby wskazać typ wyjątku, który ma zostać zgłoszony. Test zakończy się niepowodzeniem, jeśli określony wyjątek nie zostanie zgłoszony.

W testowaniu metody `StringLibrary.StartsWithUpper`, chcesz podać kilka ciągów zaczynających się od wielkiej litery. Oczekujesz, aby Metoda zwracała `true` w takich przypadkach, aby można było wywołać metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>. Podobnie, chcesz podać kilka ciągów, które zaczynają się od znaku innego niż wielkie litery. Oczekujesz, aby Metoda zwracała `false` w takich przypadkach, aby można było wywołać metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.

Ponieważ metoda biblioteki obsługuje ciągi, należy również upewnić się, że pomyślnie obsługuje [pusty ciąg (`String.Empty`)](xref:System.String.Empty), prawidłowy ciąg, który nie zawiera znaków i którego <xref:System.String.Length> to 0, i `null` ciąg, który nie został zainicjowany. Jeśli `StartsWithUpper` jest wywoływana jako Metoda rozszerzenia w wystąpieniu <xref:System.String>, nie można przesłać ciągu `null`. Można jednak wywołać go bezpośrednio jako metodę statyczną i przekazać pojedynczy argument <xref:System.String>.

Zdefiniujesz trzy metody, z których każda wywołuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodę wielokrotnie dla każdego elementu w tablicy ciągów. Ponieważ metoda testowa nie powiedzie się po znalezieniu pierwszego błędu, wywoła Przeciążenie metody, które umożliwia przekazywanie ciągu, który wskazuje wartość ciągu używaną w wywołaniu metody.

Aby utworzyć metody testowe:

1. W oknie kod *UnitTest1.cs* lub *UnitTest1. vb* Zastąp kod następującym kodem:

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   Test wielkiej litery w metodzie `TestStartsWithUpper` obejmuje wielką literę alfa (U + 0391) i wielką literę cyrylicy (U + 041C). Test małymi literami w metodzie `TestDoesNotStartWithUpper` obejmuje małą literę alfa (U + 03B1) i małą literę cyrylicy GHE (U + 0433).

1. Na pasku menu wybierz pozycję **plik** > **Zapisz UnitTest1.cs jako** lub **plik** > **Zapisz UnitTest1. vb jako**. W oknie dialogowym **Zapisz plik jako** wybierz strzałkę obok przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem**.

   > [!div class="mx-imgBorder"]
   > ![okna dialogowego zapisywania pliku w programie Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)

1. W oknie dialogowym **Potwierdzanie zapisywania jako** wybierz przycisk **tak** , aby zapisać plik.

1. W oknie dialogowym **Zaawansowane opcje zapisywania** wybierz pozycję **Unicode (UTF-8 z podpisem)-strona kodowa 65001** z listy rozwijanej **kodowanie** i wybierz **przycisk OK**.

   > [!div class="mx-imgBorder"]
   > ![okno dialogowe Zaawansowane opcje zapisywania programu Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)

   Jeśli kod źródłowy nie zostanie zapisany jako plik zakodowany w formacie UTF8, program Visual Studio może go zapisać jako plik ASCII. Gdy tak się stanie, środowisko uruchomieniowe nie dekoduje znaków UTF8 poza zakresem ASCII, a wyniki testu nie będą poprawne.

1. Na pasku menu wybierz kolejno opcje **testuj** > **Uruchom** > **wszystkie testy**. Zostanie otwarte okno **Eksplorator testów** , które pokazuje, że testy zostały wykonane pomyślnie. Trzy testy są wymienione w sekcji **testy zakończone** , a sekcja **podsumowania** raportuje wynik przebiegu testu.

   > [!div class="mx-imgBorder"]
   > ![okno Eksploratora testów z przekazaniem testów](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handle-test-failures"></a>Obsługa niepowodzeń testów

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

   > [!div class="mx-imgBorder"]
   > ![okno Eksploratora testów z testami zakończonymi niepowodzeniem](./media/testing-library-with-visual-studio/failed-test-window.png)

1. Wybierz test zakończony niepowodzeniem, `TestDoesNotStartWith`. W oknie **Eksplorator testów** zostanie wyświetlony komunikat utworzony przez potwierdzenie: "Assert. IsFalse nie powiodło się. Oczekiwano dla elementu "Error": false; rzeczywista: true ". Z powodu błędu nie przetestowano wszystkich ciągów w tablicy po "błędzie".

   > [!div class="mx-imgBorder"]
   > ![okno Eksploratora testów przedstawiające błąd potwierdzenia IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. Cofnij modyfikację w kroku 1 i usuń ciąg "Error". Ponownie uruchom test i testy zostaną zakończone pomyślnie.

## <a name="test-the-release-version-of-the-library"></a>Testowanie wersji wydania biblioteki

Uruchomiono testy w odniesieniu do wersji debugowania biblioteki. Teraz, gdy testy zostały zakończone pomyślnie i przetestowano bibliotekę, należy uruchomić testy w dodatkowym czasie w odniesieniu do kompilacji wydania biblioteki. Wiele czynników, w tym Optymalizacja kompilatora, może czasami generować różne zachowanie między kompilacjami w wersji Debug i Release.

Aby przetestować kompilację wydania:

1. Na pasku narzędzi programu Visual Studio Zmień konfigurację kompilacji z **Debuguj** do **Release**.

   > [!div class="mx-imgBorder"]
   > ![pasku narzędzi programu Visual Studio z wyróżnioną kompilacją wydania](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **StringLibrary** i wybierz polecenie **Kompiluj** z menu kontekstowego, aby ponownie skompilować bibliotekę.

   > [!div class="mx-imgBorder"]
   > ![menu kontekstowe StringLibrary z poleceniem kompilacji](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. Uruchom testy jednostkowe, wybierając **Test** > **Run** > **wszystkie testy** z paska menu. Testy zostały zakończone pomyślnie.

Po zakończeniu testowania biblioteki następnym krokiem jest udostępnienie jej do wywoływania. Można powiązać ją z co najmniej jedną lub wieloma aplikacjami lub rozpowszechniać ją jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz [zużywanie biblioteki klas .NET Standard](consuming-library-with-visual-studio.md).

## <a name="see-also"></a>Zobacz także

- [Podstawowe informacje o teście jednostkowym — Visual Studio](/visualstudio/test/unit-test-basics)
