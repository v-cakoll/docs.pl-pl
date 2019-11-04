---
title: 'Wskazówki: tworzenie formantu złożonego za pomocą Visual C#'
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c1d9be77550b1255a24120c68f20d25640e0ebdf
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460631"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a><span data-ttu-id="6fc37-102">Przewodnik: Tworzenie kontrolki złożonej za pomocą języka C\#</span><span class="sxs-lookup"><span data-stu-id="6fc37-102">Walkthrough: Author a Composite Control with C\#</span></span>

<span data-ttu-id="6fc37-103">Kontrolki złożone zapewniają metodę, za pomocą której można tworzyć i ponownie używać niestandardowych interfejsów graficznych.</span><span class="sxs-lookup"><span data-stu-id="6fc37-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="6fc37-104">Formant złożony jest zasadniczo składnikiem z reprezentacją wizualną.</span><span class="sxs-lookup"><span data-stu-id="6fc37-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="6fc37-105">W związku z tym może składać się z co najmniej jednego Windows Forms kontrolek, składników lub bloków kodu, który może zwiększyć funkcjonalność, sprawdzając dane wejściowe użytkownika, modyfikując właściwości wyświetlania lub wykonując inne zadania wymagane przez autora.</span><span class="sxs-lookup"><span data-stu-id="6fc37-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="6fc37-106">Kontrolki złożone mogą być umieszczane na Windows Forms w taki sam sposób jak w przypadku innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="6fc37-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="6fc37-107">W pierwszej części tego przewodnika utworzysz prostą kontrolkę złożoną o nazwie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="6fc37-108">W drugiej części przewodnika rozszerzono funkcjonalność `ctlClock` przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="6fc37-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="6fc37-109">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="6fc37-109">Create the Project</span></span>

<span data-ttu-id="6fc37-110">Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główną przestrzeń nazw, nazwę zestawu i nazwę projektu, i upewnić się, że składnik domyślny będzie w poprawnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6fc37-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="6fc37-111">Aby utworzyć bibliotekę kontrolek ctlClockLib i formant ctlClock</span><span class="sxs-lookup"><span data-stu-id="6fc37-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="6fc37-112">W programie Visual Studio Utwórz nowy projekt **biblioteki formantów Windows Forms** i nadaj mu nazwę **ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-112">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ctlClockLib**.</span></span>

     <span data-ttu-id="6fc37-113">Nazwa projektu, `ctlClockLib`, również jest domyślnie przypisana do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6fc37-113">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="6fc37-114">Główna przestrzeń nazw służy do kwalifikowania nazw składników w zestawie.</span><span class="sxs-lookup"><span data-stu-id="6fc37-114">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="6fc37-115">Na przykład jeśli dwa zestawy zapewniają składniki o nazwie `ctlClock`, można określić składnik `ctlClock` przy użyciu `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="6fc37-115">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

2. <span data-ttu-id="6fc37-116">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **UserControl1.cs**, a następnie kliknij polecenie **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-116">In **Solution Explorer**, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="6fc37-117">Zmień nazwę pliku na `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-117">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="6fc37-118">Kliknij przycisk **tak** po wyświetleniu monitu, jeśli chcesz zmienić nazwy wszystkich odwołań do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="6fc37-118">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="6fc37-119">Domyślnie formant złożony dziedziczy z klasy <xref:System.Windows.Forms.UserControl> dostarczonej przez system.</span><span class="sxs-lookup"><span data-stu-id="6fc37-119">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="6fc37-120">Klasa <xref:System.Windows.Forms.UserControl> zapewnia funkcje wymagane przez wszystkie kontrolki złożone i implementuje standardowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fc37-120">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

