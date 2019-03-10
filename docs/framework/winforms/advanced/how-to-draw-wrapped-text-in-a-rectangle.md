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
ms.openlocfilehash: 5c4e76cda37527d0167b21c0d206749ba6dab4a9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708863"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="9d5e8-102">Instrukcje: Rysowanie zawiniętego tekstu w prostokącie</span><span class="sxs-lookup"><span data-stu-id="9d5e8-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="9d5e8-103">Zawijanie tekstu w prostokącie można rysować za pomocą <xref:System.Drawing.Graphics.DrawString%2A> przeciążone metody <xref:System.Drawing.Graphics> klasy, która przyjmuje <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF> parametru.</span><span class="sxs-lookup"><span data-stu-id="9d5e8-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="9d5e8-104">Ponadto <xref:System.Drawing.Brush> i <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="9d5e8-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="9d5e8-105">Można też rysować zawiniętego tekstu w prostokącie, za pomocą <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążone metody <xref:System.Windows.Forms.TextRenderer> przyjmującej <xref:System.Drawing.Rectangle> i <xref:System.Windows.Forms.TextFormatFlags> parametru.</span><span class="sxs-lookup"><span data-stu-id="9d5e8-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="9d5e8-106">Ponadto <xref:System.Drawing.Color> i <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="9d5e8-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="9d5e8-107">Na poniższej ilustracji przedstawiono dane wyjściowe tekstu rysowane w prostokącie, gdy używasz <xref:System.Drawing.Graphics.DrawString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9d5e8-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method.</span></span>  
  
 <span data-ttu-id="9d5e8-108">![Fonts Text](./media/csfontstext2.png "csfontstext2")</span><span class="sxs-lookup"><span data-stu-id="9d5e8-108">![Fonts Text](./media/csfontstext2.png "csfontstext2")</span></span>  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="9d5e8-109">Rysowanie zawiniętego tekstu w prostokącie za pomocą GDI +</span><span class="sxs-lookup"><span data-stu-id="9d5e8-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1.  <span data-ttu-id="9d5e8-110">Użyj <xref:System.Drawing.Graphics.DrawString%2A> przeciążonej metody, przekazując tekst, który ma, <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> i <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="9d5e8-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="9d5e8-111">Rysowanie zawiniętego tekstu w prostokącie za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="9d5e8-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1.  <span data-ttu-id="9d5e8-112">Użyj <xref:System.Windows.Forms.TextFormatFlags> powinna być otoczona wartość wyliczenia, aby określić tekst z <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążonej metody, przekazując tekst, który ma, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> i <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="9d5e8-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d5e8-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="9d5e8-113">Compiling the Code</span></span>  
 <span data-ttu-id="9d5e8-114">Wymagaj poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="9d5e8-114">The previous examples require:</span></span>  
  
-   <span data-ttu-id="9d5e8-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="9d5e8-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d5e8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d5e8-116">See also</span></span>
- [<span data-ttu-id="9d5e8-117">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="9d5e8-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="9d5e8-118">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="9d5e8-118">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="9d5e8-119">Instrukcje: Tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="9d5e8-119">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="9d5e8-120">Instrukcje: Rysowanie tekstu w określonej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="9d5e8-120">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)
