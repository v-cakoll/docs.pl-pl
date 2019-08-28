---
title: 'Przewodnik: Demonstrowanie dziedziczenia Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 32df98852b28963ffb748895156f7d9977c74b92
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046149"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="05755-102">Przewodnik: Demonstrowanie dziedziczenia Visual</span><span class="sxs-lookup"><span data-stu-id="05755-102">Walkthrough: Demonstrating Visual Inheritance</span></span>

<span data-ttu-id="05755-103">Dziedziczenie wizualne umożliwia wyświetlanie kontrolek w formularzu podstawowym i dodawanie nowych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="05755-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="05755-104">W tym instruktażu utworzysz formularz podstawowy i skompilujesz go w bibliotece klas.</span><span class="sxs-lookup"><span data-stu-id="05755-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="05755-105">Ta biblioteka klas zostanie zaimportowana do innego projektu i zostanie utworzony nowy formularz, który dziedziczy po formularzu podstawowym.</span><span class="sxs-lookup"><span data-stu-id="05755-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="05755-106">W tym instruktażu dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="05755-106">During this walkthrough, you will learn how to:</span></span>

- <span data-ttu-id="05755-107">Utwórz projekt biblioteki klas zawierający formularz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="05755-107">Create a class library project containing a base form.</span></span>

- <span data-ttu-id="05755-108">Dodaj przycisk z właściwościami, które mogą modyfikować klasy pochodne formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="05755-108">Add a button with properties that derived classes of the base form can modify.</span></span>

- <span data-ttu-id="05755-109">Dodaj przycisk, którego nie można modyfikować przez dziedziczenie formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="05755-109">Add a button that cannot be modified by inheritors of the base form.</span></span>

- <span data-ttu-id="05755-110">Utwórz projekt zawierający formularz, który dziedziczy z `BaseForm`.</span><span class="sxs-lookup"><span data-stu-id="05755-110">Create a project containing a form that inherits from `BaseForm`.</span></span>

<span data-ttu-id="05755-111">W tym instruktażu przedstawiono różnicę między kontrolkami prywatnymi i chronionymi w formularzu dziedziczonym.</span><span class="sxs-lookup"><span data-stu-id="05755-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>

> [!CAUTION]
> <span data-ttu-id="05755-112">Nie wszystkie formanty obsługują dziedziczenie wizualne z formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="05755-112">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="05755-113">Następujące kontrolki nie obsługują scenariusza opisanego w tym instruktażu:</span><span class="sxs-lookup"><span data-stu-id="05755-113">The following controls do not support the scenario described in this walkthrough:</span></span>
>
> - <xref:System.Windows.Forms.WebBrowser>
>
> - <xref:System.Windows.Forms.ToolStrip>
>
> - <xref:System.Windows.Forms.ToolStripPanel>
>
> - <xref:System.Windows.Forms.TableLayoutPanel>
>
> - <xref:System.Windows.Forms.FlowLayoutPanel>
>
> - <xref:System.Windows.Forms.DataGridView>
>
> <span data-ttu-id="05755-114">Te kontrolki w dziedziczonym formularzu są zawsze tylko do odczytu, niezależnie od używanej modyfikatora (`private`, `protected`lub `public`).</span><span class="sxs-lookup"><span data-stu-id="05755-114">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>

## <a name="create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="05755-115">Tworzenie projektu biblioteki klas zawierającego formularz podstawowy</span><span class="sxs-lookup"><span data-stu-id="05755-115">Create a class library project containing a base form</span></span>

1. <span data-ttu-id="05755-116">W programie Visual Studio w menu **plik** wybierz polecenie **Nowy** > **projekt** , aby otworzyć okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="05755-116">In Visual Studio, from the **File** menu, choose **New** > **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="05755-117">Utwórz aplikację Windows Formsową o `BaseFormLibrary`nazwie.</span><span class="sxs-lookup"><span data-stu-id="05755-117">Create a Windows Forms application named `BaseFormLibrary`.</span></span>

