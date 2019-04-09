---
title: 'Instrukcje: Wypełnianie kształtów wzorem kreskowanym'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: f5399c4151b335090f4b93be041375b8c2781afa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118121"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="a7591-102">Instrukcje: Wypełnianie kształtów wzorem kreskowanym</span><span class="sxs-lookup"><span data-stu-id="a7591-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="a7591-103">Wzorem kreskowanym składa się z dwóch kolorów: jeden dla tła i jeden dla wierszy, które tworzą wzorzec nad tłem.</span><span class="sxs-lookup"><span data-stu-id="a7591-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="a7591-104">Aby wypełnić kształt zamknięty wzorem kreskowanym, należy użyć <xref:System.Drawing.Drawing2D.HatchBrush> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a7591-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="a7591-105">Poniższy przykład pokazuje, jak wypełnić elipsę wzorem kreskowanym:</span><span class="sxs-lookup"><span data-stu-id="a7591-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7591-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7591-106">Example</span></span>  
 <span data-ttu-id="a7591-107"><xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Konstruktor przyjmuje trzy argumenty: Styl kreskowania, kolor linii kreskowania i kolor tła.</span><span class="sxs-lookup"><span data-stu-id="a7591-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="a7591-108">Argument stylu kreskowania może być dowolną wartością z <xref:System.Drawing.Drawing2D.HatchStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a7591-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="a7591-109">Istnieje więcej niż 50 elementów w <xref:System.Drawing.Drawing2D.HatchStyle> wyliczenie; niektóre z tych elementów są wyświetlane na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="a7591-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="a7591-110">Poniższa ilustracja przedstawia wypełnioną elipsę.</span><span class="sxs-lookup"><span data-stu-id="a7591-110">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="a7591-111">![Hatch Pattern](./media/hatch1.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="a7591-111">![Hatch Pattern](./media/hatch1.png "hatch1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a7591-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a7591-112">Compiling the Code</span></span>  
 <span data-ttu-id="a7591-113">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs>`e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a7591-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7591-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7591-114">See also</span></span>

- [<span data-ttu-id="a7591-115">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="a7591-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
