---
title: 'Instrukcje: Tworzenie figur z linii, krzywych i kształtów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: eeaf478375e08734b20d83b6f3c8030732495013
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937699"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a><span data-ttu-id="03219-102">Instrukcje: Tworzenie figur z linii, krzywych i kształtów</span><span class="sxs-lookup"><span data-stu-id="03219-102">How to: Create Figures from Lines, Curves, and Shapes</span></span>
<span data-ttu-id="03219-103">Do utworzenia rysunku, należy utworzyć <xref:System.Drawing.Drawing2D.GraphicsPath>, a następnie wywołać metod, takich jak <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, aby dodać w nim elementów podstawowych do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="03219-103">To create a figure, construct a <xref:System.Drawing.Drawing2D.GraphicsPath>, and then call methods, such as <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, to add primitives to the path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03219-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="03219-104">Example</span></span>  
 <span data-ttu-id="03219-105">Poniższe przykłady kodu Utwórz ścieżek, które mają dane:</span><span class="sxs-lookup"><span data-stu-id="03219-105">The following code examples create paths that have figures:</span></span>  
  
- <span data-ttu-id="03219-106">Pierwszy przykład tworzy ścieżką, która ma jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="03219-106">The first example creates a path that has a single figure.</span></span> <span data-ttu-id="03219-107">Rysunek składa się z pojedynczego łuku. Łuk ma kąt odchylenia –180 stopni, czyli do ruchu wskazówek zegara w układzie współrzędnych domyślne.</span><span class="sxs-lookup"><span data-stu-id="03219-107">The figure consists of a single arc. The arc has a sweep angle of –180 degrees, which is counterclockwise in the default coordinate system.</span></span>  
  
- <span data-ttu-id="03219-108">Drugi przykład tworzy ścieżki, która ma dwie cyfry.</span><span class="sxs-lookup"><span data-stu-id="03219-108">The second example creates a path that has two figures.</span></span> <span data-ttu-id="03219-109">Pierwszy rysunek jest łuk znak wiersza.</span><span class="sxs-lookup"><span data-stu-id="03219-109">The first figure is an arc followed by a line.</span></span> <span data-ttu-id="03219-110">Drugi rysunek jest linię następuje krzywej znak wiersza.</span><span class="sxs-lookup"><span data-stu-id="03219-110">The second figure is a line followed by a curve followed by a line.</span></span> <span data-ttu-id="03219-111">Pierwszy rysunek pozostanie otwarty, a drugi rysunek jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="03219-111">The first figure is left open, and the second figure is closed.</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03219-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="03219-112">Compiling the Code</span></span>  
 <span data-ttu-id="03219-113">Poprzednie przykłady są skonstruowane do użycia za pomocą interfejsu Windows Forms i wymagają one <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="03219-113">The previous examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03219-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03219-114">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="03219-115">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="03219-115">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
- [<span data-ttu-id="03219-116">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="03219-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
