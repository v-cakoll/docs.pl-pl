---
title: 'Instrukcje: Wyświetlanie formantów niepowiązanych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: a20e1ba83d1963bc3d4c135817767ee02fcbdeda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730792"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="ef569-102">Instrukcje: Wyświetlanie formantów niepowiązanych w formancie DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ef569-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="ef569-103">Oprócz formanty powiązania, warto dodać inne formanty do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, na przykład etykieta statyczna lub obraz jest powtarzany w każdym elemencie w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ef569-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef569-104">Musisz również posiadać co najmniej jedną kontrolkę powiązanej <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> lub nic nie będą wyświetlane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ef569-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="ef569-105">Aby dodać niepowiązanej kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ef569-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="ef569-106">Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> z kontrolować **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.</span><span class="sxs-lookup"><span data-stu-id="ef569-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="ef569-107">Przeciągając uchwyty zmiany rozmiaru i położenia rozmiar i położenie formantu.</span><span class="sxs-lookup"><span data-stu-id="ef569-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="ef569-108">Można także rozmiar i położenie formantu, zmieniając **rozmiar** i **pozycji** właściwości w oknie dialogowym właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef569-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="ef569-109">Dodaj co najmniej jeden formant powiązany z danymi do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ef569-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="ef569-110">Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie powiązanych danych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="ef569-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="ef569-111">Przeciągnij formant z **przybornika** na region szablonu elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.</span><span class="sxs-lookup"><span data-stu-id="ef569-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="ef569-112">Należy pamiętać, że kontrolka ma dwa regiony prostokątny.</span><span class="sxs-lookup"><span data-stu-id="ef569-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="ef569-113">Wewnętrzny region jest *szablon elementu*; formantów dodanych do szablonu zostanie powtórzona w każdym elemencie w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ef569-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="ef569-114">Zewnętrzne region jest *okienka ekranu*, której elementy będą wyświetlane; formanty, które są dodawane do tego regionu nie będą wyświetlane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ef569-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef569-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef569-115">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="ef569-116">Wprowadzenie do kontrolki DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ef569-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="ef569-117">Rozwiązywanie problemów z kontrolką DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ef569-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="ef569-118">Instrukcje: Wyświetlanie powiązanych danych w formancie DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ef569-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="ef569-119">Instrukcje: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ef569-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [<span data-ttu-id="ef569-120">Instrukcje: Zmienianie wyglądu formantu DataRepeater</span><span class="sxs-lookup"><span data-stu-id="ef569-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
