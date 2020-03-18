---
title: Tworzenie kompletnego rozwiązania .NET Core przy użyciu programu Visual Studio dla komputerów Mac
description: W tym artykule przedstawiono tworzenie rozwiązania .NET Core, które zawiera bibliotekę wielokrotnego użytku i testowanie jednostek.
ms.date: 12/19/2019
ms.openlocfilehash: 8c9fcca404a3875b6bb7f9cf20551a017ff553c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239966"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne zintegrowane środowisko programistyczne (IDE) do tworzenia aplikacji .NET Core. W tym artykule przedstawiono tworzenie rozwiązania .NET Core, które zawiera bibliotekę wielokrotnego użytku i testowanie jednostek.

W tym samouczku pokazano, jak utworzyć aplikację, która akceptuje wyszukiwane słowo i ciąg tekstu od użytkownika, zlicza, ile razy szukane słowo pojawia się w ciągu przy użyciu metody w bibliotece klas i zwraca wynik do użytkownika. Rozwiązanie obejmuje również testowanie jednostkowe dla biblioteki klas jako wprowadzenie do koncepcji testowania jednostek. Jeśli wolisz przejść przez samouczek z pełną próbką, pobierz [przykładowe rozwiązanie](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Twoja opinia jest wysoko ceniona. Istnieją dwa sposoby przekazywania informacji zwrotnych do zespołu programistów w programie Visual Studio dla komputerów Mac:
>
> - W programie Visual Studio dla komputerów Mac wybierz pozycję > **Zgłoś problem** z menu lub **Zgłoś problem** na ekranie powitalnym, który otwiera okno do zgłaszania błędów. **Help** Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Aby przedstawić sugestię, wybierz **pozycję Pomóż** > **udostępnij sugestię** z menu lub **Udostępnij sugestię** z ekranu powitalnego, który przeniesie Cię do [strony sieci Web Społeczności programistów programu Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Wymagania wstępne

- [.NET Core SDK 3.1 lub nowszy](https://dotnet.microsoft.com/download)
- [Visual Studio 2019 dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Aby uzyskać więcej informacji na temat wymagań wstępnych, zobacz [zależności i wymagania .NET Core](../install/dependencies.md?pivots=os-macos). Aby zapoznać się z pełnymi wymaganiami systemowymi programu Visual Studio 2019 dla komputerów Mac, zobacz [Visual Studio 2019 for Mac Product Family Wymagania systemowe](/visualstudio/productinfo/vs2019-system-requirements-mac).

## <a name="building-a-library"></a>Tworzenie biblioteki

1. W oknie startowym wybierz pozycję **Nowy projekt**. W oknie dialogowym **Nowy projekt** w węźle **.NET Core** wybierz szablon **standardowej biblioteki .NET.** To polecenie tworzy bibliotekę standardu .NET, która jest przeznaczona dla programu .NET Core, a także dowolną inną implementację .NET obsługującej wersję 2.1 [standardu .NET .](../../standard/net-standard.md) Jeśli masz zainstalowane wiele wersji sdk .NET Core, możesz wybrać różne wersje programu .NET Standard dla swojej biblioteki. Wybierz ".NET Standard 2.1" i wybierz **przycisk Dalej**.

   > [!div class="mx-imgBorder"]
   > ![Okno dialogowe Programu Visual Studio dla komputerów Mac Nowy projekt](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Nazwij projekt "TextUtils" (krótka nazwa "Narzędzia tekstowe") i rozwiązanie "WordCounter". Pozostaw **Utwórz katalog projektu w zaznaczonym katalogu rozwiązania.** Wybierz **pozycję Utwórz**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac Nowe opcje okna dialogowego projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. W konsoli **rozwiązania** rozwiń `TextUtils` węzeł, aby odsłonić plik klasy dostarczony przez szablon, *Class1.cs*. Ctrl kliknij plik, wybierz **polecenie Zmień nazwę** z menu kontekstowego i zmień nazwę pliku na *WordCount.cs*. Otwórz plik i zastąp zawartość następującym kodem:

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/TextUtils/WordCount.cs)]

1. Zapisz plik przy użyciu dowolnej z trzech różnych metod: użyj skrótu klawiaturowego <kbd>&#8984;</kbd> + <kbd>s</kbd>, wybierz **polecenie Zapisz plik** > **Save** z menu lub kliknij z wciśniętym klawiszem ctrl na karcie pliku i wybierz **pozycję Zapisz** z menu kontekstowego. Na poniższej ilustracji przedstawiono okno IDE:

   > [!div class="mx-imgBorder"]
   > ![Okno IDE programu Visual Studio dla komputerów Mac z plikiem i metodą biblioteki klas](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. Wybierz **pozycję Błędy** na marginesie u dołu okna IDE, aby otworzyć panel **Błędy.** Wybierz przycisk **Zbuduj wyjście.**

   > [!div class="mx-imgBorder"]
   > ![Dolny margines ide programu Visual Studio Mac z przyciskiem Błędy](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Z menu **wybierz polecenie Zbuduj** > **wszystko.**

   Rozwiązanie tworzy. Panel danych wyjściowych kompilacji pokazuje, że kompilacja zakończyła się pomyślnie.

   > [!div class="mx-imgBorder"]
   > ![Panel wyjściowy kompilacji programu Visual Studio Mac panelu Błędy z komunikatem Kompilacja zakończy się pomyślnie](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Tworzenie projektu testowego

Testy jednostkowe zapewniają automatyczne testowanie oprogramowania podczas tworzenia i publikowania. Struktura testowania, której używasz w tym samouczku jest [xUnit (wersja 2.4.0 lub nowszej),](https://xunit.github.io/)który jest instalowany automatycznie po dodaniu projektu testu xUnit do rozwiązania w następujących krokach:

1. Na pasku bocznym **rozwiązania** kliknij klawisz `WordCounter` ctrl z wciśniętym klawiszem ctrl i wybierz pozycję **Dodaj** > **nowy projekt**.

1. W oknie dialogowym **Nowy projekt** wybierz **pozycję Testy** z węzła **.NET Core.** Wybierz **projekt testu xUnit,** po którym następuje **następny**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Mac Nowy projekt okno dialogowe tworzenie projektu testowego xUnit](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Jeśli masz wiele wersji sdk .NET Core, musisz wybrać wersję dla tego projektu. Wybierz **.NET Core 3.1**. Nazwij nowy projekt "TestLibrary" i wybierz **pozycję Utwórz**.

   > [!div class="mx-imgBorder"]
   > ![Okno dialogowe Visual Studio Mac New Project zawierające nazwę projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Aby biblioteka testów działała `WordCount` z klasą, dodaj `TextUtils` odwołanie do projektu. Na pasku bocznym **rozwiązania** kliknij klawisz **ctrl-click Zależności w** obszarze **Biblioteka testowa**. Z menu kontekstowego **wybierz polecenie Edytowanie odwołań.**

1. W oknie dialogowym **Edytowanie odwołań** wybierz projekt **TextUtils** na karcie **Projekty.** **OK**

   > [!div class="mx-imgBorder"]
   > ![Okno dialogowe Edytowanie odwołań dla komputerów Mac w programie Visual Studio Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. W projekcie **TestLibrary** zmień nazwę pliku *UnitTest1.cs* na *TextUtilsTests.cs*.

1. Otwórz plik i zastąp kod następującym kodem:

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");

               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   Na poniższej ilustracji przedstawiono IDE z kodem testu jednostkowego w miejscu. Zwróć uwagę `Assert.NotEqual` na oświadczenie.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac Początkowy test jednostkowy w oknie głównym IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Ważne jest, aby nowy test nie powiedzie się raz, aby potwierdzić jego logiki testowania jest poprawna. Metoda przechodzi w nazwie "Jack" (wielkie litery) i ciąg z "Jack" i "jack" (wielkie i małe litery). Jeśli `GetWordCount` metoda działa poprawnie, zwraca liczbę dwóch wystąpień szukanego słowa. Aby zakończyć ten test celowo, należy najpierw zaimplementować test, twierdząc, że dwa wystąpienia szukanego `GetWordCount` słowa "Jack" nie są zwracane przez metodę. Przejdź do następnego kroku, aby zakończyć test celowo.

1. Otwórz panel **Testy jednostkowe** po prawej stronie ekranu. Z menu **wybierz polecenie Wyświetl** > **testy.**

   > [!div class="mx-imgBorder"]
   > ![Panel Visual Studio testów jednostkowych dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Kliknij ikonę **Dock,** aby panel był otwarty. (Wyróżniony na poniższej ilustracji).

   > [!div class="mx-imgBorder"]
   > ![Ikona doki panelu Testy jednostkowe programu Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Kliknij przycisk **Uruchom wszystko.**

   Test kończy się niepowodzeniem, co jest poprawny wynik. Metoda testowa potwierdza, że dwa `inputString`wystąpienia " Jack " nie są zwracane z ciągu `GetWordCount` "Jack jack" dostarczone do metody. Ponieważ obudowa wyrazów została `GetWordCount` uwzględniona w metodzie, zwracane są dwa wystąpienia. Twierdzenie, że 2 *nie jest równa* 2 nie powiedzie się. Ten wynik jest prawidłowywynik, a logika naszego testu jest dobra.

   > [!div class="mx-imgBorder"]
   > ![Wyświetlanie niepowodzeń testu programu Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Zmodyfikuj `IgnoreCasing` `Assert.NotEqual` metodę `Assert.Equal`badania, zmieniając ją na . Zapisz plik za pomocą skrótu klawiaturowego <kbd>Ctrl</kbd>+<kbd>s</kbd>, **Zapisz plik** > **Save** z menu lub klikając klawisz ctrl na karcie pliku i wybierając **zapisz** z menu kontekstowego.

   Można oczekiwać, że `searchWord` "Jack" `inputString` zwraca dwa wystąpienia `GetWordCount`z "Jack jack" przekazany do . Uruchom test ponownie, klikając przycisk **Uruchom testy** w panelu **Testy jednostkowe** lub przycisk **Uruchom ponownie testy** w panelu **Wyniki testów** u dołu ekranu. Test przebiega pomyślnie. Istnieją dwa wystąpienia "Jack" w ciągu "Jack jack" (ignorując obudowy), `true`a twierdzenie testu jest .

   > [!div class="mx-imgBorder"]
   > ![Wyświetlanie zaprzekazu testów programu Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Testowanie poszczególnych wartości `Fact` zwracanych za pomocą a to dopiero początek tego, co można zrobić z testami jednostkowymi. Inna potężna technika pozwala przetestować `Theory`kilka wartości naraz za pomocą . Dodaj następującą `TextUtils_GetWordCountShould` metodę do swojej klasy. Po dodaniu tej metody w klasie istnieją dwie metody:

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count,
                                       string searchWord,
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   Sprawdza, `CountInstancesCorrectly` czy `GetWordCount` metoda jest poprawnie zliczana. Zapewnia `InlineData` liczbę, słowo wyszukiwania i ciąg wejściowy do sprawdzenia. Metoda testowa jest uruchamiana raz dla każdego wiersza danych. Należy zauważyć po raz kolejny, że potwierdzasz błąd najpierw za pomocą `Assert.NotEqual`, nawet jeśli wiesz, że liczby `GetWordCount` w danych są poprawne i że wartości są zgodne z liczbami zwracanymi przez metodę. Wykonanie kroku niepowodzenia testu celowo może wydawać się stratą czasu na początku, ale sprawdzanie logiki testu przez niepowodzenie jest najpierw ważnym sprawdzeniem logiki testów. Po natknąć się na metodę testową, która przechodzi, gdy można oczekiwać, że nie powiedzie się, znalazłeś błąd w logice testu. Warto postarać się o ten krok za każdym razem, gdy tworzysz metodę testową.

1. Zapisz plik i ponownie uruchom testy. Test obudowy przebiega pomyślnie, ale trzy testy zliczania nie powiodą się. Ten wynik jest dokładnie tym, czego się spodziewasz.

   > [!div class="mx-imgBorder"]
   > ![Oczekiwany błąd testu programu Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Zmodyfikuj `CountInstancesCorrectly` `Assert.NotEqual` metodę `Assert.Equal`badania, zmieniając ją na . Zapisz plik. Uruchom ponownie testy. Wszystkie testy zaprzechodzą.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac oczekiwany test przebiega](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Dodawanie aplikacji konsoli

1. Na pasku bocznym **rozwiązania** kliknij z `WordCounter` wciśniętym klawiszem ctrl rozwiązanie. Dodaj nowy projekt **aplikacji konsoli,** wybierając szablon z szablonów**aplikacji** **.NET Core.** >  Wybierz **pozycję Dalej**. Nazwij projekt **WordCounterApp**. Wybierz **pozycję Utwórz,** aby utworzyć projekt w rozwiązaniu.

1. Na pasku bocznym **Rozwiązania** kliknij ctrl-kliknij węzeł **Zależności** nowego projektu **WordCounterApp.** W oknie dialogowym **Edytowanie odwołań** zaznacz pole wyboru **TextUtils** i wybierz przycisk **OK**.

1. Otwórz plik *Program.cs.* Zastąp kod następującym kodem:

   [!code-csharp[Main](../../../samples/snippets/core/tutorials/using-on-mac-vs-full-solution/csharp/WordCounterApp/Program.cs)]

1. Ctrl kliknij na `WordCounterApp` projekt i wybierz **uruchom projekt** z menu kontekstowego. Po uruchomieniu aplikacji podaj wartości wyszukiwanego wyrazu i ciągu wejściowego w monitach w oknie konsoli. Aplikacja wskazuje, ile razy w ciągu pojawia się szukany wyraz.

   > [!div class="mx-imgBorder"]
   > ![Okno konsoli Visual Studio dla komputerów Mac z uruchomioną aplikacją](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Ostatnią funkcją do eksplorowania jest debugowanie za pomocą programu Visual Studio dla komputerów Mac. Ustaw punkt przerwania `Console.WriteLine` na instrukcji: Wybierz na lewym marginesie wiersza 23, a obok wiersza kodu pojawi się czerwone kółko. Możesz też wybrać dowolne miejsce w wierszu kodu i wybrać z menu pozycję **Uruchom** > **punkt przerwania.**

   > [!div class="mx-imgBorder"]
   > ![Zestaw punktów przerwania programu Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. ctrl-kliknij `WordCounterApp` projekt. Z menu kontekstowego wybierz **polecenie Rozpocznij debugowanie projektu.** Gdy aplikacja działa, wprowadź szukaj słowa "kot" i "Pies gonił kota, ale kot uciekł." dla ciągu do wyszukiwania. Po `Console.WriteLine` osiągnięciu instrukcji wykonanie programu zostanie zatrzymane przed wykonaniem instrukcji. Na karcie **Miejscowi** można zobaczyć `searchWord` `inputString`, `wordCount`, `pluralChar` i wartości.

   > [!div class="mx-imgBorder"]
   > ![Wykonanie programu Debuger programu Visual Studio dla komputerów Mac ustało](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. W okienku **Natychmiastowe wpisz** "wordCount = 999;" i naciśnij klawisz Enter. To polecenie przypisuje wartość nonsens 999 do zmiennej `wordCount` pokazującej, że można zastąpić wartości zmiennych podczas debugowania.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac zmienia wartości w oknie bezpośrednim](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Na pasku narzędzi kliknij strzałkę *kontynuuj.* Spójrz na dane wyjściowe w oknie konsoli. Raportuje niepoprawną wartość 999, która została ustawiona podczas debugowania aplikacji.

   > [!div class="mx-imgBorder"]
   > ![Przycisk Kontynuuj program Visual Studio dla komputerów Mac na pasku narzędzi](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   > [!div class="mx-imgBorder"]
   > ![Wyjście okna konsoli Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

Ten sam proces służy do debugowania kodu przy użyciu projektu testu jednostkowego. Zamiast rozpoczynać projekt aplikacji WordCount, kliknij ctrl projekt **biblioteki testowej** i wybierz **polecenie Rozpocznij debugowanie projektu** z menu kontekstowego. Visual Studio dla komputerów Mac rozpoczyna projekt testowy z dołączonym debugerem. Wykonanie zatrzyma się w dowolnym punkcie przerwania dodanym do projektu testowego lub podstawowym kodzie biblioteki.

## <a name="see-also"></a>Zobacz też

- [Visual Studio 2019 dla komputerów Mac — Informacje o wersji](/visualstudio/releasenotes/vs2019-mac-relnotes)
