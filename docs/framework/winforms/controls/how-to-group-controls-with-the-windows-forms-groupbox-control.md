---
title: 'Instrukcje: Grupowanie formantów za pomocą formantu GroupBox formularzy Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 44f0116511165c021f8e3dc35fb14e5cfb6f619e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686923"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="edeea-102">Instrukcje: Grupowanie formantów za pomocą formantu GroupBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="edeea-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="edeea-103">Windows Forms <xref:System.Windows.Forms.GroupBox> formantów służą do grupowania innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="edeea-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="edeea-104">Istnieją trzy powody do formantów grupy:</span><span class="sxs-lookup"><span data-stu-id="edeea-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="edeea-105">Aby utworzyć wizualne grupowanie elementów powiązanych formularza dla interfejsu użytkownika wyraźne.</span><span class="sxs-lookup"><span data-stu-id="edeea-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="edeea-106">Aby utworzyć programowe grupowanie (of przyciski radiowe, na przykład).</span><span class="sxs-lookup"><span data-stu-id="edeea-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="edeea-107">Przenoszenia kontrolek jako jednostka, w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="edeea-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="edeea-108">Aby utworzyć grupę kontrolek</span><span class="sxs-lookup"><span data-stu-id="edeea-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="edeea-109">Rysowanie <xref:System.Windows.Forms.GroupBox> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="edeea-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="edeea-110">Dodaj inne formanty do pola grupy rysowania każdego wewnątrz pola grupy.</span><span class="sxs-lookup"><span data-stu-id="edeea-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="edeea-111">W przypadku istniejących formantów, które należy wpisać w polu grupy można zaznaczyć wszystkie kontrolki, Wytnij je do Schowka, zaznacz <xref:System.Windows.Forms.GroupBox> sterowania, a następnie wklej je w polu grupy.</span><span class="sxs-lookup"><span data-stu-id="edeea-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="edeea-112">Ponadto można przeciągnąć w polu grupy.</span><span class="sxs-lookup"><span data-stu-id="edeea-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="edeea-113">Ustaw <xref:System.Windows.Forms.GroupBox.Text%2A> właściwości, pola grupy odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="edeea-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edeea-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edeea-114">See also</span></span>
- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="edeea-115">GroupBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="edeea-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
