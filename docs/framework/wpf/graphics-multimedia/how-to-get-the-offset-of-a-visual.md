---
title: 'Instrukcje: Pobierz przesunięcie Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: ad45dee5b72594f30b141e3affbb26706af645aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645395"
---
# <a name="how-to-get-the-offset-of-a-visual"></a>Instrukcje: Pobierz przesunięcie Visual
Te przykłady pokazują, jak można pobrać wartości przesunięcia visual obiektu, który jest określana względem jego elementu nadrzędnego lub dowolnego nadrzędnym lub obiekt podrzędny.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono znaczników <xref:System.Windows.Controls.TextBlock> zdefiniowanego za pomocą <xref:System.Windows.FrameworkElement.Margin%2A> wartość 4.  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> metodę, aby pobrać przesunięcie <xref:System.Windows.Controls.TextBlock>. Wartości przesunięcia znajdują się w ciągu zwracanym <xref:System.Windows.Vector> wartość.  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 Przesunięcie uwzględnia <xref:System.Windows.FrameworkElement.Margin%2A> wartość. W tym przypadku <xref:System.Windows.Vector.X%2A> to 4, i <xref:System.Windows.Vector.Y%2A> wynosi 4.  
  
 Zwrócona wartość przesunięcia jest określana względem elementu nadrzędnego <xref:System.Windows.Media.Visual>. Jeśli chcesz zwrócić wartości przesunięcia, która nie jest określana względem elementu nadrzędnego <xref:System.Windows.Media.Visual>, użyj <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metody.  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a>Pobieranie przesunięcia względem elementu nadrzędnego  
 W poniższym przykładzie przedstawiono znaczników <xref:System.Windows.Controls.TextBlock> zagnieżdżony w ramach dwóch <xref:System.Windows.Controls.StackPanel> obiektów.  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 Poniższa ilustracja przedstawia wyniki znaczników.  
  
 ![Wartości przesunięcia obiektów](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")  
Zagnieżdżone w obrębie dwóch StackPanels TextBlock  
  
 Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metodę, aby pobrać przesunięcie <xref:System.Windows.Controls.TextBlock> względem zawierający <xref:System.Windows.Window>. Wartości przesunięcia znajdują się w ciągu zwracanym <xref:System.Windows.Media.GeneralTransform> wartość.  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 Przesunięcie uwzględnia <xref:System.Windows.FrameworkElement.Margin%2A> wartości dla wszystkich obiektów w ramach zawierający <xref:System.Windows.Window>. W tym przypadku <xref:System.Windows.Vector.X%2A> to 28 (16 + 8 + 4), a <xref:System.Windows.Vector.Y%2A> to 28.  
  
 Zwrócona wartość przesunięcia jest określana względem element nadrzędny elementu <xref:System.Windows.Media.Visual>. Jeśli chcesz przywrócić wartość przesunięcia względem obiektu podrzędnego z <xref:System.Windows.Media.Visual>, użyj <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metody.  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a>Pobieranie przesunięcia względem element podrzędny  
 W poniższym przykładzie przedstawiono znaczników <xref:System.Windows.Controls.TextBlock> zawarty w <xref:System.Windows.Controls.StackPanel> obiektu.  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 Poniższy przykład kodu pokazuje sposób użycia <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metodę, aby pobrać przesunięcie <xref:System.Windows.Controls.StackPanel> względem jego podrzędny <xref:System.Windows.Controls.TextBlock>. Wartości przesunięcia znajdują się w ciągu zwracanym <xref:System.Windows.Media.GeneralTransform> wartość.  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 Przesunięcie uwzględnia <xref:System.Windows.FrameworkElement.Margin%2A> wartości dla wszystkich obiektów. W tym przypadku <xref:System.Windows.Vector.X%2A> jest -4, i <xref:System.Windows.Vector.Y%2A> jest -4. Wartości przesunięcia są wartości ujemnych, ponieważ obiekt nadrzędny negatywny jest przesuwane względem jego obiektów podrzędnych.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
