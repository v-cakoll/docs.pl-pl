---
title: 'Porady: rysowanie zawiniętego tekstu w prostokącie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: c753be6a200f166e59e1330c7dbcf1fadc7588a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524976"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="e8c97-102">Porady: rysowanie zawiniętego tekstu w prostokącie</span><span class="sxs-lookup"><span data-stu-id="e8c97-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="e8c97-103">Można Rysowanie zawiniętego tekstu w prostokącie przy użyciu <xref:System.Drawing.Graphics.DrawString%2A> przeciążona metoda <xref:System.Drawing.Graphics> klasy, która przyjmuje <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF> parametru.</span><span class="sxs-lookup"><span data-stu-id="e8c97-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="e8c97-104">Ponadto <xref:System.Drawing.Brush> i <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="e8c97-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="e8c97-105">Zawijanie tekstu może Rysowanie w prostokącie, za pomocą <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążona metoda <xref:System.Windows.Forms.TextRenderer> pobierającej <xref:System.Drawing.Rectangle> i <xref:System.Windows.Forms.TextFormatFlags> parametru.</span><span class="sxs-lookup"><span data-stu-id="e8c97-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="e8c97-106">Ponadto <xref:System.Drawing.Color> i <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="e8c97-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="e8c97-107">Na poniższej ilustracji przedstawiono dane wyjściowe tekstu w prostokącie, korzystając z <xref:System.Drawing.Graphics.DrawString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e8c97-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method.</span></span>  
  
 <span data-ttu-id="e8c97-108">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")</span><span class="sxs-lookup"><span data-stu-id="e8c97-108">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")</span></span>  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="e8c97-109">Rysowanie zawiniętego tekstu w prostokącie z GDI +</span><span class="sxs-lookup"><span data-stu-id="e8c97-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1.  <span data-ttu-id="e8c97-110">Użyj <xref:System.Drawing.Graphics.DrawString%2A> przeciążona metoda przekazywanie tekst, który ma, <xref:System.Drawing.Rectangle> lub <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> i <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="e8c97-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="e8c97-111">Rysowanie zawiniętego tekstu w prostokącie za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="e8c97-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1.  <span data-ttu-id="e8c97-112">Użyj <xref:System.Windows.Forms.TextFormatFlags> wartość wyliczenia do Podaj tekst, który musi być ujęte z <xref:System.Windows.Forms.TextRenderer.DrawText%2A> przeciążona metoda przekazywanie tekst, który ma, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> i <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="e8c97-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8c97-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e8c97-113">Compiling the Code</span></span>  
 <span data-ttu-id="e8c97-114">Wymagaj poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="e8c97-114">The previous examples require:</span></span>  
  
-   <span data-ttu-id="e8c97-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, która jest parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="e8c97-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c97-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8c97-116">See Also</span></span>  
 [<span data-ttu-id="e8c97-117">Instrukcje: rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="e8c97-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="e8c97-118">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="e8c97-118">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="e8c97-119">Instrukcje: tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="e8c97-119">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [<span data-ttu-id="e8c97-120">Instrukcje: rysowanie tekstu w określonej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="e8c97-120">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
