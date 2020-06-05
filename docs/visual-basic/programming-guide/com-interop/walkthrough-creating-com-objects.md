---
title: 'Przewodnik: Tworzenie obiektów COM'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: bb312317b2bbcb77bed9e3966db6d9fd5db79e4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396743"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="7ca49-102">Wskazówki: tworzenie obiektów COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ca49-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="7ca49-103">Podczas tworzenia nowych aplikacji lub składników najlepiej utworzyć zestawy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7ca49-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="7ca49-104">Jednak Visual Basic ułatwiają również uwidocznienie składnika .NET Framework w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="7ca49-105">Pozwala to udostępnić nowe składniki dla wcześniejszych zestawów aplikacji, które wymagają składników COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="7ca49-106">W tym instruktażu pokazano, jak za pomocą Visual Basic uwidocznić obiekty .NET Framework jako obiekty COM, zarówno z szablonem klasy COM, jak i bez niego.</span><span class="sxs-lookup"><span data-stu-id="7ca49-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="7ca49-107">Najprostszym sposobem uwidocznienia obiektów COM jest użycie szablonu klasy COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="7ca49-108">Szablon klasy COM tworzy nową klasę, a następnie konfiguruje projekt w celu wygenerowania warstwy i współdziałania jako obiektu COM i zarejestrowania go w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="7ca49-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ca49-109">Chociaż można również uwidocznić klasę utworzoną w Visual Basic jako obiekt COM dla niezarządzanego kodu do użycia, nie jest to prawdziwy obiekt COM i nie może być używany przez Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7ca49-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="7ca49-110">Aby uzyskać więcej informacji, zobacz [współdziałanie com w aplikacjach .NET Framework](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="7ca49-110">For more information, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="7ca49-111">Aby utworzyć obiekt COM przy użyciu szablonu klasy COM</span><span class="sxs-lookup"><span data-stu-id="7ca49-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="7ca49-112">Otwórz nowy projekt aplikacji systemu Windows z menu **plik** , klikając pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="7ca49-113">W oknie dialogowym **Nowy projekt** w polu **typy projektu** Sprawdź, czy jest wybrany system Windows.</span><span class="sxs-lookup"><span data-stu-id="7ca49-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="7ca49-114">Na liście **Szablony** wybierz pozycję **Biblioteka klas** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="7ca49-115">Zostanie wyświetlony nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="7ca49-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="7ca49-116">Wybierz pozycję **Dodaj nowy element** z menu **projekt** .</span><span class="sxs-lookup"><span data-stu-id="7ca49-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="7ca49-117">Zostanie wyświetlone okno dialogowe **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="7ca49-118">Z listy **Szablony** wybierz pozycję **Klasa com** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="7ca49-119">Visual Basic dodaje nową klasę i konfiguruje nowy projekt dla międzyoperacyjności modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="7ca49-120">Dodaj kod, taki jak właściwości, metody i zdarzenia, do klasy COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="7ca49-121">Wybierz pozycję **kompilacja ClassLibrary1** z menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="7ca49-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="7ca49-122">Visual Basic kompiluje zestaw i rejestruje obiekt COM w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="7ca49-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="7ca49-123">Tworzenie obiektów COM bez szablonu klasy COM</span><span class="sxs-lookup"><span data-stu-id="7ca49-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="7ca49-124">Klasy COM można także utworzyć ręcznie zamiast używać szablonu klasy COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="7ca49-125">Ta procedura jest pomocna podczas pracy z wiersza polecenia lub w przypadku, gdy potrzebna jest większa kontrola nad sposobem definiowania obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="7ca49-126">Aby skonfigurować projekt do generowania obiektu COM</span><span class="sxs-lookup"><span data-stu-id="7ca49-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="7ca49-127">Otwórz nowy projekt aplikacji systemu Windows z menu **plik** , klikając pozycję **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="7ca49-128">W oknie dialogowym **Nowy projekt** w polu **typy projektu** Sprawdź, czy jest wybrany system Windows.</span><span class="sxs-lookup"><span data-stu-id="7ca49-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="7ca49-129">Na liście **Szablony** wybierz pozycję **Biblioteka klas** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="7ca49-130">Zostanie wyświetlony nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="7ca49-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="7ca49-131">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="7ca49-132">Zostanie wyświetlony **Projektant projektu** .</span><span class="sxs-lookup"><span data-stu-id="7ca49-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="7ca49-133">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="7ca49-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="7ca49-134">Zaznacz pole wyboru **Zarejestruj dla międzyoperacyjności modelu COM** .</span><span class="sxs-lookup"><span data-stu-id="7ca49-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="7ca49-135">Aby skonfigurować kod w klasie w celu utworzenia obiektu COM</span><span class="sxs-lookup"><span data-stu-id="7ca49-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="7ca49-136">W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **Class1. vb** , aby wyświetlić swój kod.</span><span class="sxs-lookup"><span data-stu-id="7ca49-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="7ca49-137">Zmień nazwę klasy na `ComClass1` .</span><span class="sxs-lookup"><span data-stu-id="7ca49-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="7ca49-138">Dodaj następujące stałe do programu `ComClass1` .</span><span class="sxs-lookup"><span data-stu-id="7ca49-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="7ca49-139">Będą one przechowywać stałe unikatowe identyfikatory (GUID), które są wymagane do posiadania obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="7ca49-140">W menu **Narzędzia** kliknij polecenie **Utwórz identyfikator GUID**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="7ca49-141">W oknie dialogowym **Tworzenie identyfikatora GUID** kliknij przycisk **Format rejestru** , a następnie kliknij przycisk **Kopiuj**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="7ca49-142">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="7ca49-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="7ca49-143">Zastąp ciąg pusty ciągiem `ClassId` z identyfikatorem GUID, usuwając wiodące i końcowe nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="7ca49-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="7ca49-144">Na przykład, jeśli identyfikator GUID podany przez Guidgen to, `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` kod powinien wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="7ca49-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="7ca49-145">Powtórz poprzednie kroki dla `InterfaceId` i `EventsId` stałych, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7ca49-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="7ca49-146">Upewnij się, że identyfikatory GUID są nowe i unikatowe; w przeciwnym razie składnik COM może powodować konflikt z innymi składnikami modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="7ca49-147">Dodaj `ComClass` atrybut do `ComClass1` , określając identyfikatory GUID identyfikatora klasy, identyfikator interfejsu i identyfikator zdarzenia, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7ca49-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="7ca49-148">Klasy COM muszą mieć konstruktora bez parametrów `Public Sub New()` lub Klasa nie zostanie poprawnie zarejestrowana.</span><span class="sxs-lookup"><span data-stu-id="7ca49-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="7ca49-149">Dodaj Konstruktor bez parametrów do klasy:</span><span class="sxs-lookup"><span data-stu-id="7ca49-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="7ca49-150">Dodaj właściwości, metody i zdarzenia do klasy, kończąc ją z `End Class` instrukcją.</span><span class="sxs-lookup"><span data-stu-id="7ca49-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="7ca49-151">Wybierz opcję **Kompiluj rozwiązanie** z menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="7ca49-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="7ca49-152">Visual Basic kompiluje zestaw i rejestruje obiekt COM w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="7ca49-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7ca49-153">Obiekty COM generowane za pomocą Visual Basic nie mogą być używane przez inne aplikacje Visual Basic, ponieważ nie są one prawdziwymi obiektami COM.</span><span class="sxs-lookup"><span data-stu-id="7ca49-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="7ca49-154">Próby dodania odwołań do takich obiektów COM spowodują wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="7ca49-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="7ca49-155">Aby uzyskać szczegółowe informacje, zobacz [współdziałanie com w aplikacjach .NET Framework](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="7ca49-155">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca49-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ca49-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="7ca49-157">Międzyoperacyjność modelu COM</span><span class="sxs-lookup"><span data-stu-id="7ca49-157">COM Interop</span></span>](index.md)
- [<span data-ttu-id="7ca49-158">Przewodnik: Implementowanie dziedziczenia z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="7ca49-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="7ca49-159">#Region — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="7ca49-159">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="7ca49-160">Współdziałanie COM w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7ca49-160">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="7ca49-161">Rozwiązywanie problemów związanych z współdziałaniem</span><span class="sxs-lookup"><span data-stu-id="7ca49-161">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
