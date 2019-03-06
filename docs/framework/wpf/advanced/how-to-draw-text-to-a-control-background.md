---
title: 'Instrukcje: Rysuj tekst w tle formantu'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 025b13d83aeb668fa3a9f8af35d7213ae677eefc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378753"
---
# <a name="how-to-draw-text-to-a-controls-background"></a>Instrukcje: Rysuj tekst w tle formantu
Można rysować tekst bezpośrednio do tła kontrolki, dokonując przekonwertowania na ciąg tekstowy <xref:System.Windows.Media.FormattedText> obiektu, a następnie narysować obiekt na formant <xref:System.Windows.Media.DrawingContext>. Można również użyć tej techniki dla rysunku do tła obiekty pochodzące z <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.StackPanel>.  
  
 ![Formanty wyświetlania tekstu jako tło](./media/drawtext2background01.png "DrawText2Background01")  
Przykład formantów z tła niestandardowego tekstu  
  
## <a name="example"></a>Przykład  
 Aby narysować do tła kontrolki, Utwórz nowy <xref:System.Windows.Media.DrawingBrush> obiektu, a następnie narysuj tekst skonwertowany z obiektem <xref:System.Windows.Media.DrawingContext>. Następnie przypisz nowe <xref:System.Windows.Media.DrawingBrush> właściwości tła formantu.  
  
 Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu, a następnie narysuj do tła <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Button> obiektu.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.FormattedText>
- [Rysowanie formatowanego tekstu](drawing-formatted-text.md)
