---
title: 'Instrukcje: Grupa formantów RadioButton formularzy Windows aby działały jak zestaw'
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 2758ff2380431668b2c908dbddd5dbe2094ccd0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569339"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="63e70-102">Instrukcje: Grupa formantów RadioButton formularzy Windows aby działały jak zestaw</span><span class="sxs-lookup"><span data-stu-id="63e70-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="63e70-103">Windows Forms <xref:System.Windows.Forms.RadioButton> formanty są przeznaczone do zapewniają użytkownikom wybór spośród dwóch lub więcej ustawień, których można przypisać tylko jedną procedury lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="63e70-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="63e70-104">Na przykład grupy <xref:System.Windows.Forms.RadioButton> formanty mogą być wyświetlane wybór przewoźników pakietu dla zamówienia, ale tylko jeden przewoźników będzie używany.</span><span class="sxs-lookup"><span data-stu-id="63e70-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="63e70-105">W związku z tym tylko jeden <xref:System.Windows.Forms.RadioButton> w danym momencie może być zaznaczony, nawet jeśli jest częścią grupy funkcjonalnej.</span><span class="sxs-lookup"><span data-stu-id="63e70-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="63e70-106">Grupowanie przycisków radiowych za pomocą rysowania w kontenerze takich jak <xref:System.Windows.Forms.Panel> kontroli <xref:System.Windows.Forms.GroupBox> , formularz lub formant.</span><span class="sxs-lookup"><span data-stu-id="63e70-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="63e70-107">Wszystkie przyciski radiowe, które są dodawane bezpośrednio do formularza stają się z jednej grupy.</span><span class="sxs-lookup"><span data-stu-id="63e70-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="63e70-108">Aby dodać osobnych grup, trzeba je umieścić wewnątrz paneli lub pola grupy.</span><span class="sxs-lookup"><span data-stu-id="63e70-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="63e70-109">Aby uzyskać więcej informacji na temat paneli lub pola grupy zobacz [Panel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) lub [— informacje o formancie GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="63e70-109">For more information about panels or group boxes, see [Panel Control Overview](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) or [GroupBox Control Overview](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="63e70-110">Do grupy kontrolek RadioButton jako zestaw funkcji, niezależnie od innych zestawów</span><span class="sxs-lookup"><span data-stu-id="63e70-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1.  <span data-ttu-id="63e70-111">Przeciągnij <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel> z kontrolować **Windows Forms** karcie **przybornika** na formularz.</span><span class="sxs-lookup"><span data-stu-id="63e70-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="63e70-112">Rysowanie <xref:System.Windows.Forms.RadioButton> formantów na <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="63e70-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e70-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63e70-113">See also</span></span>
- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="63e70-114">RadioButton, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="63e70-114">RadioButton Control Overview</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="63e70-115">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="63e70-115">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [<span data-ttu-id="63e70-116">GroupBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="63e70-116">GroupBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="63e70-117">CheckBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="63e70-117">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="63e70-118">RadioButton, kontrolka</span><span class="sxs-lookup"><span data-stu-id="63e70-118">RadioButton Control</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
