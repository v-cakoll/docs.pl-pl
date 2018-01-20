---
title: "Wskazówki: demonstrowanie dziedziczenia Visual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c5ef33be9841b5c74b6ae2448daf56079489b61
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a><span data-ttu-id="4a97f-102">Wskazówki: demonstrowanie dziedziczenia Visual</span><span class="sxs-lookup"><span data-stu-id="4a97f-102">Walkthrough: Demonstrating Visual Inheritance</span></span>
<span data-ttu-id="4a97f-103">Dziedziczenie Visual umożliwia sprawdzenie kontrolek w formularzu podstawowej i dodać nowe kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4a97f-103">Visual inheritance enables you to see the controls on the base form and to add new controls.</span></span> <span data-ttu-id="4a97f-104">W tym przewodniku utworzysz formularza podstawowego i skompiluj go do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="4a97f-104">In this walkthrough you will create a base form and compile it into a class library.</span></span> <span data-ttu-id="4a97f-105">Zostanie zaimportować tę bibliotekę klas do innego projektu i Utwórz nowy formularz, który dziedziczy z formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4a97f-105">You will import this class library into another project and create a new form that inherits from the base form.</span></span> <span data-ttu-id="4a97f-106">W tym przewodniku przedstawiono sposób:</span><span class="sxs-lookup"><span data-stu-id="4a97f-106">During this walkthrough, you will learn how to:</span></span>  
  
-   <span data-ttu-id="4a97f-107">Tworzenie projektu biblioteki klas, zawierający formularz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="4a97f-107">Create a class library project containing a base form.</span></span>  
  
-   <span data-ttu-id="4a97f-108">Dodaj przycisk Właściwości, które pochodzi z klasy podstawowej formularza można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="4a97f-108">Add a button with properties that derived classes of the base form can modify.</span></span>  
  
-   <span data-ttu-id="4a97f-109">Dodawanie przycisku, który nie może modyfikować dziedziczenia formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4a97f-109">Add a button that cannot be modified by inheritors of the base form.</span></span>  
  
-   <span data-ttu-id="4a97f-110">Utwórz projekt zawierający formularz, który dziedziczy `BaseForm`.</span><span class="sxs-lookup"><span data-stu-id="4a97f-110">Create a project containing a form that inherits from `BaseForm`.</span></span>  
  
 <span data-ttu-id="4a97f-111">Ostatecznie w tym przewodniku zostaną przedstawione różnica między prywatnych i chronionych formantów w formularzu dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="4a97f-111">Ultimately, this walkthrough will demonstrate the difference between private and protected controls on an inherited form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a97f-112">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="4a97f-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4a97f-113">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="4a97f-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4a97f-114">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="4a97f-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4a97f-115">Nie wszystkie formanty obsługuje dziedziczenie visual z formularz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="4a97f-115">Not all controls support visual inheritance from a base form.</span></span> <span data-ttu-id="4a97f-116">Następujące formanty nie obsługują scenariusz opisany w tym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="4a97f-116">The following controls do not support the scenario described in this walkthrough:</span></span>  
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
>  <span data-ttu-id="4a97f-117">Tych kontrolek w formularzu dziedziczone są zawsze, niezależnie od Modyfikatory używany jest tylko do odczytu (`private`, `protected`, lub `public`).</span><span class="sxs-lookup"><span data-stu-id="4a97f-117">These controls in the inherited form are always read-only regardless of the modifiers you use (`private`, `protected`, or `public`).</span></span>  
  
## <a name="scenario-steps"></a><span data-ttu-id="4a97f-118">Kroki w scenariuszu</span><span class="sxs-lookup"><span data-stu-id="4a97f-118">Scenario Steps</span></span>  
 <span data-ttu-id="4a97f-119">Pierwszym krokiem jest tworzenie formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4a97f-119">The first step is to create the base form.</span></span>  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a><span data-ttu-id="4a97f-120">Aby utworzyć projektu biblioteki klas, zawierający formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="4a97f-120">To create a class library project containing a base form</span></span>  
  
