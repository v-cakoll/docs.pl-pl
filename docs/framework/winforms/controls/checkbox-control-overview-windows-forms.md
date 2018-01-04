---
title: "CheckBox — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39645a02cd66d37d61df72028ab129677edb757e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="checkbox-control-overview-windows-forms"></a><span data-ttu-id="e76b9-102">CheckBox — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="e76b9-102">CheckBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="e76b9-103">Formularze systemu Windows <xref:System.Windows.Forms.CheckBox> formant wskazuje, czy określony warunek jest on lub off.</span><span class="sxs-lookup"><span data-stu-id="e76b9-103">The Windows Forms <xref:System.Windows.Forms.CheckBox> control indicates whether a particular condition is on or off.</span></span> <span data-ttu-id="e76b9-104">Zwykle jest używana do prezentowania tak/nie lub PRAWDA/FAŁSZ wybór dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e76b9-104">It is commonly used to present a Yes/No or True/False selection to the user.</span></span> <span data-ttu-id="e76b9-105">Formanty pól wyboru w grupach służy do wyświetlania wiele wyborów, z których użytkownik może wybrać co najmniej jeden.</span><span class="sxs-lookup"><span data-stu-id="e76b9-105">You can use check box controls in groups to display multiple choices from which the user can select one or more.</span></span>  
  
 <span data-ttu-id="e76b9-106">Kontrolka pola wyboru jest podobny do kontrolkę przycisku radiowego, w tym każdego służy do wskazywania wyboru, które zostało utworzone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e76b9-106">The check box control is similar to the radio button control in that each is used to indicate a selection that is made by the user.</span></span> <span data-ttu-id="e76b9-107">Są one różne, w których można wybrać przycisk radiowy tylko jednej grupy naraz.</span><span class="sxs-lookup"><span data-stu-id="e76b9-107">They differ in that only one radio button in a group can be selected at a time.</span></span> <span data-ttu-id="e76b9-108">Za pomocą formantu pole wyboru jednak dowolną liczbę pól wyboru można zaznaczyć.</span><span class="sxs-lookup"><span data-stu-id="e76b9-108">With the check box control, however, any number of check boxes may be selected.</span></span>  
  
 <span data-ttu-id="e76b9-109">Pole wyboru może być połączone elementy w bazie danych przy użyciu proste powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="e76b9-109">A check box may be connected to elements in a database using simple data binding.</span></span> <span data-ttu-id="e76b9-110">Wiele pól wyboru mogą być zgrupowane za pomocą <xref:System.Windows.Forms.GroupBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="e76b9-110">Multiple check boxes may be grouped using the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="e76b9-111">Jest to przydatne do wyglądu i również projektu interfejsu użytkownika, ponieważ grupowanych formanty mogą być przenoszone między razem na projektanta formularza.</span><span class="sxs-lookup"><span data-stu-id="e76b9-111">This is useful for visual appearance and also for user interface design, since grouped controls can be moved around together on the form designer.</span></span> <span data-ttu-id="e76b9-112">Aby uzyskać więcej informacji, zobacz [wiązanie danych formularzy systemu Windows](../../../../docs/framework/winforms/windows-forms-data-binding.md) i [GroupBox — formant](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e76b9-112">For more information, see [Windows Forms Data Binding](../../../../docs/framework/winforms/windows-forms-data-binding.md) and [GroupBox Control](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="e76b9-113"><xref:System.Windows.Forms.CheckBox> Formant ma dwie ważne właściwości <xref:System.Windows.Forms.CheckBox.Checked%2A> i <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span><span class="sxs-lookup"><span data-stu-id="e76b9-113">The <xref:System.Windows.Forms.CheckBox> control has two important properties, <xref:System.Windows.Forms.CheckBox.Checked%2A> and <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span></span> <span data-ttu-id="e76b9-114"><xref:System.Windows.Forms.CheckBox.Checked%2A> Właściwość zwraca albo `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="e76b9-114">The <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns either `true` or `false`.</span></span> <span data-ttu-id="e76b9-115"><xref:System.Windows.Forms.CheckBox.CheckState%2A> Właściwość zwraca albo <xref:System.Windows.Forms.CheckState.Checked> lub <xref:System.Windows.Forms.CheckState.Unchecked>; lub, jeśli <xref:System.Windows.Forms.CheckBox.ThreeState%2A> właściwość jest ustawiona na `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> może też zwracać <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="e76b9-115">The <xref:System.Windows.Forms.CheckBox.CheckState%2A> property returns either <xref:System.Windows.Forms.CheckState.Checked> or <xref:System.Windows.Forms.CheckState.Unchecked>; or, if the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> may also return <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span> <span data-ttu-id="e76b9-116">W stanie nieokreślonym pole zostanie wyświetlony z wygaszone wyglądu, aby wskazać, że ta opcja jest niedostępna.</span><span class="sxs-lookup"><span data-stu-id="e76b9-116">In the indeterminate state, the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e76b9-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e76b9-117">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="e76b9-118">Instrukcje: ustawianie opcji za pomocą kontrolek CheckBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e76b9-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="e76b9-119">Instrukcje: odpowiadanie na kliknięcia kontrolki CheckBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e76b9-119">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="e76b9-120">CheckBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e76b9-120">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
