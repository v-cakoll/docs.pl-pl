---
title: 'Przewodnik: wdrażanie formularza korzystającego z operacji w tle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
ms.openlocfilehash: 6399fb853162174895d892399fd3eb5226101515
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343405"
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>Przewodnik: wdrażanie formularza korzystającego z operacji w tle
Jeśli operacja, która będzie zająć dużo czasu, i nie ma interfejsu użytkownika (UI) przestanie odpowiadać lub "zawiesza się," można użyć <xref:System.ComponentModel.BackgroundWorker> klasy do wykonywania operacji na inny wątek.  
  
 W tym instruktażu przedstawiono sposób użycia <xref:System.ComponentModel.BackgroundWorker> klasy do wykonywania czasochłonnych obliczeń "w"tle, podczas gdy interfejs użytkownika reaguje.  Po zakończeniu wykonywania masz aplikację, która oblicza numery Fibonacci asynchronicznie. Mimo że obliczeniowej dużą liczbą Fibonacci może potrwać zauważalne ilość czasu, przez to opóźnienie nie zostanie przerwana głównego wątku interfejsu użytkownika, a formularz będzie odpowiadać podczas obliczania.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie aplikacji z systemem Windows  
  
-   Tworzenie <xref:System.ComponentModel.BackgroundWorker> w formularzu  
  
-   Dodawanie obsługi zdarzeń asynchronicznych  
  
-   Dodawanie raportowania postępu i obsługę anulowania  
  
 Aby uzyskać pełną listę kod używany w tym przykładzie, zobacz [jak: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a>Aby utworzyć formularza korzystającego z operacji w tle  
  
1. Utwórz projekt aplikacji systemu Windows o nazwie `BackgroundWorkerExample` (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1** i wybierz **Zmień nazwę** z menu skrótów. Zmień nazwę pliku, aby `FibonacciCalculator`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu '`Form1`".  
  
3. Przeciągnij <xref:System.Windows.Forms.NumericUpDown> z kontrolować **przybornika** na formularz. Ustaw <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> właściwości `1` i <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> właściwość `91`.  
  
4. Dodaj dwie <xref:System.Windows.Forms.Button> formantów do formularza.  
  
5. Zmień nazwę pierwszego <xref:System.Windows.Forms.Button> kontroli `startAsyncButton` i ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwość `Start Async`. Zmień nazwę drugiej <xref:System.Windows.Forms.Button> kontroli `cancelAsyncButton`i ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwość `Cancel Async`. Ustaw jego <xref:System.Windows.Forms.Control.Enabled%2A> właściwość `false`.  
  
6. Utwórz procedurę obsługi zdarzeń dla obu <xref:System.Windows.Forms.Button> kontrolek <xref:System.Windows.Forms.Control.Click> zdarzenia. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń za pomocą projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).  
  
7. Przeciągnij <xref:System.Windows.Forms.Label> z kontrolować **przybornika** na formularz i zmień jego nazwę `resultLabel`.  
  
8. Przeciągnij <xref:System.Windows.Forms.ProgressBar> z kontrolować **przybornika** na formularz.  
  
## <a name="creating-a-backgroundworker-in-your-form"></a>Tworzenie BackgroundWorker w formularzu  
 Możesz utworzyć <xref:System.ComponentModel.BackgroundWorker> dla operacji asynchronicznej przy użyciu **Windows** **projektanta formularzy**.  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a>Aby utworzyć BackgroundWorker za pomocą projektanta  
  
-   Z **składniki** karcie **przybornika**, przeciągnij <xref:System.ComponentModel.BackgroundWorker> na formularz.  
  
## <a name="adding-asynchronous-event-handlers"></a>Dodawanie obsługi zdarzeń asynchronicznych  
 Teraz można przystąpić do dodania obsługi zdarzeń dla <xref:System.ComponentModel.BackgroundWorker> zdarzeń asynchronicznych składnika. Czasochłonne operacji, która jest uruchamiana w tle, który oblicza Fibonacci liczb, jest wywoływana za pomocą jednej z tych programów obsługi zdarzeń.  
  
#### <a name="to-implement-asynchronous-event-handlers"></a>Aby zaimplementować procedury obsługi zdarzeń asynchronicznych  
  
1. W **właściwości** oknie z <xref:System.ComponentModel.BackgroundWorker> składnika wciąż zaznaczone, kliknij przycisk **zdarzenia** przycisku. Kliknij dwukrotnie <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń, aby utworzyć procedury obsługi zdarzeń. Aby uzyskać więcej informacji na temat używania programów obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń za pomocą projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).  
  
