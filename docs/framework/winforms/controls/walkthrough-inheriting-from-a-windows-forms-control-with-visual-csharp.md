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
ms.openlocfilehash: cafd8685f34537f8efb372967dc45682afbe8fa0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306381"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="7c71c-102">Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms przy użyciu języka Visual C\#</span><span class="sxs-lookup"><span data-stu-id="7c71c-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C\#</span></span>
<span data-ttu-id="7c71c-103">Za pomocą [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], można tworzyć zaawansowane Kontrolki niestandardowe za pomocą *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="7c71c-103">With [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="7c71c-104">Poprzez dziedziczenie jest możliwe w celu tworzenia formantów, które zachować wszystkie związane funkcje standardowych kontrolek Windows Forms, ale również dołączać niestandardowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="7c71c-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="7c71c-105">W tym instruktażu utworzysz prostą odziedziczoną kontrolkę o nazwie `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="7c71c-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="7c71c-106">Ten przycisk będzie dziedziczyć funkcji z formularzy Windows <xref:System.Windows.Forms.Button> kontrolować i udostępni właściwość niestandardową o nazwie `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="7c71c-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c71c-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="7c71c-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7c71c-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="7c71c-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7c71c-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7c71c-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="7c71c-110">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="7c71c-110">Creating the Project</span></span>  
 <span data-ttu-id="7c71c-111">Podczas tworzenia nowego projektu, należy określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślną będzie poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="7c71c-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="7c71c-112">Aby utworzyć ValueButtonLib Biblioteka kontrolek i kontrola ValueButton</span><span class="sxs-lookup"><span data-stu-id="7c71c-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1. <span data-ttu-id="7c71c-113">Na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="7c71c-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="7c71c-114">Wybierz **Biblioteka kontrolek formularzy Windows** szablonu projektu z listy projektów programu Visual C# i typu `ValueButtonLib` w **nazwa** pole.</span><span class="sxs-lookup"><span data-stu-id="7c71c-114">Select the **Windows Forms Control Library** project template from the list of Visual C# Projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="7c71c-115">Nazwa projektu `ValueButtonLib`, również jest domyślnie przypisane do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7c71c-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="7c71c-116">Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="7c71c-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="7c71c-117">Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ValueButton`, możesz określić swoje `ValueButton` za pomocą składnika `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="7c71c-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="7c71c-118">Aby uzyskać więcej informacji, zobacz [przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c71c-118">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>  
  
3. <span data-ttu-id="7c71c-119">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **UserControl1.cs**, następnie wybierz **Zmień nazwę** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="7c71c-119">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="7c71c-120">Zmień nazwę pliku, aby `ValueButton.cs`.</span><span class="sxs-lookup"><span data-stu-id="7c71c-120">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="7c71c-121">Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu '`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="7c71c-121">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>  
  
4. <span data-ttu-id="7c71c-122">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.cs** i wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-122">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>  
  
5. <span data-ttu-id="7c71c-123">Znajdź `class` wiersz instrukcji `public partial class ValueButton`, a następnie zmień typ, z której dziedziczy ten formant <xref:System.Windows.Forms.UserControl> do <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="7c71c-123">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="7c71c-124">Dzięki temu Twoje odziedziczoną kontrolkę dziedziczyć wszystkie funkcje programu <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7c71c-124">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
6. <span data-ttu-id="7c71c-125">W **Eksploratora rozwiązań**, otwórz **ValueButton.cs** węzeł, aby wyświetlić plik kod wygenerowany przez projektanta **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-125">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="7c71c-126">Otwórz ten plik w **Edytor kodu**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-126">Open this file in the **Code Editor**.</span></span>  
  
7. <span data-ttu-id="7c71c-127">Znajdź `InitializeComponent` metody i usunąć wiersza, który przypisuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c71c-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="7c71c-128">Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7c71c-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8. <span data-ttu-id="7c71c-129">Z **pliku** menu, wybierz **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="7c71c-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7c71c-130">Projektant wizualny nie jest już dostępna.</span><span class="sxs-lookup"><span data-stu-id="7c71c-130">A visual designer is no longer available.</span></span> <span data-ttu-id="7c71c-131">Ponieważ <xref:System.Windows.Forms.Button> formantu nie swój własny rysowania, nie można zmodyfikować jego wygląd w projektancie.</span><span class="sxs-lookup"><span data-stu-id="7c71c-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="7c71c-132">Jego wizualnej reprezentacji będzie dokładnie taka sama jak klasa dziedziczy (czyli <xref:System.Windows.Forms.Button>) o ile nie zmodyfikowano w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7c71c-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="7c71c-133">Składniki, które mają bez elementów interfejsu użytkownika, można nadal dodawać do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="7c71c-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="7c71c-134">Dodawanie właściwości do kontrolki dziedziczone</span><span class="sxs-lookup"><span data-stu-id="7c71c-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="7c71c-135">Jedno możliwe użycie dziedziczone kontrolek Windows Forms jest tworzenie elementów sterujących, które są identyczne w wygląd i działanie standardowych kontrolek Windows Forms, ale udostępnianie właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7c71c-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="7c71c-136">W tej sekcji dodasz właściwość o nazwie `ButtonValue` do formantu.</span><span class="sxs-lookup"><span data-stu-id="7c71c-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="7c71c-137">Aby dodać właściwość wartość</span><span class="sxs-lookup"><span data-stu-id="7c71c-137">To add the Value property</span></span>  
  
1. <span data-ttu-id="7c71c-138">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.cs**, a następnie kliknij przycisk **Wyświetl kod** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="7c71c-138">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="7c71c-139">Znajdź `class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c71c-139">Locate the `class` statement.</span></span> <span data-ttu-id="7c71c-140">Natychmiast po `{`, wpisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="7c71c-140">Immediately after the `{`, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="7c71c-141">Ten kod ustawia metody za pomocą którego `ButtonValue` właściwości przechowywania i pobierania.</span><span class="sxs-lookup"><span data-stu-id="7c71c-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="7c71c-142">`get` Instrukcja ustawia wartości zwracanej wartości, która jest przechowywana w zmiennej prywatnej `varValue`i `set` instrukcja ustawia wartość zmiennej prywatnej przy użyciu `value` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="7c71c-142">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>  
  
3. <span data-ttu-id="7c71c-143">Z **pliku** menu, wybierz **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="7c71c-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="7c71c-144">Testowanie formantu</span><span class="sxs-lookup"><span data-stu-id="7c71c-144">Testing Your Control</span></span>  
 <span data-ttu-id="7c71c-145">Formanty nie są autonomiczne projektów; muszą one być obsługiwane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="7c71c-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="7c71c-146">Aby przetestować Twoją kontrolą, musisz podać projekt testowy dla niego do uruchamiania w.</span><span class="sxs-lookup"><span data-stu-id="7c71c-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="7c71c-147">Należy również upewnić kontroli nad dostępne dla projektu testowego, tworząc (Kompilacja) go.</span><span class="sxs-lookup"><span data-stu-id="7c71c-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="7c71c-148">W tej sekcji utworzysz formant i przetestować ją w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="7c71c-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="7c71c-149">Tworzenie formantu</span><span class="sxs-lookup"><span data-stu-id="7c71c-149">To build your control</span></span>  
  
1. <span data-ttu-id="7c71c-150">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="7c71c-151">Kompilacja zostanie pomyślnie zakończona bez błędów i ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="7c71c-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="7c71c-152">Aby utworzyć projekt testowy</span><span class="sxs-lookup"><span data-stu-id="7c71c-152">To create a test project</span></span>  
  
1. <span data-ttu-id="7c71c-153">Na **pliku** menu wskaż **Dodaj** a następnie kliknij przycisk **nowy projekt** otworzyć **Dodaj nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="7c71c-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="7c71c-154">Wybierz **Windows** węzła, podrzędne **Visual C#** węzeł, a następnie kliknij przycisk **aplikacja interfejsu Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-154">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="7c71c-155">W **nazwa** wpisz `Test`.</span><span class="sxs-lookup"><span data-stu-id="7c71c-155">In the **Name** box, type `Test`.</span></span>  
  
4. <span data-ttu-id="7c71c-156">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł dla projektu testowego, następnie wybierz pozycję **Dodaj odwołanie** z menu skrótów, aby wyświetlić  **Dodaj odwołanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="7c71c-156">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
5. <span data-ttu-id="7c71c-157">Kliknij kartę **projektów**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-157">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="7c71c-158">Twoje `ValueButtonLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-158">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="7c71c-159">Kliknij dwukrotnie projektu można dodać odwołania do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="7c71c-159">Double-click the project to add the reference to the test project.</span></span>  
  
6. <span data-ttu-id="7c71c-160">W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **testu** i wybierz **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-160">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="7c71c-161">Aby dodać formant do formularza</span><span class="sxs-lookup"><span data-stu-id="7c71c-161">To add your control to the form</span></span>  
  
1. <span data-ttu-id="7c71c-162">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.cs** i wybierz polecenie **Projektant widoków** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="7c71c-162">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="7c71c-163">W **przybornika**, kliknij przycisk **składniki ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-163">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="7c71c-164">Kliknij dwukrotnie **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-164">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="7c71c-165">A **ValueButton** pojawia się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7c71c-165">A **ValueButton** appears on the form.</span></span>  
  
3. <span data-ttu-id="7c71c-166">Kliknij prawym przyciskiem myszy **ValueButton** i wybierz **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="7c71c-166">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4. <span data-ttu-id="7c71c-167">W **właściwości** okna, sprawdź właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="7c71c-167">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="7c71c-168">Należy pamiętać, są identyczne z właściwości ujawnione przez przycisk standardowy, z tą różnicą, że istnieje dodatkowa właściwość `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="7c71c-168">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5. <span data-ttu-id="7c71c-169">Ustaw `ButtonValue` właściwość `5`.</span><span class="sxs-lookup"><span data-stu-id="7c71c-169">Set the `ButtonValue` property to `5`.</span></span>  
  
6. <span data-ttu-id="7c71c-170">W **wszystkie formularze Windows** karcie **przybornika**, kliknij dwukrotnie **etykiety** dodać <xref:System.Windows.Forms.Label> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="7c71c-170">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7. <span data-ttu-id="7c71c-171">Przenieś etykietę do środka formularza.</span><span class="sxs-lookup"><span data-stu-id="7c71c-171">Relocate the label to the center of the form.</span></span>  
  
8. <span data-ttu-id="7c71c-172">Kliknij dwukrotnie `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="7c71c-172">Double-click `valueButton1`.</span></span>  
  
     <span data-ttu-id="7c71c-173">**Edytor kodu** otwiera `valueButton1_Click` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7c71c-173">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="7c71c-174">Wstaw następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="7c71c-174">Insert the following line of code.</span></span>  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. <span data-ttu-id="7c71c-175">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **testu**i wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="7c71c-175">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="7c71c-176">Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="7c71c-176">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     `Form1` <span data-ttu-id="7c71c-177">zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="7c71c-177">appears.</span></span>  
  
12. <span data-ttu-id="7c71c-178">Kliknij przycisk `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="7c71c-178">Click `valueButton1`.</span></span>  
  
     <span data-ttu-id="7c71c-179">Cyfry, '5' jest wyświetlana w `label1`, pokazując, `ButtonValue` właściwości dziedziczonych formant został przekazany do `label1` za pośrednictwem `valueButton1_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="7c71c-179">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="7c71c-180">Ten sposób Twoja `ValueButton` kontrola dziedziczy wszystkie funkcje standardowe przycisku Windows Forms, ale udostępnia dodatkowe, niestandardowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c71c-180">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c71c-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c71c-181">See also</span></span>

- [<span data-ttu-id="7c71c-182">Instrukcje: wyświetlanie kontroli w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="7c71c-182">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="7c71c-183">Przewodnik: tworzenie kontrolki złożonej za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="7c71c-183">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
