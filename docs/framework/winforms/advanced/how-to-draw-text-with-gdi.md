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
ms.openlocfilehash: 644e180e2f15592db2112a5cd6f5b0130c6abea8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722334"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="f5d0d-102">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="f5d0d-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="f5d0d-103">Za pomocą <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in Class metoda <xref:System.Windows.Forms.TextRenderer> klasy, możesz uzyskać dostęp [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] funkcji Rysowanie tekstu na formularz lub formant.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] functionality for drawing text on a form or control.</span></span> [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] <span data-ttu-id="f5d0d-104">Renderowanie tekstu zwykle zapewnia lepszą wydajność i bardziej precyzyjne tekstu pomiaru niż [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f5d0d-104">text rendering typically offers better performance and more accurate text measuring than [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5d0d-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> klasy nie są obsługiwane w przypadku drukowania.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="f5d0d-106">Podczas drukowania, należy zawsze używać <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5d0d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5d0d-107">Example</span></span>  
 <span data-ttu-id="f5d0d-108">Poniższy przykład kodu pokazuje, jak rysować tekst w wielu wierszach, w obrębie prostokąta za pomocą <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="f5d0d-109">Aby renderować tekstu za pomocą <xref:System.Windows.Forms.TextRenderer> klasy, należy <xref:System.Drawing.IDeviceContext>, takich jak <xref:System.Drawing.Graphics> i <xref:System.Drawing.Font>, lokalizację w której Rysowanie tekstu i kolorów, w którym ma być rysowany.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="f5d0d-110">Opcjonalnie można określić za pomocą do formatowania tekstu <xref:System.Windows.Forms.TextFormatFlags> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="f5d0d-111">Aby uzyskać więcej informacji na temat uzyskiwania <xref:System.Drawing.Graphics>, zobacz [jak: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="f5d0d-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="f5d0d-112">Aby uzyskać więcej informacji na temat tworzenia <xref:System.Drawing.Font>, zobacz [jak: Tworzenie rodzin czcionek i czcionek](how-to-construct-font-families-and-fonts.md).</span><span class="sxs-lookup"><span data-stu-id="f5d0d-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f5d0d-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f5d0d-113">Compiling the Code</span></span>  
 <span data-ttu-id="f5d0d-114">W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f5d0d-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d0d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5d0d-115">See also</span></span>
- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="f5d0d-116">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="f5d0d-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
