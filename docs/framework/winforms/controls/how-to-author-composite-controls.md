---
title: 'Porady: autoryzowanie formantów złożonych'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 7abdeae4d19ceb6425f85e3cdd28f565a03d7ea4
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508252"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="53f75-102">Porady: autoryzowanie formantów złożonych</span><span class="sxs-lookup"><span data-stu-id="53f75-102">How to: Author Composite Controls</span></span>
<span data-ttu-id="53f75-103">Formanty złożone można zastosować na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="53f75-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="53f75-104">Można tworzyć w ramach projektu aplikacji pulpitu Windows i ich używać tylko na formularze w projekcie.</span><span class="sxs-lookup"><span data-stu-id="53f75-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="53f75-105">Lub można je tworzyć w projekcie Biblioteka formantów Windows, skompilowanie projektu do zestawu i użyj formantów w innych projektach.</span><span class="sxs-lookup"><span data-stu-id="53f75-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="53f75-106">Można również dziedziczyć z nich i umożliwia szybkie dostosować je do specjalnych celów dziedziczenie visual.</span><span class="sxs-lookup"><span data-stu-id="53f75-106">You can even inherit from them, and use visual inheritance to customize them quickly for special purposes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53f75-107">Jeśli chcesz tworzyć kontrolki złożonej do użycia w formularzach sieci Web, zobacz artykuł [tworzenia formanty serwera ASP.NET niestandardowe](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="53f75-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="53f75-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="53f75-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="53f75-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="53f75-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="53f75-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="53f75-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-author-a-composite-control"></a><span data-ttu-id="53f75-111">Tworzenie kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="53f75-111">To author a composite control</span></span>  
  
1.  <span data-ttu-id="53f75-112">Otwórz nowy **aplikacji Windows** projekt o nazwie `DemoControlHost`.</span><span class="sxs-lookup"><span data-stu-id="53f75-112">Open a new **Windows Application** project called `DemoControlHost`.</span></span>  
  
2.  <span data-ttu-id="53f75-113">Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="53f75-113">On the **Project** menu, click **Add User Control**.</span></span>  
  
3.  <span data-ttu-id="53f75-114">W **Dodaj nowy element** okno dialogowe, Dodaj plik klasy (plik .vb lub .cs) nazwę, która ma formant złożony, aby.</span><span class="sxs-lookup"><span data-stu-id="53f75-114">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>  
  
4.  <span data-ttu-id="53f75-115">Wybierz **Dodaj** przycisk, aby utworzyć plik klasy dla kontrolek złożonych.</span><span class="sxs-lookup"><span data-stu-id="53f75-115">Select the **Add** button to create the class file for the composite control.</span></span>  
  
5.  <span data-ttu-id="53f75-116">Dodawanie formantów z **przybornika** do powierzchni złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="53f75-116">Add controls from the **Toolbox** to the composite control surface.</span></span>  
  
6.  <span data-ttu-id="53f75-117">Umieść kod w procedurach zdarzeń, do obsługi zdarzeń wywołanych przez złożonego formantu lub jego formantów składowych.</span><span class="sxs-lookup"><span data-stu-id="53f75-117">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>  
  
7.  <span data-ttu-id="53f75-118">Zamknij projektanta dla formantu złożonego, a następnie zapisz plik, po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="53f75-118">Close the designer for the composite control, and save the file when you are prompted.</span></span>  
  
8.  <span data-ttu-id="53f75-119">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="53f75-119">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="53f75-120">Projekt musi być zbudowany w kolejności, w przypadku kontrolek niestandardowych, które będą wyświetlane na **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="53f75-120">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="53f75-121">Użyj **DemoControlHost** karcie **przybornika** dodać wystąpienia kontrolki do `Form1`.</span><span class="sxs-lookup"><span data-stu-id="53f75-121">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>  
  
### <a name="to-author-a-control-class-library"></a><span data-ttu-id="53f75-122">Aby utworzyć bibliotekę klas formantów</span><span class="sxs-lookup"><span data-stu-id="53f75-122">To author a control class library</span></span>  
  
1.  <span data-ttu-id="53f75-123">Otwórz nowy **Biblioteka formantów Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="53f75-123">Open a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="53f75-124">Domyślnie projektu zawiera kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="53f75-124">By default, the project contains a composite control.</span></span>  
  
2.  <span data-ttu-id="53f75-125">Dodaj formanty i kod, zgodnie z opisem w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="53f75-125">Add controls and code as described in the procedure above.</span></span>  
  
3.  <span data-ttu-id="53f75-126">Wybierz kontrolkę, która nie dziedziczy z klasy, aby zmienić i ustawić **Modyfikatory** właściwość tej kontrolki na **prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="53f75-126">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>  
  
4.  <span data-ttu-id="53f75-127">Skompiluj bibliotekę DLL.</span><span class="sxs-lookup"><span data-stu-id="53f75-127">Build the DLL.</span></span>  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="53f75-128">Dziedziczenie z kontrolki złożonej w bibliotece klas formantów</span><span class="sxs-lookup"><span data-stu-id="53f75-128">To inherit from a composite control in a control class library</span></span>  
  
1.  <span data-ttu-id="53f75-129">Na **pliku** menu wskaż **Dodaj** i wybierz **nowy projekt** Aby dodać nowy **aplikacji Windows** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="53f75-129">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>  
  
2.  <span data-ttu-id="53f75-130">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** nowy folder projektu, a następnie wybierz **Dodaj odwołanie** otworzyć **Dodaj odwołanie**okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="53f75-130">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
3.  <span data-ttu-id="53f75-131">Wybierz **projektów** kartę, a następnie kliknij dwukrotnie ikonę kontrolki projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="53f75-131">Select the **Projects** tab and double-click your control library project.</span></span>  
  
4.  <span data-ttu-id="53f75-132">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="53f75-132">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="53f75-133">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt Biblioteka kontroli i wybierz **Dodaj nowy element** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="53f75-133">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>  
  
6.  <span data-ttu-id="53f75-134">Wybierz **dziedziczone kontrolki użytkownika** szablonu z **Dodaj nowy element** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="53f75-134">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>  
  
7.  <span data-ttu-id="53f75-135">W **selektor dziedziczenia** okna dialogowego pole, kliknij dwukrotnie formant ma być dziedziczona z.</span><span class="sxs-lookup"><span data-stu-id="53f75-135">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>  
  
     <span data-ttu-id="53f75-136">Nowy formant zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="53f75-136">A new control is added to your project.</span></span>  
  
8.  <span data-ttu-id="53f75-137">Otwórz projektanta wizualnego nowego formantu i Dodaj dodatkowe formanty składników.</span><span class="sxs-lookup"><span data-stu-id="53f75-137">Open the visual designer for the new control and add additional constituent controls.</span></span>  
  
     <span data-ttu-id="53f75-138">Możesz zobaczyć formanty składników, które zostały odziedziczone złożonej kontrolki w bibliotece DLL, a można zmienić właściwości formantów którego **Modyfikatory** właściwość jest **publicznych**.</span><span class="sxs-lookup"><span data-stu-id="53f75-138">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="53f75-139">Nie można zmienić właściwości formantu którego **Modyfikatory** właściwość **prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="53f75-139">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f75-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53f75-140">See Also</span></span>  
 [<span data-ttu-id="53f75-141">Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53f75-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="53f75-142">Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="53f75-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="53f75-143">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53f75-143">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="53f75-144">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="53f75-144">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [<span data-ttu-id="53f75-145">Zalecenia dotyczące typu kontrolki</span><span class="sxs-lookup"><span data-stu-id="53f75-145">Control Type Recommendations</span></span>](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [<span data-ttu-id="53f75-146">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="53f75-146">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="53f75-147">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="53f75-147">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
