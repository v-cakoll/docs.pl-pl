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
ms.openlocfilehash: e6aecd5957ae62e3c147af22c2a1b135a4c32310
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489776"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach
Wiele składników zapewniają możliwość wykonywania pracy asynchronicznie. <xref:System.Media.SoundPlayer> i <xref:System.Windows.Forms.PictureBox> składników, na przykład włączyć ładowanie dźwięków i obrazy "w tle" nadal działa bez przerwy z wątku głównego.  
  
 Używanie metod asynchronicznych klasy, która obsługuje [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) mogą być proste i polega na dołączanie programu obsługi zdarzeń do składnika *MethodName *** Ukończono** zdarzenia Podobnie jak każde inne zdarzenie. Gdy wywołujesz *MethodName *** Async** metody, aplikacja będzie nadal działa nieprzerwanie aż do *MethodName *** Ukończono** zdarzenie jest zgłaszane. W przypadku obsługi zdarzenia, można sprawdzić <xref:System.ComponentModel.AsyncCompletedEventArgs> parametru, aby określić, czy pomyślnie Ukończono operację asynchroniczną, czy został anulowany.  
  
 Aby uzyskać więcej informacji o używaniu procedur obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Poniższa procedura przedstawia sposób użycia asynchronicznego możliwości ładowania obrazu <xref:System.Windows.Forms.PictureBox> kontroli.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Aby włączyć formant PictureBox, aby asynchronicznie załadować obrazu  
  
1.  Utwórz wystąpienie obiektu <xref:System.Windows.Forms.PictureBox> składnika w formularzu.  
  
2.  Program obsługi zdarzeń, aby przypisać <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzeń.  
  
     Sprawdź, czy wszystkie błędy, które mogły wystąpić podczas asynchronicznego pobierania w tym miejscu. Jest to również, gdzie sprawdzania występowania unieważnienia.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  Dodaje dwa przyciski, o nazwie `loadButton` i `cancelLoadButton`, do formularza. Dodaj <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń, aby uruchomić i anulować pobieranie.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  Uruchom aplikację.  
  
     W trakcie wykonywania pobrania obrazu można swobodnie przemieszczać się formularz, zminimalizować i zmaksymalizować go.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
