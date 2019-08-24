---
title: 'Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows formantu z Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a9a4b9bc15d2579837c3f4969a8d85293f10967
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015670"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a><span data-ttu-id="32fe9-102">Przewodnik: Dziedzicz z kontrolki Windows Forms przy użyciu języka C\#</span><span class="sxs-lookup"><span data-stu-id="32fe9-102">Walkthrough: Inherit from a Windows Forms Control with C\#</span></span>

<span data-ttu-id="32fe9-103">Za pomocą C#wizualizacji można tworzyć zaawansowane niestandardowe kontrolkiprzez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="32fe9-103">With Visual C#, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="32fe9-104">Za pomocą dziedziczenia można tworzyć kontrolki, które zachowują wszystkie nieodłączne funkcje standardowych formantów Windows Forms, ale również zawierają funkcje niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="32fe9-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="32fe9-105">W tym instruktażu utworzysz prostą dziedziczoną kontrolkę o nazwie `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="32fe9-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="32fe9-106">Ten przycisk dziedziczy funkcje ze standardowego formantu Windows Forms <xref:System.Windows.Forms.Button> i uwidacznia właściwość niestandardową o nazwie. `ButtonValue`</span><span class="sxs-lookup"><span data-stu-id="32fe9-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="32fe9-107">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="32fe9-107">Create the Project</span></span>

