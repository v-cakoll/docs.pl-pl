---
title: Elementy członkowskie z wyrażeniem - C# Programming Guide
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7c282157639a6a60270ce8dbebbc91dd0e0a3f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61709994"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="57801-102">Elementy członkowskie z wyrażeniem (C# Podręcznik programowania)</span><span class="sxs-lookup"><span data-stu-id="57801-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="57801-103">Wyrażenie treści definicji umożliwiają zapewnienie implementacja członka w formie bardzo zwięzły, czytelny.</span><span class="sxs-lookup"><span data-stu-id="57801-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="57801-104">Definicja treści wyrażenia można użyć w każdym przypadku, gdy logiki dla dowolnego z obsługiwanych elementów członkowskich, takich jak metody lub właściwości, składa się z pojedynczego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="57801-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="57801-105">Definicja treści wyrażenia ma następującą składnię ogólne:</span><span class="sxs-lookup"><span data-stu-id="57801-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="57801-106">gdzie *wyrażenie* jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="57801-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="57801-107">Wprowadzono obsługę definicji treści wyrażenia dla metod i właściwości tylko do odczytu w C# 6 i został rozszerzony w C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="57801-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="57801-108">Wyrażenie treści definicje mogą być używane z elementy członkowskie typu wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="57801-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="57801-109">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="57801-109">Member</span></span>  |<span data-ttu-id="57801-110">Obsługiwane, począwszy od...</span><span class="sxs-lookup"><span data-stu-id="57801-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="57801-111">— Metoda</span><span class="sxs-lookup"><span data-stu-id="57801-111">Method</span></span>](#methods)  |<span data-ttu-id="57801-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="57801-112">C# 6</span></span> |
|[<span data-ttu-id="57801-113">Właściwość tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="57801-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="57801-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="57801-114">C# 6</span></span>  |
|[<span data-ttu-id="57801-115">Property</span><span class="sxs-lookup"><span data-stu-id="57801-115">Property</span></span>](#properties)  |<span data-ttu-id="57801-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="57801-116">C# 7.0</span></span> |
|[<span data-ttu-id="57801-117">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="57801-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="57801-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="57801-118">C# 7.0</span></span> |
|[<span data-ttu-id="57801-119">Finalizator</span><span class="sxs-lookup"><span data-stu-id="57801-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="57801-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="57801-120">C# 7.0</span></span> |
|[<span data-ttu-id="57801-121">Indeksator</span><span class="sxs-lookup"><span data-stu-id="57801-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="57801-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="57801-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="57801-123">Metody</span><span class="sxs-lookup"><span data-stu-id="57801-123">Methods</span></span>

<span data-ttu-id="57801-124">Metoda z wyrażeniem składa się pojedyncze wyrażenie, które zwraca wartość, którego typ jest zgodny typ zwracany metody lub, w przypadku metod zwracających `void`, który wykonuje pewne operacje.</span><span class="sxs-lookup"><span data-stu-id="57801-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="57801-125">Na przykład typy zastąpienie <xref:System.Object.ToString%2A> metoda zazwyczaj zawierać pojedyncze wyrażenie, które zwraca ciąg reprezentujący bieżący obiekt.</span><span class="sxs-lookup"><span data-stu-id="57801-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="57801-126">W poniższym przykładzie zdefiniowano `Person` klasę, która zastępuje <xref:System.Object.ToString%2A> metody za pomocą definicji treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="57801-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="57801-127">Umożliwia on również definiowanie `DisplayName` metodę, która wyświetla nazwę do konsoli.</span><span class="sxs-lookup"><span data-stu-id="57801-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="57801-128">Należy pamiętać, że `return` — słowo kluczowe nie jest używany w `ToString` definicja treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="57801-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="57801-129">Aby uzyskać więcej informacji, zobacz [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="57801-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="57801-130">Właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="57801-130">Read-only properties</span></span>

<span data-ttu-id="57801-131">Począwszy od C# 6, można użyć definicji treści wyrażenia do zaimplementowania właściwość tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="57801-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="57801-132">Aby to zrobić, użyj następującej składni:</span><span class="sxs-lookup"><span data-stu-id="57801-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="57801-133">W poniższym przykładzie zdefiniowano `Location` klasy, których tylko do odczytu `Name` właściwość jest implementowany jako definicja treści wyrażenia, która zwraca wartość prywatna `locationName` pola:</span><span class="sxs-lookup"><span data-stu-id="57801-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="57801-134">Aby uzyskać więcej informacji o właściwościach, zobacz [właściwości (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="57801-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="57801-135">Właściwości</span><span class="sxs-lookup"><span data-stu-id="57801-135">Properties</span></span>

<span data-ttu-id="57801-136">Począwszy od C# 7.0, można użyć definicji treści wyrażenia do zaimplementowania właściwość `get` i `set` metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="57801-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="57801-137">Poniższy przykład pokazuje, jak to zrobić:</span><span class="sxs-lookup"><span data-stu-id="57801-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="57801-138">Aby uzyskać więcej informacji o właściwościach, zobacz [właściwości (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="57801-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="57801-139">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="57801-139">Constructors</span></span>

<span data-ttu-id="57801-140">Definicja treści wyrażenia dla konstruktora zwykle składa się z wyrażenia przypisania pojedynczego lub wywołanie metody, która obsługuje argumentów konstruktora lub inicjuje wystąpienie przechodzi w stan.</span><span class="sxs-lookup"><span data-stu-id="57801-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="57801-141">W poniższym przykładzie zdefiniowano `Location` klasy, której Konstruktor ma jeden ciąg parametr o nazwie *nazwa*.</span><span class="sxs-lookup"><span data-stu-id="57801-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="57801-142">Definicja treści wyrażenia przypisuje argument `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="57801-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="57801-143">Aby uzyskać więcej informacji, zobacz [konstruktorów (C# Programming Guide)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="57801-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="57801-144">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="57801-144">Finalizers</span></span>

<span data-ttu-id="57801-145">Definicja treści wyrażenia dla finalizatora zazwyczaj zawiera instrukcje czyszczenia, na przykład instrukcji, które zwolnić niezarządzane zasoby.</span><span class="sxs-lookup"><span data-stu-id="57801-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="57801-146">W poniższym przykładzie zdefiniowano finalizator, który używa definicja treści wyrażenia, aby wskazać, że finalizator została wywołana.</span><span class="sxs-lookup"><span data-stu-id="57801-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="57801-147">Aby uzyskać więcej informacji, zobacz [finalizatory (C# Programming Guide)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="57801-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="57801-148">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="57801-148">Indexers</span></span>

<span data-ttu-id="57801-149">Podobnie jak właściwości indeksatora get i set metod dostępu składają się z definicji treści wyrażenia metody dostępu get składa się z pojedynczej instrukcji, która zwraca wartość typu lub metody dostępu set wykonuje przypisanie proste.</span><span class="sxs-lookup"><span data-stu-id="57801-149">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="57801-150">W poniższym przykładzie zdefiniowano klasę o nazwie `Sports` zawierającą wewnętrzną <xref:System.String> tablicy, która zawiera nazwiska wielu dyscyplin sportowych.</span><span class="sxs-lookup"><span data-stu-id="57801-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="57801-151">Zarówno indeksatora get, jak i metody dostępu set są implementowane jako definicje treść wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="57801-151">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="57801-152">Aby uzyskać więcej informacji, zobacz [indeksatorów (C# Programming Guide)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="57801-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
