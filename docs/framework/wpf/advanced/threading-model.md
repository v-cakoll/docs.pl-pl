---
title: Model wątkowości
description: Dowiedz się więcej na temat sytuacji, w których może być potrzebnych wiele wątków w aplikacji Windows Presentation Foundation. Preferowane są rozwiązania jednowątkowe.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: 9b67b6ea2896e9e6fec57dee8d1013d54fab03fc
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166381"
---
# <a name="threading-model"></a>Model wątkowości
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]służy do zapisywania deweloperów przed trudnościami z wątkami. W związku z tym większość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deweloperów nie będzie musiała pisać interfejsu, który używa więcej niż jednego wątku. Ponieważ programy wielowątkowe są skomplikowane i trudne do debugowania, należy je unikać, gdy istnieją rozwiązania jednowątkowe.

 Niezależnie od tego, jak dobrze jest zaprojektowana architektura, żadna [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] platforma nie będzie w stanie zapewnić jednowątkowego rozwiązania dla każdego rodzaju problemu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]działa blisko siebie, ale nadal występują sytuacje, w których wiele wątków poprawia [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] czas odpowiedzi lub wydajność aplikacji. Po przedyskutowaniu pewnego materiału tła ten dokument eksploruje niektóre z tych sytuacji, a następnie kończy dyskusje na temat pewnych szczegółów niższego poziomu.

> [!NOTE]
> W tym temacie omówiono wątki przy użyciu <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody wywołań asynchronicznych. Można również wykonywać wywołania asynchroniczne <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> , wywołując metodę, która przyjmuje <xref:System.Action> lub <xref:System.Func%601> jako parametr.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>Metoda zwraca <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601> , który ma <xref:System.Windows.Threading.DispatcherOperation.Task%2A> Właściwość. Możesz użyć `await` słowa kluczowego z <xref:System.Windows.Threading.DispatcherOperation> lub skojarzone <xref:System.Threading.Tasks.Task> . Jeśli musisz odczekać synchronicznie dla, <xref:System.Threading.Tasks.Task> który jest zwracany przez <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601> , wywołaj <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> metodę rozszerzenia.  Wywołanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> spowoduje zakleszczenie. Aby uzyskać więcej informacji o używaniu programu <xref:System.Threading.Tasks.Task> do wykonywania operacji asynchronicznych, zobacz równoległość zadań.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>Metoda ma również przeciążenia, które pobierają <xref:System.Action> lub <xref:System.Func%601> jako parametr.  Można użyć <xref:System.Windows.Threading.Dispatcher.Invoke%2A> metody do wykonywania wywołań synchronicznych przez przekazanie delegata <xref:System.Action> lub <xref:System.Func%601> .