1.  <span data-ttu-id="4a97f-121">Z **pliku** menu, wybierz **nowy**, a następnie **projektu** otworzyć **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="4a97f-121">From the **File** menu, choose **New**, and then **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="4a97f-122">Tworzenie aplikacji formularzy systemu Windows o nazwie `BaseFormLibrary`.</span><span class="sxs-lookup"><span data-stu-id="4a97f-122">Create a Windows Forms application named `BaseFormLibrary`.</span></span>  
  
3.  <span data-ttu-id="4a97f-123">Do tworzenia biblioteki klas zamiast standardowego aplikacji formularzy systemu Windows, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **BaseFormLibrary** węzła projektu, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-123">To create a class library instead of a standard Windows Forms application, in **Solution Explorer**, right-click the **BaseFormLibrary** project node and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="4a97f-124">We właściwościach projektu, należy zmienić **Output typu** z **aplikacji systemu Windows** do **biblioteki klas**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-124">In the properties for the project, change the **Output type** from **Windows Application** to **Class Library**.</span></span>  
  
5.  <span data-ttu-id="4a97f-125">Z **pliku** menu, wybierz **Zapisz wszystko** do zapisywania plików projektu i w lokalizacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="4a97f-125">From the **File** menu, choose **Save All** to save the project and files to the default location.</span></span>  
  
 <span data-ttu-id="4a97f-126">Procedury w dwóch następnych dodawanie przycisków do formularza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4a97f-126">The next two procedures add buttons to the base form.</span></span> <span data-ttu-id="4a97f-127">Aby zademonstrować dziedziczenie visual, klient będzie przekazywać przycisków różne poziomy dostępu przez ustawienie ich `Modifiers` właściwości.</span><span class="sxs-lookup"><span data-stu-id="4a97f-127">To demonstrate visual inheritance, you will give the buttons different access levels by setting their `Modifiers` properties.</span></span>  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a><span data-ttu-id="4a97f-128">Aby dodać przycisku, który można modyfikować dziedziczenia formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="4a97f-128">To add a button that inheritors of the base form can modify</span></span>  
  
1.  <span data-ttu-id="4a97f-129">Otwórz **Form1** w projektancie.</span><span class="sxs-lookup"><span data-stu-id="4a97f-129">Open **Form1** in the designer.</span></span>  
  
2.  <span data-ttu-id="4a97f-130">Na **wszystkich formularzy systemu Windows** karcie **przybornika**, kliknij dwukrotnie **przycisk** w celu dodania przycisku do formularza.</span><span class="sxs-lookup"><span data-stu-id="4a97f-130">On the **All Windows Forms** tab of the **Toolbox**, double-click **Button** to add a button to the form.</span></span> <span data-ttu-id="4a97f-131">Za pomocą myszy pozycji, a następnie zmień rozmiar przycisku.</span><span class="sxs-lookup"><span data-stu-id="4a97f-131">Use the mouse to position and resize the button.</span></span>  
  
3.  <span data-ttu-id="4a97f-132">W oknie właściwości ustaw następujące właściwości przycisku:</span><span class="sxs-lookup"><span data-stu-id="4a97f-132">In the Properties window, set the following properties of the button:</span></span>  
  
    -   <span data-ttu-id="4a97f-133">Ustaw **tekst** właściwości **Hello powiedzieć**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-133">Set the **Text** property to **Say Hello**.</span></span>  
  
    -   <span data-ttu-id="4a97f-134">Ustaw **(nazwa)** właściwości **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-134">Set the **(Name)** property to **btnProtected**.</span></span>  
  
    -   <span data-ttu-id="4a97f-135">Ustaw**Modyfikatory** właściwości **chronione**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-135">Set the**Modifiers** property to **Protected**.</span></span> <span data-ttu-id="4a97f-136">Dzięki temu formularze, które dziedziczą z **Form1** można zmodyfikować właściwości **btnProtected**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-136">This makes it possible for forms that inherit from **Form1** to modify the properties of **btnProtected**.</span></span>  
  
