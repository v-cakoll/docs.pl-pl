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
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546727"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a><span data-ttu-id="a8142-102">Instruktaż: Autor kontrolki złożonej z C\#</span><span class="sxs-lookup"><span data-stu-id="a8142-102">Walkthrough: Author a Composite Control with C\#</span></span>

<span data-ttu-id="a8142-103">Formanty kompozytowe zapewniają sposób, za pomocą którego można tworzyć i ponownie konfigurować niestandardowe interfejsy graficzne.</span><span class="sxs-lookup"><span data-stu-id="a8142-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="a8142-104">Formant złożony jest zasadniczo komponentem z wizualną reprezentacją.</span><span class="sxs-lookup"><span data-stu-id="a8142-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="a8142-105">W związku z tym może składać się z jednego lub więcej formantów, składników lub bloków kodu Windows Forms, które mogą rozszerzać funkcjonalność, sprawdzając poprawność danych wejściowych użytkownika, modyfikując właściwości wyświetlania lub wykonując inne zadania wymagane przez autora.</span><span class="sxs-lookup"><span data-stu-id="a8142-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="a8142-106">Formantów złożonych mogą być umieszczane w formularzach systemu Windows w taki sam sposób jak inne formanty.</span><span class="sxs-lookup"><span data-stu-id="a8142-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="a8142-107">W pierwszej części tego przewodnika można utworzyć prosty formant złożony o nazwie `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="a8142-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="a8142-108">W drugiej części przewodnika można rozszerzyć funkcjonalność poprzez `ctlClock` dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="a8142-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="a8142-109">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="a8142-109">Create the Project</span></span>

<span data-ttu-id="a8142-110">Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główny obszar nazw, nazwę zestawu i nazwę projektu oraz upewnić się, że domyślny składnik będzie w poprawnym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="a8142-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="a8142-111">Aby utworzyć bibliotekę kontrolną ctlClockLib i kontrolka ctlClock</span><span class="sxs-lookup"><span data-stu-id="a8142-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="a8142-112">W programie Visual Studio utwórz nowy projekt **biblioteki kontroli formularzy systemu Windows** i nadaj jej nazwę **ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="a8142-112">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ctlClockLib**.</span></span>

     <span data-ttu-id="a8142-113">Nazwa `ctlClockLib`projektu jest również domyślnie przypisana do głównego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="a8142-113">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="a8142-114">Główny obszar nazw jest używany do kwalifikowaniu nazw komponentów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="a8142-114">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="a8142-115">Na przykład, jeśli dwa złoża zawierają komponenty o nazwie `ctlClock`, można określić `ctlClock` komponent za pomocą`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="a8142-115">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

2. <span data-ttu-id="a8142-116">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **UserControl1.cs**, a następnie kliknij polecenie **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="a8142-116">In **Solution Explorer**, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="a8142-117">Zmień nazwę pliku `ctlClock.cs`na .</span><span class="sxs-lookup"><span data-stu-id="a8142-117">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="a8142-118">Kliknij przycisk **Tak,** gdy pojawi się pytanie, czy chcesz zmienić nazwę wszystkich odwołań do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="a8142-118">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="a8142-119">Domyślnie formant złożony dziedziczy <xref:System.Windows.Forms.UserControl> z klasy dostarczonej przez system.</span><span class="sxs-lookup"><span data-stu-id="a8142-119">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="a8142-120">Klasa <xref:System.Windows.Forms.UserControl> zapewnia funkcje wymagane przez wszystkie formanty złożone i implementuje standardowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8142-120">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

