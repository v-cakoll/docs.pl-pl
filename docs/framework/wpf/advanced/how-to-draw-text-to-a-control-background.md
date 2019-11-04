---
title: Jak rysować tekst w tle formantu
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 14300f763b67c6ac67ee408de2009c328d499c13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424370"
---
# <a name="how-to-draw-text-to-a-controls-background"></a>Jak rysować tekst w tle formantu
Możesz narysować tekst bezpośrednio w tle kontrolki, konwertując ciąg tekstowy na obiekt <xref:System.Windows.Media.FormattedText>, a następnie rysując obiekt na <xref:System.Windows.Media.DrawingContext>formantu. Tej techniki można również użyć do rysowania na tle obiektów pochodzących od <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.StackPanel>.  
  
 ![Zrzut ekranu kontrolek wyświetlających tekst jako tło.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")  
Przykład kontrolek z niestandardowym tłem tekstu  
  
## <a name="example"></a>Przykład  
 Aby narysować w tle kontrolki, Utwórz nowy obiekt <xref:System.Windows.Media.DrawingBrush> i narysuj przekonwertowany tekst na <xref:System.Windows.Media.DrawingContext>obiektu. Następnie przypisz nowy <xref:System.Windows.Media.DrawingBrush> do właściwości tła kontrolki.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć obiekt <xref:System.Windows.Media.FormattedText> i rysować w tle obiektu <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.FormattedText>
- [Rysowanie formatowanego tekstu](drawing-formatted-text.md)
