---
title: Grupowanie kontrolek RadioButton do działania jako zestaw
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: c4b37c84bf0f93837b91c743c7681d39fd83a659
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732951"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="d5bbf-102">Porady: grupowanie formantów RadioButton formularzy systemu Windows, aby działały jak zestaw</span><span class="sxs-lookup"><span data-stu-id="d5bbf-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="d5bbf-103">Windows Forms <xref:System.Windows.Forms.RadioButton> kontrolek umożliwiają użytkownikom wybór spośród dwóch lub więcej ustawień, do których można przypisać tylko jeden z nich do procedury lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="d5bbf-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="d5bbf-104">Na przykład grupa formantów <xref:System.Windows.Forms.RadioButton> może wyświetlić wybór przewoźników pakietów dla zamówienia, ale tylko jeden z nich będzie używany.</span><span class="sxs-lookup"><span data-stu-id="d5bbf-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="d5bbf-105">W związku z tym można wybrać tylko jedną <xref:System.Windows.Forms.RadioButton> w danym momencie, nawet jeśli jest to część grupy funkcjonalnej.</span><span class="sxs-lookup"><span data-stu-id="d5bbf-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="d5bbf-106">Przyciski radiowe są grupowane przez rysowanie ich wewnątrz kontenera, takiego jak kontrolka <xref:System.Windows.Forms.Panel>, kontrolka <xref:System.Windows.Forms.GroupBox> lub formularz.</span><span class="sxs-lookup"><span data-stu-id="d5bbf-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="d5bbf-107">Wszystkie przyciski radiowe dodawane bezpośrednio do formularza stają się jedną grupą.</span><span class="sxs-lookup"><span data-stu-id="d5bbf-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="d5bbf-108">Aby dodać oddzielne grupy, należy umieścić je wewnątrz paneli lub grup pól.</span><span class="sxs-lookup"><span data-stu-id="d5bbf-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="d5bbf-109">Aby uzyskać więcej informacji na temat paneli lub grup, zobacz [Omówienie kontrolki panel](panel-control-overview-windows-forms.md) lub [kontrolka widoku grupy](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d5bbf-109">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="d5bbf-110">Aby zgrupować kontrolki RadioButton jako zestaw do działania niezależnie od innych zestawów</span><span class="sxs-lookup"><span data-stu-id="d5bbf-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="d5bbf-111">Przeciągnij formant <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel> z karty **Windows Forms** w **przyborniku** na formularz.</span><span class="sxs-lookup"><span data-stu-id="d5bbf-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="d5bbf-112">Rysuj <xref:System.Windows.Forms.RadioButton> kontrolki w kontrolce <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="d5bbf-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5bbf-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5bbf-113">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="d5bbf-114">RadioButton, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d5bbf-114">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="d5bbf-115">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d5bbf-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="d5bbf-116">GroupBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d5bbf-116">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="d5bbf-117">CheckBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d5bbf-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="d5bbf-118">RadioButton, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d5bbf-118">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
