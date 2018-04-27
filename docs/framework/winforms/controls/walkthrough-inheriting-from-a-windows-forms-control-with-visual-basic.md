---
title: 'Wskazówki: dziedziczenie z formantu formularzy systemu Windows z Visual Basic'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 342ab60d4c3481d2154293fab9fb1254f937a934
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="070d7-102">Wskazówki: dziedziczenie z formantu formularzy systemu Windows z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="070d7-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="070d7-103">Visual Basic umożliwia tworzenie zaawansowanych formantów niestandardowych za pomocą *dziedziczenia*.</span><span class="sxs-lookup"><span data-stu-id="070d7-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="070d7-104">Poprzez dziedziczenie jest możliwość tworzenia formantów, które zachowują wszystkie funkcje związane z standardowe formanty formularzy systemu Windows, ale także dołączyć do nich funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="070d7-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="070d7-105">W tym przewodniku spowoduje utworzenie prostego formantu dziedziczone o nazwie `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="070d7-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="070d7-106">Ten przycisk będzie dziedziczyć funkcje z formularzy systemu Windows <xref:System.Windows.Forms.Button> kontroli i uwidoczni właściwość niestandardowa o nazwie `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="070d7-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="070d7-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="070d7-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="070d7-108">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="070d7-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="070d7-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="070d7-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="070d7-110">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="070d7-110">Creating the Project</span></span>  
 <span data-ttu-id="070d7-111">Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślna będzie poprawną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="070d7-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="070d7-112">Aby utworzyć biblioteki formantu ValueButtonLib i kontroli ValueButton</span><span class="sxs-lookup"><span data-stu-id="070d7-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="070d7-113">Na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="070d7-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="070d7-114">Wybierz **Biblioteka formantów formularzy systemu Windows** szablonu projektu z listy projektów Visual Basic i typ `ValueButtonLib` w **nazwa** pole.</span><span class="sxs-lookup"><span data-stu-id="070d7-114">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="070d7-115">Nazwa projektu `ValueButtonLib`, jest również przypisany do głównej przestrzeni nazw domyślnie.</span><span class="sxs-lookup"><span data-stu-id="070d7-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="070d7-116">Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie.</span><span class="sxs-lookup"><span data-stu-id="070d7-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="070d7-117">Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ValueButton`, można określić użytkownika `ValueButton` przy użyciu składnika `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="070d7-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="070d7-118">Aby uzyskać więcej informacji, zobacz [przestrzeni nazw w Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="070d7-118">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
3.  <span data-ttu-id="070d7-119">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **UserControl1.vb**, a następnie wybierz **zmienić** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="070d7-119">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="070d7-120">Zmień nazwę pliku, aby `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="070d7-120">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="070d7-121">Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="070d7-121">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>  
  
4.  <span data-ttu-id="070d7-122">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.</span><span class="sxs-lookup"><span data-stu-id="070d7-122">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="070d7-123">Otwórz **ValueButton.vb** węzeł, aby wyświetlić plik kod wygenerowany przez projektanta **ValueButton.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="070d7-123">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="070d7-124">Otwórz ten plik w **edytora kodu**.</span><span class="sxs-lookup"><span data-stu-id="070d7-124">Open this file in the **Code Editor**.</span></span>  
  
