---
title: "Kompilowanie kompletnego rozwiązania .NET Core na macOS przy użyciu programu Visual Studio dla komputerów Mac"
description: "W tym temacie przedstawiono tworzenie rozwiązania .NET Core biblioteki do ponownego wykorzystania i testowania jednostek."
keywords: "System macOS .NET i .NET core, komputerów Mac"
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 6945bedf-5bf3-4955-8588-83fb87511b79
ms.openlocfilehash: 60179fb0435803c3235b75ba012e588c6f1b35d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a>Kompilowanie kompletnego rozwiązania .NET Core na macOS przy użyciu programu Visual Studio dla komputerów Mac

Visual Studio for Mac zawiera kompletne programowanie środowiska IDE (Integrated) do tworzenia aplikacji platformy .NET Core. W tym temacie przedstawiono tworzenie rozwiązania .NET Core biblioteki do ponownego wykorzystania i testowania jednostek.

Ten samouczek pokazuje, jak utworzyć aplikację, która akceptuje word wyszukiwania i ciąg tekstu od użytkownika, liczy razy wyszukiwanego pojawia się w ciągu za pomocą innej metody w bibliotece klas i zwraca wynik dla użytkownika. Rozwiązanie zawiera również testu jednostkowego dla biblioteki klas jako wprowadzenie do koncepcji projektowanie oparte na (testach TDD). Jeśli wolisz przejdź przez samouczek z kompletnego przykładu, Pobierz [przykładowe rozwiązanie](https://github.com/dotnet/docs/blob/master/samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter). Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

> [!NOTE]
> Twoja opinia jest bardzo ważnych. Istnieją dwa sposoby można przekazywania informacji pozwalających na zespół deweloperów w programie Visual Studio dla komputerów Mac:
> * W programie Visual Studio dla komputerów Mac, wybierz **pomocy** > **zgłosić Problem** z menu lub **zgłosić Problem** na ekranie powitalnym, która powoduje otwarcie okna zgłoszenia Raport o usterce. Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html).
> * Aby sugestię, wybierz **pomocy** > **Podaj sugestię** z menu lub **Podaj sugestię** na ekranie powitalnym, który umożliwia przejście do [ Programu Visual Studio for Mac UserVoice strony sieci Web](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Wymagania wstępne

- Biblioteki OpenSSL (jeśli jest uruchomiony program .NET Core 1.1): zobacz [wymagania wstępne dotyczące .NET Core w systemie Mac](../macos-prerequisites.md) tematu.
- [Oprogramowanie .NET core SDK 1.1 lub nowszej](https://www.microsoft.com/net/core#macos)
- [Visual Studio 2017 dla komputerów Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

Aby uzyskać więcej informacji dotyczących wymagań wstępnych, zobacz [wymagania wstępne dotyczące .NET Core w systemie Mac](../../core/macos-prerequisites.md). Aby uzyskać pełne wymagania systemowe programu Visual Studio 2017 dla komputerów Mac, zobacz [programu Visual Studio 2017 wymagania systemowe rodziny produktów Mac](https://www.visualstudio.com/productinfo/vs2017-system-requirements-mac).

## <a name="building-a-library"></a>Kompilowanie biblioteki

1. Na ekranie powitalnym zaznacz **nowy projekt**. W **nowy projekt** , okno dialogowe **Multiplatform** węzła, wybierz opcję **biblioteki standardowej .NET** szablonu. Wybierz **dalej**.

   ![Okno dialogowe nowego projektu](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. Nazwij projekt "TextUtils" (krótką nazwę "Narzędzia tekstowe") i rozwiązania "WordCounter". Pozostaw **Utwórz katalog projektu w katalogu rozwiązania** zaznaczone. Wybierz **utworzyć**.

   ![Okno dialogowe nowego projektu](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. W **rozwiązania** paska bocznego, rozwiń węzeł `TextUtils` węzeł, aby ujawnić klasy zapewnianą przez szablon, *Class1.cs*. Kliknij prawym przyciskiem myszy plik, wybierz **zmienić** z menu kontekstowego i Zmień nazwę pliku do *WordCount.cs*. Otwórz plik i Zastąp zawartość następującym kodem:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. Zapisz plik przy użyciu dowolnej z trzech różnych metod: Użyj skrótu klawiaturowego <kbd>&#8984;</kbd> + <kbd>s</kbd>, wybierz pozycję **pliku** > **zapisać** z menu lub kliknij prawym przyciskiem myszy na karcie i wybierz plik **zapisać**z menu kontekstowego. Na poniższej ilustracji przedstawiono okno środowiska IDE:

   ![Okno środowiska IDE TextUtils klasy biblioteki, plik klasy WordCount klasy statycznej WordCount i GetWordCount — metoda](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. Wybierz **błędy** na marginesie w dolnej części okna IDE, aby otworzyć **błędy** panelu. Wybierz **wyjścia kompilacji** przycisku.

   ![Dolny margines IDE przedstawiający przycisk błędów](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. Wybierz **kompilacji** > **kompilacji wszystkich** z menu.

   Buduje rozwiązanie. Panelu wyjścia kompilacji pokazuje, że kompilacja zakończy się pomyślnie.

   ![W okienku z wyjściem z komunikatem pomyślnej kompilacji panelu Błędy kompilacji](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a>Tworzenie projektu testu

Testy jednostkowe Podaj oprogramowania zautomatyzowanych testów podczas programowania i publikowania. Testowanie ramach używanej w tym samouczku jest [xUnit (wersja 2.2.0 lub nowszym)](https://xunit.github.io/), którym jest instalowana automatycznie podczas xUnit projektu testowego jest dodany do rozwiązania w poniższych krokach:

1. W **rozwiązania** paska bocznego, kliknij prawym przyciskiem myszy `WordCounter` rozwiązania i wybierz **Dodaj** > **Dodawanie nowego projektu**.

1. W **nowy projekt** okno dialogowe, wybierz opcję **testy** z **.NET Core** węzła. Wybierz **xUnit projekt testowy** następuje **dalej**.

   ![Okno dialogowe nowego projektu tworzenia projektu testowego xUnit](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. Nazwa nowego projektu "TestLibrary" i wybierz **Utwórz**.

   ![Okno dialogowe nowego projektu podanie nazwy projektu](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. Aby biblioteka testów do pracy z `WordCount` klasy, Dodaj odwołanie do `TextUtils` projektu. W **rozwiązania** paska bocznego, kliknij prawym przyciskiem myszy **zależności** w obszarze **TestLibrary**. Wybierz **odwołania Edytuj** z menu kontekstowego.

1. W **odwołania Edytuj** okno dialogowe, wybierz opcję **TextUtils** projektu na **projekty** kartę. Wybierz **OK**.

   ![Edytowanie okna dialogowego odwołania](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. W **TestLibrary** projektu, Zmień nazwę *UnitTest1.cs* pliku *TextUtilsTests.cs*.

1. Otwórz plik i Zastąp kod z następujących czynności:

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

   Na poniższej ilustracji przedstawiono IDE z kod testu jednostkowego w miejscu. Należy zwrócić uwagę na `Assert.NotEqual` instrukcji.

   ![Początkowa jednostka test, aby sprawdzić GetWordCount w głównym oknie IDE](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   Przy użyciu TDD, ważne jest nowego testu nie raz Potwierdź poprawność jej logiki testowych. Metoda przekazuje w nazwie "Gniazda" (wielkie litery), a ciąg "Gniazda" i "gniazda" (wielkie i małe litery). Jeśli `GetWordCount` metody działa prawidłowo, zwracana jest liczba dwa wystąpienia wyrazu wyszukiwania. Aby w celu niepowodzenie tego testu, najpierw zaimplementowaniem testu potwierdzające, że dwa wystąpienia wyrazu "Gniazda" wyszukiwania nie są zwracane przez `GetWordCount` metody. Kontynuuj do następnego kroku w celu niepowodzenie testu.

1. Otwórz **testów jednostkowych** panelu po prawej stronie ekranu.

![Panel testy jednostkowe](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. Kliknij przycisk **dokowania** ikonę, aby utrzymać otwarte panelu.

![Ikona dokowania Panelu testy jednostkowe](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. Kliknij przycisk **Uruchom wszystkie** przycisku.
   
   Test ma wynik negatywny, który jest poprawny wynik. Metoda testowa potwierdza, że dwa wystąpienia `inputString`, "Gniazda", nie są zwracane z ciągu "Gniazda gniazda" dostarczony do `GetWordCount` metody. Ponieważ wielkość liter w programie word został wzięciu pod uwagę limit `GetWordCount` metody, zwracane są dwa wystąpienia. Potwierdzenia które 2 *nie jest równa* 2 kończy się niepowodzeniem. Jest to poprawny wynik i logiki naszym teście jest dobra.

   ![Niepowodzenia testu](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. Modyfikowanie `IgnoreCasing` metoda testowa, zmieniając `Assert.NotEqual` do `Assert.Equal`. Zapisz plik przy użyciu skrótu klawiaturowego <kbd>&#8984;</kbd> + <kbd>s</kbd>, **pliku** > **zapisać** z menu lub kartę plik prawym przyciskiem myszy i wybierając **zapisać**z menu kontekstowego.

   Oczekuje, że `searchWord` "Gniazda" zwraca dwa wystąpienia z `inputString` "Gniazda gniazda" przekazany do `GetWordCount`. Uruchom test ponownie, klikając **Uruchom testy** przycisk **testów jednostkowych** panelu lub **ponownie uruchom testy** przycisk **wyników testu** panelu w dolnej części ekranu. Test zakończył się pomyślnie. Istnieją dwa wystąpienia "Gniazda" w ciągu "Gniazda gniazda" (bez uwzględnienia wielkości liter) i jest potwierdzenie testu `true`.

   ![Przebiegu testowego](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

1. Testowanie poszczególnych wartości zwracanych z `Fact` jest tylko na początku co można zrobić testowania jednostek. Innej techniki zaawansowane można testować kilku wartości naraz, korzystając z `Theory`. Dodaj następującą metodę do Twojej `TextUtils_GetWordCountShould` klasy. Masz dwie metody w klasie po dodaniu tej metody:

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

   `CountInstancesCorrectly` Sprawdza, czy `GetWordCount` metody liczy się poprawnie. `InlineData` Zawiera liczby, word wyszukiwania i wejściowy ciąg do sprawdzenia. Metoda testowa jest uruchamiane jeden raz dla każdego wiersza danych. Ponownie Pamiętaj, że błąd jest zostanie najpierw przy użyciu `Assert.NotEqual`nawet wtedy, gdy wiesz, że liczby elementów danych są poprawne, a wartości liczby zwrócony przez takie same `GetWordCount` metody. Wykonanie kroku z niepowodzeniem testu w celu może się wydawać odpady czasu na początku, ale sprawdzanie logikę testu przez przełączając ją najpierw jest ważne wyboru przy użyciu logiki testów. Po wyświetleniu przez metodę testu, która przekazuje w oczekiwanym niepowodzenie znaleźliśmy usterki w logikę testu. Warto starań, aby wykonać ten krok w każdym tworzeniu metody testowej.
   
1. Zapisz plik i ponownie uruchom testy. Wielkość liter jest prawdziwe, ale niepowodzenia testów trzy count. Jest to dokładnie, oczekują na to.

   ![Niepowodzenia testu](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. Modyfikowanie `CountInstancesCorrectly` metoda testowa, zmieniając `Assert.NotEqual` do `Assert.Equal`. Zapisz plik. Ponownie uruchom testy. Wszystkie testy zostały zaliczone pomyślnie.

   ![Przebiegu testowego](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a>Dodawanie aplikacji konsoli

1. W **rozwiązania** paska bocznego, kliknij prawym przyciskiem myszy `WordCounter` rozwiązania. Dodaj nową **aplikacji konsoli** projektu, wybierając szablon z **.NET Core** > **aplikacji** szablonów. Wybierz **dalej**. Nazwij projekt **WordCounterApp**. Wybierz **Utwórz** można utworzyć projektu w rozwiązaniu.

1. W **rozwiązań** paska bocznego, kliknij prawym przyciskiem myszy **zależności** węzła nowego **WordCounterApp** projektu. W **odwołania Edytuj** dialogowym wyboru **TextUtils** i wybierz **OK**.

1. Otwórz *Program.cs* pliku. Zastąp kod z następujących czynności:

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. Aby uruchomić aplikację w oknie konsoli zamiast IDE, kliknij prawym przyciskiem myszy `WordCounterApp` projektu, zaznacz **opcje**i Otwórz **domyślne** węźle **konfiguracje**. Pole wyboru dla **Uruchom na zewnętrznej konsoli**. Pozostaw **wstrzymać dane wyjściowe konsoli** zaznaczoną opcją. To ustawienie powoduje, że aplikację można zduplikować w oknie konsoli, w którym można wpisać dane wejściowe dla `Console.ReadLine` instrukcje. Jeśli opuścisz aplikacji do uruchamiania w środowisku IDE może zobaczyć tylko dane wyjściowe `Console.WriteLine` instrukcje. `Console.ReadLine`instrukcje nie działają w IDE **danych wyjściowych aplikacji** panelu.

   ![Okno Opcje projektu](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. Ponieważ w bieżącej wersji programu Visual Studio dla komputerów Mac nie można uruchomić testy po uruchomieniu rozwiązania, możesz uruchomić aplikację konsoli bezpośrednio. Kliknij prawym przyciskiem myszy `WordCounterApp` projekt i wybierz **Uruchom elementu** z menu kontekstowego. Jeśli użytkownik spróbuje uruchomić aplikację z przycisk Odtwórz, test runner i aplikacjami nie uruchomić. Aby uzyskać więcej informacji o stanie pracy na ten problem, zobacz [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60). Po uruchomieniu aplikacji, podaj wartości dla wyszukiwanego i ciągu wejściowego na monity w oknie konsoli. Aplikacja wskazuje, ile razy wyszukiwanego pojawia się w ciągu.

   ![Okno konsoli przedstawiający wyraz oliwki przeszukiwane w ciągu "Iro uj oliwki przez jeziora i oliwki zostały cudowne." Odpowiada aplikacji "oliwki word wyszukiwania pojawi się 2 razy."](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. Ostatni funkcję tak, aby eksplorować jest debugowanie za pomocą programu Visual Studio dla komputerów Mac. Ustaw punkt przerwania na `Console.WriteLine` instrukcji: Wybierz na lewym marginesie wiersz 23 i pojawi się czerwone kółko pojawiają się obok wiersza kodu. Można także wybrać dowolne miejsce w wierszu kodu i wybierz **Uruchom** > **Przełącz punkt przerwania** z menu.

   ![Punkt przerwania jest ustawiony w wierszu 23 instrukcji elementu Console.WriteLine](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. Kliknij prawym przyciskiem myszy `WordCounterApp` projektu. Wybierz **Rozpocznij debugowanie elementu** z menu kontekstowego. Po uruchomieniu aplikacji, wprowadź wyszukiwania słowa "kot" i "dog poszukiwane cat, ale cat zmienione znaczenie." ciąg do wyszukania. Gdy `Console.WriteLine` osiągnięciu instrukcji, wykonania programu zostanie zatrzymany przed wykonaniem instrukcji. W **zmiennych lokalnych** może zostać wyświetlona `searchWord`, `inputString`, `wordCount`, i `pluralChar` wartości.

   ![Wykonanie programu został zatrzymany na instrukcji elementu Console.WriteLine w oknie lokalne przedstawiające wartości natychmiast, przed wykonaniem instrukcji elementu Console.WriteLine.](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. W **Immediate** okienku, wpisz "wordCount = 999;" i naciśnij klawisz Enter. W ten sposób wartość żadnego znaczenia 999 do `wordCount` zmiennej pokazujący, że podczas debugowania można zastąpić wartości zmiennych.

   ![Nasze punkt przerwania zostaje trafiony. WordCount jest zmieniana na wartość 999 w oknie bezpośrednim](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. Na pasku narzędzi, kliknij przycisk *kontynuować* strzałki. Sprawdź dane wyjściowe w oknie konsoli. Przekazuje błędną wartość 999 ustawioną podczas zostały debugowania aplikacji.

   ![Kontynuować przycisku w pasku narzędzi](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![Wyrazów wyszukiwania zostanie zmieniona wartość 999 w danych wyjściowych aplikacji](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a>Zobacz także

[Visual Studio 2017 dla komputerów Mac informacje o wersji](https://www.visualstudio.com/news/releasenotes/vs2017-mac-relnotes)
