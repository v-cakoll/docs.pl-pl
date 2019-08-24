---
title: 'Przewodnik: tworzenie kontrolki złożonej za pomocą Visual C#'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d1af6c0e013f82569eed8d085df0249f4fb991bb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015681"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a><span data-ttu-id="fc772-102">Przewodnik: Tworzenie kontrolki złożonej przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="fc772-102">Walkthrough: Author a Composite Control with C\#</span></span>

<span data-ttu-id="fc772-103">Kontrolki złożone zapewniają metodę, za pomocą której można tworzyć i ponownie używać niestandardowych interfejsów graficznych.</span><span class="sxs-lookup"><span data-stu-id="fc772-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="fc772-104">Formant złożony jest zasadniczo składnikiem z reprezentacją wizualną.</span><span class="sxs-lookup"><span data-stu-id="fc772-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="fc772-105">W związku z tym może składać się z co najmniej jednego Windows Forms kontrolek, składników lub bloków kodu, który może zwiększyć funkcjonalność, sprawdzając dane wejściowe użytkownika, modyfikując właściwości wyświetlania lub wykonując inne zadania wymagane przez autora.</span><span class="sxs-lookup"><span data-stu-id="fc772-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="fc772-106">Kontrolki złożone mogą być umieszczane na Windows Forms w taki sam sposób jak w przypadku innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="fc772-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="fc772-107">W pierwszej części tego przewodnika utworzysz prostą kontrolkę złożoną o nazwie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="fc772-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="fc772-108">W drugiej części przewodnika rozszerzono funkcjonalność programu `ctlClock` przez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="fc772-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="fc772-109">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="fc772-109">Create the Project</span></span>

<span data-ttu-id="fc772-110">Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główną przestrzeń nazw, nazwę zestawu i nazwę projektu, i upewnić się, że składnik domyślny będzie w poprawnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fc772-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="fc772-111">Aby utworzyć bibliotekę kontrolek ctlClockLib i formant ctlClock</span><span class="sxs-lookup"><span data-stu-id="fc772-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="fc772-112">W programie Visual Studio Utwórz nowy projekt **biblioteki formantów Windows Forms** i nadaj mu nazwę **ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="fc772-112">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ctlClockLib**.</span></span>

     <span data-ttu-id="fc772-113">Nazwa projektu, `ctlClockLib`, również jest domyślnie przypisana do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fc772-113">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="fc772-114">Główna przestrzeń nazw służy do kwalifikowania nazw składników w zestawie.</span><span class="sxs-lookup"><span data-stu-id="fc772-114">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="fc772-115">Na przykład jeśli dwa zestawy dostarczają składniki o nazwie `ctlClock`, można `ctlClock` określić składnik przy użyciu`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="fc772-115">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

