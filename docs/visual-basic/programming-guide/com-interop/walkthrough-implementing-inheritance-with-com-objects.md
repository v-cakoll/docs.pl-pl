---
title: 'Przewodnik: Implementowanie dziedziczenia z obiektami COM'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: bdb891e1a150f0d7b79aefcc3db1f18dc8e84be4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396730"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="d29e3-102">Wskazówki: wdrażanie dziedziczenia z obiektami COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d29e3-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>

<span data-ttu-id="d29e3-103">Klasy Visual Basic można `Public` tworzyć z klas obiektów com, nawet tych, które zostały utworzone we wcześniejszych wersjach Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d29e3-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="d29e3-104">Właściwości i metody klasy dziedziczone z obiektów COM można przesłaniać lub przeciążać tylko wtedy, gdy właściwości i metody dowolnej innej klasy bazowej mogą zostać zastąpione lub przeciążone.</span><span class="sxs-lookup"><span data-stu-id="d29e3-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="d29e3-105">Dziedziczenie z obiektów COM jest przydatne, gdy masz istniejącą bibliotekę klas, której nie chcesz ponownie skompilować.</span><span class="sxs-lookup"><span data-stu-id="d29e3-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>

<span data-ttu-id="d29e3-106">Poniższa procedura pokazuje, jak używać Visual Basic 6,0 do tworzenia obiektu COM, który zawiera klasę, a następnie używać jej jako klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="d29e3-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="d29e3-107">Aby skompilować obiekt COM, który jest używany w tym instruktażu</span><span class="sxs-lookup"><span data-stu-id="d29e3-107">To build the COM object that is used in this walkthrough</span></span>

1. <span data-ttu-id="d29e3-108">W Visual Basic 6,0 Otwórz nowy projekt biblioteki DLL ActiveX.</span><span class="sxs-lookup"><span data-stu-id="d29e3-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="d29e3-109">Projekt o nazwie `Project1` jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="d29e3-109">A project named `Project1` is created.</span></span> <span data-ttu-id="d29e3-110">Ma klasę o nazwie `Class1` .</span><span class="sxs-lookup"><span data-stu-id="d29e3-110">It has a class named `Class1`.</span></span>

2. <span data-ttu-id="d29e3-111">W **Eksploratorze projektów**kliknij prawym przyciskiem myszy pozycję **Project1**, a następnie kliknij pozycję **Właściwości Project1**.</span><span class="sxs-lookup"><span data-stu-id="d29e3-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="d29e3-112">Zostanie wyświetlone okno dialogowe **właściwości projektu** .</span><span class="sxs-lookup"><span data-stu-id="d29e3-112">The **Project Properties** dialog box is displayed.</span></span>

3. <span data-ttu-id="d29e3-113">Na karcie **Ogólne** okna dialogowego **właściwości projektu** Zmień nazwę projektu, wpisując `ComObject1` w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="d29e3-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>

4. <span data-ttu-id="d29e3-114">W **Eksploratorze projektów**kliknij prawym przyciskiem myszy `Class1` , a następnie kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d29e3-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="d29e3-115">Zostanie wyświetlone okno **Właściwości** klasy.</span><span class="sxs-lookup"><span data-stu-id="d29e3-115">The **Properties** window for the class is displayed.</span></span>

5. <span data-ttu-id="d29e3-116">Zmień wartość `Name` właściwości na `MathFunctions` .</span><span class="sxs-lookup"><span data-stu-id="d29e3-116">Change the `Name` property to `MathFunctions`.</span></span>

6. <span data-ttu-id="d29e3-117">W **Eksploratorze projektów**kliknij prawym przyciskiem myszy `MathFunctions` , a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="d29e3-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="d29e3-118">Zostanie wyświetlony **Edytor kodu** .</span><span class="sxs-lookup"><span data-stu-id="d29e3-118">The **Code Editor** is displayed.</span></span>

