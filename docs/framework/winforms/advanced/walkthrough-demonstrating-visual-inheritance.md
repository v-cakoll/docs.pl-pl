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
ms.openlocfilehash: 9366c7ebe2e5b347f4795b15e6f2c2d0f3835482
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307628"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="5d69f-102">Przewodnik: Demonstrowanie dziedziczenia Visual</span><span class="sxs-lookup"><span data-stu-id="5d69f-102">Walkthrough: Demonstrating Visual Inheritance</span></span>
<span data-ttu-id="5d69f-103">Dziedziczenie Visual umożliwia sprawdzenie kontrolek w formularzu podstawowej i dodać nowe kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5d69f-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="5d69f-104">W tym instruktażu utworzysz formularza podstawowego i skompiluj go do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="5d69f-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="5d69f-105">Będzie zaimportować tej biblioteki klas do innego projektu i utworzyć nowy formularz, który dziedziczy z formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5d69f-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="5d69f-106">Z tego instruktażu dowiesz się jak:</span><span class="sxs-lookup"><span data-stu-id="5d69f-106">During this walkthrough, you will learn how to:</span></span>  
  
-   <span data-ttu-id="5d69f-107">Utwórz projekt biblioteki klas zawierający formularz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="5d69f-107">Create a class library project containing a base form.</span></span>  
  
-   <span data-ttu-id="5d69f-108">Dodaj przycisk z właściwościami, które pochodne klasy formularza podstawowego można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="5d69f-108">Add a button with properties that derived classes of the base form can modify.</span></span>  
  
-   <span data-ttu-id="5d69f-109">Dodaj przycisk, który nie może modyfikować obiektów dziedziczących z formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5d69f-109">Add a button that cannot be modified by inheritors of the base form.</span></span>  
  
-   <span data-ttu-id="5d69f-110">Utwórz projekt zawierający formularz, który dziedziczy z `BaseForm`.</span><span class="sxs-lookup"><span data-stu-id="5d69f-110">Create a project containing a form that inherits from `BaseForm`.</span></span>  
  
 <span data-ttu-id="5d69f-111">Ostatecznie w tym instruktażu będą pokazują różnicę między prywatnych i chronionych formantów na odziedziczony formularz.</span><span class="sxs-lookup"><span data-stu-id="5d69f-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d69f-112">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="5d69f-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5d69f-113">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="5d69f-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5d69f-114">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="5d69f-114">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5d69f-115">Nie wszystkie formanty obsługuje dziedziczenie visual z formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5d69f-115">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="5d69f-116">Następujące elementy sterujące nie obsługują scenariusza opisanego w tym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="5d69f-116">The following controls do not support the scenario described in this walkthrough:</span></span>  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  <span data-ttu-id="5d69f-117">Te kontrolki w odziedziczony formularz są zawsze, niezależnie od tego, Modyfikatory używasz jest tylko do odczytu (`private`, `protected`, lub `public`).</span><span class="sxs-lookup"><span data-stu-id="5d69f-117">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>  
  
## <a name="scenario-steps"></a><span data-ttu-id="5d69f-118">Kroki w scenariuszu</span><span class="sxs-lookup"><span data-stu-id="5d69f-118">Scenario Steps</span></span>  
 <span data-ttu-id="5d69f-119">Pierwszym krokiem jest utworzyć formularz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="5d69f-119">The first step is to create the base form.</span></span>  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="5d69f-120">Aby utworzyć projekt biblioteki klas zawierający formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="5d69f-120">To create a class library project containing a base form</span></span>  
  
1. <span data-ttu-id="5d69f-121">Z **pliku** menu, wybierz **New**, a następnie **projektu** otworzyć **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5d69f-121">From the **File** menu, choose **New**, and then **Project** to open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="5d69f-122">Tworzenie aplikacji Windows Forms o nazwie `BaseFormLibrary`.</span><span class="sxs-lookup"><span data-stu-id="5d69f-122">Create a Windows Forms application named `BaseFormLibrary`.</span></span>  
  
