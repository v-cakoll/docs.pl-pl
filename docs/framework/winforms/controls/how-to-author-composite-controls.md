---
title: 'Instrukcje: autoryzowanie kontrolek złożonych'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 08cb07ceebf08b3096415f9b7370e2d955152cb6
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015935"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="e811e-102">Instrukcje: Tworzenie złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="e811e-102">How to: Author composite controls</span></span>

<span data-ttu-id="e811e-103">Kontrolki złożone mogą być stosowane na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="e811e-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="e811e-104">Można je tworzyć w ramach projektu aplikacji klasycznych systemu Windows i używać ich tylko na formularzach w projekcie.</span><span class="sxs-lookup"><span data-stu-id="e811e-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="e811e-105">Można też tworzyć je w projekcie biblioteki formantów systemu Windows, kompilować projekt do zestawu i używać kontrolek w innych projektach.</span><span class="sxs-lookup"><span data-stu-id="e811e-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="e811e-106">Można nawet dziedziczyć z nich i użyć dziedziczenia wizualnego, aby szybko dostosować je do specjalnych celów.</span><span class="sxs-lookup"><span data-stu-id="e811e-106">You can even inherit from them and use visual inheritance to customize them quickly for special purposes.</span></span>

## <a name="to-author-a-composite-control"></a><span data-ttu-id="e811e-107">Aby utworzyć formant złożony</span><span class="sxs-lookup"><span data-stu-id="e811e-107">To author a composite control</span></span>

1. <span data-ttu-id="e811e-108">W programie Visual Studio Utwórz nowy projekt **aplikacji systemu Windows** , a następnie nadaj mu nazwę **DemoControlHost**.</span><span class="sxs-lookup"><span data-stu-id="e811e-108">In Visual Studio, create a new **Windows Application** project, and name it **DemoControlHost**.</span></span>

2. <span data-ttu-id="e811e-109">W menu **projekt** kliknij polecenie **Dodaj kontrolkę użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="e811e-109">On the **Project** menu, click **Add User Control**.</span></span>

3. <span data-ttu-id="e811e-110">W oknie dialogowym **Dodaj nowy element** Nadaj plikowi klasy (plik VB lub CS) nazwę, która ma mieć formant złożony.</span><span class="sxs-lookup"><span data-stu-id="e811e-110">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>

4. <span data-ttu-id="e811e-111">Wybierz przycisk **Dodaj** , aby utworzyć plik klasy dla formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="e811e-111">Select the **Add** button to create the class file for the composite control.</span></span>

5. <span data-ttu-id="e811e-112">Dodaj kontrolki z **przybornika** do powierzchni formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="e811e-112">Add controls from the **Toolbox** to the composite control surface.</span></span>

6. <span data-ttu-id="e811e-113">Umieść kod w procedurach zdarzeń, aby obsłużyć zdarzenia wywoływane przez formant złożony lub jego elementy sterujące.</span><span class="sxs-lookup"><span data-stu-id="e811e-113">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>

7. <span data-ttu-id="e811e-114">Zamknij projektanta dla kontrolki złożonej i Zapisz plik po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="e811e-114">Close the designer for the composite control, and save the file when you are prompted.</span></span>

8. <span data-ttu-id="e811e-115">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="e811e-115">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="e811e-116">Projekt musi być skompilowany, aby formanty niestandardowe były wyświetlane w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="e811e-116">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>

9. <span data-ttu-id="e811e-117">Użyj karty **DemoControlHost** przybornika, aby dodać wystąpienia formantu do `Form1`programu.</span><span class="sxs-lookup"><span data-stu-id="e811e-117">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>

## <a name="to-author-a-control-class-library"></a><span data-ttu-id="e811e-118">Aby utworzyć bibliotekę klas formantów</span><span class="sxs-lookup"><span data-stu-id="e811e-118">To author a control class library</span></span>

