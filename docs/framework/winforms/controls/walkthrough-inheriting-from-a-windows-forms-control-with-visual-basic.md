---
title: 'Wskazówki: dziedziczenie z formantu formularzy systemu Windows z Visual Basic'
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
ms.openlocfilehash: 6c70de1bf6a5340b6f5b2c652110ed9be5536665
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541081"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="b89d3-102">Wskazówki: dziedziczenie z formantu formularzy systemu Windows z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b89d3-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="b89d3-103">Za pomocą Visual Basic można tworzyć zaawansowane Kontrolki niestandardowe za pomocą *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="b89d3-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="b89d3-104">Poprzez dziedziczenie jest możliwe w celu tworzenia formantów, które zachować wszystkie związane funkcje standardowych kontrolek Windows Forms, ale również dołączać niestandardowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="b89d3-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="b89d3-105">W tym instruktażu utworzysz prostą odziedziczoną kontrolkę o nazwie `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="b89d3-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="b89d3-106">Ten przycisk będzie dziedziczyć funkcji z formularzy Windows <xref:System.Windows.Forms.Button> kontrolować i udostępni właściwość niestandardową o nazwie `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="b89d3-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b89d3-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="b89d3-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b89d3-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="b89d3-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b89d3-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b89d3-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b89d3-110">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="b89d3-110">Creating the Project</span></span>  
 <span data-ttu-id="b89d3-111">Podczas tworzenia nowego projektu, należy określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślną będzie poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="b89d3-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="b89d3-112">Aby utworzyć ValueButtonLib Biblioteka kontrolek i kontrola ValueButton</span><span class="sxs-lookup"><span data-stu-id="b89d3-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="b89d3-113">Na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b89d3-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="b89d3-114">Wybierz **Biblioteka kontrolek formularzy Windows** szablonu projektu z listy projektów języka Visual Basic, a typ `ValueButtonLib` w **nazwa** pole.</span><span class="sxs-lookup"><span data-stu-id="b89d3-114">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="b89d3-115">Nazwa projektu `ValueButtonLib`, również jest domyślnie przypisane do głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b89d3-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="b89d3-116">Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b89d3-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="b89d3-117">Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ValueButton`, możesz określić swoje `ValueButton` za pomocą składnika `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="b89d3-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="b89d3-118">Aby uzyskać więcej informacji, zobacz [przestrzeni nazw w języku Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b89d3-118">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
3.  <span data-ttu-id="b89d3-119">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **UserControl1.vb**, następnie wybierz **Zmień nazwę** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="b89d3-119">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="b89d3-120">Zmień nazwę pliku, aby `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="b89d3-120">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="b89d3-121">Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="b89d3-121">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>  
  
4.  <span data-ttu-id="b89d3-122">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b89d3-122">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="b89d3-123">Otwórz **ValueButton.vb** węzeł, aby wyświetlić plik kod wygenerowany przez projektanta **ValueButton.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-123">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="b89d3-124">Otwórz ten plik w **Edytor kodu**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-124">Open this file in the **Code Editor**.</span></span>  
  