3. <span data-ttu-id="5d69f-123">Aby utworzyć bibliotekę klas, zamiast do standardowej aplikacji Windows Forms w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **BaseFormLibrary** węzła projektu, a następnie wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-123">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>  
  
4. <span data-ttu-id="5d69f-124">We właściwościach projektu, należy zmienić **typ danych wyjściowych** z **aplikacji Windows** do **biblioteki klas**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-124">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>  
  
5. <span data-ttu-id="5d69f-125">Z **pliku** menu, wybierz **Zapisz wszystko** do zapisania projektu i plików w lokalizacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="5d69f-125">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>  
  
 <span data-ttu-id="5d69f-126">W dwóch następnych procedur dodać przyciski do formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5d69f-126">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="5d69f-127">Aby zademonstrować dziedziczenie visual, zostanie nadana przyciski różne poziomy dostępu, ustawiając ich `Modifiers` właściwości.</span><span class="sxs-lookup"><span data-stu-id="5d69f-127">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="5d69f-128">Aby dodać przycisk, który może modyfikować obiektów dziedziczących z formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="5d69f-128">To add a button that inheritors of the base form can modify</span></span>  
  
1. <span data-ttu-id="5d69f-129">Otwórz **Form1** w projektancie.</span><span class="sxs-lookup"><span data-stu-id="5d69f-129">Open **Form1** in the designer.</span></span>  
  
2. <span data-ttu-id="5d69f-130">Na **wszystkie formularze Windows** karcie **przybornika**, kliknij dwukrotnie **przycisk** Aby dodać przycisk do formularza.</span><span class="sxs-lookup"><span data-stu-id="5d69f-130">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="5d69f-131">Aby ustawić położenie i rozmiar przycisku za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="5d69f-131">Use the mouse to position and resize the button.</span></span>  
  
3. <span data-ttu-id="5d69f-132">W oknie właściwości ustaw następujące właściwości przycisku:</span><span class="sxs-lookup"><span data-stu-id="5d69f-132">In the Properties window, set the following properties of the button:</span></span>  
  
    -   <span data-ttu-id="5d69f-133">Ustaw **tekstu** właściwości **Say Hello**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-133">Set the **Text** property to **Say Hello**.</span></span>  
  
    -   <span data-ttu-id="5d69f-134">Ustaw **(nazwa)** właściwości **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-134">Set the **(Name)** property to **btnProtected**.</span></span>  
  
    -   <span data-ttu-id="5d69f-135">Ustaw **Modyfikatory** właściwości **chronione**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-135">Set the **Modifiers** property to **Protected**.</span></span> <span data-ttu-id="5d69f-136">Dzięki temu możliwe formularzy, które dziedziczą z **Form1** można zmodyfikować właściwości **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-136">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>  
  
4. <span data-ttu-id="5d69f-137">Kliknij dwukrotnie **Say Hello** przycisk, aby dodać moduł obsługi zdarzenia **kliknij** zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5d69f-137">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>  
  
5. <span data-ttu-id="5d69f-138">Dodaj następujący wiersz kodu do obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="5d69f-138">Add the following line of code to the event handler:</span></span>  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="5d69f-139">Aby dodać przycisk, który nie może modyfikować obiektów dziedziczących z formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="5d69f-139">To add a button that cannot be modified by inheritors of the base form</span></span>  
  
1. <span data-ttu-id="5d69f-140">Przełącz do widoku projektu, klikając pozycję **Form1.vb [projekt], Form1.cs [projekt] lub [projekt] Form1.jsl** kartę powyżej edytora kodu lub naciskając klawisz F7.</span><span class="sxs-lookup"><span data-stu-id="5d69f-140">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>  
  
