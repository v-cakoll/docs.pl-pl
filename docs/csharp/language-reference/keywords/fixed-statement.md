---
title: stała instrukcja - Odwołanie do języka C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713521"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="0cabd-102">fixed — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0cabd-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="0cabd-103">Instrukcja `fixed` uniemożliwia modułowi odśmiecania pamięci przemieszczanie ruchomej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0cabd-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="0cabd-104">Instrukcja `fixed` jest dozwolona tylko w [niebezpiecznym](unsafe.md) kontekście.</span><span class="sxs-lookup"><span data-stu-id="0cabd-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="0cabd-105">Za pomocą słowa `fixed` kluczowego można również utworzyć [bufory o stałym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="0cabd-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="0cabd-106">Instrukcja `fixed` ustawia wskaźnik do zmiennej zarządzanej i "pins", że zmienna podczas wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0cabd-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="0cabd-107">Wskaźniki do ruchomych zmiennych zarządzanych `fixed` są przydatne tylko w kontekście.</span><span class="sxs-lookup"><span data-stu-id="0cabd-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="0cabd-108">Bez `fixed` kontekstu wyrzucania elementów bezużytecznych można przenieść zmienne nieprzewidywalne.</span><span class="sxs-lookup"><span data-stu-id="0cabd-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="0cabd-109">Kompilator Języka C# umożliwia tylko przypisanie wskaźnika do zmiennej zarządzanej `fixed` w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0cabd-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="0cabd-110">Wskaźnik można zainicjować za pomocą tablicy, ciągu, buforu o stałym rozmiarze lub adresu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0cabd-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="0cabd-111">Poniższy przykład ilustruje użycie zmiennych adresów, tablic i ciągów:</span><span class="sxs-lookup"><span data-stu-id="0cabd-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="0cabd-112">Począwszy od Języka C# `fixed` 7.3, instrukcja działa na dodatkowe typy poza tablice, ciągi, bufory o stałym rozmiarze lub zmiennych niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="0cabd-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="0cabd-113">Każdy typ, który implementuje metodę o nazwie `GetPinnableReference` można przypiąć.</span><span class="sxs-lookup"><span data-stu-id="0cabd-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="0cabd-114">Musi `GetPinnableReference` zwrócić `ref` zmienną [typu niezarządzanego](../builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="0cabd-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="0cabd-115">Typy <xref:System.Span%601?displayProperty=nameWithType> .NET <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> i wprowadzone w .NET Core 2.0 korzystają z tego wzorca i mogą być przypięte.</span><span class="sxs-lookup"><span data-stu-id="0cabd-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="0cabd-116">Jest to pokazane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0cabd-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="0cabd-117">Jeśli tworzysz typy, które powinny <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> uczestniczyć w tym wzorzec, zobacz przykład implementowania wzorca.</span><span class="sxs-lookup"><span data-stu-id="0cabd-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="0cabd-118">Wiele wskaźników można zainicjować w jednej instrukcji, jeśli wszystkie są tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="0cabd-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="0cabd-119">Aby zainicjować wskaźniki różnych typów, `fixed` wystarczy zagnieździć instrukcje, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0cabd-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="0cabd-120">Po wykonaniu kodu w instrukcji wszystkie przypięte zmienne są odpięte i podlegają wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0cabd-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="0cabd-121">W związku z tym nie wskazują `fixed` na te zmienne poza instrukcją.</span><span class="sxs-lookup"><span data-stu-id="0cabd-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="0cabd-122">Zmienne zadeklarowane w `fixed` instrukcji są ograniczone do tej instrukcji, co ułatwia:</span><span class="sxs-lookup"><span data-stu-id="0cabd-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="0cabd-123">Wskaźniki zainicjowane `fixed` w instrukcjach są zmiennymi tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="0cabd-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="0cabd-124">Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować drugą zmienną wskaźnika i zmodyfikować ją.</span><span class="sxs-lookup"><span data-stu-id="0cabd-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="0cabd-125">Nie można zmodyfikować zmiennej zadeklarowanej w `fixed` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="0cabd-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="0cabd-126">Można przydzielić pamięć na stosie, gdzie nie podlega wyrzucania elementów bezużytecznych i dlatego nie musi być przypięty.</span><span class="sxs-lookup"><span data-stu-id="0cabd-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="0cabd-127">Aby to zrobić, należy użyć [ `stackalloc` operatora](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="0cabd-127">To do that use the [`stackalloc` operator](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0cabd-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0cabd-128">C# language specification</span></span>

<span data-ttu-id="0cabd-129">Aby uzyskać więcej informacji, zobacz sekcja [instrukcja stała](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) [specyfikacji języka Języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0cabd-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0cabd-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cabd-130">See also</span></span>

- [<span data-ttu-id="0cabd-131">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="0cabd-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0cabd-132">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="0cabd-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0cabd-133">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0cabd-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0cabd-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="0cabd-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="0cabd-135">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="0cabd-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="0cabd-136">Bufory o stałym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="0cabd-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
