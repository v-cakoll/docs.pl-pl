---
title: 'Inicjatory obiektów: typy nazwane i anonimowe'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 5561812a53e2fe45c3ad4d12d0e18a8a1e948559
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411769"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="2aa5b-102">Inicjatory obiektów: typy nazwane i anonimowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2aa5b-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>
<span data-ttu-id="2aa5b-103">Inicjatory obiektów umożliwiają określanie właściwości dla obiektu złożonego za pomocą jednego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="2aa5b-104">Mogą służyć do tworzenia wystąpień nazwanych typów i typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="2aa5b-105">Deklaracje</span><span class="sxs-lookup"><span data-stu-id="2aa5b-105">Declarations</span></span>  
 <span data-ttu-id="2aa5b-106">Deklaracje wystąpień typów nazwanych i anonimowych mogą wyglądać niemal identycznie, ale ich efekty nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="2aa5b-107">Każda kategoria ma możliwości i ograniczenia własnych.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="2aa5b-108">Poniższy przykład przedstawia wygodny sposób deklarowania i inicjowania wystąpienia nazwanej klasy, `Customer` przy użyciu listy inicjatorów obiektów.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="2aa5b-109">Zauważ, że nazwa klasy jest określona po słowie kluczowym `New` .</span><span class="sxs-lookup"><span data-stu-id="2aa5b-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="2aa5b-110">Typ anonimowy nie ma użytecznych nazw.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="2aa5b-111">W związku z tym wystąpienie typu anonimowego nie może zawierać nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2aa5b-112">Wymagania i wyniki dwóch deklaracji nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="2aa5b-113">Dla `namedCust` klasy, `Customer` która ma `Name` Właściwość musi już istnieć, a deklaracja tworzy wystąpienie tej klasy.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="2aa5b-114">Dla programu `anonymousCust` kompilator definiuje nową klasę, która ma jedną właściwość, ciąg o nazwie `Name` i tworzy nowe wystąpienie tej klasy.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="2aa5b-115">Nazwane typy</span><span class="sxs-lookup"><span data-stu-id="2aa5b-115">Named Types</span></span>  
 <span data-ttu-id="2aa5b-116">Inicjatory obiektów zapewniają prosty sposób wywoływania konstruktora typu, a następnie ustawiania wartości niektórych lub wszystkich właściwości w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="2aa5b-117">Kompilator wywołuje odpowiedni Konstruktor dla instrukcji: bezparametrowego konstruktora, jeśli nie są wyświetlane żadne argumenty lub jeśli zostanie wysłany jeden lub więcej argumentów.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-117">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="2aa5b-118">Po tym określone właściwości są inicjowane w kolejności, w jakiej są wyświetlane na liście inicjatorów.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="2aa5b-119">Każda Inicjalizacja na liście inicjatora składa się z przypisania wartości początkowej do składowej klasy.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="2aa5b-120">Nazwy i typy danych elementów członkowskich są określane, gdy Klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="2aa5b-121">W poniższych przykładach `Customer` Klasa musi istnieć i musi mieć składowe o nazwie `Name` i `City` , która może akceptować wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="2aa5b-122">Alternatywnie można uzyskać ten sam wynik przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2aa5b-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="2aa5b-123">Każda z tych deklaracji jest równoważna z poniższym przykładem, który tworzy `Customer` Obiekt przy użyciu konstruktora bez parametrów, a następnie określa początkowe wartości dla `Name` `City` właściwości i przy użyciu `With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="2aa5b-124">Jeśli `Customer` Klasa zawiera sparametryzowany Konstruktor, który umożliwia wysyłanie w wartości dla `Name` , na przykład, można również zadeklarować i zainicjować `Customer` obiekt w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2aa5b-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="2aa5b-125">Nie trzeba inicjować wszystkich właściwości, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="2aa5b-126">Jednak lista inicjalizacji nie może być pusta.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="2aa5b-127">Niezainicjowane właściwości zachowują wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="2aa5b-128">Wnioskowanie o typie z nazwanymi typami</span><span class="sxs-lookup"><span data-stu-id="2aa5b-128">Type Inference with Named Types</span></span>  
 <span data-ttu-id="2aa5b-129">Można skrócić kod dla deklaracji `cust1` przez połączenie inicjatorów obiektów i wnioskowania o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="2aa5b-130">Pozwala to pominąć `As` klauzulę w deklaracji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="2aa5b-131">Typ danych zmiennej jest wywnioskowany na podstawie typu obiektu, który jest tworzony przez przypisanie.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="2aa5b-132">W poniższym przykładzie typem `cust6` jest `Customer` .</span><span class="sxs-lookup"><span data-stu-id="2aa5b-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="2aa5b-133">Uwagi dotyczące nazwanych typów</span><span class="sxs-lookup"><span data-stu-id="2aa5b-133">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="2aa5b-134">Nie można zainicjować składowej klasy więcej niż jeden raz na liście inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="2aa5b-135">Deklaracja `cust7` powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="2aa5b-136">Elementu członkowskiego można użyć do zainicjowania samego lub innego pola.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="2aa5b-137">Jeśli dostęp do elementu członkowskiego jest możliwy przed jego zainicjowaniem, jak w następującej deklaracji dla `cust8` , zostanie użyta wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="2aa5b-138">Należy pamiętać, że gdy przetwarzana jest deklaracja, która używa inicjatora obiektów, pierwszym krokiem jest to, że odpowiedni Konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="2aa5b-139">Następnie poszczególne pola na liście inicjatorów są inicjowane.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="2aa5b-140">W poniższych przykładach wartość domyślna dla `Name` jest przypisana do `cust8` , a zainicjowana wartość jest przypisana w `cust9` .</span><span class="sxs-lookup"><span data-stu-id="2aa5b-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="2aa5b-141">W poniższym przykładzie zastosowano sparametryzowany Konstruktor z `cust3` i, `cust4` Aby zadeklarować i zainicjować `cust10` i `cust11` .</span><span class="sxs-lookup"><span data-stu-id="2aa5b-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="2aa5b-142">Inicjatory obiektów mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-142">Object initializers can be nested.</span></span> <span data-ttu-id="2aa5b-143">W poniższym przykładzie `AddressClass` jest klasą, która ma dwie właściwości, a `City` `State` `Customer` Klasa ma `Address` Właściwość, która jest wystąpieniem `AddressClass` .</span><span class="sxs-lookup"><span data-stu-id="2aa5b-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="2aa5b-144">Lista inicjalizacji nie może być pusta.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-144">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="2aa5b-145">Inicjowane wystąpienie nie może być typu Object.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-145">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="2aa5b-146">Inicjowane składowe klas nie mogą być udostępnionymi elementami członkowskimi, elementami członkowskimi tylko do odczytu, stałymi lub wywołaniami metod.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="2aa5b-147">Inicjowane składowe klas nie mogą być indeksowane ani kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="2aa5b-148">Następujące przykłady powodują wystąpienie błędów kompilatora:</span><span class="sxs-lookup"><span data-stu-id="2aa5b-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="2aa5b-149">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="2aa5b-149">Anonymous Types</span></span>  
 <span data-ttu-id="2aa5b-150">Typy anonimowe używają inicjatorów obiektów do tworzenia wystąpień nowych typów, które nie są jawnie definiowane i nazwy.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="2aa5b-151">Zamiast tego kompilator generuje typ zgodnie z właściwościami wyznaczonymi na liście inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="2aa5b-152">Ponieważ nazwa typu nie jest określona, jest określana jako *Typ anonimowy*.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="2aa5b-153">Na przykład Porównaj następującą deklarację z poprzednią `cust6` .</span><span class="sxs-lookup"><span data-stu-id="2aa5b-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="2aa5b-154">Jedyną różnicą składnią jest to, że nie określono nazwy po `New` typie danych.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="2aa5b-155">Zdarza się jednak, że jest to zupełnie inne.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-155">However, what happens is quite different.</span></span> <span data-ttu-id="2aa5b-156">Kompilator definiuje nowy typ anonimowy, który ma dwie właściwości, i `Name` `City` tworzy jego wystąpienie z określonymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="2aa5b-157">Wnioskowanie o typie określa typy `Name` i `City` w przykładach, które mają być ciągami.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2aa5b-158">Nazwa typu anonimowego jest generowana przez kompilator i może się różnić w zależności od kompilacji do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="2aa5b-159">Kod nie powinien używać nazwy typu anonimowego ani nie polega na nim.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="2aa5b-160">Ponieważ nazwa typu jest niedostępna, nie można użyć `As` klauzuli do zadeklarowania `cust13` .</span><span class="sxs-lookup"><span data-stu-id="2aa5b-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="2aa5b-161">Jego typ musi być wywnioskowany.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-161">Its type must be inferred.</span></span> <span data-ttu-id="2aa5b-162">Bez używania późnego wiązania, to ogranicza użycie typów anonimowych do zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="2aa5b-163">Typy anonimowe zapewniają krytyczną obsługę zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-163">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="2aa5b-164">Aby uzyskać więcej informacji o korzystaniu z typów anonimowych w zapytaniach, zobacz [Typy anonimowe](anonymous-types.md) i [wprowadzenie do LINQ w Visual Basic](../linq/introduction-to-linq.md).</span><span class="sxs-lookup"><span data-stu-id="2aa5b-164">For more information about the use of anonymous types in queries, see [Anonymous Types](anonymous-types.md) and [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="2aa5b-165">Uwagi dotyczące typów anonimowych</span><span class="sxs-lookup"><span data-stu-id="2aa5b-165">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="2aa5b-166">Zwykle wszystkie lub większość właściwości w deklaracji typu anonimowego będą właściwościami klucza, które są wskazywane przez wpisanie słowa kluczowego `Key` przed nazwą właściwości.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="2aa5b-167">Aby uzyskać więcej informacji na temat właściwości klucza, zobacz [Key](../../../language-reference/modifiers/key.md).</span><span class="sxs-lookup"><span data-stu-id="2aa5b-167">For more information about key properties, see [Key](../../../language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="2aa5b-168">Podobnie jak nazwane typy, listy inicjatorów dla definicji typu anonimowego muszą deklarować co najmniej jedną właściwość.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="2aa5b-169">Gdy zadeklarowane jest wystąpienie typu anonimowego, kompilator generuje zgodną definicję typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="2aa5b-170">Nazwy i typy danych właściwości są pobierane z deklaracji wystąpienia i są uwzględniane przez kompilator w definicji.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="2aa5b-171">Właściwości nie są nazwane i zdefiniowane z góry, ponieważ byłyby dla nazwanego typu.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="2aa5b-172">Ich typy są wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-172">Their types are inferred.</span></span> <span data-ttu-id="2aa5b-173">Nie można określić typów danych właściwości przy użyciu `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="2aa5b-174">Typy anonimowe mogą również określać nazwy i wartości swoich właściwości na kilka innych sposobów.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="2aa5b-175">Na przykład właściwość typu anonimowego może przyjmować zarówno nazwę, jak i wartość zmiennej, lub nazwę i wartość właściwości innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="2aa5b-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="2aa5b-176">Aby uzyskać więcej informacji o opcjach definiowania właściwości w typach anonimowych, zobacz [How to: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="2aa5b-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa5b-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2aa5b-177">See also</span></span>

- [<span data-ttu-id="2aa5b-178">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="2aa5b-178">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="2aa5b-179">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="2aa5b-179">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="2aa5b-180">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2aa5b-180">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="2aa5b-181">Instrukcje: wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="2aa5b-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="2aa5b-182">Klucz</span><span class="sxs-lookup"><span data-stu-id="2aa5b-182">Key</span></span>](../../../language-reference/modifiers/key.md)
- [<span data-ttu-id="2aa5b-183">Instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów</span><span class="sxs-lookup"><span data-stu-id="2aa5b-183">How to: Declare an Object by Using an Object Initializer</span></span>](how-to-declare-an-object-by-using-an-object-initializer.md)