2. <span data-ttu-id="5d69f-141">Dodaj drugi przycisk i ustaw jego właściwości w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5d69f-141">Add a second button and set its properties as follows:</span></span>  
  
    -   <span data-ttu-id="5d69f-142">Ustaw **tekstu** właściwości **Say Goodbye**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-142">Set the **Text** property to **Say Goodbye**.</span></span>  
  
    -   <span data-ttu-id="5d69f-143">Ustaw **(nazwa)** właściwości **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-143">Set the **(Name)** property to **btnPrivate**.</span></span>  
  
    -   <span data-ttu-id="5d69f-144">Ustaw **Modyfikatory** właściwości **prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-144">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="5d69f-145">Uniemożliwia jej formularzy, które dziedziczą z **Form1** można zmodyfikować właściwości **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-145">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>  
  
3. <span data-ttu-id="5d69f-146">Kliknij dwukrotnie **Say Goodbye** przycisk, aby dodać moduł obsługi zdarzenia **kliknij** zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5d69f-146">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="5d69f-147">Umieść następujący wiersz kodu w procedurze zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="5d69f-147">Place the following line of code in the event procedure:</span></span>  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4. <span data-ttu-id="5d69f-148">Z **kompilacji** menu, wybierz **kompilacji biblioteki BaseForm** do tworzenia biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="5d69f-148">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>  
  
     <span data-ttu-id="5d69f-149">Po skompilowaniu biblioteki można utworzyć nowy projekt, który dziedziczy z formularza, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="5d69f-149">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="5d69f-150">Aby utworzyć projekt zawierający formularz, który dziedziczy z formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="5d69f-150">To create a project containing a form that inherits from the base form</span></span>  
  
1. <span data-ttu-id="5d69f-151">Z **pliku** menu, wybierz **Dodaj** i następnie **nowy projekt** otworzyć **Dodaj nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5d69f-151">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="5d69f-152">Tworzenie aplikacji Windows Forms o nazwie `InheritanceTest`.</span><span class="sxs-lookup"><span data-stu-id="5d69f-152">Create a Windows Forms application named `InheritanceTest`.</span></span>  
  
#### <a name="to-add-an-inherited-form"></a><span data-ttu-id="5d69f-153">Aby dodać odziedziczony formularz</span><span class="sxs-lookup"><span data-stu-id="5d69f-153">To add an inherited form</span></span>  
  
1. <span data-ttu-id="5d69f-154">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projektu, wybierz opcję **Dodaj**, a następnie wybierz pozycję **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-154">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select **New Item**.</span></span>  
  
2. <span data-ttu-id="5d69f-155">W **Dodaj nowy element** okno dialogowe, wybierz opcję **Windows Forms** kategorii (Jeśli masz listę kategorii), a następnie wybierz **dziedziczone formularza** szablonu.</span><span class="sxs-lookup"><span data-stu-id="5d69f-155">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>  
  
3. <span data-ttu-id="5d69f-156">Pozostaw domyślną nazwę `Form2` a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-156">Leave the default name of `Form2` and then click **Add**.</span></span>  
  
4. <span data-ttu-id="5d69f-157">W **selektor dziedziczenia** okno dialogowe, wybierz opcję **Form1** z **BaseFormLibrary** projektu jako formularz, aby dziedziczyć z, a następnie kliknij przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="5d69f-157">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>  
  
     <span data-ttu-id="5d69f-158">Spowoduje to utworzenie formularza w **InheritanceTest** projektu, który pochodzi z formularza w **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-158">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>  
  
5. <span data-ttu-id="5d69f-159">Otwórz odziedziczony formularz (**formularz2**) w projektancie, klikając dwukrotnie plik, go, jeśli nie jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="5d69f-159">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>  
  
     <span data-ttu-id="5d69f-160">W Projektancie dziedziczone przyciski powinny mieć symbol (</span><span class="sxs-lookup"><span data-stu-id="5d69f-160">In the designer, the inherited buttons have a symbol (</span></span>![Zrzut ekranu przedstawiający symbolu dziedziczenie Visual Basic.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)<span data-ttu-id="5d69f-162">) w górnym rogu, wskazując, są one dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="5d69f-162">) in their upper corner, indicating they are inherited.</span></span>  
  