3. <span data-ttu-id="05755-118">Aby utworzyć bibliotekę klas zamiast standardowej aplikacji Windows Forms, w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **BaseFormLibrary** , a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="05755-118">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>

4. <span data-ttu-id="05755-119">We właściwościach projektu Zmień **Typ danych wyjściowych** z **aplikacji systemu Windows** na **bibliotekę klas**.</span><span class="sxs-lookup"><span data-stu-id="05755-119">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>

5. <span data-ttu-id="05755-120">Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt i pliki w domyślnej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="05755-120">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>

<span data-ttu-id="05755-121">Dwie następne procedury umożliwiają dodanie przycisków do formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="05755-121">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="05755-122">Aby zademonstrować dziedziczenie wizualne, nadajesz przyciskom różne poziomy dostępu `Modifiers` , ustawiając ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="05755-122">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="05755-123">Dodaj przycisk, który może modyfikować dziedziczenie formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="05755-123">Add a button that inheritors of the base form can modify</span></span>

1. <span data-ttu-id="05755-124">Otwórz **formularz Form1** w projektancie.</span><span class="sxs-lookup"><span data-stu-id="05755-124">Open **Form1** in the designer.</span></span>

2. <span data-ttu-id="05755-125">Na karcie **wszystkie Windows Forms** przybornika kliknijdwukrotnie przycisk, aby dodać przycisk do formularza.</span><span class="sxs-lookup"><span data-stu-id="05755-125">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="05755-126">Użyj myszy, aby ustawić położenie przycisku i zmienić jego rozmiar.</span><span class="sxs-lookup"><span data-stu-id="05755-126">Use the mouse to position and resize the button.</span></span>

3. <span data-ttu-id="05755-127">W okno Właściwości ustaw następujące właściwości przycisku:</span><span class="sxs-lookup"><span data-stu-id="05755-127">In the Properties window, set the following properties of the button:</span></span>

    - <span data-ttu-id="05755-128">Ustaw właściwość **Text** , aby **powiedzieć Hello**.</span><span class="sxs-lookup"><span data-stu-id="05755-128">Set the **Text** property to **Say Hello**.</span></span>

    - <span data-ttu-id="05755-129">Ustaw właściwość **(Name)** na **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="05755-129">Set the **(Name)** property to **btnProtected**.</span></span>

    - <span data-ttu-id="05755-130">Ustaw właściwość **Modyfikatory** na wartość **Protected**.</span><span class="sxs-lookup"><span data-stu-id="05755-130">Set the **Modifiers** property to **Protected**.</span></span> <span data-ttu-id="05755-131">Dzięki temu formularze dziedziczące z **formularza Form1** są modyfikowane w celu zmodyfikowania właściwości **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="05755-131">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>

4. <span data-ttu-id="05755-132">Kliknij dwukrotnie przycisk **powiedz Hello** , aby dodać procedurę obsługi zdarzeń dla zdarzenia **kliknięcia** .</span><span class="sxs-lookup"><span data-stu-id="05755-132">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>

5. <span data-ttu-id="05755-133">Dodaj następujący wiersz kodu do programu obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="05755-133">Add the following line of code to the event handler:</span></span>

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="05755-134">Dodaj przycisk, którego nie można modyfikować przez dziedziczenie formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="05755-134">Add a button that cannot be modified by inheritors of the base form</span></span>

1. <span data-ttu-id="05755-135">Przejdź do widoku projektu, klikając kartę **Form1. vb [projekt], Form1.cs [Design] lub Form1. JSL [Design]** nad edytorem kodu lub naciskając klawisz F7.</span><span class="sxs-lookup"><span data-stu-id="05755-135">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>

