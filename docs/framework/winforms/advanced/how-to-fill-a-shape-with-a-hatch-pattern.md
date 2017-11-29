---
title: "Porady: wypełnianie kształtów wzorem kreskowanym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36ee5b7152dabc7dcd1e0c844e8549eb03aa0045
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="fc5e6-102">Porady: wypełnianie kształtów wzorem kreskowanym</span><span class="sxs-lookup"><span data-stu-id="fc5e6-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="fc5e6-103">Wzorzec kreskowania staje się z dwóch kolorów: jeden dla tła i jeden dla wierszy, które tworzą wzorca w tle.</span><span class="sxs-lookup"><span data-stu-id="fc5e6-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="fc5e6-104">Aby wypełnić zamkniętego kształtów wzorem kreskowanym, użyj <xref:System.Drawing.Drawing2D.HatchBrush> obiektu.</span><span class="sxs-lookup"><span data-stu-id="fc5e6-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="fc5e6-105">W poniższym przykładzie pokazano sposób wypełniania elipsy wzorem kreskowanym:</span><span class="sxs-lookup"><span data-stu-id="fc5e6-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc5e6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc5e6-106">Example</span></span>  
 <span data-ttu-id="fc5e6-107"><xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Konstruktor ma trzy argumenty: Styl kreskowania, kolor kreskowania linii i kolor tła.</span><span class="sxs-lookup"><span data-stu-id="fc5e6-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="fc5e6-108">Argument Styl kreskowania może mieć dowolną wartość z <xref:System.Drawing.Drawing2D.HatchStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fc5e6-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="fc5e6-109">Istnieje więcej niż 50 elementów w <xref:System.Drawing.Drawing2D.HatchStyle> wyliczenie; niektóre z tych elementów są wyświetlane na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="fc5e6-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="fc5e6-110">Na poniższej ilustracji przedstawiono wypełnioną elipsę.</span><span class="sxs-lookup"><span data-stu-id="fc5e6-110">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="fc5e6-111">![Wzorzec kreskowania](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="fc5e6-111">![Hatch Pattern](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc5e6-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fc5e6-112">Compiling the Code</span></span>  
 <span data-ttu-id="fc5e6-113">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fc5e6-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5e6-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc5e6-114">See Also</span></span>  
 [<span data-ttu-id="fc5e6-115">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="fc5e6-115">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
