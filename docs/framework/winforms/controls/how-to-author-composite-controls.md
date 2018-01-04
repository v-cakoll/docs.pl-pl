---
title: "Porady: autoryzowanie formantów złożonych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf68d4927daa79e160df42f94aff9cbcb611592
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="643c7-102">Porady: autoryzowanie formantów złożonych</span><span class="sxs-lookup"><span data-stu-id="643c7-102">How to: Author Composite Controls</span></span>
<span data-ttu-id="643c7-103">Formanty złożone można zastosować na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="643c7-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="643c7-104">Można tworzyć je jako część projekt aplikacji komputerowych systemu Windows i ich używać tylko w formularzach w projekcie.</span><span class="sxs-lookup"><span data-stu-id="643c7-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="643c7-105">Lub tworzyć je w projekcie Biblioteka formantów systemu Windows, skompiluj projekt do zestawu i użyj formantów w innych projektach.</span><span class="sxs-lookup"><span data-stu-id="643c7-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="643c7-106">Można nawet dziedziczą z nich i umożliwia szybkie dostosować je do celów specjalnych dziedziczenie visual.</span><span class="sxs-lookup"><span data-stu-id="643c7-106">You can even inherit from them, and use visual inheritance to customize them quickly for special purposes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="643c7-107">Jeśli chcesz tworzyć formantu złożonego do używania w formularzach sieci Web, zobacz [tworzenia kontrolek serwera ASP.NET niestandardowe](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="643c7-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="643c7-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="643c7-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="643c7-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="643c7-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="643c7-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="643c7-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-author-a-composite-control"></a><span data-ttu-id="643c7-111">Do tworzenia złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="643c7-111">To author a composite control</span></span>  
  
1.  <span data-ttu-id="643c7-112">Otwórz nowe **aplikacji systemu Windows** projektu o nazwie `DemoControlHost`.</span><span class="sxs-lookup"><span data-stu-id="643c7-112">Open a new **Windows Application** project called `DemoControlHost`.</span></span>  
  
2.  <span data-ttu-id="643c7-113">Na **projektu**menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="643c7-113">On the **Project**menu, click **Add User Control**.</span></span>  
  
3.  <span data-ttu-id="643c7-114">W **Dodaj nowy element** okno dialogowe, plik klasy (plik .vb lub CS) nazwę, która ma formant złożone, aby podać.</span><span class="sxs-lookup"><span data-stu-id="643c7-114">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>  
  
4.  <span data-ttu-id="643c7-115">Kliknij przycisk **Dodaj** przycisk, aby utworzyć plik klasy dla formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="643c7-115">Click the **Add** button to create the class file for the composite control.</span></span>  
  
5.  <span data-ttu-id="643c7-116">Dodaj formanty z **przybornika** na powierzchnię złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="643c7-116">Add controls from the **Toolbox** to the composite control surface.</span></span>  
  
6.  <span data-ttu-id="643c7-117">Umieść kod w procedurach zdarzeń do obsługi zdarzeń zgłaszanych przez formantu złożonego lub jego formantów składowych.</span><span class="sxs-lookup"><span data-stu-id="643c7-117">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>  
  
7.  <span data-ttu-id="643c7-118">Zamknij projektanta dla formantu złożonego, a następnie zapisz plik po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="643c7-118">Close the designer for the composite control, and save the file when you are prompted.</span></span>  
  
8.  <span data-ttu-id="643c7-119">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="643c7-119">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="643c7-120">Projektu muszą zostać skompilowane w kolejności, w przypadku kontrolek niestandardowych w wynikach **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="643c7-120">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="643c7-121">Użyj **DemoControlHost** karcie **przybornika** można dodać wystąpienia formantu do `Form1`.</span><span class="sxs-lookup"><span data-stu-id="643c7-121">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>  
  
### <a name="to-author-a-control-class-library"></a><span data-ttu-id="643c7-122">Do tworzenia biblioteki klas formantu</span><span class="sxs-lookup"><span data-stu-id="643c7-122">To author a control class library</span></span>  
  