<a name="threading_overview"></a>
## <a name="overview-and-the-dispatcher"></a>Przegląd i Dyspozytor
 Zazwyczaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje zaczynają się od dwóch wątków: jeden do obsługi renderowania i drugi do zarządzania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Wątek renderowania efektywnie działa jako ukryty w tle, podczas gdy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątek odbiera dane wejściowe, obsługuje zdarzenia, maluje na ekranie i uruchamia kod aplikacji. Większość aplikacji używa jednego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku, chociaż w niektórych sytuacjach najlepiej jest użyć kilku. Omawiamy ten przykład w przyszłości.

 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Wątki kolejki elementy robocze wewnątrz obiektu o nazwie a <xref:System.Windows.Threading.Dispatcher> . <xref:System.Windows.Threading.Dispatcher>Wybiera elementy robocze na podstawie priorytetu i uruchamia każdy z nich do ukończenia.  Każdy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątek musi mieć co najmniej jeden <xref:System.Windows.Threading.Dispatcher> , a każdy z nich <xref:System.Windows.Threading.Dispatcher> może wykonywać elementy robocze w dokładnie jednym wątku.

 W celu zwiększenia przepływności aplikacje przyjazne dla użytkownika mają na celu zmaksymalizowanie <xref:System.Windows.Threading.Dispatcher> wydajności przez utrzymywanie niewielkich elementów roboczych. W ten sposób elementy nigdy nie uzyskują starych w <xref:System.Windows.Threading.Dispatcher> kolejce oczekujących na przetworzenie. Wszelkie widoczne opóźnienia między wejściem i odpowiedzią mogą frustrować użytkownika.

 W jaki sposób [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje powinny obsługiwać duże operacje? Co zrobić, jeśli kod obejmuje duże obliczenia lub że musi wysyłać zapytania do bazy danych na niektórych serwerach zdalnych? Zwykle odpowiedź polega na obsłudze operacji Big w osobnym wątku, pozostawiając [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątek bezpłatnie do elementów w <xref:System.Windows.Threading.Dispatcher> kolejce. Po zakończeniu operacji Big można zgłosić jej wynik z powrotem do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku w celu wyświetlenia.

 W przeszłości, system Windows umożliwia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dostęp do elementów tylko przez wątek, który go utworzył. Oznacza to, że wątek w tle, który jest odpowiedzialny za niektóre długotrwałe zadania, nie może zaktualizować pola tekstowego po zakończeniu. System Windows robi to, aby zapewnić integralność [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] składników. Pole listy może wyglądać dziwnie, jeśli jego zawartość została zaktualizowana przez wątek w tle podczas malowania.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ma wbudowany mechanizm wzajemnego wykluczania, który wymusza tę koordynację. Większość klas w klasie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pochodnej <xref:System.Windows.Threading.DispatcherObject> . Podczas konstruowania program <xref:System.Windows.Threading.DispatcherObject> zapisuje odwołanie do <xref:System.Windows.Threading.Dispatcher> połączonego z aktualnie uruchomionym wątkiem. W efekcie <xref:System.Windows.Threading.DispatcherObject> skojarzenie z wątkiem, który tworzy go. Podczas wykonywania programu element <xref:System.Windows.Threading.DispatcherObject> może wywołać metodę publiczną <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> . <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>bada <xref:System.Windows.Threading.Dispatcher> skojarzony z bieżącym wątkiem i porównuje go z <xref:System.Windows.Threading.Dispatcher> odwołaniem przechowywanym podczas konstruowania. Jeśli nie są zgodne, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> zgłasza wyjątek. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>jest przeznaczony do wywołania na początku każdej metody należącej do <xref:System.Windows.Threading.DispatcherObject> .

 Jeśli tylko jeden wątek może zmodyfikować [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , jak wątki w tle współdziałają z użytkownikiem? Wątek w tle może zażądać [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku w celu wykonania operacji w jego imieniu. Robi to przez zarejestrowanie elementu pracy z <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątkiem. <xref:System.Windows.Threading.Dispatcher>Klasa oferuje dwie metody rejestrowania elementów roboczych: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> i <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> . Obie metody planują delegata do wykonania. <xref:System.Windows.Threading.Dispatcher.Invoke%2A>jest wywołaniem synchronicznym — to oznacza, że nie zwraca do momentu zakończenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wykonywania przez wątek obiektu delegowanego. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>jest asynchroniczny i natychmiast wraca.

 <xref:System.Windows.Threading.Dispatcher>Porządkuje elementy w kolejce według priorytetu. Istnieje dziesięć poziomów, które można określić podczas dodawania elementu do <xref:System.Windows.Threading.Dispatcher> kolejki. Te priorytety są utrzymywane w <xref:System.Windows.Threading.DispatcherPriority> wyliczeniu. Szczegółowe informacje <xref:System.Windows.Threading.DispatcherPriority> na temat poziomów można znaleźć w dokumentacji Windows SDK.

<a name="samples"></a>
## <a name="threads-in-action-the-samples"></a>Wątki w akcji: przykłady

<a name="prime_number"></a>
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Jednowątkowa aplikacja z długotrwałym obliczaniem
 Większość graficznych interfejsów użytkownika (GUI) poświęca dużą część czasu bezczynności podczas oczekiwania na zdarzenia, które są generowane w odpowiedzi na interakcje użytkownika. Staranne programowanie tego czasu bezczynności może być stosowane zwyczajowo, bez wpływu na czas odpowiedzi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Model wątkowości nie zezwala na dane wejściowe do przerwania operacji wykonywanej w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Oznacza to, że należy zwrócić uwagę na <xref:System.Windows.Threading.Dispatcher> okresowe, aby przetworzyć oczekujące zdarzenia wejściowe przed uzyskaniem starych.

 Rozpatrzmy następujący przykład:

 ![Zrzut ekranu pokazujący wątki numerów pierwszych.](./media/threading-model/threading-prime-numbers.png)

 Ta prosta aplikacja liczy się w górę od trzech, wyszukując cyfry podstawowe. Gdy użytkownik kliknie przycisk **Start** , rozpocznie się wyszukiwanie. Po znalezieniu programu Program aktualizuje interfejs użytkownika przy użyciu odnajdywania. W dowolnym momencie użytkownik może zatrzymać wyszukiwanie.

 Chociaż jest to bardzo proste, wyszukiwanie w liczbie pierwszych może być bardzo trudne, co stwarza pewne problemy.  Jeśli przeprowadzimy całe wyszukiwanie w ramach programu obsługi zdarzeń kliknięcia przycisku, nigdy nie wyślemy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku do obsługi innych zdarzeń. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Nie można odpowiedzieć na komunikaty wejściowe lub procesowe. Nigdy nie będzie można go odświeżyć i nigdy nie reaguje na kliknięcia przycisku.

 Możemy przeszukać numer w osobnym wątku, ale należy zająć się problemami z synchronizacją. Dzięki podejściu jednowątkowego można bezpośrednio zaktualizować etykietę, która wyświetla największy znaleziony.

 W przypadku podziału zadania obliczeń na fragmenty zarządzane można okresowo wrócić do <xref:System.Windows.Threading.Dispatcher> zdarzeń i. Możemy dać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] szansę na odświeżenie i przetworzenie danych wejściowych.

 Najlepszym sposobem podziału czasu przetwarzania między obliczeniami a obsługą zdarzeń jest zarządzanie obliczeniami z <xref:System.Windows.Threading.Dispatcher> . Korzystając z <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody, możemy zaplanować sprawdzanie liczby pierwszych w tej samej kolejce, z której [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] są rysowane zdarzenia. W naszym przykładzie zaplanuję tylko jednolite sprawdzenie liczby. Po zakończeniu sprawdzania numeru na stronie zostanie zaplanowana natychmiastowa ponowna kontrola. To sprawdzanie jest wykonywane dopiero po [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obsłużoniu oczekujących zdarzeń.

 ![Zrzut ekranu przedstawiający kolejkę dyspozytora.](./media/threading-model/threading-dispatcher-queue.png)

 Program Microsoft Word wykonuje sprawdzanie pisowni przy użyciu tego mechanizmu. Sprawdzanie pisowni odbywa się w tle przy użyciu czasu bezczynności [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Spójrzmy na kod.

 Poniższy przykład pokazuje kod XAML, który tworzy interfejs użytkownika.

 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]

 Poniższy przykład pokazuje kod w tle.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]

 Poniższy przykład pokazuje procedurę obsługi zdarzeń dla <xref:System.Windows.Controls.Button> .

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]

 Oprócz aktualizowania tekstu w programie <xref:System.Windows.Controls.Button> Ta procedura obsługi jest odpowiedzialna za planowanie pierwszego sprawdzenia numeru bazowego przez dodanie delegata do <xref:System.Windows.Threading.Dispatcher> kolejki. Gdy ten program obsługi zdarzeń zakończy pracę, <xref:System.Windows.Threading.Dispatcher> zostanie wybrany delegat do wykonania.

 Jak wspomniano wcześniej, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> to <xref:System.Windows.Threading.Dispatcher> element członkowski używany do planowania delegowania do wykonania. W takim przypadku wybieramy <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> priorytet. <xref:System.Windows.Threading.Dispatcher>Ten delegat zostanie wykonany tylko wtedy, gdy nie ma ważnych zdarzeń do przetworzenia. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]czas odpowiedzi jest ważniejszy niż sprawdzanie liczby. Przekazujemy również nowy delegat reprezentujący procedurę sprawdzania liczby.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]

 Ta metoda sprawdza, czy Następna liczba nieparzysta jest podstawowa. Jeśli jest to zapora, metoda bezpośrednio aktualizuje program, `bigPrime` <xref:System.Windows.Controls.TextBlock> aby odzwierciedlał jego odnajdywanie. Można to zrobić, ponieważ obliczenia występują w tym samym wątku, który został użyty do utworzenia składnika. Wybrano, aby użyć oddzielnego wątku do obliczenia. będziemy musieli użyć bardziej skomplikowanego mechanizmu synchronizacji i wykonać aktualizację w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Zobaczymy tę sytuację dalej.

 Aby uzyskać pełny kod źródłowy dla tego przykładu, zobacz [jednowątkowa aplikacja z przykładowym obliczeniem długotrwałym](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication)

