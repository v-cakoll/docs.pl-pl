---
title: 'Instrukcje: Stosowanie przekształcenia do elementu w przypadku wystąpienia zdarzenia'
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
ms.openlocfilehash: 8f04db274432c0e89c6839bef825976c8a2f853c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630752"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Instrukcje: Stosowanie przekształcenia do elementu w przypadku wystąpienia zdarzenia
Ten przykład przedstawia sposób zastosowania <xref:System.Windows.Media.ScaleTransform> po wystąpieniu zdarzenia. Pojęcia, która jest wyświetlana w tym miejscu jest taka sama, używanej do stosowania innych rodzajów przekształcenia. Aby uzyskać więcej informacji na temat dostępnych typów przekształcenia zobacz <xref:System.Windows.Media.Transform> klasy lub [przekształca Przegląd](transforms-overview.md).  
  
 Należy zastosować przekształcenie do elementu w jeden z następujących dwóch sposobów:  
  
- Jeśli to zrobisz *nie* ma przekształcenia wpływają na układ, należy użyć <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu.  
  
- Przekształcanie wpływ na układ, użyć <xref:System.Windows.FrameworkElement.LayoutTransform%2A> właściwości elementu.  
  
 Następujący przykład dotyczy <xref:System.Windows.Media.ScaleTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość przycisku. Gdy wskaźnik myszy porusza się na przycisku <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości <xref:System.Windows.Media.ScaleTransform> są ustawione na `2`, co powoduje, że przycisk aby stać się zbyt duży. Gdy wskaźnik myszy przesunięty, poza <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> są ustawione na `1`, co powoduje, że przycisk, aby powrócić do oryginalnego rozmiaru.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[ButtonTransform#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Przekształcenia — przegląd](transforms-overview.md)
- [Tematy z instrukcjami](transformations-how-to-topics.md)
- [Przegląd zdarzeń trasowanych](../advanced/routed-events-overview.md)
