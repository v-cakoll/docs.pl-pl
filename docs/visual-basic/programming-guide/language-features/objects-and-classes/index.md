---
title: Obiekty i klasy
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 10e257a1cbc8778565a9838aeef423522f9d2970
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290619"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="75e06-102">Obiekty i klasy w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75e06-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="75e06-103">*Obiekt* jest kombinacją kodu i danych, który może być traktowany jako jednostka.</span><span class="sxs-lookup"><span data-stu-id="75e06-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="75e06-104">Obiekt może być częścią aplikacji, taką jak kontrolka lub formularz.</span><span class="sxs-lookup"><span data-stu-id="75e06-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="75e06-105">Cała aplikacja może być również obiektem.</span><span class="sxs-lookup"><span data-stu-id="75e06-105">An entire application can also be an object.</span></span>

<span data-ttu-id="75e06-106">Podczas tworzenia aplikacji w Visual Basic, pracujesz z obiektami.</span><span class="sxs-lookup"><span data-stu-id="75e06-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="75e06-107">Można używać obiektów dostarczonych przez Visual Basic, takich jak kontrolki, formularze i obiekty dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="75e06-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="75e06-108">Możesz również używać obiektów z innych aplikacji w aplikacji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="75e06-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="75e06-109">Można nawet utworzyć własne obiekty i zdefiniować dla nich dodatkowe właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="75e06-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="75e06-110">Obiekty takie jak prefabrykowane bloki konstrukcyjne dla programów — umożliwiają pisanie fragmentu kodu raz i wielokrotne używanie go.</span><span class="sxs-lookup"><span data-stu-id="75e06-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="75e06-111">W tym temacie omówiono obiekty szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="75e06-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="75e06-112">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="75e06-112">Objects and classes</span></span>

<span data-ttu-id="75e06-113">Każdy obiekt w Visual Basic jest zdefiniowany przez *klasę*.</span><span class="sxs-lookup"><span data-stu-id="75e06-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="75e06-114">Klasa opisuje zmienne, właściwości, procedury i zdarzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="75e06-115">Obiekty są wystąpieniami klas; można utworzyć dowolną liczbę obiektów, które są potrzebne po zdefiniowaniu klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="75e06-116">Aby zrozumieć relacje między obiektem a jego klasą, należy wziąć pod uwagę, że pliki cookie są odcięciami i plikami cookie.</span><span class="sxs-lookup"><span data-stu-id="75e06-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="75e06-117">Wykrajarki plik cookie jest klasą.</span><span class="sxs-lookup"><span data-stu-id="75e06-117">The cookie cutter is the class.</span></span> <span data-ttu-id="75e06-118">Definiuje on cechy poszczególnych plików cookie, na przykład rozmiar i kształt.</span><span class="sxs-lookup"><span data-stu-id="75e06-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="75e06-119">Klasa jest używana do tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="75e06-119">The class is used to create objects.</span></span> <span data-ttu-id="75e06-120">Obiekty są plikami cookie.</span><span class="sxs-lookup"><span data-stu-id="75e06-120">The objects are the cookies.</span></span>

<span data-ttu-id="75e06-121">Należy utworzyć obiekt, aby można było uzyskać dostęp do jego członków, z wyjątkiem [`Shared`](../../../language-reference/modifiers/shared.md) elementów członkowskich, do których można uzyskać dostęp bez obiektu klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-121">You must create an object before you can access its members, except for [`Shared`](../../../language-reference/modifiers/shared.md) members which can be accessed without an object of the class.</span></span>

### <a name="create-an-object-from-a-class"></a><span data-ttu-id="75e06-122">Utwórz obiekt z klasy</span><span class="sxs-lookup"><span data-stu-id="75e06-122">Create an object from a class</span></span>

