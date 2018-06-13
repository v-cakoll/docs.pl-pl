---
title: 'Porady: wypełnianie otwartych figur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: b7422ae2a4dc4d59fd337ab2294caa0d65057bae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521163"
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="35432-102">Porady: wypełnianie otwartych figur</span><span class="sxs-lookup"><span data-stu-id="35432-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="35432-103">Możesz wpisać ścieżkę przez przekazanie <xref:System.Drawing.Drawing2D.GraphicsPath> do obiektu <xref:System.Drawing.Graphics.FillPath%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="35432-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="35432-104"><xref:System.Drawing.Graphics.FillPath%2A> Metody wypełnia ścieżki zgodnie z trybu wypełnienia (alternatywnego lub zawijania) aktualnie ustawione dla ścieżki.</span><span class="sxs-lookup"><span data-stu-id="35432-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="35432-105">Jeśli ścieżka zawiera wszystkie otwartych figur, ścieżka zostanie wypełniony tak, jakby te dane zostały zamknięte.</span><span class="sxs-lookup"><span data-stu-id="35432-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="35432-106"> Zamyka rysunku za pomocą rysowania linii prostej od punktu końcowego do punktu początkowego.</span><span class="sxs-lookup"><span data-stu-id="35432-106"> closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35432-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="35432-107">Example</span></span>  
 <span data-ttu-id="35432-108">Poniższy przykład tworzy ścieżki, która ma jedną figurę otwartą (łuk) i jeden figurę zamkniętą (elipsy).</span><span class="sxs-lookup"><span data-stu-id="35432-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="35432-109"><xref:System.Drawing.Graphics.FillPath%2A> Metody wypełnia ścieżki zgodnie z wypełnienia domyślny tryb, który jest <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="35432-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="35432-110">Na poniższej ilustracji przedstawiono dane wyjściowe przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="35432-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="35432-111">Należy pamiętać, że ścieżka jest wypełniony (zgodnie ze standardem <xref:System.Drawing.Drawing2D.FillMode.Alternate>) tak, jakby figurę otwartą zostały zamknięte przez prostej od punktu końcowego do punktu początkowego.</span><span class="sxs-lookup"><span data-stu-id="35432-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 <span data-ttu-id="35432-112">![Ścieżka otwartego wypełnienia](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span><span class="sxs-lookup"><span data-stu-id="35432-112">![Fill Open Path](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35432-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="35432-113">Compiling the Code</span></span>  
 <span data-ttu-id="35432-114">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="35432-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35432-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35432-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="35432-116">Ścieżki grafiki w GDI+</span><span class="sxs-lookup"><span data-stu-id="35432-116">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
