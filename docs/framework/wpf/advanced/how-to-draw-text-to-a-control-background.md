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
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="67e09-102">Jak rysować tekst w tle formantu</span><span class="sxs-lookup"><span data-stu-id="67e09-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="67e09-103">Możesz narysować tekst bezpośrednio w tle kontrolki, konwertując ciąg tekstowy na obiekt <xref:System.Windows.Media.FormattedText>, a następnie rysując obiekt na <xref:System.Windows.Media.DrawingContext>formantu.</span><span class="sxs-lookup"><span data-stu-id="67e09-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="67e09-104">Tej techniki można również użyć do rysowania na tle obiektów pochodzących od <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="67e09-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="67e09-105">![Zrzut ekranu kontrolek wyświetlających tekst jako tło.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="67e09-105">![Screenshot of controls displaying text as background.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span></span>  
<span data-ttu-id="67e09-106">Przykład kontrolek z niestandardowym tłem tekstu</span><span class="sxs-lookup"><span data-stu-id="67e09-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="67e09-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="67e09-107">Example</span></span>  
 <span data-ttu-id="67e09-108">Aby narysować w tle kontrolki, Utwórz nowy obiekt <xref:System.Windows.Media.DrawingBrush> i narysuj przekonwertowany tekst na <xref:System.Windows.Media.DrawingContext>obiektu.</span><span class="sxs-lookup"><span data-stu-id="67e09-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="67e09-109">Następnie przypisz nowy <xref:System.Windows.Media.DrawingBrush> do właściwości tła kontrolki.</span><span class="sxs-lookup"><span data-stu-id="67e09-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="67e09-110">Poniższy przykład kodu pokazuje, jak utworzyć obiekt <xref:System.Windows.Media.FormattedText> i rysować w tle obiektu <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="67e09-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="67e09-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67e09-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="67e09-112">Rysowanie formatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="67e09-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