2. <span data-ttu-id="fc772-116">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **UserControl1.cs**, a następnie kliknij polecenie **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="fc772-116">In **Solution Explorer**, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="fc772-117">Zmień nazwę pliku na `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="fc772-117">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="fc772-118">Kliknij przycisk **tak** po wyświetleniu monitu, jeśli chcesz zmienić nazwy wszystkich odwołań do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="fc772-118">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc772-119">Domyślnie formant złożony dziedziczy z <xref:System.Windows.Forms.UserControl> klasy dostarczonej przez system.</span><span class="sxs-lookup"><span data-stu-id="fc772-119">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="fc772-120"><xref:System.Windows.Forms.UserControl> Klasa zawiera funkcje wymagane przez wszystkie kontrolki złożone i implementuje standardowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc772-120">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

3. <span data-ttu-id="fc772-121">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="fc772-121">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="fc772-122">Dodawanie formantów i składników systemu Windows do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="fc772-122">Add Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="fc772-123">Interfejs wizualny jest istotną częścią formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="fc772-123">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="fc772-124">Ten interfejs wizualny jest implementowany przez dodanie jednego lub większej liczby kontrolek systemu Windows do powierzchni projektanta.</span><span class="sxs-lookup"><span data-stu-id="fc772-124">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="fc772-125">Poniższa prezentacja zawiera kontrolki systemu Windows w kontrolce złożonej i pisanie kodu w celu zaimplementowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="fc772-125">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="fc772-126">Aby dodać etykietę i czasomierz do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="fc772-126">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="fc772-127">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlClock.cs**, a następnie kliknij pozycję **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="fc772-127">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="fc772-128">W **przyborniku**rozwiń węzeł **formanty wspólne** , a następnie kliknij dwukrotnie pozycję **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="fc772-128">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="fc772-129">Kontrolka o `label1` nazwie jest dodawana do kontrolki na powierzchni projektanta. <xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="fc772-129">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="fc772-130">W projektancie kliknij pozycję **Label1**.</span><span class="sxs-lookup"><span data-stu-id="fc772-130">In the designer, click **label1**.</span></span> <span data-ttu-id="fc772-131">W okno Właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc772-131">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="fc772-132">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fc772-132">Property</span></span>|<span data-ttu-id="fc772-133">Zmień na</span><span class="sxs-lookup"><span data-stu-id="fc772-133">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="fc772-134">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="fc772-134">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="fc772-135">**Text**</span><span class="sxs-lookup"><span data-stu-id="fc772-135">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="fc772-136">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="fc772-136">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="fc772-137">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="fc772-137">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="fc772-138">W **przyborniku**rozwiń węzeł **składniki** , a następnie kliknij dwukrotnie przycisk **czasomierz**.</span><span class="sxs-lookup"><span data-stu-id="fc772-138">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="fc772-139">Ponieważ element <xref:System.Windows.Forms.Timer> jest składnikiem, nie ma żadnej wizualizacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fc772-139">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="fc772-140">W związku z tym nie jest wyświetlany z kontrolkami na powierzchni projektanta, ale raczej w **projektancie składników** (zasobnik u dołu powierzchni projektanta).</span><span class="sxs-lookup"><span data-stu-id="fc772-140">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="fc772-141">W **projektancie składników**kliknij pozycję **Timer1**, <xref:System.Windows.Forms.Timer.Interval%2A> a następnie ustaw właściwość na `1000` wartość i <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość na `true`.</span><span class="sxs-lookup"><span data-stu-id="fc772-141">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="fc772-142">Właściwość kontroluje częstotliwość, z którą jest <xref:System.Windows.Forms.Timer> taktowanie składnika. <xref:System.Windows.Forms.Timer.Interval%2A></span><span class="sxs-lookup"><span data-stu-id="fc772-142">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="fc772-143">Każdy cykl `timer1` czasu uruchamia kod `timer1_Tick` w zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="fc772-143">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="fc772-144">Interwał reprezentuje liczbę milisekund między taktami.</span><span class="sxs-lookup"><span data-stu-id="fc772-144">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="fc772-145">W **projektancie składników**kliknij dwukrotnie pozycję **Timer1** , aby `timer1_Tick` przejść do zdarzenia. `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="fc772-145">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="fc772-146">Zmodyfikuj kod w taki sposób, aby wyglądał jak Poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="fc772-146">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="fc772-147">Upewnij się, że modyfikator dostępu został zmieniony `private` z `protected`na.</span><span class="sxs-lookup"><span data-stu-id="fc772-147">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="fc772-148">Ten kod spowoduje, że bieżący czas będzie pokazywany w `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="fc772-148">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="fc772-149">Ze względu na `timer1` to, że `1000`interwał został ustawiony na, to zdarzenie będzie wykonywane co tysiąc milisekund, co oznacza, że bieżący czas jest aktualizowany co sekundę.</span><span class="sxs-lookup"><span data-stu-id="fc772-149">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="fc772-150">Zmodyfikuj metodę, aby mogła zostać zastąpiona `virtual` słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="fc772-150">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="fc772-151">Aby uzyskać więcej informacji, zobacz sekcję "dziedziczenie z kontrolki użytkownika" poniżej.</span><span class="sxs-lookup"><span data-stu-id="fc772-151">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="fc772-152">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="fc772-152">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-properties-to-the-composite-control"></a><span data-ttu-id="fc772-153">Dodawanie właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="fc772-153">Add Properties to the Composite Control</span></span>

<span data-ttu-id="fc772-154">Kontrolka zegara hermetyzuje <xref:System.Windows.Forms.Label> obecnie formant <xref:System.Windows.Forms.Timer> i składnik, z których każdy ma własny zestaw właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc772-154">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="fc772-155">Chociaż poszczególne właściwości tych kontrolek nie będą dostępne dla kolejnych użytkowników kontrolki, można utworzyć i uwidocznić właściwości niestandardowe przez napisanie odpowiednich bloków kodu.</span><span class="sxs-lookup"><span data-stu-id="fc772-155">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="fc772-156">Poniższa procedura obejmuje dodanie do kontrolki właściwości, które umożliwiają użytkownikowi zmianę koloru tła i tekstu.</span><span class="sxs-lookup"><span data-stu-id="fc772-156">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="fc772-157">Aby dodać właściwość do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="fc772-157">To add a property to your composite control</span></span>

1. <span data-ttu-id="fc772-158">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlClock.cs**, a następnie kliknij pozycję **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="fc772-158">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="fc772-159">Zostanie otwarty **Edytor kodu** dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fc772-159">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="fc772-160">`public partial class ctlClock` Znajdź instrukcję.</span><span class="sxs-lookup"><span data-stu-id="fc772-160">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="fc772-161">Poniżej otwierającego nawiasu klamrowego (`{)`wpisz poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="fc772-161">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="fc772-162">Te instrukcje tworzą zmienne prywatne, które będą używane do przechowywania wartości właściwości, które mają zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="fc772-162">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="fc772-163">Wprowadź lub wklej następujący kod poniżej deklaracji zmiennych z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="fc772-163">Enter or paste the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="fc772-164">Poprzedni kod tworzy dwie właściwości `ClockForeColor` niestandardowe i `ClockBackColor`, dostępne dla kolejnych użytkowników tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fc772-164">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="fc772-165">Instrukcje `get` and`set` zapewniają przechowywanie i pobieranie wartości właściwości, a także kod służący do implementowania funkcji odpowiednich dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc772-165">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="fc772-166">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="fc772-166">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="fc772-167">Testowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="fc772-167">Test the Control</span></span>

<span data-ttu-id="fc772-168">Formanty nie są aplikacjami autonomicznymi; muszą być hostowane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="fc772-168">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="fc772-169">Przetestuj zachowanie w czasie wykonywania formantu i wykonuj jego właściwości za pomocą **kontenera testów UserControl**.</span><span class="sxs-lookup"><span data-stu-id="fc772-169">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="fc772-170">Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fc772-170">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="fc772-171">Aby przetestować kontrolkę</span><span class="sxs-lookup"><span data-stu-id="fc772-171">To test your control</span></span>

1. <span data-ttu-id="fc772-172">Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="fc772-172">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="fc772-173">W siatce właściwości kontenera testów Znajdź `ClockBackColor` właściwość, a następnie wybierz właściwość, aby wyświetlić paletę kolorów.</span><span class="sxs-lookup"><span data-stu-id="fc772-173">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="fc772-174">Wybierz kolor, klikając go.</span><span class="sxs-lookup"><span data-stu-id="fc772-174">Choose a color by clicking it.</span></span>

   <span data-ttu-id="fc772-175">Kolor tła kontrolki zmieni się na wybrany kolor.</span><span class="sxs-lookup"><span data-stu-id="fc772-175">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="fc772-176">Użyj podobnej sekwencji zdarzeń, aby sprawdzić, czy `ClockForeColor` Właściwość działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="fc772-176">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

   <span data-ttu-id="fc772-177">W tej sekcji i w powyższych sekcjach pokazano, jak można łączyć składniki i formanty systemu Windows z kodem i opakowaniem, aby zapewnić niestandardowe funkcje w formie złożonego formantu.</span><span class="sxs-lookup"><span data-stu-id="fc772-177">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="fc772-178">Wiesz już, jak uwidocznić właściwości w kontrolce złożonej oraz jak przetestować swój formant po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="fc772-178">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="fc772-179">W następnej sekcji dowiesz się, jak utworzyć Dziedziczony formant złożony, używając `ctlClock` jako podstawy.</span><span class="sxs-lookup"><span data-stu-id="fc772-179">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inherit-from-a-composite-control"></a><span data-ttu-id="fc772-180">Dziedzicz z kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="fc772-180">Inherit from a Composite Control</span></span>

<span data-ttu-id="fc772-181">W poprzednich sekcjach przedstawiono sposób łączenia formantów, składników i kodu systemu Windows z kontrolkami złożonymi do wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="fc772-181">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="fc772-182">Formant złożony może być teraz używany jako podstawa, na której można skompilować inne kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fc772-182">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="fc772-183">Proces wyprowadzania klasy z klasy bazowej nosi nazwę *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="fc772-183">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="fc772-184">W tej sekcji utworzysz formant złożony o nazwie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="fc772-184">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="fc772-185">Ten formant będzie pochodzący z jego formantu `ctlClock`nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fc772-185">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="fc772-186">Dowiesz się, jak zwiększyć funkcjonalność `ctlClock` przez zastępowanie metod nadrzędnych i dodawanie nowych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc772-186">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="fc772-187">Pierwszym krokiem tworzenia dziedziczonej kontrolki jest uzyskanie jej z elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="fc772-187">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="fc772-188">Ta akcja tworzy nową kontrolkę, która ma wszystkie właściwości, metody i charakterystyki graficzne kontrolki nadrzędnej, ale może również stanowić podstawę do dodania nowych lub zmodyfikowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="fc772-188">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="fc772-189">Aby utworzyć Dziedziczony formant</span><span class="sxs-lookup"><span data-stu-id="fc772-189">To create the inherited control</span></span>

1. <span data-ttu-id="fc772-190">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Kontrola użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="fc772-190">In **Solution Explorer**, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="fc772-191">**Dodaj nowy element** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="fc772-191">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="fc772-192">Wybierz szablon **dziedziczonej kontrolki użytkownika** .</span><span class="sxs-lookup"><span data-stu-id="fc772-192">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="fc772-193">W polu **Nazwa** wpisz `ctlAlarmClock.cs`, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="fc772-193">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="fc772-194">Zostanie wyświetlone okno dialogowe **Selektor dziedziczenia** .</span><span class="sxs-lookup"><span data-stu-id="fc772-194">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="fc772-195">W obszarze **Nazwa składnika**kliknij dwukrotnie pozycję **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="fc772-195">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="fc772-196">W **Eksplorator rozwiązań**Przeglądaj bieżące projekty.</span><span class="sxs-lookup"><span data-stu-id="fc772-196">In **Solution Explorer**, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc772-197">Plik o nazwie **ctlAlarmClock.cs** został dodany do bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="fc772-197">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="add-the-alarm-properties"></a><span data-ttu-id="fc772-198">Dodaj właściwości alarmu</span><span class="sxs-lookup"><span data-stu-id="fc772-198">Add the Alarm Properties</span></span>

<span data-ttu-id="fc772-199">Właściwości są dodawane do dziedziczonej kontrolki w taki sam sposób, w jaki są dodawane do kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="fc772-199">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="fc772-200">Teraz użyj składni deklaracji właściwości, aby dodać dwie właściwości do kontrolki: `AlarmTime`, w której będzie przechowywana wartość daty i godziny, w której ma się pojawić alarm, i `AlarmSet`wskazująca, czy alarm jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="fc772-200">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="fc772-201">Aby dodać właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="fc772-201">To add properties to your composite control</span></span>

1. <span data-ttu-id="fc772-202">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock**, a następnie kliknij pozycję **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="fc772-202">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="fc772-203">`public class` Znajdź instrukcję.</span><span class="sxs-lookup"><span data-stu-id="fc772-203">Locate the `public class` statement.</span></span> <span data-ttu-id="fc772-204">Zwróć uwagę, że kontrolka `ctlClockLib.ctlClock`dziedziczy z.</span><span class="sxs-lookup"><span data-stu-id="fc772-204">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="fc772-205">Poniżej otwierającego nawiasu klamrowego (`{)` instrukcja wpisz poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="fc772-205">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="add-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="fc772-206">Dodaj do interfejsu graficznego formantu</span><span class="sxs-lookup"><span data-stu-id="fc772-206">Add to the Graphical Interface of the Control</span></span>

<span data-ttu-id="fc772-207">Formant dziedziczony ma interfejs wizualny, który jest identyczny z kontrolką, z której dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="fc772-207">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="fc772-208">Posiada te same kontrolki elementów, jak jej kontrolki nadrzędne, ale właściwości kontrolek elementów nie będą dostępne, chyba że zostały one jawnie ujawnione.</span><span class="sxs-lookup"><span data-stu-id="fc772-208">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="fc772-209">Można dodać do interfejsu graficznego dziedziczonego formantu złożonego w taki sam sposób, jak w przypadku dowolnej kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="fc772-209">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="fc772-210">Aby kontynuować dodawanie do interfejsu wizualizacji zegara alarmu, należy dodać kontrolkę etykieta, która będzie Flash, gdy alarm jest dźwiękowy.</span><span class="sxs-lookup"><span data-stu-id="fc772-210">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="fc772-211">Aby dodać kontrolkę etykieta</span><span class="sxs-lookup"><span data-stu-id="fc772-211">To add the label control</span></span>

1. <span data-ttu-id="fc772-212">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock**, a następnie kliknij pozycję **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="fc772-212">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="fc772-213">Projektant do `ctlAlarmClock` otwarcia w oknie głównym.</span><span class="sxs-lookup"><span data-stu-id="fc772-213">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="fc772-214">Kliknij część ekranu kontrolki i Wyświetl okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc772-214">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc772-215">Wszystkie właściwości są wyświetlane, są wygaszone.</span><span class="sxs-lookup"><span data-stu-id="fc772-215">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="fc772-216">Oznacza to, że te właściwości są natywne `lblDisplay` i nie można ich modyfikować ani uzyskać do nich dostępu w okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc772-216">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="fc772-217">Domyślnie formanty zawarte w kontrolce złożonej są `private`, a ich właściwości nie są dostępne w żaden sposób.</span><span class="sxs-lookup"><span data-stu-id="fc772-217">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fc772-218">Jeśli chcesz, aby inni użytkownicy formantu złożonego mieli dostęp do jego wewnętrznych formantów, zadeklaruj je jako `public` lub `protected`.</span><span class="sxs-lookup"><span data-stu-id="fc772-218">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="fc772-219">Umożliwi to Ustawianie i modyfikowanie właściwości kontrolek zawartych w kontrolce złożonej przy użyciu odpowiedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="fc772-219">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="fc772-220"><xref:System.Windows.Forms.Label> Dodaj kontrolkę do kontrolki złożonej.</span><span class="sxs-lookup"><span data-stu-id="fc772-220">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="fc772-221">Za pomocą myszy przeciągnij <xref:System.Windows.Forms.Label> formant bezpośrednio poniżej pola wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="fc772-221">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="fc772-222">W okno Właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc772-222">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="fc772-223">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fc772-223">Property</span></span>|<span data-ttu-id="fc772-224">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="fc772-224">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="fc772-225">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="fc772-225">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="fc772-226">**Text**</span><span class="sxs-lookup"><span data-stu-id="fc772-226">**Text**</span></span>|<span data-ttu-id="fc772-227">**Uruchomienia!**</span><span class="sxs-lookup"><span data-stu-id="fc772-227">**Alarm!**</span></span>|
    |<span data-ttu-id="fc772-228">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="fc772-228">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="fc772-229">**Widać**</span><span class="sxs-lookup"><span data-stu-id="fc772-229">**Visible**</span></span>|`false`|

### <a name="add-the-alarm-functionality"></a><span data-ttu-id="fc772-230">Dodawanie funkcji alarmu</span><span class="sxs-lookup"><span data-stu-id="fc772-230">Add the Alarm Functionality</span></span>

<span data-ttu-id="fc772-231">W poprzednich procedurach dodano właściwości i kontrolkę, która spowoduje włączenie funkcji alarmu w formancie złożonym.</span><span class="sxs-lookup"><span data-stu-id="fc772-231">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="fc772-232">W ramach tej procedury dodasz kod w celu porównania bieżącego czasu z czasem alarmu i, jeśli są one takie same, do nabłysku alarmu.</span><span class="sxs-lookup"><span data-stu-id="fc772-232">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="fc772-233">Poprzez zastąpienie `timer1_Tick` `ctlAlarmClock` metody i dodanie do niej dodatkowego kodu, można zwiększyć możliwości programu, zachowując wszystkie nieodłączne funkcje programu `ctlClock`. `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="fc772-233">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="fc772-234">Aby zastąpić metodę timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="fc772-234">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="fc772-235">W **edytorze kodu**Znajdź `private bool blnAlarmSet;` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="fc772-235">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="fc772-236">Bezpośrednio poniżej, Dodaj następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="fc772-236">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="fc772-237">W **edytorze kodu**Znajdź zamykający nawias klamrowy (`})` na końcu klasy.</span><span class="sxs-lookup"><span data-stu-id="fc772-237">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="fc772-238">Tuż przed nawiasem klamrowym Dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="fc772-238">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="fc772-239">Dodanie tego kodu wykonuje kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="fc772-239">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="fc772-240">`override` Instrukcja kieruje formant do użycia tej metody zamiast metody, która była dziedziczona z kontrolki podstawowej.</span><span class="sxs-lookup"><span data-stu-id="fc772-240">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="fc772-241">Gdy ta metoda jest wywoływana, wywołuje metodę, która zastąpi przez wywoływanie `base.timer1_Tick` instrukcji, co zapewnia, że wszystkie funkcje wbudowane w pierwotnej kontrolce są odtwarzane w tym formancie.</span><span class="sxs-lookup"><span data-stu-id="fc772-241">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="fc772-242">Następnie uruchamia dodatkowy kod w celu uwzględnienia funkcji alarmu.</span><span class="sxs-lookup"><span data-stu-id="fc772-242">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="fc772-243">Migająca kontrolka etykieta zostanie wyświetlona, gdy wystąpi alarm.</span><span class="sxs-lookup"><span data-stu-id="fc772-243">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="fc772-244">Kontrola zegara alarmu jest niemal ukończona.</span><span class="sxs-lookup"><span data-stu-id="fc772-244">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="fc772-245">Jedyną czynnością, która pozostanie, jest zaimplementowanie sposobu jej wyłączenia.</span><span class="sxs-lookup"><span data-stu-id="fc772-245">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="fc772-246">W tym celu należy dodać kod do `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="fc772-246">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="fc772-247">Aby zaimplementować metodę ShutOff</span><span class="sxs-lookup"><span data-stu-id="fc772-247">To implement the shutoff method</span></span>

1. <span data-ttu-id="fc772-248">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlAlarmClock.cs**, a następnie kliknij pozycję **Projektant widoków**.</span><span class="sxs-lookup"><span data-stu-id="fc772-248">In **Solution Explorer**, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="fc772-249">Zostanie otwarty projektant.</span><span class="sxs-lookup"><span data-stu-id="fc772-249">The designer opens.</span></span>

2. <span data-ttu-id="fc772-250">Dodaj przycisk do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fc772-250">Add a button to the control.</span></span> <span data-ttu-id="fc772-251">Ustaw właściwości przycisku w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="fc772-251">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="fc772-252">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fc772-252">Property</span></span>|<span data-ttu-id="fc772-253">Wartość</span><span class="sxs-lookup"><span data-stu-id="fc772-253">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="fc772-254">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="fc772-254">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="fc772-255">**Text**</span><span class="sxs-lookup"><span data-stu-id="fc772-255">**Text**</span></span>|<span data-ttu-id="fc772-256">**Wyłącz alarm**</span><span class="sxs-lookup"><span data-stu-id="fc772-256">**Disable Alarm**</span></span>|

3. <span data-ttu-id="fc772-257">W projektancie kliknij dwukrotnie pozycję **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="fc772-257">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="fc772-258">**Edytor kodu** zostanie otwarty `private void btnAlarmOff_Click` w wierszu.</span><span class="sxs-lookup"><span data-stu-id="fc772-258">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="fc772-259">Zmodyfikuj tę metodę, tak aby była podobna do poniższego kodu.</span><span class="sxs-lookup"><span data-stu-id="fc772-259">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="fc772-260">W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="fc772-260">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="use-the-inherited-control-on-a-form"></a><span data-ttu-id="fc772-261">Używanie dziedziczonej kontrolki w formularzu</span><span class="sxs-lookup"><span data-stu-id="fc772-261">Use the Inherited Control on a Form</span></span>

<span data-ttu-id="fc772-262">Można testować Dziedziczony formant w taki sam sposób, `ctlClock`w jaki przetestowano formant klasy bazowej: Naciśnij klawisz **F5** , aby skompilować projekt i uruchomić formant w **kontenerze Test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="fc772-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="fc772-263">Aby uzyskać więcej informacji, zobacz [jak: Przetestuj zachowanie elementu UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fc772-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="fc772-264">Aby można było użyć formantu, musisz go hostować w formularzu.</span><span class="sxs-lookup"><span data-stu-id="fc772-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="fc772-265">Podobnie jak w przypadku standardowej kontroli złożonej, Dziedziczony formant złożony nie może być autonomiczny i musi być hostowany w formie lub w innym kontenerze.</span><span class="sxs-lookup"><span data-stu-id="fc772-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="fc772-266">Ponieważ `ctlAlarmClock` ma większą głębię funkcjonalności, wymagany jest dodatkowy kod do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="fc772-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="fc772-267">Ta procedura polega na napisaniu prostego programu w celu przetestowania funkcji programu `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="fc772-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="fc772-268">Napisz kod `AlarmTime` `ctlAlarmClock`, aby ustawić i wyświetlić właściwość, i przetestować jej funkcje.</span><span class="sxs-lookup"><span data-stu-id="fc772-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="fc772-269">Aby skompilować i dodać formant do formularza testowego</span><span class="sxs-lookup"><span data-stu-id="fc772-269">To build and add your control to a test form</span></span>

1. <span data-ttu-id="fc772-270">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ctlClockLib**, a następnie kliknij pozycję **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="fc772-270">In **Solution Explorer**, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="fc772-271">Dodaj nowy projekt **aplikacji systemu Windows** do rozwiązania i nadaj mu nazwę **test**.</span><span class="sxs-lookup"><span data-stu-id="fc772-271">Add a new **Windows Application** project to the solution, and name it **Test**.</span></span>

3. <span data-ttu-id="fc772-272">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="fc772-272">In **Solution Explorer**, right-click the **References** node for your test project.</span></span> <span data-ttu-id="fc772-273">Kliknij przycisk **Dodaj odwołanie** , aby wyświetlić okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="fc772-273">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="fc772-274">Kliknij kartę z etykietą **projekty**.</span><span class="sxs-lookup"><span data-stu-id="fc772-274">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="fc772-275">Projekt zostanie wyświetlony na liście **Nazwa projektu.** `ctlClockLib`</span><span class="sxs-lookup"><span data-stu-id="fc772-275">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="fc772-276">Kliknij dwukrotnie projekt, aby dodać odwołanie do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="fc772-276">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="fc772-277">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **test**, a następnie kliknij polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="fc772-277">In **Solution Explorer**, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="fc772-278">W **przyborniku**rozwiń węzeł **składniki ctlClockLib** .</span><span class="sxs-lookup"><span data-stu-id="fc772-278">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="fc772-279">Kliknij dwukrotnie pozycję **ctlAlarmClock** , aby dodać kopię `ctlAlarmClock` do formularza.</span><span class="sxs-lookup"><span data-stu-id="fc772-279">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="fc772-280">W **przyborniku**Znajdź i kliknij dwukrotnie pozycję **DateTimePicker** , <xref:System.Windows.Forms.DateTimePicker> aby dodać kontrolkę do <xref:System.Windows.Forms.Label> formularza, a następnie Dodaj kontrolkę, klikając dwukrotnie pozycję **etykieta**.</span><span class="sxs-lookup"><span data-stu-id="fc772-280">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="fc772-281">Użyj myszy, aby ustawić kontrolki w wygodnym miejscu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="fc772-281">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="fc772-282">Ustaw właściwości tych kontrolek w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="fc772-282">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="fc772-283">formant</span><span class="sxs-lookup"><span data-stu-id="fc772-283">Control</span></span>|<span data-ttu-id="fc772-284">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fc772-284">Property</span></span>|<span data-ttu-id="fc772-285">Wartość</span><span class="sxs-lookup"><span data-stu-id="fc772-285">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="fc772-286">**Text**</span><span class="sxs-lookup"><span data-stu-id="fc772-286">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="fc772-287">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="fc772-287">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="fc772-288">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="fc772-288">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="fc772-289">**Formatowanie**</span><span class="sxs-lookup"><span data-stu-id="fc772-289">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="fc772-290">W projektancie kliknij dwukrotnie pozycję **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="fc772-290">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="fc772-291">Zostanie otwarty `private void dtpTest_ValueChanged` **Edytor kodu** .</span><span class="sxs-lookup"><span data-stu-id="fc772-291">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="fc772-292">Zmodyfikuj kod w taki sposób, aby wyglądał następująco.</span><span class="sxs-lookup"><span data-stu-id="fc772-292">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="fc772-293">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **test**, a następnie kliknij pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="fc772-293">In **Solution Explorer**, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="fc772-294">Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="fc772-294">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="fc772-295">Zostanie uruchomiony program testowy.</span><span class="sxs-lookup"><span data-stu-id="fc772-295">The test program starts.</span></span> <span data-ttu-id="fc772-296">Należy pamiętać, że bieżący czas jest aktualizowany w `ctlAlarmClock` kontrolce, a czas rozpoczęcia jest pokazywany <xref:System.Windows.Forms.DateTimePicker> w formancie.</span><span class="sxs-lookup"><span data-stu-id="fc772-296">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="fc772-297"><xref:System.Windows.Forms.DateTimePicker> Kliknij miejsce, gdzie są wyświetlane minuty godziny.</span><span class="sxs-lookup"><span data-stu-id="fc772-297">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="fc772-298">Korzystając z klawiatury, ustaw wartość minut na minutę, która jest większa niż bieżąca godzina pokazana przez `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="fc772-298">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="fc772-299">Godzina ustawienia alarmu jest pokazywana w `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="fc772-299">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="fc772-300">Poczekaj, aż wyświetlany czas osiągnie czas ustawienia alarmu.</span><span class="sxs-lookup"><span data-stu-id="fc772-300">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="fc772-301">Gdy wyświetlany czas osiągnie czas, w którym ustawiono alarm, zostanie wyświetlona `lblAlarm` wartość błysk.</span><span class="sxs-lookup"><span data-stu-id="fc772-301">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="fc772-302">Wyłącz alarm, klikając pozycję `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="fc772-302">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="fc772-303">Teraz możesz zresetować alarm.</span><span class="sxs-lookup"><span data-stu-id="fc772-303">You may now reset the alarm.</span></span>

<span data-ttu-id="fc772-304">W tym artykule omówiono szereg kluczowych pojęć.</span><span class="sxs-lookup"><span data-stu-id="fc772-304">This article has covered a number of key concepts.</span></span> <span data-ttu-id="fc772-305">Wiesz już, jak utworzyć formant złożony przez połączenie formantów i składników do kontenera kontroli złożonej.</span><span class="sxs-lookup"><span data-stu-id="fc772-305">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="fc772-306">Wiesz już, jak dodać właściwości do kontrolki i napisać kod w celu zaimplementowania funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fc772-306">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="fc772-307">W ostatniej sekcji pokazano, jak zwiększyć funkcjonalność danego formantu złożonego przez dziedziczenie i zmienić funkcjonalność metod hosta, zastępując te metody.</span><span class="sxs-lookup"><span data-stu-id="fc772-307">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc772-308">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc772-308">See also</span></span>

- [<span data-ttu-id="fc772-309">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="fc772-309">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="fc772-310">Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="fc772-310">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="fc772-311">Przewodnik: Dziedziczenie z kontrolki Windows Forms za pomocą wizualizacjiC#</span><span class="sxs-lookup"><span data-stu-id="fc772-311">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