4.  <span data-ttu-id="4a97f-137">Kliknij dwukrotnie **Hello powiedzieć** przycisk, aby dodać obsługę zdarzeń dla **kliknij** zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4a97f-137">Double-click the **Say Hello** button to add an event handler for the **Click** event.</span></span>  
  
5.  <span data-ttu-id="4a97f-138">Dodaj następujący wiersz kodu do obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="4a97f-138">Add the following line of code to the event handler:</span></span>  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a><span data-ttu-id="4a97f-139">Aby dodać przycisk, którego nie można zmodyfikować przez dziedziczenia formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="4a97f-139">To add a button that cannot be modified by inheritors of the base form</span></span>  
  
1.  <span data-ttu-id="4a97f-140">Przełącz do widoku projektu, klikając **Form1.vb [projekt], [projekt] pliku Form1.cs lub Form1.jsl [projekt]** kartę powyżej edytora kodu lub naciskając klawisz F7.</span><span class="sxs-lookup"><span data-stu-id="4a97f-140">Switch to design view by clicking the **Form1.vb [Design], Form1.cs [Design], or Form1.jsl [Design]** tab above the code editor, or by pressing F7.</span></span>  
  
2.  <span data-ttu-id="4a97f-141">Dodawanie drugiego przycisku i ustawienia swoich właściwości w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4a97f-141">Add a second button and set its properties as follows:</span></span>  
  
    -   <span data-ttu-id="4a97f-142">Ustaw **tekst** właściwości **Goodbye powiedzieć**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-142">Set the **Text** property to **Say Goodbye**.</span></span>  
  
    -   <span data-ttu-id="4a97f-143">Ustaw **(nazwa)** właściwości **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-143">Set the **(Name)** property to **btnPrivate**.</span></span>  
  
    -   <span data-ttu-id="4a97f-144">Ustaw **Modyfikatory** właściwości **prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-144">Set the **Modifiers** property to **Private**.</span></span> <span data-ttu-id="4a97f-145">Uniemożliwia jej formularze, które dziedziczą z **Form1** można zmodyfikować właściwości **btnPrivate**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-145">This makes it impossible for forms that inherit from **Form1** to modify the properties of **btnPrivate**.</span></span>  
  
3.  <span data-ttu-id="4a97f-146">Kliknij dwukrotnie **Goodbye powiedzieć** przycisk, aby dodać obsługę zdarzeń dla **kliknij** zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4a97f-146">Double-click the **Say Goodbye** button to add an event handler for the **Click** event.</span></span> <span data-ttu-id="4a97f-147">Umieść następujący wiersz kodu w procedurze zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="4a97f-147">Place the following line of code in the event procedure:</span></span>  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  <span data-ttu-id="4a97f-148">Z **kompilacji** menu, wybierz **kompilacji biblioteki BaseForm** do tworzenia biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="4a97f-148">From the **Build** menu, choose **Build BaseForm Library** to build the class library.</span></span>  
  
     <span data-ttu-id="4a97f-149">Po utworzeniu biblioteki można utworzyć nowy projekt, który dziedziczy z formularza, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="4a97f-149">Once the library is built, you can create a new project that inherits from the form you just created.</span></span>  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a><span data-ttu-id="4a97f-150">Aby utworzyć projekt zawierający formularz, który dziedziczy z formularza podstawowego</span><span class="sxs-lookup"><span data-stu-id="4a97f-150">To create a project containing a form that inherits from the base form</span></span>  
  
1.  <span data-ttu-id="4a97f-151">Z **pliku** menu, wybierz **Dodaj** , a następnie **nowy projekt** otworzyć **Dodawanie nowego projektu** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="4a97f-151">From the **File** menu, choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="4a97f-152">Tworzenie aplikacji formularzy systemu Windows o nazwie `InheritanceTest`.</span><span class="sxs-lookup"><span data-stu-id="4a97f-152">Create a Windows Forms application named `InheritanceTest`.</span></span>  
  
