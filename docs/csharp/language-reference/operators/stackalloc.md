---
title: operator stackalloc — odwołanie do języka C#
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846258"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="7933d-102">operator stackalloc (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="7933d-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="7933d-103">Operator `stackalloc` przydziela blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="7933d-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="7933d-104">Stos przydzielonego bloku pamięci utworzonego podczas wykonywania metody jest automatycznie odrzucany po zwrocie tej metody.</span><span class="sxs-lookup"><span data-stu-id="7933d-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="7933d-105">Nie można jawnie zwolnić `stackalloc` pamięci przydzielonej operatorowi.</span><span class="sxs-lookup"><span data-stu-id="7933d-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="7933d-106">Blok pamięci przydzielonej stosnie nie podlega [wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md) i nie musi być przypięty za pomocą [ `fixed` instrukcji](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7933d-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="7933d-107">Wynik `stackalloc` operatora można przypisać do zmiennej jednego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="7933d-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="7933d-108">Począwszy od Języka C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7933d-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="7933d-109">Nie trzeba używać [niebezpiecznego](../keywords/unsafe.md) kontekstu podczas przypisywania stosu <xref:System.Span%601> przydzielonego bloku pamięci do lub <xref:System.ReadOnlySpan%601> zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7933d-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="7933d-110">Podczas pracy z tymi typami `stackalloc` można użyć wyrażenia w wyrażeniach [warunkowych](conditional-operator.md) lub przypisanych, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7933d-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="7933d-111">Począwszy od języka C# 8.0, można użyć `stackalloc` wyrażenia <xref:System.Span%601> <xref:System.ReadOnlySpan%601> wewnątrz innych wyrażeń, gdy lub zmienna jest dozwolone, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7933d-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="7933d-112">Zaleca się <xref:System.Span%601> <xref:System.ReadOnlySpan%601> używanie lub typy do pracy z pamięcią przydzieloną stosu, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="7933d-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="7933d-113">[Typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7933d-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="7933d-114">Jak pokazano w poprzednim przykładzie, `unsafe` należy użyć kontekstu podczas pracy z typami wskaźników.</span><span class="sxs-lookup"><span data-stu-id="7933d-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="7933d-115">W przypadku typów wskaźników można użyć `stackalloc` wyrażenia tylko w deklaracji zmiennej lokalnej do zainicjowania zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7933d-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="7933d-116">Zawartość nowo przydzielonej pamięci jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="7933d-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="7933d-117">Począwszy od C# 7.3, można użyć składni inicjatora tablicy do definiowania zawartości nowo przydzielonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="7933d-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="7933d-118">W poniższym przykładzie przedstawiono różne sposoby, aby to zrobić:</span><span class="sxs-lookup"><span data-stu-id="7933d-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="7933d-119">W `stackalloc T[E]`wyrażeniu musi `T` być `E` [typem niezarządzanym](../builtin-types/unmanaged-types.md) i musi być wyrażeniem typu [int](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="7933d-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="7933d-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="7933d-120">Security</span></span>

<span data-ttu-id="7933d-121">Użycie `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu w czasie wykonywania języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="7933d-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="7933d-122">W przypadku wykrycia przepełnienia buforu proces jest zakończony tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo wykonania złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="7933d-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7933d-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7933d-123">C# language specification</span></span>

<span data-ttu-id="7933d-124">Aby uzyskać więcej informacji, zobacz [alokacji stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) sekcji [specyfikacji języka C#](~/_csharplang/spec/introduction.md) i [zezwolenie w `stackalloc` kontekstach zagnieżdżonych](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) uwaga propozycji funkcji.</span><span class="sxs-lookup"><span data-stu-id="7933d-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="7933d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7933d-125">See also</span></span>

- [<span data-ttu-id="7933d-126">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7933d-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7933d-127">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="7933d-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="7933d-128">Operatory związane ze wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="7933d-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="7933d-129">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7933d-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="7933d-130">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="7933d-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
