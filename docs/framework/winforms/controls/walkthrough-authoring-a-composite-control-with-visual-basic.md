---
title: 'Przewodnik: tworzenie kontrolki złożonej za pomocą Visual Basic'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: abfb91c61ef72bfc1626b4cc4dcea42b75e2ab35
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040241"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="cf1ae-102">Przewodnik: tworzenie kontrolki złożonej za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf1ae-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="cf1ae-103">Kontrolki złożone zapewniają metodę, za pomocą której można tworzyć i ponownie używać niestandardowych interfejsów graficznych.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="cf1ae-104">Formant złożony jest zasadniczo składnikiem z reprezentacją wizualną.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="cf1ae-105">W związku z tym może składać się z co najmniej jednego Windows Forms kontrolek, składników lub bloków kodu, który może zwiększyć funkcjonalność, sprawdzając dane wejściowe użytkownika, modyfikując właściwości wyświetlania lub wykonując inne zadania wymagane przez autora.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="cf1ae-106">Kontrolki złożone mogą być umieszczane na Windows Forms w taki sam sposób jak w przypadku innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="cf1ae-107">W pierwszej części tego przewodnika utworzysz prostą kontrolkę złożoną o nazwie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="cf1ae-108">W drugiej części przewodnika rozszerzono funkcjonalność programu `ctlClock` przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="cf1ae-109">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="cf1ae-109">Creating the Project</span></span>
 <span data-ttu-id="cf1ae-110">Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główną przestrzeń nazw, nazwę zestawu i nazwę projektu, i upewnić się, że składnik domyślny będzie w poprawnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="cf1ae-111">Aby utworzyć bibliotekę kontrolek ctlClockLib i formant ctlClock</span><span class="sxs-lookup"><span data-stu-id="cf1ae-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="cf1ae-112">W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt** , aby otworzyć okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="cf1ae-112">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="cf1ae-113">Z listy projektów Visual Basic wybierz szablon projektu **Biblioteka formantów systemu Windows** , wpisz `ctlClockLib` w polu **Nazwa** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-113">From the list of Visual Basic projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>

     <span data-ttu-id="cf1ae-114">Nazwa projektu, `ctlClockLib`, również jest domyślnie przypisana do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-114">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="cf1ae-115">Główna przestrzeń nazw służy do kwalifikowania nazw składników w zestawie.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-115">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="cf1ae-116">Na przykład jeśli dwa zestawy dostarczają składniki o nazwie `ctlClock`, można `ctlClock` określić składnik przy użyciu`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="cf1ae-116">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

3. <span data-ttu-id="cf1ae-117">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy **UserControl1. vb**, a następnie kliknij polecenie **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-117">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="cf1ae-118">Zmień nazwę pliku na `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-118">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="cf1ae-119">Kliknij przycisk **tak** po wyświetleniu monitu, jeśli chcesz zmienić nazwy wszystkich odwołań do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="cf1ae-119">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    >  <span data-ttu-id="cf1ae-120">Domyślnie formant złożony dziedziczy z <xref:System.Windows.Forms.UserControl> klasy dostarczonej przez system.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-120">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="cf1ae-121"><xref:System.Windows.Forms.UserControl> Klasa zawiera funkcje wymagane przez wszystkie kontrolki złożone i implementuje standardowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-121">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

