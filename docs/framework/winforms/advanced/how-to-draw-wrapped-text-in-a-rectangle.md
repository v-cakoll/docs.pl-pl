---
title: 'Instrukcje: Rysowanie zawiniętego tekstu w prostokącie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: 8e5c7cab1f977bef0570b2e540d7bf3a630aceb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781403"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="9e0a4-102">Instrukcje: Rysowanie zawiniętego tekstu w prostokącie</span><span class="sxs-lookup"><span data-stu-id="9e0a4-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="9e0a4-103">Zawijanie tekstu w prostokącie można rysować za pomocą <xref:System.Drawing.Graphics.DrawString%2A> przeciążone metody <xref:System.Drawing.Graphics> klasy, która przyjmuje <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF> parametru.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="9e0a4-104">Ponadto <xref:System.Drawing.Brush> i <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="9e0a4-105">Można też rysować zawiniętego tekstu w prostokącie, za pomocą <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążone metody <xref:System.Windows.Forms.TextRenderer> przyjmującej <xref:System.Drawing.Rectangle> i <xref:System.Windows.Forms.TextFormatFlags> parametru.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="9e0a4-106">Ponadto <xref:System.Drawing.Color> i <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="9e0a4-107">Na poniższej ilustracji przedstawiono dane wyjściowe tekstu rysowane w prostokącie, gdy używasz <xref:System.Drawing.Graphics.DrawString%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="9e0a4-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method:</span></span>
  
 ![Zrzut ekranu pokazujący dane wyjściowe w przypadku korzystania z metody sznurkiem.](./media/how-to-draw-wrapped-text-in-a-rectangle/drawstring-method-font-text.png)  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="9e0a4-109">Rysowanie zawiniętego tekstu w prostokącie za pomocą GDI +</span><span class="sxs-lookup"><span data-stu-id="9e0a4-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1. <span data-ttu-id="9e0a4-110">Użyj <xref:System.Drawing.Graphics.DrawString%2A> przeciążonej metody, przekazując tekst, który ma, <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> i <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="9e0a4-111">Rysowanie zawiniętego tekstu w prostokącie za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="9e0a4-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1. <span data-ttu-id="9e0a4-112">Użyj <xref:System.Windows.Forms.TextFormatFlags> powinna być otoczona wartość wyliczenia, aby określić tekst z <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążonej metody, przekazując tekst, który ma, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> i <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9e0a4-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9e0a4-113">Compiling the Code</span></span>  
 <span data-ttu-id="9e0a4-114">Wymagaj poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="9e0a4-114">The previous examples require:</span></span>  
  
- <span data-ttu-id="9e0a4-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0a4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e0a4-116">See also</span></span>

- [<span data-ttu-id="9e0a4-117">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="9e0a4-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="9e0a4-118">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="9e0a4-118">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="9e0a4-119">Instrukcje: Tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="9e0a4-119">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="9e0a4-120">Instrukcje: Rysowanie tekstu w określonej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="9e0a4-120">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)