7. <span data-ttu-id="d29e3-119">Dodaj zmienną lokalną, aby pomieścić wartość właściwości:</span><span class="sxs-lookup"><span data-stu-id="d29e3-119">Add a local variable to hold the property value:</span></span>

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. <span data-ttu-id="d29e3-120">Dodaj właściwości `Let` i `Get` procedury właściwości właściwości:</span><span class="sxs-lookup"><span data-stu-id="d29e3-120">Add Property `Let` and Property `Get` property procedures:</span></span>

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. <span data-ttu-id="d29e3-121">Dodaj funkcję:</span><span class="sxs-lookup"><span data-stu-id="d29e3-121">Add a function:</span></span>

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. <span data-ttu-id="d29e3-122">Utwórz i zarejestruj obiekt COM, klikając pozycję **Utwórz ComObject1. dll** w menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="d29e3-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d29e3-123">Chociaż można również uwidocznić klasę utworzoną za pomocą Visual Basic jako obiekt COM, nie jest to prawdziwy obiekt COM i nie można jej użyć w tym instruktażu.</span><span class="sxs-lookup"><span data-stu-id="d29e3-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="d29e3-124">Aby uzyskać szczegółowe informacje, zobacz [współdziałanie com w aplikacjach .NET Framework](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="d29e3-124">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>

## <a name="interop-assemblies"></a><span data-ttu-id="d29e3-125">Zestawy międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="d29e3-125">Interop Assemblies</span></span>

<span data-ttu-id="d29e3-126">Poniższa procedura polega na utworzeniu zestawu międzyoperacyjnego, który działa jako Most między kodem niezarządzanym (takim jak obiekt COM) i zarządzanym przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d29e3-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="d29e3-127">Zestaw międzyoperacyjny, który Visual Basic tworzy obsługę wielu szczegółów pracy z obiektami COM, takimi jak *organizowanie międzyoperacyjności*, proces pakowania parametrów i zwracanie wartości na równoważne typy danych podczas przenoszenia ich do i z obiektów com.</span><span class="sxs-lookup"><span data-stu-id="d29e3-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="d29e3-128">Odwołanie w Visual Basic wskazuje zestaw międzyoperacyjny, a nie rzeczywisty obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="d29e3-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="d29e3-129">Aby użyć obiektu COM z Visual Basic 2005 i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="d29e3-129">To use a COM object with Visual Basic 2005 and later versions</span></span>

1. <span data-ttu-id="d29e3-130">Otwórz nowy projekt aplikacji Visual Basic systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d29e3-130">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="d29e3-131">W menu **projekt** kliknij polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d29e3-131">On the **Project** menu, click **Add Reference**.</span></span>

     <span data-ttu-id="d29e3-132">Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="d29e3-132">The **Add Reference** dialog box is displayed.</span></span>

3. <span data-ttu-id="d29e3-133">Na karcie **com** kliknij dwukrotnie `ComObject1` na liście **Nazwa składnika** , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d29e3-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>

4. <span data-ttu-id="d29e3-134">W menu **projekt** kliknij polecenie **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d29e3-134">On the **Project** menu, click **Add New Item**.</span></span>

     <span data-ttu-id="d29e3-135">Zostanie wyświetlone okno dialogowe **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="d29e3-135">The **Add New Item** dialog box is displayed.</span></span>

5. <span data-ttu-id="d29e3-136">W okienku **Szablony** kliknij pozycję **Klasa**.</span><span class="sxs-lookup"><span data-stu-id="d29e3-136">In the **Templates** pane, click **Class**.</span></span>

     <span data-ttu-id="d29e3-137">Domyślna nazwa pliku, `Class1.vb` ,, pojawia się w polu **Nazwa** .</span><span class="sxs-lookup"><span data-stu-id="d29e3-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="d29e3-138">Zmień to pole na MathClass. vb i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d29e3-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="d29e3-139">Spowoduje to utworzenie klasy o nazwie `MathClass` i wyświetlenie jej kodu.</span><span class="sxs-lookup"><span data-stu-id="d29e3-139">This creates a class named `MathClass`, and displays its code.</span></span>

6. <span data-ttu-id="d29e3-140">Dodaj następujący kod na początku, `MathClass` Aby dziedziczyć z klasy com.</span><span class="sxs-lookup"><span data-stu-id="d29e3-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. <span data-ttu-id="d29e3-141">Przeciążać publiczną metodę klasy bazowej, dodając następujący kod do `MathClass` :</span><span class="sxs-lookup"><span data-stu-id="d29e3-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. <span data-ttu-id="d29e3-142">Poszerzenie dziedziczonej klasy przez dodanie następującego kodu do `MathClass` :</span><span class="sxs-lookup"><span data-stu-id="d29e3-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

<span data-ttu-id="d29e3-143">Nowa klasa dziedziczy właściwości klasy podstawowej w obiekcie COM, przeciążuje metodę i definiuje nową metodę, aby zwiększyć klasę.</span><span class="sxs-lookup"><span data-stu-id="d29e3-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>