4. <span data-ttu-id="cf1ae-122">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-122">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="cf1ae-123">Dodawanie formantów i składników systemu Windows do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="cf1ae-123">Adding Windows Controls and Components to the Composite Control</span></span>
 <span data-ttu-id="cf1ae-124">Interfejs wizualny jest istotną częścią formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-124">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="cf1ae-125">Ten interfejs wizualny jest implementowany przez dodanie jednego lub większej liczby kontrolek systemu Windows do powierzchni projektanta.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-125">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="cf1ae-126">Poniższa prezentacja zawiera kontrolki systemu Windows w kontrolce złożonej i pisanie kodu w celu zaimplementowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-126">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="cf1ae-127">Aby dodać etykietę i czasomierz do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="cf1ae-127">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="cf1ae-128">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlClock. vb**, a następnie kliknij pozycję **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-128">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="cf1ae-129">W przyborniku rozwiń węzeł **formanty wspólne** , a następnie kliknij dwukrotnie pozycję **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-129">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="cf1ae-130">Kontrolka o `Label1` nazwie jest dodawana do kontrolki na powierzchni projektanta. <xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="cf1ae-130">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="cf1ae-131">W projektancie kliknij pozycję **Label1**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-131">In the designer, click **Label1**.</span></span> <span data-ttu-id="cf1ae-132">W okno Właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-132">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="cf1ae-133">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cf1ae-133">Property</span></span>|<span data-ttu-id="cf1ae-134">Zmień na</span><span class="sxs-lookup"><span data-stu-id="cf1ae-134">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="cf1ae-135">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-135">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="cf1ae-136">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-136">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="cf1ae-137">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-137">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="cf1ae-138">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-138">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="cf1ae-139">W **przyborniku**rozwiń węzeł **składniki** , a następnie kliknij dwukrotnie przycisk **czasomierz**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-139">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="cf1ae-140">Ponieważ element <xref:System.Windows.Forms.Timer> jest składnikiem, nie ma żadnej wizualizacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-140">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="cf1ae-141">W związku z tym nie jest wyświetlany z kontrolkami na powierzchni projektanta, ale raczej w projektancie składników (zasobnik u dołu powierzchni projektanta).</span><span class="sxs-lookup"><span data-stu-id="cf1ae-141">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="cf1ae-142">W projektancie składników kliknij pozycję **Timer1**, a następnie ustaw <xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość na `1000` wartość i właściwość na `True`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-142">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>

     <span data-ttu-id="cf1ae-143"><xref:System.Windows.Forms.Timer.Interval%2A> Właściwość kontroluje częstotliwość taktowania składnika czasomierza.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-143">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="cf1ae-144">Każdy cykl `Timer1` czasu uruchamia kod `Timer1_Tick` w zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-144">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="cf1ae-145">Interwał reprezentuje liczbę milisekund między taktami.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-145">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="cf1ae-146">W projektancie składników kliknij dwukrotnie pozycję **Timer1** , aby przejść do `Timer1_Tick` zdarzenia. `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="cf1ae-146">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="cf1ae-147">Zmodyfikuj kod w taki sposób, aby wyglądał jak Poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-147">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="cf1ae-148">Upewnij się, że modyfikator dostępu został zmieniony `Private` z `Protected`na.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-148">Be sure to change the access modifier from `Private` to `Protected`.</span></span>

    ```vb
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles Timer1.Tick
        ' Causes the label to display the current time.
        lblDisplay.Text = Format(Now, "hh:mm:ss")
    End Sub
    ```

     <span data-ttu-id="cf1ae-149">Ten kod spowoduje, że bieżący czas będzie pokazywany w `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-149">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="cf1ae-150">Ze względu na `Timer1` to, że `1000`interwał został ustawiony na, to zdarzenie będzie wykonywane co tysiąc milisekund, co oznacza, że bieżący czas jest aktualizowany co sekundę.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-150">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="cf1ae-151">Zmodyfikuj metodę, aby była możliwy do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-151">Modify the method to be overridable.</span></span> <span data-ttu-id="cf1ae-152">Aby uzyskać więcej informacji, zobacz sekcję "dziedziczenie z kontrolki użytkownika" poniżej.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-152">For more information, see the "Inheriting from a User Control" section below.</span></span>

    ```vb
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _
        e As System.EventArgs) Handles Timer1.Tick
    ```

9. <span data-ttu-id="cf1ae-153">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-153">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="cf1ae-154">Dodawanie właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="cf1ae-154">Adding Properties to the Composite Control</span></span>
 <span data-ttu-id="cf1ae-155">Kontrolka zegara hermetyzuje <xref:System.Windows.Forms.Label> obecnie formant <xref:System.Windows.Forms.Timer> i składnik, z których każdy ma własny zestaw właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-155">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="cf1ae-156">Chociaż poszczególne właściwości tych kontrolek nie będą dostępne dla kolejnych użytkowników kontrolki, można utworzyć i uwidocznić właściwości niestandardowe przez napisanie odpowiednich bloków kodu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-156">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="cf1ae-157">Poniższa procedura obejmuje dodanie do kontrolki właściwości, które umożliwiają użytkownikowi zmianę koloru tła i tekstu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-157">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="cf1ae-158">Aby dodać właściwość do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="cf1ae-158">To add a property to your composite control</span></span>

1. <span data-ttu-id="cf1ae-159">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy **ctlClock. vb**, a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-159">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>

     <span data-ttu-id="cf1ae-160">Zostanie otwarty Edytor kodu dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-160">The Code Editor for your control opens.</span></span>

2. <span data-ttu-id="cf1ae-161">`Public Class ctlClock` Znajdź instrukcję.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-161">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="cf1ae-162">Poniżej wpisz poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-162">Beneath it, type the following code.</span></span>

    ```vb
    Private colFColor as Color
    Private colBColor as Color
    ```

     <span data-ttu-id="cf1ae-163">Te instrukcje tworzą zmienne prywatne, które będą używane do przechowywania wartości właściwości, które mają zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-163">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="cf1ae-164">Wstaw następujący kod poniżej deklaracji zmiennych z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-164">Insert the following code beneath the variable declarations from step 2.</span></span>

    ```vb
    ' Declares the name and type of the property.
    Property ClockBackColor() as Color
        ' Retrieves the value of the private variable colBColor.
        Get
            Return colBColor
        End Get
        ' Stores the selected value in the private variable colBColor, and
        ' updates the background color of the label control lblDisplay.
        Set(ByVal value as Color)
            colBColor = value
            lblDisplay.BackColor = colBColor
        End Set

    End Property
    ' Provides a similar set of instructions for the foreground color.
    Property ClockForeColor() as Color
        Get
            Return colFColor
        End Get
        Set(ByVal value as Color)
            colFColor = value
            lblDisplay.ForeColor = colFColor
        End Set
    End Property
    ```

     <span data-ttu-id="cf1ae-165">Poprzedni kod tworzy dwie właściwości `ClockForeColor` niestandardowe i `ClockBackColor`, dostępne dla kolejnych użytkowników tej `Property` kontrolki przez wywoływanie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-165">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="cf1ae-166">Instrukcje `Get` and`Set` zapewniają przechowywanie i pobieranie wartości właściwości, a także kod służący do implementowania funkcji odpowiednich dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-166">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="cf1ae-167">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-167">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="testing-the-control"></a><span data-ttu-id="cf1ae-168">Testowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="cf1ae-168">Testing the Control</span></span>
 <span data-ttu-id="cf1ae-169">Formanty nie są projektami autonomicznymi; muszą być hostowane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-169">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="cf1ae-170">Przetestuj zachowanie w czasie wykonywania formantu i wykonuj jego właściwości za pomocą **kontenera testów UserControl**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-170">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="cf1ae-171">Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-171">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="cf1ae-172">Aby przetestować kontrolkę</span><span class="sxs-lookup"><span data-stu-id="cf1ae-172">To test your control</span></span>

1. <span data-ttu-id="cf1ae-173">Naciśnij klawisz F5, aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-173">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="cf1ae-174">W siatce właściwości kontenera testów zaznacz `ClockBackColor` właściwość, a następnie kliknij strzałkę listy rozwijanej, aby wyświetlić paletę kolorów.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-174">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>

3. <span data-ttu-id="cf1ae-175">Wybierz kolor, klikając go.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-175">Choose a color by clicking it.</span></span>

     <span data-ttu-id="cf1ae-176">Kolor tła kontrolki zmieni się na wybrany kolor.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-176">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="cf1ae-177">Użyj podobnej sekwencji zdarzeń, aby sprawdzić, czy `ClockForeColor` Właściwość działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-177">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

5. <span data-ttu-id="cf1ae-178">Kliknij przycisk **Zamknij** , aby zamknąć **kontener testów UserControl**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-178">Click **Close** to close the **UserControl Test Container**.</span></span>

     <span data-ttu-id="cf1ae-179">W tej sekcji i w powyższych sekcjach pokazano, jak można łączyć składniki i formanty systemu Windows z kodem i opakowaniem, aby zapewnić niestandardowe funkcje w formie złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-179">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="cf1ae-180">Wiesz już, jak uwidocznić właściwości w kontrolce złożonej oraz jak przetestować swój formant po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-180">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="cf1ae-181">W następnej sekcji dowiesz się, jak utworzyć Dziedziczony formant złożony, używając `ctlClock` jako podstawy.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-181">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="cf1ae-182">Dziedziczenie z kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="cf1ae-182">Inheriting from a Composite Control</span></span>
 <span data-ttu-id="cf1ae-183">W poprzednich sekcjach przedstawiono sposób łączenia formantów, składników i kodu systemu Windows z kontrolkami złożonymi do wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-183">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="cf1ae-184">Formant złożony może być teraz używany jako podstawa, na której można skompilować inne kontrolki.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-184">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="cf1ae-185">Proces wyprowadzania klasy z klasy bazowej nosi nazwę *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-185">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="cf1ae-186">W tej sekcji utworzysz formant złożony o nazwie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-186">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="cf1ae-187">Ten formant będzie pochodzący z jego formantu `ctlClock`nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-187">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="cf1ae-188">Dowiesz się, jak zwiększyć funkcjonalność `ctlClock` przez zastępowanie metod nadrzędnych i dodawanie nowych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-188">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

 <span data-ttu-id="cf1ae-189">Pierwszym krokiem tworzenia dziedziczonej kontrolki jest uzyskanie jej z elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-189">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="cf1ae-190">Ta akcja tworzy nową kontrolkę, która ma wszystkie właściwości, metody i charakterystyki graficzne kontrolki nadrzędnej, ale może również stanowić podstawę do dodania nowych lub zmodyfikowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-190">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="cf1ae-191">Aby utworzyć Dziedziczony formant</span><span class="sxs-lookup"><span data-stu-id="cf1ae-191">To create the inherited control</span></span>

1. <span data-ttu-id="cf1ae-192">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Kontrola użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-192">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="cf1ae-193">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-193">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="cf1ae-194">Wybierz szablon **dziedziczonej kontrolki użytkownika** .</span><span class="sxs-lookup"><span data-stu-id="cf1ae-194">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="cf1ae-195">W polu **Nazwa** wpisz `ctlAlarmClock.vb`, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-195">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>

     <span data-ttu-id="cf1ae-196">Zostanie wyświetlone okno dialogowe **Selektor dziedziczenia** .</span><span class="sxs-lookup"><span data-stu-id="cf1ae-196">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="cf1ae-197">W obszarze **Nazwa składnika**kliknij dwukrotnie pozycję **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-197">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="cf1ae-198">W Eksplorator rozwiązań Przeglądaj bieżące projekty.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-198">In Solution Explorer, browse through the current projects.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="cf1ae-199">Plik o nazwie **ctlAlarmClock. vb** został dodany do bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-199">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>

### <a name="adding-the-alarm-properties"></a><span data-ttu-id="cf1ae-200">Dodawanie właściwości alarmu</span><span class="sxs-lookup"><span data-stu-id="cf1ae-200">Adding the Alarm Properties</span></span>
 <span data-ttu-id="cf1ae-201">Właściwości są dodawane do dziedziczonej kontrolki w taki sam sposób, w jaki są dodawane do kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-201">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="cf1ae-202">Teraz użyj składni deklaracji właściwości, aby dodać dwie właściwości do kontrolki: `AlarmTime`, w której będzie przechowywana wartość daty i godziny, w której ma się pojawić alarm, i `AlarmSet`wskazująca, czy alarm jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-202">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="cf1ae-203">Aby dodać właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="cf1ae-203">To add properties to your composite control</span></span>

1. <span data-ttu-id="cf1ae-204">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock**, a następnie kliknij pozycję **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-204">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="cf1ae-205">Znajdź deklarację klasy dla kontrolki ctlAlarmClock, która jest wyświetlana `Public Class ctlAlarmClock`jako.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-205">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="cf1ae-206">W deklaracji klasy Wstaw następujący kod.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-206">In the class declaration, insert the following code.</span></span>

    ```vb
    Private dteAlarmTime As Date
    Private blnAlarmSet As Boolean
    ' These properties will be declared as Public to allow future
    ' developers to access them.
    Public Property AlarmTime() As Date
        Get
            Return dteAlarmTime
        End Get
        Set(ByVal value as Date)
            dteAlarmTime = value
        End Set
    End Property
    Public Property AlarmSet() As Boolean
        Get
            Return blnAlarmSet
        End Get
        Set(ByVal value as Boolean)
            blnAlarmSet = value
        End Set
    End Property
    ```

### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="cf1ae-207">Dodawanie do interfejsu graficznego formantu</span><span class="sxs-lookup"><span data-stu-id="cf1ae-207">Adding to the Graphical Interface of the Control</span></span>
 <span data-ttu-id="cf1ae-208">Formant dziedziczony ma interfejs wizualny, który jest identyczny z kontrolką, z której dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-208">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="cf1ae-209">Posiada te same kontrolki elementów, jak jej kontrolki nadrzędne, ale właściwości kontrolek elementów nie będą dostępne, chyba że zostały one jawnie ujawnione.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-209">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="cf1ae-210">Można dodać do interfejsu graficznego dziedziczonego formantu złożonego w taki sam sposób, jak w przypadku dowolnej kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-210">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="cf1ae-211">Aby kontynuować dodawanie do interfejsu wizualizacji zegara alarmu, należy dodać kontrolkę etykieta, która będzie Flash, gdy alarm jest dźwiękowy.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-211">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="cf1ae-212">Aby dodać kontrolkę etykieta</span><span class="sxs-lookup"><span data-stu-id="cf1ae-212">To add the label control</span></span>

1. <span data-ttu-id="cf1ae-213">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock**, a następnie kliknij pozycję **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-213">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>

     <span data-ttu-id="cf1ae-214">Projektant do `ctlAlarmClock` otwarcia w oknie głównym.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-214">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="cf1ae-215">Kliknij `lblDisplay` (część wyświetlania kontrolki) i Wyświetl okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-215">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="cf1ae-216">Wszystkie właściwości są wyświetlane, są wygaszone.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-216">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="cf1ae-217">Oznacza to, że te właściwości są natywne `lblDisplay` i nie można ich modyfikować ani uzyskać do nich dostępu w okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-217">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="cf1ae-218">Domyślnie formanty zawarte w kontrolce złożonej są `Private`, a ich właściwości nie są dostępne w żaden sposób.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-218">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="cf1ae-219">Jeśli chcesz, aby inni użytkownicy formantu złożonego mieli dostęp do jego wewnętrznych formantów, zadeklaruj je jako `Public` lub `Protected`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-219">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="cf1ae-220">Umożliwi to Ustawianie i modyfikowanie właściwości kontrolek zawartych w kontrolce złożonej przy użyciu odpowiedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-220">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="cf1ae-221"><xref:System.Windows.Forms.Label> Dodaj kontrolkę do kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-221">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="cf1ae-222">Za pomocą myszy przeciągnij <xref:System.Windows.Forms.Label> formant bezpośrednio poniżej pola wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-222">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="cf1ae-223">W okno Właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-223">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="cf1ae-224">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cf1ae-224">Property</span></span>|<span data-ttu-id="cf1ae-225">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="cf1ae-225">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="cf1ae-226">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-226">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="cf1ae-227">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-227">**Text**</span></span>|<span data-ttu-id="cf1ae-228">**Uruchomienia!**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-228">**Alarm!**</span></span>|
    |<span data-ttu-id="cf1ae-229">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-229">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="cf1ae-230">**Widać**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-230">**Visible**</span></span>|`False`|

### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="cf1ae-231">Dodawanie funkcji alarmu</span><span class="sxs-lookup"><span data-stu-id="cf1ae-231">Adding the Alarm Functionality</span></span>
 <span data-ttu-id="cf1ae-232">W poprzednich procedurach dodano właściwości i kontrolkę, która spowoduje włączenie funkcji alarmu w formancie złożonym.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-232">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="cf1ae-233">W ramach tej procedury dodasz kod w celu porównania bieżącego czasu z czasem alarmu i, jeśli są one takie same, do dźwięku i błysku alarmu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-233">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="cf1ae-234">Poprzez zastąpienie `Timer1_Tick` `ctlAlarmClock` metody i dodanie do niej dodatkowego kodu, można zwiększyć możliwości programu, zachowując wszystkie nieodłączne funkcje programu `ctlClock`. `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="cf1ae-234">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="cf1ae-235">Aby zastąpić metodę Timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="cf1ae-235">To override the Timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="cf1ae-236">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy **ctlAlarmClock. vb**, a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-236">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>

