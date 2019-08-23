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
ms.openlocfilehash: c06639ef2f2ced8bd128adea636efe8be1715764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931021"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="d6c9b-102">Przewodnik: Dziedziczenie z kontrolki Windows Forms przy użyciu języka Visual C\#</span><span class="sxs-lookup"><span data-stu-id="d6c9b-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C\#</span></span>
<span data-ttu-id="d6c9b-103">Za pomocą C#wizualizacji można tworzyć zaawansowane niestandardowe kontrolkiprzez dziedziczenie.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-103">With Visual C#, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="d6c9b-104">Za pomocą dziedziczenia można tworzyć kontrolki, które zachowują wszystkie nieodłączne funkcje standardowych formantów Windows Forms, ale również zawierają funkcje niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="d6c9b-105">W tym instruktażu utworzysz prostą dziedziczoną kontrolkę o nazwie `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="d6c9b-106">Ten przycisk dziedziczy funkcje ze standardowego formantu Windows Forms <xref:System.Windows.Forms.Button> i uwidacznia właściwość niestandardową o nazwie. `ButtonValue`</span><span class="sxs-lookup"><span data-stu-id="d6c9b-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="d6c9b-107">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="d6c9b-107">Creating the Project</span></span>
 <span data-ttu-id="d6c9b-108">Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główną przestrzeń nazw, nazwę zestawu i nazwę projektu oraz upewnić się, że domyślny składnik będzie w poprawnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="d6c9b-109">Aby utworzyć bibliotekę kontrolek ValueButtonLib i formant ValueButton</span><span class="sxs-lookup"><span data-stu-id="d6c9b-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="d6c9b-110">W menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt** , aby otworzyć okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="d6c9b-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="d6c9b-111">Wybierz szablon projektu **Biblioteka formantów Windows Forms** z listy projektów C# wizualizacji, a następnie wpisz `ValueButtonLib` w polu **Nazwa** .</span><span class="sxs-lookup"><span data-stu-id="d6c9b-111">Select the **Windows Forms Control Library** project template from the list of Visual C# Projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="d6c9b-112">Nazwa projektu, `ValueButtonLib`, również jest domyślnie przypisana do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="d6c9b-113">Główna przestrzeń nazw służy do kwalifikowania nazw składników w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="d6c9b-114">Na przykład jeśli dwa zestawy dostarczają składniki o nazwie `ValueButton`, można `ValueButton` określić składnik przy użyciu `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="d6c9b-115">Aby uzyskać więcej informacji, zobacz [przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6c9b-115">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>

3. <span data-ttu-id="d6c9b-116">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **UserControl1.cs**, a następnie wybierz polecenie **Zmień nazwę** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-116">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="d6c9b-117">Zmień nazwę pliku na `ValueButton.cs`.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-117">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="d6c9b-118">Kliknij przycisk **tak** po wyświetleniu monitu, jeśli chcesz zmienić nazwy wszystkich odwołań do elementu kodu '`UserControl1`'.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-118">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>

4. <span data-ttu-id="d6c9b-119">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ValueButton.cs** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-119">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>

5. <span data-ttu-id="d6c9b-120">`class` Znajdź <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>wiersz instrukcji i Zmień typ, z którego dziedziczy `public partial class ValueButton`ten formant.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-120">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="d6c9b-121">Dzięki temu Odziedziczone kontrolki dziedziczą wszystkie funkcje <xref:System.Windows.Forms.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-121">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

6. <span data-ttu-id="d6c9b-122">W **Eksplorator rozwiązań**otwórz węzeł **ValueButton.cs** , aby wyświetlić plik kodu wygenerowany przez projektanta, **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-122">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="d6c9b-123">Otwórz ten plik w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-123">Open this file in the **Code Editor**.</span></span>

7. <span data-ttu-id="d6c9b-124">Znajdź metodę i Usuń wiersz, który <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> przypisuje właściwość. `InitializeComponent`</span><span class="sxs-lookup"><span data-stu-id="d6c9b-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="d6c9b-125">Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="d6c9b-126">Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-126">From the **File** menu, choose **Save All** to save the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d6c9b-127">Projektant wizualny nie jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-127">A visual designer is no longer available.</span></span> <span data-ttu-id="d6c9b-128"><xref:System.Windows.Forms.Button> Ponieważ kontrolka wykonuje własne malowanie, nie można modyfikować jej wyglądu w projektancie.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="d6c9b-129">Jego reprezentacja wizualna będzie dokładnie taka sama jak Klasa, która dziedziczy z (czyli), <xref:System.Windows.Forms.Button>chyba że zostanie zmodyfikowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="d6c9b-130">Można nadal dodawać składniki, które nie mają elementów interfejsu użytkownika, do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="d6c9b-131">Dodawanie właściwości do kontrolki dziedziczonej</span><span class="sxs-lookup"><span data-stu-id="d6c9b-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="d6c9b-132">Jednym z możliwych użycia dziedziczonych kontrolek Windows Forms jest utworzenie kontrolek, które są identyczne w wyglądzie i działaniu standardowych kontrolek Windows Forms, ale Uwidacznianie właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="d6c9b-133">W tej sekcji dodasz właściwość o nazwie `ButtonValue` do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="d6c9b-134">Aby dodać właściwość Value</span><span class="sxs-lookup"><span data-stu-id="d6c9b-134">To add the Value property</span></span>

