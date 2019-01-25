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
ms.openlocfilehash: 3784c833098a5585c5cdc38014d5a9542daf39f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583409"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a><span data-ttu-id="3c7db-102">Ograniczenie powierzchni rysowania w GDI+</span><span class="sxs-lookup"><span data-stu-id="3c7db-102">Restricting the Drawing Surface in GDI+</span></span>
<span data-ttu-id="3c7db-103">Wycinka polega na ograniczenie rysunku do określonych regionów lub prostokąta.</span><span class="sxs-lookup"><span data-stu-id="3c7db-103">Clipping involves restricting drawing to a certain rectangle or region.</span></span> <span data-ttu-id="3c7db-104">Poniższa ilustracja przedstawia ciąg "Hello" przycinana w kształcie serca regionie.</span><span class="sxs-lookup"><span data-stu-id="3c7db-104">The following illustration shows the string "Hello" clipped to a heart-shaped region.</span></span>  
  
 <span data-ttu-id="3c7db-105">![Rysowanie powierzchnię z ograniczeniami](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span><span class="sxs-lookup"><span data-stu-id="3c7db-105">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span></span>  
  
## <a name="clipping-with-regions"></a><span data-ttu-id="3c7db-106">Obcinanie przy użyciu regionów</span><span class="sxs-lookup"><span data-stu-id="3c7db-106">Clipping with Regions</span></span>  
 <span data-ttu-id="3c7db-107">Regiony mogą zostać utworzone na podstawie ścieżki, a ścieżki mogą zawierać konturów ciągów, aby można było używać schemat tekstu dla wycinka.</span><span class="sxs-lookup"><span data-stu-id="3c7db-107">Regions can be constructed from paths, and paths can contain the outlines of strings, so you can use outlined text for clipping.</span></span> <span data-ttu-id="3c7db-108">Poniższa ilustracja przedstawia zestaw koncentrycznych wielokropek przycinane do wnętrza ciągu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="3c7db-108">The following illustration shows a set of concentric ellipses clipped to the interior of a string of text.</span></span>  
  
 <span data-ttu-id="3c7db-109">![Rysowanie powierzchnię z ograniczeniami](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span><span class="sxs-lookup"><span data-stu-id="3c7db-109">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span></span>  
  
 <span data-ttu-id="3c7db-110">Aby rysować wycinka, należy utworzyć <xref:System.Drawing.Graphics> obiektu, ustaw jego <xref:System.Drawing.Graphics.Clip%2A> właściwości, a następnie wywołać tej samej metody rysowania <xref:System.Drawing.Graphics> obiektu:</span><span class="sxs-lookup"><span data-stu-id="3c7db-110">To draw with clipping, create a <xref:System.Drawing.Graphics> object, set its <xref:System.Drawing.Graphics.Clip%2A> property, and then call the drawing methods of that same <xref:System.Drawing.Graphics> object:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a><span data-ttu-id="3c7db-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c7db-111">See also</span></span>
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [<span data-ttu-id="3c7db-112">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="3c7db-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="3c7db-113">Używanie regionów</span><span class="sxs-lookup"><span data-stu-id="3c7db-113">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
