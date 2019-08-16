---
title: 'Instrukcje: autoryzowanie kontrolek złożonych'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 7b0ee8efa62175e2ced2a810ca6dd76e8adc103b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039895"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="35354-102">Instrukcje: autoryzowanie kontrolek złożonych</span><span class="sxs-lookup"><span data-stu-id="35354-102">How to: Author Composite Controls</span></span>

<span data-ttu-id="35354-103">Kontrolki złożone mogą być stosowane na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="35354-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="35354-104">Można je tworzyć w ramach projektu aplikacji klasycznych systemu Windows i używać ich tylko na formularzach w projekcie.</span><span class="sxs-lookup"><span data-stu-id="35354-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="35354-105">Można też tworzyć je w projekcie biblioteki formantów systemu Windows, kompilować projekt do zestawu i używać kontrolek w innych projektach.</span><span class="sxs-lookup"><span data-stu-id="35354-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="35354-106">Można nawet dziedziczyć z nich i użyć dziedziczenia wizualnego, aby szybko dostosować je do specjalnych celów.</span><span class="sxs-lookup"><span data-stu-id="35354-106">You can even inherit from them and use visual inheritance to customize them quickly for special purposes.</span></span>

> [!NOTE]
> <span data-ttu-id="35354-107">Jeśli chcesz utworzyć formant złożony do użycia w formularzach sieci Web, zobacz [Tworzenie niestandardowych kontrolek serwera ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="35354-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="to-author-a-composite-control"></a><span data-ttu-id="35354-108">Aby utworzyć formant złożony</span><span class="sxs-lookup"><span data-stu-id="35354-108">To author a composite control</span></span>

1. <span data-ttu-id="35354-109">W programie Visual Studio Utwórz nowy projekt **aplikacji systemu Windows** o `DemoControlHost`nazwie.</span><span class="sxs-lookup"><span data-stu-id="35354-109">In Visual Studio, create a new **Windows Application** project called `DemoControlHost`.</span></span>

2. <span data-ttu-id="35354-110">W menu **projekt** kliknij polecenie **Dodaj kontrolkę użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="35354-110">On the **Project** menu, click **Add User Control**.</span></span>

3. <span data-ttu-id="35354-111">W oknie dialogowym **Dodaj nowy element** Nadaj plikowi klasy (plik VB lub CS) nazwę, która ma mieć formant złożony.</span><span class="sxs-lookup"><span data-stu-id="35354-111">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>

4. <span data-ttu-id="35354-112">Wybierz przycisk **Dodaj** , aby utworzyć plik klasy dla formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="35354-112">Select the **Add** button to create the class file for the composite control.</span></span>

5. <span data-ttu-id="35354-113">Dodaj kontrolki z **przybornika** do powierzchni formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="35354-113">Add controls from the **Toolbox** to the composite control surface.</span></span>

6. <span data-ttu-id="35354-114">Umieść kod w procedurach zdarzeń, aby obsłużyć zdarzenia wywoływane przez formant złożony lub jego elementy sterujące.</span><span class="sxs-lookup"><span data-stu-id="35354-114">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>

7. <span data-ttu-id="35354-115">Zamknij projektanta dla kontrolki złożonej i Zapisz plik po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="35354-115">Close the designer for the composite control, and save the file when you are prompted.</span></span>

8. <span data-ttu-id="35354-116">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="35354-116">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="35354-117">Projekt musi być skompilowany, aby formanty niestandardowe były wyświetlane w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="35354-117">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>

9. <span data-ttu-id="35354-118">Użyj karty **DemoControlHost** przybornika, aby dodać wystąpienia formantu do `Form1`programu.</span><span class="sxs-lookup"><span data-stu-id="35354-118">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>

## <a name="to-author-a-control-class-library"></a><span data-ttu-id="35354-119">Aby utworzyć bibliotekę klas formantów</span><span class="sxs-lookup"><span data-stu-id="35354-119">To author a control class library</span></span>

1. <span data-ttu-id="35354-120">Otwórz nowy projekt **biblioteki formantów systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="35354-120">Open a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="35354-121">Domyślnie projekt zawiera formant złożony.</span><span class="sxs-lookup"><span data-stu-id="35354-121">By default, the project contains a composite control.</span></span>

2. <span data-ttu-id="35354-122">Dodaj kontrolki i kod zgodnie z opisem w powyższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="35354-122">Add controls and code as described in the procedure above.</span></span>

3. <span data-ttu-id="35354-123">Wybierz kontrolkę, której klasy nie chcesz zmienić, i ustaw właściwość Modyfikatory tej kontrolki na **prywatną**.</span><span class="sxs-lookup"><span data-stu-id="35354-123">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>

4. <span data-ttu-id="35354-124">Skompiluj bibliotekę DLL.</span><span class="sxs-lookup"><span data-stu-id="35354-124">Build the DLL.</span></span>

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="35354-125">Aby dziedziczyć z formantu złożonego w bibliotece klas formantów</span><span class="sxs-lookup"><span data-stu-id="35354-125">To inherit from a composite control in a control class library</span></span>

1. <span data-ttu-id="35354-126">W menu **plik** wskaż polecenie **Dodaj** i wybierz pozycję **Nowy projekt** , aby dodać nowy projekt **aplikacji systemu Windows** do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="35354-126">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>

2. <span data-ttu-id="35354-127">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **odwołania** dla nowego projektu i wybierz polecenie **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="35354-127">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

3. <span data-ttu-id="35354-128">Wybierz kartę **projekty** i kliknij dwukrotnie projekt Biblioteka kontrolek.</span><span class="sxs-lookup"><span data-stu-id="35354-128">Select the **Projects** tab and double-click your control library project.</span></span>

4. <span data-ttu-id="35354-129">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="35354-129">On the **Build** menu, click **Build Solution**.</span></span>

5. <span data-ttu-id="35354-130">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt Biblioteka formantów i wybierz polecenie **Dodaj nowy element** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="35354-130">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>

6. <span data-ttu-id="35354-131">Wybierz **Dziedziczony szablon kontrolki użytkownika** w oknie dialogowym **Dodaj nowy element** .</span><span class="sxs-lookup"><span data-stu-id="35354-131">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>

7. <span data-ttu-id="35354-132">W oknie dialogowym **Selektor dziedziczenia** kliknij dwukrotnie formant, z którego chcesz dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="35354-132">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>

     <span data-ttu-id="35354-133">Do projektu zostanie dodany nowy formant.</span><span class="sxs-lookup"><span data-stu-id="35354-133">A new control is added to your project.</span></span>

8. <span data-ttu-id="35354-134">Otwórz projektanta wizualnego dla nowej kontrolki i Dodaj dodatkowe kontrolki elementów.</span><span class="sxs-lookup"><span data-stu-id="35354-134">Open the visual designer for the new control and add additional constituent controls.</span></span>

     <span data-ttu-id="35354-135">Można zobaczyć kontrolki elementów, które zostały odziedziczone z formantu złożonego w bibliotece DLL, i można zmienić właściwości formantów, których właściwość **modyfikatorów** jest publiczna.</span><span class="sxs-lookup"><span data-stu-id="35354-135">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="35354-136">Nie można zmienić właściwości kontrolki, której właściwość **modyfikatorów** jest **prywatna**.</span><span class="sxs-lookup"><span data-stu-id="35354-136">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>

## <a name="see-also"></a><span data-ttu-id="35354-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35354-137">See also</span></span>

- [<span data-ttu-id="35354-138">Przewodnik: Tworzenie złożonego formantu z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35354-138">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="35354-139">Przewodnik: Tworzenie formantu złożonego za pomocą wizualizacjiC#</span><span class="sxs-lookup"><span data-stu-id="35354-139">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="35354-140">Przewodnik: Dziedziczenie z kontrolki Windows Forms z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35354-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="35354-141">Przewodnik: Dziedziczenie z kontrolki Windows Forms za pomocą wizualizacjiC#</span><span class="sxs-lookup"><span data-stu-id="35354-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="35354-142">Zalecenia dotyczące typu kontrolki</span><span class="sxs-lookup"><span data-stu-id="35354-142">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="35354-143">Instrukcje: Kontrolki autora dla Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35354-143">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="35354-144">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="35354-144">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
