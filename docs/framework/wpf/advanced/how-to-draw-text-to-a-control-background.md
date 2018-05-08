---
title: 'Porady: Rysowanie tekstu do formantu&#39;tła s'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: f79ec4f2c394fdc9462f4fd00942673b4536d713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>Porady: Rysowanie tekstu do formantu&#39;tła s
Tekst można narysować bezpośrednio do tła formantu, konwertując ciąg tekstowy do <xref:System.Windows.Media.FormattedText> obiekt, a następnie rysowania obiektu do formantu <xref:System.Windows.Media.DrawingContext>. Umożliwia także ta technika dla rysunku do tła obiekty pochodne <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.StackPanel>.  
  
 ![Wyświetlanie tekstu jako tła formantów](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Przykład formantów z tła tekstu niestandardowego  
  
## <a name="example"></a>Przykład  
 Aby narysować do tła formantu, Utwórz nową <xref:System.Windows.Media.DrawingBrush> obiektu i Rysuj tekst skonwertowany do obiektu <xref:System.Windows.Media.DrawingContext>. Następnie przypisz nowe <xref:System.Windows.Media.DrawingBrush> do właściwości tła formantu.  
  
 W poniższym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu i rysowanie do tła <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Button> obiektu.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.FormattedText>  
 [Rysowanie formatowanego tekstu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