2. <span data-ttu-id="cf1ae-237">`Private blnAlarmSet As Boolean` Znajdź instrukcję.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-237">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="cf1ae-238">Bezpośrednio poniżej, Dodaj następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-238">Immediately beneath it, add the following statement.</span></span>

    ```vb
    Dim blnColorTicker as Boolean
    ```

3. <span data-ttu-id="cf1ae-239">`End Class` Znajdź instrukcję w dolnej części strony.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-239">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="cf1ae-240">Tuż przed `End Class` instrukcją Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-240">Just before the `End Class` statement, add the following code.</span></span>

    ```vb
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _
        As System.EventArgs)
        ' Calls the Timer1_Tick method of ctlClock.
        MyBase.Timer1_Tick(sender, e)
        ' Checks to see if the Alarm is set.
        If AlarmSet = False Then
            Exit Sub
        End If
        ' If the date, hour, and minute of the alarm time are the same as
        ' now, flash and beep an alarm.
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _
            AlarmTime.Minute = Now.Minute Then
            ' Sounds an audible beep.
            Beep()
            ' Sets lblAlarmVisible to True, and changes the background color based on the
            ' value of blnColorTicker. The background color of the label will
            ' flash once per tick of the clock.
            lblAlarm.Visible = True
            If blnColorTicker = False Then
                lblAlarm.BackColor = Color.PeachPuff
                blnColorTicker = True
            Else
                lblAlarm.BackColor = Color.Plum
                blnColorTicker = False
            End If
        Else
            ' Once the alarm has sounded for a minute, the label is made
            ' invisible again.
            lblAlarm.Visible = False
        End If
    End Sub
    ```

     <span data-ttu-id="cf1ae-241">Dodanie tego kodu wykonuje kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-241">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="cf1ae-242">`Overrides` Instrukcja kieruje formant do użycia tej metody zamiast metody, która była dziedziczona z kontrolki podstawowej.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-242">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="cf1ae-243">Gdy ta metoda jest wywoływana, wywołuje metodę, która zastąpi przez wywoływanie `MyBase.Timer1_Tick` instrukcji, co zapewnia, że wszystkie funkcje wbudowane w pierwotnej kontrolce są odtwarzane w tym formancie.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-243">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="cf1ae-244">Następnie uruchamia dodatkowy kod w celu uwzględnienia funkcji alarmu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-244">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="cf1ae-245">Migająca kontrolka etykieta zostanie wyświetlona, gdy wystąpi alarm, i słychać dźwięk dźwiękowy.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-245">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="cf1ae-246">Ponieważ przesłaniasz dziedziczonego programu obsługi zdarzeń, nie trzeba określać zdarzenia za pomocą `Handles` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-246">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="cf1ae-247">Zdarzenie zostało już podłączane.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-247">The event is already hooked up.</span></span> <span data-ttu-id="cf1ae-248">Wszystkie zastępowanie są implementacją programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-248">All you are overriding is the implementation of the handler.</span></span>

     <span data-ttu-id="cf1ae-249">Kontrola zegara alarmu jest niemal ukończona.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-249">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="cf1ae-250">Jedyną czynnością, która pozostanie, jest zaimplementowanie sposobu jej wyłączenia.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-250">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="cf1ae-251">W tym celu należy dodać kod do `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-251">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="cf1ae-252">Aby zaimplementować metodę ShutOff</span><span class="sxs-lookup"><span data-stu-id="cf1ae-252">To implement the shutoff method</span></span>

1. <span data-ttu-id="cf1ae-253">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock. vb**, a następnie kliknij pozycję **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-253">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="cf1ae-254">W projektancie kliknij dwukrotnie pozycję **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-254">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="cf1ae-255">**Edytor kodu** zostanie otwarty `Private Sub lblAlarm_Click` w wierszu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-255">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>

3. <span data-ttu-id="cf1ae-256">Zmodyfikuj tę metodę, tak aby była podobna do poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-256">Modify this method so that it resembles the following code.</span></span>

    ```vb
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _
     System.EventArgs) Handles lblAlarm.Click
        ' Turns off the alarm.
        AlarmSet = False
        ' Hides the flashing label.
        lblAlarm.Visible = False
    End Sub
    ```

4. <span data-ttu-id="cf1ae-257">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-257">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="cf1ae-258">Używanie dziedziczonej kontrolki w formularzu</span><span class="sxs-lookup"><span data-stu-id="cf1ae-258">Using the Inherited Control on a Form</span></span>
 <span data-ttu-id="cf1ae-259">Można testować Dziedziczony formant w taki sam sposób, `ctlClock`w jaki przetestowano formant klasy bazowej: Naciśnij klawisz F5, aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-259">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="cf1ae-260">Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-260">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

 <span data-ttu-id="cf1ae-261">Aby można było użyć formantu, musisz go hostować w formularzu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-261">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="cf1ae-262">Podobnie jak w przypadku standardowej kontroli złożonej, Dziedziczony formant złożony nie może być autonomiczny i musi być hostowany w formie lub w innym kontenerze.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-262">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="cf1ae-263">Ponieważ `ctlAlarmClock` ma większą głębię funkcjonalności, wymagany jest dodatkowy kod do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-263">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="cf1ae-264">Ta procedura polega na napisaniu prostego programu w celu przetestowania funkcji programu `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-264">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="cf1ae-265">Napisz kod `AlarmTime` `ctlAlarmClock`, aby ustawić i wyświetlić właściwość, i przetestować jej funkcje.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-265">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="cf1ae-266">Aby skompilować i dodać formant do formularza testowego</span><span class="sxs-lookup"><span data-stu-id="cf1ae-266">To build and add your control to a test form</span></span>

