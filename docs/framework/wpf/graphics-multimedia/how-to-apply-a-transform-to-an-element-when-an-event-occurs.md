---
title: Jak zastosować przekształcenie do elementu kiedy wystąpi zdarzenie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: bd50b369666a1b65226b2b7eb6f3d866ec670bde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Jak zastosować przekształcenie do elementu kiedy wystąpi zdarzenie
W tym przykładzie pokazano, jak zastosować <xref:System.Windows.Media.ScaleTransform> po wystąpieniu zdarzenia. Pojęcia, które przedstawiono w tym miejscu jest taki sam, służące do stosowania innych typów przekształcenia. Aby uzyskać więcej informacji na temat dostępnych typów przekształcenia, zobacz <xref:System.Windows.Media.Transform> klasy lub [przekształca omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
 Transformacja można zastosować do elementu w jeden z tych dwóch sposobów:  
  
-   Jeśli chcesz *nie* mają transformacji mają wpływ na układ, należy użyć <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu.  
  
-   Przekształcenie do mają wpływ na układ, należy użyć <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości elementu.  
  
 Następujący przykład dotyczy <xref:System.Windows.Media.ScaleTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość przycisku. Gdy wskaźnik myszy przesuwa się nad przycisku <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości <xref:System.Windows.Media.ScaleTransform> ustawiono `2`, co powoduje, że przycisk, aby stać się zbyt duży. Gdy wskaźnik myszy przesunięty poza, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> ustawiono `1`, co powoduje, że przycisk, aby wrócić do oryginalnego rozmiaru.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