3. <span data-ttu-id="6fc37-121">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="6fc37-121">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="6fc37-122">Dodawanie formantów i składników systemu Windows do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="6fc37-122">Add Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="6fc37-123">Interfejs wizualny jest istotną częścią formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="6fc37-123">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="6fc37-124">Ten interfejs wizualny jest implementowany przez dodanie jednego lub większej liczby kontrolek systemu Windows do powierzchni projektanta.</span><span class="sxs-lookup"><span data-stu-id="6fc37-124">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="6fc37-125">Poniższa prezentacja zawiera kontrolki systemu Windows w kontrolce złożonej i pisanie kodu w celu zaimplementowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="6fc37-125">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="6fc37-126">Aby dodać etykietę i czasomierz do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="6fc37-126">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="6fc37-127">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlClock.cs**, a następnie kliknij pozycję **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-127">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="6fc37-128">W **przyborniku**rozwiń węzeł **formanty wspólne** , a następnie kliknij dwukrotnie pozycję **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-128">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="6fc37-129">Kontrolka <xref:System.Windows.Forms.Label> o nazwie `label1` jest dodawana do kontrolki na powierzchni projektanta.</span><span class="sxs-lookup"><span data-stu-id="6fc37-129">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="6fc37-130">W projektancie kliknij pozycję **Label1**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-130">In the designer, click **label1**.</span></span> <span data-ttu-id="6fc37-131">W okno Właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fc37-131">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="6fc37-132">Właściwość</span><span class="sxs-lookup"><span data-stu-id="6fc37-132">Property</span></span>|<span data-ttu-id="6fc37-133">Zmień na</span><span class="sxs-lookup"><span data-stu-id="6fc37-133">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="6fc37-134">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6fc37-134">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="6fc37-135">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6fc37-135">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="6fc37-136">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="6fc37-136">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="6fc37-137">**Font. size**</span><span class="sxs-lookup"><span data-stu-id="6fc37-137">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="6fc37-138">W **przyborniku**rozwiń węzeł **składniki** , a następnie kliknij dwukrotnie przycisk **czasomierz**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-138">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="6fc37-139">Ponieważ <xref:System.Windows.Forms.Timer> jest składnikiem, nie ma żadnej wizualizacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6fc37-139">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="6fc37-140">W związku z tym nie jest wyświetlany z kontrolkami na powierzchni projektanta, ale raczej w **projektancie składników** (zasobnik u dołu powierzchni projektanta).</span><span class="sxs-lookup"><span data-stu-id="6fc37-140">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="6fc37-141">W **projektancie składników**kliknij pozycję **Timer1**, a następnie ustaw właściwość <xref:System.Windows.Forms.Timer.Interval%2A> na `1000` i Właściwość <xref:System.Windows.Forms.Timer.Enabled%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-141">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="6fc37-142">Właściwość <xref:System.Windows.Forms.Timer.Interval%2A> kontroluje częstotliwość, z którą <xref:System.Windows.Forms.Timer> składnik.</span><span class="sxs-lookup"><span data-stu-id="6fc37-142">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="6fc37-143">Za każdym razem, gdy `timer1` takty, uruchamia kod w zdarzeniu `timer1_Tick`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-143">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="6fc37-144">Interwał reprezentuje liczbę milisekund między taktami.</span><span class="sxs-lookup"><span data-stu-id="6fc37-144">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="6fc37-145">W **projektancie składników**kliknij dwukrotnie pozycję **Timer1** , aby przejść do zdarzenia `timer1_Tick` `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-145">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="6fc37-146">Zmodyfikuj kod w taki sposób, aby wyglądał jak Poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-146">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="6fc37-147">Zmień modyfikator dostępu z `private` na `protected`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-147">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="6fc37-148">Ten kod spowoduje, że bieżący czas będzie pokazywany w `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-148">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="6fc37-149">Ponieważ interwał `timer1` został ustawiony na `1000`, to zdarzenie będzie wykonywane co tysiąc milisekund, co oznacza zaktualizowanie bieżącego czasu co sekundę.</span><span class="sxs-lookup"><span data-stu-id="6fc37-149">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="6fc37-150">Zmodyfikuj metodę, aby można było ją zastąpić za pomocą słowa kluczowego `virtual`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-150">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="6fc37-151">Aby uzyskać więcej informacji, zobacz sekcję "dziedziczenie z kontrolki użytkownika" poniżej.</span><span class="sxs-lookup"><span data-stu-id="6fc37-151">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="6fc37-152">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="6fc37-152">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-properties-to-the-composite-control"></a><span data-ttu-id="6fc37-153">Dodawanie właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="6fc37-153">Add Properties to the Composite Control</span></span>

