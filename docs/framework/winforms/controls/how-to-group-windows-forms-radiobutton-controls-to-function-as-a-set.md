---
title: "Porady: grupowanie formantów RadioButton formularzy systemu Windows, aby działały jak zestaw"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37d8571624272f62c6ce327b0ed25e082c5cf713
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="49bcd-102">Porady: grupowanie formantów RadioButton formularzy systemu Windows, aby działały jak zestaw</span><span class="sxs-lookup"><span data-stu-id="49bcd-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="49bcd-103">Formularze systemu Windows <xref:System.Windows.Forms.RadioButton> formanty mają na celu zapewniają użytkownikom wybór między co najmniej dwa ustawienia, których można przypisać tylko jeden z nich do procedury lub obiektu.</span><span class="sxs-lookup"><span data-stu-id="49bcd-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="49bcd-104">Na przykład grupa <xref:System.Windows.Forms.RadioButton> formanty mogą być wyświetlane wybór pakietu nośniki zamówienia, ale tylko jeden z nośników będą używane.</span><span class="sxs-lookup"><span data-stu-id="49bcd-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="49bcd-105">W związku z tym tylko jeden <xref:System.Windows.Forms.RadioButton> jednocześnie można wybrać, nawet jeśli jest częścią grupy funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="49bcd-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="49bcd-106">Grupa przycisków radiowych za pomocą rysowania wewnątrz kontenera takich jak <xref:System.Windows.Forms.Panel> kontroli, <xref:System.Windows.Forms.GroupBox> kontroli lub formularz.</span><span class="sxs-lookup"><span data-stu-id="49bcd-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="49bcd-107">Wszystkie przycisków radiowych dodane bezpośrednio do jednej grupy stają się formularza.</span><span class="sxs-lookup"><span data-stu-id="49bcd-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="49bcd-108">Aby dodać oddzielnych grup, trzeba je umieścić wewnątrz paneli lub pola grupy.</span><span class="sxs-lookup"><span data-stu-id="49bcd-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="49bcd-109">Aby uzyskać więcej informacji na temat paneli lub pola grupy, zobacz [Panel — Informacje o formancie](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) lub [informacje o formancie GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="49bcd-109">For more information about panels or group boxes, see [Panel Control Overview](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) or [GroupBox Control Overview](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="49bcd-110">Do grupy kontrolek RadioButton jako zestaw funkcji, niezależnie od innych zestawów</span><span class="sxs-lookup"><span data-stu-id="49bcd-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1.  <span data-ttu-id="49bcd-111">Przeciągnij <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel> kontrolować z **formularzy systemu Windows** karcie na **przybornika** na formularzu.</span><span class="sxs-lookup"><span data-stu-id="49bcd-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="49bcd-112">Rysuj <xref:System.Windows.Forms.RadioButton> formantów na <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel> formantu.</span><span class="sxs-lookup"><span data-stu-id="49bcd-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bcd-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49bcd-113">See Also</span></span>  
 <xref:System.Windows.Forms.RadioButton>  
 [<span data-ttu-id="49bcd-114">Informacje o formancie RadioButton</span><span class="sxs-lookup"><span data-stu-id="49bcd-114">RadioButton Control Overview</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [<span data-ttu-id="49bcd-115">Panel — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="49bcd-115">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="49bcd-116">Informacje o formancie GroupBox</span><span class="sxs-lookup"><span data-stu-id="49bcd-116">GroupBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="49bcd-117">Informacje o formancie CheckBox</span><span class="sxs-lookup"><span data-stu-id="49bcd-117">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="49bcd-118">RadioButton — formant</span><span class="sxs-lookup"><span data-stu-id="49bcd-118">RadioButton Control</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
