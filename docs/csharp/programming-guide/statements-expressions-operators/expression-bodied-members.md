---
title: Składowe w postaci wyrażeń — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: 45dcc58b252963e80798ba86ca5c4f461d493fac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120146"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="169cb-102">Elementy członkowskie z wyrażeniami (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="169cb-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="169cb-103">Definicje treści wyrażenia pozwalają zapewnić implementację elementu członkowskiego w bardzo zwięzłej, czytelnej postaci.</span><span class="sxs-lookup"><span data-stu-id="169cb-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="169cb-104">Można użyć definicji treści wyrażenia za każdym razem, gdy logika dowolnego obsługiwanego elementu członkowskiego, takiego jak metoda lub właściwość, składa się z jednego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="169cb-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="169cb-105">Definicja treści wyrażenia ma następującą składnię ogólną:</span><span class="sxs-lookup"><span data-stu-id="169cb-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="169cb-106">*wyrażenie* WHERE jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="169cb-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="169cb-107">Obsługa definicji treści wyrażenia została wprowadzona dla metod i właściwości tylko do odczytu w C# 6 i została rozwinięta w C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="169cb-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="169cb-108">Definicje treści wyrażenia mogą być używane z elementami członkowskimi typu wymienionymi w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="169cb-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="169cb-109">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="169cb-109">Member</span></span>  |<span data-ttu-id="169cb-110">Obsługiwane przez...</span><span class="sxs-lookup"><span data-stu-id="169cb-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="169cb-111">Method</span><span class="sxs-lookup"><span data-stu-id="169cb-111">Method</span></span>](#methods)  |<span data-ttu-id="169cb-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="169cb-112">C# 6</span></span> |
|[<span data-ttu-id="169cb-113">Właściwość tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="169cb-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="169cb-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="169cb-114">C# 6</span></span>  |
|[<span data-ttu-id="169cb-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="169cb-115">Property</span></span>](#properties)  |<span data-ttu-id="169cb-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="169cb-116">C# 7.0</span></span> |
|[<span data-ttu-id="169cb-117">Konstruktora</span><span class="sxs-lookup"><span data-stu-id="169cb-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="169cb-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="169cb-118">C# 7.0</span></span> |
|[<span data-ttu-id="169cb-119">Finalizator</span><span class="sxs-lookup"><span data-stu-id="169cb-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="169cb-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="169cb-120">C# 7.0</span></span> |
|[<span data-ttu-id="169cb-121">Indeksatora</span><span class="sxs-lookup"><span data-stu-id="169cb-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="169cb-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="169cb-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="169cb-123">Metody</span><span class="sxs-lookup"><span data-stu-id="169cb-123">Methods</span></span>

<span data-ttu-id="169cb-124">Metoda zabudowana wyrażenia składa się z pojedynczego wyrażenia, które zwraca wartość, której typ pasuje do typu zwracanego metody, lub dla metod, które zwracają `void`, który wykonuje pewne operacje.</span><span class="sxs-lookup"><span data-stu-id="169cb-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="169cb-125">Na przykład typy, które zastępują metodę <xref:System.Object.ToString%2A>, zazwyczaj zawierają pojedyncze wyrażenie, które zwraca reprezentację ciągu bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="169cb-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="169cb-126">W poniższym przykładzie zdefiniowano klasę `Person`, która zastępuje metodę <xref:System.Object.ToString%2A> z definicją treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="169cb-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="169cb-127">Definiuje również metodę `DisplayName`, która wyświetla nazwę konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="169cb-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="169cb-128">Należy zauważyć, że słowo kluczowe `return` nie jest używane w definicji treści wyrażenia `ToString`.</span><span class="sxs-lookup"><span data-stu-id="169cb-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="169cb-129">Aby uzyskać więcej informacji, zobacz [metodyC# (Przewodnik programowania)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="169cb-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="169cb-130">Właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="169cb-130">Read-only properties</span></span>

<span data-ttu-id="169cb-131">Począwszy od C# 6, można użyć definicji treści wyrażenia, aby zaimplementować właściwość tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="169cb-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="169cb-132">W tym celu należy użyć następującej składni:</span><span class="sxs-lookup"><span data-stu-id="169cb-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="169cb-133">W poniższym przykładzie zdefiniowano klasę `Location`, której Właściwość `Name` tylko do odczytu jest zaimplementowana jako definicja treści wyrażenia, która zwraca wartość pola `locationName` prywatnego:</span><span class="sxs-lookup"><span data-stu-id="169cb-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="169cb-134">Aby uzyskać więcej informacji na temat właściwości, zobacz [właściwości (C# Przewodnik programowania)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="169cb-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="169cb-135">Właściwości</span><span class="sxs-lookup"><span data-stu-id="169cb-135">Properties</span></span>

<span data-ttu-id="169cb-136">Począwszy od C# 7,0, można użyć definicji treści wyrażenia do implementowania właściwości`get`i`set`metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="169cb-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="169cb-137">Poniższy przykład ilustruje, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="169cb-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="169cb-138">Aby uzyskać więcej informacji na temat właściwości, zobacz [właściwości (C# Przewodnik programowania)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="169cb-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="169cb-139">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="169cb-139">Constructors</span></span>

<span data-ttu-id="169cb-140">Definicja treści wyrażenia dla konstruktora zwykle składa się z pojedynczego wyrażenia przypisania lub wywołania metody, które obsługuje argumenty konstruktora lub inicjuje stan wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="169cb-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="169cb-141">W poniższym przykładzie zdefiniowano klasę `Location`, której Konstruktor ma jeden parametr ciągu o nazwie *name*.</span><span class="sxs-lookup"><span data-stu-id="169cb-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="169cb-142">Definicja treści wyrażenia przypisuje argument do właściwości `Name`.</span><span class="sxs-lookup"><span data-stu-id="169cb-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="169cb-143">Aby uzyskać więcej informacji, zobacz [konstruktory (C# Przewodnik programowania)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="169cb-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="169cb-144">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="169cb-144">Finalizers</span></span>

<span data-ttu-id="169cb-145">Definicja treści wyrażenia dla finalizatora zwykle zawiera instrukcje czyszczenia, takie jak instrukcje zwalniania niezarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="169cb-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="169cb-146">W poniższym przykładzie zdefiniowano finalizator, który używa definicji treści wyrażenia, aby wskazać, że finalizator został wywołany.</span><span class="sxs-lookup"><span data-stu-id="169cb-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="169cb-147">Aby uzyskać więcej informacji, zobacz [finalizatoryC# (Przewodnik programowania)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="169cb-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="169cb-148">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="169cb-148">Indexers</span></span>

<span data-ttu-id="169cb-149">Podobnie jak w przypadku właściwości, `get` indeksatora i Akcesory `set` składają się z definicji treści wyrażenia, jeśli metoda dostępu `get` składa się z jednego wyrażenia, które zwraca wartość lub metoda dostępu `set` wykonuje proste przypisanie.</span><span class="sxs-lookup"><span data-stu-id="169cb-149">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="169cb-150">W poniższym przykładzie zdefiniowano klasę o nazwie `Sports`, która zawiera wewnętrzną tablicę <xref:System.String>, która zawiera nazwy wielu sportów.</span><span class="sxs-lookup"><span data-stu-id="169cb-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="169cb-151">Zarówno metody dostępu indeksatora `get`, jak i `set` są implementowane jako definicje treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="169cb-151">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="169cb-152">Aby uzyskać więcej informacji, zobacz [IndeksatoryC# (Przewodnik programowania)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="169cb-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