1. <span data-ttu-id="d6c9b-135">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ValueButton.cs**, a następnie kliknij pozycję **Wyświetl kod** w menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-135">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="d6c9b-136">`class` Znajdź instrukcję.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-136">Locate the `class` statement.</span></span> <span data-ttu-id="d6c9b-137">Natychmiast po `{`wpisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="d6c9b-137">Immediately after the `{`, type the following code:</span></span>

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

     <span data-ttu-id="d6c9b-138">Ten kod ustawia metody, za pomocą których `ButtonValue` właściwość jest przechowywana i pobierana.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="d6c9b-139">Instrukcja ustawia wartość zwracaną na wartość, która jest przechowywana w zmiennej `varValue`prywatnej, a `set` instrukcja ustawia wartość zmiennej prywatnej za pomocą `value` słowa kluczowego. `get`</span><span class="sxs-lookup"><span data-stu-id="d6c9b-139">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>

3. <span data-ttu-id="d6c9b-140">Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="d6c9b-141">Testowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="d6c9b-141">Testing Your Control</span></span>
 <span data-ttu-id="d6c9b-142">Formanty nie są projektami autonomicznymi; muszą być hostowane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="d6c9b-143">W celu przetestowania kontrolki musisz dostarczyć projekt testowy, aby uruchomić go w programie.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="d6c9b-144">Należy również udostępnić formant dla projektu testowego przez skompilowanie (skompilowanie).</span><span class="sxs-lookup"><span data-stu-id="d6c9b-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="d6c9b-145">W tej sekcji utworzysz swój formant i przetestujesz go w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="d6c9b-146">Aby skompilować swój formant</span><span class="sxs-lookup"><span data-stu-id="d6c9b-146">To build your control</span></span>

1. <span data-ttu-id="d6c9b-147">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="d6c9b-148">Kompilacja powinna zakończyć się powodzeniem bez błędów lub ostrzeżeń kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="d6c9b-149">Aby utworzyć projekt testowy</span><span class="sxs-lookup"><span data-stu-id="d6c9b-149">To create a test project</span></span>

1. <span data-ttu-id="d6c9b-150">W menu **plik** wskaż polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt** , aby otworzyć okno dialogowe **Dodaj nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="d6c9b-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="d6c9b-151">Wybierz węzeł **systemu Windows** znajdujący się pod węzłem **wizualizacji C#**  , a następnie kliknij pozycję **Windows Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-151">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="d6c9b-152">W polu **Nazwa** wpisz `Test`.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="d6c9b-153">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla projektu testowego, a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów, aby wyświetlić okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="d6c9b-153">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="d6c9b-154">Kliknij kartę z etykietą **projekty**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-154">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="d6c9b-155">Projekt zostanie wyświetlony na liście **Nazwa projektu.** `ValueButtonLib`</span><span class="sxs-lookup"><span data-stu-id="d6c9b-155">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="d6c9b-156">Kliknij dwukrotnie projekt, aby dodać odwołanie do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-156">Double-click the project to add the reference to the test project.</span></span>

6. <span data-ttu-id="d6c9b-157">W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Testuj** i wybierz polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-157">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="d6c9b-158">Aby dodać kontrolkę do formularza</span><span class="sxs-lookup"><span data-stu-id="d6c9b-158">To add your control to the form</span></span>

1. <span data-ttu-id="d6c9b-159">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1.cs** i wybierz polecenie **View Designer** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-159">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="d6c9b-160">W **przyborniku**kliknij pozycję **składniki ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-160">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="d6c9b-161">Kliknij dwukrotnie pozycję **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-161">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="d6c9b-162">**ValueButton** pojawia się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-162">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="d6c9b-163">Kliknij prawym przyciskiem myszy **ValueButton** i wybierz polecenie **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-163">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="d6c9b-164">W oknie **Właściwości** , przejrzyj właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-164">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="d6c9b-165">Należy zauważyć, że są one takie same jak właściwości udostępniane przez standardowy przycisk, z tą różnicą, że istnieje `ButtonValue`dodatkowa właściwość.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-165">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="d6c9b-166">Ustaw `ButtonValue` właściwość `5`.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-166">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="d6c9b-167">Na karcie **wszystkie Windows Forms** przybornika kliknijdwukrotnie pozycję <xref:System.Windows.Forms.Label> **etykieta** , aby dodać kontrolkę do formularza.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-167">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="d6c9b-168">Przenieś etykietę do środka formularza.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-168">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="d6c9b-169">Kliknij `valueButton1`dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-169">Double-click `valueButton1`.</span></span>

     <span data-ttu-id="d6c9b-170">**Edytor kodu** zostanie otwarty dla `valueButton1_Click` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-170">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>

9. <span data-ttu-id="d6c9b-171">Wstaw następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-171">Insert the following line of code.</span></span>

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. <span data-ttu-id="d6c9b-172">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **test**, a następnie wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-172">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="d6c9b-173">Z menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-173">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="d6c9b-174">`Form1`się.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-174">`Form1` appears.</span></span>

12. <span data-ttu-id="d6c9b-175">Kliknij `valueButton1`pozycję.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-175">Click `valueButton1`.</span></span>

     <span data-ttu-id="d6c9b-176">Liczba "5 `label1`" jest wyświetlana w, pokazując, `ButtonValue` że właściwość dziedziczonego formantu została przeniesiona do `label1` za pomocą `valueButton1_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="d6c9b-176">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="d6c9b-177">W ten sposób formant dziedziczy wszystkie funkcje standardowego przycisku Windows Forms, ale uwidacznia dodatkową, niestandardową właściwość. `ValueButton`</span><span class="sxs-lookup"><span data-stu-id="d6c9b-177">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6c9b-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6c9b-178">See also</span></span>

- [<span data-ttu-id="d6c9b-179">Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="d6c9b-179">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="d6c9b-180">Przewodnik: Tworzenie formantu złożonego za pomocą wizualizacjiC#</span><span class="sxs-lookup"><span data-stu-id="d6c9b-180">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