#### <a name="to-add-an-inherited-form"></a><span data-ttu-id="4a97f-153">Aby dodać dziedziczone formularza</span><span class="sxs-lookup"><span data-stu-id="4a97f-153">To add an inherited form</span></span>  
  
1.  <span data-ttu-id="4a97f-154">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projektu, zaznacz **Dodaj**, a następnie wybierz**nowy element**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-154">In **Solution Explorer**, right-click the **InheritanceTest** project, select **Add**, and then select**New Item**.</span></span>  
  
2.  <span data-ttu-id="4a97f-155">W **Dodaj nowy element** okno dialogowe, wybierz opcję **formularzy systemu Windows** kategorii (Jeśli korzystasz z listy Kategorie), a następnie wybierz **dziedziczone formularza** szablonu.</span><span class="sxs-lookup"><span data-stu-id="4a97f-155">In the **Add New Item** dialog box, select the **Windows Forms** category (if you have a list of categories) and then select the **Inherited Form** template.</span></span>  
  
3.  <span data-ttu-id="4a97f-156">Pozostaw nazwę domyślną `Form2` , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-156">Leave the default name of `Form2` and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="4a97f-157">W **selektora dziedziczenia** okno dialogowe, wybierz opcję **Form1** z **BaseFormLibrary** projektu jako formularza, aby dziedziczyć z, a następnie kliknij przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="4a97f-157">In the **Inheritance Picker** dialog box, select **Form1** from the **BaseFormLibrary** project as the form to inherit from and click **OK**.</span></span>  
  
     <span data-ttu-id="4a97f-158">Spowoduje to utworzenie formularza w **InheritanceTest** projektu pochodzący z formularza w **BaseFormLibrary**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-158">This creates a form in the **InheritanceTest** project that derives from the form in **BaseFormLibrary**.</span></span>  
  
