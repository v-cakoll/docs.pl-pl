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
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="2bc88-102">Instrukcje: Rysuj tekst w tle formantu</span><span class="sxs-lookup"><span data-stu-id="2bc88-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="2bc88-103">Można rysować tekst bezpośrednio do tła kontrolki, dokonując przekonwertowania na ciąg tekstowy <xref:System.Windows.Media.FormattedText> obiektu, a następnie narysować obiekt na formant <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="2bc88-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="2bc88-104">Można również użyć tej techniki dla rysunku do tła obiekty pochodzące z <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="2bc88-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="2bc88-105">![Formanty wyświetlania tekstu jako tło](./media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="2bc88-105">![Controls displaying text as background](./media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="2bc88-106">Przykład formantów z tła niestandardowego tekstu</span><span class="sxs-lookup"><span data-stu-id="2bc88-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bc88-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2bc88-107">Example</span></span>  
 <span data-ttu-id="2bc88-108">Aby narysować do tła kontrolki, Utwórz nowy <xref:System.Windows.Media.DrawingBrush> obiektu, a następnie narysuj tekst skonwertowany z obiektem <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="2bc88-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="2bc88-109">Następnie przypisz nowe <xref:System.Windows.Media.DrawingBrush> właściwości tła formantu.</span><span class="sxs-lookup"><span data-stu-id="2bc88-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="2bc88-110">Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu, a następnie narysuj do tła <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Button> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2bc88-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="2bc88-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bc88-111">See also</span></span>
- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="2bc88-112">Rysowanie formatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="2bc88-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
