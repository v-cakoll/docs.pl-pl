---
title: Elementy członkowskie zabudowane wyrażeniem — przewodnik programowania języka C#
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711990"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="5b540-102">Elementy członkowskie zabudowane wyrażeniem (przewodnik programowania Języka C#)</span><span class="sxs-lookup"><span data-stu-id="5b540-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="5b540-103">Definicje treści wyrażeń umożliwiają podanie implementacji członka w bardzo zwięzłej, czytelnej formie.</span><span class="sxs-lookup"><span data-stu-id="5b540-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="5b540-104">Definicji treści wyrażenia można użyć zawsze, gdy logika dla dowolnego obsługiwanego elementu członkowskiego, takiego jak metoda lub właściwość, składa się z pojedynczego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5b540-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="5b540-105">Definicja treści wyrażenia ma następującą ogólną składnię:</span><span class="sxs-lookup"><span data-stu-id="5b540-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="5b540-106">gdzie *wyrażenie* jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="5b540-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="5b540-107">Obsługa definicji treści wyrażeń została wprowadzona dla metod i właściwości tylko do odczytu w języku C# 6 i została rozszerzona w języku C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="5b540-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="5b540-108">Definicje treści wyrażeń mogą być używane z członkami typu wymienionymi w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="5b540-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="5b540-109">Członek</span><span class="sxs-lookup"><span data-stu-id="5b540-109">Member</span></span>  |<span data-ttu-id="5b540-110">Obsługiwane od...</span><span class="sxs-lookup"><span data-stu-id="5b540-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="5b540-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="5b540-111">Method</span></span>](#methods)  |<span data-ttu-id="5b540-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="5b540-112">C# 6</span></span> |
|[<span data-ttu-id="5b540-113">Właściwość tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5b540-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="5b540-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="5b540-114">C# 6</span></span>  |
|[<span data-ttu-id="5b540-115">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5b540-115">Property</span></span>](#properties)  |<span data-ttu-id="5b540-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="5b540-116">C# 7.0</span></span> |
|[<span data-ttu-id="5b540-117">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="5b540-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="5b540-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="5b540-118">C# 7.0</span></span> |
|[<span data-ttu-id="5b540-119">Finalizatorów</span><span class="sxs-lookup"><span data-stu-id="5b540-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="5b540-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="5b540-120">C# 7.0</span></span> |
|[<span data-ttu-id="5b540-121">Indeksator</span><span class="sxs-lookup"><span data-stu-id="5b540-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="5b540-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="5b540-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="5b540-123">Metody</span><span class="sxs-lookup"><span data-stu-id="5b540-123">Methods</span></span>

<span data-ttu-id="5b540-124">Metoda zabudowana wyrażeniem składa się z pojedynczego wyrażenia, które zwraca wartość, której typ `void`pasuje do typu zwracanego metody, lub dla metod, które zwracają , który wykonuje niektóre operacje.</span><span class="sxs-lookup"><span data-stu-id="5b540-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="5b540-125">Na przykład typy, które <xref:System.Object.ToString%2A> zastępują metodę zazwyczaj zawierają pojedyncze wyrażenie, które zwraca reprezentację ciągu bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5b540-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="5b540-126">W poniższym `Person` przykładzie definiuje klasę, <xref:System.Object.ToString%2A> która zastępuje metodę z definicji treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5b540-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="5b540-127">Definiuje również `DisplayName` metodę, która wyświetla nazwę konsoli.</span><span class="sxs-lookup"><span data-stu-id="5b540-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="5b540-128">Należy zauważyć, że `return` słowo `ToString` kluczowe nie jest używany w definicji treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5b540-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="5b540-129">Aby uzyskać więcej informacji, zobacz [Metody (Przewodnik programowania C#)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="5b540-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="5b540-130">Właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5b540-130">Read-only properties</span></span>

<span data-ttu-id="5b540-131">Począwszy od języka C# 6, można użyć definicji treści wyrażenia do zaimplementowania właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="5b540-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="5b540-132">Aby to zrobić, należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="5b540-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="5b540-133">W poniższym `Location` przykładzie zdefiniowano `Name` klasę, której właściwość tylko do odczytu jest `locationName` implementowana jako definicja treści wyrażeń, która zwraca wartość pola prywatnego:</span><span class="sxs-lookup"><span data-stu-id="5b540-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="5b540-134">Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości (Przewodnik programowania C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="5b540-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="5b540-135">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5b540-135">Properties</span></span>

<span data-ttu-id="5b540-136">Począwszy od języka C# 7.0, można użyć `get` `set` definicji treści wyrażenia do zaimplementowania właściwości i akcesorów.</span><span class="sxs-lookup"><span data-stu-id="5b540-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="5b540-137">W poniższym przykładzie pokazano, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="5b540-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="5b540-138">Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości (Przewodnik programowania C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="5b540-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="5b540-139">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="5b540-139">Constructors</span></span>

<span data-ttu-id="5b540-140">Definicja treści wyrażenia dla konstruktora zazwyczaj składa się z pojedynczego wyrażenia przypisania lub wywołania metody, który obsługuje argumenty konstruktora lub inicjuje stan wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5b540-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="5b540-141">Poniższy przykład definiuje `Location` klasę, której konstruktor ma parametr pojedynczego ciągu *o*nazwie .</span><span class="sxs-lookup"><span data-stu-id="5b540-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="5b540-142">Definicja treści wyrażenia przypisuje argument `Name` do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b540-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="5b540-143">Aby uzyskać więcej informacji, zobacz [Konstruktory (C# Programming Guide)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="5b540-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="5b540-144">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="5b540-144">Finalizers</span></span>

<span data-ttu-id="5b540-145">Definicja treści wyrażenia dla finalizatora zazwyczaj zawiera instrukcje oczyszczania, takie jak instrukcje zwalniające zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="5b540-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="5b540-146">W poniższym przykładzie definiuje finalizator, który używa definicji treści wyrażenia, aby wskazać, że finalizator został wywołany.</span><span class="sxs-lookup"><span data-stu-id="5b540-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="5b540-147">Aby uzyskać więcej informacji, zobacz [Finalizatory (C# Programming Guide)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="5b540-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="5b540-148">Indexers (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="5b540-148">Indexers</span></span>

<span data-ttu-id="5b540-149">Podobnie jak w przypadku `get` `set` właściwości indeksatora i akcesorów składa się z definicji treści wyrażenia, jeśli `get` akcesor składa się z pojedynczego wyrażenia, które zwraca wartość lub `set` akcesor wykonuje proste przypisanie.</span><span class="sxs-lookup"><span data-stu-id="5b540-149">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="5b540-150">W poniższym przykładzie zdefiniowano klasę o nazwie, `Sports` która zawiera tablicę wewnętrzną, <xref:System.String> która zawiera nazwy liczby sportowych.</span><span class="sxs-lookup"><span data-stu-id="5b540-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="5b540-151">Zarówno indeksatora `get` i `set` akcesorów są implementowane jako definicje treści wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="5b540-151">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="5b540-152">Aby uzyskać więcej informacji, zobacz [Indeksatory (C# Programming Guide)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b540-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