5.  <span data-ttu-id="4a97f-159">Otwórz formularz dziedziczone (**formularz2**) w projektancie, klikając go, jeśli nie jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="4a97f-159">Open the inherited form (**Form2**) in the designer by double-clicking it, if it is not already open.</span></span>  
  
     <span data-ttu-id="4a97f-160">W Projektancie dziedziczone przyciski mają symbolu (![VisualBasicInheritanceSymbol — zrzut ekranu](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) w górnym rogu, wskazując, są one dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="4a97f-160">In the designer, the inherited buttons have a symbol (![VisualBasicInheritanceSymbol screenshot](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) in their upper corner, indicating they are inherited.</span></span>  
  
6.  <span data-ttu-id="4a97f-161">Wybierz **Hello powiedzieć** przycisk i obserwować uchwytów zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="4a97f-161">Select the **Say Hello** button and observe the resize handles.</span></span> <span data-ttu-id="4a97f-162">Ponieważ ten przycisk jest chroniony, dziedziczenia można go przenieść, jej rozmiar, zmienić jego podpis i wprowadzić inne zmiany.</span><span class="sxs-lookup"><span data-stu-id="4a97f-162">Because this button is protected, the inheritors can move it, resize it, change its caption, and make other modifications.</span></span>  
  
7.  <span data-ttu-id="4a97f-163">Wybierz prywatna **Goodbye powiedzieć** przycisk i zwróć uwagę, że nie ma uchwytów zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="4a97f-163">Select the private **Say Goodbye** button, and notice that it does not have resize handles.</span></span> <span data-ttu-id="4a97f-164">Ponadto w **właściwości** okna właściwości tego przycisku jest wyszarzony wskaż, nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="4a97f-164">Additionally, in the **Properties** window, the properties of this button are grayed to indicate they cannot be modified.</span></span>  
  
8.  <span data-ttu-id="4a97f-165">Jeśli używasz [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="4a97f-165">If you are using [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="4a97f-166">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1** w **InheritanceTest** projektu, a następnie wybierz pozycję **usunąć**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-166">In **Solution Explorer**, right-click **Form1** in the **InheritanceTest** project and then choose **Delete**.</span></span> <span data-ttu-id="4a97f-167">W wyświetlonym oknie komunikatu kliknij **OK** aby potwierdzić usunięcie.</span><span class="sxs-lookup"><span data-stu-id="4a97f-167">In the message box that appears, click **OK** to confirm the deletion.</span></span>  
  
    2.  <span data-ttu-id="4a97f-168">Otwórz plik Program.cs i zmień wiersz `Application.Run(new Form1());` do `Application.Run(new Form2());`.</span><span class="sxs-lookup"><span data-stu-id="4a97f-168">Open the Program.cs file and change the line `Application.Run(new Form1());` to `Application.Run(new Form2());`.</span></span>  
  
9. <span data-ttu-id="4a97f-169">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projekt i wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-169">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Set As Startup Project**.</span></span>  
  
10. <span data-ttu-id="4a97f-170">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projekt i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-170">In **Solution Explorer**, right-click the **InheritanceTest** project and select **Properties**.</span></span>  
  
11. <span data-ttu-id="4a97f-171">W **InheritanceTest** ustawić strony właściwości **obiekt uruchomieniowy** być dziedziczone formularza (**formularz2**).</span><span class="sxs-lookup"><span data-stu-id="4a97f-171">In the **InheritanceTest** property pages, set the **Startup object** to be the inherited form (**Form2**).</span></span>  
  
12. <span data-ttu-id="4a97f-172">Naciśnij klawisz F5, aby uruchomić aplikację i przyjrzeć się zachowaniu dziedziczone formularza.</span><span class="sxs-lookup"><span data-stu-id="4a97f-172">Press F5 to run the application, and observe the behavior of the inherited form.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4a97f-173">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4a97f-173">Next Steps</span></span>  
 <span data-ttu-id="4a97f-174">W przypadku kontrolek użytkownika dziedziczenia w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="4a97f-174">Inheritance for user controls works in much the same way.</span></span> <span data-ttu-id="4a97f-175">Otwórz nowy projektu biblioteki klas i Dodaj kontrolkę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a97f-175">Open a new class library project and add a user control.</span></span> <span data-ttu-id="4a97f-176">Umieść formanty składników na nim i skompilować projekt.</span><span class="sxs-lookup"><span data-stu-id="4a97f-176">Place constituent controls on it and compile the project.</span></span> <span data-ttu-id="4a97f-177">Otwórz innego nowego projektu biblioteki klas i Dodaj odwołanie do biblioteki klas skompilowany.</span><span class="sxs-lookup"><span data-stu-id="4a97f-177">Open another new class library project and add a reference to the compiled class library.</span></span> <span data-ttu-id="4a97f-178">Ponadto spróbuj dodać formant dziedziczony (za pośrednictwem **Dodawanie nowych elementów** okno dialogowe) do projektu i przy użyciu **selektora dziedziczenia**.</span><span class="sxs-lookup"><span data-stu-id="4a97f-178">Also, try adding an inherited control (through the **Add New Items** dialog box) to the project and using the **Inheritance Picker**.</span></span> <span data-ttu-id="4a97f-179">Dodaj kontrolkę użytkownika, a następnie zmień `Inherits` (`:` w [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4a97f-179">Add a user control, and change the `Inherits` (`:` in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) statement.</span></span> <span data-ttu-id="4a97f-180">Aby uzyskać więcej informacji, zobacz [porady: dziedziczenie formularzy systemu Windows](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4a97f-180">For more information, see [How to: Inherit Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a97f-181">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a97f-181">See Also</span></span>  
 [<span data-ttu-id="4a97f-182">Instrukcje: dziedziczenie formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4a97f-182">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="4a97f-183">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="4a97f-183">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="4a97f-184">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4a97f-184">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
