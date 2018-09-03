---
title: Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 9986a91b18c536773f4ca20b71c54588c3e95f32
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43476134"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="b9f9c-102">Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b9f9c-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="b9f9c-103">Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="b9f9c-104">Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).</span><span class="sxs-lookup"><span data-stu-id="b9f9c-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="b9f9c-105">Poniższy przykład pokazuje, jak używać inicjatora obiektów z typem nazwanym `Cat` i jak wywołać konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="b9f9c-106">Zwróć uwagę na użycie właściwości zaimplementowane automatycznie w `Cat` klasy.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="b9f9c-107">Aby uzyskać więcej informacji, zobacz [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b9f9c-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="b9f9c-108">Składnię inicjatorów obiektów można utworzyć wystąpienia, a po tym przypisuje nowo utworzony obiekt, za pomocą właściwości przypisane do zmiennej w ramach przypisania.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="b9f9c-109">Inicjatory obiektów z typami anonimowymi</span><span class="sxs-lookup"><span data-stu-id="b9f9c-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="b9f9c-110">Mimo że inicjatorów obiektów można używać w dowolnym kontekście, są one szczególnie użyteczne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="b9f9c-111">Wyrażeniach zapytań często są używane [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), który może być inicjowane tylko przy użyciu inicjatora obiektów, jak pokazano w poniższej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="b9f9c-112">Typy anonimowe umożliwiają `select` w klauzuli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniu do przekształcenia obiektów oryginalnej sekwencji w obiekty, których wartość i kształt mogą różnić się od oryginalnego zapytania.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="b9f9c-113">Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="b9f9c-114">W poniższym przykładzie przyjęto założenie, że obiekt produktu (`p`) zawiera wiele pól i metod, i że możesz jest zainteresowany wyłącznie utworzeniem sekwencji obiektów, które zawierają nazwę produktu i cenę jednostkową.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="b9f9c-115">Gdy to zapytanie jest wykonywane, `productInfos` zmienna będzie zawierać sekwencję obiektów, które mogą być udostępniane w `foreach` instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b9f9c-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="b9f9c-116">Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które otrzymują takie same nazwy, jak właściwości lub pola w oryginalnym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="b9f9c-117">Możesz również zmienić nazwę pola, podczas tworzenia typu anonimowego; w poniższym przykładzie nazwa `UnitPrice` pole `Price`.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="collection-initializers"></a><span data-ttu-id="b9f9c-118">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="b9f9c-118">Collection initializers</span></span>  
 <span data-ttu-id="b9f9c-119">Inicjatory kolekcji pozwalają określić jedną lub więcej inicjatory elementów podczas inicjowania kolekcji typu, który implementuje <xref:System.Collections.IEnumerable> i ma `Add` z odpowiednim podpisem jako metodę wystąpienia lub metodę rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-119">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="b9f9c-120">Inicjatory elementów mogą być wartościami prostymi, wyrażeniami lub inicjatorami obiektów.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-120">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="b9f9c-121">Za pomocą inicjatora kolekcji nie trzeba określać wielu wywołań `Add` klasy w kodzie źródłowym, ponieważ kompilator sam doda te wywołania.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-121">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="b9f9c-122">W poniższych przykładach pokazano dwa proste inicjatory kolekcji:</span><span class="sxs-lookup"><span data-stu-id="b9f9c-122">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="b9f9c-123">Następujący inicjator kolekcji używa inicjatorów obiektów w celu zainicjowania obiektów klasy `Cat` klasy zdefiniowanej w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-123">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="b9f9c-124">Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-124">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="b9f9c-125">Można określić [null](../../../csharp/language-reference/keywords/null.md) jako element w inicjatorze kolekcji Jeśli kolekcji `Add` zezwala na to metoda.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-125">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="b9f9c-126">Można określić indeksowane elementów, jeśli kolekcja obsługuje indeksowanie.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-126">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a><span data-ttu-id="b9f9c-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b9f9c-127">Examples</span></span>

 <span data-ttu-id="b9f9c-128">Poniższy przykład łączy koncepcji inicjatory obiektów i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-128">The following example combines the concepts of object and collection initializers.</span></span>

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 <span data-ttu-id="b9f9c-129">Pokazano w poniższym przykładzie obiekt, który implementuje <xref:System.Collections.IEnumerable> zawierający `Add` metody z wieloma parametrami umożliwia inicjatory kolekcji z wieloma elementami każdego elementu na liście odpowiadający podpis `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-129">Shown in the following example, an object which implements <xref:System.Collections.IEnumerable> containing an `Add` method with multiple parameters allows for collection initializers with multiple elements per item in the list corresponding to the signature of the `Add` method.</span></span> 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 <span data-ttu-id="b9f9c-130">`Add` można użyć metody `params` — słowo kluczowe, aby móc zmienną liczbę argumentów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-130">`Add` methods can use the `params` keyword to take a variable number of arguments as shown in the following example.</span></span> <span data-ttu-id="b9f9c-131">W tym przykładzie pokazano niestandardową implementację indeksatora również zainicjować kolekcji za pomocą indeksów.</span><span class="sxs-lookup"><span data-stu-id="b9f9c-131">This example demonstrates the custom implementation of an indexer as well to initialize a collection using indexes.</span></span>
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a><span data-ttu-id="b9f9c-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9f9c-132">See Also</span></span>  
 [<span data-ttu-id="b9f9c-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b9f9c-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b9f9c-134">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="b9f9c-134">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="b9f9c-135">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="b9f9c-135">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
