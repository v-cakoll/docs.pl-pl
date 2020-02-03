---
title: Grupowanie kontrolek z kontrolką grupy
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: bb7476c410d2802b5d32cc9842a778f290765e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736650"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="4976a-102">Porady: grupowanie formantów za pomocą formantu GroupBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4976a-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="4976a-103">Kontrolki <xref:System.Windows.Forms.GroupBox> Windows Forms są używane do grupowania innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="4976a-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="4976a-104">Istnieją trzy powody, dla których należy grupować kontrolki:</span><span class="sxs-lookup"><span data-stu-id="4976a-104">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="4976a-105">Aby utworzyć wizualne grupowanie elementów formularza pokrewnych dla czystego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4976a-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="4976a-106">Aby utworzyć grupowanie programistyczne (na przykład przyciski radiowe).</span><span class="sxs-lookup"><span data-stu-id="4976a-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="4976a-107">Do przesuwania formantów jako jednostki w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="4976a-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="4976a-108">Aby utworzyć grupę kontrolek</span><span class="sxs-lookup"><span data-stu-id="4976a-108">To create a group of controls</span></span>  
  
1. <span data-ttu-id="4976a-109">Narysuj kontrolkę <xref:System.Windows.Forms.GroupBox> w formularzu.</span><span class="sxs-lookup"><span data-stu-id="4976a-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="4976a-110">Dodaj inne kontrolki do pola Grupa, rysując każdy wewnątrz pola grupy.</span><span class="sxs-lookup"><span data-stu-id="4976a-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="4976a-111">Jeśli masz istniejące kontrolki, które chcesz umieścić w polu grupy, możesz zaznaczyć wszystkie kontrolki, wyciąć je do schowka, wybrać kontrolkę <xref:System.Windows.Forms.GroupBox>, a następnie wkleić ją do pola Grupa.</span><span class="sxs-lookup"><span data-stu-id="4976a-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="4976a-112">Możesz również przeciągnąć je do pola Grupa.</span><span class="sxs-lookup"><span data-stu-id="4976a-112">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="4976a-113">Ustaw właściwość <xref:System.Windows.Forms.GroupBox.Text%2A> pola grupy na odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="4976a-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4976a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4976a-114">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="4976a-115">GroupBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="4976a-115">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