1. <span data-ttu-id="cf1ae-267">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **ctlClockLib**, a następnie kliknij pozycję **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-267">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="cf1ae-268">W menu **plik** wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-268">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>

3. <span data-ttu-id="cf1ae-269">Dodaj nowy projekt **aplikacji systemu Windows** do rozwiązania i nadaj mu `Test`nazwę.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-269">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>

     <span data-ttu-id="cf1ae-270">Projekt **testowy** zostanie dodany do Eksplorator rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-270">The **Test** project is added to Solution Explorer.</span></span>

4. <span data-ttu-id="cf1ae-271">W Eksplorator rozwiązań kliknij prawym przyciskiem `Test` myszy węzeł projektu, a następnie kliknij pozycję **Dodaj odwołanie** , aby wyświetlić okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="cf1ae-271">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="cf1ae-272">Kliknij kartę z etykietą **projekty**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-272">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="cf1ae-273">Projekt **ctlClockLib** zostanie wyświetlony na liście **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-273">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="cf1ae-274">Kliknij dwukrotnie pozycję **ctlClockLib** , aby dodać odwołanie do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-274">Double-click **ctlClockLib** to add the reference to the test project.</span></span>

6. <span data-ttu-id="cf1ae-275">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **test**, a następnie kliknij polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-275">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>