<span data-ttu-id="32fe9-108">Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główną przestrzeń nazw, nazwę zestawu i nazwę projektu oraz upewnić się, że domyślny składnik będzie w poprawnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="32fe9-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="32fe9-109">Aby utworzyć bibliotekę kontrolek ValueButtonLib i formant ValueButton</span><span class="sxs-lookup"><span data-stu-id="32fe9-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="32fe9-110">W programie Visual Studio Utwórz nowy projekt **biblioteki formantów Windows Forms** i nadaj mu nazwę **ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-110">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ValueButtonLib**.</span></span>

     <span data-ttu-id="32fe9-111">Nazwa projektu, `ValueButtonLib`, również jest domyślnie przypisana do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="32fe9-111">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="32fe9-112">Główna przestrzeń nazw służy do kwalifikowania nazw składników w zestawie.</span><span class="sxs-lookup"><span data-stu-id="32fe9-112">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="32fe9-113">Na przykład jeśli dwa zestawy dostarczają składniki o nazwie `ValueButton`, można `ValueButton` określić składnik przy użyciu `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="32fe9-113">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="32fe9-114">Aby uzyskać więcej informacji, zobacz [przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="32fe9-114">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>

2. <span data-ttu-id="32fe9-115">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **UserControl1.cs**, a następnie wybierz polecenie **Zmień nazwę** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="32fe9-115">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="32fe9-116">Zmień nazwę pliku na **ValueButton.cs**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-116">Change the file name to **ValueButton.cs**.</span></span> <span data-ttu-id="32fe9-117">Kliknij przycisk **tak** po wyświetleniu monitu, jeśli chcesz zmienić nazwy wszystkich odwołań do elementu kodu '`UserControl1`'.</span><span class="sxs-lookup"><span data-stu-id="32fe9-117">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>

3. <span data-ttu-id="32fe9-118">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ValueButton.cs** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-118">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>

4. <span data-ttu-id="32fe9-119">`class` Znajdź <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>wiersz instrukcji i Zmień typ, z którego dziedziczy `public partial class ValueButton`ten formant.</span><span class="sxs-lookup"><span data-stu-id="32fe9-119">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="32fe9-120">Dzięki temu Odziedziczone kontrolki dziedziczą wszystkie funkcje <xref:System.Windows.Forms.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="32fe9-120">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

5. <span data-ttu-id="32fe9-121">W **Eksplorator rozwiązań**otwórz węzeł **ValueButton.cs** , aby wyświetlić plik kodu wygenerowany przez projektanta, **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-121">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="32fe9-122">Otwórz ten plik w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-122">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="32fe9-123">Znajdź metodę i Usuń wiersz, który <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> przypisuje właściwość. `InitializeComponent`</span><span class="sxs-lookup"><span data-stu-id="32fe9-123">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="32fe9-124">Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="32fe9-124">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="32fe9-125">Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="32fe9-125">From the **File** menu, choose **Save All** to save the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="32fe9-126">Projektant wizualny nie jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="32fe9-126">A visual designer is no longer available.</span></span> <span data-ttu-id="32fe9-127"><xref:System.Windows.Forms.Button> Ponieważ kontrolka wykonuje własne malowanie, nie można modyfikować jej wyglądu w projektancie.</span><span class="sxs-lookup"><span data-stu-id="32fe9-127">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="32fe9-128">Jego reprezentacja wizualna będzie dokładnie taka sama jak Klasa, która dziedziczy z (czyli), <xref:System.Windows.Forms.Button>chyba że zostanie zmodyfikowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="32fe9-128">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="32fe9-129">Można nadal dodawać składniki, które nie mają elementów interfejsu użytkownika, do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="32fe9-129">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="add-a-property-to-your-inherited-control"></a><span data-ttu-id="32fe9-130">Dodawanie właściwości do kontrolki dziedziczonej</span><span class="sxs-lookup"><span data-stu-id="32fe9-130">Add a Property to Your Inherited Control</span></span>

<span data-ttu-id="32fe9-131">Jednym z możliwych użycia dziedziczonych kontrolek Windows Forms jest utworzenie kontrolek, które są identyczne w wyglądzie i działaniu standardowych kontrolek Windows Forms, ale Uwidacznianie właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="32fe9-131">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="32fe9-132">W tej sekcji dodasz właściwość o nazwie `ButtonValue` do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="32fe9-132">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="32fe9-133">Aby dodać właściwość Value</span><span class="sxs-lookup"><span data-stu-id="32fe9-133">To add the Value property</span></span>

1. <span data-ttu-id="32fe9-134">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ValueButton.cs**, a następnie kliknij pozycję **Wyświetl kod** w menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="32fe9-134">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="32fe9-135">`class` Znajdź instrukcję.</span><span class="sxs-lookup"><span data-stu-id="32fe9-135">Locate the `class` statement.</span></span> <span data-ttu-id="32fe9-136">Natychmiast po `{`wpisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="32fe9-136">Immediately after the `{`, type the following code:</span></span>

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     <span data-ttu-id="32fe9-137">Ten kod ustawia metody, za pomocą których `ButtonValue` właściwość jest przechowywana i pobierana.</span><span class="sxs-lookup"><span data-stu-id="32fe9-137">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="32fe9-138">Instrukcja ustawia wartość zwracaną na wartość, która jest przechowywana w zmiennej `varValue`prywatnej, a `set` instrukcja ustawia wartość zmiennej prywatnej za pomocą `value` słowa kluczowego. `get`</span><span class="sxs-lookup"><span data-stu-id="32fe9-138">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>

3. <span data-ttu-id="32fe9-139">Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="32fe9-139">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="32fe9-140">Testowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="32fe9-140">Test the control</span></span>

<span data-ttu-id="32fe9-141">Formanty nie są projektami autonomicznymi; muszą być hostowane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="32fe9-141">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="32fe9-142">W celu przetestowania kontrolki musisz dostarczyć projekt testowy, aby uruchomić go w programie.</span><span class="sxs-lookup"><span data-stu-id="32fe9-142">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="32fe9-143">Należy również udostępnić formant dla projektu testowego przez skompilowanie (skompilowanie).</span><span class="sxs-lookup"><span data-stu-id="32fe9-143">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="32fe9-144">W tej sekcji utworzysz swój formant i przetestujesz go w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="32fe9-144">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="32fe9-145">Aby skompilować swój formant</span><span class="sxs-lookup"><span data-stu-id="32fe9-145">To build your control</span></span>

<span data-ttu-id="32fe9-146">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-146">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="32fe9-147">Kompilacja powinna zakończyć się powodzeniem bez błędów lub ostrzeżeń kompilatora.</span><span class="sxs-lookup"><span data-stu-id="32fe9-147">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="32fe9-148">Aby utworzyć projekt testowy</span><span class="sxs-lookup"><span data-stu-id="32fe9-148">To create a test project</span></span>

1. <span data-ttu-id="32fe9-149">W menu **plik** wskaż polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt** , aby otworzyć okno dialogowe **Dodaj nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="32fe9-149">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="32fe9-150">Wybierz węzeł **systemu Windows** znajdujący się pod węzłem **wizualizacji C#**  , a następnie kliknij pozycję **Windows Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-150">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="32fe9-151">W polu **Nazwa** wprowadź **test**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-151">In the **Name** box, enter **Test**.</span></span>

4. <span data-ttu-id="32fe9-152">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla projektu testowego, a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów, aby wyświetlić okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="32fe9-152">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="32fe9-153">Kliknij kartę z etykietą **projekty**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-153">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="32fe9-154">Projekt ValueButtonLib zostanie wyświetlony na liście **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-154">Your ValueButtonLib project will be listed under **Project Name**.</span></span> <span data-ttu-id="32fe9-155">Kliknij dwukrotnie projekt, aby dodać odwołanie do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="32fe9-155">Double-click the project to add the reference to the test project.</span></span>

6. <span data-ttu-id="32fe9-156">W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Testuj** i wybierz polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-156">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="32fe9-157">Aby dodać kontrolkę do formularza</span><span class="sxs-lookup"><span data-stu-id="32fe9-157">To add your control to the form</span></span>

1. <span data-ttu-id="32fe9-158">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1.cs** i wybierz polecenie **View Designer** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="32fe9-158">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="32fe9-159">W **przyborniku**wybierz pozycję **składniki ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-159">In the **Toolbox**, select **ValueButtonLib Components**.</span></span> <span data-ttu-id="32fe9-160">Kliknij dwukrotnie pozycję **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-160">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="32fe9-161">**ValueButton** pojawia się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="32fe9-161">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="32fe9-162">Kliknij prawym przyciskiem myszy **ValueButton** i wybierz polecenie **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="32fe9-162">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="32fe9-163">W oknie **Właściwości** , przejrzyj właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="32fe9-163">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="32fe9-164">Należy zauważyć, że są one takie same jak właściwości udostępniane przez standardowy przycisk, z tą różnicą, że istnieje dodatkowa Właściwość ButtonValue.</span><span class="sxs-lookup"><span data-stu-id="32fe9-164">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, ButtonValue.</span></span>

5. <span data-ttu-id="32fe9-165">Ustaw właściwość **ButtonValue** na **5**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-165">Set the **ButtonValue** property to **5**.</span></span>

6. <span data-ttu-id="32fe9-166">Na karcie **wszystkie Windows Forms** przybornika kliknijdwukrotnie pozycję <xref:System.Windows.Forms.Label> **etykieta** , aby dodać kontrolkę do formularza.</span><span class="sxs-lookup"><span data-stu-id="32fe9-166">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="32fe9-167">Przenieś etykietę do środka formularza.</span><span class="sxs-lookup"><span data-stu-id="32fe9-167">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="32fe9-168">Kliknij `valueButton1`dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="32fe9-168">Double-click `valueButton1`.</span></span>

     <span data-ttu-id="32fe9-169">**Edytor kodu** zostanie otwarty dla `valueButton1_Click` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="32fe9-169">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>

9. <span data-ttu-id="32fe9-170">Wstaw następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="32fe9-170">Insert the following line of code.</span></span>

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. <span data-ttu-id="32fe9-171">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **test**, a następnie wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="32fe9-171">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="32fe9-172">Z menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="32fe9-172">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="32fe9-173">`Form1`się.</span><span class="sxs-lookup"><span data-stu-id="32fe9-173">`Form1` appears.</span></span>

12. <span data-ttu-id="32fe9-174">Kliknij `valueButton1`pozycję.</span><span class="sxs-lookup"><span data-stu-id="32fe9-174">Click `valueButton1`.</span></span>

     <span data-ttu-id="32fe9-175">Liczba "5 `label1`" jest wyświetlana w, pokazując, `ButtonValue` że właściwość dziedziczonego formantu została przeniesiona do `label1` za pomocą `valueButton1_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="32fe9-175">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="32fe9-176">W ten sposób formant dziedziczy wszystkie funkcje standardowego przycisku Windows Forms, ale uwidacznia dodatkową, niestandardową właściwość. `ValueButton`</span><span class="sxs-lookup"><span data-stu-id="32fe9-176">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="32fe9-177">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32fe9-177">See also</span></span>

- [<span data-ttu-id="32fe9-178">Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="32fe9-178">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="32fe9-179">Przewodnik: Tworzenie formantu złożonego za pomocą wizualizacjiC#</span><span class="sxs-lookup"><span data-stu-id="32fe9-179">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
