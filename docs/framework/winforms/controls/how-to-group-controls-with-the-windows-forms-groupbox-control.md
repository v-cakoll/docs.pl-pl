---
title: "Porady: grupowanie formantów za pomocą formantu GroupBox formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ecdb7b8682b13f93f59d1de21552abfa91b8f50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="14526-102">Porady: grupowanie formantów za pomocą formantu GroupBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="14526-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="14526-103">Formularze systemu Windows <xref:System.Windows.Forms.GroupBox> formanty są używane do grupowania inne formanty.</span><span class="sxs-lookup"><span data-stu-id="14526-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="14526-104">Istnieją trzy powodów Grupowanie formantów:</span><span class="sxs-lookup"><span data-stu-id="14526-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="14526-105">Aby utworzyć visual grupowanie elementów pokrewnych formularza dla interfejsu zwykłego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14526-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="14526-106">Aby utworzyć programowe grupowania (of przycisków radiowych, na przykład).</span><span class="sxs-lookup"><span data-stu-id="14526-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="14526-107">Przenoszenie kontrolek jako jednostki w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="14526-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="14526-108">Aby utworzyć grupę formantów</span><span class="sxs-lookup"><span data-stu-id="14526-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="14526-109">Rysuj <xref:System.Windows.Forms.GroupBox> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="14526-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="14526-110">W polu Grupa rysowania każdego wewnątrz pola grupy, należy dodać inne formanty.</span><span class="sxs-lookup"><span data-stu-id="14526-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="14526-111">Jeśli masz istniejących formantów, które chcesz umieścić w polu grupy można wybierz wszystkie formanty, Wytnij je do Schowka, zaznacz <xref:System.Windows.Forms.GroupBox> kontroli, a następnie wklej je w pole grupy.</span><span class="sxs-lookup"><span data-stu-id="14526-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="14526-112">Można również przeciągnij je do pole grupy.</span><span class="sxs-lookup"><span data-stu-id="14526-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="14526-113">Ustaw <xref:System.Windows.Forms.GroupBox.Text%2A> właściwości pola grupy do odpowiednich podpis.</span><span class="sxs-lookup"><span data-stu-id="14526-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14526-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14526-114">See Also</span></span>  
 <xref:System.Windows.Forms.GroupBox>  
 [<span data-ttu-id="14526-115">GroupBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="14526-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
