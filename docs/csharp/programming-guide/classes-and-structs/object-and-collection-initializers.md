---
title: Inicjatory obiektów i kolekcji — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 1f8ae023c414f8762139b194a9a8274218d0b5aa
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419372"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="5cd4c-102">Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5cd4c-102">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="5cd4c-103">C#umożliwia utworzenie wystąpienia obiektu lub kolekcji i wykonywanie przypisań elementów członkowskich w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-103">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="5cd4c-104">Inicjatory obiektów</span><span class="sxs-lookup"><span data-stu-id="5cd4c-104">Object initializers</span></span>

<span data-ttu-id="5cd4c-105">Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-105">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="5cd4c-106">Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).</span><span class="sxs-lookup"><span data-stu-id="5cd4c-106">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="5cd4c-107">Poniższy przykład pokazuje, jak używać inicjatora obiektów z nazwanym typem, `Cat` i sposób wywoływania konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-107">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="5cd4c-108">Zwróć uwagę na użycie właściwości, które są implementowane w klasie `Cat`.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-108">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="5cd4c-109">Aby uzyskać więcej informacji, zobacz [zaimplementowane właściwości](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5cd4c-109">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
<span data-ttu-id="5cd4c-110">Składnia inicjatorów obiektów umożliwia utworzenie wystąpienia, a po nim przypisuje nowo utworzony obiekt z przypisanymi do niego właściwościami do zmiennej w przypisaniu.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-110">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="5cd4c-111">Począwszy od C# 6, Inicjatory obiektów mogą ustawiać indeksatory oprócz przypisywania pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-111">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="5cd4c-112">Rozważmy tę podstawową klasę `Matrix`:</span><span class="sxs-lookup"><span data-stu-id="5cd4c-112">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="5cd4c-113">Macierz tożsamości można zainicjować przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5cd4c-113">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="5cd4c-114">Dowolny dostępny indeksator zawierający dostępną metodę ustawiającą można użyć jako jednego z wyrażeń w inicjatorze obiektu, niezależnie od liczby lub typów argumentów.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-114">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="5cd4c-115">Argumenty indeksu tworzą lewą stronę przypisania, a wartość jest prawą stroną wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-115">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="5cd4c-116">Na przykład są one prawidłowe, jeśli `IndexersExample` ma odpowiednie indeksatory:</span><span class="sxs-lookup"><span data-stu-id="5cd4c-116">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

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

<span data-ttu-id="5cd4c-117">Dla poprzedniego kodu do skompilowania typ `IndexersExample` musi mieć następujących członków:</span><span class="sxs-lookup"><span data-stu-id="5cd4c-117">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="5cd4c-118">Inicjatory obiektów z typami anonimowymi</span><span class="sxs-lookup"><span data-stu-id="5cd4c-118">Object Initializers with anonymous types</span></span>

<span data-ttu-id="5cd4c-119">Chociaż inicjatorów obiektów można używać w dowolnym kontekście, są one szczególnie przydatne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-119">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="5cd4c-120">Wyrażenia zapytania często używają [anonimowych typów](./anonymous-types.md), które mogą być inicjowane tylko przy użyciu inicjatora obiektów, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-120">Query expressions make frequent use of [anonymous types](./anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="5cd4c-121">Typy anonimowe umożliwiają klauzulę `select` w wyrażeniu zapytania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], aby przekształcić obiekty oryginalnej sekwencji do obiektów, których wartość i kształt mogą się różnić od oryginału.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-121">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="5cd4c-122">Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-122">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="5cd4c-123">W poniższym przykładzie Załóżmy, że obiekt produktu (`p`) zawiera wiele pól i metod oraz że interesuje Cię tylko Tworzenie sekwencji obiektów zawierających nazwę produktu i cenę jednostkową.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-123">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="5cd4c-124">Po wykonaniu tego zapytania zmienna `productInfos` będzie zawierać sekwencję obiektów, do których można uzyskać dostęp w instrukcji `foreach`, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5cd4c-124">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="5cd4c-125">Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które otrzymują takie same nazwy, jak właściwości lub pola w oryginalnym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-125">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="5cd4c-126">Możesz również zmienić nazwę pola podczas tworzenia typu anonimowego; Poniższy przykład zmienia nazwę pola `UnitPrice`, aby `Price`.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-126">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="5cd4c-127">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="5cd4c-127">Collection initializers</span></span>

