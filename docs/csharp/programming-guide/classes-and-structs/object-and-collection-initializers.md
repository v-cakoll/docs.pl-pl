---
title: Inicjatory obiektów i kolekcji - C# przewodnik programowania
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 6c713072e120f2b5a6740add296c957d499c93c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978656"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="fcefb-102">Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="fcefb-102">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="fcefb-103">C#Pozwala utworzyć wystąpienie obiektu lub kolekcji i wykonywać przypisań składowych w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fcefb-103">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="fcefb-104">Inicjatory obiektów</span><span class="sxs-lookup"><span data-stu-id="fcefb-104">Object initializers</span></span>

<span data-ttu-id="fcefb-105">Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="fcefb-105">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="fcefb-106">Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).</span><span class="sxs-lookup"><span data-stu-id="fcefb-106">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="fcefb-107">Poniższy przykład pokazuje, jak używać inicjatora obiektów z typem nazwanym `Cat` i jak wywołać konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="fcefb-107">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="fcefb-108">Zwróć uwagę na użycie właściwości zaimplementowane automatycznie w `Cat` klasy.</span><span class="sxs-lookup"><span data-stu-id="fcefb-108">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="fcefb-109">Aby uzyskać więcej informacji, zobacz [implemented Properties](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="fcefb-109">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
<span data-ttu-id="fcefb-110">Składnię inicjatorów obiektów można utworzyć wystąpienia, a po tym przypisuje nowo utworzony obiekt, za pomocą właściwości przypisane do zmiennej w ramach przypisania.</span><span class="sxs-lookup"><span data-stu-id="fcefb-110">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="fcefb-111">Począwszy od C# 6, obiektu, inicjatory można ustawić indeksatorów, oprócz przypisywanie pola i właściwości.</span><span class="sxs-lookup"><span data-stu-id="fcefb-111">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="fcefb-112">Należy wziąć pod uwagę to podstawowe `Matrix` klasy:</span><span class="sxs-lookup"><span data-stu-id="fcefb-112">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="fcefb-113">Można zainicjować macierzą następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="fcefb-113">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="fcefb-114">Dostęp indeksatora, który zawiera dostępnej metody ustawiającej może służyć jako jedno z wyrażeń w inicjatorze obiektu, niezależnie od liczby i typy argumentów.</span><span class="sxs-lookup"><span data-stu-id="fcefb-114">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="fcefb-115">Argumenty indeksu formularza po lewej stronie przypisania, a wartość jest po prawej stronie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fcefb-115">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="fcefb-116">Na przykład są to wszystkie prawidłowe, gdy `IndexersExample` ma odpowiednie indeksatory:</span><span class="sxs-lookup"><span data-stu-id="fcefb-116">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Baz = Math.PI,
    ['C',4] = "Middle C"
}
```

<span data-ttu-id="fcefb-117">Dla poprzedniego kodu skompilować `IndexersExample` typ musi zawierać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="fcefb-117">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
}
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="fcefb-118">Inicjatory obiektów z typami anonimowymi</span><span class="sxs-lookup"><span data-stu-id="fcefb-118">Object Initializers with anonymous types</span></span>

<span data-ttu-id="fcefb-119">Mimo że inicjatorów obiektów można używać w dowolnym kontekście, są one szczególnie użyteczne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="fcefb-119">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="fcefb-120">Wyrażeniach zapytań często są używane [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), który może być inicjowane tylko przy użyciu inicjatora obiektów, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="fcefb-120">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="fcefb-121">Typy anonimowe umożliwiają `select` w klauzuli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniu do przekształcenia obiektów oryginalnej sekwencji w obiekty, których wartość i kształt mogą różnić się od oryginalnego zapytania.</span><span class="sxs-lookup"><span data-stu-id="fcefb-121">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="fcefb-122">Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="fcefb-122">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="fcefb-123">W poniższym przykładzie przyjęto założenie, że obiekt produktu (`p`) zawiera wiele pól i metod, i że możesz jest zainteresowany wyłącznie utworzeniem sekwencji obiektów, które zawierają nazwę produktu i cenę jednostkową.</span><span class="sxs-lookup"><span data-stu-id="fcefb-123">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="fcefb-124">Gdy to zapytanie jest wykonywane, `productInfos` zmienna będzie zawierać sekwencję obiektów, które mogą być udostępniane w `foreach` instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fcefb-124">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="fcefb-125">Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które odbierają takie same nazwy właściwości lub pola w oryginalnym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="fcefb-125">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="fcefb-126">Możesz również zmienić nazwę pola, podczas tworzenia typu anonimowego; w poniższym przykładzie nazwa `UnitPrice` pole `Price`.</span><span class="sxs-lookup"><span data-stu-id="fcefb-126">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="fcefb-127">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="fcefb-127">Collection initializers</span></span>

<span data-ttu-id="fcefb-128">Inicjatory kolekcji pozwalają określić jedną lub więcej inicjatory elementów podczas inicjowania kolekcji typu, który implementuje <xref:System.Collections.IEnumerable> i ma `Add` z odpowiednim podpisem jako metodę wystąpienia lub metodę rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="fcefb-128">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="fcefb-129">Inicjatory elementów mogą być wartościami prostymi, wyrażenie lub inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="fcefb-129">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="fcefb-130">Za pomocą inicjatora kolekcji, nie trzeba określać wielu wywołań; Kompilator sam doda te wywołania automatycznie.</span><span class="sxs-lookup"><span data-stu-id="fcefb-130">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="fcefb-131">W poniższym przykładzie pokazano dwa proste inicjatory kolekcji:</span><span class="sxs-lookup"><span data-stu-id="fcefb-131">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="fcefb-132">Następujący inicjator kolekcji używa inicjatorów obiektów w celu zainicjowania obiektów klasy `Cat` klasy zdefiniowanej w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fcefb-132">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="fcefb-133">Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fcefb-133">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="fcefb-134">Można określić [null](../../language-reference/keywords/null.md) jako element w inicjatorze kolekcji Jeśli kolekcji `Add` zezwala na to metoda.</span><span class="sxs-lookup"><span data-stu-id="fcefb-134">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="fcefb-135">Można określić elementy indeksowane, jeżeli obsługuje kolekcji odczytu i zapisu indeksowania.</span><span class="sxs-lookup"><span data-stu-id="fcefb-135">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="fcefb-136">Poprzedni przykład generuje kod, który wywołuje <xref:System.Collections.Generic.Dictionary%602.Item(%600)> można ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="fcefb-136">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="fcefb-137">Począwszy od C# 6, można inicjować słowników i inne kontenery asocjacyjne przy użyciu następującej składni.</span><span class="sxs-lookup"><span data-stu-id="fcefb-137">Beginning with C# 6, you can initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="fcefb-138">Zwróć uwagę, że zamiast składni indeksatora, za pomocą nawiasów i przypisania, używa obiekt z wieloma wartościami:</span><span class="sxs-lookup"><span data-stu-id="fcefb-138">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="fcefb-139">Ten przykład inicjatora wywołuje <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> można dodać trzy elementy do słownika.</span><span class="sxs-lookup"><span data-stu-id="fcefb-139">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="fcefb-140">Te dwa różne sposoby inicjowania kolekcji asocjacyjnych ma nieco inaczej, ze względu na wywołania metody, które kompilator generuje.</span><span class="sxs-lookup"><span data-stu-id="fcefb-140">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="fcefb-141">Oba warianty pracować `Dictionary` klasy.</span><span class="sxs-lookup"><span data-stu-id="fcefb-141">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="fcefb-142">Inne typy mogą obsługują tylko jeden lub innych zależności na ich publicznego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="fcefb-142">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="fcefb-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="fcefb-143">Examples</span></span>

<span data-ttu-id="fcefb-144">Poniższy przykład łączy koncepcji inicjatory obiektów i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fcefb-144">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="fcefb-145">W poniższym przykładzie pokazano obiekt, który implementuje <xref:System.Collections.IEnumerable> i zawiera `Add` metody z wieloma parametrami, używa inicjatora kolekcji z wieloma elementami każdego elementu na liście, które odpowiadają podpis `Add`metody.</span><span class="sxs-lookup"><span data-stu-id="fcefb-145">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="fcefb-146">`Add` można użyć metody `params` — słowo kluczowe, aby móc zmienną liczbę argumentów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fcefb-146">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="fcefb-147">W przykładzie pokazano również niestandardową implementację indeksatora zainicjować kolekcji za pomocą indeksów.</span><span class="sxs-lookup"><span data-stu-id="fcefb-147">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="fcefb-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcefb-148">See also</span></span>

- [<span data-ttu-id="fcefb-149">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fcefb-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fcefb-150">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="fcefb-150">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
- [<span data-ttu-id="fcefb-151">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="fcefb-151">Anonymous Types</span></span>](anonymous-types.md)
