---
title: "Porady: spłaszczanie ścieżki krzywej do linii"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 334fc0fee7166f8f8c5c1db61d3b9e370da72f87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="a03c2-102">Porady: spłaszczanie ścieżki krzywej do linii</span><span class="sxs-lookup"><span data-stu-id="a03c2-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="a03c2-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt przechowuje sekwencji linii i krzywych Beziera.</span><span class="sxs-lookup"><span data-stu-id="a03c2-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="a03c2-104">Można dodać kilka typów krzywych (wielokropek, łuki, krzywe kardynalne) do ścieżki, ale każda krzywa jest konwertowana na krzywej Beziera przed znajduje się w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="a03c2-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="a03c2-105">Spłaszczanie ścieżki składa się z konwertowanie każdego krzywej Beziera w ścieżce do sekwencji proste.</span><span class="sxs-lookup"><span data-stu-id="a03c2-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="a03c2-106">Na poniższej ilustracji przedstawiono ścieżki przed i po spłaszczanie.</span><span class="sxs-lookup"><span data-stu-id="a03c2-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="a03c2-107">![Proste linii i krzywych](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="a03c2-107">![Straight Lines and Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="a03c2-108">Aby spłaszczanie ścieżki</span><span class="sxs-lookup"><span data-stu-id="a03c2-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="a03c2-109">wywołanie <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> metody <xref:System.Drawing.Drawing2D.GraphicsPath> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a03c2-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="a03c2-110"><xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> Metody odbiera argument płaskość, która określa maksymalną odległość między spłaszczoną ścieżkę i oryginalnej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a03c2-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03c2-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a03c2-111">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [<span data-ttu-id="a03c2-112">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="a03c2-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="a03c2-113">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="a03c2-113">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
