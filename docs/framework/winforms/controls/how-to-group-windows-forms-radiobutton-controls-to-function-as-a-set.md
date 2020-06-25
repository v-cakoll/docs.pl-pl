---
title: Grupowanie kontrolek RadioButton do działania jako zestaw
description: Dowiedz się, jak grupować Windows Forms formantów RadioButton, aby funkcjonowały niezależnie od innych zestawów.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325922"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="2b88c-103">Porady: grupowanie formantów RadioButton formularzy systemu Windows, aby działały jak zestaw</span><span class="sxs-lookup"><span data-stu-id="2b88c-103">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="2b88c-104"><xref:System.Windows.Forms.RadioButton>Kontrolki Windows Forms zaprojektowano w celu zapewnienia użytkownikom wyboru spośród dwóch lub więcej ustawień, do których można przypisać tylko jeden element do procedury lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="2b88c-104">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="2b88c-105">Na przykład grupa <xref:System.Windows.Forms.RadioButton> kontrolek może wyświetlić wybór przewoźników pakietów dla zamówienia, ale tylko jeden z nich będzie używany.</span><span class="sxs-lookup"><span data-stu-id="2b88c-105">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="2b88c-106">W związku z tym można wybrać tylko jedną z nich <xref:System.Windows.Forms.RadioButton> naraz, nawet jeśli jest to część grupy funkcjonalnej.</span><span class="sxs-lookup"><span data-stu-id="2b88c-106">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="2b88c-107">Możesz grupować przyciski radiowe, rysując je wewnątrz kontenera, takiego jak <xref:System.Windows.Forms.Panel> kontrolka, <xref:System.Windows.Forms.GroupBox> kontrolka lub formularz.</span><span class="sxs-lookup"><span data-stu-id="2b88c-107">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="2b88c-108">Wszystkie przyciski radiowe dodawane bezpośrednio do formularza stają się jedną grupą.</span><span class="sxs-lookup"><span data-stu-id="2b88c-108">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="2b88c-109">Aby dodać oddzielne grupy, należy umieścić je wewnątrz paneli lub grup pól.</span><span class="sxs-lookup"><span data-stu-id="2b88c-109">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="2b88c-110">Aby uzyskać więcej informacji na temat paneli lub grup, zobacz [Omówienie kontrolki panel](panel-control-overview-windows-forms.md) lub [kontrolka widoku grupy](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2b88c-110">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="2b88c-111">Aby zgrupować kontrolki RadioButton jako zestaw do działania niezależnie od innych zestawów</span><span class="sxs-lookup"><span data-stu-id="2b88c-111">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="2b88c-112">Przeciągnij <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> kontrolkę lub z karty **Windows Forms** w **przyborniku** na formularz.</span><span class="sxs-lookup"><span data-stu-id="2b88c-112">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="2b88c-113">Rysuj <xref:System.Windows.Forms.RadioButton> kontrolki w <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> kontrolce lub.</span><span class="sxs-lookup"><span data-stu-id="2b88c-113">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b88c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b88c-114">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="2b88c-115">RadioButton, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2b88c-115">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="2b88c-116">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2b88c-116">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="2b88c-117">GroupBox — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="2b88c-117">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="2b88c-118">CheckBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2b88c-118">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="2b88c-119">RadioButton, kontrolka</span><span class="sxs-lookup"><span data-stu-id="2b88c-119">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
