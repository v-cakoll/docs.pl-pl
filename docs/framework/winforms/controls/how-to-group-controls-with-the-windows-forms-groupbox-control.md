---
title: 'Instrukcje: Grupowanie formantów za pomocą formantu GroupBox formularzy Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 14c832251a76eaff21611c88179c4d2ffa7ab738
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708558"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="e17c7-102">Instrukcje: Grupowanie formantów za pomocą formantu GroupBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="e17c7-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="e17c7-103">Windows Forms <xref:System.Windows.Forms.GroupBox> formantów służą do grupowania innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="e17c7-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="e17c7-104">Istnieją trzy powody do formantów grupy:</span><span class="sxs-lookup"><span data-stu-id="e17c7-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="e17c7-105">Aby utworzyć wizualne grupowanie elementów powiązanych formularza dla interfejsu użytkownika wyraźne.</span><span class="sxs-lookup"><span data-stu-id="e17c7-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="e17c7-106">Aby utworzyć programowe grupowanie (of przyciski radiowe, na przykład).</span><span class="sxs-lookup"><span data-stu-id="e17c7-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="e17c7-107">Przenoszenia kontrolek jako jednostka, w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="e17c7-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="e17c7-108">Aby utworzyć grupę kontrolek</span><span class="sxs-lookup"><span data-stu-id="e17c7-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="e17c7-109">Rysowanie <xref:System.Windows.Forms.GroupBox> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e17c7-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="e17c7-110">Dodaj inne formanty do pola grupy rysowania każdego wewnątrz pola grupy.</span><span class="sxs-lookup"><span data-stu-id="e17c7-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="e17c7-111">W przypadku istniejących formantów, które należy wpisać w polu grupy można zaznaczyć wszystkie kontrolki, Wytnij je do Schowka, zaznacz <xref:System.Windows.Forms.GroupBox> sterowania, a następnie wklej je w polu grupy.</span><span class="sxs-lookup"><span data-stu-id="e17c7-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="e17c7-112">Ponadto można przeciągnąć w polu grupy.</span><span class="sxs-lookup"><span data-stu-id="e17c7-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="e17c7-113">Ustaw <xref:System.Windows.Forms.GroupBox.Text%2A> właściwości, pola grupy odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="e17c7-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e17c7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e17c7-114">See also</span></span>
- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="e17c7-115">GroupBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e17c7-115">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
