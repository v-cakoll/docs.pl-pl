---
title: 'Przewodnik: uruchamianie operacji w tle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
ms.openlocfilehash: c1881ffa1c6fca546b086efea59d2263af853949
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792174"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a>Przewodnik: uruchamianie operacji w tle
Jeśli operacja, która będzie zająć dużo czasu, i nie chcesz powodować opóźnienia w interfejsie użytkownika, możesz użyć <xref:System.ComponentModel.BackgroundWorker> klasy, aby uruchomić operację na inny wątek.  
  
 Aby uzyskać pełną listę kod używany w tym przykładzie, zobacz [jak: Uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-run-an-operation-in-the-background"></a>Uruchamianie operacji w tle  
  
1. Za pomocą formularza aktywny w Windows Forms Designer, przeciągnij dwa <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do formularza, a następnie ustaw `Name` i <xref:System.Windows.Forms.Control.Text%2A> właściwości przycisków zgodnie z poniższą tabelą.  
  
    |Przycisk|Nazwa|Tekst|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|**Start**|  
    |`button2`|`cancelBtn`|**Anulowanie**|  
  
2. Otwórz **przybornika**, kliknij przycisk **składniki** kartę, a następnie przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika do formularza.  
  
     `backgroundWorker1` Składnika, który pojawia się w **zasobniku składnika**.  
  
3. W oknie **Właściwości** ustaw właściwość <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> na `true`.   
  
4. W **właściwości** okna, kliknij pozycję **zdarzenia** przycisk, a następnie kliknij dwukrotnie <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń, aby utworzyć procedury obsługi zdarzeń.  
  
5. Wstaw kod czasochłonne do <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.  
  
6. Wyodrębnij wszystkie parametry wymagane przez operację z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs> parametru.  
  
7. Przypisz wynik obliczeń, aby <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs>.  
  
     To jest dostępne <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8. Wstawianie kodu do pobierania wyników operacji w <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. Implementowanie `TimeConsumingOperation` metody.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. W Windows Forms Designer, kliknij dwukrotnie `startButton` utworzyć <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.  
  
11. Wywołaj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in Class metoda <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `startButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. W Windows Forms Designer, kliknij dwukrotnie `cancelButton` utworzyć <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.  
  
13. Wywołaj <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in Class metoda <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń dla `cancelButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. W górnej części pliku zaimportuj przestrzenie nazw System.ComponentModel i System.Threading.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. Naciśnij klawisz F6, aby skompilować rozwiązanie, a następnie naciśnij kombinację klawiszy CTRL-F5, aby uruchomić aplikację poza debugerem.  
  
> [!NOTE]
>  Jeśli użytkownik naciśnie klawisz F5, aby uruchomić aplikację w debugerze, wyjątek zgłoszony w `TimeConsumingOperation` metoda jest przechwycony i wyświetlane przez debuger. Po uruchomieniu aplikacji poza debugerem, <xref:System.ComponentModel.BackgroundWorker> obsługuje wyjątek i zapisuje go w pamięci podręcznej <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwość <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.  
  
1. Kliknij przycisk **Start** przycisk, aby uruchomić operację asynchroniczną, a następnie kliknij przycisk **anulować** przycisk, aby zatrzymać operację pracę asynchroniczną.  
  
     Wynikiem operacji jest wyświetlana w <xref:System.Windows.Forms.MessageBox>.  
  
## <a name="next-steps"></a>Następne kroki  
  
- Implementowanie formularza, który zgłasza postępy pracy w trakcie wykonywania operacji asynchronicznej. Aby uzyskać więcej informacji, zobacz [jak: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md).  
  
- Implementuje klasę, która obsługuje wzorca asynchronicznego dla składników. Aby uzyskać więcej informacji, zobacz [implementacja wzorca asynchronicznego opartego na zdarzeniach](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Instrukcje: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Instrukcje: Uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md)
- [BackgroundWorker, składnik](backgroundworker-component.md)