6.  <span data-ttu-id="070d7-125">Zlokalizuj `Class` instrukcji, `Partial Public Class ValueButton`i zmienić typ, z której dziedziczy ten formant <xref:System.Windows.Forms.UserControl> do <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="070d7-125">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="070d7-126">Dzięki temu dziedziczone formantu dziedziczy wszystkie funkcje <xref:System.Windows.Forms.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="070d7-126">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
7.  <span data-ttu-id="070d7-127">Zlokalizuj `InitializeComponent` — metoda i Usuń wiersz, który przypisuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="070d7-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="070d7-128">Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="070d7-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="070d7-129">Z **pliku** menu, wybierz **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="070d7-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
     <span data-ttu-id="070d7-130">Należy pamiętać, że projektant wizualny nie jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="070d7-130">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="070d7-131">Ponieważ <xref:System.Windows.Forms.Button> formant wykonuje własny obraz, nie można zmodyfikować jego wygląd w projektancie.</span><span class="sxs-lookup"><span data-stu-id="070d7-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="070d7-132">Jego wizualnej reprezentacji będą dokładnie taka sama jak klasa dziedziczy z (czyli <xref:System.Windows.Forms.Button>), chyba że zmodyfikowany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="070d7-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="070d7-133">Nadal możesz dodać składniki, które mają żadnych elementów interfejsu użytkownika, na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="070d7-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="070d7-134">Dodawanie właściwości do dziedziczonej formantu</span><span class="sxs-lookup"><span data-stu-id="070d7-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="070d7-135">Jeden wykorzystanie dziedziczone formanty formularzy systemu Windows jest tworzenie formantów, które są takie same jak w wygląd i zachowanie (wygląd i działanie) standardowe formanty formularzy systemu Windows, ale udostępniają właściwości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="070d7-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="070d7-136">W tej sekcji dodasz właściwość o nazwie `ButtonValue` do formantu.</span><span class="sxs-lookup"><span data-stu-id="070d7-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="070d7-137">Aby dodać właściwości Value</span><span class="sxs-lookup"><span data-stu-id="070d7-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="070d7-138">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.vb**, a następnie kliknij przycisk **kod widoku** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="070d7-138">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="070d7-139">Zlokalizuj `Public Class ValueButton` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="070d7-139">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="070d7-140">Natychmiast poniżej tej instrukcji, wpisz następujący kod:</span><span class="sxs-lookup"><span data-stu-id="070d7-140">Immediately beneath this statement, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="070d7-141">Ten kod ustawia metody za pomocą której `ButtonValue` przechowywania i pobierania właściwości.</span><span class="sxs-lookup"><span data-stu-id="070d7-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="070d7-142">`Get` Instrukcja ustawia wartości zwracanej wartości, który jest przechowywany w prywatnej zmiennej `varValue`i `Set` instrukcja ustawia wartość zmiennej prywatnej przy użyciu `Value` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="070d7-142">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>  
  
3.  <span data-ttu-id="070d7-143">Z **pliku** menu, wybierz **Zapisz wszystko** zapisać projektu.</span><span class="sxs-lookup"><span data-stu-id="070d7-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="070d7-144">Testowanie formantu</span><span class="sxs-lookup"><span data-stu-id="070d7-144">Testing Your Control</span></span>  
 <span data-ttu-id="070d7-145">Formanty nie są autonomicznych projektów; muszą one być obsługiwane w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="070d7-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="070d7-146">W celu przetestowania formantu, należy podać projekt testowy na jej uruchamianie.</span><span class="sxs-lookup"><span data-stu-id="070d7-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="070d7-147">Należy również upewnić formantu dostępne dla projektu testowego według budynków (Kompilacja) go.</span><span class="sxs-lookup"><span data-stu-id="070d7-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="070d7-148">W tej sekcji zostanie kompilacji formantu i przetestować go w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="070d7-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="070d7-149">Tworzenie formantu</span><span class="sxs-lookup"><span data-stu-id="070d7-149">To build your control</span></span>  
  
1.  <span data-ttu-id="070d7-150">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="070d7-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="070d7-151">Kompilacja zostanie pomyślnie zakończona bez błędów lub ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="070d7-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="070d7-152">Aby utworzyć projekt testowy</span><span class="sxs-lookup"><span data-stu-id="070d7-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="070d7-153">Na **pliku** menu wskaż **Dodaj** , a następnie kliknij przycisk **nowy projekt** otworzyć **Dodawanie nowego projektu** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="070d7-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="070d7-154">Wybierz węzeł projekty Visual Basic, a następnie kliknij przycisk **aplikacji Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="070d7-154">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="070d7-155">W **nazwa** wpisz `Test`.</span><span class="sxs-lookup"><span data-stu-id="070d7-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="070d7-156">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.</span><span class="sxs-lookup"><span data-stu-id="070d7-156">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="070d7-157">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzła dla projektu testowego, następnie wybierz **Dodaj odwołanie** z menu skrótów do wyświetlenia  **Dodaj odwołanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="070d7-157">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
6.  <span data-ttu-id="070d7-158">Kliknij przycisk **projekty** kartę.</span><span class="sxs-lookup"><span data-stu-id="070d7-158">Click the **Projects** tab.</span></span>  
  