7. <span data-ttu-id="cf1ae-276">W **przyborniku**rozwiń węzeł **składniki ctlClockLib** .</span><span class="sxs-lookup"><span data-stu-id="cf1ae-276">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

8. <span data-ttu-id="cf1ae-277">Kliknij dwukrotnie pozycję **ctlAlarmClock** , aby dodać wystąpienie `ctlAlarmClock` do formularza.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-277">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>

9. <span data-ttu-id="cf1ae-278">W **przyborniku**Znajdź i kliknij dwukrotnie pozycję **DateTimePicker** , <xref:System.Windows.Forms.DateTimePicker> aby dodać kontrolkę do <xref:System.Windows.Forms.Label> formularza, a następnie Dodaj kontrolkę, klikając dwukrotnie pozycję **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-278">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

10. <span data-ttu-id="cf1ae-279">Użyj myszy, aby ustawić kontrolki w wygodnym miejscu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-279">Use the mouse to position the controls in a convenient place on the form.</span></span>

11. <span data-ttu-id="cf1ae-280">Ustaw właściwości tych kontrolek w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-280">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="cf1ae-281">formant</span><span class="sxs-lookup"><span data-stu-id="cf1ae-281">Control</span></span>|<span data-ttu-id="cf1ae-282">Właściwość</span><span class="sxs-lookup"><span data-stu-id="cf1ae-282">Property</span></span>|<span data-ttu-id="cf1ae-283">Wartość</span><span class="sxs-lookup"><span data-stu-id="cf1ae-283">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="cf1ae-284">**Text**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-284">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="cf1ae-285">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-285">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="cf1ae-286">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-286">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="cf1ae-287">**Formatowanie**</span><span class="sxs-lookup"><span data-stu-id="cf1ae-287">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

