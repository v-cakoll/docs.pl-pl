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
ms.openlocfilehash: 15115cc0ed14cb5605100ebe47abd5cd4dc02ec0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549506"
---
# <a name="threading-model"></a>Model wątkowości
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Służy do zapisywania deweloperzy trudności z wątków. W rezultacie, większość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programiści nie muszą zapisu interfejs, który korzysta z więcej niż jeden wątek. Ponieważ programy wielowątkowe są złożone i trudne do debugowania, ich należy unikać gdy istnieją jednowątkowe rozwiązania.  
  
 Niezależnie od tego, jak również zaprojektowana, jednak nie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] framework kiedykolwiek będą mogli stanowią rozwiązanie jednowątkowe dla każdego rodzaju problem. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pochodzi zamknięcia, ale nadal istnieją sytuacje, w którym wiele wątków poprawy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] wydajności czasu odpowiedzi lub aplikacji. Po omówieniu niektórych materiałów tła, w tym dokumencie Eksploruje niektóre z tych sytuacji i stwierdza, z omówieniem niektórych szczegółów niskiego poziomu.  
  

  
> [!NOTE]
>  W tym temacie omówiono wątkowość przy użyciu <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metodę wywołania asynchronicznego. Asynchroniczne wywołania można również ustawić, wywołując <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> metodę, która zająć <xref:System.Action> lub <xref:System.Func%601> jako parametr.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> Metoda zwraca <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>, który ma <xref:System.Windows.Threading.DispatcherOperation.Task%2A> właściwości. Można użyć `await` — słowo kluczowe przy użyciu jednej <xref:System.Windows.Threading.DispatcherOperation> lub skojarzony <xref:System.Threading.Tasks.Task>. Jeśli musisz poczekać synchronicznie <xref:System.Threading.Tasks.Task> zwróconego przez <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>, wywołaj <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> — metoda rozszerzenia.  Wywoływanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> będzie doprowadzić do zakleszczenia. Aby uzyskać więcej informacji o korzystaniu z <xref:System.Threading.Tasks.Task> do wykonywania asynchronicznych operacji, zobacz równoległość zadań.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A> Metoda ma również przeciążeń, które przyjmują <xref:System.Action> lub <xref:System.Func%601> jako parametr.  Można użyć <xref:System.Windows.Threading.Dispatcher.Invoke%2A> wywołuje metodę, aby wprowadzić synchroniczne przez przekazywanie delegata, <xref:System.Action> lub <xref:System.Func%601>.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Omówienie i Dyspozytor  
 Zazwyczaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje są uruchamiane z dwoma wątkami: jeden do obsługi renderowania i drugi dla zarządzania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Wątek renderowania skutecznie uruchamia ukryte w tle podczas [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku odbiera dane wejściowe, obsługuje zdarzenia rysują ekranu i uruchamia kod aplikacji. Większość aplikacji używa pojedynczego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku, chociaż w niektórych sytuacjach warto użyć kilku. Omówiono to przykład później.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Kolejek wątku roboczego elementy wewnątrz obiektu o nazwie <xref:System.Windows.Threading.Dispatcher>. <xref:System.Windows.Threading.Dispatcher> Wybiera elementów roboczych w pierwszej kolejności i uruchamia do ukończenia każdej z nich.  Każdy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku musi mieć co najmniej jeden <xref:System.Windows.Threading.Dispatcher>i każdego <xref:System.Windows.Threading.Dispatcher> można wykonać elementów roboczych w dokładnie jeden wątek.  
  
 Do tworzenia aplikacji reakcji i przyjazny dla użytkownika jest aby zmaksymalizować <xref:System.Windows.Threading.Dispatcher> przepływność przy zachowaniu małych elementów roboczych. Nigdy nie elementów w ten sposób uzyskać starych oczekuje w <xref:System.Windows.Threading.Dispatcher> kolejki oczekiwanie na przetwarzanie. Wszelkie odczytywane opóźnienia między dane wejściowe i odpowiedzi może frustrować użytkownika.  
  
 Jak to [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji powinien obsługiwać operacje duży? Co zrobić, jeśli kod obejmuje dużą obliczeń lub wymaga kwerendy bazy danych na niektórych serwera zdalnego? Zazwyczaj odpowiedzi jest duży operację w oddzielnym wątku, pozostawiając [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zająć się zazwyczaj do elementów w wątku <xref:System.Windows.Threading.Dispatcher> kolejki. Po zakończeniu operacji duży może raportować jego wynik do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku do wyświetlenia.  
  
 W przeszłości [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] umożliwia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów, aby były dostępne tylko dla wątku, który je utworzył. Oznacza to, że wątku w tle odpowiedzialnym za niektóre długotrwałe zadanie nie można zaktualizować pola tekstowego po zakończeniu. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Dzieje się tak, aby zapewnić integralność [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] składników. Pole listy może wyglądać dziwne, jeśli jego zawartość zostały zaktualizowane przez wątek w tle podczas rysowania.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wbudowane wzajemne wykluczenie mechanizm, który wymusza koordynacja. Większość klas w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pochodzi od <xref:System.Windows.Threading.DispatcherObject>. W konstrukcji <xref:System.Windows.Threading.DispatcherObject> zawiera odwołanie do <xref:System.Windows.Threading.Dispatcher> połączone z aktualnie uruchomiony. W efekcie <xref:System.Windows.Threading.DispatcherObject> kojarzy z wątku, który go utworzył. Podczas wykonywania programu <xref:System.Windows.Threading.DispatcherObject> można wywołać jej publicznego <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> metody. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> sprawdza, czy <xref:System.Windows.Threading.Dispatcher> skojarzone z bieżącym wątku i porównuje go do <xref:System.Windows.Threading.Dispatcher> odwołanie podczas konstruowania przechowywane. Jeśli nie są zgodne, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> zgłasza wyjątek. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> jest przeznaczona do wywoływania na początku każdej metody należących do <xref:System.Windows.Threading.DispatcherObject>.  
  
 Jeśli tylko jeden wątek można zmodyfikować [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], wątki w tle interakcji z użytkownikiem? Poproś wątku w tle [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku do wykonania operacji w jej imieniu. Robi to poprzez zarejestrowanie elementu roboczego z <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. <xref:System.Windows.Threading.Dispatcher> Klasy udostępnia dwie metody rejestrowania elementów roboczych: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> i <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Obie metody zaplanować delegata do wykonania. <xref:System.Windows.Threading.Dispatcher.Invoke%2A> to wywołanie synchroniczne — to znaczy nie zwraca do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku rzeczywiście ukończeniem wykonywania delegata. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> jest asynchroniczne i zwraca natychmiast.  
  
 <xref:System.Windows.Threading.Dispatcher> Porządkuje elementy w swojej kolejki według priorytetu. Istnieją dziesięć poziomy, które można określić podczas dodawania elementu <xref:System.Windows.Threading.Dispatcher> kolejki. Priorytety te są obsługiwane w <xref:System.Windows.Threading.DispatcherPriority> wyliczenia. Szczegółowe informacje na temat <xref:System.Windows.Threading.DispatcherPriority> poziomy znajdują się w [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] dokumentacji.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Wątki w działaniu: przykłady  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Jednowątkowe aplikacja o obliczenie długotrwałe  
 Większość [!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)] poświęcać dużo czasu bezczynności podczas oczekiwania na zdarzenia, które są generowane w odpowiedzi na interakcję użytkownika. Dokładne programowania tego czasu bezczynności można konstruktywnie, bez wywierania wpływu na czas odpowiedzi z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Model wątkowości nie zezwala na dane wejściowe, aby przerwać operację wykonywane w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Oznacza to, należy upewnić się powrócić do <xref:System.Windows.Threading.Dispatcher> okresowo do przetworzenia oczekujących zdarzeń wejściowych, zanim uzyskają przestarzałe.  
  
 Rozważmy następujący przykład:  
  
 ![Zrzut ekranu przedstawiający liczb pierwszych](../../../../docs/framework/wpf/advanced/media/threadingprimenumberscreenshot.PNG "ThreadingPrimeNumberScreenShot")  
  
 Ta prosta aplikacja większej liczby z trzech, wyszukiwanie liczb pierwszych. Po kliknięciu przez użytkownika **Start** przycisku, wyszukiwanie rozpoczyna się. Gdy wyszukiwany Zapora aktualizacje interfejsu użytkownika z jego odnajdywania. W dowolnym momencie użytkownik może zatrzymać wyszukiwania.  
  
 Chociaż tyle prosta, liczba pierwsza wyszukiwania można umieścić w nieskończoność, który przedstawia niektóre problemy.  Firma Microsoft obsługi całego wyszukiwania wewnątrz obsługi zdarzenia kliknięcia przycisku, firma Microsoft może nigdy nie udzielają żadnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku możliwość obsługi innych zdarzeń. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Nie może odpowiadać na dane wejściowe lub proces wiadomości. Będzie on nigdy nie odświeżenia i nigdy nie odpowiadanie na kliknięcia przycisku.  
  
 Firma Microsoft może przeprowadzić wyszukiwania liczba pierwsza w oddzielnym wątku, ale będzie trzeba postępowania w przypadku problemów z synchronizacją. Jednowątkowe podejście możemy bezpośrednio zaktualizować etykietę, którą zawiera największy priorytetowe znaleziono.  
  
 Jeśli zadanie obliczeń w partiach łatwych do możemy podzielić, możemy okresowo powrócić do <xref:System.Windows.Threading.Dispatcher> i przetwarzania zdarzeń. Firma Microsoft może zapewnić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] możliwość odświeżenia i przetwarzania danych wejściowych.  
  
 Najlepszym sposobem podział czasu przetwarzania między obliczania i obsługa zdarzeń ma zarządzać obliczeń z <xref:System.Windows.Threading.Dispatcher>. Za pomocą <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody, można zaplanować liczba pierwsza kontroli w taki sam kolejki, która [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zdarzenia są pobierane z. W naszym przykładzie zaplanować tylko sprawdzanie jeden numer prime naraz. Po zakończeniu wyboru liczba pierwsza zaplanować dalej wyboru natychmiast. Ten test tylko po będzie kontynuowane do czasu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zdarzeń zostały obsłużone.  
  
 ![Ilustracja przedstawiająca kolejkę dyspozytora](../../../../docs/framework/wpf/advanced/media/threadingdispatcherqueue.PNG "ThreadingDispatcherQueue")  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)] wykonuje sprawdzanie pisowni przy użyciu tego mechanizmu. Sprawdzanie pisowni jest wykonywane w tle, na podstawie czasu bezczynności [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Spójrzmy na kod.  
  
 W poniższym przykładzie przedstawiono XAML, która tworzy interfejs użytkownika.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 W poniższym przykładzie przedstawiono CodeBehind.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 W poniższym przykładzie pokazano programu obsługi zdarzeń dla <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Oprócz Aktualizowanie tekstu w <xref:System.Windows.Controls.Button>, ten program obsługi jest odpowiedzialny za planowanie pierwszy wyboru liczba pierwsza przez dodanie pełnomocnika, aby <xref:System.Windows.Threading.Dispatcher> kolejki. Pewnym czasie, po zakończeniu pracy, ten program obsługi zdarzeń <xref:System.Windows.Threading.Dispatcher> wybierze ten delegat do wykonania.  
  
 Jak wspomniano wcześniej, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> jest <xref:System.Windows.Threading.Dispatcher> Członkowskie zaplanowano delegata do wykonania. W takim przypadku wybieramy opcję <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> priorytet. <xref:System.Windows.Threading.Dispatcher> Wykona ten delegat tylko wtedy, gdy Brak ważnych zdarzeń do przetwarzania. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] czas odpowiedzi jest ważniejsze niż liczba sprawdzania. Możemy również przekazać nowe delegowanie reprezentujący sprawdzanie numer procedury.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Ta metoda sprawdza, czy dalej nieparzystą liczbą jest pierwsze. Jeśli tak jest, zapisują, metoda bezpośrednio aktualizacji `bigPrime` <xref:System.Windows.Controls.TextBlock> do uwzględnienia jego odnajdywania. Firma Microsoft może to zrobić, ponieważ obliczenie jest wykonywana w tym samym wątku, który został użyty do utworzenia składnika. Firma Microsoft wybierze oddzielnym wątku na potrzeby obliczania, firma Microsoft będzie musiał używać bardziej skomplikowanych mechanizmu synchronizacji i wykonać aktualizację w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Zostanie przedstawiony obok tej sytuacji.  
  
 Kod źródłowy pełną dla tego przykładu, aby zapoznać [aplikacji Single-Threaded długotrwałe obliczania próbki](http://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Obsługa operacji blokowania z wątku w tle  
 Obsługa operacji blokowania w graficznym aplikacji może być trudne. Nie chcemy wywoływać metod blokowania z obsługi zdarzeń, ponieważ aplikacja pojawi się zawiesza. Możemy użyć oddzielnym wątku do obsługi tych operacji, ale gdy skończymy, konieczne jest synchronizowana [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku, ponieważ firma Microsoft nie można bezpośrednio modyfikować [!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)] z naszych wątku roboczego. Możemy użyć <xref:System.Windows.Threading.Dispatcher.Invoke%2A> lub <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> do wstawienia delegatów w <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Po pewnym czasie zostaną wykonane tych obiektów delegowanych z uprawnień do modyfikowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów.  
  
 W tym przykładzie mamy naśladować wywołanie procedury zdalnej, która pobiera prognozie pogody. Używamy oddzielnym wątku do wykonania tego wywołania, a zaplanować metody aktualizacji w <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku, gdy jest gotowe.  
  
 ![Zrzut ekranu interfejsu użytkownika pogodowe](../../../../docs/framework/wpf/advanced/media/threadingweatheruiscreenshot.PNG "ThreadingWeatherUIScreenShot")  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Poniżej przedstawiono niektóre szczegóły można zauważyć.  
  
-   Tworzenie obsługi przycisku  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Po kliknięciu przycisku nasz Wyświetl rysunek zegara i uruchomić go animacji. Możemy wyłączyć przycisku. Firma Microsoft wywołania `FetchWeatherFromServer` metoda nowego wątku, a następnie usuniemy zwracany, dzięki czemu <xref:System.Windows.Threading.Dispatcher> przetwarzania zdarzeń podczas oczekiwania na zbieranie prognozie pogody.  
  
-   Pobieranie pogody  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Aby zachować proste rzeczy, nie faktycznie mamy sieci kodu w tym przykładzie. Zamiast tego firma Microsoft symulowania opóźnienia dostępu do sieci przez umieszczenie naszego nowego wątku w stan uśpienia przez cztery sekundy. W tej chwili oryginalnej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku jest nadal uruchomiona i reagowanie na zdarzenia. Pokaż, firma Microsoft już pozostanie uruchomiona Animacja i Minimalizuj i zmaksymalizować przycisków również kontynuować pracę.  
  
 Po zakończeniu opóźnienie, losowo Wybraliśmy naszych prognozie pogody, nadszedł czas na raportowane [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Firma Microsoft w tym celu planowania wywołanie `UpdateUserInterface` w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku przy użyciu tego wątku <xref:System.Windows.Threading.Dispatcher>. Ciąg opisujący pogody do wywołania tej metody zaplanowane jest przekazywana.  
  
-   Aktualizowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Gdy <xref:System.Windows.Threading.Dispatcher> w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku jest czas, wykonywania zaplanowanych wywołanie `UpdateUserInterface`. Ta metoda zatrzymuje animacji zegara i wybiera obrazu do opisywania pogody. On wyświetla ten obraz i przywraca przycisk "pobieranie forecast".  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Wiele okien, wiele wątków  
 Niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje wymagają wielu okien najwyższego poziomu. Dopuszczalne dokładnie jeden wątek są /<xref:System.Windows.Threading.Dispatcher> kombinacja do zarządzania wiele okien, ale czasami kilka wątków czy lepiej zadania. Jest to szczególnie istotne, jeśli wysłanej co systemu windows będzie zająć całych wątku.  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Eksplorator działa w ten sposób. Każde nowe okno Eksploratora należy do oryginalnej proces, ale jest tworzony poza kontrolą niezależnie od wątku.  
  
 Za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> kontroli, można wyświetlić strony sieci Web. Można łatwo utworzyć prostą [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] podstaw. Możemy zaczynać ważna cecha: możliwość Otwórz nowe okno Eksploratora. Gdy użytkownik kliknie przycisk "nowe okno" przycisku, możemy uruchomić kopię naszych okna w oddzielnym wątku. W ten sposób długotrwałe lub blokowania operacji w jednym z systemu windows nie będzie blokować wszystkich innych okien.  
  
 W rzeczywistości modelu przeglądarki sieci Web ma własną skomplikowane modelu wątkowości. Firma Microsoft został wybrany, ponieważ powinna być znana większości czytelników.  
  
 Poniższy przykład przedstawia kod.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Następujące segmenty wątków tego kodu jest najbardziej interesujące nam w tym kontekście:  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Ta metoda jest wywoływana, gdy "nowe okno" przycisk zostanie kliknięty. Tworzy nowego wątku i uruchamia go asynchronicznie.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Ta metoda jest punkt początkowy dla nowego wątku. Utworzymy nowe okno pod kontrolą tego wątku. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] automatycznie tworzy nową <xref:System.Windows.Threading.Dispatcher> do zarządzania nowego wątku. Wszystkie mamy zrobić, aby wyświetlić okno funkcjonalności jest uruchomienie <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Szczegółowe informacje techniczne i Stumbling punkty  
  
### <a name="writing-components-using-threading"></a>Składniki zapisywania za pomocą wątków  
 Przewodnik dewelopera programu Microsoft .NET Framework w tym artykule opisano szablon dla jak składnika mogą uwidaczniać asynchroniczne zachowanie klientom (zobacz [oparty na zdarzeniach asynchroniczny wzorzec — Przegląd](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Na przykład, załóżmy, że trzeba pakietu `FetchWeatherFromServer` metody do wielokrotnego użytku, które składnika. Następujące standardowy wzorzec Microsoft .NET Framework to może wyglądać poniżej.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync` użyje jednej z metod opisanych wcześniej, takich jak tworzenie wątku w tle, które wykonają tę pracę asynchronicznie, nie blokuje wątek wywołujący.  
  
 Jedną z najważniejszych części tego wzorca wywołuje *MethodName* `Completed` metody w tym samym wątku, który wywołał *MethodName* `Async` rozpoczynać się od metody. Użytkownik może to zrobić przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dość łatwe, przechowując <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>—, ale następnie składnika, które mogą być używane tylko w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, nie znajduje się w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] programów.  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext> Klasy adresów tę potrzebę — Pomyśl o tym jako uproszczonej wersji <xref:System.Windows.Threading.Dispatcher> który współpracuje z innymi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] również struktury.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>Zagnieżdżone przekazywania  
 Czasami nie jest to wykonalne całkowicie blokowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. Zastanówmy <xref:System.Windows.MessageBox.Show%2A> metody <xref:System.Windows.MessageBox> klasy. <xref:System.Windows.MessageBox.Show%2A> nie zwraca, dopóki użytkownik kliknie przycisk OK. Utworzone jednak okna, którą muszą dysponować Pętla wiadomości, aby interakcyjne. Gdy firma Microsoft oczekujące dla użytkownika kliknij przycisk OK, oryginalnego okna aplikacji nie odpowiada na dane wejściowe użytkownika. Jednakże nadal przetwarzać komunikaty dotyczące malowania. Oryginalnego okna ponownie rysuje samego w sobie podczas objętych usługą i ujawniony.  
  
 ![Element MessageBox z przycisk "OK"](../../../../docs/framework/wpf/advanced/media/threadingnestedpumping.png "ThreadingNestedPumping")  
  
 Niektóre wątek musi być odpowiedzialnym za okno komunikatu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można utworzyć nowego wątku do okno komunikatu, ale ten wątek można malować wyłączonych elementów w oknie oryginalnego (należy pamiętać o wcześniejszych omówienie wzajemne wykluczenie). Zamiast tego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa zagnieżdżonych komunikat przetwarzania systemu. <xref:System.Windows.Threading.Dispatcher> Klasa zawiera specjalne metody o nazwie <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, bieżącego punktu wykonywania aplikacji której przechowywana jest następnie rozpoczyna się nowych pętli komunikatów. Po zakończeniu pracy pętli komunikatów zagnieżdżonych wykonywania wznawia działanie po oryginalnej <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> wywołania.  
  
 W takim przypadku <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> przechowuje kontekście program w wywołaniu <xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>, i jest on uruchamiany nowy pętli komunikatów do odświeżenia okna tła i obsługi danych wejściowych okno komunikatu. Gdy użytkownik kliknie przycisk OK i czyści okno podręczne, zamyka zagnieżdżonych pętli i sterowania zostanie wznowione po wywołaniu <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Zdarzenia rozsyłane przestarzały  
 System kierowanego zdarzenia w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] powiadamia całego drzewa w momencie pojawienia się zdarzenia.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Po naciśnięciu lewego przycisku myszy nad elipsy, `handler2` jest wykonywana. Po `handler2` zakończeniu zdarzenia są przekazywane do wzdłuż <xref:System.Windows.Controls.Canvas> obiektu, który używa `handler1` go przetworzyć. Dzieje się tak tylko wtedy, gdy `handler2` jest nie jawnie znacznik obiekt zdarzenia jako obsłużone.  
  
 Istnieje możliwość, że `handler2` potrwa dużą ilość czasu na przetwarzanie tego zdarzenia. `handler2` może używać <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> pętli zagnieżdżonych wiadomości, która nie zwraca godziny rozpoczęcia. Jeśli `handler2` nie nie znacznika zdarzenia jako obsługiwany, gdy ta pętla wiadomości jest zakończenie, zdarzenie jest przekazywany górę drzewa, mimo że jest to bardzo starych.  
  
### <a name="reentrancy-and-locking"></a>Wielobieżność i blokowanie  
 Mechanizm blokowania [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nie zachowywać się dokładnie jako jeden oczywiście; jedną może spodziewać się wątek całkowicie przestaną operacji podczas żądania blokady. W rzeczywistości wątku w dalszym ciągu otrzymywać i przetwarzania komunikatów o wysokim priorytecie. Pomaga to zapobiec zakleszczenie i utworzyć co najmniej odpowiadać interfejsów, jednak wprowadza możliwość subtelnych błędów.  Większość czasu nie trzeba niczego wiedzieć o tym, ale w rzadkich przypadkach (zwykle obejmujące [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] komunikatów okien i składników COM STA) może to być wartość uzyskiwanie informacji.  
  
 Większość interfejsów nie są tworzone za bezpieczeństwo wątków na uwadze, ponieważ deweloperzy pracować przy założeniu, że [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nigdy nie jest dostępny więcej niż jednego wątku. W tym przypadku pojedynczego wątku mogą mieć wpływ zmiany w nieoczekiwanym czasie, powodując tych źle wpływ który <xref:System.Windows.Threading.DispatcherObject> mechanizmu wzajemne wykluczenie powinien rozwiązać. Należy wziąć pod uwagę następujące pseudocode:  
  
 ![Diagram współużytkowania wątkowości](../../../../docs/framework/wpf/advanced/media/threadingreentrancy.png "ThreadingReentrancy")  
  
 W większości przypadków, który jest co, ale czasami w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gdzie takie nieoczekiwane ponowne wejście naprawdę mogą powodować problemy. Tak, w pewnych porach klucza, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wywołania <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, który zmienia instrukcji lock dla tego wątku do użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bez ponownego rozpoczęcia blokady, zamiast standardowego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] blokady.  
  
 Dlaczego tak czy [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zespołu wybierz takie zachowanie? Miał z obiektami COM STA i finalizacji wątku. Gdy obiekt jest bezużytecznych, jego `Finalize` metody jest uruchamiane na wątek finalizatora dedykowanych nie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. I tam leży problem, ponieważ obiekt COM STA, który został utworzony na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku mogą zostać usunięte tylko na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Jest odpowiednikiem <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (w tym przypadku przy użyciu jego Win32 `SendMessage`). Jeśli jednak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] wątku jest zajęty, został wstrzymany wątku finalizatora i obiektu COM STA nie można usunąć, co powoduje przeciek pamięci poważne. Dlatego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zespołu wprowadzone trudnych wywołania blokad działa w sposób, aby je.  
  
 Zadanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest uniknięcie nieoczekiwany wielobieżność bez ponownym wprowadzeniem przeciek pamięci, dlatego nie zostanie zablokowany wielobieżność wszędzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Jednowątkowe aplikacji długotrwałe obliczania próbki](http://go.microsoft.com/fwlink/?LinkID=160038)