7.  <span data-ttu-id="070d7-159">Kliknij kartę **projekty**.</span><span class="sxs-lookup"><span data-stu-id="070d7-159">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="070d7-160">Twoje `ValueButtonLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="070d7-160">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="070d7-161">Kliknij dwukrotnie plik projektu można dodać odwołania do projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="070d7-161">Double-click the project to add the reference to the test project.</span></span>  
  
8.  <span data-ttu-id="070d7-162">W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **testu** i wybierz **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="070d7-162">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="070d7-163">Aby dodać formantu do formularza</span><span class="sxs-lookup"><span data-stu-id="070d7-163">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="070d7-164">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.vb** i wybierz polecenie **Widok projektanta** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="070d7-164">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="070d7-165">W **przybornika**, kliknij przycisk **składniki ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="070d7-165">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="070d7-166">Kliknij dwukrotnie **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="070d7-166">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="070d7-167">A **ValueButton** w formularzu.</span><span class="sxs-lookup"><span data-stu-id="070d7-167">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="070d7-168">Kliknij prawym przyciskiem myszy **ValueButton** i wybierz **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="070d7-168">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="070d7-169">W **właściwości** okna, sprawdź właściwości tego formantu.</span><span class="sxs-lookup"><span data-stu-id="070d7-169">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="070d7-170">Należy pamiętać, są takie same jak właściwości udostępniane przez przycisk standardowy, z tą różnicą, że jest właściwością dodatkowe `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="070d7-170">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="070d7-171">Ustaw `ButtonValue` właściwości `5`.</span><span class="sxs-lookup"><span data-stu-id="070d7-171">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="070d7-172">Na **wszystkich formularzy systemu Windows** karcie **przybornika**, kliknij dwukrotnie **etykiety** można dodać <xref:System.Windows.Forms.Label> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="070d7-172">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="070d7-173">Przemieszczenie etykietę do Centrum formularza.</span><span class="sxs-lookup"><span data-stu-id="070d7-173">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="070d7-174">Kliknij dwukrotnie `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="070d7-174">Double-click `ValueButton1`.</span></span>  
  
     <span data-ttu-id="070d7-175">**Edytora kodu** otwiera `ValueButton1_Click` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="070d7-175">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="070d7-176">Wpisz następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="070d7-176">Type the following line of code.</span></span>  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. <span data-ttu-id="070d7-177">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **testu**i wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="070d7-177">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="070d7-178">Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="070d7-178">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="070d7-179">`Form1` zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="070d7-179">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="070d7-180">Kliknij przycisk `Valuebutton1`.</span><span class="sxs-lookup"><span data-stu-id="070d7-180">Click `Valuebutton1`.</span></span>  
  
     <span data-ttu-id="070d7-181">Liczb, "5" jest wyświetlany w `Label1`, ilustrujące który `ButtonValue` właściwości dziedziczone formantu został przekazany do `Label1` za pośrednictwem `ValueButton1_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="070d7-181">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="070d7-182">W związku z tym Twoje `ValueButton` kontrola dziedziczy wszystkie funkcje standardowej przycisku formularzy systemu Windows, ale udostępnia dodatkowe, niestandardowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="070d7-182">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070d7-183">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="070d7-183">See Also</span></span>  
 [<span data-ttu-id="070d7-184">Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="070d7-184">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="070d7-185">Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika</span><span class="sxs-lookup"><span data-stu-id="070d7-185">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="070d7-186">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="070d7-186">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="070d7-187">Podstawowe informacje o dziedziczeniu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="070d7-187">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="070d7-188">Wskazówki dotyczące tworzenia składników</span><span class="sxs-lookup"><span data-stu-id="070d7-188">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
