---
title: 'Instrukcje: Zmienianie rozmiaru kanwy przy użyciu kciuka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
ms.openlocfilehash: 14942157429b029147d47e2f88428c56e66523d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770750"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Instrukcje: Zmienianie rozmiaru kanwy przy użyciu kciuka
W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.Primitives.Thumb> formantu, aby zmienić rozmiar <xref:System.Windows.Controls.Canvas> kontroli.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.Primitives.Thumb> Control oferuje funkcje przeciągania, który może służyć do przeniesienia lub zmiany rozmiaru kontrolek poprzez monitorowanie <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzenia <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Użytkownik rozpoczyna się operacja przeciągania, naciskając klawisze lewy przycisk myszy, gdy wskaźnik myszy jest wstrzymana na <xref:System.Windows.Controls.Primitives.Thumb> kontroli. Operacja przeciągania nadal nie zostanie po naciśnięciu lewego przycisku myszy. Podczas operacji przeciągania <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> może wystąpić więcej niż jeden raz. Każdorazowo, wystąpi, <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> klasa udostępnia zmianę pozycji, która odnosi się do zmian w miejscu położenia wskaźnika myszy. Gdy użytkownik zwolni przycisk myszy po lewej stronie, operacja przeciągania została zakończona. Operacja przeciągania zapewnia tylko nowe współrzędne; go nie zmieniaj położenia automatycznie <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb> kontrolować czyli element podrzędny elementu <xref:System.Windows.Controls.Canvas> kontroli. Program obsługi zdarzeń dla jego <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> zdarzenia udostępnia logikę, aby przenieść <xref:System.Windows.Controls.Primitives.Thumb> i zmienianie rozmiaru <xref:System.Windows.Controls.Canvas>. Programy obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzenia Zmień kolor <xref:System.Windows.Controls.Primitives.Thumb> podczas operacji przeciągania. W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> programu obsługi zdarzeń, który przenosi <xref:System.Windows.Controls.Primitives.Thumb> i zmienia rozmiar <xref:System.Windows.Controls.Canvas> w odpowiedzi na ruchów myszy.  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> programu obsługi zdarzeń.  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> programu obsługi zdarzeń.  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Aby uzyskać pełny przykład, zobacz [Przykładowe funkcje przeciągania Thumb](https://go.microsoft.com/fwlink/?LinkID=160042).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
