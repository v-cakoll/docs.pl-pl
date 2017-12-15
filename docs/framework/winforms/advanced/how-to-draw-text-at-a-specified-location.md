---
title: "Porady: rysowanie tekstu w określonej lokalizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe6e8563b19ef18b89ad970f3ca35bf5f0782a32
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-draw-text-at-a-specified-location"></a><span data-ttu-id="eb9d3-102">Porady: rysowanie tekstu w określonej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="eb9d3-102">How to: Draw Text at a Specified Location</span></span>
<span data-ttu-id="eb9d3-103">Podczas wykonywania Rysowanie niestandardowe może wykonywać Rysowanie tekstu w jednej linii poziomej rozpoczynającą się w określonym punkcie.</span><span class="sxs-lookup"><span data-stu-id="eb9d3-103">When you perform custom drawing, you can draw text in a single horizontal line starting at a specified point.</span></span> <span data-ttu-id="eb9d3-104">W ten sposób można narysować tekstu przy użyciu <xref:System.Drawing.Graphics.DrawString%2A> przeciążona metoda <xref:System.Drawing.Graphics> klasy, która przyjmuje <xref:System.Drawing.Point> lub <xref:System.Drawing.PointF> parametru.</span><span class="sxs-lookup"><span data-stu-id="eb9d3-104">You can draw text in this manner by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Point> or <xref:System.Drawing.PointF> parameter.</span></span> <span data-ttu-id="eb9d3-105"><xref:System.Drawing.Graphics.DrawString%2A> Wymaga również metody <xref:System.Drawing.Brush> i<xref:System.Drawing.Font></span><span class="sxs-lookup"><span data-stu-id="eb9d3-105">The <xref:System.Drawing.Graphics.DrawString%2A> method also requires a <xref:System.Drawing.Brush> and <xref:System.Drawing.Font></span></span>  
  
 <span data-ttu-id="eb9d3-106">Można również użyć <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążona metoda <xref:System.Windows.Forms.TextRenderer> pobierającej <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="eb9d3-106">You can also use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Point>.</span></span> <span data-ttu-id="eb9d3-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A>wymaga również <xref:System.Drawing.Color> i <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="eb9d3-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> also requires a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="eb9d3-108">Na poniższej ilustracji przedstawiono dane wyjściowe tekstu w określonym momencie, gdy używasz <xref:System.Drawing.Graphics.DrawString%2A> przeciążonej metody.</span><span class="sxs-lookup"><span data-stu-id="eb9d3-108">The following illustration shows the output of text drawn at a specified point when you use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method.</span></span>  
  
 <span data-ttu-id="eb9d3-109">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")</span><span class="sxs-lookup"><span data-stu-id="eb9d3-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")</span></span>  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="eb9d3-110">Rysowanie linii tekstu z GDI +</span><span class="sxs-lookup"><span data-stu-id="eb9d3-110">To draw a line of text with GDI+</span></span>  
  
1.  <span data-ttu-id="eb9d3-111">Użyj <xref:System.Drawing.Graphics.DrawString%2A> jest metoda tekst, który ma, <xref:System.Drawing.Point> lub <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, i <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="eb9d3-111">Use the <xref:System.Drawing.Graphics.DrawString%2A> method, passing the text you want, <xref:System.Drawing.Point> or <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="eb9d3-112">Rysowanie linii tekstu z GDI</span><span class="sxs-lookup"><span data-stu-id="eb9d3-112">To draw a line of text with GDI</span></span>  
  
1.  <span data-ttu-id="eb9d3-113">Użyj <xref:System.Windows.Forms.TextRenderer.DrawText%2A> jest metoda tekst, który ma, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, i <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="eb9d3-113">Use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method, passing the text you want, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eb9d3-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="eb9d3-114">Compiling the Code</span></span>  
 <span data-ttu-id="eb9d3-115">Wymagaj poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="eb9d3-115">The previous examples require:</span></span>  
  
-   <span data-ttu-id="eb9d3-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, która jest parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="eb9d3-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9d3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb9d3-117">See Also</span></span>  
 [<span data-ttu-id="eb9d3-118">Instrukcje: rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="eb9d3-118">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="eb9d3-119">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="eb9d3-119">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="eb9d3-120">Instrukcje: tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="eb9d3-120">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [<span data-ttu-id="eb9d3-121">Instrukcje: rysowanie zawiniętego tekstu w prostokącie</span><span class="sxs-lookup"><span data-stu-id="eb9d3-121">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
