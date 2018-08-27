---
title: Elementy członkowskie z wyrażeniem (C# Programming Guide)
ms.date: 07/20/2015
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e58afadae78d3f6b15a8e859edc8d554d84c393
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911909"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="fc827-102">Elementy członkowskie z wyrażeniem (C# Podręcznik programowania)</span><span class="sxs-lookup"><span data-stu-id="fc827-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="fc827-103">Wyrażenie treści definicji umożliwiają zapewnienie implementacja członka w formie bardzo zwięzły, czytelny.</span><span class="sxs-lookup"><span data-stu-id="fc827-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="fc827-104">Definicja treści wyrażenia można użyć w każdym przypadku, gdy logiki dla dowolnego z obsługiwanych elementów członkowskich, takich jak metody lub właściwości, składa się z pojedynczego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fc827-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="fc827-105">Definicja treści wyrażenia ma następującą składnię ogólne:</span><span class="sxs-lookup"><span data-stu-id="fc827-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="fc827-106">gdzie *wyrażenie* jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="fc827-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="fc827-107">Wprowadzono obsługę definicji treści wyrażenia dla metod i właściwości uzyskać metod dostępu w języku C# 6 i został rozszerzony w języku C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="fc827-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="fc827-108">Wyrażenie treści definicje mogą być używane z elementy członkowskie typu wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="fc827-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="fc827-109">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fc827-109">Member</span></span>  |<span data-ttu-id="fc827-110">Obsługiwane, począwszy od...</span><span class="sxs-lookup"><span data-stu-id="fc827-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="fc827-111">— Metoda</span><span class="sxs-lookup"><span data-stu-id="fc827-111">Method</span></span>](#methods)  |<span data-ttu-id="fc827-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="fc827-112">C# 6</span></span> |
|[<span data-ttu-id="fc827-113">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="fc827-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="fc827-114">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="fc827-114">C# 7.0</span></span> |
|[<span data-ttu-id="fc827-115">Finalizator</span><span class="sxs-lookup"><span data-stu-id="fc827-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="fc827-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="fc827-116">C# 7.0</span></span> |
|[<span data-ttu-id="fc827-117">Pobierz właściwości</span><span class="sxs-lookup"><span data-stu-id="fc827-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="fc827-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="fc827-118">C# 6</span></span> |
|[<span data-ttu-id="fc827-119">Zestaw właściwości</span><span class="sxs-lookup"><span data-stu-id="fc827-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="fc827-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="fc827-120">C# 7.0</span></span> |
|[<span data-ttu-id="fc827-121">Indeksator</span><span class="sxs-lookup"><span data-stu-id="fc827-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="fc827-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="fc827-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="fc827-123">Metody</span><span class="sxs-lookup"><span data-stu-id="fc827-123">Methods</span></span>

<span data-ttu-id="fc827-124">Metoda z wyrażeniem składa się pojedyncze wyrażenie, które zwraca wartość, którego typ jest zgodny typ zwracany metody lub, w przypadku metod zwracających `void`, który wykonuje pewne operacje.</span><span class="sxs-lookup"><span data-stu-id="fc827-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="fc827-125">Na przykład typy zastąpienie <xref:System.Object.ToString%2A> metoda zazwyczaj zawierać pojedyncze wyrażenie, które zwraca ciąg reprezentujący bieżący obiekt.</span><span class="sxs-lookup"><span data-stu-id="fc827-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="fc827-126">W poniższym przykładzie zdefiniowano `Person` klasę, która zastępuje <xref:System.Object.ToString%2A> metody za pomocą definicji treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fc827-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="fc827-127">Umożliwia on również definiowanie `DisplayName` metodę, która wyświetla nazwę do konsoli.</span><span class="sxs-lookup"><span data-stu-id="fc827-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="fc827-128">Należy pamiętać, że `return` — słowo kluczowe nie jest używany w `ToString` definicja treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fc827-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="fc827-129">Aby uzyskać więcej informacji, zobacz [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="fc827-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="fc827-130">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="fc827-130">Constructors</span></span>

<span data-ttu-id="fc827-131">Definicja treści wyrażenia dla konstruktora zwykle składa się z wyrażenia przypisania pojedynczego lub wywołanie metody, która obsługuje argumentów konstruktora lub inicjuje wystąpienie przechodzi w stan.</span><span class="sxs-lookup"><span data-stu-id="fc827-131">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="fc827-132">W poniższym przykładzie zdefiniowano `Location` klasy, której Konstruktor ma jeden ciąg parametr o nazwie *nazwa*.</span><span class="sxs-lookup"><span data-stu-id="fc827-132">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="fc827-133">Definicja treści wyrażenia przypisuje argument `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc827-133">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="fc827-134">Aby uzyskać więcej informacji, zobacz [konstruktorów (C# Programming Guide)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="fc827-134">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="fc827-135">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="fc827-135">Finalizers</span></span>

<span data-ttu-id="fc827-136">Definicja treści wyrażenia dla finalizatora zazwyczaj zawiera instrukcje czyszczenia, na przykład instrukcji, które zwolnić niezarządzane zasoby.</span><span class="sxs-lookup"><span data-stu-id="fc827-136">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="fc827-137">W poniższym przykładzie zdefiniowano finalizator, który używa definicja treści wyrażenia, aby wskazać, że finalizator została wywołana.</span><span class="sxs-lookup"><span data-stu-id="fc827-137">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="fc827-138">Aby uzyskać więcej informacji, zobacz [finalizatory (C# Programming Guide)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="fc827-138">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="fc827-139">Property — instrukcje get</span><span class="sxs-lookup"><span data-stu-id="fc827-139">Property get statements</span></span>

<span data-ttu-id="fc827-140">Jeśli wybierzesz do zaimplementowania właściwości metoda dostępu get samodzielnie, można użyć definicji treści wyrażenia dla pojedynczego wyrażenia, które po prostu zwrócenia wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc827-140">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="fc827-141">Należy pamiętać, że `return` instrukcja nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="fc827-141">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="fc827-142">W poniższym przykładzie zdefiniowano `Location.Name` właściwości, których właściwość pobierająca zwraca wartość prywatna `locationName` pola, która będzie tworzyć kopię właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc827-142">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="fc827-143">Właściwości tylko do odczytu, korzystających z definicji treści wyrażenia można zaimplementować bez jawnego `set` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fc827-143">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="fc827-144">Składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="fc827-144">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="fc827-145">W poniższym przykładzie zdefiniowano `Location` klasy, których tylko do odczytu `Name` właściwość jest implementowany jako definicja treści wyrażenia, która zwraca wartość prywatna `locationName` pola.</span><span class="sxs-lookup"><span data-stu-id="fc827-145">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="fc827-146">Aby uzyskać więcej informacji, zobacz [właściwości (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="fc827-146">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="fc827-147">Instrukcje set właściwości</span><span class="sxs-lookup"><span data-stu-id="fc827-147">Property set statements</span></span>

<span data-ttu-id="fc827-148">Jeśli zdecydujesz się samodzielnie implementować metody dostępu właściwości zestawu, można użyć definicja treści wyrażenia dla wyrażenia jednowierszowego, która przypisuje wartość do pola, która będzie tworzyć kopię właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc827-148">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="fc827-149">W poniższym przykładzie zdefiniowano `Location.Name` właściwością instrukcji w której właściwość przypisuje jej argument wejściowy prywatnego `locationName` pola, która będzie tworzyć kopię właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc827-149">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="fc827-150">Aby uzyskać więcej informacji, zobacz [właściwości (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="fc827-150">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="fc827-151">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="fc827-151">Indexers</span></span>

<span data-ttu-id="fc827-152">Podobnie jak właściwości indeksatora get i set metod dostępu składają się z definicji treści wyrażenia metody dostępu get składa się z pojedynczej instrukcji, która zwraca wartość typu lub metody dostępu set wykonuje przypisanie proste.</span><span class="sxs-lookup"><span data-stu-id="fc827-152">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="fc827-153">W poniższym przykładzie zdefiniowano klasę o nazwie `Sports` zawierającą wewnętrzną <xref:System.String> tablicy, która zawiera nazwiska wielu dyscyplin sportowych.</span><span class="sxs-lookup"><span data-stu-id="fc827-153">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="fc827-154">Zarówno indeksatora get, jak i metody dostępu set są implementowane jako definicje treść wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fc827-154">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

<span data-ttu-id="fc827-155">Aby uzyskać więcej informacji, zobacz [indeksatorów (C# Programming Guide)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="fc827-155">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>

