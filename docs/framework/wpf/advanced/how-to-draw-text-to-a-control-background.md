---
title: "Porady: Rysowanie tekstu do formantu &#39; s tła"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0c98422e337678e68a8e4b72979635e8c867b4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-to-a-control39s-background"></a><span data-ttu-id="666a8-102">Porady: Rysowanie tekstu do formantu &#39; s tła</span><span class="sxs-lookup"><span data-stu-id="666a8-102">How to: Draw Text to a Control&#39;s Background</span></span>
<span data-ttu-id="666a8-103">Tekst można narysować bezpośrednio do tła formantu, konwertując ciąg tekstowy do <xref:System.Windows.Media.FormattedText> obiekt, a następnie rysowania obiektu do formantu <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="666a8-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="666a8-104">Umożliwia także ta technika dla rysunku do tła obiekty pochodne <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="666a8-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="666a8-105">![Wyświetlanie tekstu jako tła formantów](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="666a8-105">![Controls displaying text as background](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="666a8-106">Przykład formantów z tła tekstu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="666a8-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="666a8-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="666a8-107">Example</span></span>  
 <span data-ttu-id="666a8-108">Aby narysować do tła formantu, Utwórz nową <xref:System.Windows.Media.DrawingBrush> obiektu i Rysuj tekst skonwertowany do obiektu <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="666a8-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="666a8-109">Następnie przypisz nowe <xref:System.Windows.Media.DrawingBrush> do właściwości tła formantu.</span><span class="sxs-lookup"><span data-stu-id="666a8-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="666a8-110">W poniższym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu i rysowanie do tła <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Button> obiektu.</span><span class="sxs-lookup"><span data-stu-id="666a8-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="666a8-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="666a8-111">See Also</span></span>  
 <xref:System.Windows.Media.FormattedText>  
 [<span data-ttu-id="666a8-112">Rysowanie sformatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="666a8-112">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