2. <span data-ttu-id="05755-136">Dodaj drugi przycisk i ustaw jego właściwości w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="05755-136">Add a second button and set its properties as follows:</span></span>

    - <span data-ttu-id="05755-137">Ustaw właściwość **Text** na wartość"Pożegnanie".</span><span class="sxs-lookup"><span data-stu-id="05755-137">Set the **Text** property to **Say Goodbye**.</span></span>

    - <span data-ttu-id="05755-138">Ustaw właściwość **(Name)** na **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="05755-138">Set the **(Name)** property to **btnPrivate**.</span></span>

    - <span data-ttu-id="05755-139">Ustaw właściwość **Modyfikatory** na wartość **Private**.</span><span class="sxs-lookup"><span data-stu-id="05755-139">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="05755-140">To sprawia, że dla formularzy dziedziczących z **formularza Form1** nie można modyfikować właściwości **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="05755-140">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>

3. <span data-ttu-id="05755-141">Kliknij dwukrotnie przycisk "na **przykład** ", aby dodać procedurę obsługi zdarzeń dla zdarzenia **kliknięcia** .</span><span class="sxs-lookup"><span data-stu-id="05755-141">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="05755-142">W procedurze zdarzenia umieść następujący wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="05755-142">Place the following line of code in the event procedure:</span></span>

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. <span data-ttu-id="05755-143">Z menu **kompilacja** wybierz kolejno opcje **Kompiluj BaseForm Library** , aby skompilować bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="05755-143">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>

     <span data-ttu-id="05755-144">Po skompilowaniu biblioteki można utworzyć nowy projekt, który dziedziczy po właśnie utworzonym formularzu.</span><span class="sxs-lookup"><span data-stu-id="05755-144">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="05755-145">Utwórz projekt zawierający formularz, który dziedziczy z formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="05755-145">Create a project containing a form that inherits from the base form</span></span>

1. <span data-ttu-id="05755-146">Z menu **plik** wybierz polecenie **Dodaj** , a następnie **Nowy projekt** , aby otworzyć okno dialogowe **Dodaj nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="05755-146">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="05755-147">Utwórz aplikację Windows Formsową o `InheritanceTest`nazwie.</span><span class="sxs-lookup"><span data-stu-id="05755-147">Create a Windows Forms application named `InheritanceTest`.</span></span>

## <a name="add-an-inherited-form"></a><span data-ttu-id="05755-148">Dodaj Dziedziczony formularz</span><span class="sxs-lookup"><span data-stu-id="05755-148">Add an inherited form</span></span>

1. <span data-ttu-id="05755-149">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **InheritanceTest** , wybierz polecenie **Dodaj**, a następnie wybierz pozycję **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="05755-149">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select **New Item**.</span></span>

2. <span data-ttu-id="05755-150">W oknie dialogowym **Dodaj nowy element** wybierz kategorię **Windows Forms** (Jeśli masz listę kategorii), a następnie wybierz **Dziedziczony szablon formularza** .</span><span class="sxs-lookup"><span data-stu-id="05755-150">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>

3. <span data-ttu-id="05755-151">Pozostaw domyślną nazwę `Form2` , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="05755-151">Leave the default name of `Form2` and then click **Add**.</span></span>

4. <span data-ttu-id="05755-152">W oknie dialogowym **Selektor dziedziczenia** wybierz opcję **Form1** z projektu **BaseFormLibrary** jako formularz do dziedziczenia, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="05755-152">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>

     <span data-ttu-id="05755-153">Spowoduje to utworzenie formularza w projekcie **InheritanceTest** , który pochodzi z formularza w **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="05755-153">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>

5. <span data-ttu-id="05755-154">Otwórz Dziedziczony formularz (**Form2**) w projektancie, klikając go dwukrotnie, jeśli nie jest jeszcze otwarty.</span><span class="sxs-lookup"><span data-stu-id="05755-154">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>

    <span data-ttu-id="05755-155">W projektancie przyciski dziedziczone mają symbol (</span><span class="sxs-lookup"><span data-stu-id="05755-155">In the designer, the inherited buttons have a symbol (</span></span>![Zrzut ekranu przedstawiający symbol dziedziczenia Visual Basic.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)<span data-ttu-id="05755-157">) w górnym rogu wskazujące, że są dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="05755-157">) in their upper corner, indicating they are inherited.</span></span>

