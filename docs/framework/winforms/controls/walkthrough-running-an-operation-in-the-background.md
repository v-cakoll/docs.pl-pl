---
title: "Wskazówki: przeprowadzanie operacji w tle"
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
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de485eb0b9c67ee9c3c897b6521971f50aaf751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-running-an-operation-in-the-background"></a>Wskazówki: przeprowadzanie operacji w tle
Jeśli masz operacji potrwa długo, i nie chcesz powodować opóźnienia w interfejsie użytkownika, można użyć <xref:System.ComponentModel.BackgroundWorker> klasę, aby uruchomić operację w innym wątku.  
  
 Aby uzyskać pełną listę kod używany w tym przykładzie, zobacz [porady: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-run-an-operation-in-the-background"></a>Uruchamianie operacji w tle  
  
1.  Formularz aktywne w narzędziu Projektant dla formularzy systemu Windows, przeciągnij dwa <xref:System.Windows.Forms.Button> formantów **przybornika** do formularza, a następnie ustawić `Name` i <xref:System.Windows.Forms.Control.Text%2A> właściwości przycisków zgodnie z poniższą tabelą.  
  
    |Przycisk|Nazwa|Tekst|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|**Początek**|  
    |`button2`|`cancelBtn`|**Anuluj**|  
  
2.  Otwórz **przybornika**, kliknij przycisk **składniki** karcie, a następnie przeciągnij <xref:System.ComponentModel.BackgroundWorker> składnika w formularzu.  
  
     `backgroundWorker1` Składnika jest wyświetlana w **zasobnik składnika**.  
  
3.  W **właściwości** ustaw <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> właściwości `true`.  
  
4.  W **właściwości** kliknij na **zdarzenia** przycisk, a następnie kliknij dwukrotnie <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenia można utworzyć procedury obsługi zdarzeń.  
  
5.  Wstaw kod czasochłonne do <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń.  
  
6.  Wyodrębnij wszystkie parametry wymagane przez operację z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs> parametru.  
  
7.  Przypisz wynik do obliczenia <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> właściwość <xref:System.ComponentModel.DoWorkEventArgs>.  
  
     Jest to będzie dostępna do <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obsługi zdarzeń.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  Wstawianie kodu do pobierania wyników operacji w <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obsługi zdarzeń.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. Implementowanie `TimeConsumingOperation` metody.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. W narzędziu Projektant dla formularzy systemu Windows, kliknij dwukrotnie `startButton` utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.  
  
11. Wywołanie <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody w <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `startButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. W narzędziu Projektant dla formularzy systemu Windows, kliknij dwukrotnie `cancelButton` utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.  
  
13. Wywołanie <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metody w <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń dla `cancelButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. W górnej części pliku należy zaimportować System.ComponentModel i System.Threading przestrzeni nazw.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. Naciśnij klawisz F6 w celu skompilowania rozwiązania, a następnie naciśnij klawisz CTRL-F5, aby uruchomić aplikację poza debugerem.  
  
> [!NOTE]
>  Jeśli użytkownik naciśnie klawisz F5, aby uruchomić aplikację w debugerze, wyjątek w `TimeConsumingOperation` metoda przechwycony i wyświetlane przez debuger. Po uruchomieniu aplikacji poza debugerem, <xref:System.ComponentModel.BackgroundWorker> obsługuje wyjątek i buforuje ją w <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> właściwość <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.  
  
1.  Kliknij przycisk **Start** przycisk, aby uruchomić operację asynchroniczną, a następnie kliknij przycisk **anulować** przycisk, aby zatrzymać operację uruchomiona asynchroniczną.  
  
     Wynik każdej operacji jest wyświetlany w <xref:System.Windows.Forms.MessageBox>.  
  
## <a name="next-steps"></a>Następne kroki  
  
-   Implementowanie formularza, który zgłasza postęp w trakcie wykonywania operacji asynchronicznej. Aby uzyskać więcej informacji, zobacz [porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
-   Implementuje klasę, która obsługuje wzorca asynchronicznego dla składników. Aby uzyskać więcej informacji, zobacz [implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Porady: Implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Porady: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [BackgroundWorker — składnik](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