1. <span data-ttu-id="75e06-123">Ustal, z której klasy chcesz utworzyć obiekt, lub Zdefiniuj własną klasę.</span><span class="sxs-lookup"><span data-stu-id="75e06-123">Determine from which class you want to create an object, or define your own class.</span></span> <span data-ttu-id="75e06-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="75e06-124">For example:</span></span>

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. <span data-ttu-id="75e06-125">Napisz [instrukcję Dim](../../../language-reference/statements/dim-statement.md) , aby utworzyć zmienną, do której można przypisać wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-125">Write a [Dim Statement](../../../language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="75e06-126">Zmienna powinna być typu żądanej klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-126">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As Customer
   ```

3. <span data-ttu-id="75e06-127">Dodaj słowo kluczowe [new operatora](../../../language-reference/operators/new-operator.md) , aby zainicjować zmienną do nowego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-127">Add the [New Operator](../../../language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New Customer
   ```

4. <span data-ttu-id="75e06-128">Teraz możesz uzyskiwać dostęp do elementów członkowskich klasy za pomocą zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-128">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="75e06-129">Jeśli to możliwe, należy zadeklarować zmienną jako typ klasy, która ma zostać przypisana do niej.</span><span class="sxs-lookup"><span data-stu-id="75e06-129">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="75e06-130">Nazywa się to *wczesnym wiązaniem*.</span><span class="sxs-lookup"><span data-stu-id="75e06-130">This is called *early binding*.</span></span> <span data-ttu-id="75e06-131">Jeśli nie znasz typu klasy w czasie kompilacji, możesz wywołać *późne wiązanie* przez zadeklarowanie zmiennej jako [typu danych obiektu](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="75e06-131">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="75e06-132">Jednak późne wiązanie może zwiększyć wydajność i ograniczyć dostęp do elementów członkowskich obiektu czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="75e06-132">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="75e06-133">Aby uzyskać więcej informacji, zobacz [Deklaracja zmiennej obiektu](../variables/object-variable-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="75e06-133">For more information, see [Object Variable Declaration](../variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="75e06-134">Wiele wystąpień</span><span class="sxs-lookup"><span data-stu-id="75e06-134">Multiple instances</span></span>

<span data-ttu-id="75e06-135">Obiekty nowo utworzone na podstawie klasy są często takie same.</span><span class="sxs-lookup"><span data-stu-id="75e06-135">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="75e06-136">Gdy istnieją one jako pojedyncze obiekty, można jednak zmienić ich zmienne i właściwości niezależnie od innych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="75e06-136">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="75e06-137">Na przykład jeśli dodasz trzy pola wyboru do formularza, każdy obiekt pola wyboru jest wystąpieniem <xref:System.Windows.Forms.CheckBox> klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-137">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="75e06-138">Poszczególne <xref:System.Windows.Forms.CheckBox> obiekty mają wspólny zestaw cech i funkcji (właściwości, zmienne, procedury i zdarzenia) zdefiniowane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="75e06-138">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="75e06-139">Jednak każda z nich ma własną nazwę, może być oddzielnie włączona i wyłączona i może być umieszczona w innej lokalizacji w formularzu.</span><span class="sxs-lookup"><span data-stu-id="75e06-139">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="75e06-140">Elementy członkowskie obiektów</span><span class="sxs-lookup"><span data-stu-id="75e06-140">Object members</span></span>

<span data-ttu-id="75e06-141">Obiekt jest elementem aplikacji, reprezentującym *wystąpienie* klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-141">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="75e06-142">Pola, właściwości, metody i zdarzenia są blokami konstrukcyjnymi obiektów i stanowią ich *składowe*.</span><span class="sxs-lookup"><span data-stu-id="75e06-142">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="75e06-143">Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="75e06-143">Member Access</span></span>

<span data-ttu-id="75e06-144">Użytkownik uzyskuje dostęp do elementu członkowskiego obiektu przez określenie w kolejności nazwy zmiennej obiektu, kropki ( `.` ) i nazwy elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="75e06-144">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="75e06-145">Poniższy przykład ustawia <xref:System.Windows.Forms.Control.Text%2A> Właściwość <xref:System.Windows.Forms.Label> obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-145">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="75e06-146">Lista elementów członkowskich IntelliSense</span><span class="sxs-lookup"><span data-stu-id="75e06-146">IntelliSense listing of members</span></span>

