---
title: 'Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: 0f15cd870efbdcd00dafa071175be078311a9a37
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289398"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach
Wiele składników oferuje możliwość wykonywania pracy asynchronicznie. <xref:System.Media.SoundPlayer>Składniki i <xref:System.Windows.Forms.PictureBox> umożliwiają na przykład ładowanie dźwięków i obrazów "w tle", podczas gdy główny wątek nadal działa bez przeszkód.  
  
 Korzystanie z metod asynchronicznych na klasie, która obsługuje [oparte na zdarzeniach](event-based-asynchronous-pattern-overview.md) , można jak równie łatwo dołączać obsługę zdarzeń do zdarzenia**ukończenia** _MethodName_przez składnik, podobnie jak w przypadku dowolnego innego zdarzenia. Po wywołaniu metody**asynchronicznej** _MethodName_aplikacja będzie kontynuowała pracę bez przeszkód do momentu zgłoszenia zdarzenia _MethodName_**ukończone** . W programie obsługi zdarzeń można sprawdzić <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr, aby określić, czy operacja asynchroniczna została ukończona pomyślnie, czy też została anulowana.  
  
 Aby uzyskać więcej informacji o korzystaniu z programów obsługi zdarzeń, zobacz [Omówienie obsługi zdarzeń](../../framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Poniższa procedura pokazuje, jak używać funkcji asynchronicznego ładowania obrazu <xref:System.Windows.Forms.PictureBox> formantu.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Aby włączyć formant PictureBox do asynchronicznego ładowania obrazu  
  
1. Utwórz wystąpienie <xref:System.Windows.Forms.PictureBox> składnika w formularzu.  
  
2. Przypisz do zdarzenia procedurę obsługi zdarzeń <xref:System.Windows.Forms.PictureBox.LoadCompleted> .  
  
     Sprawdź pod kątem błędów, które mogły wystąpić podczas pobierania asynchronicznego w tym miejscu. Jest to również miejsce, w którym można sprawdzić, czy jest to możliwe.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3. Dodaj dwa przyciski, nazywane `loadButton` i `cancelLoadButton` , do formularza. Dodaj <xref:System.Windows.Forms.Control.Click> programy obsługi zdarzeń, aby rozpocząć i anulować pobieranie.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4. Uruchom aplikację.  
  
     Po pobraniu obrazu będzie można swobodnie przenieść formularz, zminimalizować go i zmaksymalizować.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: uruchamianie operacji w tle](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](event-based-asynchronous-pattern-overview.md)