12. <span data-ttu-id="cf1ae-288">W projektancie kliknij dwukrotnie pozycję **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-288">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="cf1ae-289">Zostanie otwarty `Private Sub dtpTest_ValueChanged` **Edytor kodu** .</span><span class="sxs-lookup"><span data-stu-id="cf1ae-289">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>

13. <span data-ttu-id="cf1ae-290">Zmodyfikuj kod w taki sposób, aby wyglądał następująco.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-290">Modify the code so that it resembles the following.</span></span>

    ```vb
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles dtpTest.ValueChanged
        ctlAlarmClock1.AlarmTime = dtpTest.Value
        ctlAlarmClock1.AlarmSet = True
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _
            "hh:mm")
    End Sub
    ```

14. <span data-ttu-id="cf1ae-291">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy pozycję **test**, a następnie kliknij pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-291">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

15. <span data-ttu-id="cf1ae-292">Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-292">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="cf1ae-293">Zostanie uruchomiony program testowy.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-293">The test program starts.</span></span> <span data-ttu-id="cf1ae-294">Należy pamiętać, że bieżący czas jest aktualizowany w `ctlAlarmClock` kontrolce, a czas rozpoczęcia jest pokazywany <xref:System.Windows.Forms.DateTimePicker> w formancie.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-294">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