<span data-ttu-id="75e06-147">Funkcja IntelliSense wyświetla listę elementów członkowskich klasy po wywołaniu opcji członków listy, na przykład podczas wpisywania kropki ( `.` ) jako operatora dostępu do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="75e06-147">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="75e06-148">Jeśli wpiszesz kropkę po nazwie zmiennej zadeklarowanej jako wystąpienie tej klasy, IntelliSense wyświetla wszystkie elementy członkowskie wystąpienia i żaden z udostępnionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="75e06-148">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="75e06-149">Jeśli wpiszesz kropkę po samej nazwie klasy, IntelliSense wyświetla wszystkie udostępnione elementy członkowskie i żaden z elementów członkowskich wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="75e06-149">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="75e06-150">Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="75e06-150">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="75e06-151">Pola i właściwości</span><span class="sxs-lookup"><span data-stu-id="75e06-151">Fields and properties</span></span>

<span data-ttu-id="75e06-152">*Pola* i *Właściwości* reprezentują informacje przechowywane w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="75e06-152">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="75e06-153">Pobieranie i ustawianie wartości przy użyciu instrukcji przypisania w taki sam sposób, jak pobieranie i Ustawianie zmiennych lokalnych w procedurze.</span><span class="sxs-lookup"><span data-stu-id="75e06-153">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="75e06-154">Poniższy przykład pobiera <xref:System.Windows.Forms.Control.Width%2A> Właściwość i ustawia <xref:System.Windows.Forms.Control.ForeColor%2A> Właściwość <xref:System.Windows.Forms.Label> obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-154">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="75e06-155">Należy zauważyć, że pole jest również nazywane *zmienną członkowską*.</span><span class="sxs-lookup"><span data-stu-id="75e06-155">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="75e06-156">Użyj procedur właściwości, gdy:</span><span class="sxs-lookup"><span data-stu-id="75e06-156">Use property procedures when:</span></span>

- <span data-ttu-id="75e06-157">Należy określić, kiedy i w jaki sposób ma być ustawiona lub pobrana wartość.</span><span class="sxs-lookup"><span data-stu-id="75e06-157">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="75e06-158">Właściwość zawiera dobrze zdefiniowany zestaw wartości, które muszą zostać sprawdzone.</span><span class="sxs-lookup"><span data-stu-id="75e06-158">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="75e06-159">Ustawienie wartości powoduje pewne zauważalne zmiany stanu obiektu, takie jak `IsVisible` Właściwość.</span><span class="sxs-lookup"><span data-stu-id="75e06-159">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="75e06-160">Ustawienie właściwości powoduje zmianę innych zmiennych wewnętrznych lub wartości innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="75e06-160">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="75e06-161">Przed ustawieniem lub pobraniem właściwości należy wykonać zestaw kroków.</span><span class="sxs-lookup"><span data-stu-id="75e06-161">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="75e06-162">Użyj pól w przypadku:</span><span class="sxs-lookup"><span data-stu-id="75e06-162">Use fields when:</span></span>

