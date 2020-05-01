---
title: '! operator (null-łagodniejszej) — odwołanie w C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 2a8db2882968dbcbe6a8868ab6fe1c128c94a41f
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624881"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="7b646-103">!</span><span class="sxs-lookup"><span data-stu-id="7b646-103">!</span></span> <span data-ttu-id="7b646-104">(null-łagodniejszej) — operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7b646-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="7b646-105">Dostępne w języku C# 8,0 i nowszych, jednoargumentowy operator przyrostkowy `!` jest operatorem łagodniejszej o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7b646-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="7b646-106">W włączonym [kontekście dopuszczającym wartość null](../../nullable-references.md#nullable-annotation-context)należy użyć operatora null-łagodniejszej, aby zadeklarować wyrażenie `x` typu referencyjnego `null`nie `x!`jest:.</span><span class="sxs-lookup"><span data-stu-id="7b646-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="7b646-107">Jednoargumentowy `!` operator prefiksu jest [logicznym operatorem negacji](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="7b646-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="7b646-108">Operator null-łagodniejszej nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7b646-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="7b646-109">Ma wpływ tylko na analizę przepływu statycznego kompilatora przez zmianę stanu null wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7b646-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="7b646-110">W czasie wykonywania wyrażenie `x!` oblicza wynik wyrażenia `x`bazowego.</span><span class="sxs-lookup"><span data-stu-id="7b646-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="7b646-111">W języku C# 8 operator łagodniejszej o wartości null kończy listę poprzednich operacji [warunkowych o wartości null](member-access-operators.md#null-conditional-operators--and-) .</span><span class="sxs-lookup"><span data-stu-id="7b646-111">In C# 8, the null-forgiving operator terminates the list of preceding [null-conditional](member-access-operators.md#null-conditional-operators--and-) operations.</span></span> <span data-ttu-id="7b646-112">Na przykład wyrażenie `x?.y!.z` jest analizowane jako `(x?.y)!.z`.</span><span class="sxs-lookup"><span data-stu-id="7b646-112">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="7b646-113">Ze względu na tę `z` interpretację, jest `x` oceniane `null`, nawet jeśli jest, co <xref:System.NullReferenceException>może skutkować.</span><span class="sxs-lookup"><span data-stu-id="7b646-113">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="7b646-114">Aby uzyskać więcej informacji na temat funkcji typów referencyjnych dopuszczających wartość null, zobacz [typy referencyjne dopuszczające wartość null](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="7b646-114">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="7b646-115">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7b646-115">Examples</span></span>

<span data-ttu-id="7b646-116">Jednym z przypadków użycia operatora null-łagodniejszej jest Testowanie logiki walidacji argumentów.</span><span class="sxs-lookup"><span data-stu-id="7b646-116">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="7b646-117">Rozważmy na przykład następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="7b646-117">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="7b646-118">Używając [platformy testów MSTest](../../../core/testing/unit-testing-with-mstest.md), można utworzyć następujący test dla logiki walidacji w konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="7b646-118">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="7b646-119">Bez operatora null łagodniejszej kompilator generuje następujące ostrzeżenie dla poprzedniego kodu: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="7b646-119">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="7b646-120">Za pomocą operatora null-łagodniejszej, należy poinformować kompilator, że oczekiwano `null` , i nie powinien być ostrzegany o.</span><span class="sxs-lookup"><span data-stu-id="7b646-120">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="7b646-121">Można również użyć operatora o wartości null-łagodniejszej, gdy wiadomo, że wyrażenie nie może być `null` , ale kompilator nie rozpoznaje tego elementu.</span><span class="sxs-lookup"><span data-stu-id="7b646-121">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="7b646-122">W poniższym przykładzie, jeśli metoda zwraca `IsValid` `true`, jego argument nie `null` jest i można bezpiecznie odwoływać się do niego:</span><span class="sxs-lookup"><span data-stu-id="7b646-122">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="7b646-123">Bez operatora null łagodniejszej kompilator generuje następujące ostrzeżenie dla `p.Name` kodu:. `Warning CS8602: Dereference of a possibly null reference`</span><span class="sxs-lookup"><span data-stu-id="7b646-123">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="7b646-124">`IsValid` Jeśli można zmodyfikować metodę, można użyć atrybutu [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) do informowania kompilatora, że `IsValid` argument metody nie może być `null` , gdy metoda zwraca: `true`</span><span class="sxs-lookup"><span data-stu-id="7b646-124">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="7b646-125">W poprzednim przykładzie nie trzeba używać operatora o wartości null-łagodniejszej, ponieważ kompilator ma wystarczającą ilość informacji, aby dowiedzieć się, `p` że nie `null` może znajdować się wewnątrz `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7b646-125">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="7b646-126">Aby uzyskać więcej informacji o atrybutach, które umożliwiają podanie dodatkowych informacji o stanie null zmiennej, zobacz [uaktualnianie interfejsów API z atrybutami w celu zdefiniowania oczekiwań o wartości null](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="7b646-126">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7b646-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7b646-127">C# language specification</span></span>

<span data-ttu-id="7b646-128">Aby uzyskać więcej informacji, zobacz sekcję [operator null-łagodniejszej](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) w [wersji roboczej specyfikacji typów odwołań dopuszczających wartość null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="7b646-128">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b646-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b646-129">See also</span></span>

- [<span data-ttu-id="7b646-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7b646-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7b646-131">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="7b646-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="7b646-132">Samouczek: Projektowanie przy użyciu typów referencyjnych dopuszczających wartość null</span><span class="sxs-lookup"><span data-stu-id="7b646-132">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
