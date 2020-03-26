---
title: stała instrukcja - Odwołanie do języka C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 53bee82bf24a847b0b21ed2375d09a6303d4fe48
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507194"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="7f071-102">fixed — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7f071-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="7f071-103">Instrukcja `fixed` uniemożliwia moduł zbierający elementy bezużyteczne przeniesienie zmiennej ruchomej.</span><span class="sxs-lookup"><span data-stu-id="7f071-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="7f071-104">Instrukcja `fixed` jest dozwolona tylko w [niebezpiecznym](unsafe.md) kontekście.</span><span class="sxs-lookup"><span data-stu-id="7f071-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="7f071-105">Za pomocą słowa `fixed` kluczowego można również utworzyć [bufory o stałym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="7f071-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="7f071-106">Instrukcja `fixed` ustawia wskaźnik do zmiennej zarządzanej i "pins" tej zmiennej podczas wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7f071-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="7f071-107">Wskaźniki do ruchomych zmiennych zarządzanych są `fixed` przydatne tylko w kontekście.</span><span class="sxs-lookup"><span data-stu-id="7f071-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="7f071-108">Bez `fixed` kontekstu wyrzucania elementów bezużytecznych można przenieść zmienne nieprzewidywalnie.</span><span class="sxs-lookup"><span data-stu-id="7f071-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="7f071-109">Kompilator języka C# umożliwia przypisanie wskaźnika `fixed` do zmiennej zarządzanej w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7f071-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="7f071-110">Wskaźnik można zainicjować przy użyciu tablicy, ciągu, buforu o stałym rozmiarze lub adresu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7f071-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="7f071-111">Poniższy przykład ilustruje użycie adresów zmiennych, tablic i ciągów:</span><span class="sxs-lookup"><span data-stu-id="7f071-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="7f071-112">Począwszy od języka C# 7.3, `fixed` instrukcja działa na dodatkowe typy poza tablice, ciągi, bufory o stałym rozmiarze lub zmienne niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="7f071-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="7f071-113">Każdy typ, który implementuje metodę o nazwie `GetPinnableReference` można przypiąć.</span><span class="sxs-lookup"><span data-stu-id="7f071-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="7f071-114">Musi `GetPinnableReference` zwrócić `ref` zmienną [typu niezarządzanego](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="7f071-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="7f071-115">Typy <xref:System.Span%601?displayProperty=nameWithType> .NET <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> i wprowadzone w .NET Core 2.0 korzystają z tego wzorca i mogą być przypięte.</span><span class="sxs-lookup"><span data-stu-id="7f071-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="7f071-116">Jest to pokazane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7f071-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="7f071-117">Jeśli tworzysz typy, które powinny uczestniczyć <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> w tym wzorzec, zobacz na przykład implementacji wzorca.</span><span class="sxs-lookup"><span data-stu-id="7f071-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="7f071-118">Wiele wskaźników można zainicjować w jednej instrukcji, jeśli wszystkie są tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="7f071-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="7f071-119">Aby zainicjować wskaźniki różnych typów, `fixed` po prostu zagnieżdżanie instrukcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7f071-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="7f071-120">Po wykonaniu kodu w instrukcji, wszystkie przypięte zmienne są odpinane i podlegają wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7f071-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="7f071-121">W związku z tym nie wskazują `fixed` na te zmienne poza instrukcją.</span><span class="sxs-lookup"><span data-stu-id="7f071-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="7f071-122">Zmienne zadeklarowane `fixed` w instrukcji są ograniczone do tej instrukcji, co ułatwia:</span><span class="sxs-lookup"><span data-stu-id="7f071-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="7f071-123">Wskaźniki zainicjowane `fixed` w instrukcjach są odczytywane tylko zmienne.</span><span class="sxs-lookup"><span data-stu-id="7f071-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="7f071-124">Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować drugą zmienną wskaźnika i zmodyfikować tę.</span><span class="sxs-lookup"><span data-stu-id="7f071-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="7f071-125">Zmiennej zadeklarowanej `fixed` w instrukcji nie można zmodyfikować:</span><span class="sxs-lookup"><span data-stu-id="7f071-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="7f071-126">Można przydzielić pamięć na stosie, gdzie nie podlega wyrzucania elementów bezużytecznych i dlatego nie musi być przypięty.</span><span class="sxs-lookup"><span data-stu-id="7f071-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="7f071-127">Aby to zrobić, należy użyć [ `stackalloc` wyrażenia](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="7f071-127">To do that, use a [`stackalloc` expression](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7f071-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7f071-128">C# language specification</span></span>

<span data-ttu-id="7f071-129">Aby uzyskać więcej informacji, zobacz Stała sekcja [instrukcji](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) [specyfikacji języka języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="7f071-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f071-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f071-130">See also</span></span>

- [<span data-ttu-id="7f071-131">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="7f071-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7f071-132">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="7f071-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7f071-133">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7f071-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7f071-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="7f071-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="7f071-135">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="7f071-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="7f071-136">Bufory o stałym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="7f071-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
