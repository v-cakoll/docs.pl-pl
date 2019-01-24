---
title: 'Instrukcje: Rysowanie linii za pomocą formantów LineShape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
ms.openlocfilehash: 46360c01dfaf2c6fe199725a9ecfba2248c72d6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596231"
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="cb8a8-102">Instrukcje: Rysowanie linii za pomocą formantów LineShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="cb8a8-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="cb8a8-103">Możesz użyć <xref:Microsoft.VisualBasic.PowerPacks.LineShape> formantu do rysowania linii poziomej, pionowej lub na skos na formularzu lub kontenera, zarówno w czasie projektowania, jak i w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cb8a8-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="cb8a8-104">**Uwaga** komputer może wyświetlać różne nazwy lub lokalizacje dla niektórych użytkowników programu Visual Studio elementy interfejsu w poniższych instrukcjach.</span><span class="sxs-lookup"><span data-stu-id="cb8a8-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="cb8a8-105">Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="cb8a8-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="cb8a8-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="cb8a8-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="cb8a8-107">Aby narysować linię w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="cb8a8-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="cb8a8-108">Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.LineShape> z kontrolować **Visual Basic PowerPacks** karcie **przybornika** przeciągnij do kontrolki formularza lub kontenera.</span><span class="sxs-lookup"><span data-stu-id="cb8a8-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="cb8a8-109">Przeciągnij zmiany rozmiaru i przenoszenie dojścia do rozmiaru i pozycji wiersza.</span><span class="sxs-lookup"><span data-stu-id="cb8a8-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="cb8a8-110">Można także rozmiar i położenie wiersza, zmieniając `X1`, `X2`, `Y1`, i `Y2` właściwości w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="cb8a8-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="cb8a8-111">W **właściwości** okna, takie jak opcjonalnie ustawić dodatkowe właściwości `BorderStyle` lub `BorderColor` można zmienić wygląd linii.</span><span class="sxs-lookup"><span data-stu-id="cb8a8-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="cb8a8-112">Aby narysować linię w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="cb8a8-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="cb8a8-113">Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="cb8a8-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="cb8a8-114">W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Microsoft.VisualBasic.PowerPacks.VS**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cb8a8-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="cb8a8-115">W **Edytor kodu**, Dodaj `Imports` lub `using` instrukcji w górnej części modułu:</span><span class="sxs-lookup"><span data-stu-id="cb8a8-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="cb8a8-116">Dodaj następujący kod w `Event` procedury:</span><span class="sxs-lookup"><span data-stu-id="cb8a8-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cb8a8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb8a8-117">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.LineShape>
- [<span data-ttu-id="cb8a8-118">Linie i kształty — Wprowadzenie do kontrolek</span><span class="sxs-lookup"><span data-stu-id="cb8a8-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [<span data-ttu-id="cb8a8-119">Instrukcje: Rysowanie kształtów za pomocą formantów OvalShape i Rectangleshape</span><span class="sxs-lookup"><span data-stu-id="cb8a8-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