<span data-ttu-id="6fc37-154">Kontrolka zegara hermetyzuje obecnie formant <xref:System.Windows.Forms.Label> i składnik <xref:System.Windows.Forms.Timer>, z których każdy ma własny zestaw właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fc37-154">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="6fc37-155">Chociaż poszczególne właściwości tych kontrolek nie będą dostępne dla kolejnych użytkowników kontrolki, można utworzyć i uwidocznić właściwości niestandardowe przez napisanie odpowiednich bloków kodu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-155">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="6fc37-156">Poniższa procedura obejmuje dodanie do kontrolki właściwości, które umożliwiają użytkownikowi zmianę koloru tła i tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-156">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="6fc37-157">Aby dodać właściwość do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="6fc37-157">To add a property to your composite control</span></span>

1. <span data-ttu-id="6fc37-158">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlClock.cs**, a następnie kliknij pozycję **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-158">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="6fc37-159">Zostanie otwarty **Edytor kodu** dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6fc37-159">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="6fc37-160">Znajdź instrukcję `public partial class ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-160">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="6fc37-161">Poniżej otwierającego nawiasu klamrowego (`{)`wpisz poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="6fc37-161">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="6fc37-162">Te instrukcje tworzą zmienne prywatne, które będą używane do przechowywania wartości właściwości, które mają zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="6fc37-162">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="6fc37-163">Wprowadź lub wklej następujący kod poniżej deklaracji zmiennych z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="6fc37-163">Enter or paste the following code beneath the variable declarations from step 2.</span></span>

    ```csharp
    // Declares the name and type of the property.
    public Color ClockBackColor
    {
        // Retrieves the value of the private variable colBColor.
        get
        {
            return colBColor;
        }
        // Stores the selected value in the private variable colBColor, and
        // updates the background color of the label control lblDisplay.
        set
        {
            colBColor = value;
            lblDisplay.BackColor = colBColor;
        }
    }
    // Provides a similar set of instructions for the foreground color.
    public Color ClockForeColor
    {
        get
        {
            return colFColor;
        }
        set
        {
            colFColor = value;
            lblDisplay.ForeColor = colFColor;
        }
    }
    ```

     <span data-ttu-id="6fc37-164">Poprzedni kod tworzy dwie niestandardowe właściwości, `ClockForeColor` i `ClockBackColor`, dostępne dla kolejnych użytkowników tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6fc37-164">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="6fc37-165">Instrukcje `get` i `set` zapewniają przechowywanie i pobieranie wartości właściwości, a także kodu do implementacji funkcji odpowiednich dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fc37-165">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="6fc37-166">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="6fc37-166">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="6fc37-167">Testowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="6fc37-167">Test the Control</span></span>

<span data-ttu-id="6fc37-168">Formanty nie są aplikacjami autonomicznymi; muszą być hostowane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="6fc37-168">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="6fc37-169">Przetestuj zachowanie w czasie wykonywania formantu i wykonuj jego właściwości za pomocą **kontenera testów UserControl**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-169">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="6fc37-170">Aby uzyskać więcej informacji, zobacz [jak: testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="6fc37-170">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="6fc37-171">Aby przetestować kontrolkę</span><span class="sxs-lookup"><span data-stu-id="6fc37-171">To test your control</span></span>

1. <span data-ttu-id="6fc37-172">Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-172">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="6fc37-173">W siatce właściwości kontenera testów Znajdź Właściwość `ClockBackColor`, a następnie wybierz właściwość, aby wyświetlić paletę kolorów.</span><span class="sxs-lookup"><span data-stu-id="6fc37-173">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="6fc37-174">Wybierz kolor, klikając go.</span><span class="sxs-lookup"><span data-stu-id="6fc37-174">Choose a color by clicking it.</span></span>

   <span data-ttu-id="6fc37-175">Kolor tła kontrolki zmieni się na wybrany kolor.</span><span class="sxs-lookup"><span data-stu-id="6fc37-175">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="6fc37-176">Użyj podobnej sekwencji zdarzeń, aby sprawdzić, czy właściwość `ClockForeColor` działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="6fc37-176">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

   <span data-ttu-id="6fc37-177">W tej sekcji i w powyższych sekcjach pokazano, jak można łączyć składniki i formanty systemu Windows z kodem i opakowaniem, aby zapewnić niestandardowe funkcje w formie złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-177">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="6fc37-178">Wiesz już, jak uwidocznić właściwości w kontrolce złożonej oraz jak przetestować swój formant po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-178">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="6fc37-179">W następnej sekcji dowiesz się, jak utworzyć Dziedziczony formant złożony przy użyciu `ctlClock` jako podstawy.</span><span class="sxs-lookup"><span data-stu-id="6fc37-179">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inherit-from-a-composite-control"></a><span data-ttu-id="6fc37-180">Dziedzicz z kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="6fc37-180">Inherit from a Composite Control</span></span>

<span data-ttu-id="6fc37-181">W poprzednich sekcjach przedstawiono sposób łączenia formantów, składników i kodu systemu Windows z kontrolkami złożonymi do wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="6fc37-181">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="6fc37-182">Formant złożony może być teraz używany jako podstawa, na której można skompilować inne kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6fc37-182">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="6fc37-183">Proces wyprowadzania klasy z klasy bazowej nosi nazwę *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="6fc37-183">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="6fc37-184">W tej sekcji utworzysz formant złożony o nazwie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-184">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="6fc37-185">Ta kontrolka będzie wyprowadzana z jej formantu nadrzędnego, `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-185">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="6fc37-186">Dowiesz się, jak zwiększyć funkcjonalność `ctlClock`, zastępując metody nadrzędne i dodając nowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fc37-186">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="6fc37-187">Pierwszym krokiem tworzenia dziedziczonej kontrolki jest uzyskanie jej z elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6fc37-187">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="6fc37-188">Ta akcja tworzy nową kontrolkę, która ma wszystkie właściwości, metody i charakterystyki graficzne kontrolki nadrzędnej, ale może również stanowić podstawę do dodania nowych lub zmodyfikowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="6fc37-188">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="6fc37-189">Aby utworzyć Dziedziczony formant</span><span class="sxs-lookup"><span data-stu-id="6fc37-189">To create the inherited control</span></span>

