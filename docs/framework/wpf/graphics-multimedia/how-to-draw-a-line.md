---
title: Jak narysować linię
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: bee343676175098493df347823a3bdbdf17b205f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658447"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="0fd6a-102">Jak narysować linię</span><span class="sxs-lookup"><span data-stu-id="0fd6a-102">How to: Draw a Line</span></span>
<span data-ttu-id="0fd6a-103">W tym przykładzie pokazano, jak rysowanie linii za pomocą <xref:System.Windows.Shapes.Line> elementu.</span><span class="sxs-lookup"><span data-stu-id="0fd6a-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="0fd6a-104">Aby narysować linię, należy utworzyć <xref:System.Windows.Shapes.Line> elementu.</span><span class="sxs-lookup"><span data-stu-id="0fd6a-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="0fd6a-105">Użyj jego <xref:System.Windows.Shapes.Line.X1%2A> i <xref:System.Windows.Shapes.Line.Y1%2A> właściwości, aby ustawić jej punktu początkowego; i używać jej <xref:System.Windows.Shapes.Line.X2%2A> i <xref:System.Windows.Shapes.Line.Y2%2A> właściwości, aby ustawić jej punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="0fd6a-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="0fd6a-106">Wreszcie, ustaw jego <xref:System.Windows.Shapes.Shape.Stroke%2A> i <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> ponieważ wiersza bez obrysu jest niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="0fd6a-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="0fd6a-107">Ustawienie <xref:System.Windows.Shapes.Shape.Fill%2A> element wiersza nie ma wpływu, ponieważ ma nie wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="0fd6a-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="0fd6a-108">Poniższy przykład pobiera trzy wiersze wewnątrz <xref:System.Windows.Controls.Canvas> elementu.</span><span class="sxs-lookup"><span data-stu-id="0fd6a-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fd6a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fd6a-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="0fd6a-110">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe elementy kształtu](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="0fd6a-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd6a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fd6a-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Line>  
 [<span data-ttu-id="0fd6a-112">Przykładowe elementy kształtu</span><span class="sxs-lookup"><span data-stu-id="0fd6a-112">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