<a name="weather_sim"></a>
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Obsługa operacji blokowania z wątkiem w tle
 Obsługa operacji blokowania w aplikacji graficznej może być trudna. Nie chcemy wywoływać metod blokowania z obsługi zdarzeń, ponieważ aplikacja zostanie wyświetlona w celu zablokowania. Możemy użyć oddzielnego wątku do obsługi tych operacji, ale gdy wszystko będzie gotowe, musimy przeprowadzić synchronizację z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątkiem, ponieważ nie można bezpośrednio zmodyfikować graficznego interfejsu użytkownika z naszego wątku roboczego. Możemy użyć <xref:System.Windows.Threading.Dispatcher.Invoke%2A> lub <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> , aby wstawić delegatów do <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. W rezultacie te Delegaty zostaną wykonane z uprawnieniami do modyfikowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów.

 W tym przykładzie naśladuje zdalne wywołanie procedury, które pobiera prognozę pogody. Używamy oddzielnego wątku roboczego do wykonania tego wywołania i planujemy metodę Update w <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku po zakończeniu.

 ![Zrzut ekranu przedstawiający interfejs użytkownika pogody.](./media/threading-model/threading-weather-ui.png)

 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]

 Poniżej przedstawiono niektóre szczegółowe informacje, które należy zanotować.

