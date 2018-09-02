---
title: 'Porady: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 249210d2bcb7a9ef2c5bf1aed00bcfe138193aab
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456710"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="87e86-102">Porady: tworzenie interfejsu w stylu Eksploratora Windows na formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="87e86-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="87e86-103">Eksplorator Windows jest wspólne wybór interfejsu użytkownika dla aplikacji ze względu na swoją znajomość gotowe.</span><span class="sxs-lookup"><span data-stu-id="87e86-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="87e86-104">Eksplorator Windows jest zasadniczo <xref:System.Windows.Forms.TreeView> kontroli i <xref:System.Windows.Forms.ListView> formantu w oddzielnych paneli.</span><span class="sxs-lookup"><span data-stu-id="87e86-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="87e86-105">Rozdzielacz zostają o zmiennym rozmiarze paneli.</span><span class="sxs-lookup"><span data-stu-id="87e86-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="87e86-106">Taki układ kontrolki jest bardzo skuteczny sposób na wyświetlanie i informacji o przeglądaniu.</span><span class="sxs-lookup"><span data-stu-id="87e86-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="87e86-107">Poniższe kroki pokazują, jak można rozmieścić formanty w Windows Explorer przypominającej formularza.</span><span class="sxs-lookup"><span data-stu-id="87e86-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="87e86-108">Nie są wyświetlane jak dodać funkcję przeglądania plików aplikacji w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="87e86-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87e86-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="87e86-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="87e86-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="87e86-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="87e86-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="87e86-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="87e86-112">Aby utworzyć formularz Windows stylu Eksploratora Windows</span><span class="sxs-lookup"><span data-stu-id="87e86-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1.  <span data-ttu-id="87e86-113">Utwórz nowy projekt aplikacji Windows (**pliku** > **New** > **projektu** > **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="87e86-113">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="87e86-114">Z **przybornika**:</span><span class="sxs-lookup"><span data-stu-id="87e86-114">From the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="87e86-115">Przeciągnij <xref:System.Windows.Forms.SplitContainer> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="87e86-115">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2.  <span data-ttu-id="87e86-116">Przeciągnij <xref:System.Windows.Forms.TreeView> sterowania do **SplitterPanel1** (z panelu <xref:System.Windows.Forms.SplitContainer> kontroli oznaczone **Panel1**).</span><span class="sxs-lookup"><span data-stu-id="87e86-116">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3.  <span data-ttu-id="87e86-117">Przeciągnij <xref:System.Windows.Forms.ListView> sterowania do **SplitterPanel2** (z panelu <xref:System.Windows.Forms.SplitContainer> kontroli oznaczone **elementu Panel2**).</span><span class="sxs-lookup"><span data-stu-id="87e86-117">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3.  <span data-ttu-id="87e86-118">Zaznacz wszystkie trzy, naciskając klawisz CTRL i klikając je z osobna.</span><span class="sxs-lookup"><span data-stu-id="87e86-118">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="87e86-119">Po wybraniu <xref:System.Windows.Forms.SplitContainer> sterowania, kliknij pasek podziału, a nie paneli.</span><span class="sxs-lookup"><span data-stu-id="87e86-119">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87e86-120">Nie używaj **Zaznacz wszystko** polecenie **Edytuj** menu.</span><span class="sxs-lookup"><span data-stu-id="87e86-120">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="87e86-121">Jeśli tak zrobisz, właściwość potrzebna w następnym kroku nie będą widoczne w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="87e86-121">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="87e86-122">W **właściwości** oknie <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="87e86-122">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="87e86-123">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="87e86-123">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="87e86-124">Formularz zawiera interfejs użytkownika składający się z dwóch części, podobnie jak w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="87e86-124">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87e86-125">Podczas przeciągania rozdzielacza zmienić rozmiar paneli, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="87e86-125">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e86-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87e86-126">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="87e86-127">Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87e86-127">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [<span data-ttu-id="87e86-128">Instrukcje: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie</span><span class="sxs-lookup"><span data-stu-id="87e86-128">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [<span data-ttu-id="87e86-129">Instrukcje: dzielenie okna w poziomie</span><span class="sxs-lookup"><span data-stu-id="87e86-129">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [<span data-ttu-id="87e86-130">SplitContainer, kontrolka</span><span class="sxs-lookup"><span data-stu-id="87e86-130">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