6. <span data-ttu-id="5d69f-163">Wybierz **Say Hello** przycisk i obserwuj uchwytami zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="5d69f-163">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="5d69f-164">Ponieważ ten przycisk jest chroniony, obiektów dziedziczących można go przenieść, zmienić jego rozmiar, zmień swój podpis i wprowadzać inne modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="5d69f-164">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>  
  
7. <span data-ttu-id="5d69f-165">Wybierz prywatna **Say Goodbye** przycisku i zwróć uwagę, że nie ma uchwytami zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="5d69f-165">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="5d69f-166">Ponadto **właściwości** okna właściwości ten przycisk jest wyszarzony do wskazania, nie można ich modyfikować.</span><span class="sxs-lookup"><span data-stu-id="5d69f-166">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>  
  
8. <span data-ttu-id="5d69f-167">Jeśli używasz Visual C#:</span><span class="sxs-lookup"><span data-stu-id="5d69f-167">If you are using Visual C#:</span></span>  
  
    1.  <span data-ttu-id="5d69f-168">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1** w **InheritanceTest** projektu, a następnie wybierz **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-168">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="5d69f-169">W wyświetlonym oknie komunikatu kliknij **OK** o potwierdzenie usunięcia.</span><span class="sxs-lookup"><span data-stu-id="5d69f-169">In the message box that appears, click **OK** to confirm the deletion.</span></span>  
  
    2.  <span data-ttu-id="5d69f-170">Otwórz plik Program.cs i zmień wiersz `Application.Run(new Form1());` do `Application.Run(new Form2());`.</span><span class="sxs-lookup"><span data-stu-id="5d69f-170">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>  
  
9. <span data-ttu-id="5d69f-171">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-171">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>  
  
10. <span data-ttu-id="5d69f-172">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-172">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>  
  
11. <span data-ttu-id="5d69f-173">W **InheritanceTest** stron właściwości ustaw **obiekt początkowy** jako odziedziczony formularz (**formularz2**).</span><span class="sxs-lookup"><span data-stu-id="5d69f-173">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>  
  
12. <span data-ttu-id="5d69f-174">Naciśnij klawisz F5, aby uruchomić aplikację i przyjrzeć się zachowaniu odziedziczony formularz.</span><span class="sxs-lookup"><span data-stu-id="5d69f-174">Press F5 to run the application, and observe the behavior of the inherited form.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5d69f-175">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5d69f-175">Next Steps</span></span>  
 <span data-ttu-id="5d69f-176">Dziedziczenie w przypadku kontrolek użytkownika działa w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="5d69f-176">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="5d69f-177">Otwórz nowy projekt biblioteki klas i Dodaj kontrolkę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d69f-177">Open a new class library project and add a user control.</span></span> <span data-ttu-id="5d69f-178">Umieść formanty składników na nim i skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="5d69f-178">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="5d69f-179">Otwórz inny nowy projekt biblioteki klas i Dodaj odwołanie do biblioteki klas skompilowany.</span><span class="sxs-lookup"><span data-stu-id="5d69f-179">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="5d69f-180">Ponadto spróbuj dodać odziedziczoną kontrolkę (za pośrednictwem **Dodaj nowe elementy** okno dialogowe) do projektu i przy użyciu **selektor dziedziczenia**.</span><span class="sxs-lookup"><span data-stu-id="5d69f-180">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="5d69f-181">Dodaj formant użytkownika, a następnie zmień `Inherits` (`:` w języku Visual C#) instrukcja.</span><span class="sxs-lookup"><span data-stu-id="5d69f-181">Add a user control, and change the `Inherits` (`:` in Visual C#) statement.</span></span> <span data-ttu-id="5d69f-182">Aby uzyskać więcej informacji, zobacz [jak: Dziedziczenie formularzy Windows](how-to-inherit-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5d69f-182">For more information, see [How to: Inherit Windows Forms](how-to-inherit-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d69f-183">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d69f-183">See also</span></span>

- [<span data-ttu-id="5d69f-184">Instrukcje: Dziedziczenie formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="5d69f-184">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="5d69f-185">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="5d69f-185">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="5d69f-186">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5d69f-186">Windows Forms</span></span>](../index.md)
