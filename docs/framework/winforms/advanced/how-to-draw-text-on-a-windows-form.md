---
title: 'Instrukcje: Rysowanie tekstu w formularzu systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: ae7749deedba03f0a63bb74099d071d5da4fe27e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004084"
---
# <a name="how-to-draw-text-on-a-windows-form"></a><span data-ttu-id="cc79f-102">Instrukcje: Rysowanie tekstu w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cc79f-102">How to: Draw Text on a Windows Form</span></span>
<span data-ttu-id="cc79f-103">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> Rysowanie tekstu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="cc79f-103">The following code example shows how to use the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> to draw text on a form.</span></span> <span data-ttu-id="cc79f-104">Alternatywnie, można użyć <xref:System.Windows.Forms.TextRenderer> dla Rysowanie tekstu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="cc79f-104">Alternatively, you can use <xref:System.Windows.Forms.TextRenderer> for drawing text on a form.</span></span> <span data-ttu-id="cc79f-105">Aby uzyskać więcej informacji, zobacz [jak: Rysowanie tekstu za pomocą GDI](how-to-draw-text-with-gdi.md).</span><span class="sxs-lookup"><span data-stu-id="cc79f-105">For more information, see [How to: Draw Text with GDI](how-to-draw-text-with-gdi.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc79f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc79f-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cc79f-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cc79f-107">Compiling the Code</span></span>  
 <span data-ttu-id="cc79f-108">Nie można wywołać <xref:System.Drawing.Graphics.DrawString%2A> method in Class metoda <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cc79f-108">You cannot call the <xref:System.Drawing.Graphics.DrawString%2A> method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="cc79f-109">Rysowane zawartość nie zostanie narysowany ponownie, gdy formularz jest zmiany rozmiaru lub zostanie przesłonięty przez inny formularz.</span><span class="sxs-lookup"><span data-stu-id="cc79f-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="cc79f-110">Aby automatycznie odświeżenia zawartości, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cc79f-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cc79f-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="cc79f-111">Robust Programming</span></span>  
 <span data-ttu-id="cc79f-112">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="cc79f-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cc79f-113">Czcionka Arial nie jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="cc79f-113">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc79f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc79f-114">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Windows.Forms.TextRenderer.DrawText%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.TextFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="cc79f-115">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="cc79f-115">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="cc79f-116">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="cc79f-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
