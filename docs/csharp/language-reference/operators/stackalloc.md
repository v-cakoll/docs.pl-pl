---
title: operator stackalloc — C# odwołania
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 3be4e827e75e4e26a34d9ed70423af5aa317e7fb
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025001"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="820e3-102">stackalloc — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="820e3-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="820e3-103">`stackalloc` Operator przydziela blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="820e3-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="820e3-104">Stos przydzielony blok pamięci, utworzony podczas wykonywania metody jest automatycznie odrzucane po powrocie z tej metody.</span><span class="sxs-lookup"><span data-stu-id="820e3-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="820e3-105">Nie można jawnie zwolnić pamięć alokowaną `stackalloc` operatora.</span><span class="sxs-lookup"><span data-stu-id="820e3-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="820e3-106">Blok pamięci przydzielony stos nie jest podlegają [wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md) i nie musi być przypinane z [ `fixed` instrukcji](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="820e3-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="820e3-107">Możesz przypisać wynik `stackalloc` operatora zmiennej jednego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="820e3-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="820e3-108">Począwszy od C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="820e3-108">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="820e3-109">Nie trzeba stosować [niebezpieczne](../keywords/unsafe.md) kontekstu po przypisaniu stosu przydzielony blok pamięci, aby <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> zmiennej.</span><span class="sxs-lookup"><span data-stu-id="820e3-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="820e3-110">Podczas pracy z tych typów, można użyć `stackalloc` wyrażenia w [warunkowego](conditional-operator.md) lub wyrażenia przypisania, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="820e3-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > <span data-ttu-id="820e3-111">Firma Microsoft zaleca używanie <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> typy do pracy z na stosie pamięci, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="820e3-111">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="820e3-112">A [typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="820e3-112">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="820e3-113">Jak pokazano na poprzednim przykładzie, należy użyć `unsafe` kontekście podczas pracy z typami wskaźników.</span><span class="sxs-lookup"><span data-stu-id="820e3-113">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

<span data-ttu-id="820e3-114">Zawartość nowo przydzielonego pamięci jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="820e3-114">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="820e3-115">Począwszy od C# 7.3, można użyć składni inicjatora tablicy definiowanie zawartości nowo alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="820e3-115">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="820e3-116">W poniższym przykładzie pokazano różne sposoby, aby to zrobić:</span><span class="sxs-lookup"><span data-stu-id="820e3-116">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="820e3-117">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="820e3-117">Security</span></span>

<span data-ttu-id="820e3-118">Korzystanie z `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu, w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="820e3-118">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="820e3-119">W przypadku wykrycia przepełnienie buforu tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo, że złośliwy kod jest wykonywany zakończenia procesu.</span><span class="sxs-lookup"><span data-stu-id="820e3-119">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="820e3-120">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="820e3-120">C# language specification</span></span>

<span data-ttu-id="820e3-121">Aby uzyskać więcej informacji, zobacz [alokacji stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="820e3-121">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="820e3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="820e3-122">See also</span></span>

- [<span data-ttu-id="820e3-123">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="820e3-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="820e3-124">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="820e3-124">C# operators</span></span>](index.md)
- [<span data-ttu-id="820e3-125">Wskaźnik związane z operatorów</span><span class="sxs-lookup"><span data-stu-id="820e3-125">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="820e3-126">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="820e3-126">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="820e3-127">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="820e3-127">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
