---
title: Model wątkowości
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
ms.openlocfilehash: 0bcb0e7369345aaae39d99a005a07304aaad7043
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200353"
---
# <a name="threading-model"></a>Model wątkowości
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Służy do zapisywania deweloperów trudności wątkowości. W rezultacie, większość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deweloperzy nie będą musieli napisać interfejs, który korzysta z więcej niż jeden wątek. Ponieważ złożonej i trudnej do debugowania programów wielowątkowych, należy ich unikać gdy istnieje jednowątkowe rozwiązania.  
  
 Niezależnie od tego, jak dobrze zaprojektowana, jednak nie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] framework nigdy nie będą mogli stanowią rozwiązanie jednowątkowe dla każdego rodzaju problemu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pochodzi Zamknij, ale nadal istnieją sytuacje, gdy wiele wątków poprawić [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] wydajności aplikacji lub czas odpowiedzi. Po omówieniu niektóre materiały tła, w tym dokumencie analizuje niektóre z tych sytuacji, a następnie uzna, za pomocą dyskusję na temat niektórych informacji niższego poziomu.  

> [!NOTE]
>  W tym temacie omówiono wielowątkowości za pomocą <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metodę wywołania asynchroniczne. Asynchroniczne wywołania można również ustawić, wywołując <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> metody, która zająć <xref:System.Action> lub <xref:System.Func%601> jako parametr.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> Metoda zwraca <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>, który ma <xref:System.Windows.Threading.DispatcherOperation.Task%2A> właściwości. Możesz użyć `await` — słowo kluczowe z oboma <xref:System.Windows.Threading.DispatcherOperation> lub skojarzonego <xref:System.Threading.Tasks.Task>. Jeśli musisz czekać synchronicznie <xref:System.Threading.Tasks.Task> zwracanym przez <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>, wywołaj <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> — metoda rozszerzenia.  Wywoływanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> spowoduje zakleszczenia. Aby uzyskać więcej informacji o korzystaniu z <xref:System.Threading.Tasks.Task> do wykonywania operacji asynchronicznych, zobacz równoległość zadań.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A> Metoda ta ma również przeciążeń, które przyjmują <xref:System.Action> lub <xref:System.Func%601> jako parametr.  Możesz użyć <xref:System.Windows.Threading.Dispatcher.Invoke%2A> synchroniczne metody wywołania, przekazując delegata, <xref:System.Action> lub <xref:System.Func%601>.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Omówienie i Dyspozytor  
 Zazwyczaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje są uruchamiane z dwoma wątkami: jeden do obsługi renderowania i inny wpis dla zarządzania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Wątek renderowania skutecznie uruchomiony w trybie ukrytym w tle podczas [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku odbiera dane wejściowe, obsługuje zdarzenia, rysują ekranu i uruchamia kod aplikacji. Większość aplikacji używa pojedynczego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątków, mimo że w niektórych sytuacjach warto korzystać z kilku. Omówimy to przykład później.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Kolejek wątków elementach wewnątrz obiektu o nazwie <xref:System.Windows.Threading.Dispatcher>. <xref:System.Windows.Threading.Dispatcher> Wybiera elementy robocze w pierwszej kolejności i działa każdy z nich do zakończenia.  Co [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątek musi mieć co najmniej jeden <xref:System.Windows.Threading.Dispatcher>, a każdy <xref:System.Windows.Threading.Dispatcher> można wykonać elementy robocze w dokładnie jeden wątek.  
  
 Lewy do tworzenia aplikacji interaktywnych, przyjazny dla użytkownika jest zwiększenie <xref:System.Windows.Threading.Dispatcher> przepływność przy zachowaniu małych elementów roboczych. Nigdy nie ten sposób elementy Pobierz starych, znajdują się <xref:System.Windows.Threading.Dispatcher> kolejki oczekiwania na przetwarzanie. Wszelkie odczytywane opóźnienia między dane wejściowe i odpowiedzi może frustrować użytkownika.  
  
 Jak można [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji powinien obsługiwać operacje big Data? Co zrobić, jeśli kod wymaga dużych obliczeń lub musi zapytanie dotyczące bazy danych na niektórych serwerze zdalnym? Zazwyczaj jest odpowiedź do obsługi dużych operacji w oddzielnym wątku, pozostawiając [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] się zwykle do elementów w wątku <xref:System.Windows.Threading.Dispatcher> kolejki. Po zakończeniu operacji big Data, wynik może raportować do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku do wyświetlenia.  
  
 W przeszłości [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] umożliwia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy, aby był dostępny tylko dla wątku, który je utworzył. Oznacza to, czy wątku w tle odpowiedzialnym za niektóre długotrwałe zadanie nie można zaktualizować pola tekstowego po jego zakończeniu. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] robi to w celu zapewnienia integralności [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] składników. Pole listy mogłoby wyglądać dziwne, jeśli jego zawartość zostały zaktualizowane przez wątku w tle podczas rysowania.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma mechanizm wbudowanych wzajemne wykluczenie, który wymusza to koordynacji. Większość klas w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dziedziczyć <xref:System.Windows.Threading.DispatcherObject>. W konstrukcji <xref:System.Windows.Threading.DispatcherObject> przechowuje odwołania do <xref:System.Windows.Threading.Dispatcher> połączone z aktualnie uruchomionemu wątkowi. W efekcie <xref:System.Windows.Threading.DispatcherObject> kojarzy z wątku, który tworzy go. Podczas wykonywania programu <xref:System.Windows.Threading.DispatcherObject> może wywołać jej publicznego <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> metody. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> sprawdza, czy <xref:System.Windows.Threading.Dispatcher> skojarzone z bieżącym wątkiem i porównuje go do <xref:System.Windows.Threading.Dispatcher> odwołanie przechowywanych w trakcie konstruowania. Jeśli nie są zgodne, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> zgłasza wyjątek. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> jest przeznaczona do wywoływania na początku każdej metody należących do <xref:System.Windows.Threading.DispatcherObject>.  
  
 Jeśli tylko jeden wątek może modyfikować [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], wątków w tle interakcję z użytkownikiem? Poproś wątku w tle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku w celu wykonania operacji w jej imieniu. Jest to realizowane przez zarejestrowanie kodowań z elementu roboczego <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. <xref:System.Windows.Threading.Dispatcher> Klasa udostępnia dwie metody rejestrowania elementów roboczych: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> i <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Obie metody zaplanować delegata do wykonania. <xref:System.Windows.Threading.Dispatcher.Invoke%2A> to wywołanie synchroniczne — oznacza to, nie zwracać do momentu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku faktycznie kończy wykonywanie delegata. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> asynchroniczne i zwraca natychmiast.  
  
 <xref:System.Windows.Threading.Dispatcher> Porządkuje elementy które w swojej kolejki według priorytetu. Istnieją dziesięć poziomy, które może być określona podczas dodawania elementu <xref:System.Windows.Threading.Dispatcher> kolejki. Priorytety są obsługiwane w <xref:System.Windows.Threading.DispatcherPriority> wyliczenia. Szczegółowe informacje na temat <xref:System.Windows.Threading.DispatcherPriority> poziomy znajdują się w [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] dokumentacji.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Wątki w akcji: Przykłady  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Aplikacja jednowątkowa z obliczeniami długotrwałych  
 Większość [!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)] poświęcić dużo czasu bezczynności podczas oczekiwania na zdarzenia, które są generowane w odpowiedzi na interakcję użytkownika. Za pomocą programowania dokładnej tego czasu bezczynności może służyć konstruktywnie, bez wywierania wpływu na czas odpowiedzi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Model wątkowości nie zezwala na dane wejściowe przerwać operację działań wykonywanych w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Oznacza to, należy upewnić się powrócić do <xref:System.Windows.Threading.Dispatcher> okresowo, aby proces oczekujące zdarzenia wejściowe, zanim staną się przestarzałe.  
  
 Rozważmy następujący przykład:  
  
 ![Zrzut ekranu pokazujący wątkowości liczb pierwszych.](./media/threading-model/threading-prime-numbers.png)  
  
 Ta prosta aplikacja, do góry liczy się z trzech, wyszukując liczb pierwszych. Kiedy użytkownik kliknie **Start** przycisku, wyszukiwanie rozpoczyna się. Gdy program znajduje się zapora, aktualizacje interfejsu użytkownika jego poznawania. W dowolnym momencie użytkownik może zatrzymać wyszukiwanie.  
  
 Mimo że jest to prosta, wyszukiwanie liczba pierwsza można przejść w nieskończoność, który przedstawia pewne trudności.  Jeśli firma Microsoft obsługi całej wyszukiwania wewnątrz program obsługi zdarzeń kliknięcie przycisku, firma Microsoft nigdy nie dałaby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku szansę, aby obsłużyć inne zdarzenia. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Można odpowiedzieć na dane wejściowe lub przetwarzania komunikatów. Będzie ona nigdy nie repaint i nigdy nie odpowiadanie na kliknięcia przycisków.  
  
 Przeprowadzamy wyszukiwania liczba pierwsza w oddzielnym wątku, ale następnie będziemy potrzebować radzenia sobie z problemów z synchronizacją. Jednowątkowe podejście możemy bezpośrednio zaktualizować etykietę, która wyświetla największą priorytetowe znaleziono.  
  
 Jeśli firma Microsoft Podziel zadanie obliczania w partiach łatwych do zarządzania, firma Microsoft okresowo powrócić do <xref:System.Windows.Threading.Dispatcher> i przetwarzania zdarzeń. Możemy udostępnić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] możliwość odświeżenia i przetwarzania danych wejściowych.  
  
 Najlepszym sposobem podziału czas przetwarzania między obliczeń i obsługa zdarzeń jest zarządzanie obliczeń z <xref:System.Windows.Threading.Dispatcher>. Za pomocą <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody, możemy zaplanować liczba pierwsza kontroli w taki sam kolejki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zdarzenia są pobierane z. W tym przykładzie firma Microsoft zaplanować tylko sprawdzanie pojedyncza liczba prime w danym momencie. Po zakończeniu wyboru liczba pierwsza możemy zaplanować następne sprawdzenie natychmiast. Tego wyboru rozpoczynające się tylko po oczekiwaniu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zdarzenia zostały obsłużone.  
  
 ![Zrzut ekranu pokazujący kolejki dyspozytora.](./media/threading-model/threading-dispatcher-queue.png)  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)] w ramach przy użyciu tego mechanizmu sprawdzania pisowni. Sprawdzanie pisowni jest wykonywane w tle za pomocą czas bezczynności, po z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Spójrzmy na kod.  
  
 Poniższy przykład pokazuje XAML, który jest tworzony interfejs użytkownika.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 Poniższy przykład pokazuje związanym z kodem.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 W poniższym przykładzie pokazano program obsługi zdarzeń dla <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Oprócz Aktualizowanie tekstu w <xref:System.Windows.Controls.Button>, ten program obsługi jest odpowiedzialny za planowanie pierwszego wyboru liczba pierwsza, dodając obiekt delegowany do <xref:System.Windows.Threading.Dispatcher> kolejki. Za jakiś czas, po tej obsługi zdarzeń zakończy pracę, <xref:System.Windows.Threading.Dispatcher> wybierze ten delegat do wykonania.  
  
 Jak wspomniano wcześniej, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> jest <xref:System.Windows.Threading.Dispatcher> składowa użyta do zaplanowania delegata do wykonania. W tym przypadku Wybraliśmy <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> priorytetu. <xref:System.Windows.Threading.Dispatcher> Ten delegat będą wykonywane tylko wtedy, gdy Brak ważnych zdarzeń do przetworzenia. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czas odpowiedzi jest ważniejsza niż Sprawdzanie numeru. Możemy również przekazać nowe delegowanie reprezentujący sprawdzanie numer procedury.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Ta metoda sprawdza, czy najbliższej nieparzystej liczby pierwsze. Jeśli jest zainicjowanie, metoda bezpośrednio aktualizuje `bigPrime`<xref:System.Windows.Controls.TextBlock> aby odzwierciedlić ich odnajdywania. Możemy to zrobić, ponieważ obliczenie jest wykonywane w tym samym wątku, który został użyty do utworzenia składnika. Firma Microsoft wybierze użyć oddzielnego wątku do obliczenia, firma Microsoft musiałaby używany był mechanizm synchronizacji bardziej skomplikowane i wykonać aktualizację w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Następnie zademonstrujemy tę sytuację.  
  
 Aby uzyskać pełnego kodu źródłowego dla tego przykładu, zobacz [Single-Threaded aplikacji z przykładem obliczania długotrwałych](https://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Obsługa blokowania operacji z wątku w tle  
 Obsługa operacji blokowania w aplikacji graficznej może być trudne. Nie chcemy wywoływać metody blokowania z programu obsługi zdarzeń, ponieważ aplikacja pojawi się można zablokować w. Możemy użyć oddzielnego wątku, aby obsługiwać te operacje, ale gdy wszystko jest gotowe, mamy do synchronizacji z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątków, ponieważ nie można zmodyfikować bezpośrednio [!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)] z naszych wątku roboczego. Możemy użyć <xref:System.Windows.Threading.Dispatcher.Invoke%2A> lub <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> do wstawienia delegatów do <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Po pewnym czasie te delegaty zostanie wykonana przy użyciu uprawnień do modyfikowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów.  
  
 W tym przykładzie firma Microsoft naśladować wywołanie procedury zdalnej, która pobiera prognozę pogody. Firma Microsoft wątku roboczego oddzielnych do wykonania tego wywołania, a firma Microsoft zaplanować metodę aktualizacji w <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku, gdy będziemy zakończone.  
  
 ![Zrzut ekranu pokazujący pogody interfejsu użytkownika.](./media/threading-model/threading-weather-ui.png)  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Poniżej przedstawiono niektóre szczegółowe informacje, można zauważyć.  
  