1. <span data-ttu-id="6fc37-190">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Kontrola użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-190">In **Solution Explorer**, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="6fc37-191">Zostanie otwarte okno dialogowe **Dodaj nowy element** .</span><span class="sxs-lookup"><span data-stu-id="6fc37-191">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="6fc37-192">Wybierz szablon **dziedziczonej kontrolki użytkownika** .</span><span class="sxs-lookup"><span data-stu-id="6fc37-192">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="6fc37-193">W polu **Nazwa** wpisz `ctlAlarmClock.cs`, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-193">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="6fc37-194">Zostanie wyświetlone okno dialogowe **Selektor dziedziczenia** .</span><span class="sxs-lookup"><span data-stu-id="6fc37-194">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="6fc37-195">W obszarze **Nazwa składnika**kliknij dwukrotnie pozycję **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-195">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="6fc37-196">W **Eksplorator rozwiązań**Przeglądaj bieżące projekty.</span><span class="sxs-lookup"><span data-stu-id="6fc37-196">In **Solution Explorer**, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6fc37-197">Plik o nazwie **ctlAlarmClock.cs** został dodany do bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-197">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="add-the-alarm-properties"></a><span data-ttu-id="6fc37-198">Dodaj właściwości alarmu</span><span class="sxs-lookup"><span data-stu-id="6fc37-198">Add the Alarm Properties</span></span>

<span data-ttu-id="6fc37-199">Właściwości są dodawane do dziedziczonej kontrolki w taki sam sposób, w jaki są dodawane do kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="6fc37-199">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="6fc37-200">Teraz użyjesz składni deklaracji właściwości, aby dodać dwie właściwości do kontrolki: `AlarmTime`, w której będzie przechowywana wartość daty i czasu alarmu, a `AlarmSet`, która wskazuje, czy alarm jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="6fc37-200">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="6fc37-201">Aby dodać właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="6fc37-201">To add properties to your composite control</span></span>

