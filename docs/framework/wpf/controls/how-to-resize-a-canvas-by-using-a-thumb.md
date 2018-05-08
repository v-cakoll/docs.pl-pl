---
title: Jak zmienić rozmiar kanwy przy użyciu kciuka
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
ms.openlocfilehash: c3e7176b0578c8fdc5f4331ad8f3b464f3a88b51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Jak zmienić rozmiar kanwy przy użyciu kciuka
Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.Primitives.Thumb> sterowania, aby zmienić rozmiar <xref:System.Windows.Controls.Canvas> formantu.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.Primitives.Thumb> Formant zawiera funkcję przeciągania, która może służyć do przeniesienia lub zmiany rozmiaru formantów przez monitorowanie <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzenia <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Użytkownik rozpoczyna się operacja przeciągania, naciskając klawisz lewego przycisku myszy, gdy wskaźnik myszy jest wstrzymana na <xref:System.Windows.Controls.Primitives.Thumb> formantu. Operacja przeciągania nadal lewy przycisk myszy zostanie kliknięty. Podczas operacji przeciągania <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> może występować więcej niż raz. Zawsze wystąpi, <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> klasa udostępnia zmiany w pozycji, która odpowiada zmiany pozycji myszy. Gdy użytkownik zwalnia lewego przycisku myszy, operacja przeciągania została zakończona. Operacja przeciągania zapewnia tylko nowe współrzędne; nie automatycznie zmienić <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb> kontrolować będący elementem podrzędnym <xref:System.Windows.Controls.Canvas> formantu. Program obsługi zdarzeń dla jego <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> zdarzeń zapewnia logiki przenoszenia <xref:System.Windows.Controls.Primitives.Thumb> i zmień rozmiar <xref:System.Windows.Controls.Canvas>. Programy obsługi zdarzeń dla <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzeń umożliwia zmianę koloru <xref:System.Windows.Controls.Primitives.Thumb> podczas operacji przeciągania. W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> obsługi zdarzeń, który przenosi <xref:System.Windows.Controls.Primitives.Thumb> i zmienia rozmiar <xref:System.Windows.Controls.Canvas> w odpowiedzi na ruchów myszy.  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> obsługi zdarzeń.  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> obsługi zdarzeń.  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Pełny przykład, zobacz [próbki funkcjonalność przeciągania Thumb](http://go.microsoft.com/fwlink/?LinkID=160042).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