3. <span data-ttu-id="a8142-121">W menu **Plik** kliknij polecenie **Zapisz wszystko,** aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="a8142-121">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="a8142-122">Dodawanie formantów i składników systemu Windows do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="a8142-122">Add Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="a8142-123">Interfejs wizualny jest istotną częścią kontroli złożonej.</span><span class="sxs-lookup"><span data-stu-id="a8142-123">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="a8142-124">Ten interfejs wizualny jest implementowany przez dodanie jednego lub więcej formantów systemu Windows do powierzchni projektanta.</span><span class="sxs-lookup"><span data-stu-id="a8142-124">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="a8142-125">W poniższej demonstracji zostaną uwzględnione formanty systemu Windows do kontroli złożonej i napisać kod do zaimplementowania funkcji.</span><span class="sxs-lookup"><span data-stu-id="a8142-125">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="a8142-126">Aby dodać etykietę i timer do formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="a8142-126">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="a8142-127">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij polecenie **Projektant widoku**.</span><span class="sxs-lookup"><span data-stu-id="a8142-127">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="a8142-128">W **przyborniku**rozwiń węzeł **Typowe formanty,** a następnie kliknij dwukrotnie pozycję **Etykieta**.</span><span class="sxs-lookup"><span data-stu-id="a8142-128">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="a8142-129">Formant <xref:System.Windows.Forms.Label> `label1` o nazwie jest dodawany do formantu na powierzchni projektanta.</span><span class="sxs-lookup"><span data-stu-id="a8142-129">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="a8142-130">W projektancie kliknij pozycję **label1**.</span><span class="sxs-lookup"><span data-stu-id="a8142-130">In the designer, click **label1**.</span></span> <span data-ttu-id="a8142-131">W oknie Właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8142-131">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="a8142-132">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a8142-132">Property</span></span>|<span data-ttu-id="a8142-133">Zmień na</span><span class="sxs-lookup"><span data-stu-id="a8142-133">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="a8142-134">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="a8142-134">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="a8142-135">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="a8142-135">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="a8142-136">**Textalign**</span><span class="sxs-lookup"><span data-stu-id="a8142-136">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="a8142-137">**Czcionka.Rozmiar**</span><span class="sxs-lookup"><span data-stu-id="a8142-137">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="a8142-138">W **przyborniku**rozwiń węzeł **Składniki,** a następnie kliknij dwukrotnie pozycję **Timer**.</span><span class="sxs-lookup"><span data-stu-id="a8142-138">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="a8142-139">Ponieważ <xref:System.Windows.Forms.Timer> a jest składnikiem, nie ma wizualnej reprezentacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a8142-139">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="a8142-140">W związku z tym nie pojawia się z formantami na powierzchni **projektanta,** ale raczej w Projektancie składników (zasobnik u dołu powierzchni projektanta).</span><span class="sxs-lookup"><span data-stu-id="a8142-140">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="a8142-141">W **Projektancie składników**kliknij przycisk **Timer1**, `1000` a <xref:System.Windows.Forms.Timer.Enabled%2A> następnie `true`ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwość na i właściwość na .</span><span class="sxs-lookup"><span data-stu-id="a8142-141">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="a8142-142">Właściwość <xref:System.Windows.Forms.Timer.Interval%2A> kontroluje częstotliwość, <xref:System.Windows.Forms.Timer> z jaką składnik tyka.</span><span class="sxs-lookup"><span data-stu-id="a8142-142">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="a8142-143">Za `timer1` każdym razem zaznacza, uruchamia `timer1_Tick` kod w przypadku.</span><span class="sxs-lookup"><span data-stu-id="a8142-143">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="a8142-144">Interwał reprezentuje liczbę milisekund między znacznikami.</span><span class="sxs-lookup"><span data-stu-id="a8142-144">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="a8142-145">W **Projektancie składników**kliknij dwukrotnie **timer1,** aby przejść do `timer1_Tick` zdarzenia dla `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="a8142-145">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="a8142-146">Zmodyfikuj kod tak, aby przypominał poniższy przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="a8142-146">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="a8142-147">Pamiętaj, aby zmienić modyfikator dostępu z `private` na `protected`.</span><span class="sxs-lookup"><span data-stu-id="a8142-147">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="a8142-148">Ten kod spowoduje, że bieżący `lblDisplay`czas będzie wyświetlany w .</span><span class="sxs-lookup"><span data-stu-id="a8142-148">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="a8142-149">Ponieważ interwał `timer1` został `1000`ustawiony na , to zdarzenie będzie występować co tysiąc milisekund, aktualizując w ten sposób bieżący czas co sekundę.</span><span class="sxs-lookup"><span data-stu-id="a8142-149">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="a8142-150">Zmodyfikuj metodę, `virtual` która ma być zastąpiona słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="a8142-150">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="a8142-151">Aby uzyskać więcej informacji, zobacz sekcję "Dziedziczenie z kontroli użytkownika" poniżej.</span><span class="sxs-lookup"><span data-stu-id="a8142-151">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="a8142-152">W menu **Plik** kliknij polecenie **Zapisz wszystko,** aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="a8142-152">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-properties-to-the-composite-control"></a><span data-ttu-id="a8142-153">Dodawanie właściwości do kontrolki złożonej</span><span class="sxs-lookup"><span data-stu-id="a8142-153">Add Properties to the Composite Control</span></span>

