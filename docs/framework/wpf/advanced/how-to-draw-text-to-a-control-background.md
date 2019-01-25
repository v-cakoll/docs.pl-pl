---
title: 'Instrukcje: Rysuj tekst do kontrolki&#39;tła s'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: d580330de5ef3841979fffc61db336064f1643f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740432"
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>Instrukcje: Rysuj tekst do kontrolki&#39;tła s
Można rysować tekst bezpośrednio do tła kontrolki, dokonując przekonwertowania na ciąg tekstowy <xref:System.Windows.Media.FormattedText> obiektu, a następnie narysować obiekt na formant <xref:System.Windows.Media.DrawingContext>. Można również użyć tej techniki dla rysunku do tła obiekty pochodzące z <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.StackPanel>.  
  
 ![Formanty wyświetlania tekstu jako tło](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Przykład formantów z tła niestandardowego tekstu  
  
## <a name="example"></a>Przykład  
 Aby narysować do tła kontrolki, Utwórz nowy <xref:System.Windows.Media.DrawingBrush> obiektu, a następnie narysuj tekst skonwertowany z obiektem <xref:System.Windows.Media.DrawingContext>. Następnie przypisz nowe <xref:System.Windows.Media.DrawingBrush> właściwości tła formantu.  
  
 Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu, a następnie narysuj do tła <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Button> obiektu.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.FormattedText>
- [Rysowanie formatowanego tekstu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