-   Tworzenie procedury obsługi przycisku  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Po kliknięciu przycisku, możemy wyświetlić rysowania zegara, a następnie uruchom, zanimowaniu jej. Firma Microsoft wyłączenie przycisku. Możemy wywołać `FetchWeatherFromServer` metody w nowym wątku, a następnie utworzymy zwrotu, dzięki czemu <xref:System.Windows.Threading.Dispatcher> do przetwarzania zdarzeń, gdy firma Microsoft poczekać na zebranie prognozę pogody.  
  
-   Pobieranie pogody  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Aby zachować ich prostotę, faktycznie nie ma żadnego kodu sieci w tym przykładzie. Zamiast tego możemy symulować opóźnienia dostępu do sieci, umieszczając nasze nowy wątek w stan uśpienia na czterech sekund. W tym okresie, oryginalnym [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątek jest nadal uruchomiona i reagowanie na zdarzenia. Pokaż, firma Microsoft odeszli animację, uruchamianie i Minimalizuj i zmaksymalizować przyciski również kontynuować pracę.  
  
 Po zakończeniu opóźnienie i losowo Wybraliśmy naszych prognozę pogody, nadszedł czas na raportowane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Możemy to zrobić, planowanie wywołanie `UpdateUserInterface` w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku, przy użyciu tego wątku <xref:System.Windows.Threading.Dispatcher>. Przekazanie ciąg opisujący pogody na to wywołanie metody zaplanowane.  
  
-   Aktualizowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Gdy <xref:System.Windows.Threading.Dispatcher> w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątek ma czas, wykonuje wywołanie zaplanowane `UpdateUserInterface`. Ta metoda zatrzymuje animacji zegara i wybiera obraz do opisania pogody. On wyświetla ten obraz i przywraca przycisku "pobierania forecast".  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Windows wielu, wielu wątków  
 Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji wymaga wiele okien najwyższego poziomu. Doskonale dopuszczalna jeden wątek jest /<xref:System.Windows.Threading.Dispatcher> kombinację, aby zarządzać wieloma oknami, ale czasami kilku wątków wykonywanie lepszej pracy. Jest to szczególnie istotne w przypadku każdej okazji ten. systemu windows będzie zajmą wszystkich wątku.  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Eksplorator działa w ten sposób. Każde nowe okno Eksploratora należy do oryginalnego proces, ale jest tworzona pod kontrolą, niezależnie od wątku.  
  
 Za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Frame> kontrolki, można też wyświetlać stron sieci Web. Firma Microsoft można łatwo utworzyć prostą [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] zastąpienia. Rozpoczniemy pracę ważną funkcją: możliwości, aby otworzyć nowe okno Eksploratora. Gdy użytkownik kliknie przycisk "nowe okno" przycisk, możemy uruchomić kopię naszych okna w oddzielnym wątku. W ten sposób operacji długotrwałych lub blokowania w jednym z systemu windows nie będzie blokować inne okna.  
  
 W rzeczywistości modelu przeglądarki sieci Web ma swój własny skomplikowany model wątkowości. Wybraliśmy on, ponieważ powinna być znane większość odbiorców.  
  
 Poniższy przykład zawiera kod.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Cię najbardziej interesuje NAS w tym kontekście są następujące segmenty wątkowości tego kodu:  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Ta metoda jest wywoływana, gdy "nowe okno" przycisku. Tworzy nowy wątek i uruchamia go asynchronicznie.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Ta metoda jest punkt początkowy dla nowego wątku. Możemy utworzyć nowe okno pod kontrolą tego wątku. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] automatycznie tworzy nową <xref:System.Windows.Threading.Dispatcher> Zarządzanie nowy wątek. Musimy to zrobić, aby wyświetlić to okno funkcjonalności wystarczy uruchomić <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Szczegóły techniczne i Stumbling punktów  
  
