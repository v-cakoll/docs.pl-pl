---
title: 'Porady: rysowanie tekstu za pomocą GDI'
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
ms.openlocfilehash: e18ff96ea97eb636de8ab73aaa094c07b10fd456
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522918"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="f62f2-102">Porady: rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="f62f2-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="f62f2-103">Z <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody w <xref:System.Windows.Forms.TextRenderer> klasy, można uzyskać dostęp [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] funkcji Rysowanie tekstu na formularz lub formant.</span><span class="sxs-lookup"><span data-stu-id="f62f2-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] functionality for drawing text on a form or control.</span></span> [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]<span data-ttu-id="f62f2-104"> Renderowanie tekstu zwykle zapewnia lepszą wydajność i dokładniejsze tekst pomiaru niż [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f62f2-104"> text rendering typically offers better performance and more accurate text measuring than [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f62f2-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> klasy nie są obsługiwane do drukowania.</span><span class="sxs-lookup"><span data-stu-id="f62f2-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="f62f2-106">Podczas drukowania, należy zawsze używać <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="f62f2-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f62f2-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f62f2-107">Example</span></span>  
 <span data-ttu-id="f62f2-108">W poniższym przykładzie pokazano, jak rysowanie tekstu w wielu wierszach w prostokącie przy użyciu <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f62f2-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="f62f2-109">Do renderowania tekstu w <xref:System.Windows.Forms.TextRenderer> klasy, należy <xref:System.Drawing.IDeviceContext>, takich jak <xref:System.Drawing.Graphics> i <xref:System.Drawing.Font>, lokalizacji do rysowania tekstu i kolor, w którym ma być rysowany.</span><span class="sxs-lookup"><span data-stu-id="f62f2-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="f62f2-110">Opcjonalnie można określić formatowanie przy użyciu tekstu <xref:System.Windows.Forms.TextFormatFlags> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f62f2-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="f62f2-111">Aby uzyskać więcej informacji na temat uzyskiwania <xref:System.Drawing.Graphics>, zobacz [porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="f62f2-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="f62f2-112">Aby uzyskać więcej informacji na temat tworzenia <xref:System.Drawing.Font>, zobacz [jak: utworzyć rodzin czcionek i czcionek](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span><span class="sxs-lookup"><span data-stu-id="f62f2-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f62f2-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f62f2-113">Compiling the Code</span></span>  
 <span data-ttu-id="f62f2-114">W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f62f2-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f62f2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f62f2-115">See Also</span></span>  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [<span data-ttu-id="f62f2-116">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="f62f2-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
