---
title: Elementy członkowskie zabudowanych wyrażenia (C# przewodnik programowania w języku)
ms.date: 07/20/2015
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 800280ed9ceaf69b825bb2a3c2c3d0d5f829922d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="6c961-102">Elementy członkowskie zabudowanych wyrażenia (C# Podręcznik programowania)</span><span class="sxs-lookup"><span data-stu-id="6c961-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="6c961-103">Wyrażenie treści definicji umożliwiają implementacji członka w postaci bardzo krótkie, który może zostać odczytany.</span><span class="sxs-lookup"><span data-stu-id="6c961-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="6c961-104">Możesz użyć definicji treści wyrażenia zawsze, gdy logiki żadnego z obsługiwanych elementów, takich jak metody lub właściwości, składa się z jednego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6c961-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="6c961-105">Definicja treść wyrażenia ma następującą składnię ogólne:</span><span class="sxs-lookup"><span data-stu-id="6c961-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="6c961-106">gdzie *wyrażenie* jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="6c961-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="6c961-107">Wprowadzono obsługę wyrażenie treści definicji dla metod i właściwości uzyskać metod dostępu w języku C# 6 i została rozszerzona w języku C# w wersji 7.0.</span><span class="sxs-lookup"><span data-stu-id="6c961-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="6c961-108">Definicje treść wyrażenia mogą być używane z elementami członkowskimi typu wymienione w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="6c961-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="6c961-109">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6c961-109">Member</span></span>  |<span data-ttu-id="6c961-110">Obsługiwane począwszy od...</span><span class="sxs-lookup"><span data-stu-id="6c961-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="6c961-111">— Metoda</span><span class="sxs-lookup"><span data-stu-id="6c961-111">Method</span></span>](#methods)  |<span data-ttu-id="6c961-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="6c961-112">C# 6</span></span> |
|[<span data-ttu-id="6c961-113">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="6c961-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="6c961-114">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="6c961-114">C# 7.0</span></span> |
|[<span data-ttu-id="6c961-115">Finalizator</span><span class="sxs-lookup"><span data-stu-id="6c961-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="6c961-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="6c961-116">C# 7.0</span></span> |
|[<span data-ttu-id="6c961-117">Get właściwości</span><span class="sxs-lookup"><span data-stu-id="6c961-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="6c961-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="6c961-118">C# 6</span></span> |
|[<span data-ttu-id="6c961-119">Zestaw właściwości</span><span class="sxs-lookup"><span data-stu-id="6c961-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="6c961-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="6c961-120">C# 7.0</span></span> |
|[<span data-ttu-id="6c961-121">indeksator</span><span class="sxs-lookup"><span data-stu-id="6c961-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="6c961-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="6c961-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="6c961-123">Metody</span><span class="sxs-lookup"><span data-stu-id="6c961-123">Methods</span></span>

<span data-ttu-id="6c961-124">Metoda zabudowanych wyrażenie polega na jedno wyrażenie zwracające wartości, którego typ pasuje zwracany typ metody lub, w przypadku metod zwracających `void`, który wykonuje pewne operacje.</span><span class="sxs-lookup"><span data-stu-id="6c961-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="6c961-125">Na przykład typy zastąpienie tego <xref:System.Object.ToString%2A> metody zwykle zawierają jedno wyrażenie, które zwraca reprezentację ciągu bieżącego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6c961-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="6c961-126">W poniższym przykładzie zdefiniowano `Person` klasy, która zastępuje <xref:System.Object.ToString%2A> metody z definicją w treści wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6c961-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="6c961-127">Definiuje również `Show` metodę, która wyświetla nazwę do konsoli.</span><span class="sxs-lookup"><span data-stu-id="6c961-127">It also defines a `Show` method that displays a name to the console.</span></span> <span data-ttu-id="6c961-128">Należy pamiętać, że `return` — słowo kluczowe nie jest używany w `ToString` definicja treść wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6c961-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="6c961-129">Aby uzyskać więcej informacji, zobacz [metody (C# przewodnik programowania w języku)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="6c961-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="6c961-130">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="6c961-130">Constructors</span></span>

<span data-ttu-id="6c961-131">Definicja treść wyrażenia konstruktora zazwyczaj składa się z wyrażenia do jednej lub wywołanie metody obsługująca argumentów konstruktora lub Inicjuje stan wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6c961-131">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="6c961-132">W poniższym przykładzie zdefiniowano `Location` klasy, których Konstruktor ma jeden ciąg parametru o nazwie *nazwa*.</span><span class="sxs-lookup"><span data-stu-id="6c961-132">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="6c961-133">Definicja treść wyrażenia przypisuje argument `Name` właściwości.</span><span class="sxs-lookup"><span data-stu-id="6c961-133">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="6c961-134">Aby uzyskać więcej informacji, zobacz [konstruktory (C# przewodnik programowania w języku)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="6c961-134">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="6c961-135">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="6c961-135">Finalizers</span></span>

<span data-ttu-id="6c961-136">Definicja treść wyrażenia finalizator zwykle zawiera instrukcje oczyszczania, na przykład instrukcji, które zwolnić zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="6c961-136">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="6c961-137">W poniższym przykładzie zdefiniowano finalizatora, który używa wyrażenia treści definicji w celu wskazania, finalizator został wywołany.</span><span class="sxs-lookup"><span data-stu-id="6c961-137">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="6c961-138">Aby uzyskać więcej informacji, zobacz [finalizatory (C# przewodnik programowania w języku)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="6c961-138">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="6c961-139">Instrukcje get właściwości</span><span class="sxs-lookup"><span data-stu-id="6c961-139">Property get statements</span></span>

<span data-ttu-id="6c961-140">Jeśli wybierzesz do wdrożenia właściwość pobierająca metoda dostępu użytkownika, można użyć wyrażenia treści definicji dla pojedynczego wyrażeń, które po prostu zwracają wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="6c961-140">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="6c961-141">Należy pamiętać, że `return` instrukcja nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="6c961-141">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="6c961-142">W poniższym przykładzie zdefiniowano `Location.Name` właściwości, których właściwość metoda dostępu get zwraca wartość prywatna `locationName` pola, aby utworzyć kopię zapasową właściwości.</span><span class="sxs-lookup"><span data-stu-id="6c961-142">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="6c961-143">Właściwości tylko do odczytu, korzystających z definicji treść wyrażenia można zaimplementować bez jawnego `set` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6c961-143">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="6c961-144">Składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="6c961-144">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="6c961-145">W poniższym przykładzie zdefiniowano `Location` klasy, których tylko do odczytu `Name` właściwości jest zaimplementowany jako wyrażenie definicji treści, która zwraca wartość prywatna `locationName` pola.</span><span class="sxs-lookup"><span data-stu-id="6c961-145">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="6c961-146">Aby uzyskać więcej informacji, zobacz [właściwości (C# przewodnik programowania w języku)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="6c961-146">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="6c961-147">Instrukcje set właściwości</span><span class="sxs-lookup"><span data-stu-id="6c961-147">Property set statements</span></span>

<span data-ttu-id="6c961-148">Jeśli zdecydujesz się na siebie zaimplementować metodą dostępu set właściwości, można użyć wyrażenia treści definicji dla wyrażenia jeden wiersz, który przypisuje wartość do pola, aby utworzyć kopię zapasową właściwości.</span><span class="sxs-lookup"><span data-stu-id="6c961-148">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="6c961-149">W poniższym przykładzie zdefiniowano `Location.Name` właściwości, których właściwość set — instrukcja przypisuje jej argument wejściowy prywatnego `locationName` pola, aby utworzyć kopię zapasową właściwości.</span><span class="sxs-lookup"><span data-stu-id="6c961-149">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="6c961-150">Aby uzyskać więcej informacji, zobacz [właściwości (C# przewodnik programowania w języku)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="6c961-150">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="6c961-151">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="6c961-151">Indexers</span></span>

<span data-ttu-id="6c961-152">Podobnie jak właściwości, indeksatora get i metody dostępu set składa się z definicji treści wyrażenia metody dostępu get składa się z jednej instrukcji, która zwraca wartość lub metody dostępu set wykonuje przypisanie proste.</span><span class="sxs-lookup"><span data-stu-id="6c961-152">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="6c961-153">W poniższym przykładzie zdefiniowano klasę o nazwie `Sports` zawierającą wewnętrznego <xref:System.String> tablica, która zawiera nazwy liczba sportowych.</span><span class="sxs-lookup"><span data-stu-id="6c961-153">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="6c961-154">Zarówno indeksatora get, jak i metody dostępu set są zaimplementowane jako wyrażenie treści definicji.</span><span class="sxs-lookup"><span data-stu-id="6c961-154">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

<span data-ttu-id="6c961-155">Aby uzyskać więcej informacji, zobacz [indeksatorów (C# przewodnik programowania w języku)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="6c961-155">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>

