---
title: "Porady: grupowanie formantów z formantem panelu formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c1c6dd45d2070c77b34c66388b397bb784215654
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="e7975-102">Porady: grupowanie formantów z formantem panelu formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="e7975-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="e7975-103">Formularze systemu Windows <xref:System.Windows.Forms.Panel> formanty są używane do grupowania inne formanty.</span><span class="sxs-lookup"><span data-stu-id="e7975-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="e7975-104">Istnieją trzy powodów Grupowanie formantów.</span><span class="sxs-lookup"><span data-stu-id="e7975-104">There are three reasons to group controls.</span></span> <span data-ttu-id="e7975-105">Jedna jest visual grupowanie elementów pokrewnych formularza dla interfejsu użytkownika wyczyść; inny jest programowe grupowania, przyciski radiowe na przykład; ostatni jest przenoszenie kontrolek jako jednostki w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="e7975-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7975-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="e7975-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e7975-107">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="e7975-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e7975-108">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e7975-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="e7975-109">Aby utworzyć grupę formantów</span><span class="sxs-lookup"><span data-stu-id="e7975-109">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="e7975-110">Przeciągnij <xref:System.Windows.Forms.Panel> kontrolować z **formularzy systemu Windows** karcie przybornika do formularza.</span><span class="sxs-lookup"><span data-stu-id="e7975-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2.  <span data-ttu-id="e7975-111">Dodać inne formanty do panelu rysowania każdego wewnątrz panelu.</span><span class="sxs-lookup"><span data-stu-id="e7975-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="e7975-112">Jeśli masz istniejących formantów, które chcesz umieścić w panelu można zaznaczyć wszystkie kontrolki, Wytnij je do Schowka, zaznacz <xref:System.Windows.Forms.Panel> kontroli, a następnie wklej je do panelu.</span><span class="sxs-lookup"><span data-stu-id="e7975-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="e7975-113">Można również przeciągnij je do panelu.</span><span class="sxs-lookup"><span data-stu-id="e7975-113">You can also drag them into the panel.</span></span>  
  
3.  <span data-ttu-id="e7975-114">(Opcjonalnie) Jeśli chcesz dodać obramowanie do panelu, ustaw jej <xref:System.Windows.Forms.BorderStyle> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7975-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="e7975-115">Istnieją trzy opcje: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, i <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="e7975-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7975-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7975-116">See Also</span></span>  
 [<span data-ttu-id="e7975-117">Panel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e7975-117">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="e7975-118">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="e7975-118">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="e7975-119">Instrukcje: ustawianie tła panelu</span><span class="sxs-lookup"><span data-stu-id="e7975-119">How to: Set the Background of a Panel</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
