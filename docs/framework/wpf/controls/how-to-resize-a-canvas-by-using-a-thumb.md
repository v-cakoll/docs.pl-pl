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
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124302"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>Jak zmienić rozmiar kanwy przy użyciu kciuka
W tym przykładzie pokazano, jak za pomocą kontrolki <xref:System.Windows.Controls.Primitives.Thumb> zmienić rozmiar kontrolki <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Przykład  
 Formant <xref:System.Windows.Controls.Primitives.Thumb> zapewnia funkcję przeciągania, która może służyć do przenoszenia lub zmieniania rozmiaru formantów przez monitorowanie <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zdarzeń <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 Użytkownik rozpoczyna operację przeciągania, naciskając lewy przycisk myszy, gdy wskaźnik myszy jest wstrzymany w kontrolce <xref:System.Windows.Controls.Primitives.Thumb>. Operacja przeciągania jest kontynuowana, o ile lewy przycisk myszy pozostanie wciśnięty. Podczas operacji przeciągania <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> może wystąpić więcej niż jeden raz. Za każdym razem, gdy występuje, Klasa <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> zapewnia zmianę położenia, która odnosi się do zmiany położenia wskaźnika myszy. Gdy użytkownik zwolni lewy przycisk myszy, operacja przeciągania zostanie zakończona. Operacja przeciągania zawiera tylko nowe współrzędne; nie powoduje automatycznego zmiany położenia <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 W poniższym przykładzie pokazano formant <xref:System.Windows.Controls.Primitives.Thumb>, który jest elementem podrzędnym kontrolki <xref:System.Windows.Controls.Canvas>. Program obsługi zdarzeń dla jego zdarzenia <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> udostępnia logikę do przeniesienia <xref:System.Windows.Controls.Primitives.Thumb> i zmiany rozmiaru <xref:System.Windows.Controls.Canvas>. Procedury obsługi zdarzeń <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> i <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> zmieniają kolor <xref:System.Windows.Controls.Primitives.Thumb> podczas operacji przeciągania. W poniższym przykładzie zdefiniowano <xref:System.Windows.Controls.Primitives.Thumb>.  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>, która przenosi <xref:System.Windows.Controls.Primitives.Thumb> i zmienia rozmiar <xref:System.Windows.Controls.Canvas> w odpowiedzi na ruch myszy.  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>.  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 Poniższy przykład pokazuje procedurę obsługi zdarzeń <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>.  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 Pełny przykład można znaleźć w sekcji [Przykładowa funkcja przeciągania](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
