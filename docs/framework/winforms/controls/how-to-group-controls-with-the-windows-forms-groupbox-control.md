---
title: 'Instrukcje: grupowanie kontrolek za pomocą kontrolki GroupBox formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: 706655c8cb2c2548b393b6ad731c13e47fd9381a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179635"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="e4775-102">Instrukcje: grupowanie kontrolek za pomocą kontrolki GroupBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e4775-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="e4775-103">Windows Forms <xref:System.Windows.Forms.GroupBox> formantów służą do grupowania innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="e4775-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="e4775-104">Istnieją trzy powody do formantów grupy:</span><span class="sxs-lookup"><span data-stu-id="e4775-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="e4775-105">Aby utworzyć wizualne grupowanie elementów powiązanych formularza dla interfejsu użytkownika wyraźne.</span><span class="sxs-lookup"><span data-stu-id="e4775-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="e4775-106">Aby utworzyć programowe grupowanie (of przyciski radiowe, na przykład).</span><span class="sxs-lookup"><span data-stu-id="e4775-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="e4775-107">Przenoszenia kontrolek jako jednostka, w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="e4775-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="e4775-108">Aby utworzyć grupę kontrolek</span><span class="sxs-lookup"><span data-stu-id="e4775-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="e4775-109">Rysowanie <xref:System.Windows.Forms.GroupBox> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e4775-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="e4775-110">Dodaj inne formanty do pola grupy rysowania każdego wewnątrz pola grupy.</span><span class="sxs-lookup"><span data-stu-id="e4775-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="e4775-111">W przypadku istniejących formantów, które należy wpisać w polu grupy można zaznaczyć wszystkie kontrolki, Wytnij je do Schowka, zaznacz <xref:System.Windows.Forms.GroupBox> sterowania, a następnie wklej je w polu grupy.</span><span class="sxs-lookup"><span data-stu-id="e4775-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="e4775-112">Ponadto można przeciągnąć w polu grupy.</span><span class="sxs-lookup"><span data-stu-id="e4775-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="e4775-113">Ustaw <xref:System.Windows.Forms.GroupBox.Text%2A> właściwości, pola grupy odpowiedni podpis.</span><span class="sxs-lookup"><span data-stu-id="e4775-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4775-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4775-114">See also</span></span>

- <xref:System.Windows.Forms.GroupBox>
- [<span data-ttu-id="e4775-115">GroupBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e4775-115">GroupBox Control</span></span>](groupbox-control-windows-forms.md)
