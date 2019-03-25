---
title: 'Instrukcje: Rysowanie niestandardowej linii kreskowanej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 06555309b8432397e754bc9dfa717c89b052343f
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410228"
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="f791e-102">Porady: Rysowanie niestandardowej linii kreskowanej</span><span class="sxs-lookup"><span data-stu-id="f791e-102">How to: Draw a Custom Dashed Line</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="f791e-103">dostępnych jest kilka typów dash, które są wymienione w <xref:System.Drawing.Drawing2D.DashStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f791e-103">provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="f791e-104">Jeśli te style standard dash nie spełnia Twoich potrzeb, można utworzyć wzorze kreskowym niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f791e-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f791e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f791e-105">Example</span></span>  
 <span data-ttu-id="f791e-106">Rysowanie niestandardowej linii kreskowanej, umieścić długości kresek i spacji w tablicy, a następnie przypisać tablicę jako wartość <xref:System.Drawing.Pen.DashPattern%2A> właściwość <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f791e-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="f791e-107">Poniższy przykład pobiera niestandardowej linii kreskowanej oparte na tablicy `{5, 2, 15, 4}`.</span><span class="sxs-lookup"><span data-stu-id="f791e-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="f791e-108">Jeśli elementy tablicy są mnożenia szerokość pióra, 5, możesz uzyskać `{25, 10, 75, 20}`.</span><span class="sxs-lookup"><span data-stu-id="f791e-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="f791e-109">Łączniki wyświetlanych alternatywny o długości od 25 do 75 i spacje alternatywny o długości od 10 do 20.</span><span class="sxs-lookup"><span data-stu-id="f791e-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="f791e-110">Poniższa ilustracja przedstawia wynikowy linia przerywana.</span><span class="sxs-lookup"><span data-stu-id="f791e-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="f791e-111">Należy zauważyć, że końcowej kreski, musi być krótsza niż 25 jednostek, tak, aby zakończyć w wierszu (405, 5).</span><span class="sxs-lookup"><span data-stu-id="f791e-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="f791e-112">![Ilustracja przedstawiająca linia przerywana. ](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="f791e-112">![Illustration that shows a dashed line.](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f791e-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f791e-113">Compiling the Code</span></span>  
 <span data-ttu-id="f791e-114">Tworzenie formularza Windows i obsłużyć formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f791e-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="f791e-115">Wklej poprzedni kod z gałęzią <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f791e-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f791e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f791e-116">See also</span></span>
- [<span data-ttu-id="f791e-117">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="f791e-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
