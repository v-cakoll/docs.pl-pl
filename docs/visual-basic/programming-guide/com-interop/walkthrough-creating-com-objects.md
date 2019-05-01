---
title: 'Przewodnik: Tworzenie obiektów COM z Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 97e917d568b31860979e54598350d1ae7a6fdb25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022314"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="b4b90-102">Przewodnik: Tworzenie obiektów COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4b90-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="b4b90-103">Podczas tworzenia nowych aplikacji lub składników, najlepiej utworzyć zestawów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4b90-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="b4b90-104">Jednakże Visual Basic również ułatwia udostępnianie składników .NET Framework, dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="b4b90-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="b4b90-105">Dzięki temu można zapewnić nowych składników dla starszych zestawów aplikacji, które wymagają składników COM.</span><span class="sxs-lookup"><span data-stu-id="b4b90-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="b4b90-106">W tym instruktażu przedstawiono sposób użycia języka Visual Basic do udostępnienia [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] obiekty jako obiekty COM, zarówno z i bez szablonu klasy COM.</span><span class="sxs-lookup"><span data-stu-id="b4b90-106">This walkthrough demonstrates how to use Visual Basic to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="b4b90-107">Najprostszym sposobem udostępnienia obiektów COM jest przy użyciu szablonu klasy COM.</span><span class="sxs-lookup"><span data-stu-id="b4b90-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="b4b90-108">Szablon klasy COM tworzy nową klasę, a następnie konfiguruje projekt, aby wygenerować klasę i współdziałanie warstwy jako obiekt COM i zarejestruj je przy użyciu systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b4b90-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4b90-109">Chociaż można także udostępnić klasy utworzone w języku Visual Basic jako obiekt COM dla niezarządzanego kodu do użycia, nie jest obiektem COM wartość true i nie można użyć w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b4b90-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="b4b90-110">Aby uzyskać więcej informacji, zobacz [współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="b4b90-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="b4b90-111">Aby utworzyć obiekt COM za pomocą szablonu klasy modelu COM</span><span class="sxs-lookup"><span data-stu-id="b4b90-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="b4b90-112">Otwórz nowy projekt aplikacji Windows z **pliku** menu, klikając **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="b4b90-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="b4b90-113">W **nowy projekt** okno dialogowe, w obszarze **typów projektów** pola, należy sprawdzić, czy wybrano Windows.</span><span class="sxs-lookup"><span data-stu-id="b4b90-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="b4b90-114">Wybierz **biblioteki klas** z **szablony** listy, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4b90-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="b4b90-115">Zostanie wyświetlony nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="b4b90-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="b4b90-116">Wybierz **Dodaj nowy element** z **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="b4b90-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="b4b90-117">**Dodaj nowy element** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b4b90-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="b4b90-118">Wybierz **klasa COM —** z **szablony** listy, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="b4b90-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="b4b90-119">Visual Basic dodaje nową klasę i konfiguruje nowy projekt dla współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="b4b90-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="b4b90-120">Dodaj kod, takie jak właściwości, metody i zdarzenia do klasy COM.</span><span class="sxs-lookup"><span data-stu-id="b4b90-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="b4b90-121">Wybierz **kompilacji ClassLibrary1** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="b4b90-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="b4b90-122">Visual Basic kompilacji zestawu i rejestruje obiekt COM w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="b4b90-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="b4b90-123">Tworzenie obiektów COM bez szablonu klasy modelu COM</span><span class="sxs-lookup"><span data-stu-id="b4b90-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="b4b90-124">Można również utworzyć klasę modelu COM ręcznie, zamiast używać szablonu klasy COM.</span><span class="sxs-lookup"><span data-stu-id="b4b90-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="b4b90-125">Ta procedura jest pomocna podczas pracy z poziomu wiersza polecenia, lub gdy chcesz mieć większą kontrolę nad jak obiekty COM są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="b4b90-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="b4b90-126">Aby skonfigurować projekt do wygenerowania obiektów COM</span><span class="sxs-lookup"><span data-stu-id="b4b90-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="b4b90-127">Otwórz nowy projekt aplikacji Windows z **pliku** menu, klikając **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="b4b90-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="b4b90-128">W **nowy projekt** okno dialogowe, w obszarze **typów projektów** pola, należy sprawdzić, czy wybrano Windows.</span><span class="sxs-lookup"><span data-stu-id="b4b90-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="b4b90-129">Wybierz **biblioteki klas** z **szablony** listy, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4b90-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="b4b90-130">Zostanie wyświetlony nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="b4b90-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="b4b90-131">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b4b90-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="b4b90-132">**Projektanta projektu** jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="b4b90-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="b4b90-133">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="b4b90-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="b4b90-134">Wybierz **Zarejestruj dla współdziałania COM** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="b4b90-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="b4b90-135">Aby skonfigurować kod w swojej klasie, można utworzyć obiektu COM</span><span class="sxs-lookup"><span data-stu-id="b4b90-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="b4b90-136">W **Eksploratora rozwiązań**, kliknij dwukrotnie **Class1.vb** do wyświetlenia jego kodu.</span><span class="sxs-lookup"><span data-stu-id="b4b90-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="b4b90-137">Zmień nazwę klasy, która ma `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="b4b90-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="b4b90-138">Dodaj następujące stałe do `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="b4b90-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="b4b90-139">Będą one przechowywane w stałych Unikatowy identyfikator globalny (GUID), które obiekty COM są wymagane do.</span><span class="sxs-lookup"><span data-stu-id="b4b90-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="b4b90-140">Na **narzędzia** menu, kliknij przycisk **Utwórz Guid**.</span><span class="sxs-lookup"><span data-stu-id="b4b90-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="b4b90-141">W **Utwórz GUID** okno dialogowe, kliknij przycisk **Format rejestru** a następnie kliknij przycisk **kopiowania**.</span><span class="sxs-lookup"><span data-stu-id="b4b90-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="b4b90-142">Kliknij przycisk **zakończenia**.</span><span class="sxs-lookup"><span data-stu-id="b4b90-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="b4b90-143">Zastąp ciąg pusty dla `ClassId` przy użyciu identyfikatora GUID, nawiasy klamrowe usuwanie wiodące i końcowe.</span><span class="sxs-lookup"><span data-stu-id="b4b90-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="b4b90-144">Na przykład, jeśli identyfikator GUID udostępnione przez Guidgen jest `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , a następnie kod powinien wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="b4b90-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="b4b90-145">Powtórz poprzednie kroki dla `InterfaceId` i `EventsId` stałych, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b4b90-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    >  <span data-ttu-id="b4b90-146">Upewnij się, że identyfikator GUID w faktycznej nowych i unikatowych; w przeciwnym razie składnika COM mogą powodować konflikt z innymi składnikami COM.</span><span class="sxs-lookup"><span data-stu-id="b4b90-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="b4b90-147">Dodaj `ComClass` atrybutu `ComClass1`, określając identyfikatorów GUID dla Identyfikatora klasy, identyfikator interfejsu i identyfikator zdarzenia, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b4b90-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="b4b90-148">Klasy COM musi mieć bez parametrów `Public Sub New()` konstruktora lub klasa nie zarejestruje poprawnie.</span><span class="sxs-lookup"><span data-stu-id="b4b90-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="b4b90-149">Dodaj konstruktor bez parametrów do klasy:</span><span class="sxs-lookup"><span data-stu-id="b4b90-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="b4b90-150">Dodaj do klasy, kończy go za pomocą właściwości, metody i zdarzenia `End Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b4b90-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="b4b90-151">Wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="b4b90-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="b4b90-152">Visual Basic kompilacji zestawu i rejestruje obiekt COM w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="b4b90-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4b90-153">Nie można użyć obiektów COM, który można wygenerować za pomocą Visual Basic przez inne aplikacje w języku Visual Basic, ponieważ nie mają wartość true, obiekty COM.</span><span class="sxs-lookup"><span data-stu-id="b4b90-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="b4b90-154">Próby dodania odwołania do tych obiektów COM zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="b4b90-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="b4b90-155">Aby uzyskać więcej informacji, zobacz [współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="b4b90-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b90-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4b90-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="b4b90-157">Usługa międzyoperacyjna modelu COM</span><span class="sxs-lookup"><span data-stu-id="b4b90-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="b4b90-158">Przewodnik: implementowanie dziedziczenia z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="b4b90-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="b4b90-159">#Region, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="b4b90-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="b4b90-160">Współdziałanie COM w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4b90-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="b4b90-161">Rozwiązywanie problemów związanych z współdziałaniem</span><span class="sxs-lookup"><span data-stu-id="b4b90-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