### <a name="writing-components-using-threading"></a>Składniki zapisywania za pomocą wielowątkowości  
 Podręcznik dewelopera programu Microsoft .NET Framework w tym artykule opisano wzorzec jak składnik może narazić zachowanie asynchroniczne swoim klientom (zobacz [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Na przykład załóżmy, że Chcieliśmy utworzyć pakiet `FetchWeatherFromServer` metody do wielokrotnego użytku, które składnika. Następujące standardowego wzorca Microsoft .NET Framework to będzie wyglądać poniżej.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync` użyć jednej z metod opisanych wcześniej, takich jak tworzenie wątku w tle, które wykonają tę pracę asynchronicznie, nie blokuje wątek wywołujący.  
  
 Jeden z najważniejszych elementów tego wzorca wywoływany *MethodName* `Completed` metody w tym samym wątku, który wywołał *MethodName* `Async` zaczynają się od metody. Użytkownik może to zrobić za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dość łatwe dzięki przechowywaniu <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>—, ale następnie które składnik może być używana tylko w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, nie w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] programów.  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext> Klasy eliminuje to potrzebę — ją traktować jako uproszczoną wersję <xref:System.Windows.Threading.Dispatcher> która współdziała z innymi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] również struktury.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>Zagnieżdżone przekazywanie  
 Czasami nie jest to możliwe, całkowicie blokuje się [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Rozważmy <xref:System.Windows.MessageBox.Show%2A> metody <xref:System.Windows.MessageBox> klasy. <xref:System.Windows.MessageBox.Show%2A> nie zwraca, dopóki użytkownik kliknie przycisk OK. Jednak to utworzyć okno które musi mieć pętli komunikatów, aby być interaktywna. Gdy firma Microsoft oczekuje na użytkownika, kliknij przycisk OK, oryginalnym okna aplikacji nie odpowiada na dane wejściowe użytkownika. Jednak nadal przetwarzać komunikaty dotyczące malowania. Okno oryginalne odrysowuje samego w sobie podczas wchodzi w zakres i reakcja.  
  
 ![Zrzut ekranu, który pokazuje komunikat MessageBox, za pomocą przycisku OK](./media/threading-model/threading-message-loop.png)  
  
 Niektóre wątek musi być odpowiedzialnym za okno komunikatu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można utworzyć nowego wątku, tylko dla okno komunikatu, ale ten wątek nie będzie można malować wyłączone elementy w oknie oryginalnego (należy pamiętać o wcześniej dyskusji wzajemne wykluczenie). Zamiast tego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa komunikatu zagnieżdżonych, systemu przetwarzania. <xref:System.Windows.Threading.Dispatcher> Klasa zawiera specjalne metodę o nazwie <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, który następnie zapisuje bieżący punkt wykonania aplikacji rozpocznie się nowych pętli komunikatów. Po zakończeniu pętli komunikatów zagnieżdżonych, wykonanie zostanie wznowione po oryginalnej <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> wywołania.  
  
 W tym przypadku <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> utrzymuje kontekst program w wywołaniu do <xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>, i jest on uruchamiany pętlę komunikatów repaint okna tła i obsługiwać dane wejściowe okno komunikatu. Gdy użytkownik kliknie przycisk OK i czyści okno podręczne, zamyka zagnieżdżonej pętli i sterowania wznawia działanie po wywołaniu <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Stare zdarzenia trasowanego  
 System zdarzenia trasowanego w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] powiadamia całego drzewa, gdy zdarzenia są wywoływane.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Po naciśnięciu lewego przycisku myszy na wielokropku przy `handler2` jest wykonywany. Po `handler2` zostanie zakończone, zdarzenie jest przekazywany do <xref:System.Windows.Controls.Canvas> obiektu, który używa `handler1` go przetworzyć. Dzieje się tak tylko wtedy, gdy `handler2` jest nie zostały jawnie znak z obiektem zdarzenia jako obsługiwane.  
  
 Istnieje możliwość, że `handler2` zajmie się dużym stopniem czas przetwarzania tego zdarzenia. `handler2` może używać <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> pętlę komunikatów zagnieżdżonych, która nie zwraca godziny rozpoczęcia. Jeśli `handler2` nie nie znacznika zdarzenia jako obsłużony, gdy jest to pętli komunikatów ukończenia, zdarzenie jest przekazywany górę drzewa, mimo że jest to bardzo starych.  
  
### <a name="reentrancy-and-locking"></a>Wielobieżność i blokowania  
 Mechanizm blokowania [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nie zachowywać się dokładnie tak jak jedną może imagine; można oczekiwać, że wątek całkowicie zaprzestania operacji podczas żądania blokady. W rzeczywistości wątku w dalszym ciągu odbierania i przetwarzania wiadomości o wysokim priorytecie. Pomaga to zapobiegać zakleszczenia i wprowadź minimalny zestaw dynamiczny interfejsów, ale wprowadza możliwość subtelnych błędów.  Większość czasu nie muszą nic wiedzieć o tym, ale w bardzo rzadkich przypadkach (zwykle obejmujące [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] komunikatów okien lub składniki COM STA) może to być warte wiedzy.  
  
 Większość interfejsów nie są tworzone za pomocą bezpieczeństwo wątków, pamiętając, ponieważ deweloperzy pracują przy założeniu, że [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nigdy nie odbywa się przez więcej niż jeden wątek. W tym przypadku jeden wątek mogą wprowadzać zmiany środowiska w nieoczekiwanym czasie, powodując tych źle wpływ, <xref:System.Windows.Threading.DispatcherObject> wzajemne wykluczenie mechanizm powinien rozwiązać. Należy wziąć pod uwagę poniższym pseudokodzie:  
  
 ![Diagram pokazujący wątkowości współużytkowania wątkowości. ](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")  
  
 W większości przypadków to właściwe, ale istnieją momenty, w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gdzie takie nieoczekiwany współużytkowania wątkowości naprawdę może powodować problemy. Tak, w określonym czasie klucza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wywołania <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, który zmienia instrukcji lock dla tego wątku użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wielobieżność bez blokady, zamiast zwykłego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] blokady.  
  
 Dlaczego czy [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zespołu, wybierz ten problem? Należało wykonać za pomocą obiektów COM, STA i wątku finalizacji. Gdy obiekt jest bezużyteczne, jego `Finalize` metoda jest uruchomiona w wątku finalizatora dedykowanych nie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. I tam jest problem, ponieważ obiekt COM STA, który został utworzony na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku, tylko może zostać usunięty w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Jest odpowiednikiem <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (w tym przypadku przy użyciu firmy Win32 `SendMessage`). Ale w tym przypadku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku jest zajęty i został zablokowany wątek finalizatora obiektu COM STA nie można usunąć, co powoduje utworzenie przeciek pamięci poważne. Więc [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zespołu wprowadzone trudne wywołanie się blokad, które działają w ten sposób wykonują.  
  
 Zadanie dotyczące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest unikanie nieoczekiwanych wielobieżność bez ponownym wprowadzeniem przeciek pamięci, dlatego firma Microsoft nie blokują współużytkowania wątkowości w dowolnym miejscu.  
  
## <a name="see-also"></a>Zobacz także

- [Aplikacja jednowątkowa z przykładem obliczania długotrwałych](https://go.microsoft.com/fwlink/?LinkID=160038)
