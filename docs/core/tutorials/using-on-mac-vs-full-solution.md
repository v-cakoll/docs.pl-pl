---
title: Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac
description: W tym temacie omówiono tworzenie rozwiązania .NET Core, które obejmuje biblioteki wielokrotnego użytku i testy jednostkowe.
author: mairaw
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: 46d118cc4dc54e34db0f964aa3f8d76f0ad67249
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925994"
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne zintegrowane środowisko programistyczne (IDE) do tworzenia aplikacji platformy .NET Core. W tym temacie omówiono tworzenie rozwiązania .NET Core, które obejmuje biblioteki wielokrotnego użytku i testy jednostkowe.

W tym samouczku pokazano, jak utworzyć aplikację, która akceptuje słowo wyszukiwania i ciąg tekstu od użytkownika, zlicza, ile razy słowo wyszukiwania pojawia się w ciągu przy użyciu metody w bibliotece klas i zwraca wynik do użytkownika. Rozwiązanie obejmuje również testy jednostkowe dla biblioteki klas jako wprowadzenie do koncepcji testowania jednostkowego. Jeśli wolisz przejść przez samouczek z kompletnym przykładem, Pobierz [przykładowe rozwiązanie](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Opinie są wysoce wyceniane. Istnieją dwa sposoby przekazywania opinii zespołowi programistycznemu na Visual Studio dla komputerów Mac:
>
> - W Visual Studio dla komputerów Mac wybierz pozycję **Pomoc** > **Zgłoś problem** z menu lub **Zgłoś problem** na ekranie powitalnym, co spowoduje otwarcie okna umożliwiającego zgłoszenie usterki. Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Aby dokonać sugestii, wybierz pozycję **Pomoc** > **Podaj sugestię** z menu lub **Podaj sugestię** z ekranu powitalnego, który przeprowadzi Cię do [witryny internetowej społeczność deweloperów Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Wymagania wstępne

- OpenSSL (w przypadku uruchamiania programu .NET Core 1,1): Zapoznaj się z tematem [wymagania wstępne dotyczące programu .NET Core w systemie Mac](../macos-prerequisites.md) .
- [Zestaw .NET Core SDK 1,1 lub nowszy](https://dotnet.microsoft.com/download)
- [Visual Studio 2017 for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

Aby uzyskać więcej informacji na temat wymagań wstępnych, zobacz [wymagania wstępne dotyczące platformy .NET Core na komputerze Mac](../macos-prerequisites.md). Aby uzyskać pełne wymagania systemowe programu Visual Studio 2017 dla komputerów Mac, zobacz [wymagania systemowe rodziny produktów Visual studio 2017 for Mac](/visualstudio/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Kompilowanie biblioteki

1. Na ekranie powitalnym wybierz pozycję **Nowy projekt**. W oknie dialogowym **Nowy projekt** w węźle **.NET Core** wybierz szablon **Biblioteka .NET Standard** . Spowoduje to utworzenie biblioteki .NET Standard, która jest przeznaczona dla platformy .NET Core, a także innych implementacji platformy .NET, które obsługują wersję 2,0 [.NET Standard](../../standard/net-standard.md). Wybierz opcję **Dalej**.

   ![Okno dialogowe Visual Studio dla komputerów Mac nowego projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)

1. Nadaj projektowi nazwę "textnarzędzis" (krótka nazwa "programów tekstowych") i rozwiązanie "WordCounter". Pozostaw pole wyboru **Utwórz katalog projektu w katalogu rozwiązania** . Wybierz pozycję **Utwórz**.

   ![Opcje okna dialogowego Visual Studio dla komputerów Mac nowego projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)

1. Na pasku bocznym **rozwiązania** rozwiń `TextUtils` węzeł, aby odsłonić plik klasy dostarczony przez szablon, *Class1.cs*. Kliknij plik prawym przyciskiem myszy, wybierz polecenie **Zmień nazwę** z menu kontekstowego, a następnie zmień nazwę pliku na *WORDCOUNT.cs*. Otwórz plik i Zastąp jego zawartość następującym kodem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Zapisz plik przy użyciu jednej z trzech różnych metod: Użyj <kbd>&#8984;</kbd> +skrótu klawiaturowego **, wybierz opcję** > **Zapisz** z menu lub kliknij prawym przyciskiem myszy na karcie <kbd>pliku, a</kbd>następnie wybierz pozycję **Zapisz** z kontekstowego DodajMenu. Na poniższej ilustracji przedstawiono okno środowiska IDE:

   ![Visual Studio dla komputerów Mac okno środowiska IDE z plikiem biblioteki klas i metodą](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)

1. Wybierz pozycję **Błędy** na marginesie u dołu okna IDE, aby otworzyć panel **Błędy** . Wybierz przycisk **kompilacja danych wyjściowych** .

   ![Dolny margines środowiska IDE programu Visual Studio Mac przedstawiającego przycisk błędy](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)

1. Z menu wybierz pozycję **kompilacja** > **Kompiluj wszystko** .

   Rozwiązanie kompiluje. Panel dane wyjściowe kompilacji pokazuje, że kompilacja zakończyła się pomyślnie.

   ![Okienko danych wyjściowych kompilacji programu Visual Studio dla komputerów Mac w panelu Błędy z komunikatem Kompilacja zakończona pomyślnie](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)

## <a name="creating-a-test-project"></a>Tworzenie projektu testowego

Testy jednostkowe zapewniają zautomatyzowane testowanie oprogramowania podczas opracowywania i publikowania. Platforma testowa używana w tym samouczku to [xUnit (wersja 2.2.0 lub nowsza)](https://xunit.github.io/), która jest instalowana automatycznie po dodaniu projektu testowego xUnit do rozwiązania w następujących krokach:

1. Na pasku bocznym **rozwiązania** kliknij prawym przyciskiem `WordCounter` myszy rozwiązanie, a następnie wybierz polecenie **Dodaj** > **Dodaj nowy projekt**.

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **testy** z węzła **.NET Core** . Wybierz **projekt testu xUnit** , a następnie kliknij przycisk **dalej**.

   ![Tworzenie projektu testu xUnit w oknie dialogowym programu Visual Studio Mac New Project](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)

1. Nadaj nowemu projektowi nazwę "TestLibrary" i wybierz pozycję **Utwórz**.

   ![Okno dialogowe nowego projektu programu Visual Studio dla komputerów Mac z nazwą projektu](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)

1. Aby biblioteka testowa działała z `WordCount` klasą, Dodaj odwołanie `TextUtils` do projektu. Na pasku bocznym **rozwiązania** kliknij prawym przyciskiem myszy pozycję **zależności** w obszarze **TestLibrary**. Wybierz pozycję **Edytuj odwołania** z menu kontekstowego.

1. W oknie dialogowym **Edytowanie odwołań** **Wybierz projekt na karcie** **projekty** . Kliknij przycisk **OK**.

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

   Na poniższej ilustracji przedstawiono środowisko IDE z kodem testu jednostkowego. Zwróć uwagę na `Assert.NotEqual` instrukcję.

   ![Visual Studio dla komputerów Mac początkowy test jednostkowy w oknie głównym IDE](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)

   Ważne jest, aby nowy test był zakończony niepowodzeniem, aby potwierdzić, że logika testowania jest poprawna. Metoda przekazuje nazwę "Jack" (wielkie litery) i ciąg z "Jack" i "Jack" (wielkie i małe litery). `GetWordCount` Jeśli metoda działa prawidłowo, zwraca liczbę dwóch wystąpień szukanego wyrazu. Aby ten test mógł zakończyć się niepowodzeniem, należy najpierw zaimplementować test potwierdzający, że dwa wystąpienia wyrazu wyszukiwania "Jack" nie są zwracane przez `GetWordCount` metodę. Przejdź do następnego kroku, aby zakończyć test w celu przeprowadzenia testu.

1. Otwórz panel **testy jednostkowe** po prawej stronie ekranu.

   ![Panel testów jednostkowych Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)

1. Kliknij ikonę **dokowania** , aby pozostawić otwarty panel.

   ![Ikona dokowania panelu testy jednostkowe Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)

1. Kliknij przycisk **Uruchom wszystko** .

   Test zakończy się niepowodzeniem, co jest prawidłowym wynikiem. Metoda testowa potwierdza, że dwa wystąpienia elementu `inputString`"Jack" nie są zwracane z ciągu "gniazdko gniazdko" przekazanego `GetWordCount` do metody. Ponieważ wielkość liter słowa została przeprowadzona w `GetWordCount` metodzie, zwracane są dwa wystąpienia. Potwierdzenie, że 2 *nie jest równe* 2, kończy się niepowodzeniem. Jest to prawidłowy wynik, a logika naszego testu jest dobra.

   ![Visual Studio dla komputerów Mac wyświetlania niepowodzeń testów](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)

1. Zmodyfikuj metodę `IgnoreCasing` testową, zmieniając `Assert.NotEqual` wartość `Assert.Equal`na. Zapisz plik przy użyciu skrótu <kbd>&#8984;</kbd> +klawiaturowego <kbd>s</kbd>, **File** > **Save** z menu lub kliknij prawym przyciskiem myszy kartę pliku i wybierz polecenie **Zapisz** z menu kontekstowego.

   Oczekuje się, że `searchWord` "wtyczka" zwraca dwa wystąpienia z `inputString` przekazaną `GetWordCount`"gniazdem". Uruchom test ponownie, klikając przycisk **Uruchom testy** w panelu **testy jednostkowe** lub przycisk **uruchom testy ponownie** w panelu **wyniki testów** w dolnej części ekranu. Test zakończy się pomyślnie. Istnieją dwa wystąpienia "wtyczki" w ciągu "wtyczka gniazda" (ignorowanie wielkości liter), a potwierdzenie testu to `true`.

   ![Visual Studio dla komputerów Mac wyświetlania przebiegu testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

1. Testowanie pojedynczych wartości `Fact` zwracanych przez to tylko początek tego, co można zrobić za pomocą testów jednostkowych. Inna zaawansowana technika umożliwia przetestowanie kilku wartości jednocześnie przy `Theory`użyciu. Dodaj następującą metodę do `TextUtils_GetWordCountShould` klasy. Po dodaniu tej metody masz dwie metody klasy:

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

   Sprawdza, czy metoda `GetWordCount` jest prawidłowo liczona. `CountInstancesCorrectly` `InlineData` Zawiera liczbę, szukany wyraz i ciąg wejściowy do sprawdzenia. Metoda testowa jest uruchamiana jednokrotnie dla każdego wiersza danych. Należy pamiętać, że po raz pierwszy potwierdzasz niepowodzenie przy użyciu `Assert.NotEqual`, nawet jeśli wiesz, że liczby w danych są poprawne i że wartości są zgodne z liczbą zwracaną `GetWordCount` przez metodę. Wykonanie kroku niepowodzenia testu w celu może pozornie wyglądać jak marnowanie czasu, ale sprawdzenie logiki testów przez jego niepowodzenie najpierw jest ważnym sprawdzaniem logiki testów. Gdy powrócisz przez metodę testową, która kończy się niepowodzeniem, w logice testu znaleziono usterkę. Warto wykonać ten krok przy każdym tworzeniu metody testowej.

1. Zapisz plik i ponownie uruchom testy. Test wielkości liter kończy się, ale trzy testy Count kończą się niepowodzeniem. Jest to dokładnie to, czego oczekujesz.

   ![Visual Studio dla komputerów Mac oczekiwany błąd testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)

1. Zmodyfikuj metodę `CountInstancesCorrectly` testową, zmieniając `Assert.NotEqual` wartość `Assert.Equal`na. Zapisz plik. Uruchom testy ponownie. Wszystkie testy zostały zakończone pomyślnie.

   ![Visual Studio dla komputerów Mac oczekiwanego przebiegu testu](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)

## <a name="adding-a-console-app"></a>Dodawanie aplikacji konsolowej

1. Na pasku bocznym **rozwiązania** kliknij prawym przyciskiem `WordCounter` myszy rozwiązanie. Dodaj nowy projekt **aplikacji konsolowej** , wybierając szablon z szablonów**aplikacji** **platformy .NET Core** > . Wybierz opcję **Dalej**. Nazwij projekt **WordCounterApp**. Wybierz pozycję **Utwórz** , aby utworzyć projekt w rozwiązaniu.

1. Na pasku bocznym **rozwiązania** kliknij prawym przyciskiem myszy węzeł **zależności** nowego projektu **WordCounterApp** . W oknie dialogowym **Edytowanie odwołań** **zaznacz pole wyboru,** a następnie wybierz pozycję **OK**.

1. Otwórz plik *program.cs* . Zastąp kod następującym:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Aby uruchomić aplikację w oknie konsoli zamiast IDE, `WordCounterApp` kliknij prawym przyciskiem myszy projekt, wybierz opcję **Opcje**i Otwórz **domyślny** węzeł w obszarze **konfiguracje**. Zaznacz pole wyboru **Uruchom w konsoli zewnętrznej**. Pozostaw zaznaczoną opcję **Wstrzymaj wyjście konsoli** . To ustawienie powoduje, że aplikacja będzie duplikowana w oknie konsoli, aby można było wpisać dane wejściowe `Console.ReadLine` dla instrukcji. Jeśli opuścisz aplikację do uruchamiania w środowisku IDE, zobaczysz tylko dane wyjściowe `Console.WriteLine` instrukcji. `Console.ReadLine`instrukcje nie działają w panelu **wyjście aplikacji** IDE.

   ![Okno opcji projektu Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-project-options.png)

1. Ponieważ bieżąca wersja Visual Studio dla komputerów Mac nie może uruchomić testów po uruchomieniu rozwiązania, należy uruchomić aplikację konsolową bezpośrednio. Kliknij prawym przyciskiem `WordCounterApp` myszy projekt i wybierz polecenie **Uruchom element** z menu kontekstowego. Jeśli spróbujesz uruchomić aplikację przy użyciu przycisku Odtwórz, moduł uruchamiający testy i aplikacja nie powiodą się. Aby uzyskać więcej informacji na temat stanu pracy dotyczącej tego problemu, zobacz [xUnit/xamarinstudio. xUnit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Po uruchomieniu aplikacji podaj wartości dla wyrazu wyszukiwania i ciąg wejściowy na monitach w oknie konsoli. Aplikacja wskazuje, ile razy słowo wyszukiwania ma być wyświetlane w ciągu.

   ![Visual Studio dla komputerów Mac okno konsoli z uruchomioną aplikacją](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)

1. Ostatnią funkcją eksplorowania jest debugowanie za pomocą Visual Studio dla komputerów Mac. Ustaw punkt przerwania w `Console.WriteLine` instrukcji: Wybierz pozycję na lewym marginesie linii 23, a obok wiersza kodu zobaczysz czerwone koło. Alternatywnie możesz wybrać dowolne miejsce w wierszu kodu i wybrać polecenie **Uruchom** > **przełączanie punktu przerwania** z menu.

   ![Visual Studio dla komputerów Mac ustawiony punkt przerwania](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)

1. Kliknij prawym przyciskiem `WordCounterApp` myszy projekt. Wybierz pozycję **Rozpocznij debugowanie elementu** z menu kontekstowego. Po uruchomieniu aplikacji wprowadź wyraz wyszukiwania "Cat" i "piesed kot, ale kot". ciąg do wyszukania. `Console.WriteLine` Gdy instrukcja zostanie osiągnięta, wykonanie programu zostaje zatrzymane przed wykonaniem instrukcji. Na karcie **zmienne lokalne** `searchWord`można zobaczyć wartości, `inputString`, `wordCount`i `pluralChar` .

   ![Wykonywanie programu debugera Visual Studio dla komputerów Mac zostało zatrzymane](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)

1. W okienku **bezpośrednim** wpisz "wordCount = 999;" i naciśnij klawisz ENTER. Powoduje to przypisanie wartości niewykrywanej 999 do `wordCount` zmiennej, która wskazuje, że wartości zmiennych można zamienić podczas debugowania.

   ![Visual Studio dla komputerów Mac zmienić wartości w oknie bezpośrednim](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)

1. Na pasku narzędzi kliknij strzałkę *Kontynuuj* . Spójrz na dane wyjściowe w oknie konsoli. Raportuje niepoprawną wartość 999 ustawioną podczas debugowania aplikacji.

   ![Przycisk Visual Studio dla komputerów Mac Kontynuuj na pasku narzędzi](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)

   ![Dane wyjściowe okna konsoli Visual Studio dla komputerów Mac](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)

## <a name="see-also"></a>Zobacz także

- [Informacje o wersji programu Visual Studio 2017 dla komputerów Mac](/visualstudio/releasenotes/vs2017-mac-relnotes)
