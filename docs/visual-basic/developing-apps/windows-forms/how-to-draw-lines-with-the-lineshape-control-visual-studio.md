---
title: 'Porady: rysowanie linii za pomocą formantów LineShape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
ms.openlocfilehash: 5e1a837578aab4b4609a58ffee46406b022b8f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587348"
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="57d48-102">Porady: rysowanie linii za pomocą formantów LineShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="57d48-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="57d48-103">Można użyć <xref:Microsoft.VisualBasic.PowerPacks.LineShape> formantu do rysowania poziomych, pionowy lub ukośnych linii w formularzu lub kontenera, zarówno w czasie projektowania, jak i w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="57d48-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="57d48-104">**Uwaga** komputera mogą być wyświetlane inne nazwy i lokalizacje niektórych użytkownika programu Visual Studio interfejsu elementów w poniższych instrukcjach.</span><span class="sxs-lookup"><span data-stu-id="57d48-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="57d48-105">Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="57d48-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="57d48-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="57d48-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="57d48-107">Rysowanie linii w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="57d48-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="57d48-108">Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.LineShape> kontrolować z **Visual Basic PowerPacks** karcie **przybornika** przeciągnij formularza lub kontenera formantu.</span><span class="sxs-lookup"><span data-stu-id="57d48-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="57d48-109">Przeciągnij zmiany rozmiaru i Przenieś dojścia do rozmiaru i pozycji wiersza.</span><span class="sxs-lookup"><span data-stu-id="57d48-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="57d48-110">Możesz również rozmiar i położenie wiersza, zmieniając `X1`, `X2`, `Y1`, i `Y2` właściwości w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="57d48-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="57d48-111">W **właściwości** okna, takich jak opcjonalnie skonfigurować dodatkowe właściwości `BorderStyle` lub `BorderColor` Aby zmienić wygląd linii.</span><span class="sxs-lookup"><span data-stu-id="57d48-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="57d48-112">Rysowanie linii w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="57d48-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="57d48-113">Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="57d48-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="57d48-114">W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Microsoft.VisualBasic.PowerPacks.VS**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="57d48-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="57d48-115">W **edytora kodu**, Dodaj `Imports` lub `using` instrukcji w górnej części modułu:</span><span class="sxs-lookup"><span data-stu-id="57d48-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="57d48-116">Dodaj następujący kod w `Event` procedury:</span><span class="sxs-lookup"><span data-stu-id="57d48-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="57d48-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57d48-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [<span data-ttu-id="57d48-118">Linie i kształty — Wprowadzenie do kontrolek</span><span class="sxs-lookup"><span data-stu-id="57d48-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="57d48-119">Instrukcje: rysowanie kształtów za pomocą kontrolek OvalShape i RectangleShape</span><span class="sxs-lookup"><span data-stu-id="57d48-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