1. <span data-ttu-id="e811e-119">Otwórz nowy projekt **biblioteki formantów systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="e811e-119">Open a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="e811e-120">Domyślnie projekt zawiera formant złożony.</span><span class="sxs-lookup"><span data-stu-id="e811e-120">By default, the project contains a composite control.</span></span>

2. <span data-ttu-id="e811e-121">Dodaj kontrolki i kod zgodnie z opisem w powyższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="e811e-121">Add controls and code as described in the procedure above.</span></span>

3. <span data-ttu-id="e811e-122">Wybierz kontrolkę, której klasy nie chcesz zmienić, i ustaw właściwość Modyfikatory tej kontrolki na **prywatną**.</span><span class="sxs-lookup"><span data-stu-id="e811e-122">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>

4. <span data-ttu-id="e811e-123">Skompiluj bibliotekę DLL.</span><span class="sxs-lookup"><span data-stu-id="e811e-123">Build the DLL.</span></span>

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="e811e-124">Aby dziedziczyć z formantu złożonego w bibliotece klas formantów</span><span class="sxs-lookup"><span data-stu-id="e811e-124">To inherit from a composite control in a control class library</span></span>

1. <span data-ttu-id="e811e-125">W menu **plik** wskaż polecenie **Dodaj** i wybierz pozycję **Nowy projekt** , aby dodać nowy projekt **aplikacji systemu Windows** do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e811e-125">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>

2. <span data-ttu-id="e811e-126">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **odwołania** dla nowego projektu i wybierz polecenie **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="e811e-126">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

3. <span data-ttu-id="e811e-127">Wybierz kartę **projekty** i kliknij dwukrotnie projekt Biblioteka kontrolek.</span><span class="sxs-lookup"><span data-stu-id="e811e-127">Select the **Projects** tab and double-click your control library project.</span></span>

4. <span data-ttu-id="e811e-128">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="e811e-128">On the **Build** menu, click **Build Solution**.</span></span>

5. <span data-ttu-id="e811e-129">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt Biblioteka formantów i wybierz polecenie **Dodaj nowy element** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="e811e-129">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>

6. <span data-ttu-id="e811e-130">Wybierz **Dziedziczony szablon kontrolki użytkownika** w oknie dialogowym **Dodaj nowy element** .</span><span class="sxs-lookup"><span data-stu-id="e811e-130">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>

7. <span data-ttu-id="e811e-131">W oknie dialogowym **Selektor dziedziczenia** kliknij dwukrotnie formant, z którego chcesz dziedziczyć.</span><span class="sxs-lookup"><span data-stu-id="e811e-131">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>

     <span data-ttu-id="e811e-132">Do projektu zostanie dodany nowy formant.</span><span class="sxs-lookup"><span data-stu-id="e811e-132">A new control is added to your project.</span></span>

8. <span data-ttu-id="e811e-133">Otwórz projektanta wizualnego dla nowej kontrolki i Dodaj dodatkowe kontrolki elementów.</span><span class="sxs-lookup"><span data-stu-id="e811e-133">Open the visual designer for the new control and add additional constituent controls.</span></span>

     <span data-ttu-id="e811e-134">Można zobaczyć kontrolki elementów, które zostały odziedziczone z formantu złożonego w bibliotece DLL, i można zmienić właściwości formantów, których właściwość **modyfikatorów** jest publiczna.</span><span class="sxs-lookup"><span data-stu-id="e811e-134">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="e811e-135">Nie można zmienić właściwości kontrolki, której właściwość **modyfikatorów** jest **prywatna**.</span><span class="sxs-lookup"><span data-stu-id="e811e-135">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e811e-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e811e-136">See also</span></span>

- [<span data-ttu-id="e811e-137">Przewodnik: Tworzenie kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="e811e-137">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="e811e-138">Przewodnik: Dziedziczenie z kontrolki Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e811e-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="e811e-139">Zalecenia dotyczące typu kontrolki</span><span class="sxs-lookup"><span data-stu-id="e811e-139">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="e811e-140">Instrukcje: Kontrolki autora dla Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e811e-140">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="e811e-141">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="e811e-141">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
