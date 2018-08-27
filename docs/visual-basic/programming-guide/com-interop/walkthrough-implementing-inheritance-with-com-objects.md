---
title: 'Wskazówki: wdrażanie dziedziczenia z obiektami COM (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: a1c1b7c247d3277c6614a4774395650c4c069c2f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930001"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="8bd1c-102">Wskazówki: wdrażanie dziedziczenia z obiektami COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bd1c-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="8bd1c-103">Utworzeniu klasy pochodnej klasy Visual Basic z `Public` klas obiektów COM, nawet te, utworzone we wcześniejszych wersjach programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="8bd1c-104">Właściwości i metody klasy dziedziczone z obiektów COM mogą być zastąpione lub przeciążone, podobnie jak właściwości i metody inne klasy bazowej można zastąpić lub przeciążone.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="8bd1c-105">Dziedziczenie z obiektami COM jest przydatne, jeśli masz istniejące biblioteki klas, które nie chcesz ponownie skompilować.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="8bd1c-106">Poniższa procedura pokazuje, jak używać języka Visual Basic 6.0 do tworzenia obiektów COM, który zawiera klasę, a następnie użyć go jako klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="8bd1c-107">Aby zbudować obiekt COM, który jest używany w tym przewodniku</span><span class="sxs-lookup"><span data-stu-id="8bd1c-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="8bd1c-108">W Visual Basic 6.0 otwórz nowy projekt ActiveX DLL.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="8bd1c-109">Projekt o nazwie `Project1` zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-109">A project named `Project1` is created.</span></span> <span data-ttu-id="8bd1c-110">Ma ona klasę o nazwie `Class1`.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="8bd1c-111">W **Eksplorator projektów**, kliknij prawym przyciskiem myszy **projektu Project1**, a następnie kliknij przycisk **właściwości projektu Project1**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="8bd1c-112">**Właściwości projektu** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="8bd1c-113">Na **ogólne** karcie **właściwości projektu** okno dialogowe Zmień nazwę projektu, wpisując `ComObject1` w **Nazwa projektu** pola.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="8bd1c-114">W **Eksplorator projektów**, kliknij prawym przyciskiem myszy `Class1`, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="8bd1c-115">**Właściwości** zostanie wyświetlone okno dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="8bd1c-116">Zmiana `Name` właściwość `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="8bd1c-117">W **Eksplorator projektów**, kliknij prawym przyciskiem myszy `MathFunctions`, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="8bd1c-118">**Edytor kodu** jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="8bd1c-119">Dodaj zmienną lokalną, do przechowywania wartości właściwości:</span><span class="sxs-lookup"><span data-stu-id="8bd1c-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="8bd1c-120">Dodaj właściwość `Let` i właściwość `Get` procedury właściwości:</span><span class="sxs-lookup"><span data-stu-id="8bd1c-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. <span data-ttu-id="8bd1c-121">Dodawanie funkcji:</span><span class="sxs-lookup"><span data-stu-id="8bd1c-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="8bd1c-122">Utwórz i zarejestruj obiekt COM, klikając **wprowadzić ComObject1.dll** na **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8bd1c-123">Chociaż można także udostępnić klasy utworzonej za pomocą Visual Basic jako obiekt COM, nie jest obiektem COM wartość true, a nie może być używana w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="8bd1c-124">Aby uzyskać więcej informacji, zobacz [współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="8bd1c-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="8bd1c-125">Zestawy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="8bd1c-125">Interop Assemblies</span></span>  
 <span data-ttu-id="8bd1c-126">W poniższej procedurze utworzysz zestawu międzyoperacyjnego, który działa jako Most między kodem niezarządzanym (np. obiekt COM) i kod zarządzany, który korzysta z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="8bd1c-127">Zestawu międzyoperacyjnego, który tworzy języka Visual Basic obsługuje wiele szczegółów pracy z obiektami COM, takich jak *marshaling międzyoperacyjny*, proces tworzenia pakietów parametrów i zwracanych wartości danych równoważne typy przechodzące do a obiekty COM.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="8bd1c-128">W aplikacji Visual Basic wskazuje odwołanie do zestawu międzyoperacyjnego nie rzeczywistego obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="8bd1c-129">Obiekt COM za pomocą programu Visual Basic 2005 i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="8bd1c-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="8bd1c-130">Otwórz nowy projekt aplikacji Windows Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-130">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="8bd1c-131">Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="8bd1c-132">**Dodaj odwołanie** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="8bd1c-133">Na **COM** kartę, kliknij dwukrotnie `ComObject1` w **nazwa składnika** listy, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="8bd1c-134">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="8bd1c-135">**Dodaj nowy element** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="8bd1c-136">W **szablony** okienku kliknij **klasy**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="8bd1c-137">Domyślna nazwa pliku `Class1.vb`, pojawia się w **nazwa** pola.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="8bd1c-138">Zmień to pole na MathClass.vb, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="8bd1c-139">Spowoduje to utworzenie klasę o nazwie `MathClass`i wyświetla jego kod.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="8bd1c-140">Dodaj następujący kod na górze `MathClass` dziedziczyć z klasy COM.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  <span data-ttu-id="8bd1c-141">Przeciążenia metody publiczne klasy bazowej, dodając następujący kod do `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="8bd1c-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  <span data-ttu-id="8bd1c-142">Rozszerzanie odziedziczoną klasę, dodając następujący kod do `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="8bd1c-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 <span data-ttu-id="8bd1c-143">Nowa klasa dziedziczy właściwości klasy bazowej w obiekcie COM, przeciążenia metody i definiuje nową metodę rozszerzenia klasy.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="8bd1c-144">Aby przetestować odziedziczoną klasę</span><span class="sxs-lookup"><span data-stu-id="8bd1c-144">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="8bd1c-145">Dodawanie przycisku do uruchamiania formularza, a następnie go dwukrotnie, aby wyświetlić jej kod.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="8bd1c-146">W przycisku `Click` procedury obsługi zdarzeń, Dodaj następujący kod, aby utworzyć wystąpienie `MathClass` i wywołania przeciążonych metod:</span><span class="sxs-lookup"><span data-stu-id="8bd1c-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  <span data-ttu-id="8bd1c-147">Uruchom projekt, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="8bd1c-148">Po kliknięciu przycisku w formularzu `AddNumbers` metoda najpierw jest wywoływana z `Short` liczb, typ danych i Visual Basic wybiera odpowiednią metodę z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="8bd1c-149">Drugie wywołanie `AddNumbers` zostaje skierowany do przeciążenia metody z `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="8bd1c-150">Trzecie wywołanie wywołania `SubtractNumbers` metody, która rozszerza klasę.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="8bd1c-151">Ustawiono właściwość w klasie bazowej, a wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8bd1c-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8bd1c-152">Next Steps</span></span>  
 <span data-ttu-id="8bd1c-153">Być może zauważono, że przeciążone `AddNumbers` funkcja wydaje się mieć taki sam typ jako metody dziedziczone z klasy bazowej obiektu COM danych.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="8bd1c-154">Jest to spowodowane argumentów i parametrów metody klasy bazowej są definiowane jako 16-bitowych liczb całkowitych w języku Visual Basic 6.0, ale są one widoczne jako 16-bitowych liczb całkowitych typu `Short` w nowszych wersjach programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="8bd1c-155">Nowa funkcja akceptuje 32-bitowych liczb całkowitych i przeciążenia funkcji klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="8bd1c-156">Podczas pracy z obiektami COM, upewnij się, że należy sprawdzić, rozmiar i typy danych parametrów.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="8bd1c-157">Na przykład korzystając z obiektu COM, który akceptuje jako argument obiektu kolekcji Visual Basic 6.0, nie może dostarczyć kolekcji z nowszej wersji programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="8bd1c-158">Właściwości i metody dziedziczone z klasy COM można przesłonić, co oznacza, że można zadeklarować lokalnego właściwości lub metody, która zastępuje właściwość lub dziedziczone z klasy bazowej COM.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="8bd1c-159">Reguły zastępowania dziedziczonych właściwości modelu COM są podobne do reguł zastępowanie innych właściwości i metod z następującymi wyjątkami:</span><span class="sxs-lookup"><span data-stu-id="8bd1c-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="8bd1c-160">Jeśli zastąpisz każda właściwość lub metoda odziedziczoną z klasy COM muszą przesłaniać wszystkie odziedziczone właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="8bd1c-161">Właściwości, które używają `ByRef` parametrów nie może być zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="8bd1c-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd1c-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bd1c-162">See Also</span></span>  
 [<span data-ttu-id="8bd1c-163">Współdziałanie COM w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8bd1c-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="8bd1c-164">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8bd1c-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="8bd1c-165">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="8bd1c-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
