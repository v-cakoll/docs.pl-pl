---
title: "Wskazówki: wdrażanie formularza korzystającego z operacji w tle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89a352baed4d07c3c935643e9962131a20af2802
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>Wskazówki: wdrażanie formularza korzystającego z operacji w tle
Jeśli masz operacji potrwa długo, i nie ma interfejsu użytkownika (UI) przestanie odpowiadać lub "zawiesza się," można użyć <xref:System.ComponentModel.BackgroundWorker> klasy, aby wykonać tę operację w innym wątku.  
  
 W tym przewodniku przedstawiono sposób użycia <xref:System.ComponentModel.BackgroundWorker> klasę, aby wykonać obliczenia czasochłonne "w tle" podczas reaguje interfejsu użytkownika.  Po zakończeniu wykonywania masz aplikację, która oblicza numery Fibonacci asynchronicznie. Mimo że obliczeniowych dużą liczbą Fibonacci może zająć zauważalne ilość czasu, głównego wątku interfejsu użytkownika nie zostanie przerwana przez to opóźnienie i formularz będzie odpowiadać podczas obliczania.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie aplikacji systemu Windows  
  
-   Tworzenie <xref:System.ComponentModel.BackgroundWorker> w formularzu  
  
-   Dodawanie programów obsługi zdarzeń asynchroniczne  
  
