---
title: operator stackalloc — C# odwołanie
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9ef5f98f2b4973c5873417ecc9a71c187e7299b9
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182422"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="ed722-102">stackalloc — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="ed722-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="ed722-103">`stackalloc` Operator przydziela blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="ed722-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="ed722-104">Blok pamięci przydzielony przez stos utworzony podczas wykonywania metody jest automatycznie usuwany, gdy ta metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="ed722-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="ed722-105">Nie można jawnie zwolnić pamięci przydzieloną z `stackalloc` operatorem.</span><span class="sxs-lookup"><span data-stu-id="ed722-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="ed722-106">Przydzielony blok pamięci stosu nie podlega [wyrzucaniu elementów bezużytecznych](../../../standard/garbage-collection/index.md) i nie musi być przypięty za pomocą [ `fixed` instrukcji](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ed722-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="ed722-107">W `stackalloc T[E]`wyrażeniu `T` element musi być [typem niezarządzanym](../builtin-types/unmanaged-types.md) i `E` musi być wyrażeniem `int`typu.</span><span class="sxs-lookup"><span data-stu-id="ed722-107">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type `int`.</span></span>

<span data-ttu-id="ed722-108">Można przypisać wynik `stackalloc` operatora do zmiennej jednego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ed722-108">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="ed722-109">Począwszy od C# 7,2 <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ed722-109">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="ed722-110">Nie trzeba używać [niebezpiecznego](../keywords/unsafe.md) kontekstu, gdy przypiszesz blok pamięci przydzielony przez stos do <xref:System.Span%601> zmiennej <xref:System.ReadOnlySpan%601> lub.</span><span class="sxs-lookup"><span data-stu-id="ed722-110">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="ed722-111">Podczas pracy z tymi typami można użyć `stackalloc` wyrażenia w wyrażeniach [warunkowych](conditional-operator.md) lub przypisywania, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ed722-111">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="ed722-112">Począwszy od C# 8,0, można użyć `stackalloc` wyrażenia wewnątrz <xref:System.Span%601> innych wyrażeń, gdy zmienna lub <xref:System.ReadOnlySpan%601> jest dozwolona, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ed722-112">Starting with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="ed722-113">Zalecamy używanie <xref:System.Span%601> lub typy <xref:System.ReadOnlySpan%601> do pracy z przydzieloną pamięcią stosu, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="ed722-113">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="ed722-114">[Typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ed722-114">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="ed722-115">Jak pokazano w powyższym przykładzie, należy użyć `unsafe` kontekstu podczas pracy z typami wskaźników.</span><span class="sxs-lookup"><span data-stu-id="ed722-115">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="ed722-116">W przypadku typów wskaźnika można użyć `stackalloc` wyrażenia tylko w deklaracji zmiennej lokalnej, aby zainicjować zmienną.</span><span class="sxs-lookup"><span data-stu-id="ed722-116">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="ed722-117">Zawartość nowo przydzieloną pamięci jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="ed722-117">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="ed722-118">Począwszy od C# 7,3, można użyć składni inicjatora tablicy do zdefiniowania zawartości nowo przydzieloną pamięć.</span><span class="sxs-lookup"><span data-stu-id="ed722-118">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="ed722-119">Poniższy przykład ilustruje różne sposoby, aby to zrobić:</span><span class="sxs-lookup"><span data-stu-id="ed722-119">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="ed722-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ed722-120">Security</span></span>

<span data-ttu-id="ed722-121">Korzystanie z programu `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ed722-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="ed722-122">Jeśli wykryto przepełnienie buforu, proces zostaje zakończony jak najszybciej, aby zminimalizować prawdopodobieństwo wykonania złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="ed722-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ed722-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ed722-123">C# language specification</span></span>

<span data-ttu-id="ed722-124">Aby uzyskać więcej informacji, zobacz sekcję [Alokacja stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ed722-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed722-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed722-125">See also</span></span>

- [<span data-ttu-id="ed722-126">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="ed722-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ed722-127">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="ed722-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="ed722-128">Operatory powiązane z wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="ed722-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="ed722-129">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="ed722-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="ed722-130">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="ed722-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
