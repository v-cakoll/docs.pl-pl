---
title: Grupowanie kontrolek z kontrolką grupy
description: Dowiedz się, jak grupować kontrolki za pomocą kontrolki grupy Windows Forms, aby można było utworzyć wizualną grupę powiązanych elementów.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: f84c495a18f4ae5e04367f024a1e2849f1ed59f9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618067"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="906fe-103">Porady: grupowanie formantów za pomocą formantu GroupBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="906fe-103">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="906fe-104"><xref:System.Windows.Forms.GroupBox>Kontrolki Windows Forms są używane do grupowania innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="906fe-104">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="906fe-105">Istnieją trzy powody, dla których należy grupować kontrolki:</span><span class="sxs-lookup"><span data-stu-id="906fe-105">There are three reasons to group controls:</span></span>  
  
- <span data-ttu-id="906fe-106">Aby utworzyć wizualne grupowanie elementów formularza pokrewnych dla czystego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="906fe-106">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
- <span data-ttu-id="906fe-107">Aby utworzyć grupowanie programistyczne (na przykład przyciski radiowe).</span><span class="sxs-lookup"><span data-stu-id="906fe-107">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
- <span data-ttu-id="906fe-108">Do przesuwania formantów jako jednostki w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="906fe-108">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="906fe-109">Aby utworzyć grupę kontrolek</span><span class="sxs-lookup"><span data-stu-id="906fe-109">To create a group of controls</span></span>  
  
1. <span data-ttu-id="906fe-110">Narysuj <xref:System.Windows.Forms.GroupBox> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="906fe-110">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2. <span data-ttu-id="906fe-111">Dodaj inne kontrolki do pola Grupa, rysując każdy wewnątrz pola grupy.</span><span class="sxs-lookup"><span data-stu-id="906fe-111">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="906fe-112">Jeśli masz istniejące kontrolki, które chcesz umieścić w polu grupy, możesz zaznaczyć wszystkie kontrolki, wyciąć je do schowka, zaznaczyć <xref:System.Windows.Forms.GroupBox> kontrolkę, a następnie wkleić do pola Grupa.</span><span class="sxs-lookup"><span data-stu-id="906fe-112">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="906fe-113">Możesz również przeciągnąć je do pola Grupa.</span><span class="sxs-lookup"><span data-stu-id="906fe-113">You can also drag them into the group box.</span></span>  
  
3. <span data-ttu-id="906fe-114">Ustaw <xref:System.Windows.Forms.GroupBox.Text%2A> Właściwość pola grupy na odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="906fe-114">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906fe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="906fe-115">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="906fe-116">GroupBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="906fe-116">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