- <span data-ttu-id="75e06-163">Wartość jest typu samowalidacji.</span><span class="sxs-lookup"><span data-stu-id="75e06-163">The value is of a self-validating type.</span></span> <span data-ttu-id="75e06-164">Na przykład błąd lub Automatyczna konwersja danych występuje, jeśli wartość inna niż `True` lub `False` jest przypisana do `Boolean` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="75e06-164">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="75e06-165">Dowolna wartość z zakresu obsługiwanego przez typ danych jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="75e06-165">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="75e06-166">Jest to prawdziwe w przypadku wielu właściwości typu `Single` lub `Double` .</span><span class="sxs-lookup"><span data-stu-id="75e06-166">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="75e06-167">Właściwość jest `String` typem danych i nie ma żadnego ograniczenia dotyczącego rozmiaru lub wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="75e06-167">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="75e06-168">Aby uzyskać więcej informacji, zobacz [procedury właściwości](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="75e06-168">For more information, see [Property Procedures](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).</span></span>

> [!TIP]
> <span data-ttu-id="75e06-169">Zawsze zachowuj prywatne pola niestałe.</span><span class="sxs-lookup"><span data-stu-id="75e06-169">Always keep the non-constant fields private.</span></span> <span data-ttu-id="75e06-170">Jeśli chcesz, aby był on publiczny, zamiast tego użyj właściwości.</span><span class="sxs-lookup"><span data-stu-id="75e06-170">When you want to make it public, use a property instead.</span></span>

### <a name="methods"></a><span data-ttu-id="75e06-171">Metody</span><span class="sxs-lookup"><span data-stu-id="75e06-171">Methods</span></span>

<span data-ttu-id="75e06-172">*Metoda* jest akcją, którą obiekt może wykonać.</span><span class="sxs-lookup"><span data-stu-id="75e06-172">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="75e06-173">Na przykład, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> jest metodą <xref:System.Windows.Forms.ComboBox> obiektu, który dodaje nowy wpis do pola kombi.</span><span class="sxs-lookup"><span data-stu-id="75e06-173">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="75e06-174">Poniższy przykład ilustruje <xref:System.Windows.Forms.Timer.Start%2A> metodę <xref:System.Windows.Forms.Timer> obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-174">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="75e06-175">Należy pamiętać, że metoda jest po prostu *procedurą* , która jest udostępniana przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="75e06-175">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="75e06-176">Aby uzyskać więcej informacji, zobacz [procedur](../procedures/index.md).</span><span class="sxs-lookup"><span data-stu-id="75e06-176">For more information, see [Procedures](../procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="75e06-177">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="75e06-177">Events</span></span>

<span data-ttu-id="75e06-178">Zdarzenie jest akcją rozpoznawaną przez obiekt, taką jak kliknięcie myszą lub naciśnięcie klawisza, dla którego można napisać kod, aby odpowiedzieć.</span><span class="sxs-lookup"><span data-stu-id="75e06-178">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="75e06-179">Zdarzenia mogą wystąpić w wyniku działania użytkownika lub kodu programu albo mogą być spowodowane przez system.</span><span class="sxs-lookup"><span data-stu-id="75e06-179">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="75e06-180">Kod, który sygnalizuje zdarzenie, jest wywoływany *w celu* *podniesienia* zdarzenia, a kod, który odpowiada na ten komunikat, jest nazywany.</span><span class="sxs-lookup"><span data-stu-id="75e06-180">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="75e06-181">Możesz również opracować własne zdarzenia niestandardowe, które mają być zgłaszane przez obiekty i obsługiwane przez inne obiekty.</span><span class="sxs-lookup"><span data-stu-id="75e06-181">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="75e06-182">Aby uzyskać więcej informacji, zobacz [zdarzenia](../events/index.md).</span><span class="sxs-lookup"><span data-stu-id="75e06-182">For more information, see [Events](../events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="75e06-183">Elementy członkowskie wystąpienia i udostępnione elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="75e06-183">Instance members and shared members</span></span>

<span data-ttu-id="75e06-184">Gdy tworzysz obiekt z klasy, wynikiem jest wystąpienie tej klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-184">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="75e06-185">Elementy członkowskie, które nie są zadeklarowane za pomocą słowa kluczowego [Shared](../../../language-reference/modifiers/shared.md) , są *elementami członkowskimi wystąpień*, które należą do tego konkretnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="75e06-185">Members that are not declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="75e06-186">Element członkowski wystąpienia w jednym wystąpieniu jest niezależny od tego samego elementu członkowskiego w innym wystąpieniu tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-186">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="75e06-187">Zmienna elementu członkowskiego wystąpienia może na przykład mieć różne wartości w różnych wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="75e06-187">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="75e06-188">Składowe zadeklarowane za pomocą `Shared` słowa kluczowego są *udostępnionymi elementami członkowskimi*, które należą do klasy jako całości, a nie do żadnego konkretnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="75e06-188">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="75e06-189">Współużytkowany element członkowski istnieje tylko raz, niezależnie od tego, ile wystąpień klasy tworzysz, lub nawet wtedy, gdy nie utworzysz żadnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="75e06-189">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="75e06-190">Współdzielona zmienna członkowska na przykład ma tylko jedną wartość, która jest dostępna dla wszystkich kodów, które mogą uzyskać dostęp do klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-190">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-non-shared-members"></a><span data-ttu-id="75e06-191">Uzyskiwanie dostępu do nieudostępnionych elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="75e06-191">Accessing non-shared members</span></span>

1. <span data-ttu-id="75e06-192">Upewnij się, że obiekt został utworzony z klasy i przypisany do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-192">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="75e06-193">W instrukcji, która uzyskuje dostęp do elementu członkowskiego, postępuj według nazwy zmiennej obiektu z *operatorem dostępu do elementu członkowskiego* ( `.` ), a następnie nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="75e06-193">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="75e06-194">Uzyskiwanie dostępu do udostępnionych członków</span><span class="sxs-lookup"><span data-stu-id="75e06-194">Accessing shared members</span></span>

- <span data-ttu-id="75e06-195">Postępuj według nazwy klasy z *operatorem dostępu do elementów członkowskich* ( `.` ), a następnie nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="75e06-195">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="75e06-196">Zawsze należy uzyskiwać dostęp do `Shared` elementu członkowskiego obiektu bezpośrednio za pomocą nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-196">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="75e06-197">Jeśli utworzono już obiekt z klasy, możesz alternatywnie uzyskać dostęp do `Shared` elementu członkowskiego za pośrednictwem zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-197">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="75e06-198">Różnice między klasami i modułami</span><span class="sxs-lookup"><span data-stu-id="75e06-198">Differences between classes and modules</span></span>

<span data-ttu-id="75e06-199">Główną różnicą między klasami i modułami jest to, że klasy mogą być tworzone jako obiekty, gdy nie mogą być używane w standardowym module.</span><span class="sxs-lookup"><span data-stu-id="75e06-199">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="75e06-200">Ponieważ istnieje tylko jedna kopia danych modułu standardowego, gdy jedna część programu zmienia zmienną publiczną w module standardowym, każda inna część programu pobiera tę samą wartość, jeśli następnie odczytuje tę zmienną.</span><span class="sxs-lookup"><span data-stu-id="75e06-200">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="75e06-201">Z kolei dane obiektów istnieją osobno dla każdego obiektu, który tworzy wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="75e06-201">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="75e06-202">Kolejną różnicą jest to, że w przeciwieństwie do modułów standardowych klasy mogą implementować interfejsy.</span><span class="sxs-lookup"><span data-stu-id="75e06-202">Another difference is that unlike standard modules, classes can implement interfaces.</span></span> <span data-ttu-id="75e06-203">Jeśli klasa jest oznaczona za pomocą modyfikatora [MustInherit](../../../language-reference/modifiers/mustinherit.md) , nie można jej utworzyć bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="75e06-203">If a class is marked with the [MustInherit](../../../language-reference/modifiers/mustinherit.md) modifier, it can't be instantiated directly.</span></span> <span data-ttu-id="75e06-204">Jednak nadal różni się od modułu, ponieważ może być dziedziczony, podczas gdy moduły nie mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="75e06-204">However, it's still different from a module as it can be inherited while modules can't be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="75e06-205">Gdy `Shared` modyfikator zostanie zastosowany do elementu członkowskiego klasy, jest on kojarzony z samą klasą, a nie z konkretnym wystąpieniem klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-205">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="75e06-206">Dostęp do elementu członkowskiego uzyskuje się bezpośrednio przy użyciu nazwy klasy, w taki sam sposób, jak członkowie modułów są dostępni.</span><span class="sxs-lookup"><span data-stu-id="75e06-206">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="75e06-207">Klasy i moduły również używają różnych zakresów dla ich członków.</span><span class="sxs-lookup"><span data-stu-id="75e06-207">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="75e06-208">Elementy członkowskie zdefiniowane w klasie są objęte zakresem określonego wystąpienia klasy i istnieją tylko dla okresu istnienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-208">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="75e06-209">Aby uzyskać dostęp do składowych klasy spoza klasy, należy użyć w pełni kwalifikowanych nazw w formacie *obiektu*. *Element członkowski*.</span><span class="sxs-lookup"><span data-stu-id="75e06-209">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="75e06-210">Z drugiej strony członkowie zadeklarowani w module są publicznie dostępni domyślnie i dostęp do niego można uzyskać za pomocą dowolnego kodu, który może uzyskać dostęp do modułu.</span><span class="sxs-lookup"><span data-stu-id="75e06-210">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="75e06-211">Oznacza to, że zmienne w module standardowym są efektywnie zmiennymi globalnymi, ponieważ są widoczne z dowolnego miejsca w projekcie i istnieją w okresie istnienia programu.</span><span class="sxs-lookup"><span data-stu-id="75e06-211">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="75e06-212">Używanie klas i obiektów</span><span class="sxs-lookup"><span data-stu-id="75e06-212">Reusing classes and objects</span></span>

<span data-ttu-id="75e06-213">Obiekty umożliwiają deklarowanie zmiennych i procedur jednokrotnie, a następnie ponowne używanie ich w razie konieczności.</span><span class="sxs-lookup"><span data-stu-id="75e06-213">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="75e06-214">Na przykład, jeśli chcesz dodać do aplikacji moduł sprawdzania pisowni, możesz zdefiniować wszystkie zmienne i funkcje obsługi, aby zapewnić funkcje sprawdzania pisowni.</span><span class="sxs-lookup"><span data-stu-id="75e06-214">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="75e06-215">Jeśli tworzysz moduł sprawdzania pisowni jako klasę, możesz użyć go ponownie w innych aplikacjach przez dodanie odwołania do skompilowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="75e06-215">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="75e06-216">Jeszcze lepszym rozwiązaniem może być Oszczędność pracy przy użyciu klasy sprawdzania pisowni, która została już opracowana przez kogoś innego.</span><span class="sxs-lookup"><span data-stu-id="75e06-216">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="75e06-217">Platforma .NET zawiera wiele przykładów składników, które są dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="75e06-217">.NET provides many examples of components that are available for use.</span></span> <span data-ttu-id="75e06-218">Poniższy przykład używa <xref:System.TimeZone> klasy w <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="75e06-218">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="75e06-219"><xref:System.TimeZone>zawiera elementy członkowskie, które umożliwiają pobieranie informacji o strefie czasowej bieżącego systemu komputerowego.</span><span class="sxs-lookup"><span data-stu-id="75e06-219"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

<span data-ttu-id="75e06-220">W poprzednim przykładzie, pierwsza [instrukcja Dim](../../../language-reference/statements/dim-statement.md) deklaruje zmienną obiektu typu <xref:System.TimeZone> i przypisuje do niego <xref:System.TimeZone> obiekt zwracany przez <xref:System.TimeZone.CurrentTimeZone%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="75e06-220">In the preceding example, the first [Dim Statement](../../../language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="75e06-221">Relacje między obiektami</span><span class="sxs-lookup"><span data-stu-id="75e06-221">Relationships among objects</span></span>

<span data-ttu-id="75e06-222">Obiekty mogą być ze sobą powiązane na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="75e06-222">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="75e06-223">Główne rodzaje relacji są *hierarchiczne* i *zawiera*.</span><span class="sxs-lookup"><span data-stu-id="75e06-223">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="75e06-224">Relacja hierarchiczna</span><span class="sxs-lookup"><span data-stu-id="75e06-224">Hierarchical relationship</span></span>

<span data-ttu-id="75e06-225">Gdy klasy są wyprowadzane z bardziej podstawowych klas, są one określane jako *relacje hierarchiczne*.</span><span class="sxs-lookup"><span data-stu-id="75e06-225">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="75e06-226">Hierarchie klas są przydatne podczas opisywania elementów będących podtypem klasy bardziej ogólnej.</span><span class="sxs-lookup"><span data-stu-id="75e06-226">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="75e06-227">W poniższym przykładzie Załóżmy, że chcesz zdefiniować specjalny rodzaj <xref:System.Windows.Forms.Button> , który działa jak normalny, <xref:System.Windows.Forms.Button> ale również udostępnia metodę, która odwraca kolory pierwszego planu i tła.</span><span class="sxs-lookup"><span data-stu-id="75e06-227">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a><span data-ttu-id="75e06-228">Zdefiniuj klasę pochodną już istniejącej klasy</span><span class="sxs-lookup"><span data-stu-id="75e06-228">Define a class that is derived from an already existing class</span></span>

1. <span data-ttu-id="75e06-229">Użyj [instrukcji klasy](../../../language-reference/statements/class-statement.md) , aby zdefiniować klasę, z której ma być tworzony obiekt.</span><span class="sxs-lookup"><span data-stu-id="75e06-229">Use a [Class Statement](../../../language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class ReversibleButton
   ```

   <span data-ttu-id="75e06-230">Upewnij się, że `End Class` instrukcja jest zgodna z ostatnim wierszem kodu w klasie.</span><span class="sxs-lookup"><span data-stu-id="75e06-230">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="75e06-231">Domyślnie zintegrowane środowisko programistyczne (IDE) automatycznie generuje `End Class` po wprowadzeniu `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="75e06-231">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="75e06-232">Wykonaj `Class` instrukcję natychmiast, używając [instrukcji Inherits](../../../language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="75e06-232">Follow the `Class` statement immediately with an [Inherits Statement](../../../language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="75e06-233">Określ klasę, z której pochodzi nowa klasa.</span><span class="sxs-lookup"><span data-stu-id="75e06-233">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="75e06-234">Nowa klasa dziedziczy wszystkie elementy członkowskie zdefiniowane przez klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="75e06-234">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="75e06-235">Dodaj kod dla dodatkowych elementów członkowskich udostępnianej przez klasę pochodną.</span><span class="sxs-lookup"><span data-stu-id="75e06-235">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="75e06-236">Na przykład możesz dodać `ReverseColors` metodę, a Klasa pochodna może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="75e06-236">For example, you might add a `ReverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="75e06-237">Jeśli utworzysz obiekt z `ReversibleButton` klasy, będzie on miał dostęp do wszystkich elementów członkowskich <xref:System.Windows.Forms.Button> klasy, a także do `ReverseColors` metody i innych nowych elementów członkowskich, które definiujesz w `ReversibleButton` .</span><span class="sxs-lookup"><span data-stu-id="75e06-237">If you create an object from the `ReversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `ReverseColors` method and any other new members you define in `ReversibleButton`.</span></span>

<span data-ttu-id="75e06-238">Klasy pochodne dziedziczą elementy członkowskie z klasy, na której bazują, co pozwala na dodawanie złożoności w miarę postępu w hierarchii klas.</span><span class="sxs-lookup"><span data-stu-id="75e06-238">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="75e06-239">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [dziedziczeniu](inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="75e06-239">For more information, see [Inheritance Basics](inheritance-basics.md).</span></span>

### <a name="compile-the-code"></a><span data-ttu-id="75e06-240">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="75e06-240">Compile the code</span></span>

<span data-ttu-id="75e06-241">Upewnij się, że kompilator ma dostęp do klasy, z której zamierzasz utworzyć nową klasę.</span><span class="sxs-lookup"><span data-stu-id="75e06-241">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="75e06-242">Może to oznaczać, że w pełni kwalifikuje swoją nazwę, tak jak w poprzednim przykładzie, lub identyfikując jej przestrzeń nazw w [instrukcji Imports (przestrzeń nazw i typ platformy .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="75e06-242">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="75e06-243">Jeśli Klasa znajduje się w innym projekcie, może być konieczne dodanie odwołania do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-243">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="75e06-244">Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).</span><span class="sxs-lookup"><span data-stu-id="75e06-244">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="75e06-245">Relacja zawierania</span><span class="sxs-lookup"><span data-stu-id="75e06-245">Containment relationship</span></span>

<span data-ttu-id="75e06-246">Innym sposobem, w jaki obiekty mogą być powiązane, jest *relacja zawierania*.</span><span class="sxs-lookup"><span data-stu-id="75e06-246">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="75e06-247">Obiekty kontenera logicznie hermetyzują inne obiekty.</span><span class="sxs-lookup"><span data-stu-id="75e06-247">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="75e06-248">Na przykład <xref:System.OperatingSystem> obiekt logicznie zawiera <xref:System.Version> obiekt, który zwraca za pomocą jego <xref:System.OperatingSystem.Version%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="75e06-248">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="75e06-249">Należy zauważyć, że obiekt kontenera nie zawiera fizycznie żadnego innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="75e06-249">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="75e06-250">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="75e06-250">Collections</span></span>

<span data-ttu-id="75e06-251">Jeden określony typ obiektu jest reprezentowany przez *kolekcje*.</span><span class="sxs-lookup"><span data-stu-id="75e06-251">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="75e06-252">Kolekcje są grupami podobnych obiektów, które można wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="75e06-252">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="75e06-253">Visual Basic obsługuje określoną składnię w instrukcji [for each... Następna instrukcja](../../../language-reference/statements/for-each-next-statement.md) , która pozwala na iterację elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75e06-253">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="75e06-254">Ponadto kolekcje często umożliwiają <xref:Microsoft.VisualBasic.Collection.Item%2A> Pobieranie elementów według ich indeksu lub kojarzenie ich z unikatowym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="75e06-254">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="75e06-255">Kolekcje mogą być łatwiejsze w użyciu niż tablice, ponieważ umożliwiają dodawanie lub usuwanie elementów bez użycia indeksów.</span><span class="sxs-lookup"><span data-stu-id="75e06-255">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="75e06-256">Ze względu na łatwość użytkowania kolekcje są często używane do przechowywania formularzy i kontrolek.</span><span class="sxs-lookup"><span data-stu-id="75e06-256">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="75e06-257">Powiązane tematy</span><span class="sxs-lookup"><span data-stu-id="75e06-257">Related topics</span></span>

<span data-ttu-id="75e06-258">[Wskazówki: Definiowanie klas](walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="75e06-258">[Walkthrough: Defining Classes](walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="75e06-259">Zawiera opis krok po kroku dotyczący sposobu tworzenia klasy.</span><span class="sxs-lookup"><span data-stu-id="75e06-259">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="75e06-260">[Przeciążone właściwości i metody](overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="75e06-260">[Overloaded Properties and Methods](overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="75e06-261">Przeciążone właściwości i metody</span><span class="sxs-lookup"><span data-stu-id="75e06-261">Overloaded Properties and Methods</span></span>

<span data-ttu-id="75e06-262">[Podstawowe informacje o dziedziczeniu](inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="75e06-262">[Inheritance Basics](inheritance-basics.md)</span></span>\
<span data-ttu-id="75e06-263">Obejmuje Modyfikatory dziedziczenia, zastępowanie metod i właściwości, MyClass i webbase.</span><span class="sxs-lookup"><span data-stu-id="75e06-263">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="75e06-264">[Okres istnienia obiektu: sposób tworzenia i zniszczenia obiektów](object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="75e06-264">[Object Lifetime: How Objects Are Created and Destroyed](object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="75e06-265">Omawia tworzenie i usuwanie wystąpień klas.</span><span class="sxs-lookup"><span data-stu-id="75e06-265">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="75e06-266">[Typy anonimowe](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="75e06-266">[Anonymous Types](anonymous-types.md)</span></span>\
<span data-ttu-id="75e06-267">Opisuje sposób tworzenia i używania typów anonimowych, które umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="75e06-267">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="75e06-268">[Inicjatory obiektów: typy nazwane i anonimowe](object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="75e06-268">[Object Initializers: Named and Anonymous Types](object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="75e06-269">Omawia Inicjatory obiektów, które są używane do tworzenia wystąpień nazwanych i anonimowych typów przy użyciu jednego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="75e06-269">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="75e06-270">[Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="75e06-270">[How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="75e06-271">Wyjaśnia, w jaki sposób można wywnioskować nazwy właściwości i typy w deklaracjach typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="75e06-271">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="75e06-272">Zawiera przykłady udanych i nieudanych wnioskowania.</span><span class="sxs-lookup"><span data-stu-id="75e06-272">Provides examples of successful and unsuccessful inference.</span></span>
