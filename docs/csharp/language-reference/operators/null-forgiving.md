---
title: '! (null-wyrozumiały) operator - odwołanie C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: f3d06dec42ba117cd30dbf4d05fa4a6f594e57e5
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82101981"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="a55eb-103">!</span><span class="sxs-lookup"><span data-stu-id="a55eb-103">!</span></span> <span data-ttu-id="a55eb-104">(zero-wyrozumiały) operator (odwołanie C#)</span><span class="sxs-lookup"><span data-stu-id="a55eb-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="a55eb-105">Dostępne w języku C# 8.0 i `!` nowszych, operator poprawek bezwysyłkowych jest operatorem wyrozumiałości zerowej.</span><span class="sxs-lookup"><span data-stu-id="a55eb-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="a55eb-106">W włączonym [kontekście adnotacji z możliwością null,](../../nullable-references.md#nullable-annotation-context)operator wyrozumiały o wartości null, aby zadeklarować, że wyrażenie `x` typu odwołania nie `null`jest : `x!`.</span><span class="sxs-lookup"><span data-stu-id="a55eb-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="a55eb-107">Operator prefiksu dwuobrodczego `!` jest [operatorem logicznego negacji](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="a55eb-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="a55eb-108">Operator wyrozumiały null nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a55eb-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="a55eb-109">Wpływa tylko na analizę przepływu statycznego kompilatora, zmieniając stan zerowy wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a55eb-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="a55eb-110">W czasie wykonywania `x!` wyrażenie ocenia wynik wyrażenia `x`źródłowego .</span><span class="sxs-lookup"><span data-stu-id="a55eb-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="a55eb-111">Aby uzyskać więcej informacji na temat funkcji typy odwołań z dopuszczalną wartością null, zobacz [Typy odwołań możliwe do wartości null](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="a55eb-111">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="a55eb-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a55eb-112">Examples</span></span>

<span data-ttu-id="a55eb-113">Jednym z przypadków użycia operatora null-forgiving jest w testowaniu logiki sprawdzania poprawności argumentu.</span><span class="sxs-lookup"><span data-stu-id="a55eb-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="a55eb-114">Rozważmy na przykład następującą klasę:</span><span class="sxs-lookup"><span data-stu-id="a55eb-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="a55eb-115">Za pomocą [mstest test framework](../../../core/testing/unit-testing-with-mstest.md), można utworzyć następujący test dla logiki sprawdzania poprawności w konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="a55eb-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="a55eb-116">Bez operatora wyrozumiałości zerowej kompilator generuje następujące `Warning CS8625: Cannot convert null literal to non-nullable reference type`ostrzeżenie dla poprzedniego kodu: .</span><span class="sxs-lookup"><span data-stu-id="a55eb-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="a55eb-117">Za pomocą operatora null-wyrozumiały, `null` informujesz kompilator, że przekazywanie jest oczekiwane i nie powinny być ostrzegane o.</span><span class="sxs-lookup"><span data-stu-id="a55eb-117">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="a55eb-118">Można również użyć operatora wyrozumiałości zerowej, `null` gdy na pewno wiadomo, że wyrażenie nie może być, ale kompilator nie zarządza rozpoznać.</span><span class="sxs-lookup"><span data-stu-id="a55eb-118">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="a55eb-119">W poniższym przykładzie, jeśli `IsValid` metoda zwraca `true`, jej argument nie `null` jest i można bezpiecznie wyłuskać go:</span><span class="sxs-lookup"><span data-stu-id="a55eb-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="a55eb-120">Bez operatora wyrozumiałości zerowej kompilator `p.Name` generuje `Warning CS8602: Dereference of a possibly null reference`następujące ostrzeżenie dla kodu: .</span><span class="sxs-lookup"><span data-stu-id="a55eb-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="a55eb-121">Jeśli można `IsValid` zmodyfikować metodę, można użyć [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) atrybut poinformować kompilator, że argument `IsValid` metody nie może być, `null` gdy metoda zwraca: `true`</span><span class="sxs-lookup"><span data-stu-id="a55eb-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="a55eb-122">W poprzednim przykładzie nie trzeba używać operatora wyrozumiałości zerowej, ponieważ kompilator ma wystarczająco dużo informacji, aby dowiedzieć się, że `p` nie może znajdować `null` się wewnątrz `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a55eb-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="a55eb-123">Aby uzyskać więcej informacji na temat atrybutów, które umożliwiają dostarczenie dodatkowych informacji o stanie zerowym zmiennej, zobacz [Uaktualnianie interfejsów API z atrybutami definiuuuujymicy oczekiwania zerowe](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="a55eb-123">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a55eb-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a55eb-124">C# language specification</span></span>

<span data-ttu-id="a55eb-125">Aby uzyskać więcej informacji, zobacz [sekcję operatora z wyrozumiałym o wartości null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) [w wersji roboczej specyfikacji typów odwołań, których nie można unieważnić.](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)</span><span class="sxs-lookup"><span data-stu-id="a55eb-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a55eb-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a55eb-126">See also</span></span>

- [<span data-ttu-id="a55eb-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a55eb-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a55eb-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a55eb-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="a55eb-129">Samouczek: Projektowanie z typami odwołań z dopuszczalnymi do wartości null</span><span class="sxs-lookup"><span data-stu-id="a55eb-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
