---
title: Używanie transformacji świata
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: cc6bcca42e84580199f75c64087af6d98f476d4b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715701"
---
# <a name="using-the-world-transformation"></a><span data-ttu-id="006ca-102">Używanie transformacji świata</span><span class="sxs-lookup"><span data-stu-id="006ca-102">Using the World Transformation</span></span>
<span data-ttu-id="006ca-103">Transformacja świata jest właściwością <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="006ca-103">The world transformation is a property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="006ca-104">Numery, które określają transformacji świata są przechowywane w <xref:System.Drawing.Drawing2D.Matrix> obiekt, który reprezentuje macierzy 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="006ca-104">The numbers that specify the world transformation are stored in a <xref:System.Drawing.Drawing2D.Matrix> object, which represents a 3×3 matrix.</span></span> <span data-ttu-id="006ca-105"><xref:System.Drawing.Drawing2D.Matrix> i <xref:System.Drawing.Graphics> klasy mają kilka metod ustawienie liczby w macierzy transformacji świata.</span><span class="sxs-lookup"><span data-stu-id="006ca-105">The <xref:System.Drawing.Drawing2D.Matrix> and <xref:System.Drawing.Graphics> classes have several methods for setting the numbers in the world transformation matrix.</span></span>  
  
## <a name="different-types-of-transformations"></a><span data-ttu-id="006ca-106">Różne rodzaje przekształcenia</span><span class="sxs-lookup"><span data-stu-id="006ca-106">Different Types of Transformations</span></span>  
 <span data-ttu-id="006ca-107">W poniższym przykładzie kod najpierw tworzy prostokąt, 50 x 50 i lokalizuje go w miejscu pochodzenia (0, 0).</span><span class="sxs-lookup"><span data-stu-id="006ca-107">In the following example, the code first creates a 50×50 rectangle and locates it at the origin (0, 0).</span></span> <span data-ttu-id="006ca-108">Początek znajduje się w lewym górnym rogu obszaru klienta.</span><span class="sxs-lookup"><span data-stu-id="006ca-108">The origin is at the upper-left corner of the client area.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 <span data-ttu-id="006ca-109">Poniższy kod stosuje przekształcenia skalowania, które rozszerza prostokąt o 1,75 w kierunku x i zmniejsza prostokąt o 0,5 w kierunku y:</span><span class="sxs-lookup"><span data-stu-id="006ca-109">The following code applies a scaling transformation that expands the rectangle by a factor of 1.75 in the x direction and shrinks the rectangle by a factor of 0.5 in the y direction:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 <span data-ttu-id="006ca-110">Wynik jest prostokąt, tym dłużej w kierunku x i krótszy w kierunku y niż oryginał.</span><span class="sxs-lookup"><span data-stu-id="006ca-110">The result is a rectangle that is longer in the x direction and shorter in the y direction than the original.</span></span>  
  
 <span data-ttu-id="006ca-111">Aby obrócić prostokąt zamiast jej skalowania, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="006ca-111">To rotate the rectangle instead of scaling it, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 <span data-ttu-id="006ca-112">Aby przetłumaczyć prostokąt, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="006ca-112">To translate the rectangle, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="006ca-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="006ca-113">See also</span></span>
- <xref:System.Drawing.Drawing2D.Matrix>
- [<span data-ttu-id="006ca-114">Systemy i przekształcenia współrzędnych</span><span class="sxs-lookup"><span data-stu-id="006ca-114">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="006ca-115">Używanie przekształceń w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="006ca-115">Using Transformations in Managed GDI+</span></span>](using-transformations-in-managed-gdi.md)
