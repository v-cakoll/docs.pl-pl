---
title: 'Instrukcje: Spłaszczanie ścieżki krzywej do linii'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: aa47a655417cdf82d79fb222dc6ff6f6d8c3a947
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601821"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="18b3d-102">Instrukcje: Spłaszczanie ścieżki krzywej do linii</span><span class="sxs-lookup"><span data-stu-id="18b3d-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="18b3d-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt przechowuje sekwencji linii i krzywych Beziera.</span><span class="sxs-lookup"><span data-stu-id="18b3d-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="18b3d-104">Można dodać kilka typów krzywych (wielokropek, łuki kardynalne) do ścieżki, ale każda krzywa jest konwertowany na krzywej Beziera, zanim znajduje się w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="18b3d-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="18b3d-105">Spłaszczanie ścieżki składa się z konwersji każdego krzywej Beziera w ścieżce z linii prostych sekwencji.</span><span class="sxs-lookup"><span data-stu-id="18b3d-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="18b3d-106">Na poniższej ilustracji przedstawiono ścieżkę przed i po nim spłaszczanie.</span><span class="sxs-lookup"><span data-stu-id="18b3d-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="18b3d-107">![Proste linii i krzywych](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="18b3d-107">![Straight Lines and Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="18b3d-108">Spłaszczanie ścieżki</span><span class="sxs-lookup"><span data-stu-id="18b3d-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="18b3d-109">Wywołaj <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> metody <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu.</span><span class="sxs-lookup"><span data-stu-id="18b3d-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="18b3d-110"><xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Metoda otrzymuje argument płaskość, który określa maksymalną odległość między ścieżką spłaszczone i Oryginalna ścieżka.</span><span class="sxs-lookup"><span data-stu-id="18b3d-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b3d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18b3d-111">See also</span></span>
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [<span data-ttu-id="18b3d-112">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="18b3d-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="18b3d-113">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="18b3d-113">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
