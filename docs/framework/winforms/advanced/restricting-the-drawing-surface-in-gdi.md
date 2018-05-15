---
title: Ograniczenie powierzchni rysowania w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: b457e94acb334dc012f017090c63189de372592d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="restricting-the-drawing-surface-in-gdi"></a><span data-ttu-id="d86fb-102">Ograniczenie powierzchni rysowania w GDI+</span><span class="sxs-lookup"><span data-stu-id="d86fb-102">Restricting the Drawing Surface in GDI+</span></span>
<span data-ttu-id="d86fb-103">Wycinka obejmuje ograniczenie rysunku do niektórych prostokąta lub regionu.</span><span class="sxs-lookup"><span data-stu-id="d86fb-103">Clipping involves restricting drawing to a certain rectangle or region.</span></span> <span data-ttu-id="d86fb-104">Na poniższej ilustracji przedstawiono ciąg "Hello" przycinana w kształcie serca regionie.</span><span class="sxs-lookup"><span data-stu-id="d86fb-104">The following illustration shows the string "Hello" clipped to a heart-shaped region.</span></span>  
  
 <span data-ttu-id="d86fb-105">![Ograniczone powierzchni rysowania](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span><span class="sxs-lookup"><span data-stu-id="d86fb-105">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span></span>  
  
## <a name="clipping-with-regions"></a><span data-ttu-id="d86fb-106">Wycinek z regionów</span><span class="sxs-lookup"><span data-stu-id="d86fb-106">Clipping with Regions</span></span>  
 <span data-ttu-id="d86fb-107">Regiony mogą zostać utworzone na podstawie ścieżki i ścieżki może zawierać opisanych ciągów, dzięki czemu można używać obramowane tekstu dla wycinka.</span><span class="sxs-lookup"><span data-stu-id="d86fb-107">Regions can be constructed from paths, and paths can contain the outlines of strings, so you can use outlined text for clipping.</span></span> <span data-ttu-id="d86fb-108">Na poniższej ilustracji przedstawiono zestaw koncentrycznych wielokropek obcięta wewnątrz ciągu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="d86fb-108">The following illustration shows a set of concentric ellipses clipped to the interior of a string of text.</span></span>  
  
 <span data-ttu-id="d86fb-109">![Ograniczone powierzchni rysowania](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span><span class="sxs-lookup"><span data-stu-id="d86fb-109">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span></span>  
  
 <span data-ttu-id="d86fb-110">Aby rysować wycinka, Utwórz <xref:System.Drawing.Graphics> obiekt, ustaw jej <xref:System.Drawing.Graphics.Clip%2A> właściwości, a następnie wywołać metody rysowania w tej samej <xref:System.Drawing.Graphics> obiektu:</span><span class="sxs-lookup"><span data-stu-id="d86fb-110">To draw with clipping, create a <xref:System.Drawing.Graphics> object, set its <xref:System.Drawing.Graphics.Clip%2A> property, and then call the drawing methods of that same <xref:System.Drawing.Graphics> object:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a><span data-ttu-id="d86fb-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d86fb-111">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="d86fb-112">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="d86fb-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="d86fb-113">Używanie regionów</span><span class="sxs-lookup"><span data-stu-id="d86fb-113">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
