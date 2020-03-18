---
title: Inicjatory obiektów i kolekcji — przewodnik programowania języka C#
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: ae8741e2f29db0a470ad8d3b121375fbdeaff0d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170198"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="96547-102">Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="96547-102">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="96547-103">C# umożliwia tworzenie wystąpienia obiektu lub kolekcji i wykonywania przypisań elementów członkowskich w jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="96547-103">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="96547-104">Inicjatory obiektów</span><span class="sxs-lookup"><span data-stu-id="96547-104">Object initializers</span></span>

<span data-ttu-id="96547-105">Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="96547-105">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="96547-106">Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).</span><span class="sxs-lookup"><span data-stu-id="96547-106">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="96547-107">W poniższym przykładzie pokazano, jak używać inicjatora obiektów o nazwanym typie `Cat` i jak wywołać konstruktora bezparametrowego.</span><span class="sxs-lookup"><span data-stu-id="96547-107">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="96547-108">Należy zwrócić uwagę na użycie właściwości `Cat` implementowane automatycznie w klasie.</span><span class="sxs-lookup"><span data-stu-id="96547-108">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="96547-109">Aby uzyskać więcej informacji, zobacz [Właściwości implementowane automatycznie](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="96547-109">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

<span data-ttu-id="96547-110">Składnia inicjaalizatorów obiektów umożliwia utworzenie wystąpienia, a następnie przypisuje nowo utworzony obiekt, z jego przypisanymi właściwościami, do zmiennej w przydziale.</span><span class="sxs-lookup"><span data-stu-id="96547-110">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="96547-111">Począwszy od C# 6 inicjatory obiektów można ustawić indeksatory, oprócz przypisywania pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="96547-111">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="96547-112">Rozważmy `Matrix` tę podstawową klasę:</span><span class="sxs-lookup"><span data-stu-id="96547-112">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="96547-113">Macierz tożsamości można zainicjować następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="96547-113">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="96547-114">Każdy indeksator dostępny, który zawiera zestawseter dostępne może służyć jako jedno z wyrażeń w inicjatora obiektu, niezależnie od liczby lub typów argumentów.</span><span class="sxs-lookup"><span data-stu-id="96547-114">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="96547-115">Argumenty indeksu tworzą lewą stronę przypisania, a wartość jest po prawej stronie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="96547-115">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="96547-116">Na przykład wszystkie te `IndexersExample` są prawidłowe, jeśli ma odpowiednie indeksatory:</span><span class="sxs-lookup"><span data-stu-id="96547-116">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Size = Math.PI,
    ['C',4] = "Middle C"
}
```

<span data-ttu-id="96547-117">Dla poprzedniego kodu do `IndexersExample` skompilowania, typ musi mieć następujące elementy członkowskie:</span><span class="sxs-lookup"><span data-stu-id="96547-117">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="96547-118">Inicjatory obiektów z typami anonimowymi</span><span class="sxs-lookup"><span data-stu-id="96547-118">Object Initializers with anonymous types</span></span>

<span data-ttu-id="96547-119">Chociaż inicjatory obiektów mogą być używane w dowolnym kontekście, są one szczególnie przydatne w wyrażeniach kwerend LINQ.</span><span class="sxs-lookup"><span data-stu-id="96547-119">Although object initializers can be used in any context, they are especially useful in LINQ query expressions.</span></span> <span data-ttu-id="96547-120">Wyrażenia kwerendy często używają [typów anonimowych](./anonymous-types.md), które mogą być inicjowane tylko przy użyciu inicjatora obiektów, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="96547-120">Query expressions make frequent use of [anonymous types](./anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="96547-121">Typy anonimowe `select` włączyć klauzulę w wyrażeniu kwerendy LINQ do przekształcania obiektów oryginalnej sekwencji do obiektów, których wartość i kształt może różnić się od oryginału.</span><span class="sxs-lookup"><span data-stu-id="96547-121">Anonymous types enable the `select` clause in a LINQ query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="96547-122">Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="96547-122">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="96547-123">W poniższym przykładzie załóżmy,`p`że obiekt produktu ( ) zawiera wiele pól i metod i że jesteś zainteresowany tylko utworzeniesekwencji obiektów, które zawierają nazwę produktu i cenę jednostkową.</span><span class="sxs-lookup"><span data-stu-id="96547-123">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="96547-124">Po wykonaniu tej kwerendy zmienna `productInfos` będzie zawierać sekwencję obiektów, `foreach` do których można uzyskać dostęp w instrukcji, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="96547-124">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="96547-125">Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które otrzymują takie same nazwy jak właściwości lub pola w oryginalnym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="96547-125">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="96547-126">Można również zmienić nazwę pola podczas tworzenia typu anonimowego; w poniższym przykładzie `UnitPrice` zmienia `Price`nazwę pola na .</span><span class="sxs-lookup"><span data-stu-id="96547-126">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="96547-127">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="96547-127">Collection initializers</span></span>

<span data-ttu-id="96547-128">Inicjatory kolekcji pozwalają określić jeden lub więcej inicjatorów elementu <xref:System.Collections.IEnumerable> podczas `Add` inicjowania typu kolekcji, który implementuje i ma odpowiedni podpis jako metodę wystąpienia lub metodę rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="96547-128">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="96547-129">Inicjatory elementu może być wartość prostą, wyrażenie lub inicjator obiektu.</span><span class="sxs-lookup"><span data-stu-id="96547-129">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="96547-130">Za pomocą inicjatora kolekcji, nie trzeba określić wiele wywołań; kompilator automatycznie dodaje wywołania.</span><span class="sxs-lookup"><span data-stu-id="96547-130">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="96547-131">W poniższym przykładzie przedstawiono dwa proste inicjatory kolekcji:</span><span class="sxs-lookup"><span data-stu-id="96547-131">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="96547-132">Poniższy inicjator kolekcji używa inicjatorów `Cat` obiektów do inicjowania obiektów klasy zdefiniowanej w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="96547-132">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="96547-133">Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="96547-133">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="96547-134">Można określić [null](../../language-reference/keywords/null.md) jako element w inicjatora `Add` kolekcji, jeśli metoda kolekcji zezwala na to.</span><span class="sxs-lookup"><span data-stu-id="96547-134">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="96547-135">Można określić elementy indeksowane, jeśli kolekcja obsługuje indeksowanie odczytu /zapisu.</span><span class="sxs-lookup"><span data-stu-id="96547-135">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="96547-136">Poprzedni przykład generuje kod, który <xref:System.Collections.Generic.Dictionary%602.Item(%600)> wywołuje, aby ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="96547-136">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="96547-137">Przed C# 6, można zainicjować słowniki i inne kontenery zestosujące przy użyciu następującej składni.</span><span class="sxs-lookup"><span data-stu-id="96547-137">Before C# 6, you could initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="96547-138">Należy zauważyć, że zamiast składni indeksatora, z nawiasami i przypisaniem, używa obiektu z wieloma wartościami:</span><span class="sxs-lookup"><span data-stu-id="96547-138">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="96547-139">Ten przykład inicjatora wywołuje, <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> aby dodać trzy elementy do słownika.</span><span class="sxs-lookup"><span data-stu-id="96547-139">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="96547-140">Te dwa różne sposoby inicjowania kolekcje zeszalenie mają nieco inne zachowanie ze względu na metodę wywołuje generuje kompilator.</span><span class="sxs-lookup"><span data-stu-id="96547-140">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="96547-141">Oba warianty działają `Dictionary` z klasą.</span><span class="sxs-lookup"><span data-stu-id="96547-141">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="96547-142">Inne typy mogą obsługiwać tylko jeden lub drugi na podstawie ich publicznego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="96547-142">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="96547-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="96547-143">Examples</span></span>

<span data-ttu-id="96547-144">Poniższy przykład łączy pojęcia inicjali obiektów i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="96547-144">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="96547-145">W poniższym przykładzie przedstawiono <xref:System.Collections.IEnumerable> obiekt, `Add` który implementuje i zawiera metodę z wieloma parametrami, Używa inicjatora `Add` kolekcji z wieloma elementami na element na listę, które odpowiadają podpismetody.</span><span class="sxs-lookup"><span data-stu-id="96547-145">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="96547-146">`Add`metody można użyć `params` słowa kluczowego do podjęcia zmiennej liczby argumentów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="96547-146">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="96547-147">W tym przykładzie przedstawiono również implementację niestandardową indeksatora, aby zainicjować kolekcję przy użyciu indeksów.</span><span class="sxs-lookup"><span data-stu-id="96547-147">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="96547-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96547-148">See also</span></span>

- [<span data-ttu-id="96547-149">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="96547-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="96547-150">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="96547-150">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="96547-151">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="96547-151">Anonymous Types</span></span>](anonymous-types.md)
