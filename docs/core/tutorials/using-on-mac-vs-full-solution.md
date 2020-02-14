---
title: Tworzenie kompletnego rozwiązania .NET Core przy użyciu Visual Studio dla komputerów Mac
description: W tym artykule omówiono tworzenie rozwiązania .NET Core, które obejmuje biblioteki wielokrotnego użytku i testy jednostkowe.
ms.date: 12/19/2019
ms.openlocfilehash: dea23da33912de849f0dcbe1e2f6fa3edb3a5e24
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215207"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne zintegrowane środowisko programistyczne (IDE) do tworzenia aplikacji platformy .NET Core. W tym artykule omówiono tworzenie rozwiązania .NET Core, które obejmuje biblioteki wielokrotnego użytku i testy jednostkowe.

W tym samouczku pokazano, jak utworzyć aplikację, która akceptuje słowo wyszukiwania i ciąg tekstu od użytkownika, zlicza, ile razy słowo wyszukiwania pojawia się w ciągu przy użyciu metody w bibliotece klas i zwraca wynik do użytkownika. Rozwiązanie obejmuje również testy jednostkowe dla biblioteki klas jako wprowadzenie do koncepcji testowania jednostkowego. Jeśli wolisz przejść przez samouczek z kompletnym przykładem, Pobierz [przykładowe rozwiązanie](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Opinie są wysoce wyceniane. Istnieją dwa sposoby przekazywania opinii zespołowi programistycznemu na Visual Studio dla komputerów Mac:
>
> - W Visual Studio dla komputerów Mac wybierz pozycję **Pomoc** , > **zgłosić problem** z menu lub **Zgłoś problem** na ekranie powitalnym, co spowoduje otwarcie okna umożliwiającego zgłoszenie usterki. Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Aby utworzyć sugestię, wybierz pozycję **pomoc** > **Podaj sugestię** z menu lub **Podaj sugestię** z ekranu powitalnego, który przeprowadzi cię do [witryny internetowej społeczności deweloperów Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Wymagania wstępne

- [Zestaw .NET Core SDK 3,1 lub nowszy](https://dotnet.microsoft.com/download)
- [Program Visual Studio 2019 dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Aby uzyskać więcej informacji na temat wymagań wstępnych, zobacz [zależności i wymagania dotyczące platformy .NET Core](../install/dependencies.md?pivots=os-macos). Aby uzyskać pełne wymagania systemowe programu Visual Studio 2019 dla komputerów Mac, zobacz [wymagania systemowe rodziny produktów Visual studio 2019 for Mac](/visualstudio/productinfo/vs2019-system-requirements-mac).

## <a name="building-a-library"></a>Kompilowanie biblioteki

1. W oknie uruchamiania wybierz pozycję **Nowy projekt**. W oknie dialogowym **Nowy projekt** w węźle **.NET Core** wybierz szablon **Biblioteka .NET Standard** . To polecenie tworzy bibliotekę .NET Standard, która jest przeznaczona dla platformy .NET Core, a także inne implementacje platformy .NET, które obsługują wersję 2,1 [.NET Standard](../../standard/net-standard.md). Jeśli masz zainstalowaną wiele wersji zestaw .NET Core SDK, możesz wybrać różne wersje .NET Standard dla biblioteki. Wybierz pozycję ".NET Standard 2,1" i wybierz pozycję **dalej**.

   > [!div class="mx-imgBorder"]
   > okno dialogowe ![Visual Studio dla komputerów Mac nowego projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Nadaj projektowi nazwę "textnarzędzis" (krótka nazwa "programów tekstowych") i rozwiązanie "WordCounter". Pozostaw pole wyboru **Utwórz katalog projektu w katalogu rozwiązania** . Wybierz pozycję **Utwórz**.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac opcje okna dialogowego Nowy projekt](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. W konsoli **rozwiązania** rozwiń węzeł `TextUtils`, aby odsłonić plik klasy dostarczony przez szablon, *Class1.cs*. Naciśnij klawisz Ctrl i kliknij plik, wybierz polecenie **Zmień nazwę** z menu kontekstowego, a następnie zmień nazwę pliku na *WORDCOUNT.cs*. Otwórz plik i Zastąp jego zawartość następującym kodem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Zapisz plik przy użyciu jednej z trzech różnych metod <kbd>&#8984;</kbd> : Użyj skrótu klawiaturowego+<kbd>s</kbd>, wybierz pozycję **plik** > **Zapisz** z menu lub kliknij przycisk CTRL-kliknięcie na karcie plik i wybierz pozycję **Zapisz** z menu kontekstowego. Na poniższej ilustracji przedstawiono okno środowiska IDE:

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac okno środowiska IDE z plikiem biblioteki klas i metodą](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. Wybierz pozycję **Błędy** na marginesie u dołu okna IDE, aby otworzyć panel **Błędy** . Wybierz przycisk **kompilacja danych wyjściowych** .

   > [!div class="mx-imgBorder"]
   > ![dolny margines środowiska IDE programu Visual Studio Mac z wyświetlonym przyciskiem błędy](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Wybierz kolejno opcje **kompiluj** > **Kompiluj wszystko** z menu.

   Rozwiązanie kompiluje. Panel dane wyjściowe kompilacji pokazuje, że kompilacja zakończyła się pomyślnie.

   > [!div class="mx-imgBorder"]
   > ![okienku danych wyjściowych kompilacji programu Visual Studio Mac w panelu Błędy z komunikatem kompilacja pomyślna](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Tworzenie projektu testowego

Testy jednostkowe zapewniają zautomatyzowane testowanie oprogramowania podczas opracowywania i publikowania. Platforma testowa używana w tym samouczku to [xUnit (wersja 2.4.0 lub nowsza)](https://xunit.github.io/), która jest instalowana automatycznie po dodaniu projektu testowego xUnit do rozwiązania w następujących krokach:

1. Na pasku bocznym **rozwiązania** naciśnij klawisz Ctrl i kliknij `WordCounter` rozwiązanie, a następnie wybierz pozycję **Dodaj** > **Dodaj nowy projekt**.

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **testy** z węzła **.NET Core** . Wybierz **projekt testu xUnit** , a następnie kliknij przycisk **dalej**.

   > [!div class="mx-imgBorder"]
   > ![oknie dialogowym Nowy projekt w programie Visual Studio dla komputerów Mac Utwórz projekt testu xUnit](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Jeśli masz wiele wersji zestaw .NET Core SDK, musisz wybrać wersję dla tego projektu. Wybierz pozycję **.NET Core 3,1**. Nadaj nowemu projektowi nazwę "TestLibrary" i wybierz pozycję **Utwórz**.

   > [!div class="mx-imgBorder"]
   > ![okno dialogowe nowego projektu programu Visual Studio dla komputerów Mac, które udostępnia nazwę projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Aby biblioteka testowa działała z klasą `WordCount`, Dodaj odwołanie do projektu `TextUtils`. Na pasku bocznym **rozwiązania** kliknij pozycję **zależności** w obszarze **TestLibrary**. Wybierz pozycję **Edytuj odwołania** z menu kontekstowego.

1. W oknie dialogowym **Edytowanie odwołań** **Wybierz projekt na karcie** **projekty** . Wybierz **przycisk OK**.

   > [!div class="mx-imgBorder"]
   > ![oknie dialogowym Edytowanie odwołań w programie Visual Studio Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)

1. W projekcie **TestLibrary** Zmień nazwę pliku *UnitTest1.cs* na *TextUtilsTests.cs*.

1. Otwórz plik i Zastąp kod następującym kodem:

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

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac początkowy test jednostkowy w oknie głównym IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Ważne jest, aby nowy test był zakończony niepowodzeniem, aby potwierdzić, że logika testowania jest poprawna. Metoda przekazuje nazwę "Jack" (wielkie litery) i ciąg z "Jack" i "Jack" (wielkie i małe litery). Jeśli metoda `GetWordCount` działa prawidłowo, zwraca liczbę dwóch wystąpień szukanego wyrazu. Aby ten test mógł zakończyć się niepowodzeniem, należy najpierw zaimplementować test potwierdzający, że dwa wystąpienia wyrazu wyszukiwania "Jack" nie są zwracane przez metodę `GetWordCount`. Przejdź do następnego kroku, aby zakończyć test w celu przeprowadzenia testu.

1. Otwórz panel **testy jednostkowe** po prawej stronie ekranu. Wybierz pozycję **wyświetl** > **testy** z menu.

   > [!div class="mx-imgBorder"]
   > Panel testów jednostkowych ![Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Kliknij ikonę **dokowania** , aby pozostawić otwarty panel. (Wyróżniony na poniższej ilustracji).

   > [!div class="mx-imgBorder"]
   > ikona dokowania ![panelu testy jednostkowe Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Kliknij przycisk **Uruchom wszystko** .

   Test zakończy się niepowodzeniem, co jest prawidłowym wynikiem. Metoda testowa potwierdza, że dwa wystąpienia `inputString`"wtyczka" nie są zwracane z ciągu "gniazdko gniazdko" dostarczonego do metody `GetWordCount`. Ponieważ wielkość liter wyrazów została zainicjowana w metodzie `GetWordCount`, zwracane są dwa wystąpienia. Potwierdzenie, że 2 *nie jest równe* 2, kończy się niepowodzeniem. Wynikiem tego jest prawidłowy wynik, a logika naszego testu jest dobra.

   > [!div class="mx-imgBorder"]
   > ![wyświetlania niepowodzeń testów Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Zmodyfikuj metodę testową `IgnoreCasing`, zmieniając `Assert.NotEqual` do `Assert.Equal`. Zapisz plik przy użyciu skrótu klawiaturowego <kbd>Ctrl</kbd>+<kbd>s</kbd>, **plik** > **Zapisz** z menu lub naciśnij klawisz CTRL, klikając kartę pliku i wybierając pozycję **Zapisz** z menu kontekstowego.

   Oczekuje się, że `searchWord` "wtyczka" zwróci dwa wystąpienia z `inputString` "gniazdko gniazdko" przesłane do `GetWordCount`. Uruchom test ponownie, klikając przycisk **Uruchom testy** w panelu **testy jednostkowe** lub przycisk **uruchom testy ponownie** w panelu **wyniki testów** w dolnej części ekranu. Test zakończy się pomyślnie. Istnieją dwa wystąpienia "Jack" w ciągu "wtyczka gniazda" (ignorowanie wielkości liter), a potwierdzenie testu jest `true`.

   > [!div class="mx-imgBorder"]
   > ![wyświetlania testów Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

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

1. Zapisz plik i ponownie uruchom testy. Test wielkości liter kończy się, ale trzy testy Count kończą się niepowodzeniem. Ten wynik ma dokładne znaczenie.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac oczekiwany błąd testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Zmodyfikuj metodę testową `CountInstancesCorrectly`, zmieniając `Assert.NotEqual` do `Assert.Equal`. Zapisz plik. Uruchom testy ponownie. Wszystkie testy zostały zakończone pomyślnie.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac oczekiwanych przebiegów testowych](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Dodawanie aplikacji konsolowej

1. Na pasku bocznym **rozwiązania** naciśnij klawisz Ctrl i kliknij `WordCounter` rozwiązanie. Dodaj nowy projekt **aplikacji konsolowej** , wybierając szablon z szablonów aplikacji **.NET Core** >  . Wybierz opcję **Dalej**. Nazwij projekt **WordCounterApp**. Wybierz pozycję **Utwórz** , aby utworzyć projekt w rozwiązaniu.

1. Na pasku bocznym **rozwiązania** naciśnij klawisz Ctrl i kliknij węzeł **zależności** nowego projektu **WordCounterApp** . W oknie dialogowym **Edytowanie odwołań** **zaznacz pole wyboru,** a następnie wybierz pozycję **OK**.

1. Otwórz plik *program.cs* . Zastąp kod następującym kodem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Naciśnij klawisz Ctrl i kliknij projekt `WordCounterApp` i wybierz polecenie **Uruchom projekt** z menu kontekstowego. Po uruchomieniu aplikacji podaj wartości dla wyrazu wyszukiwania i ciąg wejściowy na monitach w oknie konsoli. Aplikacja wskazuje, ile razy słowo wyszukiwania ma być wyświetlane w ciągu.

   > [!div class="mx-imgBorder"]
   > ![okno konsoli Visual Studio dla komputerów Mac z uruchomioną aplikacją](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Ostatnią funkcją eksplorowania jest debugowanie za pomocą Visual Studio dla komputerów Mac. Ustaw punkt przerwania w instrukcji `Console.WriteLine`: wybierz pozycję na lewym marginesie linii 23. zobaczysz czerwony okrąg obok wiersza kodu. Alternatywnie możesz wybrać dowolne miejsce w wierszu kodu i wybrać polecenie **uruchom** > **Przełącz punkt przerwania** z menu.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac punkt przerwania](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. Naciśnij klawisz Ctrl i kliknij projekt `WordCounterApp`. Wybierz pozycję **Rozpocznij debugowanie projektu** z menu kontekstowego. Po uruchomieniu aplikacji wprowadź wyraz wyszukiwania "Cat" i "piesed kot, ale kot". ciąg do wyszukania. Po osiągnięciu instrukcji `Console.WriteLine` wykonywanie programu zostaje zatrzymane przed wykonaniem instrukcji. Na karcie zmienne **lokalne** można zobaczyć wartości `searchWord`, `inputString`, `wordCount`i `pluralChar`.

   > [!div class="mx-imgBorder"]
   > ![wykonywanie programu debugera Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. W okienku **bezpośrednim** wpisz "wordCount = 999;" i naciśnij klawisz ENTER. To polecenie przypisuje wartość nierozpoznaną 999 do zmiennej `wordCount`, co oznacza, że można zamienić wartości zmiennych podczas debugowania.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac zmienić wartości w oknie bezpośrednim](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Na pasku narzędzi kliknij strzałkę *Kontynuuj* . Spójrz na dane wyjściowe w oknie konsoli. Raportuje niepoprawną wartość 999 ustawioną podczas debugowania aplikacji.

   > [!div class="mx-imgBorder"]
   > ![Visual Studio dla komputerów Mac przycisk Kontynuuj na pasku narzędzi](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   > [!div class="mx-imgBorder"]
   > ![dane wyjściowe okna konsoli Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

Można użyć tego samego procesu do debugowania kodu przy użyciu projektu testu jednostkowego. Zamiast uruchamiać projekt aplikacji WordCount, kliknij pozycję projekt **biblioteki testowej** , a następnie wybierz pozycję **Rozpocznij debugowanie projektu** z menu kontekstowego. Visual Studio dla komputerów Mac uruchamia projekt testowy z dołączonym debugerem. Wykonanie zostanie zatrzymane na dowolnym punkcie przerwania, który został dodany do projektu testowego lub kodu biblioteki źródłowej.

## <a name="see-also"></a>Zobacz też

- [Visual Studio 2019 dla komputerów Mac — Informacje o wersji](/visualstudio/releasenotes/vs2019-mac-relnotes)