1. <span data-ttu-id="6fc37-202">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock**, a następnie kliknij pozycję **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-202">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="6fc37-203">Znajdź instrukcję `public class`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-203">Locate the `public class` statement.</span></span> <span data-ttu-id="6fc37-204">Należy zauważyć, że formant dziedziczy po `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-204">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="6fc37-205">Poniżej otwierającego nawiasu klamrowego (`{)` instrukcji wpisz poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="6fc37-205">Beneath the opening brace (`{)` statement, type the following code.</span></span>

    ```csharp
    private DateTime dteAlarmTime;
    private bool blnAlarmSet;
    // These properties will be declared as public to allow future
    // developers to access them.
    public DateTime AlarmTime
    {
        get
        {
            return dteAlarmTime;
        }
        set
        {
            dteAlarmTime = value;
        }
    }
    public bool AlarmSet
    {
        get
        {
            return blnAlarmSet;
        }
        set
        {
            blnAlarmSet = value;
        }
    }
    ```

### <a name="add-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="6fc37-206">Dodaj do interfejsu graficznego formantu</span><span class="sxs-lookup"><span data-stu-id="6fc37-206">Add to the Graphical Interface of the Control</span></span>

<span data-ttu-id="6fc37-207">Formant dziedziczony ma interfejs wizualny, który jest identyczny z kontrolką, z której dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="6fc37-207">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="6fc37-208">Posiada te same kontrolki elementów, jak jej kontrolki nadrzędne, ale właściwości kontrolek elementów nie będą dostępne, chyba że zostały one jawnie ujawnione.</span><span class="sxs-lookup"><span data-stu-id="6fc37-208">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="6fc37-209">Można dodać do interfejsu graficznego dziedziczonego formantu złożonego w taki sam sposób, jak w przypadku dowolnej kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="6fc37-209">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="6fc37-210">Aby kontynuować dodawanie do interfejsu wizualizacji zegara alarmu, należy dodać kontrolkę etykieta, która będzie Flash, gdy alarm jest dźwiękowy.</span><span class="sxs-lookup"><span data-stu-id="6fc37-210">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="6fc37-211">Aby dodać kontrolkę etykieta</span><span class="sxs-lookup"><span data-stu-id="6fc37-211">To add the label control</span></span>

1. <span data-ttu-id="6fc37-212">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock**, a następnie kliknij pozycję **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-212">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="6fc37-213">Projektant dla `ctlAlarmClock` otwiera się w oknie głównym.</span><span class="sxs-lookup"><span data-stu-id="6fc37-213">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="6fc37-214">Kliknij część ekranu kontrolki i Wyświetl okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fc37-214">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6fc37-215">Wszystkie właściwości są wyświetlane, są wygaszone.</span><span class="sxs-lookup"><span data-stu-id="6fc37-215">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="6fc37-216">Oznacza to, że te właściwości są natywne dla `lblDisplay` i nie można ich modyfikować ani uzyskiwać do nich dostępu w okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fc37-216">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="6fc37-217">Domyślnie formanty zawarte w kontrolce złożonej są `private`, a ich właściwości nie są dostępne w żaden sposób.</span><span class="sxs-lookup"><span data-stu-id="6fc37-217">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6fc37-218">Jeśli chcesz, aby użytkownicy formantu złożonego mieli dostęp do swoich wewnętrznych kontrolek, zadeklaruj je jako `public` lub `protected`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-218">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="6fc37-219">Umożliwi to Ustawianie i modyfikowanie właściwości kontrolek zawartych w kontrolce złożonej przy użyciu odpowiedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-219">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="6fc37-220">Dodaj kontrolkę <xref:System.Windows.Forms.Label> do formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="6fc37-220">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="6fc37-221">Za pomocą myszy przeciągnij kontrolkę <xref:System.Windows.Forms.Label> bezpośrednio poniżej pola wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="6fc37-221">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="6fc37-222">W okno Właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="6fc37-222">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="6fc37-223">Właściwość</span><span class="sxs-lookup"><span data-stu-id="6fc37-223">Property</span></span>|<span data-ttu-id="6fc37-224">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="6fc37-224">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="6fc37-225">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6fc37-225">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="6fc37-226">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6fc37-226">**Text**</span></span>|<span data-ttu-id="6fc37-227">**Uruchomienia!**</span><span class="sxs-lookup"><span data-stu-id="6fc37-227">**Alarm!**</span></span>|
    |<span data-ttu-id="6fc37-228">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="6fc37-228">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="6fc37-229">**Widać**</span><span class="sxs-lookup"><span data-stu-id="6fc37-229">**Visible**</span></span>|`false`|

### <a name="add-the-alarm-functionality"></a><span data-ttu-id="6fc37-230">Dodawanie funkcji alarmu</span><span class="sxs-lookup"><span data-stu-id="6fc37-230">Add the Alarm Functionality</span></span>

<span data-ttu-id="6fc37-231">W poprzednich procedurach dodano właściwości i kontrolkę, która spowoduje włączenie funkcji alarmu w formancie złożonym.</span><span class="sxs-lookup"><span data-stu-id="6fc37-231">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="6fc37-232">W ramach tej procedury dodasz kod w celu porównania bieżącego czasu z czasem alarmu i, jeśli są one takie same, do nabłysku alarmu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-232">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="6fc37-233">Zastępując `timer1_Tick` metodę `ctlClock` i dodając do niej dodatkowy kod, będzie można zwiększyć możliwości `ctlAlarmClock` przy zachowaniu wszystkich nieodłącznych funkcji `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-233">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="6fc37-234">Aby zastąpić metodę timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="6fc37-234">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="6fc37-235">W **edytorze kodu**znajdź instrukcję `private bool blnAlarmSet;`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-235">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="6fc37-236">Bezpośrednio poniżej, Dodaj następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="6fc37-236">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="6fc37-237">W **edytorze kodu**Znajdź zamykający nawias klamrowy (`})` na końcu klasy.</span><span class="sxs-lookup"><span data-stu-id="6fc37-237">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="6fc37-238">Tuż przed nawiasem klamrowym Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="6fc37-238">Just before the brace, add the following code.</span></span>

    ```csharp
    protected override void timer1_Tick(object sender, System.EventArgs e)
    {
        // Calls the Timer1_Tick method of ctlClock.
        base.timer1_Tick(sender, e);
        // Checks to see if the alarm is set.
        if (AlarmSet == false)
            return;
        else
            // If the date, hour, and minute of the alarm time are the same as
            // the current time, flash an alarm.
        {
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)
            {
                // Sets lblAlarmVisible to true, and changes the background color based on
                // the value of blnColorTicker. The background color of the label
                // will flash once per tick of the clock.
                lblAlarm.Visible = true;
                if (blnColorTicker == false)
                {
                    lblAlarm.BackColor = Color.Red;
                    blnColorTicker = true;
                }
                else
                {
                    lblAlarm.BackColor = Color.Blue;
                    blnColorTicker = false;
                }
            }
            else
            {
                // Once the alarm has sounded for a minute, the label is made
                // invisible again.
                lblAlarm.Visible = false;
            }
        }
    }
    ```

     <span data-ttu-id="6fc37-239">Dodanie tego kodu wykonuje kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="6fc37-239">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="6fc37-240">Instrukcja `override` kieruje formant do użycia tej metody zamiast metody, która była dziedziczona z kontrolki podstawowej.</span><span class="sxs-lookup"><span data-stu-id="6fc37-240">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="6fc37-241">Gdy ta metoda jest wywoływana, wywołuje metodę, która zastąpi przez wywołanie instrukcji `base.timer1_Tick`, co zapewnia, że wszystkie funkcje wbudowane w pierwotnej kontrolce są odtwarzane w tym formancie.</span><span class="sxs-lookup"><span data-stu-id="6fc37-241">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="6fc37-242">Następnie uruchamia dodatkowy kod w celu uwzględnienia funkcji alarmu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-242">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="6fc37-243">Migająca kontrolka etykieta zostanie wyświetlona, gdy wystąpi alarm.</span><span class="sxs-lookup"><span data-stu-id="6fc37-243">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="6fc37-244">Kontrola zegara alarmu jest niemal ukończona.</span><span class="sxs-lookup"><span data-stu-id="6fc37-244">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="6fc37-245">Jedyną czynnością, która pozostanie, jest zaimplementowanie sposobu jej wyłączenia.</span><span class="sxs-lookup"><span data-stu-id="6fc37-245">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="6fc37-246">W tym celu należy dodać kod do metody `lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-246">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="6fc37-247">Aby zaimplementować metodę ShutOff</span><span class="sxs-lookup"><span data-stu-id="6fc37-247">To implement the shutoff method</span></span>

1. <span data-ttu-id="6fc37-248">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock.cs**, a następnie kliknij pozycję **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-248">In **Solution Explorer**, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="6fc37-249">Zostanie otwarty projektant.</span><span class="sxs-lookup"><span data-stu-id="6fc37-249">The designer opens.</span></span>

2. <span data-ttu-id="6fc37-250">Dodaj przycisk do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6fc37-250">Add a button to the control.</span></span> <span data-ttu-id="6fc37-251">Ustaw właściwości przycisku w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="6fc37-251">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="6fc37-252">Właściwość</span><span class="sxs-lookup"><span data-stu-id="6fc37-252">Property</span></span>|<span data-ttu-id="6fc37-253">Wartość</span><span class="sxs-lookup"><span data-stu-id="6fc37-253">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="6fc37-254">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6fc37-254">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="6fc37-255">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6fc37-255">**Text**</span></span>|<span data-ttu-id="6fc37-256">**Wyłącz alarm**</span><span class="sxs-lookup"><span data-stu-id="6fc37-256">**Disable Alarm**</span></span>|

3. <span data-ttu-id="6fc37-257">W projektancie kliknij dwukrotnie pozycję **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-257">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="6fc37-258">**Edytor kodu** zostanie otwarty w wierszu `private void btnAlarmOff_Click`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-258">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="6fc37-259">Zmodyfikuj tę metodę, tak aby była podobna do poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-259">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="6fc37-260">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="6fc37-260">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="use-the-inherited-control-on-a-form"></a><span data-ttu-id="6fc37-261">Używanie dziedziczonej kontrolki w formularzu</span><span class="sxs-lookup"><span data-stu-id="6fc37-261">Use the Inherited Control on a Form</span></span>

<span data-ttu-id="6fc37-262">Można testować Dziedziczony formant w taki sam sposób, w jaki przetestowano kontrolkę klasy bazowej, `ctlClock`: naciśnij klawisz **F5** , aby skompilować projekt i uruchomić formant w **kontenerze testów UserControl**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="6fc37-263">Aby uzyskać więcej informacji, zobacz [jak: testowanie zachowania elementu UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="6fc37-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="6fc37-264">Aby można było użyć formantu, musisz go hostować w formularzu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="6fc37-265">Podobnie jak w przypadku standardowej kontroli złożonej, Dziedziczony formant złożony nie może być autonomiczny i musi być hostowany w formie lub w innym kontenerze.</span><span class="sxs-lookup"><span data-stu-id="6fc37-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="6fc37-266">Ponieważ `ctlAlarmClock` ma większą głębię funkcjonalności, wymagany jest dodatkowy kod do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="6fc37-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="6fc37-267">Ta procedura polega na napisaniu prostego programu w celu przetestowania funkcjonalności `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="6fc37-268">Napisz kod, aby ustawić i wyświetlić Właściwość `AlarmTime` `ctlAlarmClock`i przetestować jej funkcje.</span><span class="sxs-lookup"><span data-stu-id="6fc37-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="6fc37-269">Aby skompilować i dodać formant do formularza testowego</span><span class="sxs-lookup"><span data-stu-id="6fc37-269">To build and add your control to a test form</span></span>

1. <span data-ttu-id="6fc37-270">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlClockLib**, a następnie kliknij pozycję **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-270">In **Solution Explorer**, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="6fc37-271">Dodaj nowy projekt **aplikacji systemu Windows** do rozwiązania i nadaj mu nazwę **test**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-271">Add a new **Windows Application** project to the solution, and name it **Test**.</span></span>

3. <span data-ttu-id="6fc37-272">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="6fc37-272">In **Solution Explorer**, right-click the **References** node for your test project.</span></span> <span data-ttu-id="6fc37-273">Kliknij przycisk **Dodaj odwołanie** , aby wyświetlić okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="6fc37-273">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="6fc37-274">Kliknij kartę z etykietą **projekty**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-274">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="6fc37-275">Projekt `ctlClockLib` zostanie wyświetlony na liście **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-275">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="6fc37-276">Kliknij dwukrotnie projekt, aby dodać odwołanie do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="6fc37-276">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="6fc37-277">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **test**, a następnie kliknij polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-277">In **Solution Explorer**, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="6fc37-278">W **przyborniku**rozwiń węzeł **składniki ctlClockLib** .</span><span class="sxs-lookup"><span data-stu-id="6fc37-278">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="6fc37-279">Kliknij dwukrotnie pozycję **ctlAlarmClock** , aby dodać kopię `ctlAlarmClock` do formularza.</span><span class="sxs-lookup"><span data-stu-id="6fc37-279">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="6fc37-280">W **przyborniku**Znajdź i kliknij dwukrotnie pozycję **DateTimePicker** , aby dodać do formularza formant <xref:System.Windows.Forms.DateTimePicker>, a następnie Dodaj kontrolkę <xref:System.Windows.Forms.Label>, klikając dwukrotnie pozycję **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-280">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="6fc37-281">Użyj myszy, aby ustawić kontrolki w wygodnym miejscu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-281">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="6fc37-282">Ustaw właściwości tych kontrolek w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="6fc37-282">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="6fc37-283">formant</span><span class="sxs-lookup"><span data-stu-id="6fc37-283">Control</span></span>|<span data-ttu-id="6fc37-284">Właściwość</span><span class="sxs-lookup"><span data-stu-id="6fc37-284">Property</span></span>|<span data-ttu-id="6fc37-285">Wartość</span><span class="sxs-lookup"><span data-stu-id="6fc37-285">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="6fc37-286">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="6fc37-286">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="6fc37-287">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6fc37-287">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="6fc37-288">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6fc37-288">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="6fc37-289">**Formatowanie**</span><span class="sxs-lookup"><span data-stu-id="6fc37-289">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="6fc37-290">W projektancie kliknij dwukrotnie pozycję **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-290">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="6fc37-291">**Edytor kodu** zostanie otwarty w celu `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-291">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="6fc37-292">Zmodyfikuj kod w taki sposób, aby wyglądał następująco.</span><span class="sxs-lookup"><span data-stu-id="6fc37-292">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="6fc37-293">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **test**, a następnie kliknij pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-293">In **Solution Explorer**, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="6fc37-294">W menu **debugowanie** kliknij **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="6fc37-294">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="6fc37-295">Zostanie uruchomiony program testowy.</span><span class="sxs-lookup"><span data-stu-id="6fc37-295">The test program starts.</span></span> <span data-ttu-id="6fc37-296">Należy pamiętać, że bieżący czas jest aktualizowany w kontrolce `ctlAlarmClock` i że czas rozpoczęcia jest pokazywany w kontrolce <xref:System.Windows.Forms.DateTimePicker>.</span><span class="sxs-lookup"><span data-stu-id="6fc37-296">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="6fc37-297">Kliknij <xref:System.Windows.Forms.DateTimePicker>, w którym są wyświetlane minuty godziny.</span><span class="sxs-lookup"><span data-stu-id="6fc37-297">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="6fc37-298">Korzystając z klawiatury, ustaw wartość minut na minutę, która jest większa niż bieżąca godzina pokazana przez `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-298">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="6fc37-299">Czas ustawienia alarmu jest pokazywany w `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-299">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="6fc37-300">Poczekaj, aż wyświetlany czas osiągnie czas ustawienia alarmu.</span><span class="sxs-lookup"><span data-stu-id="6fc37-300">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="6fc37-301">Gdy wyświetlany czas osiągnie czas, w którym ustawiono alarm, `lblAlarm` zostanie błysk.</span><span class="sxs-lookup"><span data-stu-id="6fc37-301">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="6fc37-302">Wyłącz alarm, klikając `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="6fc37-302">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="6fc37-303">Teraz możesz zresetować alarm.</span><span class="sxs-lookup"><span data-stu-id="6fc37-303">You may now reset the alarm.</span></span>

<span data-ttu-id="6fc37-304">W tym artykule omówiono szereg kluczowych pojęć.</span><span class="sxs-lookup"><span data-stu-id="6fc37-304">This article has covered a number of key concepts.</span></span> <span data-ttu-id="6fc37-305">Wiesz już, jak utworzyć formant złożony przez połączenie formantów i składników do kontenera kontroli złożonej.</span><span class="sxs-lookup"><span data-stu-id="6fc37-305">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="6fc37-306">Wiesz już, jak dodać właściwości do kontrolki i napisać kod w celu zaimplementowania funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6fc37-306">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="6fc37-307">W ostatniej sekcji pokazano, jak zwiększyć funkcjonalność danego formantu złożonego przez dziedziczenie i zmienić funkcjonalność metod hosta, zastępując te metody.</span><span class="sxs-lookup"><span data-stu-id="6fc37-307">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fc37-308">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fc37-308">See also</span></span>

- [<span data-ttu-id="6fc37-309">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="6fc37-309">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="6fc37-310">Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="6fc37-310">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="6fc37-311">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="6fc37-311">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