- Tworzenie procedury obsługi przycisku

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]

 Po kliknięciu przycisku zostanie wyświetlony rysunek zegar i rozpocznie się jego animowanie. Wyłącz przycisk. Wywołujemy `FetchWeatherFromServer` metodę w nowym wątku, a następnie zwracamy, <xref:System.Windows.Threading.Dispatcher> Aby umożliwić przetwarzanie zdarzeń w czasie oczekiwania na zebranie prognozy pogody.

- Pobieranie pogody

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]

 Aby zachować prostotę, w tym przykładzie nie ma żadnego kodu sieciowego. Zamiast tego symulowanie opóźnień dostępu do sieci przez umieszczenie nowego wątku w stanie uśpienia przez cztery sekundy. W tym czasie oryginalny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątek nadal działa i odpowiada na zdarzenia. Aby to pokazać, pozostawiłeś animację, a przyciski Minimalizuj i Maksymalizuj również nadal działają.

 Gdy opóźnienie zostanie zakończone i losowo wybieramy naszą prognozę pogody, czas na zgłoszenie do wątku jest raportowany ponownie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Możemy to zrobić przez zaplanowanie wywołania `UpdateUserInterface` w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku przy użyciu tego wątku <xref:System.Windows.Threading.Dispatcher> . Przekazujemy ciąg opisujący Pogoda do tego wywołania metody zaplanowanej.

- Aktualizowanie[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]

 Gdy <xref:System.Windows.Threading.Dispatcher> w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku ma czas, wykonywane jest zaplanowane wywołanie do `UpdateUserInterface` . Ta metoda powoduje zatrzymanie animacji zegara i wybranie obrazu opisującego Pogoda. Wyświetla ten obraz i przywraca przycisk "Pobierz prognozę".

<a name="multi_browser"></a>
### <a name="multiple-windows-multiple-threads"></a>Wiele okien, wiele wątków
 Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje wymagają wielu okien najwyższego poziomu. Jest to doskonale akceptowalne dla jednego wątku/ <xref:System.Windows.Threading.Dispatcher> kombinacji do zarządzania wieloma oknami, ale czasami kilka wątków ma lepsze zadanie. Jest to szczególnie prawdziwe, jeśli istnieje prawdopodobieństwo, że jeden z okien będzie monopolize wątek.

 Eksplorator Windows działa w ten sposób. Każde nowe okno Eksploratora należy do oryginalnego procesu, ale jest tworzone w ramach formantu niezależnego wątku.

 Za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> kontrolki można wyświetlić strony sieci Web. Można łatwo utworzyć prosty substytut programu Internet Explorer. Zaczynamy od ważnej funkcji: możliwość otwarcia nowego okna Eksploratora. Gdy użytkownik kliknie przycisk "nowe okno", zostanie uruchomiona kopia naszego okna w osobnym wątku. W ten sposób długotrwałe lub zablokowanie operacji w jednym z okien nie spowoduje zablokowania wszystkich innych okien.

 W rzeczywistości model przeglądarki sieci Web ma swój własny skomplikowany model wątkowości. Została wybrana, ponieważ powinna być znana większością czytelników.

 Poniższy przykład pokazuje kod.

 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]

 Następujące segmenty wątku tego kodu są najbardziej interesujące dla nas w tym kontekście:

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]

 Ta metoda jest wywoływana, gdy zostanie kliknięty przycisk "nowe okno". Tworzy nowy wątek i uruchamia go asynchronicznie.

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]

 Ta metoda jest punktem początkowym dla nowego wątku. Tworzymy nowe okno pod kontrolą tego wątku. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]automatycznie tworzy nowy <xref:System.Windows.Threading.Dispatcher> wątek do zarządzania nowym wątkiem. Wszystko, co należy zrobić, aby uruchomić okno <xref:System.Windows.Threading.Dispatcher> .

