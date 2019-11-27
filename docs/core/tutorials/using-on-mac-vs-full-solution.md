---
title: Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac
description: W tym temacie omówiono tworzenie rozwiązania .NET Core, które obejmuje biblioteki wielokrotnego użytku i testy jednostkowe.
author: mairaw
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: 0081463c0a99acc5cb4e02bb96e2218bbcf61131
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428629"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne zintegrowane środowisko programistyczne (IDE) do tworzenia aplikacji platformy .NET Core. W tym temacie omówiono tworzenie rozwiązania .NET Core, które obejmuje biblioteki wielokrotnego użytku i testy jednostkowe.

W tym samouczku pokazano, jak utworzyć aplikację, która akceptuje słowo wyszukiwania i ciąg tekstu od użytkownika, zlicza, ile razy słowo wyszukiwania pojawia się w ciągu przy użyciu metody w bibliotece klas i zwraca wynik do użytkownika. Rozwiązanie obejmuje również testy jednostkowe dla biblioteki klas jako wprowadzenie do koncepcji testowania jednostkowego. Jeśli wolisz przejść przez samouczek z kompletnym przykładem, Pobierz [przykładowe rozwiązanie](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Opinie są wysoce wyceniane. Istnieją dwa sposoby przekazywania opinii zespołowi programistycznemu na Visual Studio dla komputerów Mac:
>
> - W Visual Studio dla komputerów Mac wybierz pozycję **Pomoc** , > **zgłosić problem** z menu lub **Zgłoś problem** na ekranie powitalnym, co spowoduje otwarcie okna umożliwiającego zgłoszenie usterki. Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Aby utworzyć sugestię, wybierz pozycję **pomoc** > **Podaj sugestię** z menu lub **Podaj sugestię** z ekranu powitalnego, który przeprowadzi cię do [witryny internetowej społeczności deweloperów Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Wymagania wstępne

- OpenSSL (w przypadku uruchamiania programu .NET Core 1,1): zobacz temat [zależności i wymagania dotyczące platformy .NET Core](../install/dependencies.md?tabs=netcore30&pivots=os-macos) .
- [Zestaw .NET Core SDK 1,1 lub nowszy](https://dotnet.microsoft.com/download)
- [Program Visual Studio 2017 dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Aby uzyskać więcej informacji na temat wymagań wstępnych, zobacz [zależności i wymagania dotyczące platformy .NET Core](../install/dependencies.md?tabs=netcore30&pivots=os-macos). Aby uzyskać pełne wymagania systemowe programu Visual Studio 2017 dla komputerów Mac, zobacz [wymagania systemowe rodziny produktów Visual studio 2017 for Mac](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Kompilowanie biblioteki

1. Na ekranie powitalnym wybierz pozycję **Nowy projekt**. W oknie dialogowym **Nowy projekt** w węźle **.NET Core** wybierz szablon **Biblioteka .NET Standard** . Spowoduje to utworzenie biblioteki .NET Standard, która jest przeznaczona dla platformy .NET Core, a także innych implementacji platformy .NET, które obsługują wersję 2,0 [.NET Standard](../../standard/net-standard.md). Wybierz pozycję **dalej**.

   ![Okno dialogowe Visual Studio dla komputerów Mac nowego projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Nadaj projektowi nazwę "textnarzędzis" (krótka nazwa "programów tekstowych") i rozwiązanie "WordCounter". Pozostaw pole wyboru **Utwórz katalog projektu w katalogu rozwiązania** . Wybierz pozycję **Utwórz**.

   ![Opcje okna dialogowego Visual Studio dla komputerów Mac nowego projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. Na pasku bocznym **rozwiązania** rozwiń węzeł `TextUtils`, aby odsłonić plik klasy dostarczony przez szablon, *Class1.cs*. Kliknij plik prawym przyciskiem myszy, wybierz polecenie **Zmień nazwę** z menu kontekstowego, a następnie zmień nazwę pliku na *WORDCOUNT.cs*. Otwórz plik i Zastąp jego zawartość następującym kodem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Zapisz plik przy użyciu jednej z trzech różnych metod <kbd>&#8984;</kbd> : Użyj skrótu klawiaturowego+<kbd>s</kbd>, zaznacz opcję **plik** > **Zapisz** z menu lub kliknij prawym przyciskiem myszy na karcie pliku i wybierz polecenie **Zapisz** z menu kontekstowego. Na poniższej ilustracji przedstawiono okno środowiska IDE:

   ![Visual Studio dla komputerów Mac okno środowiska IDE z plikiem biblioteki klas i metodą](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. Wybierz pozycję **Błędy** na marginesie u dołu okna IDE, aby otworzyć panel **Błędy** . Wybierz przycisk **kompilacja danych wyjściowych** .

   ![Dolny margines środowiska IDE programu Visual Studio Mac przedstawiającego przycisk błędy](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Wybierz kolejno opcje **kompiluj** > **Kompiluj wszystko** z menu.

   Rozwiązanie kompiluje. Panel dane wyjściowe kompilacji pokazuje, że kompilacja zakończyła się pomyślnie.

   ![Okienko danych wyjściowych kompilacji programu Visual Studio dla komputerów Mac w panelu Błędy z komunikatem Kompilacja zakończona pomyślnie](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Tworzenie projektu testowego

Testy jednostkowe zapewniają zautomatyzowane testowanie oprogramowania podczas opracowywania i publikowania. Platforma testowa używana w tym samouczku to [xUnit (wersja 2.2.0 lub nowsza)](https://xunit.github.io/), która jest instalowana automatycznie po dodaniu projektu testowego xUnit do rozwiązania w następujących krokach:

1. Na pasku bocznym **rozwiązania** kliknij prawym przyciskiem myszy rozwiązanie `WordCounter` i wybierz polecenie **Dodaj** > **Dodaj nowy projekt**.

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **testy** z węzła **.NET Core** . Wybierz **projekt testu xUnit** , a następnie kliknij przycisk **dalej**.

   ![Tworzenie projektu testu xUnit w oknie dialogowym programu Visual Studio Mac New Project](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Nadaj nowemu projektowi nazwę "TestLibrary" i wybierz pozycję **Utwórz**.

   ![Okno dialogowe nowego projektu programu Visual Studio dla komputerów Mac z nazwą projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Aby biblioteka testowa działała z klasą `WordCount`, Dodaj odwołanie do projektu `TextUtils`. Na pasku bocznym **rozwiązania** kliknij prawym przyciskiem myszy pozycję **zależności** w obszarze **TestLibrary**. Wybierz pozycję **Edytuj odwołania** z menu kontekstowego.

1. W oknie dialogowym **Edytowanie odwołań** **Wybierz projekt na karcie** **projekty** . Wybierz **przycisk OK**.

   ![Okno dialogowe edycji odwołań dla programu Visual Studio Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. W projekcie **TestLibrary** Zmień nazwę pliku *UnitTest1.cs* na *TextUtilsTests.cs*.

1. Otwórz plik i zastąp go następującym kodem:

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

   Na poniższej ilustracji przedstawiono środowisko IDE z kodem testu jednostkowego. Zwróć uwagę na `Assert.NotEqual` instrukcji.

   ![Visual Studio dla komputerów Mac początkowy test jednostkowy w oknie głównym IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Ważne jest, aby nowy test był zakończony niepowodzeniem, aby potwierdzić, że logika testowania jest poprawna. Metoda przekazuje nazwę "Jack" (wielkie litery) i ciąg z "Jack" i "Jack" (wielkie i małe litery). Jeśli metoda `GetWordCount` działa prawidłowo, zwraca liczbę dwóch wystąpień szukanego wyrazu. Aby ten test mógł zakończyć się niepowodzeniem, należy najpierw zaimplementować test potwierdzający, że dwa wystąpienia wyrazu wyszukiwania "Jack" nie są zwracane przez metodę `GetWordCount`. Przejdź do następnego kroku, aby zakończyć test w celu przeprowadzenia testu.

1. Otwórz panel **testy jednostkowe** po prawej stronie ekranu.

   ![Panel testów jednostkowych Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Kliknij ikonę **dokowania** , aby pozostawić otwarty panel.

   ![Ikona dokowania panelu testy jednostkowe Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Kliknij przycisk **Uruchom wszystko** .

   Test zakończy się niepowodzeniem, co jest prawidłowym wynikiem. Metoda testowa potwierdza, że dwa wystąpienia `inputString`"wtyczka" nie są zwracane z ciągu "gniazdko gniazdko" dostarczonego do metody `GetWordCount`. Ponieważ wielkość liter wyrazów została zainicjowana w metodzie `GetWordCount`, zwracane są dwa wystąpienia. Potwierdzenie, że 2 *nie jest równe* 2, kończy się niepowodzeniem. Jest to prawidłowy wynik, a logika naszego testu jest dobra.

   ![Visual Studio dla komputerów Mac wyświetlania niepowodzeń testów](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Zmodyfikuj metodę testową `IgnoreCasing`, zmieniając `Assert.NotEqual` do `Assert.Equal`. Zapisz plik przy <kbd>&#8984;</kbd> użyciu skrótu klawiaturowego+<kbd>s</kbd>, **plik** > **Zapisz** z menu lub kliknij prawym przyciskiem myszy kartę pliku i wybierz polecenie **Zapisz** z menu kontekstowego.

   Oczekuje się, że `searchWord` "wtyczka" zwróci dwa wystąpienia z `inputString` "gniazdko gniazdko" przesłane do `GetWordCount`. Uruchom test ponownie, klikając przycisk **Uruchom testy** w panelu **testy jednostkowe** lub przycisk **uruchom testy ponownie** w panelu **wyniki testów** w dolnej części ekranu. Test zakończy się pomyślnie. Istnieją dwa wystąpienia "Jack" w ciągu "wtyczka gniazda" (ignorowanie wielkości liter), a potwierdzenie testu jest `true`.

   ![Visual Studio dla komputerów Mac wyświetlania przebiegu testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Testowanie pojedynczych wartości zwracanych za pomocą `Fact` jest tylko początkiem czynności, które można wykonać za pomocą testów jednostkowych. Inna zaawansowana technika umożliwia przetestowanie kilku wartości jednocześnie przy użyciu `Theory`. Dodaj następującą metodę do klasy `TextUtils_GetWordCountShould`. Po dodaniu tej metody masz dwie metody klasy:

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

   `CountInstancesCorrectly` sprawdza, czy metoda `GetWordCount` liczy się poprawnie. `InlineData` zawiera liczbę, szukany wyraz i ciąg wejściowy do sprawdzenia. Metoda testowa jest uruchamiana jednokrotnie dla każdego wiersza danych. Należy pamiętać, że po raz pierwszy zakończyło się niepowodzeniem przy użyciu `Assert.NotEqual`, nawet jeśli wiesz, że liczby w danych są poprawne i że wartości są zgodne z liczbą zwracaną przez metodę `GetWordCount`. Wykonanie kroku niepowodzenia testu w celu może pozornie wyglądać jak marnowanie czasu, ale sprawdzenie logiki testów przez jego niepowodzenie najpierw jest ważnym sprawdzaniem logiki testów. Gdy powrócisz przez metodę testową, która kończy się niepowodzeniem, w logice testu znaleziono usterkę. Warto wykonać ten krok przy każdym tworzeniu metody testowej.

1. Zapisz plik i ponownie uruchom testy. Test wielkości liter kończy się, ale trzy testy Count kończą się niepowodzeniem. Jest to dokładnie to, czego oczekujesz.

   ![Visual Studio dla komputerów Mac oczekiwany błąd testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Zmodyfikuj metodę testową `CountInstancesCorrectly`, zmieniając `Assert.NotEqual` do `Assert.Equal`. Zapisz plik. Uruchom testy ponownie. Wszystkie testy zostały zakończone pomyślnie.

   ![Visual Studio dla komputerów Mac oczekiwanego przebiegu testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Dodawanie aplikacji konsolowej

1. Na pasku bocznym **rozwiązania** kliknij prawym przyciskiem myszy rozwiązanie `WordCounter`. Dodaj nowy projekt **aplikacji konsolowej** , wybierając szablon z szablonów aplikacji **.NET Core** >  . Wybierz pozycję **dalej**. Nazwij projekt **WordCounterApp**. Wybierz pozycję **Utwórz** , aby utworzyć projekt w rozwiązaniu.

1. Na pasku bocznym **rozwiązania** kliknij prawym przyciskiem myszy węzeł **zależności** nowego projektu **WordCounterApp** . W oknie dialogowym **Edytowanie odwołań** **zaznacz pole wyboru,** a następnie wybierz pozycję **OK**.

1. Otwórz plik *program.cs* . Zastąp kod następującym:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Aby uruchomić aplikację w oknie konsoli zamiast IDE, kliknij prawym przyciskiem myszy projekt `WordCounterApp`, wybierz pozycję **Opcje**, a następnie otwórz węzeł **domyślny** w obszarze **konfiguracje**. Zaznacz pole wyboru **Uruchom w konsoli zewnętrznej**. Pozostaw zaznaczoną opcję **Wstrzymaj wyjście konsoli** . To ustawienie powoduje, że aplikacja będzie duplikowana w oknie konsoli, aby można było wpisać dane wejściowe dla instrukcji `Console.ReadLine`. Jeśli opuścisz aplikację do uruchamiania w środowisku IDE, możesz zobaczyć tylko dane wyjściowe instrukcji `Console.WriteLine`. instrukcje `Console.ReadLine` nie działają w panelu **wyjście aplikacji** IDE.

   ![Okno opcji projektu Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-project-options.png)

1. Ponieważ bieżąca wersja Visual Studio dla komputerów Mac nie może uruchomić testów po uruchomieniu rozwiązania, należy uruchomić aplikację konsolową bezpośrednio. Kliknij prawym przyciskiem myszy projekt `WordCounterApp` i wybierz polecenie **Uruchom element** z menu kontekstowego. Jeśli spróbujesz uruchomić aplikację przy użyciu przycisku Odtwórz, moduł uruchamiający testy i aplikacja nie powiodą się. Aby uzyskać więcej informacji na temat stanu pracy dotyczącej tego problemu, zobacz [xUnit/xamarinstudio. xUnit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Po uruchomieniu aplikacji podaj wartości dla wyrazu wyszukiwania i ciąg wejściowy na monitach w oknie konsoli. Aplikacja wskazuje, ile razy słowo wyszukiwania ma być wyświetlane w ciągu.

   ![Visual Studio dla komputerów Mac okno konsoli z uruchomioną aplikacją](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Ostatnią funkcją eksplorowania jest debugowanie za pomocą Visual Studio dla komputerów Mac. Ustaw punkt przerwania w instrukcji `Console.WriteLine`: wybierz pozycję na lewym marginesie linii 23. zobaczysz czerwony okrąg obok wiersza kodu. Alternatywnie możesz wybrać dowolne miejsce w wierszu kodu i wybrać polecenie **uruchom** > **Przełącz punkt przerwania** z menu.

   ![Visual Studio dla komputerów Mac ustawiony punkt przerwania](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. Kliknij prawym przyciskiem myszy projekt `WordCounterApp`. Wybierz pozycję **Rozpocznij debugowanie elementu** z menu kontekstowego. Po uruchomieniu aplikacji wprowadź wyraz wyszukiwania "Cat" i "piesed kot, ale kot". ciąg do wyszukania. Po osiągnięciu instrukcji `Console.WriteLine` wykonywanie programu zostaje zatrzymane przed wykonaniem instrukcji. Na karcie zmienne **lokalne** można zobaczyć wartości `searchWord`, `inputString`, `wordCount`i `pluralChar`.

   ![Wykonywanie programu debugera Visual Studio dla komputerów Mac zostało zatrzymane](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. W okienku **bezpośrednim** wpisz "wordCount = 999;" i naciśnij klawisz ENTER. Spowoduje to przypisanie wartości niewykrywanej 999 do zmiennej `wordCount`, co oznacza, że można zamienić wartości zmiennych podczas debugowania.

   ![Visual Studio dla komputerów Mac zmienić wartości w oknie bezpośrednim](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Na pasku narzędzi kliknij strzałkę *Kontynuuj* . Spójrz na dane wyjściowe w oknie konsoli. Raportuje niepoprawną wartość 999 ustawioną podczas debugowania aplikacji.

   ![Przycisk Visual Studio dla komputerów Mac Kontynuuj na pasku narzędzi](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   ![Dane wyjściowe okna konsoli Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

## <a name="see-also"></a>Zobacz także

- [Informacje o wersji programu Visual Studio 2017 dla komputerów Mac](/visualstudio/releasenotes/vs2017-mac-relnotes)
