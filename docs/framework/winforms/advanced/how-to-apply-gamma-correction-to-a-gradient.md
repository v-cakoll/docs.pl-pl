---
title: 'Instrukcje: Stosowanie korekcji gamma do gradientu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: 066ccc649105018d20cb86b6e576a1a238e0dc62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973269"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="6b042-102">Instrukcje: Stosowanie korekcji gamma do gradientu</span><span class="sxs-lookup"><span data-stu-id="6b042-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="6b042-103">Możesz włączyć korekcji gamma pędzel gradientów liniowych, ustawiając pędzla <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="6b042-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="6b042-104">Korekcja gamma można wyłączyć, ustawiając <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="6b042-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="6b042-105">Korekcja gamma jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="6b042-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b042-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b042-106">Example</span></span>  

<span data-ttu-id="6b042-107">Poniższy przykład jest metodą, która jest wywoływana z kontrolki <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6b042-107">The following example is a method that is called from a control's <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="6b042-108">W przykładzie utworzono pędzel gradientów liniowych i używa tego pędzla do wypełniania dwoma prostokątami.</span><span class="sxs-lookup"><span data-stu-id="6b042-108">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="6b042-109">Pierwszy prostokąt zostanie wypełnione bez korekcji gamma, a drugi prostokąta jest wypełniany korekcji gamma.</span><span class="sxs-lookup"><span data-stu-id="6b042-109">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="6b042-110">Poniższa ilustracja przedstawia dwoma prostokątami wypełniony.</span><span class="sxs-lookup"><span data-stu-id="6b042-110">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="6b042-111">Najważniejsze prostokąt, którego nie ma korekcji gamma, pojawi się ciemny w środku.</span><span class="sxs-lookup"><span data-stu-id="6b042-111">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="6b042-112">Prostokąt dolnej, mającej korekcja gamma wydaje się mieć więcej intensywność jednolite.</span><span class="sxs-lookup"><span data-stu-id="6b042-112">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 <span data-ttu-id="6b042-113">![Gradient](./media/gammagradient1.png "gammagradient1")</span><span class="sxs-lookup"><span data-stu-id="6b042-113">![Gradient](./media/gammagradient1.png "gammagradient1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b042-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6b042-114">Compiling the Code</span></span>  
 <span data-ttu-id="6b042-115">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6b042-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b042-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b042-116">See also</span></span>

- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="6b042-117">Używanie pędzla gradientów do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="6b042-117">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
