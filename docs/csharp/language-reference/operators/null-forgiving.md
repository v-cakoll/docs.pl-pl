---
title: '! (null-wyrozumiały) operator - odwołanie C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 36bfa46cebd2b35c4985dfc23dbe84f8f5dc9201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846324"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="5c32b-103">!</span><span class="sxs-lookup"><span data-stu-id="5c32b-103">!</span></span> <span data-ttu-id="5c32b-104">operator (wyrozumiały null) (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="5c32b-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="5c32b-105">Dostępne w języku C# 8.0 i `!` nowszych, operator unary postfix jest operatorem wyrozumiały mównika.</span><span class="sxs-lookup"><span data-stu-id="5c32b-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="5c32b-106">W włączonym [kontekście adnotacji nullable](../../nullable-references.md#nullable-annotation-context), należy użyć null-wyrozumiały operator zadeklarować, że wyrażenie `x` typu odwołania nie `null`jest : `x!`.</span><span class="sxs-lookup"><span data-stu-id="5c32b-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="5c32b-107">Operator prefiksu `!` unary jest [operatorem negacji logicznej](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="5c32b-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="5c32b-108">Operator wyrozumiały nie ma wpływu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5c32b-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="5c32b-109">Ma to wpływ tylko na analizę przepływu statycznego kompilatora, zmieniając stan zerowy wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5c32b-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="5c32b-110">W czasie wykonywania wyrażenie `x!` oblicza wynik wyrażenia `x`źródłowego .</span><span class="sxs-lookup"><span data-stu-id="5c32b-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="5c32b-111">Aby uzyskać więcej informacji na temat funkcji typów odwołań z możliwością null, zobacz [Typy odwołań nullable](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="5c32b-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="5c32b-112">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5c32b-112">Examples</span></span>

<span data-ttu-id="5c32b-113">Jednym z przypadków użycia operatora wyrozumiałego jest testowanie logiki sprawdzania poprawności argumentu.</span><span class="sxs-lookup"><span data-stu-id="5c32b-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="5c32b-114">Rozważmy na przykład następującą klasę:</span><span class="sxs-lookup"><span data-stu-id="5c32b-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="5c32b-115">Za pomocą [struktury testów MSTest](../../../core/testing/unit-testing-with-mstest.md)można utworzyć następujący test dla logiki sprawdzania poprawności w konstruktorze:</span><span class="sxs-lookup"><span data-stu-id="5c32b-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="5c32b-116">Bez operatora wyrozumiałego dla wartości null kompilator generuje `Warning CS8625: Cannot convert null literal to non-nullable reference type`następujące ostrzeżenie dla poprzedniego kodu: .</span><span class="sxs-lookup"><span data-stu-id="5c32b-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="5c32b-117">Za pomocą operatora wyrozumiały null, informujesz kompilator, że przekazywanie `null` jest oczekiwane i nie powinien być ostrzeżony.</span><span class="sxs-lookup"><span data-stu-id="5c32b-117">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="5c32b-118">Można również użyć null-wyrozumiały operator, gdy na `null` pewno wiesz, że wyrażenie nie może być, ale kompilator nie udaje się rozpoznać, że.</span><span class="sxs-lookup"><span data-stu-id="5c32b-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="5c32b-119">W poniższym przykładzie, `IsValid` jeśli `true`metoda zwraca, `null` jej argument nie jest i można bezpiecznie wyłuskać go:</span><span class="sxs-lookup"><span data-stu-id="5c32b-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="5c32b-120">Bez operatora wyrozumiałego null kompilator generuje `p.Name` następujące `Warning CS8602: Dereference of a possibly null reference`ostrzeżenie dla kodu: .</span><span class="sxs-lookup"><span data-stu-id="5c32b-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="5c32b-121">Jeśli można zmodyfikować `IsValid` metodę, można użyć [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) atrybut poinformować kompilator, że argument `IsValid` metody nie może być, `null` gdy metoda zwraca: `true`</span><span class="sxs-lookup"><span data-stu-id="5c32b-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="5c32b-122">W poprzednim przykładzie nie trzeba używać null-wyrozumiały operator, ponieważ kompilator ma `p` wystarczająco `null` dużo `if` informacji, aby dowiedzieć się, że nie może być wewnątrz instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5c32b-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="5c32b-123">Aby uzyskać więcej informacji na temat atrybutów, które umożliwiają podanie dodatkowych informacji o stanie zerowym zmiennej, zobacz [Uaktualnianie interfejsów API z atrybutami definiującymi oczekiwania null](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5c32b-123">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5c32b-124">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5c32b-124">C# language specification</span></span>

<span data-ttu-id="5c32b-125">Aby uzyskać więcej informacji, zobacz [null-wyrozumiały operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) sekcji [wersji roboczej specyfikacji typów odwołań nullable](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="5c32b-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5c32b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c32b-126">See also</span></span>

- [<span data-ttu-id="5c32b-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5c32b-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5c32b-128">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5c32b-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="5c32b-129">Samouczek: Projektowanie z typami odwołań z wartościami null</span><span class="sxs-lookup"><span data-stu-id="5c32b-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
