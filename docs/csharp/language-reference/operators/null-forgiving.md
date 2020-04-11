---
title: '! (null-wyrozumiały) operator - odwołanie C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 658043f8d5e149064f6da328657b2ccef9b5da94
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121440"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="97586-103">!</span><span class="sxs-lookup"><span data-stu-id="97586-103">!</span></span> <span data-ttu-id="97586-104">(zero-wyrozumiały) operator (odwołanie C#)</span><span class="sxs-lookup"><span data-stu-id="97586-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="97586-105">Dostępne w języku C# 8.0 i `!` nowszych, operator poprawek bezwysyłkowych jest operatorem wyrozumiałości zerowej.</span><span class="sxs-lookup"><span data-stu-id="97586-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="97586-106">W włączonym [kontekście adnotacji z możliwością null,](../../nullable-references.md#nullable-annotation-context)operator wyrozumiały o wartości null, aby zadeklarować, że wyrażenie `x` typu odwołania nie `null`jest : `x!`.</span><span class="sxs-lookup"><span data-stu-id="97586-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="97586-107">Operator prefiksu dwuobrodczego `!` jest [operatorem logicznego negacji](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="97586-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="97586-108">Operator wyrozumiały null nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="97586-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="97586-109">Wpływa tylko na analizę przepływu statycznego kompilatora, zmieniając stan zerowy wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="97586-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="97586-110">W czasie wykonywania `x!` wyrażenie ocenia wynik wyrażenia `x`źródłowego .</span><span class="sxs-lookup"><span data-stu-id="97586-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="97586-111">Aby uzyskać więcej informacji na temat funkcji typy odwołań z dopuszczalną wartością null, zobacz [Typy odwołań możliwe do wartości null](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="97586-111">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="97586-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="97586-112">Examples</span></span>

<span data-ttu-id="97586-113">Jednym z przypadków użycia operatora null-forgiving jest w testowaniu logiki sprawdzania poprawności argumentu.</span><span class="sxs-lookup"><span data-stu-id="97586-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="97586-114">Rozważmy na przykład następującą klasę:</span><span class="sxs-lookup"><span data-stu-id="97586-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="97586-115">Za pomocą [mstest test framework](../../../core/testing/unit-testing-with-mstest.md), można utworzyć następujący test dla logiki sprawdzania poprawności w konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="97586-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="97586-116">Bez operatora wyrozumiałości zerowej kompilator generuje następujące `Warning CS8625: Cannot convert null literal to non-nullable reference type`ostrzeżenie dla poprzedniego kodu: .</span><span class="sxs-lookup"><span data-stu-id="97586-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="97586-117">Za pomocą operatora null-wyrozumiały, `null` informujesz kompilator, że przekazywanie jest oczekiwane i nie powinny być ostrzegane o.</span><span class="sxs-lookup"><span data-stu-id="97586-117">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="97586-118">Można również użyć operatora wyrozumiałości zerowej, `null` gdy na pewno wiesz, że wyrażenie nie może być, ale kompilator nie zarządza rozpoznać.</span><span class="sxs-lookup"><span data-stu-id="97586-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="97586-119">W poniższym przykładzie, jeśli `IsValid` metoda zwraca `true`, jej argument nie `null` jest i można bezpiecznie wyłuskać go:</span><span class="sxs-lookup"><span data-stu-id="97586-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="97586-120">Bez operatora wyrozumiałości zerowej kompilator `p.Name` generuje `Warning CS8602: Dereference of a possibly null reference`następujące ostrzeżenie dla kodu: .</span><span class="sxs-lookup"><span data-stu-id="97586-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="97586-121">Jeśli można `IsValid` zmodyfikować metodę, można użyć [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) atrybut poinformować kompilator, że argument `IsValid` metody nie może być, `null` gdy metoda zwraca: `true`</span><span class="sxs-lookup"><span data-stu-id="97586-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="97586-122">W poprzednim przykładzie nie trzeba używać operatora wyrozumiałości zerowej, ponieważ kompilator ma wystarczająco dużo informacji, aby dowiedzieć się, że `p` nie może znajdować `null` się wewnątrz `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="97586-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="97586-123">Aby uzyskać więcej informacji na temat atrybutów, które umożliwiają dostarczenie dodatkowych informacji o stanie zerowym zmiennej, zobacz [Uaktualnianie interfejsów API z atrybutami definiuuuujymicy oczekiwania zerowe](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="97586-123">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="97586-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="97586-124">C# language specification</span></span>

<span data-ttu-id="97586-125">Aby uzyskać więcej informacji, zobacz [sekcję operatora z wyrozumiałym o wartości null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) [w wersji roboczej specyfikacji typów odwołań, których nie można unieważnić.](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)</span><span class="sxs-lookup"><span data-stu-id="97586-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="97586-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97586-126">See also</span></span>

- [<span data-ttu-id="97586-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="97586-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="97586-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="97586-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="97586-129">Samouczek: Projektowanie z typami odwołań z dopuszczalnymi do wartości null</span><span class="sxs-lookup"><span data-stu-id="97586-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