2. Utwórz nową metodę o nazwie `ComputeFibonacci`, w formularzu. Ta metoda wykonuje faktyczną pracę, a zostanie ona uruchomiona w tle. Ten kod przedstawia implementację cyklicznego algorytmu Fibonacci, który jest szczególnie nieefektywne, biorąc wykładniczo dłużej, aby uzyskać większą liczbą. Służy w tym miejscu w celach ilustracyjnych, aby pokazać operacji, która może prowadzić do opóźnień w aplikacji.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3. W <xref:System.ComponentModel.BackgroundWorker.DoWork> procedura obsługi zdarzeń, dodaj wywołanie do `ComputeFibonacci` metody. Wykonaj pierwszy parametr `ComputeFibonacci` z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs>. <xref:System.ComponentModel.BackgroundWorker> i <xref:System.ComponentModel.DoWorkEventArgs> parametry będzie później używane dla raportowania postępu i anulowania obsługi. Przypisz wartość zwrotną z elementu `ComputeFibonacci` do <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs>. Ten wynik będzie dostępny dla <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BackgroundWorker.DoWork> Program obsługi zdarzeń nie odwołuje się `backgroundWorker1` wystąpienie zmiennej bezpośrednio, jak to będzie sprzęgnięcie ta procedura obsługi zdarzeń do określonego wystąpienia <xref:System.ComponentModel.BackgroundWorker>. Zamiast tego odwołania do <xref:System.ComponentModel.BackgroundWorker> , to zgłoszone zdarzenie jest przywracany z `sender` parametru. Jest to ważne, gdy formularz udostępnia więcej niż jedną <xref:System.ComponentModel.BackgroundWorker>. Jest również pamiętać, aby nie modyfikować żadnych obiektów interfejsu użytkownika w Twojej <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń. Zamiast tego komunikują się interfejs użytkownika za pośrednictwem <xref:System.ComponentModel.BackgroundWorker> zdarzenia.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4. W `startAsyncButton` kontrolki <xref:System.Windows.Forms.Control.Click> procedura obsługi zdarzeń, Dodaj kod, który rozpoczyna operację asynchroniczną.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5. W <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> procedura obsługi zdarzeń, przypisz wynik obliczenia `resultLabel` kontroli.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a>Dodawanie raportowania postępu i obsługę anulowania  
 Operacje asynchroniczne, które będzie trwać często jest pożądane, aby raport postęp dla użytkownika, aby umożliwić użytkownikowi anulować operację. <xref:System.ComponentModel.BackgroundWorker> Klasa udostępnia zdarzenia, które pozwala na publikowanie postępu jako swoje przychody operacji tła. Zapewnia także flagę, która umożliwia wywołanie w celu wykrywania kodu procesu roboczego <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> i przerwać samej sobie.  
  
#### <a name="to-implement-progress-reporting"></a>Aby zaimplementować raportowania postępu  
  
1. W **właściwości**, wybierz `backgroundWorker1`. Ustaw <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości `true`.  
  
2. Zadeklaruj dwie zmienne w `FibonacciCalculator` formularza. Będą one używane, w celu śledzenia postępu.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3. Dodawanie obsługi zdarzeń dla <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń. W <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> programu obsługi zdarzeń, aktualizacja <xref:System.Windows.Forms.ProgressBar> z <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> właściwość <xref:System.ComponentModel.ProgressChangedEventArgs> parametru.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a>Aby zaimplementować obsługę anulowania  
  
1. W `cancelAsyncButton` kontrolki <xref:System.Windows.Forms.Control.Click> procedura obsługi zdarzeń, Dodaj kod, który anuluje operację asynchroniczną.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2. Poniższy kod fragmentów w `ComputeFibonacci` metoda raport postępu i pomoc techniczna anulowania.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można skompilować i uruchomić aplikacja Kalkulator Fibonacci.  
  
#### <a name="to-test-your-project"></a>Aby przetestować projekt  
  
-   Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     Obliczenie jest uruchomiona w tle, zobaczysz <xref:System.Windows.Forms.ProgressBar> Wyświetlanie postępu obliczeń w kierunku ukończenia. Możesz również anulować oczekujące operacje.  
  
     Dla małymi liczbami obliczenia powinny być bardzo szybko, ale w przypadku większych liczb, powinien zostać wyświetlony zauważalnego opóźnienia. Jeśli wprowadzisz wartość 30 lub większą, powinien zostać wyświetlony opóźnienie kilka sekund, w zależności od szybkości komputera. Dla wartości jest większa niż 40 może upłynąć minuty lub godziny na zakończenie obliczania. Kalkulator jest zajęty, przetwarzanie dużą liczbą Fibonacci, zwróć uwagę, czy można swobodnie poruszać się formularz, zminimalizować, maksymalizacji i nawet je zamknąć. Jest to spowodowane wątku interfejsu użytkownika głównego nie oczekuje na potrzeby obliczeń zakończyć.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, że udało Ci się wdrożyć formularz, który używa <xref:System.ComponentModel.BackgroundWorker> składnik do wykonywania obliczeń w tle, możesz zapoznać się z innych możliwości dla asynchronicznych operacji:  
  
-   Używanych jest wiele <xref:System.ComponentModel.BackgroundWorker> obiektów dla kilku operacji jednoczesnych.  
  
-   Do debugowania aplikacji wielowątkowych, zobacz [jak: Korzystanie z okna wątków](/visualstudio/debugger/how-to-use-the-threads-window).  
  
-   Implementowanie własnego składnika, który obsługuje model programowania asynchronicznego. Aby uzyskać więcej informacji, zobacz [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
    > [!CAUTION]
    >  Korzystając z wielowątkowością jakiegokolwiek rodzaju, możesz potencjalnie się narazić na bardzo poważne i złożone usterek. Zapoznaj się z [zarządzana wątkowość najlepsze](../../../standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem dowolne rozwiązanie, który używa wielowątkowości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- [Zarządzana wątkowość](../../../standard/threading/index.md)
- [Zarządzana wątkowość — najlepsze rozwiązania](../../../standard/threading/managed-threading-best-practices.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Instrukcje: implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Przewodnik: uruchamianie operacji w tle](walkthrough-running-an-operation-in-the-background.md)
- [BackgroundWorker — Składnik](backgroundworker-component.md)
