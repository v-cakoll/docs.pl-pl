---
title: "Jak pobrać przesunięcie Visual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22c35a683f479660a17f11e44f9a0721f9d35968
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-offset-of-a-visual"></a>Jak pobrać przesunięcie Visual
Poniższe przykłady pokazują, jak można pobrać wartości przesunięcia względem jego elementu nadrzędnego lub żadnych nadrzędnym lub podrzędnym obiektu visual.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano kod znaczników <xref:System.Windows.Controls.TextBlock> zdefiniowanego z <xref:System.Windows.FrameworkElement.Margin%2A> o wartości 4.  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> metoda pobierania przesunięcie <xref:System.Windows.Controls.TextBlock>. Wartości przesunięcia są zawarte w zwróconym <xref:System.Windows.Vector> wartość.  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 Przesunięcie bierze pod uwagę <xref:System.Windows.FrameworkElement.Margin%2A> wartość. W takim przypadku <xref:System.Windows.Vector.X%2A> 4, i <xref:System.Windows.Vector.Y%2A> to 4.  
  
 Zwrócona wartość przesunięcia jest określana względem elementu nadrzędnego <xref:System.Windows.Media.Visual>. Jeśli chcesz zwrócić wartość przesunięcia, które nie jest określana względem elementu nadrzędnego <xref:System.Windows.Media.Visual>, użyj <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metody.  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a>Pierwsze przesunięcie względem elementu nadrzędnego  
 W poniższym przykładzie pokazano kod znaczników <xref:System.Windows.Controls.TextBlock> zagnieżdżony w dwóch <xref:System.Windows.Controls.StackPanel> obiektów.  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 Na poniższej ilustracji przedstawiono wyniki znaczników.  
  
 ![Wartości przesunięcia obiektów](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")  
W dwóch StackPanels zagnieżdżony blok tekstu  
  
 Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Windows.Media.Visual.TransformToAncestor%2A> metoda pobierania przesunięcie <xref:System.Windows.Controls.TextBlock> względem zawierający <xref:System.Windows.Window>. Wartości przesunięcia są zawarte w zwróconym <xref:System.Windows.Media.GeneralTransform> wartość.  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 Przesunięcie bierze pod uwagę <xref:System.Windows.FrameworkElement.Margin%2A> wartości dla wszystkich obiektów w ramach zawierający <xref:System.Windows.Window>. W takim przypadku <xref:System.Windows.Vector.X%2A> jest 28 (16 + 8 + 4), a <xref:System.Windows.Vector.Y%2A> to 28.  
  
 Zwrócona wartość przesunięcia jest określana względem element nadrzędny elementu <xref:System.Windows.Media.Visual>. Jeśli chcesz zwrócić wartość przesunięcia względem obiektu podrzędnego z <xref:System.Windows.Media.Visual>, użyj <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metody.  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a>Pierwsze przesunięcie względem element podrzędny  
 W poniższym przykładzie pokazano kod znaczników <xref:System.Windows.Controls.TextBlock> zawarty w <xref:System.Windows.Controls.StackPanel> obiektu.  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Windows.Media.Visual.TransformToDescendant%2A> metoda pobierania przesunięcie <xref:System.Windows.Controls.StackPanel> względem jego podrzędny <xref:System.Windows.Controls.TextBlock>. Wartości przesunięcia są zawarte w zwróconym <xref:System.Windows.Media.GeneralTransform> wartość.  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 Przesunięcie bierze pod uwagę <xref:System.Windows.FrameworkElement.Margin%2A> wartości dla wszystkich obiektów. W takim przypadku <xref:System.Windows.Vector.X%2A> jest -4, i <xref:System.Windows.Vector.Y%2A> jest -4. Wartości przesunięcia są wartości ujemnych, ponieważ obiekt nadrzędny negatywnie jest przesuwane względem jego obiektu podrzędnego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
