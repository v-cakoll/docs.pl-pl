---
title: 'Instrukcje: Włączanie przełączania między kształtami (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
ms.openlocfilehash: c47d94317008af57907b747e53bd13ae7ca229f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498284"
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="f395a-102">Instrukcje: Włączanie przełączania między kształtami (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="f395a-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="f395a-103">Formanty linii i kształtu nie mają `TabStop` lub `TabIndex` właściwości, ale można nadal Włączanie przełączania między nimi.</span><span class="sxs-lookup"><span data-stu-id="f395a-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="f395a-104">W poniższym przykładzie naciskając klawisz CTRL i klucze karty będzie kartę między kształtów. Naciśnięcie klawisza TAB będzie karcie między przyciskami.</span><span class="sxs-lookup"><span data-stu-id="f395a-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f395a-105">Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f395a-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="f395a-106">Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="f395a-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="f395a-107">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f395a-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="f395a-108">Aby włączyć przełączania między kształtami</span><span class="sxs-lookup"><span data-stu-id="f395a-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="f395a-109">Przeciągnij trzy <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kontrolek i dwóch <xref:System.Windows.Forms.Button> kontrolki z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="f395a-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="f395a-110">W **Edytor kodu**, Dodaj `Imports` lub `using` instrukcji w górnej części modułu:</span><span class="sxs-lookup"><span data-stu-id="f395a-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="f395a-111">Dodaj następujący kod w procedurze zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f395a-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="f395a-112">Dodaj następujący kod w `Button1_PreviewKeyDown` procedury zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="f395a-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f395a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f395a-113">See also</span></span>
- [<span data-ttu-id="f395a-114">Instrukcje: Rysowanie kształtów za pomocą formantów OvalShape i Rectangleshape</span><span class="sxs-lookup"><span data-stu-id="f395a-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
- [<span data-ttu-id="f395a-115">Instrukcje: Rysowanie linii za pomocą formantu LineShape</span><span class="sxs-lookup"><span data-stu-id="f395a-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
- [<span data-ttu-id="f395a-116">Linie i kształty — Wprowadzenie do kontrolek</span><span class="sxs-lookup"><span data-stu-id="f395a-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
