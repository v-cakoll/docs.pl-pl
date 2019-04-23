---
title: 'Instrukcje: Rysowanie tekstu w określonej lokalizacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: f7834ea45db8dd6e971defd9c3b2b152ffddf512
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336411"
---
# <a name="how-to-draw-text-at-a-specified-location"></a><span data-ttu-id="114df-102">Instrukcje: Rysowanie tekstu w określonej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="114df-102">How to: Draw Text at a Specified Location</span></span>
<span data-ttu-id="114df-103">Podczas wykonywania niestandardowego rysowania można rysować tekst w pojedynczej linii poziomej, zaczynając od określonego punktu.</span><span class="sxs-lookup"><span data-stu-id="114df-103">When you perform custom drawing, you can draw text in a single horizontal line starting at a specified point.</span></span> <span data-ttu-id="114df-104">W ten sposób można rysować tekst przy użyciu <xref:System.Drawing.Graphics.DrawString%2A> przeciążone metody <xref:System.Drawing.Graphics> klasy, która przyjmuje <xref:System.Drawing.Point> lub <xref:System.Drawing.PointF> parametru.</span><span class="sxs-lookup"><span data-stu-id="114df-104">You can draw text in this manner by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Point> or <xref:System.Drawing.PointF> parameter.</span></span> <span data-ttu-id="114df-105"><xref:System.Drawing.Graphics.DrawString%2A> Wymaga również metoda <xref:System.Drawing.Brush> i <xref:System.Drawing.Font></span><span class="sxs-lookup"><span data-stu-id="114df-105">The <xref:System.Drawing.Graphics.DrawString%2A> method also requires a <xref:System.Drawing.Brush> and <xref:System.Drawing.Font></span></span>  
  
 <span data-ttu-id="114df-106">Można również użyć <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążone metody <xref:System.Windows.Forms.TextRenderer> przyjmującej <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="114df-106">You can also use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Point>.</span></span> <span data-ttu-id="114df-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> wymaga również <xref:System.Drawing.Color> i <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="114df-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> also requires a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="114df-108">Na poniższej ilustracji przedstawiono dane wyjściowe tekstu rysowane w określonym momencie, gdy używasz <xref:System.Drawing.Graphics.DrawString%2A> przeciążonej metody.</span><span class="sxs-lookup"><span data-stu-id="114df-108">The following illustration shows the output of text drawn at a specified point when you use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method.</span></span>  
  
 ![Zrzut ekranu pokazujący danych wyjściowych tekst w określonym momencie.](./media/how-to-draw-text-at-a-specified-location/font-text-specified-point.png)  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="114df-110">Aby narysować linię tekstu za pomocą GDI +</span><span class="sxs-lookup"><span data-stu-id="114df-110">To draw a line of text with GDI+</span></span>  
  
1. <span data-ttu-id="114df-111">Użyj <xref:System.Drawing.Graphics.DrawString%2A> jest metoda tekst, który ma, <xref:System.Drawing.Point> lub <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, i <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="114df-111">Use the <xref:System.Drawing.Graphics.DrawString%2A> method, passing the text you want, <xref:System.Drawing.Point> or <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="114df-112">Aby narysować linię tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="114df-112">To draw a line of text with GDI</span></span>  
  
1. <span data-ttu-id="114df-113">Użyj <xref:System.Windows.Forms.TextRenderer.DrawText%2A> jest metoda tekst, który ma, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, i <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="114df-113">Use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method, passing the text you want, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="114df-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="114df-114">Compiling the Code</span></span>  
 <span data-ttu-id="114df-115">Wymagaj poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="114df-115">The previous examples require:</span></span>  
  
-   <span data-ttu-id="114df-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="114df-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114df-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="114df-117">See also</span></span>

- [<span data-ttu-id="114df-118">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="114df-118">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="114df-119">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="114df-119">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="114df-120">Instrukcje: Tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="114df-120">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="114df-121">Instrukcje: Rysowanie zawiniętego tekstu w prostokącie</span><span class="sxs-lookup"><span data-stu-id="114df-121">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)