<a name="stumbling_points"></a>
## <a name="technical-details-and-stumbling-points"></a>Szczegóły techniczne i punkty Stumbling

### <a name="writing-components-using-threading"></a>Pisanie składników przy użyciu wątków
 Przewodnik dewelopera Microsoft .NET Framework opisuje wzorzec, w jaki składnik może ujawniać asynchroniczne zachowanie klientom (zobacz [Omówienie asynchronicznego wzorca opartego na zdarzeniach](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Na przykład załóżmy, że chcemy spakować `FetchWeatherFromServer` metodę do wielokrotnego użycia, niegraficznego składnika. Zgodnie ze standardowym wzorcem programu Microsoft .NET Framework będzie wyglądać podobnie do poniższego.

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]

 `GetWeatherAsync`Użyj jednej z opisanych wcześniej technik, takich jak tworzenie wątku w tle, do wykonywania pracy asynchronicznej, bez blokowania wątku wywołującego.

 Jedną z najważniejszych części tego wzorca jest wywołanie metody *MethodName* `Completed` w tym samym wątku, który wywołał metodę MethodName, *MethodName* `Async` Aby rozpocząć od. Można to zrobić przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dość łatwo, przez przechowywanie <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> — ale następnie składnik Niegraficzny może być używany tylko w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacjach, a nie w Windows Forms ani w programach ASP.NET.

 <xref:System.Windows.Threading.DispatcherSynchronizationContext>Ta klasa zaspokaja tę potrzebę — należy traktować ją jako uproszczoną wersję programu <xref:System.Windows.Threading.Dispatcher> , która również współpracuje z innymi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] środowiskami.

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]

### <a name="nested-pumping"></a>Zagnieżdżona pompa
 Czasami nie jest możliwe całkowite zablokowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Rozważmy <xref:System.Windows.MessageBox.Show%2A> metodę <xref:System.Windows.MessageBox> klasy. <xref:System.Windows.MessageBox.Show%2A>nie zwraca do momentu kliknięcia przycisku OK przez użytkownika. Istnieje jednak możliwość utworzenia okna, które musi zawierać pętlę komunikatów, aby można było go interaktywnie. Gdy oczekujemy, że użytkownik kliknie przycisk OK, oryginalne okno aplikacji nie odpowiada na dane wejściowe użytkownika. Można jednak nadal przetwarzać komunikaty programu Paint. Oryginalne okno jest ponownie rysowane po pokrytym i ujawnionym czasie.

 ![Zrzut ekranu, który pokazuje element MessageBox z przyciskiem OK](./media/threading-model/threading-message-loop.png)

 Część wątku musi być obciążona oknem komunikatu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]można utworzyć nowy wątek tylko dla okna komunikatu, ale ten wątek nie będzie mógł malować wyłączonych elementów w oryginalnym oknie (należy pamiętać o wcześniejszym omówieniu wzajemnego wykluczenia). Zamiast tego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa zagnieżdżonego systemu przetwarzania komunikatów. <xref:System.Windows.Threading.Dispatcher>Klasa zawiera specjalną metodę o nazwie <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> , która przechowuje bieżący punkt wykonywania aplikacji, a następnie rozpoczyna nową pętlę komunikatów. Po zakończeniu zagnieżdżonej pętli komunikatów wykonywanie jest wznawiane po oryginalnym <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> wywołaniu.

 W takim przypadku <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> utrzymuje kontekst programu w wywołaniu <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> i uruchamia nową pętlę komunikatów w celu odświeżenia okna tła i obsługi danych wejściowych w oknie komunikatu. Gdy użytkownik kliknie przycisk OK i wyczyści okno podręczne, zagnieżdżona pętla zostanie ZAMKNIĘTA, a kontrolka zostanie wznowiona po wywołaniu <xref:System.Windows.MessageBox.Show%2A> .

