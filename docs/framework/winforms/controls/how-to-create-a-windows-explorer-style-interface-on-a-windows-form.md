---
title: 'Porady: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96f2ca8189d6840bc68f063ef9b97539c24b0e6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="94efd-102">Porady: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94efd-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="94efd-103">Z powodu jego gotowy znajomości Eksploratora Windows jest typowe wybór interfejsu użytkownika dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94efd-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="94efd-104">Eksplorator Windows jest zasadniczo <xref:System.Windows.Forms.TreeView> kontroli i <xref:System.Windows.Forms.ListView> formantu w oddzielnych paneli.</span><span class="sxs-lookup"><span data-stu-id="94efd-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="94efd-105">Rozdzielacz zostają o zmiennym rozmiarze panelu.</span><span class="sxs-lookup"><span data-stu-id="94efd-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="94efd-106">To rozmieszczenie formantów jest bardzo efektywnym sposobem wyświetlania oraz informacji o przeglądaniu.</span><span class="sxs-lookup"><span data-stu-id="94efd-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="94efd-107">Poniższe kroki przedstawiają sposób rozmieszczanie formantów w oknie Eksploratora przypominającej formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94efd-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="94efd-108">Nie pokazuj sposób dodawania funkcji przeglądania plików aplikacji Eksploratora Windows.</span><span class="sxs-lookup"><span data-stu-id="94efd-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94efd-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="94efd-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="94efd-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="94efd-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="94efd-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="94efd-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="94efd-112">Aby utworzyć formularzu systemu Windows w stylu Eksploratora Windows</span><span class="sxs-lookup"><span data-stu-id="94efd-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1.  <span data-ttu-id="94efd-113">Utwórz nowy projekt aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94efd-113">Create a new Windows Application project.</span></span> <span data-ttu-id="94efd-114">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="94efd-114">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="94efd-115">Z **przybornika**:</span><span class="sxs-lookup"><span data-stu-id="94efd-115">From the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="94efd-116">Przeciągnij <xref:System.Windows.Forms.SplitContainer> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="94efd-116">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2.  <span data-ttu-id="94efd-117">Przeciągnij <xref:System.Windows.Forms.TreeView> sterowania do **SplitterPanel1** (panelu <xref:System.Windows.Forms.SplitContainer> kontroli oznaczone **Panel1**).</span><span class="sxs-lookup"><span data-stu-id="94efd-117">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3.  <span data-ttu-id="94efd-118">Przeciągnij <xref:System.Windows.Forms.ListView> sterowania do **SplitterPanel2** (panelu <xref:System.Windows.Forms.SplitContainer> kontroli oznaczone **Panel2**).</span><span class="sxs-lookup"><span data-stu-id="94efd-118">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3.  <span data-ttu-id="94efd-119">Zaznacz wszystkie trzy naciśnięcie klawisza CTRL i klikając kolejno.</span><span class="sxs-lookup"><span data-stu-id="94efd-119">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="94efd-120">Po wybraniu <xref:System.Windows.Forms.SplitContainer> sterowania, kliknij przycisk pasek podziału, a nie panele.</span><span class="sxs-lookup"><span data-stu-id="94efd-120">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94efd-121">Nie używaj **Zaznacz wszystko** na **Edytuj** menu.</span><span class="sxs-lookup"><span data-stu-id="94efd-121">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="94efd-122">Jeśli tak zrobisz, właściwość potrzebnych w następnym kroku nie będą widoczne w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="94efd-122">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="94efd-123">W **właściwości** ustaw <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="94efd-123">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="94efd-124">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="94efd-124">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="94efd-125">Formularz zawiera interfejs użytkownika dwuczęściową, podobnie jak w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="94efd-125">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94efd-126">Podczas przeciągania rozdzielacza panele resize samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="94efd-126">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94efd-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94efd-127">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="94efd-128">Porady: Tworzenie złożonego interfejsu użytkownika z formularzami systemu Windows</span><span class="sxs-lookup"><span data-stu-id="94efd-128">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [<span data-ttu-id="94efd-129">Porady: Definiowanie zmieniania rozmiaru i pozycjonowania w podzielonym oknie zachowanie</span><span class="sxs-lookup"><span data-stu-id="94efd-129">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [<span data-ttu-id="94efd-130">Porady: Dzielenie okna w poziomie</span><span class="sxs-lookup"><span data-stu-id="94efd-130">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [<span data-ttu-id="94efd-131">SplitContainer — formant</span><span class="sxs-lookup"><span data-stu-id="94efd-131">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