### <a name="to-test-the-inherited-class"></a><span data-ttu-id="d29e3-144">Aby przetestować dziedziczonej klasy</span><span class="sxs-lookup"><span data-stu-id="d29e3-144">To test the inherited class</span></span>

1. <span data-ttu-id="d29e3-145">Dodaj przycisk do formularza startowego, a następnie kliknij go dwukrotnie, aby wyświetlić jego kod.</span><span class="sxs-lookup"><span data-stu-id="d29e3-145">Add a button to your startup form, and then double-click it to view its code.</span></span>

2. <span data-ttu-id="d29e3-146">W `Click` procedurze obsługi zdarzeń przycisku Dodaj następujący kod, aby utworzyć wystąpienie `MathClass` i wywołać przeciążone metody:</span><span class="sxs-lookup"><span data-stu-id="d29e3-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. <span data-ttu-id="d29e3-147">Uruchom projekt, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="d29e3-147">Run the project by pressing F5.</span></span>

<span data-ttu-id="d29e3-148">Po kliknięciu przycisku w formularzu `AddNumbers` Metoda jest najpierw wywoływana z `Short` liczbami typu danych, a Visual Basic wybiera odpowiednią metodę z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="d29e3-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="d29e3-149">Drugie wywołanie `AddNumbers` jest kierowane do metody przeciążenia z `MathClass` .</span><span class="sxs-lookup"><span data-stu-id="d29e3-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="d29e3-150">Trzecie wywołanie wywołuje `SubtractNumbers` metodę, która rozszerza klasę.</span><span class="sxs-lookup"><span data-stu-id="d29e3-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="d29e3-151">Właściwość w klasie bazowej jest ustawiona i zostanie wyświetlona wartość.</span><span class="sxs-lookup"><span data-stu-id="d29e3-151">The property in the base class is set, and the value is displayed.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d29e3-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d29e3-152">Next Steps</span></span>

<span data-ttu-id="d29e3-153">Być może zauważono, że przeciążona `AddNumbers` Funkcja wydaje się mieć ten sam typ danych co Metoda dziedziczona z klasy podstawowej obiektu com.</span><span class="sxs-lookup"><span data-stu-id="d29e3-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="d29e3-154">Wynika to z faktu, że argumenty i parametry metody klasy bazowej są zdefiniowane jako 16-bitowe liczby całkowite w Visual Basic 6,0, ale są one widoczne jako 16-bitowe liczby całkowite typu `Short` w nowszych wersjach Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d29e3-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="d29e3-155">Nowa funkcja akceptuje 32-bitowe liczby całkowite i przeciążać funkcję klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="d29e3-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>

<span data-ttu-id="d29e3-156">Podczas pracy z obiektami COM upewnij się, że sprawdzane są rozmiary i typy danych parametrów.</span><span class="sxs-lookup"><span data-stu-id="d29e3-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="d29e3-157">Na przykład podczas korzystania z obiektu COM, który akceptuje obiekt kolekcji Visual Basic 6,0 jako argument, nie można dostarczyć kolekcji z nowszej wersji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d29e3-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>

<span data-ttu-id="d29e3-158">Właściwości i metody dziedziczone z klas COM można przesłonić, co oznacza, że można zadeklarować lokalną właściwość lub metodę zastępującą właściwość lub metodę dziedziczoną z klasy podstawowej modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d29e3-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="d29e3-159">Reguły przesłaniania dziedziczonych właściwości COM są podobne do reguł zastępowania innych właściwości i metod z następującymi wyjątkami:</span><span class="sxs-lookup"><span data-stu-id="d29e3-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>

- <span data-ttu-id="d29e3-160">W przypadku zastąpienia dowolnej właściwości lub metody odziedziczonej z klasy COM należy zastąpić wszystkie inne dziedziczone właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="d29e3-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>

- <span data-ttu-id="d29e3-161">Właściwości używające `ByRef` parametrów nie mogą być zastępowane.</span><span class="sxs-lookup"><span data-stu-id="d29e3-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>

## <a name="see-also"></a><span data-ttu-id="d29e3-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d29e3-162">See also</span></span>

- [<span data-ttu-id="d29e3-163">Współdziałanie COM w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d29e3-163">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="d29e3-164">Inherits — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="d29e3-164">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="d29e3-165">Short, typ danych</span><span class="sxs-lookup"><span data-stu-id="d29e3-165">Short Data Type</span></span>](../../language-reference/data-types/short-data-type.md)