16. <span data-ttu-id="cf1ae-295"><xref:System.Windows.Forms.DateTimePicker> Kliknij miejsce, gdzie są wyświetlane minuty godziny.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-295">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

17. <span data-ttu-id="cf1ae-296">Korzystając z klawiatury, ustaw wartość minut na minutę, która jest większa niż bieżąca godzina pokazana przez `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-296">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="cf1ae-297">Godzina ustawienia alarmu jest pokazywana w `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-297">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="cf1ae-298">Poczekaj, aż wyświetlany czas osiągnie czas ustawienia alarmu.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-298">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="cf1ae-299">Gdy wyświetlany czas osiągnie czas, w którym ustawiono alarm, dźwięk zostanie dźwiękowy i `lblAlarm` rozpocznie się błysk.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-299">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>

18. <span data-ttu-id="cf1ae-300">Wyłącz alarm, klikając pozycję `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-300">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="cf1ae-301">Teraz możesz zresetować alarm.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-301">You may now reset the alarm.</span></span>

     <span data-ttu-id="cf1ae-302">W tym instruktażu przedstawiono szereg kluczowych pojęć.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-302">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="cf1ae-303">Wiesz już, jak utworzyć formant złożony przez połączenie formantów i składników do kontenera kontroli złożonej.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-303">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="cf1ae-304">Wiesz już, jak dodać właściwości do kontrolki i napisać kod w celu zaimplementowania funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-304">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="cf1ae-305">W ostatniej sekcji pokazano, jak zwiększyć funkcjonalność danego formantu złożonego przez dziedziczenie i zmienić funkcjonalność metod hosta, zastępując te metody.</span><span class="sxs-lookup"><span data-stu-id="cf1ae-305">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf1ae-306">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf1ae-306">See also</span></span>

- [<span data-ttu-id="cf1ae-307">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="cf1ae-307">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="cf1ae-308">Instrukcje: Tworzenie złożonych kontrolek</span><span class="sxs-lookup"><span data-stu-id="cf1ae-308">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="cf1ae-309">Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="cf1ae-309">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