6.  <span data-ttu-id="b89d3-125">Znajdź `Class` instrukcji `Partial Public Class ValueButton`, a następnie zmień typ, z której dziedziczy ten formant <xref:System.Windows.Forms.UserControl> do <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="b89d3-125">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="b89d3-126">Dzięki temu Twoje odziedziczoną kontrolkę dziedziczyć wszystkie funkcje programu <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b89d3-126">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
7.  <span data-ttu-id="b89d3-127">Znajdź `InitializeComponent` metody i usunąć wiersza, który przypisuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b89d3-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="b89d3-128">Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b89d3-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="b89d3-129">Z **pliku** menu, wybierz **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="b89d3-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
     <span data-ttu-id="b89d3-130">Należy pamiętać, że projektant wizualny nie jest już dostępna.</span><span class="sxs-lookup"><span data-stu-id="b89d3-130">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="b89d3-131">Ponieważ <xref:System.Windows.Forms.Button> formantu nie swój własny rysowania, nie można zmodyfikować jego wygląd w projektancie.</span><span class="sxs-lookup"><span data-stu-id="b89d3-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="b89d3-132">Jego wizualnej reprezentacji będzie dokładnie taka sama jak klasa dziedziczy (czyli <xref:System.Windows.Forms.Button>) o ile nie zmodyfikowano w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b89d3-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b89d3-133">Składniki, które mają bez elementów interfejsu użytkownika, można nadal dodawać do powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="b89d3-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="b89d3-134">Dodawanie właściwości do kontrolki dziedziczone</span><span class="sxs-lookup"><span data-stu-id="b89d3-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="b89d3-135">Jedno możliwe użycie dziedziczone kontrolek Windows Forms jest tworzenie elementów sterujących, które są takie same jak w wygląd i zachowanie (wyglądu i działania) standardowych kontrolek Windows Forms, ale udostępnianie właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="b89d3-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="b89d3-136">W tej sekcji dodasz właściwość o nazwie `ButtonValue` do formantu.</span><span class="sxs-lookup"><span data-stu-id="b89d3-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="b89d3-137">Aby dodać właściwość wartość</span><span class="sxs-lookup"><span data-stu-id="b89d3-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="b89d3-138">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.vb**, a następnie kliknij przycisk **Wyświetl kod** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="b89d3-138">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="b89d3-139">Znajdź `Public Class ValueButton` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b89d3-139">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="b89d3-140">Natychmiast poniżej tej instrukcji, wpisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="b89d3-140">Immediately beneath this statement, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="b89d3-141">Ten kod ustawia metody za pomocą którego `ButtonValue` właściwości przechowywania i pobierania.</span><span class="sxs-lookup"><span data-stu-id="b89d3-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="b89d3-142">`Get` Instrukcja ustawia wartości zwracanej wartości, która jest przechowywana w zmiennej prywatnej `varValue`i `Set` instrukcja ustawia wartość zmiennej prywatnej przy użyciu `Value` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="b89d3-142">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>  
  
3.  <span data-ttu-id="b89d3-143">Z **pliku** menu, wybierz **Zapisz wszystko** być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="b89d3-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="b89d3-144">Testowanie formantu</span><span class="sxs-lookup"><span data-stu-id="b89d3-144">Testing Your Control</span></span>  
 <span data-ttu-id="b89d3-145">Formanty nie są autonomiczne projektów; muszą one być obsługiwane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="b89d3-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="b89d3-146">Aby przetestować Twoją kontrolą, musisz podać projekt testowy dla niego do uruchamiania w.</span><span class="sxs-lookup"><span data-stu-id="b89d3-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="b89d3-147">Należy również upewnić kontroli nad dostępne dla projektu testowego, tworząc (Kompilacja) go.</span><span class="sxs-lookup"><span data-stu-id="b89d3-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="b89d3-148">W tej sekcji utworzysz formant i przetestować ją w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="b89d3-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="b89d3-149">Tworzenie formantu</span><span class="sxs-lookup"><span data-stu-id="b89d3-149">To build your control</span></span>  
  
1.  <span data-ttu-id="b89d3-150">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="b89d3-151">Kompilacja zostanie pomyślnie zakończona bez błędów i ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="b89d3-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="b89d3-152">Aby utworzyć projekt testowy</span><span class="sxs-lookup"><span data-stu-id="b89d3-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="b89d3-153">Na **pliku** menu wskaż **Dodaj** a następnie kliknij przycisk **nowy projekt** otworzyć **Dodaj nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b89d3-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="b89d3-154">Wybierz węzeł projektów języka Visual Basic, a następnie kliknij przycisk **aplikacja interfejsu Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-154">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="b89d3-155">W **nazwa** wpisz `Test`.</span><span class="sxs-lookup"><span data-stu-id="b89d3-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="b89d3-156">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b89d3-156">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="b89d3-157">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł dla projektu testowego, następnie wybierz pozycję **Dodaj odwołanie** z menu skrótów, aby wyświetlić  **Dodaj odwołanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b89d3-157">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
6.  <span data-ttu-id="b89d3-158">Kliknij przycisk **projektów** kartę.</span><span class="sxs-lookup"><span data-stu-id="b89d3-158">Click the **Projects** tab.</span></span>  
  
