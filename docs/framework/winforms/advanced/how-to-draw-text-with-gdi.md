---
title: 'Instrukcje: Rysowanie tekstu za pomocą GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956542"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="4f92b-102">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="4f92b-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="4f92b-103">Za pomocą <xref:System.Windows.Forms.TextRenderer> metody w klasie można uzyskać dostęp do funkcji GDI do rysowania tekstu w formularzu lub formancie. <xref:System.Windows.Forms.TextRenderer.DrawText%2A></span><span class="sxs-lookup"><span data-stu-id="4f92b-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access GDI functionality for drawing text on a form or control.</span></span> <span data-ttu-id="4f92b-104">Renderowanie tekstu GDI zwykle zapewnia lepszą wydajność i dokładniejsze mierzenie tekstu niż GDI+.</span><span class="sxs-lookup"><span data-stu-id="4f92b-104">GDI text rendering typically offers better performance and more accurate text measuring than GDI+.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f92b-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody<xref:System.Windows.Forms.TextRenderer> klasy nie są obsługiwane na potrzeby drukowania.</span><span class="sxs-lookup"><span data-stu-id="4f92b-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="4f92b-106">Podczas drukowania zawsze używaj <xref:System.Drawing.Graphics.DrawString%2A> metod <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="4f92b-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f92b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f92b-107">Example</span></span>  
 <span data-ttu-id="4f92b-108">Poniższy przykład kodu demonstruje sposób rysowania tekstu w wielu wierszach w prostokącie przy użyciu <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4f92b-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="4f92b-109">Aby renderować tekst <xref:System.Windows.Forms.TextRenderer> z klasą, potrzebna jest <xref:System.Drawing.IDeviceContext>, <xref:System.Drawing.Font>taka jak <xref:System.Drawing.Graphics> i, lokalizacja do rysowania tekstu oraz kolor, w którym ma zostać narysowany.</span><span class="sxs-lookup"><span data-stu-id="4f92b-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="4f92b-110">Opcjonalnie można określić formatowanie tekstu przy użyciu <xref:System.Windows.Forms.TextFormatFlags> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4f92b-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="4f92b-111">Aby uzyskać więcej informacji na temat <xref:System.Drawing.Graphics>uzyskiwania, [zobacz How to: Utwórz obiekty graficzne do rysowania](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="4f92b-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="4f92b-112">Aby uzyskać więcej informacji na temat konstruowania <xref:System.Drawing.Font>, zobacz [How to: Skonstruuj rodziny czcionek i czcionki](how-to-construct-font-families-and-fonts.md).</span><span class="sxs-lookup"><span data-stu-id="4f92b-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f92b-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4f92b-113">Compiling the Code</span></span>  
 <span data-ttu-id="4f92b-114">Poprzedni przykład kodu jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, <xref:System.Windows.Forms.PaintEventHandler>który jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="4f92b-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f92b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f92b-115">See also</span></span>

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="4f92b-116">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="4f92b-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