### <a name="stale-routed-events"></a>Nieodświeżone zdarzenia kierowane
 System zdarzeń kierowany w programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] powiadamia całe drzewa o zdarzeniach.

 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]

 Po naciśnięciu lewego przycisku myszy nad elipsą `handler2` jest wykonywane. Po `handler2` zakończeniu zdarzenie jest przesyłane do <xref:System.Windows.Controls.Canvas> obiektu, który używa `handler1` do przetwarzania. Dzieje się tak tylko wtedy `handler2` , gdy obiekt zdarzenia nie jest jawnie oznaczany jako obsłużony.

 Jest możliwe, że `handler2` przetwarzanie tego zdarzenia będzie bardzo czasochłonne. `handler2`może użyć, <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> Aby rozpocząć zagnieżdżoną pętlę komunikatów, która nie zwraca dla godzin. Jeśli `handler2` nie oznacza to zdarzenia jako obsługiwanego po zakończeniu tej pętli komunikatu, zdarzenie jest przesyłane w górę drzewa, mimo że jest bardzo stare.

### <a name="reentrancy-and-locking"></a>Współużytkowania wątkowości i blokowanie
 Mechanizm blokowania aparatu plików wykonywalnych języka wspólnego (CLR) nie zachowuje się dokładnie tak, jak to możliwe. może oczekiwać, że wątek zaprzestanie operacji w całości podczas żądania blokady. W rzeczywistości wątek nadal otrzymuje i przetwarza komunikaty o wysokim priorytecie. Pomaga to zapobiegać zakleszczeniom i sprawiać, że interfejsy w minimalnym stopniu odpowiadają, ale wprowadzają możliwość delikatnych usterek.  Ogromna większość czasu nie musi wiedzieć o tym, ale w rzadkich przypadkach (zazwyczaj obejmuje komunikaty okna Win32 lub składniki STA COM), co może być bardziej świadome.

 Większość interfejsów nie jest zbudowana z myślą o bezpieczeństwie wątków, ponieważ deweloperzy pracują w ramach założeń, do których [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nigdy nie uzyskuje dostępu za pomocą więcej niż jednego wątku. W takim przypadku ten pojedynczy wątek może wprowadzać zmiany w środowisku w nieoczekiwanym czasie, powodując niekorzystne skutki, że <xref:System.Windows.Threading.DispatcherObject> mechanizm wzajemnego wykluczania ma zostać rozwiązany. Weź pod uwagę następujące pseudokodzie:

 ![Diagram przedstawiający współużytkowania wątkowości wątków.](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")

 Większość czasu, który jest właściwy, ale istnieją przypadki, w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] których takie nieoczekiwane współużytkowania wątkowości mogą naprawdę spowodować problemy. W związku z tym, w określonych momentach, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wywołania <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A> , które zmieniają instrukcję Lock dla tego wątku, tak, aby korzystały z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] blokady współużytkowania wątkowości-Free, zamiast zwykłej blokady środowiska CLR.

 Dlaczego zespół CLR wybiera takie zachowanie? Musiało to zrobić z obiektami COM STA i wątkiem finalizacji. Gdy obiekt jest odzyskiwany, jego `Finalize` Metoda jest uruchamiana w dedykowanym wątku finalizatora, a nie w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Jest to problem, ponieważ obiekt STA obiektu COM, który został utworzony w wątku, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] można usunąć tylko w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Środowisko CLR pełni odpowiednik wartości <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (w tym przypadku przy użyciu Win32's `SendMessage` ). Ale jeśli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątek jest zajęty, wątek finalizatora jest wstrzymany i nie można usunąć obiektu sta. com, co powoduje powstanie poważnych przecieków pamięci. Dlatego zespół CLR wykonał trudne wywołanie, aby blokady działały w taki sposób.

 Zadanie ma na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] celu uniknięcie nieoczekiwanej współużytkowania wątkowości bez konieczności podania wycieku pamięci, dlatego nie blokujemy współużytkowania wątkowości wszędzie.

## <a name="see-also"></a>Zobacz także

- [Przykładowa aplikacja jednowątkowa o długim czasie wykonywania obliczeń](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication)
