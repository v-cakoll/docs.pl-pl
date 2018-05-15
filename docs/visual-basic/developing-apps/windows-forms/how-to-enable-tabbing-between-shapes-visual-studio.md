---
title: 'Porady: włączanie przełączania między kształtami (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
ms.openlocfilehash: 437027e53cb651dd5fabe40b9d8952250f108dad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="399eb-102">Porady: włączanie przełączania między kształtami (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="399eb-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="399eb-103">Formanty linii i kształtu nie mają `TabStop` lub `TabIndex` właściwości, ale można nadal Włączanie przełączania między nimi.</span><span class="sxs-lookup"><span data-stu-id="399eb-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="399eb-104">W poniższym przykładzie naciskając jednocześnie klawisze CTRL i kartę będzie karcie między kształtami; Naciśnięcie klawisza TAB będzie karcie między przyciskami.</span><span class="sxs-lookup"><span data-stu-id="399eb-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="399eb-105">Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="399eb-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="399eb-106">Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="399eb-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="399eb-107">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="399eb-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="399eb-108">Aby włączyć przełączania między kształtami</span><span class="sxs-lookup"><span data-stu-id="399eb-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="399eb-109">Przeciągnij trzy <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> kontrolek i dwa <xref:System.Windows.Forms.Button> formantów **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="399eb-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="399eb-110">W **edytora kodu**, Dodaj `Imports` lub `using` instrukcji w górnej części modułu:</span><span class="sxs-lookup"><span data-stu-id="399eb-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="399eb-111">Dodaj następujący kod w procedurze zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="399eb-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="399eb-112">Dodaj następujący kod w `Button1_PreviewKeyDown` procedury zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="399eb-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="399eb-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="399eb-113">See Also</span></span>  
 [<span data-ttu-id="399eb-114">Instrukcje: rysowanie kształtów za pomocą kontrolek OvalShape i RectangleShape</span><span class="sxs-lookup"><span data-stu-id="399eb-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [<span data-ttu-id="399eb-115">Instrukcje: rysowanie linii za pomocą kontrolki LineShape</span><span class="sxs-lookup"><span data-stu-id="399eb-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [<span data-ttu-id="399eb-116">Linie i kształty — Wprowadzenie do kontrolek</span><span class="sxs-lookup"><span data-stu-id="399eb-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