-   Dodawanie raportowania postępu i obsługa anulowania  
  
 Aby uzyskać pełną listę kod używany w tym przykładzie, zobacz [porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a>Aby utworzyć formularza korzystającego z operacji w tle  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie `BackgroundWorkerExample`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1** i wybierz **zmienić** z menu skrótów. Zmień nazwę pliku, aby `FibonacciCalculator`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu '`Form1`".  
  
3.  Przeciągnij <xref:System.Windows.Forms.NumericUpDown> kontrolować z **przybornika** na formularzu. Ustaw <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> właściwości `1` i <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> właściwości `91`.  
  
4.  Dodaj dwa <xref:System.Windows.Forms.Button> formantów w formularzu.  
  
5.  Zmień nazwę pierwszego <xref:System.Windows.Forms.Button> kontroli `startAsyncButton` i ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości `Start Async`. Zmień nazwę drugiego <xref:System.Windows.Forms.Button> kontroli `cancelAsyncButton`i ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości `Cancel Async`. Ustaw jego <xref:System.Windows.Forms.Control.Enabled%2A> właściwości `false`.  
  
6.  Tworzenie procedury obsługi zdarzeń dla obu <xref:System.Windows.Forms.Button> formantów <xref:System.Windows.Forms.Control.Click> zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: tworzenie zdarzeń obsługi przy użyciu narzędzia Projektant](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
7.  Przeciągnij <xref:System.Windows.Forms.Label> kontrolować z **przybornika** na formularz i zmień jego nazwę `resultLabel`.  
  
8.  Przeciągnij <xref:System.Windows.Forms.ProgressBar> kontrolować z **przybornika** na formularzu.  
  
## <a name="creating-a-backgroundworker-in-your-form"></a>Tworzenie BackgroundWorker w formularzu  
 Można utworzyć <xref:System.ComponentModel.BackgroundWorker> do operacji asynchronicznej przy użyciu **Windows** **Projektant formularzy**.  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a>Aby utworzyć BackgroundWorker za pomocą narzędzia Projektant  
  
-   Z **składniki** karcie **przybornika**, przeciągnij <xref:System.ComponentModel.BackgroundWorker> na formularzu.  
  
## <a name="adding-asynchronous-event-handlers"></a>Dodawanie programów obsługi zdarzeń asynchroniczne  
 Teraz można przystąpić do dodawania obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker> zdarzenia asynchroniczne składnika. Czasochłonna operacja, które zostanie uruchomione w tle, który oblicza numery Fibonacci, jest wywoływana przez jeden z tych programów obsługi zdarzeń.  
  
#### <a name="to-implement-asynchronous-event-handlers"></a>Do wykonania procedury obsługi zdarzeń asynchroniczne  
  
1.  W **właściwości** okno z <xref:System.ComponentModel.BackgroundWorker> składnika jest wybrana, kliknij przycisk **zdarzenia** przycisku. Kliknij dwukrotnie <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenia można utworzyć procedury obsługi zdarzeń. Aby uzyskać więcej informacji o sposobie używania programów obsługi zdarzeń, zobacz [porady: tworzenie zdarzeń obsługi przy użyciu narzędzia Projektant](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
2.  Utworzenie nowej metody o nazwie `ComputeFibonacci`, w formularzu. Ta metoda wykonuje całą pracę i będzie działał w tle. Ten kod ilustruje cyklicznego wykonania algorytmu Fibonacci, co jest szczególnie nieefektywne, biorąc wykładniczo dłuższego czasu na większą liczbą. Służy w tym miejscu celach ilustracyjnych, aby wyświetlić operacji, które mogą powodować duże opóźnienia w aplikacji.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  W <xref:System.ComponentModel.BackgroundWorker.DoWork> program obsługi zdarzeń, dodaj wywołanie do `ComputeFibonacci` metody. Przeprowadzanie pierwszy parametr `ComputeFibonacci` z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs>. <xref:System.ComponentModel.BackgroundWorker> i <xref:System.ComponentModel.DoWorkEventArgs> parametry będą później używane dla raportowania postępu i anulowania obsługi. Przypisz wartość zwrotną z elementu `ComputeFibonacci` do <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs>. Ten wynik będzie dostępna do <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obsługi zdarzeń.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BackgroundWorker.DoWork> Program obsługi zdarzeń nie odwołuje się `backgroundWorker1` wystąpienie zmiennej bezpośrednio, ponieważ spowoduje to połączenie ten program obsługi zdarzeń do konkretnego wystąpienia <xref:System.ComponentModel.BackgroundWorker>. Zamiast tego odwołania do <xref:System.ComponentModel.BackgroundWorker> wywoływane to, że zdarzenie jest odzyskała sprawność działania po `sender` parametru. Jest to ważne, gdy formularz zawiera więcej niż jeden <xref:System.ComponentModel.BackgroundWorker>. Warto również nie manipulowania żadne obiekty interfejsu użytkownika w Twojej <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń. Zamiast tego komunikują się za pośrednictwem interfejsu użytkownika <xref:System.ComponentModel.BackgroundWorker> zdarzenia.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  W `startAsyncButton` formantu <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń, Dodaj kod, który rozpoczyna operację asynchroniczną.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  W <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> program obsługi zdarzeń, przypisz wynik obliczenia `resultLabel` formantu.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a>Dodawanie raportowania postępu i obsługa anulowania  
 Asynchroniczne operacje wykonywane przez długi czas często jest pożądane raportowania postępu dla użytkownika, aby zezwolić użytkownikowi anulować operację. <xref:System.ComponentModel.BackgroundWorker> Udostępnia zdarzenie pozwala na księgowanie postępu jako programu będzie kontynuowane operacji tła. Zapewnia także Flaga, która umożliwia kodu procesu roboczego do wykrywania wywołanie <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> i przerwać samej sobie.  
  
#### <a name="to-implement-progress-reporting"></a>Aby zaimplementować raportowania postępu  
  
1.  W **właściwości**, wybierz `backgroundWorker1`. Ustaw <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości `true`.  
  
2.  Zadeklaruj dwie zmienne w `FibonacciCalculator` formularza. Te będzie można śledzić postęp.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  Dodaj program obsługi zdarzeń dla <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń. W <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> obsługi zdarzeń, aktualizacja <xref:System.Windows.Forms.ProgressBar> z <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> właściwość <xref:System.ComponentModel.ProgressChangedEventArgs> parametru.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a>Obsługa anulowania  
  
1.  W `cancelAsyncButton` formantu <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń, Dodaj kod, który anuluje operację asynchroniczną.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  Poniższy kod fragmentów w `ComputeFibonacci` — metoda raportu postęp i obsługa anulowania.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie można skompilować i uruchomić aplikację Fibonacci Kalkulator.  
  
#### <a name="to-test-your-project"></a>Aby przetestować projektu  
  
-   Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
     Obliczenie jest uruchomiona w tle, zobaczysz <xref:System.Windows.Forms.ProgressBar> Wyświetlanie postępu obliczenia w kierunku ukończenia. Możesz również anulować oczekująca operacja.  
  
     Dla małej liczby obliczenia powinny być bardzo szybko, ale dla większej liczby powinna zostać wyświetlona zauważalnego opóźnienia. Jeśli wprowadzisz wartość 30 lub większą, powinna zostać wyświetlona opóźnienie kilka sekund, w zależności od szybkości komputera. W przypadku wartości większej niż 40 może potrwać minut lub godziny na zakończenie działania. Kalkulator jest zajęty obliczeniowych dużą liczbą Fibonacci, zwróć uwagę, że można swobodnie poruszanie formularza, zminimalizować, zmaksymalizować, a nawet je zamknąć. Jest to spowodowane wątku interfejsu użytkownika głównego nie oczekuje na obliczenia zakończyć.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, gdy zostały zaimplementowane formularza korzystającego z <xref:System.ComponentModel.BackgroundWorker> składnika do wykonywania obliczeń w tle, można sprawdzić możliwości innych operacji asynchronicznych:  
  
-   Używanych jest wiele <xref:System.ComponentModel.BackgroundWorker> obiektów dla wielu jednoczesnych operacji.  
  
-   Debugowanie aplikacji wielowątkowych, zobacz [porady: Korzystanie z okna wątków](/visualstudio/debugger/how-to-use-the-threads-window).  
  
-   Implementuje własne składnik, który obsługuje model programowania asynchronicznego. Aby uzyskać więcej informacji, zobacz [oparty na zdarzeniach asynchroniczny wzorzec — Przegląd](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
    > [!CAUTION]
    >  Korzystając z wielowątkowość jakiegokolwiek, możesz narażając samodzielnie do usterki bardzo poważne i złożone. Zapoznaj się [zarządzanych wątków najlepsze rozwiązania w zakresie](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem rozwiązania, w którym używane wielowątkowości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Zarządzana wątkowość — najlepsze praktyki](../../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Wielowątkowość składników](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [NIE w kompilacji: Wielowątkowość w języku Visual Basic](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Wskazówki: Przeprowadzanie operacji w tle](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 [BackgroundWorker — składnik](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
