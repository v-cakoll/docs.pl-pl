---
title: FIXED — C# odwołanie
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713521"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="591f2-102">fixed — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="591f2-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="591f2-103">Instrukcja `fixed` uniemożliwia ponowne lokalizowanie ruchomej zmiennej przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="591f2-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="591f2-104">Instrukcja jest dozwolona tylko w niebezpiecznym kontekście. [niebezpieczny](unsafe.md) `fixed`</span><span class="sxs-lookup"><span data-stu-id="591f2-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="591f2-105">Można również użyć słowa kluczowego `fixed`, aby utworzyć [bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="591f2-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="591f2-106">Instrukcja `fixed` ustawia wskaźnik do zmiennej zarządzanej i "pinezki", która jest zmienna podczas wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="591f2-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="591f2-107">Wskaźniki do ruchomych zmiennych zarządzanych są przydatne tylko w kontekście `fixed`.</span><span class="sxs-lookup"><span data-stu-id="591f2-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="591f2-108">Bez kontekstu `fixed`, wyrzucanie elementów bezużytecznych może przewidzieć nieprzewidywalne zmienne.</span><span class="sxs-lookup"><span data-stu-id="591f2-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="591f2-109">C# Kompilator umożliwia tylko przypisanie wskaźnika do zmiennej zarządzanej w instrukcji `fixed`.</span><span class="sxs-lookup"><span data-stu-id="591f2-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="591f2-110">Wskaźnik można zainicjować za pomocą tablicy, ciągu, buforu o ustalonym rozmiarze lub adresu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="591f2-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="591f2-111">Poniższy przykład ilustruje użycie adresów zmiennych, tablic i ciągów:</span><span class="sxs-lookup"><span data-stu-id="591f2-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="591f2-112">Począwszy od C# 7,3, instrukcja `fixed` działa na dodatkowych typach poza tablicami, ciągami, buforami o ustalonym rozmiarze lub zmiennymi niezarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="591f2-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="591f2-113">Dowolny typ implementujący metodę o nazwie `GetPinnableReference` może być przypięty.</span><span class="sxs-lookup"><span data-stu-id="591f2-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="591f2-114">Musi zwracać zmienną typu niezarządzanego. [Cómo se pronuncia
typ niezarządzany](../builtin-types/unmanaged-types.md) `GetPinnableReference` `ref`</span><span class="sxs-lookup"><span data-stu-id="591f2-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="591f2-115">Typy .NET <xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> wprowadzone w środowisku .NET Core 2,0 używają tego wzorca i mogą być przypięte.</span><span class="sxs-lookup"><span data-stu-id="591f2-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="591f2-116">Jest to pokazane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="591f2-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="591f2-117">Jeśli tworzysz typy, które powinny wchodzić w skład tego wzorca, zobacz <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType>, aby zapoznać się z przykładem implementacji wzorca.</span><span class="sxs-lookup"><span data-stu-id="591f2-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="591f2-118">W jednej instrukcji można zainicjować wiele wskaźników, jeśli są one tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="591f2-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="591f2-119">Aby zainicjować wskaźniki różnych typów, należy po prostu zagnieździć instrukcje `fixed`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="591f2-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="591f2-120">Po wykonaniu kodu w instrukcji wszystkie przypięte zmienne są odpięte i podlegają wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="591f2-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="591f2-121">W związku z tym nie należy wskazywać na te zmienne poza instrukcją `fixed`.</span><span class="sxs-lookup"><span data-stu-id="591f2-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="591f2-122">Zmienne zadeklarowane w instrukcji `fixed` są zakresem tej instrukcji, ułatwiając to:</span><span class="sxs-lookup"><span data-stu-id="591f2-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="591f2-123">Wskaźniki inicjowane w instrukcjach `fixed` są zmiennymi tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="591f2-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="591f2-124">Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować drugą zmienną wskaźnika i zmodyfikować ją.</span><span class="sxs-lookup"><span data-stu-id="591f2-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="591f2-125">Zmienna zadeklarowana w instrukcji `fixed` nie może być modyfikowana:</span><span class="sxs-lookup"><span data-stu-id="591f2-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="591f2-126">Możesz przydzielić pamięć na stosie, gdzie nie podlega wyrzucaniu elementów bezużytecznych i dlatego nie musi być przypięty.</span><span class="sxs-lookup"><span data-stu-id="591f2-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="591f2-127">Aby to zrobić, użyj [operatora`stackalloc`](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="591f2-127">To do that use the [`stackalloc` operator](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="591f2-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="591f2-128">C# language specification</span></span>

<span data-ttu-id="591f2-129">Aby uzyskać więcej informacji, zobacz sekcję [FIXED Statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="591f2-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="591f2-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="591f2-130">See also</span></span>

- [<span data-ttu-id="591f2-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="591f2-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="591f2-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="591f2-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="591f2-133">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="591f2-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="591f2-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="591f2-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="591f2-135">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="591f2-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="591f2-136">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="591f2-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
