---
title: "Używanie transformacji świata"
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
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5b2a8de0644e71a5e6ae1a5ca796f580f0c4f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-world-transformation"></a><span data-ttu-id="9af2d-102">Używanie transformacji świata</span><span class="sxs-lookup"><span data-stu-id="9af2d-102">Using the World Transformation</span></span>
<span data-ttu-id="9af2d-103">Transformacja świata jest właściwością <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="9af2d-103">The world transformation is a property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="9af2d-104">Numery, które określają transformacji świata są przechowywane w <xref:System.Drawing.Drawing2D.Matrix> obiekt, który reprezentuje macierzy 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="9af2d-104">The numbers that specify the world transformation are stored in a <xref:System.Drawing.Drawing2D.Matrix> object, which represents a 3×3 matrix.</span></span> <span data-ttu-id="9af2d-105"><xref:System.Drawing.Drawing2D.Matrix> i <xref:System.Drawing.Graphics> klasy mają kilka metod do ustawiania liczb w macierzy transformacji świata.</span><span class="sxs-lookup"><span data-stu-id="9af2d-105">The <xref:System.Drawing.Drawing2D.Matrix> and <xref:System.Drawing.Graphics> classes have several methods for setting the numbers in the world transformation matrix.</span></span>  
  
## <a name="different-types-of-transformations"></a><span data-ttu-id="9af2d-106">Różne typy przekształcenia</span><span class="sxs-lookup"><span data-stu-id="9af2d-106">Different Types of Transformations</span></span>  
 <span data-ttu-id="9af2d-107">W poniższym przykładzie kodu najpierw tworzy prostokąt 50 x 50 i znajduje się on w źródle (0, 0).</span><span class="sxs-lookup"><span data-stu-id="9af2d-107">In the following example, the code first creates a 50×50 rectangle and locates it at the origin (0, 0).</span></span> <span data-ttu-id="9af2d-108">Pochodzi w lewym górnym rogu obszaru klienckiego.</span><span class="sxs-lookup"><span data-stu-id="9af2d-108">The origin is at the upper-left corner of the client area.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 <span data-ttu-id="9af2d-109">Poniższy kod stosuje transformację skalowania, która rozszerza prostokąt o 1,75 w kierunku x i zmniejszana prostokąt według współczynnika 0,5 w kierunku y:</span><span class="sxs-lookup"><span data-stu-id="9af2d-109">The following code applies a scaling transformation that expands the rectangle by a factor of 1.75 in the x direction and shrinks the rectangle by a factor of 0.5 in the y direction:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 <span data-ttu-id="9af2d-110">Wynik jest prostokąt, który jest już w kierunku x i krótszy niż oryginalna kierunku y.</span><span class="sxs-lookup"><span data-stu-id="9af2d-110">The result is a rectangle that is longer in the x direction and shorter in the y direction than the original.</span></span>  
  
 <span data-ttu-id="9af2d-111">Obracanie prostokąt zamiast jej skalowania, należy użyć poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="9af2d-111">To rotate the rectangle instead of scaling it, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 <span data-ttu-id="9af2d-112">Tłumaczenie prostokąta, należy użyć poniższego kodu:</span><span class="sxs-lookup"><span data-stu-id="9af2d-112">To translate the rectangle, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="9af2d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9af2d-113">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [<span data-ttu-id="9af2d-114">Systemy i transformacje współrzędnych</span><span class="sxs-lookup"><span data-stu-id="9af2d-114">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="9af2d-115">Używanie przekształceń w zarządzanym GDI +</span><span class="sxs-lookup"><span data-stu-id="9af2d-115">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
