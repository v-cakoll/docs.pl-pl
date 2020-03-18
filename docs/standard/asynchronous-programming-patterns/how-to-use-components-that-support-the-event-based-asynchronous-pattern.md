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
ms.openlocfilehash: 9ac98b5c576c065f8944714c72b492539e0d2f05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "61870243"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach
Wiele składników zapewnia możliwość wykonywania ich pracy asynchronicznie. <xref:System.Media.SoundPlayer> Komponenty <xref:System.Windows.Forms.PictureBox> i, na przykład, umożliwiają ładowanie dźwięków i obrazów "w tle", podczas gdy główny wątek nadal działa bez przerwy.  
  
 Przy użyciu metod asynchronicznych w klasie, która obsługuje [omówienie wzorca asynchronicznego opartego](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) na zdarzeniach może być tak proste, jak dołączanie programu obsługi zdarzeń do zdarzenia _MethodName_**Complete** składnika, tak jak w przypadku każdego innego zdarzenia. Po wywołaniu _MethodName_**Async** metody, aplikacja będzie nadal działać bez przerwy, dopóki _MethodName_**Completed** zdarzenie zostanie podniesiona. W programie obsługi zdarzeń <xref:System.ComponentModel.AsyncCompletedEventArgs> można sprawdzić parametr, aby ustalić, czy operacja asynchroniczna została pomyślnie ukończona lub czy została anulowana.  
  
 Aby uzyskać więcej informacji na temat korzystania z programów obsługi zdarzeń, zobacz [Omówienie programów obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 W poniższej procedurze pokazano, jak używać asynchronicznej możliwości ładowania obrazu formantu. <xref:System.Windows.Forms.PictureBox>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Aby włączyć formant PictureBox do asynchronicznie załadować obraz  
  
1. Utwórz wystąpienie <xref:System.Windows.Forms.PictureBox> składnika w formularzu.  
  
2. Przypisz program obsługi <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzeń do zdarzenia.  
  
     Sprawdź, czy nie wystąpiły błędy podczas pobierania asynchronicznego tutaj. W tym miejscu można również sprawdzić możliwość anulowania.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3. Dodaj dwa przyciski, o nazwie `loadButton` i `cancelLoadButton`, do formularza. Dodaj <xref:System.Windows.Forms.Control.Click> programy obsługi zdarzeń, aby rozpocząć i anulować pobieranie.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4. Uruchom aplikację.  
  
     W miarę pobierania obrazu można swobodnie przenosić formularz, minimalizować go i zmaksymalizować.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
