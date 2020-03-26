---
title: wyrażenie stackalloc — odwołanie do języka C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 2e99ce8b1e44dfa040c1acac799a3a55b375bd91
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546604"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="5946e-102">wyrażenie stackalloc (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="5946e-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="5946e-103">Wyrażenie `stackalloc` przydziela blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="5946e-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="5946e-104">Blok pamięci przydzielony stos utworzony podczas wykonywania metody jest automatycznie odrzucany, gdy ta metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="5946e-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="5946e-105">Nie można jawnie zwolnić `stackalloc`pamięci przydzielonej za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="5946e-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="5946e-106">Blok pamięci przydzielony do stosu nie podlega [wyrzucaniu elementów bezużytecznych](../../../standard/garbage-collection/index.md) i nie musi być przypięty [ `fixed` za](../keywords/fixed-statement.md)pomocą instrukcji .</span><span class="sxs-lookup"><span data-stu-id="5946e-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="5946e-107">Wynik `stackalloc` wyrażenia można przypisać do zmiennej jednego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="5946e-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="5946e-108">Począwszy od C# 7.2 <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5946e-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="5946e-109">Nie trzeba używać [niebezpiecznego](../keywords/unsafe.md) kontekstu podczas przypisywania bloku pamięci <xref:System.Span%601> <xref:System.ReadOnlySpan%601> przydzielonego stosu do lub zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5946e-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="5946e-110">Podczas pracy z tymi typami `stackalloc` można użyć wyrażenia w wyrażeniach [warunkowych](conditional-operator.md) lub przypisanych, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5946e-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="5946e-111">Począwszy od języka C# 8.0, można użyć `stackalloc` wyrażenia <xref:System.Span%601> <xref:System.ReadOnlySpan%601> wewnątrz innych wyrażeń, gdy jest dozwolone lub zmiennej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5946e-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="5946e-112">Zaleca się <xref:System.Span%601> <xref:System.ReadOnlySpan%601> używanie lub typy do pracy z pamięcią przydzieloną do stosu, gdy tylko jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5946e-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="5946e-113">[Typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5946e-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="5946e-114">Jak pokazano w poprzednim przykładzie, `unsafe` należy użyć kontekstu podczas pracy z typami wskaźników.</span><span class="sxs-lookup"><span data-stu-id="5946e-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="5946e-115">W przypadku typów wskaźników można użyć `stackalloc` wyrażenia tylko w deklaracji zmiennej lokalnej, aby zainicjować zmienną.</span><span class="sxs-lookup"><span data-stu-id="5946e-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="5946e-116">Ilość pamięci dostępnej na stosie jest ograniczona.</span><span class="sxs-lookup"><span data-stu-id="5946e-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="5946e-117">Jeśli przydzielić zbyt dużo pamięci <xref:System.StackOverflowException> na stosie, a jest wyrzucany.</span><span class="sxs-lookup"><span data-stu-id="5946e-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="5946e-118">Aby tego uniknąć, postępuj zgodnie z poniższymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="5946e-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="5946e-119">Ogranicz ilość pamięci `stackalloc`przydzielanej za pomocą:</span><span class="sxs-lookup"><span data-stu-id="5946e-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="5946e-120">Ponieważ ilość pamięci dostępnej na stosie zależy od środowiska, w którym kod jest wykonywany, zachowawczego podczas definiowania rzeczywistej wartości dopuszczalnej.</span><span class="sxs-lookup"><span data-stu-id="5946e-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="5946e-121">Unikaj `stackalloc` używania wewnętrznych pętli.</span><span class="sxs-lookup"><span data-stu-id="5946e-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="5946e-122">Przydzielić blok pamięci poza pętlę i użyć go ponownie wewnątrz pętli.</span><span class="sxs-lookup"><span data-stu-id="5946e-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="5946e-123">Zawartość nowo przydzielonej pamięci jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="5946e-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="5946e-124">Należy go zainicjować przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="5946e-124">You should initialize it before the use.</span></span> <span data-ttu-id="5946e-125">Na przykład można użyć <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> metody, która ustawia wszystkie elementy `T`na domyślną wartość typu .</span><span class="sxs-lookup"><span data-stu-id="5946e-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="5946e-126">Począwszy od języka C# 7.3, można użyć składni inicjatora tablicy do definiowania zawartości pamięci nowo przydzielonej.</span><span class="sxs-lookup"><span data-stu-id="5946e-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="5946e-127">W poniższym przykładzie przedstawiono różne sposoby, aby to zrobić:</span><span class="sxs-lookup"><span data-stu-id="5946e-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="5946e-128">W `stackalloc T[E]`wyrażeniu musi `T` być `E` [typem niezarządzanym](../builtin-types/unmanaged-types.md) i musi być wartością [int](../builtin-types/integral-numeric-types.md) nieujemną.</span><span class="sxs-lookup"><span data-stu-id="5946e-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="5946e-129">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="5946e-129">Security</span></span>

<span data-ttu-id="5946e-130">Użycie funkcji `stackalloc` automatycznego wykrywania przepełnienia buforu w czasie wykonywania języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="5946e-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="5946e-131">Jeśli zostanie wykryte przepełnienie buforu, proces zostanie zakończony tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo wykonania złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="5946e-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5946e-132">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5946e-132">C# language specification</span></span>

<span data-ttu-id="5946e-133">Aby uzyskać więcej informacji, zobacz sekcję [Alokacja stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) [specyfikacji języka C#](~/_csharplang/spec/introduction.md) i [Zezwolenie `stackalloc` w kontekstach zagnieżdżonych](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) uwaga propozycji funkcji.</span><span class="sxs-lookup"><span data-stu-id="5946e-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="5946e-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5946e-134">See also</span></span>

- [<span data-ttu-id="5946e-135">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5946e-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5946e-136">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5946e-136">C# operators</span></span>](index.md)
- [<span data-ttu-id="5946e-137">Operatory związane ze wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="5946e-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="5946e-138">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="5946e-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="5946e-139">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="5946e-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="5946e-140">Dos i nie stosalloc</span><span class="sxs-lookup"><span data-stu-id="5946e-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
