---
title: 'Instrukcje: Wypełnianie otwartych figur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: c7d193fdad554048ecd0f2cca5a83cfccbc2a403
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654084"
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="dbd8f-102">Instrukcje: Wypełnianie otwartych figur</span><span class="sxs-lookup"><span data-stu-id="dbd8f-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="dbd8f-103">Możesz wpisać ścieżkę, przekazując <xref:System.Drawing.Drawing2D.GraphicsPath> obiekt <xref:System.Drawing.Graphics.FillPath%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dbd8f-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="dbd8f-104"><xref:System.Drawing.Graphics.FillPath%2A> Metoda wypełni ścieżkę zgodnie z trybu wypełnienia (alternatywne lub zawijania) ustawione dla ścieżki.</span><span class="sxs-lookup"><span data-stu-id="dbd8f-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="dbd8f-105">Jeśli ścieżka zawiera żadnych otwartych figur, ścieżka jest wypełniony, tak jakby te wartości zostały zamknięte.</span><span class="sxs-lookup"><span data-stu-id="dbd8f-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="dbd8f-106">Zamyka rysunku za pomocą rysowania prostej od punktu końcowego do punktu początkowego.</span><span class="sxs-lookup"><span data-stu-id="dbd8f-106">closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbd8f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbd8f-107">Example</span></span>  
 <span data-ttu-id="dbd8f-108">Poniższy przykład tworzy ścieżkę, która ma co otwartego rysunku (łuk) i jeden figurę zamkniętą (elipsy).</span><span class="sxs-lookup"><span data-stu-id="dbd8f-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="dbd8f-109"><xref:System.Drawing.Graphics.FillPath%2A> Metoda wypełni ścieżkę zgodnie z domyślny tryb wypełnienia, czyli <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="dbd8f-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="dbd8f-110">Poniższa ilustracja przedstawia dane wyjściowe przykładowego kodu.</span><span class="sxs-lookup"><span data-stu-id="dbd8f-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="dbd8f-111">Należy zauważyć, że ścieżka jest wypełniony (zgodnie z opisem w <xref:System.Drawing.Drawing2D.FillMode.Alternate>) tak, jakby figurę otwartą zostało zamkniętych przez linię prostą rysowaną od jej punkt końcowy do punktu początkowego.</span><span class="sxs-lookup"><span data-stu-id="dbd8f-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 ![Diagram przedstawiający dane wyjściowe metody FillPath](./media/how-to-fill-open-figures/fill-path-alternate-mode.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dbd8f-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="dbd8f-113">Compiling the Code</span></span>  
 <span data-ttu-id="dbd8f-114">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dbd8f-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd8f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbd8f-115">See also</span></span>
- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="dbd8f-116">Ścieżki grafiki w GDI+</span><span class="sxs-lookup"><span data-stu-id="dbd8f-116">Graphics Paths in GDI+</span></span>](graphics-paths-in-gdi.md)
