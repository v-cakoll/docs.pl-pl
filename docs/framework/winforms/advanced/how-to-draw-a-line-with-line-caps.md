---
title: 'Instrukcje: Rysowanie linii z zakończeniem linii'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: 05c678b25563eb7a4e2e5ce0e49138b5445b4764
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707602"
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="201f0-102">Instrukcje: Rysowanie linii z zakończeniem linii</span><span class="sxs-lookup"><span data-stu-id="201f0-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="201f0-103">Możesz narysować początek lub koniec wiersza w jednym z kilku kształtów wywoływana z zakończeniem linii.</span><span class="sxs-lookup"><span data-stu-id="201f0-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="201f0-104">obsługuje kilka zakończeniem linii, takich jak round, kwadratowy, romb i grotu strzałki.</span><span class="sxs-lookup"><span data-stu-id="201f0-104">supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="201f0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="201f0-105">Example</span></span>  
 <span data-ttu-id="201f0-106">Możesz określić limity wiersz na początku wiersza (start cap), na koniec wiersza (zakończenie) lub łączniki linii kreskowanej (kreska cap).</span><span class="sxs-lookup"><span data-stu-id="201f0-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="201f0-107">Poniższy przykład rysuje za pomocą strzałki na jednym końcu i okrągłe zakończenie na końcu.</span><span class="sxs-lookup"><span data-stu-id="201f0-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="201f0-108">Na ilustracji przedstawiono wynikowego wiersza:</span><span class="sxs-lookup"><span data-stu-id="201f0-108">The illustration shows the resulting line:</span></span>  
  
 <span data-ttu-id="201f0-109">![Pióra](./media/pens4.gif "pens4")</span><span class="sxs-lookup"><span data-stu-id="201f0-109">![Pens](./media/pens4.gif "pens4")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="201f0-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="201f0-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="201f0-111">Tworzenie formularza Windows i obsłużyć formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="201f0-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="201f0-112">Wklej przykładowy kod do <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń, przekazując `e` jako <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="201f0-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201f0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="201f0-113">See also</span></span>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [<span data-ttu-id="201f0-114">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="201f0-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="201f0-115">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="201f0-115">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
