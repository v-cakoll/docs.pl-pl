---
title: operator stackalloc — C# odwołanie
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 5654cae622cd94c8dad7e58fbc8a99fcf48391a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712627"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="87860-102">stackalloc — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="87860-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="87860-103">Operator `stackalloc` przydziela blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="87860-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="87860-104">Blok pamięci przydzielony przez stos utworzony podczas wykonywania metody jest automatycznie usuwany, gdy ta metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="87860-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="87860-105">Nie można jawnie zwolnić pamięci przydzieloną za pomocą operatora `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="87860-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="87860-106">Przydzielony blok pamięci stosu nie podlega [wyrzucaniu elementów bezużytecznych](../../../standard/garbage-collection/index.md) i nie musi być przypięty za pomocą [instrukcji`fixed`](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="87860-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="87860-107">Wynik operatora `stackalloc` można przypisać do zmiennej jednego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="87860-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="87860-108">Począwszy od C# 7,2, <xref:System.Span%601?displayProperty=nameWithType> lub <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="87860-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="87860-109">Nie trzeba używać [niebezpiecznego](../keywords/unsafe.md) kontekstu, gdy przypiszesz blok pamięci przydzielony przez stos do zmiennej <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="87860-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="87860-110">Podczas pracy z tymi typami można użyć wyrażenia `stackalloc` w wyrażeniach [warunkowych](conditional-operator.md) lub przypisywania, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="87860-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="87860-111">Począwszy od C# 8,0, można użyć wyrażenia `stackalloc` w innych wyrażeniach za każdym razem, gdy zmienna <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> jest dozwolona, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="87860-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="87860-112">Zaleca się używanie typów <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> do pracy z przydzieloną pamięcią, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="87860-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="87860-113">[Typ wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="87860-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="87860-114">Jak pokazano w powyższym przykładzie, należy użyć kontekstu `unsafe` podczas pracy z typami wskaźników.</span><span class="sxs-lookup"><span data-stu-id="87860-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="87860-115">W przypadku typów wskaźnika można użyć wyrażenia `stackalloc` tylko w deklaracji zmiennej lokalnej, aby zainicjować zmienną.</span><span class="sxs-lookup"><span data-stu-id="87860-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="87860-116">Zawartość nowo przydzieloną pamięci jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="87860-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="87860-117">Począwszy od C# 7,3, można użyć składni inicjatora tablicy do zdefiniowania zawartości nowo przydzieloną pamięć.</span><span class="sxs-lookup"><span data-stu-id="87860-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="87860-118">Poniższy przykład ilustruje różne sposoby, aby to zrobić:</span><span class="sxs-lookup"><span data-stu-id="87860-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="87860-119">W `stackalloc T[E]`Expression `T` musi być [typem niezarządzanym](../builtin-types/unmanaged-types.md) , a `E` musi być wyrażeniem typu [int](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="87860-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="87860-120">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="87860-120">Security</span></span>

<span data-ttu-id="87860-121">Użycie `stackalloc` powoduje automatyczne włączenie funkcji wykrywania przepełnienia buforu w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="87860-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="87860-122">Jeśli wykryto przepełnienie buforu, proces zostaje zakończony jak najszybciej, aby zminimalizować prawdopodobieństwo wykonania złośliwego kodu.</span><span class="sxs-lookup"><span data-stu-id="87860-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="87860-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="87860-123">C# language specification</span></span>

<span data-ttu-id="87860-124">Aby uzyskać więcej informacji, zapoznaj się z sekcją [Alokacja stosu](~/_csharplang/spec/unsafe-code.md#stack-allocation) w temacie [ C# Specyfikacja języka](~/_csharplang/spec/introduction.md) i opcja [Zezwalaj `stackalloc` w przypadku zagnieżdżonych kontekstów](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="87860-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="87860-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87860-125">See also</span></span>

- [<span data-ttu-id="87860-126">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="87860-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="87860-127">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="87860-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="87860-128">Operatory powiązane z wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="87860-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="87860-129">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="87860-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="87860-130">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="87860-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