<span data-ttu-id="a8142-154">Kontrola zegara teraz hermetyzuje <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Timer> formant i składnik, każdy z własnym zestawem właściwości nieodłączne.</span><span class="sxs-lookup"><span data-stu-id="a8142-154">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="a8142-155">Podczas gdy poszczególne właściwości tych formantów nie będą dostępne dla kolejnych użytkowników formantu, można utworzyć i udostępnić właściwości niestandardowe, zapisując odpowiednie bloki kodu.</span><span class="sxs-lookup"><span data-stu-id="a8142-155">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="a8142-156">W poniższej procedurze dodasz do formantu właściwości, które umożliwiają użytkownikowi zmianę koloru tła i tekstu.</span><span class="sxs-lookup"><span data-stu-id="a8142-156">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="a8142-157">Aby dodać właściwość do formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="a8142-157">To add a property to your composite control</span></span>

1. <span data-ttu-id="a8142-158">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlClock.cs**, a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="a8142-158">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="a8142-159">Zostanie otwarty **Edytor kodu** formantu.</span><span class="sxs-lookup"><span data-stu-id="a8142-159">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="a8142-160">Znajdź `public partial class ctlClock` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="a8142-160">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="a8142-161">Pod nawiasem klamrowym`{)`otwierającym ( wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="a8142-161">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="a8142-162">Te instrukcje tworzą zmienne prywatne, które będą używane do przechowywania wartości właściwości, które mają być utworzone.</span><span class="sxs-lookup"><span data-stu-id="a8142-162">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="a8142-163">Wprowadź lub wklej następujący kod pod deklaracjami zmiennych z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="a8142-163">Enter or paste the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="a8142-164">Powyższy kod sprawia, `ClockForeColor` że dwie `ClockBackColor`właściwości niestandardowe i , dostępne dla kolejnych użytkowników tego formantu.</span><span class="sxs-lookup"><span data-stu-id="a8142-164">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="a8142-165">`get` Instrukcje `set` i zapewniają przechowywanie i pobieranie wartości właściwości, a także kod do zaimplementowania funkcji odpowiednich dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8142-165">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="a8142-166">W menu **Plik** kliknij polecenie **Zapisz wszystko,** aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="a8142-166">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="a8142-167">Przetestuj formant</span><span class="sxs-lookup"><span data-stu-id="a8142-167">Test the Control</span></span>

<span data-ttu-id="a8142-168">Formanty nie są aplikacjami autonomicznymi; muszą być hostowane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="a8142-168">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="a8142-169">Przetestuj zachowanie w czasie wykonywania formantu i wykonuj jego właściwości za pomocą **kontenera testowego UserControl.**</span><span class="sxs-lookup"><span data-stu-id="a8142-169">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="a8142-170">Aby uzyskać więcej informacji, zobacz [Jak: Testowanie zachowania w czasie wykonywania usercontrol](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="a8142-170">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="a8142-171">Aby przetestować kontrolę</span><span class="sxs-lookup"><span data-stu-id="a8142-171">To test your control</span></span>

1. <span data-ttu-id="a8142-172">Naciśnij **klawisz F5,** aby utworzyć projekt i uruchomić formant w **kontenerze testowym UserControl**.</span><span class="sxs-lookup"><span data-stu-id="a8142-172">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="a8142-173">W siatce właściwości kontenera `ClockBackColor` testowego zlokalizuj właściwość, a następnie wybierz właściwość, aby wyświetlić paletę kolorów.</span><span class="sxs-lookup"><span data-stu-id="a8142-173">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="a8142-174">Wybierz kolor, klikając go.</span><span class="sxs-lookup"><span data-stu-id="a8142-174">Choose a color by clicking it.</span></span>

   <span data-ttu-id="a8142-175">Kolor tła formantu zmieni się na wybrany kolor.</span><span class="sxs-lookup"><span data-stu-id="a8142-175">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="a8142-176">Użyj podobnej sekwencji zdarzeń, `ClockForeColor` aby sprawdzić, czy właściwość działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="a8142-176">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

   <span data-ttu-id="a8142-177">W tej sekcji i poprzednich sekcjach można zobaczyć, jak składniki i formanty systemu Windows mogą być łączone z kodem i opakowaniem, aby zapewnić niestandardowe funkcje w postaci formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="a8142-177">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="a8142-178">Nauczysz się uwidaczniać właściwości w formancie złożonym i jak przetestować formant po jego zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="a8142-178">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="a8142-179">W następnej sekcji dowiesz się, jak skonstruować formant złożony dziedziczone przy użyciu `ctlClock` jako podstawy.</span><span class="sxs-lookup"><span data-stu-id="a8142-179">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inherit-from-a-composite-control"></a><span data-ttu-id="a8142-180">Dziedzicz po formancie złożonym</span><span class="sxs-lookup"><span data-stu-id="a8142-180">Inherit from a Composite Control</span></span>

<span data-ttu-id="a8142-181">W poprzednich sekcjach opisano, jak łączyć formanty systemu Windows, składniki i kod w formantów złożonych wielokrotnegoużytnia.</span><span class="sxs-lookup"><span data-stu-id="a8142-181">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="a8142-182">Formant złożony może być teraz używany jako podstawa, na której można zbudować inne formanty.</span><span class="sxs-lookup"><span data-stu-id="a8142-182">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="a8142-183">Proces wyprowadzania klasy z klasy podstawowej jest nazywany *dziedziczeniem*.</span><span class="sxs-lookup"><span data-stu-id="a8142-183">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="a8142-184">W tej sekcji utworzysz formant złożony o nazwie `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="a8142-184">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="a8142-185">Ta kontrolka będzie pochodzić `ctlClock`z jego kontroli nadrzędnej, .</span><span class="sxs-lookup"><span data-stu-id="a8142-185">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="a8142-186">Nauczysz się rozszerzać `ctlClock` funkcjonalność, zastępując metody nadrzędne i dodając nowe metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8142-186">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="a8142-187">Pierwszym krokiem w tworzeniu formantu dziedziczonego jest wyprowadzenie go z jego nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a8142-187">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="a8142-188">Ta akcja tworzy nowy formant, który ma wszystkie właściwości, metody i graficzne właściwości formantu nadrzędnego, ale może również działać jako podstawa do dodawania nowych lub zmodyfikowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a8142-188">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="a8142-189">Aby utworzyć formant dziedziczony</span><span class="sxs-lookup"><span data-stu-id="a8142-189">To create the inherited control</span></span>

1. <span data-ttu-id="a8142-190">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **polecenie ctlClockLib**, wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Kontrola użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="a8142-190">In **Solution Explorer**, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="a8142-191">Zostanie otwarte okno dialogowe **Dodawanie nowego elementu.**</span><span class="sxs-lookup"><span data-stu-id="a8142-191">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="a8142-192">Wybierz szablon **Formant dziedziczonego użytkownika.**</span><span class="sxs-lookup"><span data-stu-id="a8142-192">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="a8142-193">W polu **Nazwa** `ctlAlarmClock.cs`wpisz , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="a8142-193">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="a8142-194">Zostanie wyświetlone okno dialogowe **Selektor dziedziczenia.**</span><span class="sxs-lookup"><span data-stu-id="a8142-194">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="a8142-195">W obszarze **Nazwa składnika**kliknij dwukrotnie **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="a8142-195">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="a8142-196">W **Eksploratorze rozwiązań**przeglądaj bieżące projekty.</span><span class="sxs-lookup"><span data-stu-id="a8142-196">In **Solution Explorer**, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a8142-197">Plik o nazwie **ctlAlarmClock.cs** został dodany do bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="a8142-197">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="add-the-alarm-properties"></a><span data-ttu-id="a8142-198">Dodawanie właściwości alarmu</span><span class="sxs-lookup"><span data-stu-id="a8142-198">Add the Alarm Properties</span></span>

<span data-ttu-id="a8142-199">Właściwości są dodawane do formantu dziedziczonego w taki sam sposób, w jaki są dodawane do formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="a8142-199">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="a8142-200">Teraz użyjesz składni deklaracji właściwości, aby dodać dwie `AlarmTime`właściwości do formantu: , która będzie przechowywać `AlarmSet`wartość daty i godziny alarmu, która ma zniknąć, oraz , która wskaże, czy alarm jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="a8142-200">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="a8142-201">Aby dodać właściwości do formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="a8142-201">To add properties to your composite control</span></span>

1. <span data-ttu-id="a8142-202">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="a8142-202">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="a8142-203">Znajdź `public class` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="a8142-203">Locate the `public class` statement.</span></span> <span data-ttu-id="a8142-204">Należy pamiętać, że `ctlClockLib.ctlClock`formant dziedziczy z .</span><span class="sxs-lookup"><span data-stu-id="a8142-204">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="a8142-205">Pod nawiasem klamrowym`{)` otwarcia ( instrukcja wpisz następujący kod.</span><span class="sxs-lookup"><span data-stu-id="a8142-205">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="add-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="a8142-206">Dodaj do interfejsu graficznego formantu</span><span class="sxs-lookup"><span data-stu-id="a8142-206">Add to the Graphical Interface of the Control</span></span>

<span data-ttu-id="a8142-207">Formant dziedziczony ma interfejs wizualny, który jest identyczny z formantu dziedziczy z.</span><span class="sxs-lookup"><span data-stu-id="a8142-207">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="a8142-208">Posiada te same kontrole składników, co jego formant nadrzędny, ale właściwości formantów składowych nie będą dostępne, chyba że zostały one wyraźnie ujawnione.</span><span class="sxs-lookup"><span data-stu-id="a8142-208">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="a8142-209">Można dodać do interfejsu graficznego dziedziczonego formantu złożonego w taki sam sposób, jak można dodać do dowolnego formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="a8142-209">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="a8142-210">Aby kontynuować dodawanie do interfejsu wizualnego budzika, dodasz kontrolkę etykiety, która będzie migać, gdy alarm będzie brzmiał.</span><span class="sxs-lookup"><span data-stu-id="a8142-210">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="a8142-211">Aby dodać kontrolka etykiety</span><span class="sxs-lookup"><span data-stu-id="a8142-211">To add the label control</span></span>

1. <span data-ttu-id="a8142-212">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlAlarmClock**, a następnie kliknij polecenie **Wyświetl projektanta**.</span><span class="sxs-lookup"><span data-stu-id="a8142-212">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="a8142-213">Projektant otwiera `ctlAlarmClock` się w oknie głównym.</span><span class="sxs-lookup"><span data-stu-id="a8142-213">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="a8142-214">Kliknij część wyświetlania formantu i wyświetl okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8142-214">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a8142-215">Podczas gdy wszystkie właściwości są wyświetlane, są one wyszarzone.</span><span class="sxs-lookup"><span data-stu-id="a8142-215">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="a8142-216">Oznacza to, że te właściwości `lblDisplay` są natywne i nie mogą być modyfikowane lub dostępne w oknie Właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8142-216">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="a8142-217">Domyślnie formanty zawarte w `private`formancie złożonym są , a ich właściwości nie są dostępne w żaden sposób.</span><span class="sxs-lookup"><span data-stu-id="a8142-217">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a8142-218">Jeśli chcesz, aby kolejni użytkownicy formantu złożonego `public` mieli `protected`dostęp do kontroli wewnętrznej, zadeklaruj ich jako .</span><span class="sxs-lookup"><span data-stu-id="a8142-218">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="a8142-219">Umożliwi to ustawienie i zmodyfikowanie właściwości formantów zawartych w formancie złożonym przy użyciu odpowiedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="a8142-219">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="a8142-220">Dodaj <xref:System.Windows.Forms.Label> formant do formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="a8142-220">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="a8142-221">Za pomocą myszy <xref:System.Windows.Forms.Label> przeciągnij kontrolkę bezpośrednio pod polem wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="a8142-221">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="a8142-222">W oknie Właściwości ustaw następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8142-222">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="a8142-223">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a8142-223">Property</span></span>|<span data-ttu-id="a8142-224">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="a8142-224">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="a8142-225">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="a8142-225">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="a8142-226">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="a8142-226">**Text**</span></span>|<span data-ttu-id="a8142-227">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="a8142-227">**Alarm!**</span></span>|
    |<span data-ttu-id="a8142-228">**Textalign**</span><span class="sxs-lookup"><span data-stu-id="a8142-228">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="a8142-229">**Widoczne**</span><span class="sxs-lookup"><span data-stu-id="a8142-229">**Visible**</span></span>|`false`|

### <a name="add-the-alarm-functionality"></a><span data-ttu-id="a8142-230">Dodawanie funkcji alarmu</span><span class="sxs-lookup"><span data-stu-id="a8142-230">Add the Alarm Functionality</span></span>

<span data-ttu-id="a8142-231">W poprzednich procedurach dodano właściwości i formant, który włączy funkcje alarmu w formancie złożonym.</span><span class="sxs-lookup"><span data-stu-id="a8142-231">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="a8142-232">W tej procedurze dodasz kod, aby porównać bieżący czas z czasem alarmu i, jeśli są one takie same, aby migać alarm.</span><span class="sxs-lookup"><span data-stu-id="a8142-232">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="a8142-233">Poprzez `timer1_Tick` zastąpienie metody `ctlClock` i dodanie dodatkowego kodu do niego, można `ctlAlarmClock` rozszerzyć możliwości przy zachowaniu `ctlClock`wszystkich nieodłącznych funkcji .</span><span class="sxs-lookup"><span data-stu-id="a8142-233">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="a8142-234">Aby zastąpić timer1_Tick metodę ctlClock</span><span class="sxs-lookup"><span data-stu-id="a8142-234">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="a8142-235">W **Edytorze kodu** `private bool blnAlarmSet;` znajdź instrukcję.</span><span class="sxs-lookup"><span data-stu-id="a8142-235">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="a8142-236">Natychmiast pod nim dodaj następującą instrukcję.</span><span class="sxs-lookup"><span data-stu-id="a8142-236">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="a8142-237">W **Edytorze kodu**znajdź nawias`})` zamykający ( na końcu klasy.</span><span class="sxs-lookup"><span data-stu-id="a8142-237">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="a8142-238">Tuż przed nawiasem klamrowym dodaj następujący kod.</span><span class="sxs-lookup"><span data-stu-id="a8142-238">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="a8142-239">Dodanie tego kodu wykonuje kilka zadań.</span><span class="sxs-lookup"><span data-stu-id="a8142-239">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="a8142-240">Instrukcja `override` kieruje formantu do korzystania z tej metody zamiast metody, która została odziedziczona z formantu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a8142-240">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="a8142-241">Gdy ta metoda jest wywoływana, wywołuje metodę, którą `base.timer1_Tick` zastępuje, wywołując instrukcję, zapewniając, że wszystkie funkcje włączone w oryginalnym formancie jest powielana w tym formancie.</span><span class="sxs-lookup"><span data-stu-id="a8142-241">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="a8142-242">Następnie uruchamia dodatkowy kod, aby włączyć funkcję alarmu.</span><span class="sxs-lookup"><span data-stu-id="a8142-242">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="a8142-243">Po wystąpieniu alarmu pojawi się migająca kontrolka etykiety.</span><span class="sxs-lookup"><span data-stu-id="a8142-243">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="a8142-244">Sterowanie budzikiem jest prawie kompletne.</span><span class="sxs-lookup"><span data-stu-id="a8142-244">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="a8142-245">Pozostaje tylko wdrożyć sposób, aby go wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="a8142-245">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="a8142-246">Aby to zrobić, należy dodać `lblAlarm_Click` kod do metody.</span><span class="sxs-lookup"><span data-stu-id="a8142-246">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="a8142-247">Aby zaimplementować metodę wyłączania</span><span class="sxs-lookup"><span data-stu-id="a8142-247">To implement the shutoff method</span></span>

1. <span data-ttu-id="a8142-248">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlAlarmClock.cs**, a następnie kliknij polecenie **Widok Projektanta**.</span><span class="sxs-lookup"><span data-stu-id="a8142-248">In **Solution Explorer**, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="a8142-249">Projektant otwiera.</span><span class="sxs-lookup"><span data-stu-id="a8142-249">The designer opens.</span></span>

2. <span data-ttu-id="a8142-250">Dodaj przycisk do formantu.</span><span class="sxs-lookup"><span data-stu-id="a8142-250">Add a button to the control.</span></span> <span data-ttu-id="a8142-251">Ustaw właściwości przycisku w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a8142-251">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="a8142-252">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a8142-252">Property</span></span>|<span data-ttu-id="a8142-253">Wartość</span><span class="sxs-lookup"><span data-stu-id="a8142-253">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="a8142-254">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="a8142-254">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="a8142-255">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="a8142-255">**Text**</span></span>|<span data-ttu-id="a8142-256">**Wyłącz alarm**</span><span class="sxs-lookup"><span data-stu-id="a8142-256">**Disable Alarm**</span></span>|

3. <span data-ttu-id="a8142-257">W projektancie kliknij dwukrotnie **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="a8142-257">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="a8142-258">**Edytor kodu** zostanie `private void btnAlarmOff_Click` otwarty do wiersza.</span><span class="sxs-lookup"><span data-stu-id="a8142-258">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="a8142-259">Zmodyfikuj tę metodę, tak aby przypominała następujący kod.</span><span class="sxs-lookup"><span data-stu-id="a8142-259">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="a8142-260">W menu **Plik** kliknij polecenie **Zapisz wszystko,** aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="a8142-260">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="use-the-inherited-control-on-a-form"></a><span data-ttu-id="a8142-261">Używanie formantu dziedziczonego w formularzu</span><span class="sxs-lookup"><span data-stu-id="a8142-261">Use the Inherited Control on a Form</span></span>

<span data-ttu-id="a8142-262">Odziedziczonego formantu można przetestować w taki sam `ctlClock`sposób, w jaki testowano kontrolę klasy podstawowej: Naciśnij **klawisz F5,** aby utworzyć projekt i uruchomić formant w **kontenerze testowym UserControl**.</span><span class="sxs-lookup"><span data-stu-id="a8142-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="a8142-263">Aby uzyskać więcej informacji, zobacz [Jak: Testowanie zachowania w czasie wykonywania usercontrol](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="a8142-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="a8142-264">Aby użyć formantu, musisz go hostować w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a8142-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="a8142-265">Podobnie jak w przypadku standardowego formantu złożonego, dziedziczona formant złożony nie może być autonomiczna i musi być hostowana w formularzu lub innym kontenerze.</span><span class="sxs-lookup"><span data-stu-id="a8142-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="a8142-266">Ponieważ `ctlAlarmClock` ma większą głębię funkcjonalności, dodatkowy kod jest wymagany do przetestowania go.</span><span class="sxs-lookup"><span data-stu-id="a8142-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="a8142-267">W tej procedurze napiszesz prosty program do `ctlAlarmClock`testowania funkcjonalności .</span><span class="sxs-lookup"><span data-stu-id="a8142-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="a8142-268">Napiszesz kod, aby `AlarmTime` ustawić `ctlAlarmClock`i wyświetlić właściwość , i przetestuje jego nieodłączne funkcje.</span><span class="sxs-lookup"><span data-stu-id="a8142-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="a8142-269">Aby utworzyć i dodać formant do formularza testowego</span><span class="sxs-lookup"><span data-stu-id="a8142-269">To build and add your control to a test form</span></span>

1. <span data-ttu-id="a8142-270">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **ctlClockLib**, a następnie kliknij polecenie **Kompilacja**.</span><span class="sxs-lookup"><span data-stu-id="a8142-270">In **Solution Explorer**, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="a8142-271">Dodaj do rozwiązania nowy projekt **aplikacji Formularze systemu Windows** i nazwij go **Test**.</span><span class="sxs-lookup"><span data-stu-id="a8142-271">Add a new **Windows Forms Application** project to the solution, and name it **Test**.</span></span>

3. <span data-ttu-id="a8142-272">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Odwołania** dla projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="a8142-272">In **Solution Explorer**, right-click the **References** node for your test project.</span></span> <span data-ttu-id="a8142-273">Kliknij **pozycję Dodaj odwołanie,** aby wyświetlić okno dialogowe **Dodawanie odwołania.**</span><span class="sxs-lookup"><span data-stu-id="a8142-273">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="a8142-274">Kliknij kartę z etykietą **Projekty**.</span><span class="sxs-lookup"><span data-stu-id="a8142-274">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="a8142-275">Projekt `ctlClockLib` zostanie wyświetlony w obszarze **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="a8142-275">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="a8142-276">Kliknij dwukrotnie projekt, aby dodać odwołanie do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="a8142-276">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="a8142-277">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję **Testuj,** a następnie kliknij polecenie **Kompilacja**.</span><span class="sxs-lookup"><span data-stu-id="a8142-277">In **Solution Explorer**, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="a8142-278">W **przyborniku**rozwiń węzeł **składniki ctlClockLib.**</span><span class="sxs-lookup"><span data-stu-id="a8142-278">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="a8142-279">Kliknij dwukrotnie **ctlAlarmClock,** aby `ctlAlarmClock` dodać kopię do formularza.</span><span class="sxs-lookup"><span data-stu-id="a8142-279">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="a8142-280">W **przyborniku**znajdź i kliknij dwukrotnie **datetimepicker,** aby dodać <xref:System.Windows.Forms.DateTimePicker> formant do formularza, a następnie dodaj <xref:System.Windows.Forms.Label> formant, klikając dwukrotnie pozycję **Etykieta**.</span><span class="sxs-lookup"><span data-stu-id="a8142-280">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="a8142-281">Użyj myszki, aby ustawić kontrolki w dogodnym miejscu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a8142-281">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="a8142-282">Ustaw właściwości tych formantów w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a8142-282">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="a8142-283">Kontrola</span><span class="sxs-lookup"><span data-stu-id="a8142-283">Control</span></span>|<span data-ttu-id="a8142-284">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a8142-284">Property</span></span>|<span data-ttu-id="a8142-285">Wartość</span><span class="sxs-lookup"><span data-stu-id="a8142-285">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="a8142-286">**Tekst**</span><span class="sxs-lookup"><span data-stu-id="a8142-286">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="a8142-287">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="a8142-287">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="a8142-288">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="a8142-288">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="a8142-289">**Formacie**</span><span class="sxs-lookup"><span data-stu-id="a8142-289">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="a8142-290">W projektancie kliknij dwukrotnie **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="a8142-290">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="a8142-291">**Otworzy** się `private void dtpTest_ValueChanged`Edytor kodu .</span><span class="sxs-lookup"><span data-stu-id="a8142-291">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="a8142-292">Zmodyfikuj kod tak, aby przypominał następującą.</span><span class="sxs-lookup"><span data-stu-id="a8142-292">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="a8142-293">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję **Testuj**, a następnie kliknij polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="a8142-293">In **Solution Explorer**, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="a8142-294">W menu **Debugowanie** kliknij polecenie **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="a8142-294">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="a8142-295">Rozpocznie się program testowy.</span><span class="sxs-lookup"><span data-stu-id="a8142-295">The test program starts.</span></span> <span data-ttu-id="a8142-296">Należy zauważyć, że bieżący `ctlAlarmClock` czas jest aktualizowany w formancie i że godzina rozpoczęcia jest wyświetlana w formancie. <xref:System.Windows.Forms.DateTimePicker></span><span class="sxs-lookup"><span data-stu-id="a8142-296">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="a8142-297">Kliknij <xref:System.Windows.Forms.DateTimePicker> miejsce wyświetlania minut godziny.</span><span class="sxs-lookup"><span data-stu-id="a8142-297">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="a8142-298">Za pomocą klawiatury ustaw wartość minut o minutę większą niż `ctlAlarmClock`bieżący czas wyświetlany przez program .</span><span class="sxs-lookup"><span data-stu-id="a8142-298">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="a8142-299">Czas ustawienia alarmu jest `lblTest`wyświetlany w pliku .</span><span class="sxs-lookup"><span data-stu-id="a8142-299">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="a8142-300">Poczekaj, aż wyświetlany czas osiągnie czas ustawienia alarmu.</span><span class="sxs-lookup"><span data-stu-id="a8142-300">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="a8142-301">Gdy wyświetlany czas osiągnie czas, na który ustawiony `lblAlarm` jest alarm, będzie migać.</span><span class="sxs-lookup"><span data-stu-id="a8142-301">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="a8142-302">Wyłącz alarm, klikając `btnAlarmOff`przycisk .</span><span class="sxs-lookup"><span data-stu-id="a8142-302">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="a8142-303">Możesz teraz zresetować alarm.</span><span class="sxs-lookup"><span data-stu-id="a8142-303">You may now reset the alarm.</span></span>

<span data-ttu-id="a8142-304">Ten artykuł obejmuje szereg kluczowych pojęć.</span><span class="sxs-lookup"><span data-stu-id="a8142-304">This article has covered a number of key concepts.</span></span> <span data-ttu-id="a8142-305">Nauczysz się tworzyć formant złożony, łącząc formanty i składniki w kontenerze sterowania kompozytowego.</span><span class="sxs-lookup"><span data-stu-id="a8142-305">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="a8142-306">Nauczysz się dodawać właściwości do formantu i pisać kod w celu zaimplementowania funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a8142-306">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="a8142-307">W ostatniej sekcji, można nauczyć się rozszerzyć funkcjonalność danego sterowania złożonego poprzez dziedziczenie i zmienić funkcjonalność metod hosta przez zastąpienie tych metod.</span><span class="sxs-lookup"><span data-stu-id="a8142-307">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8142-308">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8142-308">See also</span></span>

- [<span data-ttu-id="a8142-309">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a8142-309">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="a8142-310">Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="a8142-310">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="a8142-311">Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#</span><span class="sxs-lookup"><span data-stu-id="a8142-311">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