1.  <span data-ttu-id="643c7-123">Otwórz nowe **Biblioteka formantów systemu Windows** projektu.</span><span class="sxs-lookup"><span data-stu-id="643c7-123">Open a new **Windows Control Library** project.</span></span>  
  
     <span data-ttu-id="643c7-124">Domyślnie projekt zawiera złożonych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="643c7-124">By default, the project contains a composite control.</span></span>  
  
2.  <span data-ttu-id="643c7-125">Dodaj formanty i kod, zgodnie z opisem w powyższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="643c7-125">Add controls and code as described in the procedure above.</span></span>  
  
3.  <span data-ttu-id="643c7-126">Wybierz formant nie ma dziedziczenie klas do zmiany, a następnie ustaw **Modyfikatory** właściwości do **prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="643c7-126">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>  
  
4.  <span data-ttu-id="643c7-127">Skompiluj bibliotekę DLL.</span><span class="sxs-lookup"><span data-stu-id="643c7-127">Build the DLL.</span></span>  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="643c7-128">Dziedziczenie z formantu złożonego w bibliotece klas formantu</span><span class="sxs-lookup"><span data-stu-id="643c7-128">To inherit from a composite control in a control class library</span></span>  
  
1.  <span data-ttu-id="643c7-129">Na **pliku** menu wskaż **Dodaj** i wybierz **nowy projekt** Aby dodać nowy **aplikacji systemu Windows** projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="643c7-129">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>  
  
2.  <span data-ttu-id="643c7-130">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** folderu dla nowego projektu i wybierz polecenie **Dodaj odwołanie do** można otworzyć **Dodaj odwołanie**okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="643c7-130">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
3.  <span data-ttu-id="643c7-131">Wybierz **projekty** karcie, a następnie kliknij dwukrotnie ikonę projektu biblioteki formantu.</span><span class="sxs-lookup"><span data-stu-id="643c7-131">Select the **Projects** tab and double-click your control library project.</span></span>  
  
4.  <span data-ttu-id="643c7-132">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="643c7-132">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="643c7-133">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projektu biblioteki sterowania i wybierz **Dodaj nowy element** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="643c7-133">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>  
  
6.  <span data-ttu-id="643c7-134">Wybierz **dziedziczone kontrolki użytkownika** szablonu z **Dodaj nowy element** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="643c7-134">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>  
  
7.  <span data-ttu-id="643c7-135">W **selektora dziedziczenia** okno dialogowe, kliknij dwukrotnie formant ma być dziedziczona z.</span><span class="sxs-lookup"><span data-stu-id="643c7-135">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>  
  
     <span data-ttu-id="643c7-136">Nowy formant został dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="643c7-136">A new control is added to your project.</span></span>  
  
8.  <span data-ttu-id="643c7-137">Otwórz projektanta dla nowego formantu i Dodaj formanty dodatkowych składników.</span><span class="sxs-lookup"><span data-stu-id="643c7-137">Open the visual designer for the new control and add additional constituent controls.</span></span>  
  
     <span data-ttu-id="643c7-138">Można sprawdzić formanty składników, które zostały odziedziczone złożonych kontrolek w bibliotece DLL i można zmieniać właściwości formantów których **Modyfikatory** właściwość jest **publicznego**.</span><span class="sxs-lookup"><span data-stu-id="643c7-138">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="643c7-139">Nie można zmienić właściwości formantu których **Modyfikatory** właściwość jest **prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="643c7-139">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643c7-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="643c7-140">See Also</span></span>  
 [<span data-ttu-id="643c7-141">Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="643c7-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="643c7-142">Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="643c7-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="643c7-143">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="643c7-143">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="643c7-144">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="643c7-144">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [<span data-ttu-id="643c7-145">Zalecenia dotyczące typu kontrolki</span><span class="sxs-lookup"><span data-stu-id="643c7-145">Control Type Recommendations</span></span>](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [<span data-ttu-id="643c7-146">Instrukcje: tworzenie kontrolek dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="643c7-146">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="643c7-147">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="643c7-147">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
