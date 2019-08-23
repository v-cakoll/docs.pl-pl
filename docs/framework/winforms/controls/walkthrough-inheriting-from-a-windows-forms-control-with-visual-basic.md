---
title: 'Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows z Visual Basic'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 378d7b0c67791e6c48e9859e0546594df3ccc85e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931006"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="af25b-102">Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af25b-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="af25b-103">Za pomocą Visual Basic można tworzyć zaawansowane niestandardowe kontrolki przez *dziedziczenie*.</span><span class="sxs-lookup"><span data-stu-id="af25b-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="af25b-104">Za pomocą dziedziczenia można tworzyć kontrolki, które zachowują wszystkie nieodłączne funkcje standardowych formantów Windows Forms, ale również zawierają funkcje niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="af25b-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="af25b-105">W tym instruktażu utworzysz prostą dziedziczoną kontrolkę o nazwie `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="af25b-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="af25b-106">Ten przycisk dziedziczy funkcje ze standardowego formantu Windows Forms <xref:System.Windows.Forms.Button> i uwidacznia właściwość niestandardową o nazwie. `ButtonValue`</span><span class="sxs-lookup"><span data-stu-id="af25b-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="af25b-107">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="af25b-107">Creating the Project</span></span>
 <span data-ttu-id="af25b-108">Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główną przestrzeń nazw, nazwę zestawu i nazwę projektu oraz upewnić się, że domyślny składnik będzie w poprawnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="af25b-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="af25b-109">Aby utworzyć bibliotekę kontrolek ValueButtonLib i formant ValueButton</span><span class="sxs-lookup"><span data-stu-id="af25b-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="af25b-110">W menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt** , aby otworzyć okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="af25b-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="af25b-111">Wybierz szablon projektu **Biblioteka formantów Windows Forms** z listy projektów Visual Basic i wpisz `ValueButtonLib` w polu **Nazwa** .</span><span class="sxs-lookup"><span data-stu-id="af25b-111">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="af25b-112">Nazwa projektu, `ValueButtonLib`, również jest domyślnie przypisana do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="af25b-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="af25b-113">Główna przestrzeń nazw służy do kwalifikowania nazw składników w zestawie.</span><span class="sxs-lookup"><span data-stu-id="af25b-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="af25b-114">Na przykład jeśli dwa zestawy dostarczają składniki o nazwie `ValueButton`, można `ValueButton` określić składnik przy użyciu `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="af25b-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="af25b-115">Aby uzyskać więcej informacji, zobacz [przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="af25b-115">For more information, see [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>

3. <span data-ttu-id="af25b-116">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **UserControl1. vb**, a następnie wybierz polecenie **Zmień nazwę** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="af25b-116">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="af25b-117">Zmień nazwę pliku na `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="af25b-117">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="af25b-118">Kliknij przycisk **tak** po wyświetleniu monitu, jeśli chcesz zmienić nazwę wszystkich odwołań do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="af25b-118">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>

4. <span data-ttu-id="af25b-119">W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** .</span><span class="sxs-lookup"><span data-stu-id="af25b-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="af25b-120">Otwórz węzeł **ValueButton. vb** , aby wyświetlić plik kodu wygenerowany przez projektanta, **ValueButton. Designer. vb**.</span><span class="sxs-lookup"><span data-stu-id="af25b-120">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="af25b-121">Otwórz ten plik w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="af25b-121">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="af25b-122">`Class` Znajdź <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>instrukcję iZmieńtyp,zktóregota`Partial Public Class ValueButton`kontrolka dziedziczy.</span><span class="sxs-lookup"><span data-stu-id="af25b-122">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="af25b-123">Dzięki temu Odziedziczone kontrolki dziedziczą wszystkie funkcje <xref:System.Windows.Forms.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="af25b-123">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="af25b-124">Znajdź metodę i Usuń wiersz, który <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> przypisuje właściwość. `InitializeComponent`</span><span class="sxs-lookup"><span data-stu-id="af25b-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="af25b-125">Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="af25b-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="af25b-126">Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="af25b-126">From the **File** menu, choose **Save All** to save the project.</span></span>

     <span data-ttu-id="af25b-127">Należy zauważyć, że projektant wizualny nie jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="af25b-127">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="af25b-128"><xref:System.Windows.Forms.Button> Ponieważ kontrolka wykonuje własne malowanie, nie można modyfikować jej wyglądu w projektancie.</span><span class="sxs-lookup"><span data-stu-id="af25b-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="af25b-129">Jego reprezentacja wizualna będzie dokładnie taka sama jak Klasa, która dziedziczy z (czyli), <xref:System.Windows.Forms.Button>chyba że zostanie zmodyfikowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="af25b-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>

> [!NOTE]
> <span data-ttu-id="af25b-130">Można nadal dodawać składniki, które nie mają elementów interfejsu użytkownika, do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="af25b-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="af25b-131">Dodawanie właściwości do kontrolki dziedziczonej</span><span class="sxs-lookup"><span data-stu-id="af25b-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="af25b-132">Jednym z możliwych użycia dziedziczonych kontrolek Windows Forms jest tworzenie formantów, które są identyczne w wyglądzie i zachowaniu (wygląd i działanie) w standardowych kontrolkach Windows Forms, ale uwidaczniają właściwości niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="af25b-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="af25b-133">W tej sekcji dodasz właściwość o nazwie `ButtonValue` do kontrolki.</span><span class="sxs-lookup"><span data-stu-id="af25b-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="af25b-134">Aby dodać właściwość Value</span><span class="sxs-lookup"><span data-stu-id="af25b-134">To add the Value property</span></span>

1. <span data-ttu-id="af25b-135">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **ValueButton. vb**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="af25b-135">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="af25b-136">`Public Class ValueButton` Znajdź instrukcję.</span><span class="sxs-lookup"><span data-stu-id="af25b-136">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="af25b-137">Bezpośrednio poniżej tej instrukcji wpisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="af25b-137">Immediately beneath this statement, type the following code:</span></span>

    ```vb
    ' Creates the private variable that will store the value of your
    ' property.
    Private varValue as integer
    ' Declares the property.
    Property ButtonValue() as Integer
    ' Sets the method for retrieving the value of your property.
       Get
          Return varValue
       End Get
    ' Sets the method for setting the value of your property.
       Set(ByVal Value as Integer)
          varValue = Value
       End Set
    End Property
    ```

     <span data-ttu-id="af25b-138">Ten kod ustawia metody, za pomocą których `ButtonValue` właściwość jest przechowywana i pobierana.</span><span class="sxs-lookup"><span data-stu-id="af25b-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="af25b-139">Instrukcja ustawia wartość zwracaną na wartość, która jest przechowywana w zmiennej `varValue`prywatnej, a `Set` instrukcja ustawia wartość zmiennej prywatnej za pomocą `Value` słowa kluczowego. `Get`</span><span class="sxs-lookup"><span data-stu-id="af25b-139">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>

3. <span data-ttu-id="af25b-140">Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.</span><span class="sxs-lookup"><span data-stu-id="af25b-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="af25b-141">Testowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="af25b-141">Testing Your Control</span></span>
 <span data-ttu-id="af25b-142">Formanty nie są projektami autonomicznymi; muszą być hostowane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="af25b-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="af25b-143">W celu przetestowania kontrolki musisz dostarczyć projekt testowy, aby uruchomić go w programie.</span><span class="sxs-lookup"><span data-stu-id="af25b-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="af25b-144">Należy również udostępnić formant dla projektu testowego przez skompilowanie (skompilowanie).</span><span class="sxs-lookup"><span data-stu-id="af25b-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="af25b-145">W tej sekcji utworzysz swój formant i przetestujesz go w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="af25b-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="af25b-146">Aby skompilować swój formant</span><span class="sxs-lookup"><span data-stu-id="af25b-146">To build your control</span></span>

1. <span data-ttu-id="af25b-147">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="af25b-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="af25b-148">Kompilacja powinna zakończyć się powodzeniem bez błędów lub ostrzeżeń kompilatora.</span><span class="sxs-lookup"><span data-stu-id="af25b-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="af25b-149">Aby utworzyć projekt testowy</span><span class="sxs-lookup"><span data-stu-id="af25b-149">To create a test project</span></span>

1. <span data-ttu-id="af25b-150">W menu **plik** wskaż polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt** , aby otworzyć okno dialogowe **Dodaj nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="af25b-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="af25b-151">Wybierz węzeł projekty Visual Basic, a następnie kliknij pozycję **Windows Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="af25b-151">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="af25b-152">W polu **Nazwa** wpisz `Test`.</span><span class="sxs-lookup"><span data-stu-id="af25b-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="af25b-153">W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** .</span><span class="sxs-lookup"><span data-stu-id="af25b-153">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="af25b-154">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla projektu testowego, a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów, aby wyświetlić okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="af25b-154">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

6. <span data-ttu-id="af25b-155">Kliknij kartę **projekty** .</span><span class="sxs-lookup"><span data-stu-id="af25b-155">Click the **Projects** tab.</span></span>

7. <span data-ttu-id="af25b-156">Kliknij kartę z etykietą **projekty**.</span><span class="sxs-lookup"><span data-stu-id="af25b-156">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="af25b-157">Projekt zostanie wyświetlony na liście **Nazwa projektu.** `ValueButtonLib`</span><span class="sxs-lookup"><span data-stu-id="af25b-157">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="af25b-158">Kliknij dwukrotnie projekt, aby dodać odwołanie do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="af25b-158">Double-click the project to add the reference to the test project.</span></span>

8. <span data-ttu-id="af25b-159">W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Testuj** i wybierz polecenie **Kompiluj**.</span><span class="sxs-lookup"><span data-stu-id="af25b-159">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="af25b-160">Aby dodać kontrolkę do formularza</span><span class="sxs-lookup"><span data-stu-id="af25b-160">To add your control to the form</span></span>

1. <span data-ttu-id="af25b-161">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1. vb** i wybierz polecenie **Projektant widoków** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="af25b-161">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="af25b-162">W **przyborniku**kliknij pozycję **składniki ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="af25b-162">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="af25b-163">Kliknij dwukrotnie pozycję **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="af25b-163">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="af25b-164">**ValueButton** pojawia się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="af25b-164">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="af25b-165">Kliknij prawym przyciskiem myszy **ValueButton** i wybierz polecenie **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="af25b-165">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="af25b-166">W oknie **Właściwości** , przejrzyj właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="af25b-166">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="af25b-167">Należy zauważyć, że są one takie same jak właściwości udostępniane przez standardowy przycisk, z tą różnicą, że istnieje `ButtonValue`dodatkowa właściwość.</span><span class="sxs-lookup"><span data-stu-id="af25b-167">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="af25b-168">Ustaw `ButtonValue` właściwość `5`.</span><span class="sxs-lookup"><span data-stu-id="af25b-168">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="af25b-169">Na karcie **wszystkie Windows Forms** przybornika kliknijdwukrotnie pozycję <xref:System.Windows.Forms.Label> **etykieta** , aby dodać kontrolkę do formularza.</span><span class="sxs-lookup"><span data-stu-id="af25b-169">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="af25b-170">Przenieś etykietę do środka formularza.</span><span class="sxs-lookup"><span data-stu-id="af25b-170">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="af25b-171">Kliknij `ValueButton1`dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="af25b-171">Double-click `ValueButton1`.</span></span>

     <span data-ttu-id="af25b-172">**Edytor kodu** zostanie otwarty dla `ValueButton1_Click` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="af25b-172">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>

9. <span data-ttu-id="af25b-173">Wpisz następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="af25b-173">Type the following line of code.</span></span>

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. <span data-ttu-id="af25b-174">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **test**, a następnie wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="af25b-174">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="af25b-175">Z menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="af25b-175">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="af25b-176">`Form1`się.</span><span class="sxs-lookup"><span data-stu-id="af25b-176">`Form1` appears.</span></span>

12. <span data-ttu-id="af25b-177">Kliknij `Valuebutton1`pozycję.</span><span class="sxs-lookup"><span data-stu-id="af25b-177">Click `Valuebutton1`.</span></span>

     <span data-ttu-id="af25b-178">Liczba "5 `Label1`" jest wyświetlana w, pokazując, `ButtonValue` że właściwość dziedziczonego formantu została przeniesiona do `Label1` za pomocą `ValueButton1_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="af25b-178">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="af25b-179">W ten sposób formant dziedziczy wszystkie funkcje standardowego przycisku Windows Forms, ale uwidacznia dodatkową, niestandardową właściwość. `ValueButton`</span><span class="sxs-lookup"><span data-stu-id="af25b-179">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="af25b-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af25b-180">See also</span></span>

- [<span data-ttu-id="af25b-181">Przewodnik: Tworzenie złożonego formantu z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af25b-181">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="af25b-182">Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="af25b-182">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="af25b-183">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="af25b-183">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="af25b-184">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af25b-184">Inheritance basics (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
