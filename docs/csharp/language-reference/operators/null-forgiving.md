---
title: '! (null-łagodniejszej) — C# odwołanie'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 865e55a28e2f3db85d50a81f6ab29c354ee3c62a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319097"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="71850-103">!</span><span class="sxs-lookup"><span data-stu-id="71850-103">!</span></span> <span data-ttu-id="71850-104">(null-łagodniejszej) — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="71850-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="71850-105">Dostępne w C# 8,0 i nowszych operatory jednoargumentowe `!` jest operatorem null-łagodniejszej.</span><span class="sxs-lookup"><span data-stu-id="71850-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="71850-106">W kontekście włączonego [dopuszczającego wartość](../../nullable-references.md#nullable-annotation-context)null należy użyć operatora null-łagodniejszej, aby zadeklarować, że wyrażenie `x` typu referencyjnego nie ma wartości null: `x!`.</span><span class="sxs-lookup"><span data-stu-id="71850-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't null: `x!`.</span></span> <span data-ttu-id="71850-107">Prefiks jednoargumentowy `!` operator jest [logicznym operatorem negacji](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="71850-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="71850-108">Operator null-łagodniejszej nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="71850-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="71850-109">Ma wpływ tylko na analizę przepływu statycznego kompilatora przez zmianę stanu null wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="71850-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="71850-110">W czasie wykonywania wyrażenie `x!` szacuje wynik wyrażenia bazowego `x`.</span><span class="sxs-lookup"><span data-stu-id="71850-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="71850-111">Aby uzyskać więcej informacji na temat funkcji typów referencyjnych dopuszczających wartość null, zobacz [typy referencyjne dopuszczające wartość null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="71850-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="71850-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="71850-112">Examples</span></span>

<span data-ttu-id="71850-113">Jednym z przypadków użycia operatora null-łagodniejszej jest Testowanie logiki walidacji argumentów.</span><span class="sxs-lookup"><span data-stu-id="71850-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="71850-114">Rozważmy na przykład następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="71850-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="71850-115">Używając [platformy testów MSTest](../../../core/testing/unit-testing-with-mstest.md), można utworzyć następujący test dla logiki walidacji w konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="71850-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="71850-116">Bez operatora null łagodniejszej kompilator generuje następujące ostrzeżenie dla poprzedniego kodu: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="71850-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="71850-117">Korzystając z operatora łagodniejszej o wartości null, można poinformować kompilator, że oczekiwane jest przekazywanie `null` i nie powinno być ostrzegane o.</span><span class="sxs-lookup"><span data-stu-id="71850-117">With the use of the null-forgiving operator, you let the compiler know that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="71850-118">Można również użyć operatora o wartości null-łagodniejszej, gdy wiadomo, że wyrażenie nie może być `null`, ale kompilator nie rozpoznaje tego.</span><span class="sxs-lookup"><span data-stu-id="71850-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="71850-119">W poniższym przykładzie, jeśli metoda `IsValid` zwróci `true`, jego argument nie jest `null` i można bezpiecznie go wywoływać:</span><span class="sxs-lookup"><span data-stu-id="71850-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="71850-120">Bez operatora null łagodniejszej kompilator generuje następujące ostrzeżenie dla kodu `p.Name`: `Warning CS8602: Dereference of a possibly null reference`.</span><span class="sxs-lookup"><span data-stu-id="71850-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="71850-121">Jeśli można zmodyfikować metodę `IsValid`, można użyć atrybutu [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) , aby dać kompilatorowi, że argument metody `IsValid` nie może być `null`, gdy metoda zwraca `true`:</span><span class="sxs-lookup"><span data-stu-id="71850-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to let the compiler know that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="71850-122">W poprzednim przykładzie nie trzeba używać operatora łagodniejszej o wartości null, ponieważ kompilator ma wystarczającą ilość informacji, aby dowiedzieć się, że `p` nie może być `null` w instrukcji `if`.</span><span class="sxs-lookup"><span data-stu-id="71850-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="71850-123">Aby uzyskać więcej informacji o atrybutach, które umożliwiają określenie dodatkowych informacji o stanie null zmiennej, zobacz [uaktualnianie interfejsów API z atrybutami w celu zdefiniowania oczekiwań o wartości null](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="71850-123">For more information about the attributes that allow you to specify additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="71850-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="71850-124">C# language specification</span></span>

<span data-ttu-id="71850-125">Aby uzyskać więcej informacji, zobacz sekcję [operator null-łagodniejszej](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) w [wersji roboczej specyfikacji typów odwołań dopuszczających wartość null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="71850-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="71850-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71850-126">See also</span></span>

- [<span data-ttu-id="71850-127">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="71850-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="71850-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="71850-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="71850-129">Samouczek: Projektowanie przy użyciu typów referencyjnych dopuszczających wartość null</span><span class="sxs-lookup"><span data-stu-id="71850-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