7.  <span data-ttu-id="b89d3-159">Kliknij kartę **projektów**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-159">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="b89d3-160">Twoje `ValueButtonLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-160">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="b89d3-161">Kliknij dwukrotnie projektu można dodać odwołania do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="b89d3-161">Double-click the project to add the reference to the test project.</span></span>  
  
8.  <span data-ttu-id="b89d3-162">W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **testu** i wybierz **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-162">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="b89d3-163">Aby dodać formant do formularza</span><span class="sxs-lookup"><span data-stu-id="b89d3-163">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="b89d3-164">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.vb** i wybierz polecenie **Projektant widoków** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="b89d3-164">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="b89d3-165">W **przybornika**, kliknij przycisk **składniki ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-165">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="b89d3-166">Kliknij dwukrotnie **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-166">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="b89d3-167">A **ValueButton** pojawia się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="b89d3-167">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="b89d3-168">Kliknij prawym przyciskiem myszy **ValueButton** i wybierz **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="b89d3-168">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="b89d3-169">W **właściwości** okna, sprawdź właściwości tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b89d3-169">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="b89d3-170">Należy pamiętać, są identyczne z właściwości ujawnione przez przycisk standardowy, z tą różnicą, że istnieje dodatkowa właściwość `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="b89d3-170">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="b89d3-171">Ustaw `ButtonValue` właściwość `5`.</span><span class="sxs-lookup"><span data-stu-id="b89d3-171">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="b89d3-172">Na **wszystkie formularze Windows** karcie **przybornika**, kliknij dwukrotnie **etykiety** dodać <xref:System.Windows.Forms.Label> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="b89d3-172">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="b89d3-173">Przenieś etykietę do środka formularza.</span><span class="sxs-lookup"><span data-stu-id="b89d3-173">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="b89d3-174">Kliknij dwukrotnie `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="b89d3-174">Double-click `ValueButton1`.</span></span>  
  
     <span data-ttu-id="b89d3-175">**Edytor kodu** otwiera `ValueButton1_Click` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b89d3-175">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="b89d3-176">Wpisz następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="b89d3-176">Type the following line of code.</span></span>  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. <span data-ttu-id="b89d3-177">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **testu**i wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="b89d3-177">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="b89d3-178">Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="b89d3-178">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="b89d3-179">`Form1` zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="b89d3-179">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="b89d3-180">Kliknij przycisk `Valuebutton1`.</span><span class="sxs-lookup"><span data-stu-id="b89d3-180">Click `Valuebutton1`.</span></span>  
  
     <span data-ttu-id="b89d3-181">Cyfry, '5' jest wyświetlana w `Label1`, pokazując, `ButtonValue` właściwości dziedziczonych formant został przekazany do `Label1` za pośrednictwem `ValueButton1_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="b89d3-181">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="b89d3-182">Ten sposób Twoja `ValueButton` kontrola dziedziczy wszystkie funkcje standardowe przycisku Windows Forms, ale udostępnia dodatkowe, niestandardowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="b89d3-182">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b89d3-183">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b89d3-183">See Also</span></span>  
 [<span data-ttu-id="b89d3-184">Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b89d3-184">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="b89d3-185">Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="b89d3-185">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="b89d3-186">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b89d3-186">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="b89d3-187">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b89d3-187">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="b89d3-188">Tworzenie składników — wskazówki</span><span class="sxs-lookup"><span data-stu-id="b89d3-188">Component Authoring Walkthroughs</span></span>](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