6. <span data-ttu-id="05755-158">Wybierz przycisk **powiedz Hello** i obserwuj uchwyty zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="05755-158">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="05755-159">Ponieważ ten przycisk jest chroniony, dziedziczenia można przenieść, zmienić jego rozmiar, zmienić jego podpis i wprowadzić inne modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="05755-159">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>

7. <span data-ttu-id="05755-160">Wybierz prywatny przycisk "Pożegnanie" i zwróć uwagę, że nie ma dojść do zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="05755-160">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="05755-161">Ponadto w oknie **Właściwości** właściwości tego przycisku są wyszarzone, aby wskazać, że nie można ich modyfikować.</span><span class="sxs-lookup"><span data-stu-id="05755-161">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>

8. <span data-ttu-id="05755-162">Jeśli używasz wizualizacji C#:</span><span class="sxs-lookup"><span data-stu-id="05755-162">If you are using Visual C#:</span></span>

    1. <span data-ttu-id="05755-163">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1** w projekcie **InheritanceTest** , a następnie wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="05755-163">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="05755-164">W wyświetlonym oknie komunikatu kliknij przycisk **OK** , aby potwierdzić usunięcie.</span><span class="sxs-lookup"><span data-stu-id="05755-164">In the message box that appears, click **OK** to confirm the deletion.</span></span>

    2. <span data-ttu-id="05755-165">Otwórz plik program.cs i Zmień wiersz `Application.Run(new Form1());` na. `Application.Run(new Form2());`</span><span class="sxs-lookup"><span data-stu-id="05755-165">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>

9. <span data-ttu-id="05755-166">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **InheritanceTest** i wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="05755-166">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>

10. <span data-ttu-id="05755-167">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **InheritanceTest** i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="05755-167">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>

11. <span data-ttu-id="05755-168">Na stronach właściwości **InheritanceTest** Ustaw **obiekt startowy** jako Dziedziczony formularz (**Form2**).</span><span class="sxs-lookup"><span data-stu-id="05755-168">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>

12. <span data-ttu-id="05755-169">Naciśnij klawisz **F5** , aby uruchomić aplikację, i obserwuj zachowanie dziedziczonego formularza.</span><span class="sxs-lookup"><span data-stu-id="05755-169">Press **F5** to run the application, and observe the behavior of the inherited form.</span></span>

## <a name="next-steps"></a><span data-ttu-id="05755-170">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="05755-170">Next steps</span></span>

<span data-ttu-id="05755-171">Dziedziczenie dla kontrolek użytkownika działa w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="05755-171">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="05755-172">Otwórz nowy projekt biblioteki klas i Dodaj kontrolkę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="05755-172">Open a new class library project and add a user control.</span></span> <span data-ttu-id="05755-173">Umieść w nim kontrolki elementów i skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="05755-173">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="05755-174">Otwórz inny projekt biblioteki klas i Dodaj odwołanie do skompilowanej biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="05755-174">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="05755-175">Ponadto spróbuj dodać odziedziczony formant (za pomocą okna dialogowego **Dodaj nowe elementy** ) do projektu i przy użyciu **selektora dziedziczenia**.</span><span class="sxs-lookup"><span data-stu-id="05755-175">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="05755-176">Dodaj kontrolkę użytkownika i Zmień `Inherits` instrukcję (`:` w języku wizualnym C#).</span><span class="sxs-lookup"><span data-stu-id="05755-176">Add a user control, and change the `Inherits` (`:` in Visual C#) statement.</span></span> <span data-ttu-id="05755-177">Aby uzyskać więcej informacji, zobacz [jak: Dziedzicz Windows Forms](how-to-inherit-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="05755-177">For more information, see [How to: Inherit Windows Forms](how-to-inherit-windows-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05755-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05755-178">See also</span></span>

- [<span data-ttu-id="05755-179">Instrukcje: Dziedzicz Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05755-179">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="05755-180">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="05755-180">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="05755-181">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05755-181">Windows Forms</span></span>](../index.md)
