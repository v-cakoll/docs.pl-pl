---
title: 'Instrukcje: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 34a5cd735c350688d9e83003806668e213932c85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960628"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="a7715-102">Instrukcje: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a7715-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="a7715-103">Eksplorator Windows to typowy wybór interfejsu użytkownika dla aplikacji ze względu na jego gotowość.</span><span class="sxs-lookup"><span data-stu-id="a7715-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>

 <span data-ttu-id="a7715-104">Eksplorator Windows jest zasadniczo <xref:System.Windows.Forms.TreeView> formantem <xref:System.Windows.Forms.ListView> i kontrolką w oddzielnych panelach.</span><span class="sxs-lookup"><span data-stu-id="a7715-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="a7715-105">Panele są zmieniane na rozmiar rozdzielacza.</span><span class="sxs-lookup"><span data-stu-id="a7715-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="a7715-106">Takie rozmieszczenie formantów jest bardzo skuteczne do wyświetlania i przeglądania informacji.</span><span class="sxs-lookup"><span data-stu-id="a7715-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>

 <span data-ttu-id="a7715-107">Poniższe kroki pokazują, jak rozmieścić kontrolki w formularzu podobnym do Eksploratora Windows.</span><span class="sxs-lookup"><span data-stu-id="a7715-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="a7715-108">Nie pokazuje, jak dodać funkcję przeglądania plików aplikacji Eksploratora Windows.</span><span class="sxs-lookup"><span data-stu-id="a7715-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>

## <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="a7715-109">Aby utworzyć formularz systemu Windows w stylu Eksploratora Windows</span><span class="sxs-lookup"><span data-stu-id="a7715-109">To create a Windows Explorer-style Windows Form</span></span>

1. <span data-ttu-id="a7715-110">Tworzenie nowego projektu aplikacji systemu Windows (**plik** > **Nowy** > **projekt** > **Visual C#**  lub **Visual Basic** > **klasyczny** pulpit >  **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="a7715-110">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="a7715-111">Z **przybornika**:</span><span class="sxs-lookup"><span data-stu-id="a7715-111">From the **Toolbox**:</span></span>

    1. <span data-ttu-id="a7715-112"><xref:System.Windows.Forms.SplitContainer> Przeciągnij kontrolkę na formularz.</span><span class="sxs-lookup"><span data-stu-id="a7715-112">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>

    2. <span data-ttu-id="a7715-113">Przeciągnij kontrolkę do **SplitterPanel1** (Panel <xref:System.Windows.Forms.SplitContainer> kontrolki oznaczonej jako **element Panel1**). <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="a7715-113">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>

    3. <span data-ttu-id="a7715-114">Przeciągnij kontrolkę do **SplitterPanel2** (Panel <xref:System.Windows.Forms.SplitContainer> kontrolki oznaczonej jako **Panel2**). <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="a7715-114">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>

3. <span data-ttu-id="a7715-115">Zaznacz wszystkie trzy kontrolki, naciskając klawisz CTRL i klikając je.</span><span class="sxs-lookup"><span data-stu-id="a7715-115">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="a7715-116">Po wybraniu <xref:System.Windows.Forms.SplitContainer> kontrolki kliknij pasek podziału zamiast paneli.</span><span class="sxs-lookup"><span data-stu-id="a7715-116">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a7715-117">Nie należy używać polecenia **Zaznacz wszystko** w menu **Edycja** .</span><span class="sxs-lookup"><span data-stu-id="a7715-117">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="a7715-118">Jeśli to zrobisz, właściwość wymagana w następnym kroku nie zostanie wyświetlona w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="a7715-118">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>

4. <span data-ttu-id="a7715-119">W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.SplitContainer.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="a7715-119">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="a7715-120">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="a7715-120">Press F5 to run the application.</span></span>

     <span data-ttu-id="a7715-121">W formularzu zostanie wyświetlony dwuczęściowy interfejs użytkownika, podobny do tego w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="a7715-121">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a7715-122">Po przeciągnięciu rozdzielacza panele zmienią się.</span><span class="sxs-lookup"><span data-stu-id="a7715-122">When you drag the splitter, the panels resize themselves.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7715-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7715-123">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="a7715-124">Instrukcje: Tworzenie wielookienkowego interfejsu użytkownika z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7715-124">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="a7715-125">Instrukcje: Definiowanie zachowania zmiany rozmiaru i pozycjonowania w podzielonym oknie</span><span class="sxs-lookup"><span data-stu-id="a7715-125">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="a7715-126">Instrukcje: Podziel okno w poziomie</span><span class="sxs-lookup"><span data-stu-id="a7715-126">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="a7715-127">SplitContainer, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a7715-127">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
