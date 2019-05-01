---
title: 'Instrukcje: grupowanie kontrolek z kontrolką panelu formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 662343af42f72816a5a673d2cd6d839a5dca9190
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971304"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="a8c40-102">Instrukcje: grupowanie kontrolek z kontrolką panelu formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a8c40-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="a8c40-103">Windows Forms <xref:System.Windows.Forms.Panel> formantów służą do grupowania innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="a8c40-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="a8c40-104">Istnieją trzy powody do grupy kontrolek.</span><span class="sxs-lookup"><span data-stu-id="a8c40-104">There are three reasons to group controls.</span></span> <span data-ttu-id="a8c40-105">Jeden jest wizualne grupowanie elementów powiązanych formularza dla interfejsu użytkownika wyraźne; innym jest programowe grupowanie przycisków radiowych np. ostatni jest przenoszenie kontrolek jako jednostki w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="a8c40-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8c40-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="a8c40-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a8c40-107">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="a8c40-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a8c40-108">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="a8c40-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="a8c40-109">Aby utworzyć grupę kontrolek</span><span class="sxs-lookup"><span data-stu-id="a8c40-109">To create a group of controls</span></span>  
  
1. <span data-ttu-id="a8c40-110">Przeciągnij <xref:System.Windows.Forms.Panel> z kontrolować **Windows Forms** kartę przybornika do formularza.</span><span class="sxs-lookup"><span data-stu-id="a8c40-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2. <span data-ttu-id="a8c40-111">Dodaj inne formanty do panelu, rysowania każdego wewnątrz panelu.</span><span class="sxs-lookup"><span data-stu-id="a8c40-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="a8c40-112">W przypadku istniejących formantów, które chcesz umieścić w panelu można zaznaczyć wszystkie kontrolki, Wytnij je do Schowka, zaznacz <xref:System.Windows.Forms.Panel> sterowania, a następnie wklej je do panelu.</span><span class="sxs-lookup"><span data-stu-id="a8c40-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="a8c40-113">Można również przeciągnąć je do panelu.</span><span class="sxs-lookup"><span data-stu-id="a8c40-113">You can also drag them into the panel.</span></span>  
  
3. <span data-ttu-id="a8c40-114">(Opcjonalnie) Jeśli chcesz dodać obramowanie do panelu, ustaw jego <xref:System.Windows.Forms.BorderStyle> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8c40-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="a8c40-115">Istnieją trzy opcje: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, i <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="a8c40-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c40-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8c40-116">See also</span></span>

- [<span data-ttu-id="a8c40-117">Panel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a8c40-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="a8c40-118">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a8c40-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="a8c40-119">Instrukcje: Ustawianie tła panelu</span><span class="sxs-lookup"><span data-stu-id="a8c40-119">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