<span data-ttu-id="5cd4c-128">Inicjatory kolekcji pozwalają określić jeden lub więcej inicjatorów elementów po zainicjowaniu typu kolekcji implementującego <xref:System.Collections.IEnumerable> i ma `Add` z odpowiednią sygnaturą jako metodę wystąpienia lub metodę rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-128">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="5cd4c-129">Inicjatory elementów mogą być prostą wartością, wyrażeniem lub inicjatorem obiektu.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-129">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="5cd4c-130">Za pomocą inicjatora kolekcji nie trzeba określać wielu wywołań; Kompilator automatycznie dodaje wywołania.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-130">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="5cd4c-131">W poniższym przykładzie przedstawiono dwa proste Inicjatory kolekcji:</span><span class="sxs-lookup"><span data-stu-id="5cd4c-131">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="5cd4c-132">Poniższy inicjator kolekcji używa inicjatorów obiektów do inicjowania obiektów klasy `Cat` zdefiniowanej w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-132">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="5cd4c-133">Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-133">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="5cd4c-134">Można określić [wartość null](../../language-reference/keywords/null.md) jako element w inicjatorze kolekcji, jeśli pozwala na to metoda `Add` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-134">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="5cd4c-135">Można określić indeksowane elementy, jeśli kolekcja obsługuje indeksowanie odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-135">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="5cd4c-136">Poprzedni przykład generuje kod, który wywołuje <xref:System.Collections.Generic.Dictionary%602.Item(%600)>, aby ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-136">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="5cd4c-137">Począwszy od C# 6, można inicjować słowniki i inne kontenery asocjacyjne przy użyciu następującej składni.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-137">Beginning with C# 6, you can initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="5cd4c-138">Należy zauważyć, że zamiast składni indeksatora, z nawiasami i przypisaniem, używa obiektu z wieloma wartościami:</span><span class="sxs-lookup"><span data-stu-id="5cd4c-138">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="5cd4c-139">Ten inicjator przykładu wywołuje <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)>, aby dodać trzy elementy do słownika.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-139">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="5cd4c-140">Te dwa różne sposoby inicjowania kolekcji asocjacyjnych mają nieco inne zachowanie ze względu na to, że metoda wywołuje kompilator.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-140">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="5cd4c-141">Obie warianty pracują z klasą `Dictionary`.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-141">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="5cd4c-142">Inne typy mogą obsługiwać tylko jedną lub drugą w oparciu o ich publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-142">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="5cd4c-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5cd4c-143">Examples</span></span>

<span data-ttu-id="5cd4c-144">Poniższy przykład łączy koncepcje inicjatorów obiektów i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-144">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="5cd4c-145">Poniższy przykład pokazuje obiekt, który implementuje <xref:System.Collections.IEnumerable> i zawiera metodę `Add` z wieloma parametrami, używa inicjatora kolekcji z wieloma elementami na liście, które odpowiadają sygnaturze metody `Add`.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-145">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="5cd4c-146">Metody `Add` mogą użyć słowa kluczowego `params`, aby przyjąć zmienną liczbę argumentów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-146">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="5cd4c-147">Ten przykład ilustruje również niestandardową implementację indeksatora w celu zainicjowania kolekcji przy użyciu indeksów.</span><span class="sxs-lookup"><span data-stu-id="5cd4c-147">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="5cd4c-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cd4c-148">See also</span></span>

- [<span data-ttu-id="5cd4c-149">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5cd4c-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5cd4c-150">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="5cd4c-150">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="5cd4c-151">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="5cd4c-151">Anonymous Types</span></span>](anonymous-types.md)
