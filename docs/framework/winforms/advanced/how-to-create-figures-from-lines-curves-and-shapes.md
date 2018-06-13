---
title: 'Porady: tworzenie figur z linii, krzywych i kształtów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: 222245fa4b3b593e0a38752a8cb991a12e469698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521859"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a><span data-ttu-id="6818c-102">Porady: tworzenie figur z linii, krzywych i kształtów</span><span class="sxs-lookup"><span data-stu-id="6818c-102">How to: Create Figures from Lines, Curves, and Shapes</span></span>
<span data-ttu-id="6818c-103">Do utworzenia rysunku, należy utworzyć <xref:System.Drawing.Drawing2D.GraphicsPath>, a następnie wywołać metod, takich jak <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, aby dodać elementów podstawowych do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="6818c-103">To create a figure, construct a <xref:System.Drawing.Drawing2D.GraphicsPath>, and then call methods, such as <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, to add primitives to the path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6818c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6818c-104">Example</span></span>  
 <span data-ttu-id="6818c-105">W poniższych przykładach kodu Utwórz ścieżek, które mają dane:</span><span class="sxs-lookup"><span data-stu-id="6818c-105">The following code examples create paths that have figures:</span></span>  
  
-   <span data-ttu-id="6818c-106">W pierwszym przykładzie jest tworzony ścieżki, która zawiera jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="6818c-106">The first example creates a path that has a single figure.</span></span> <span data-ttu-id="6818c-107">Rysunek składa się z jednego łuk. Łuk ma kąt odchylenia –180 stopni, która jest zegara w układzie współrzędnych domyślne.</span><span class="sxs-lookup"><span data-stu-id="6818c-107">The figure consists of a single arc. The arc has a sweep angle of –180 degrees, which is counterclockwise in the default coordinate system.</span></span>  
  
-   <span data-ttu-id="6818c-108">W drugim przykładzie jest tworzony ścieżki, która ma dwa rysunki.</span><span class="sxs-lookup"><span data-stu-id="6818c-108">The second example creates a path that has two figures.</span></span> <span data-ttu-id="6818c-109">Pierwszą jest łuk znak wiersza.</span><span class="sxs-lookup"><span data-stu-id="6818c-109">The first figure is an arc followed by a line.</span></span> <span data-ttu-id="6818c-110">Drugi rysunek to linia następuje krzywej znak wiersza.</span><span class="sxs-lookup"><span data-stu-id="6818c-110">The second figure is a line followed by a curve followed by a line.</span></span> <span data-ttu-id="6818c-111">Pierwszą pozostanie otwarte, a drugi rysunek jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="6818c-111">The first figure is left open, and the second figure is closed.</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6818c-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6818c-112">Compiling the Code</span></span>  
 <span data-ttu-id="6818c-113">Poprzednich przykładach są przeznaczone do użytku z formularzy systemu Windows, a potrzebują <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6818c-113">The previous examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6818c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6818c-114">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="6818c-115">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="6818c-115">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 [<span data-ttu-id="6818c-116">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="6818c-116">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
