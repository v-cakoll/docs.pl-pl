---
title: FIXED — C# odwołanie
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: d3c87f0e71095bbcc7c5a1d64b026e92838a6306
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433752"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="b1c01-102">fixed — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b1c01-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="b1c01-103">`fixed` Instrukcja zapobiega ponownemu lokalizowaniu ruchomej zmiennej przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b1c01-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="b1c01-104">Instrukcja jest dozwolona tylko w niebezpiecznym kontekście. [niebezpieczny](unsafe.md) `fixed`</span><span class="sxs-lookup"><span data-stu-id="b1c01-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="b1c01-105">Możesz również użyć słowa kluczowego, `fixed` aby utworzyć bufory o ustalonym [rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="b1c01-105">You can also use the `fixed` keyword to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="b1c01-106">`fixed` Instrukcja ustawia wskaźnik na zmienną zarządzaną i "pinezki", która jest zmienna podczas wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b1c01-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="b1c01-107">Wskaźniki do ruchomych zmiennych zarządzanych są przydatne tylko w `fixed` kontekście.</span><span class="sxs-lookup"><span data-stu-id="b1c01-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="b1c01-108">`fixed` Bez kontekstu, wyrzucanie elementów bezużytecznych może przewidzieć nieprzewidywalne zmienne.</span><span class="sxs-lookup"><span data-stu-id="b1c01-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="b1c01-109">C# Kompilator umożliwia tylko przypisanie wskaźnika do zmiennej zarządzanej w `fixed` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b1c01-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="b1c01-110">Wskaźnik można zainicjować za pomocą tablicy, ciągu, buforu o ustalonym rozmiarze lub adresu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b1c01-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="b1c01-111">Poniższy przykład ilustruje użycie adresów zmiennych, tablic i ciągów:</span><span class="sxs-lookup"><span data-stu-id="b1c01-111">The following example illustrates the use of variable addresses, arrays, and strings:</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="b1c01-112">Począwszy od C# 7,3, `fixed` instrukcja działa na dodatkowych typach poza tablicami, ciągami, buforami o stałym rozmiarze lub zmiennymi niezarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="b1c01-112">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed size buffers, or unmanaged variables.</span></span> <span data-ttu-id="b1c01-113">Każdy typ, który implementuje metodę o `GetPinnableReference` nazwie, może być przypięty.</span><span class="sxs-lookup"><span data-stu-id="b1c01-113">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="b1c01-114">Musi zwracać zmienną typu niezarządzanego. [Cómo se pronuncia
typ niezarządzany](../builtin-types/unmanaged-types.md) `GetPinnableReference` `ref`</span><span class="sxs-lookup"><span data-stu-id="b1c01-114">The `GetPinnableReference` must return a `ref` variable of an [unmanaged type](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="b1c01-115">Typy <xref:System.Span%601?displayProperty=nameWithType> .NET i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> wprowadzone w środowisku .NET Core 2,0 używają tego wzorca i mogą być przypięte.</span><span class="sxs-lookup"><span data-stu-id="b1c01-115">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="b1c01-116">Jest to pokazane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b1c01-116">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="b1c01-117">Jeśli tworzysz typy, które powinny wchodzić w skład tego wzorca, zobacz <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> , aby zapoznać się z przykładem implementacji wzorca.</span><span class="sxs-lookup"><span data-stu-id="b1c01-117">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="b1c01-118">W jednej instrukcji można zainicjować wiele wskaźników, jeśli są one tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="b1c01-118">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="b1c01-119">Aby zainicjować wskaźniki różnych typów, należy po prostu `fixed` zagnieżdżać instrukcje, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b1c01-119">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="b1c01-120">Po wykonaniu kodu w instrukcji wszystkie przypięte zmienne są odpięte i podlegają wyrzucaniu elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b1c01-120">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="b1c01-121">W związku z tym nie należy wskazywać na te `fixed` zmienne poza instrukcją.</span><span class="sxs-lookup"><span data-stu-id="b1c01-121">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="b1c01-122">Zmienne zadeklarowane w `fixed` instrukcji należą do zakresu tej instrukcji, ułatwiając to:</span><span class="sxs-lookup"><span data-stu-id="b1c01-122">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="b1c01-123">Wskaźniki inicjowane `fixed` w instrukcjach są zmiennymi tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="b1c01-123">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="b1c01-124">Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować drugą zmienną wskaźnika i zmodyfikować ją.</span><span class="sxs-lookup"><span data-stu-id="b1c01-124">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="b1c01-125">Nie można zmodyfikować zmiennej zadeklarowanej w `fixed` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="b1c01-125">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

<span data-ttu-id="b1c01-126">Możesz przydzielić pamięć na stosie, gdzie nie podlega wyrzucaniu elementów bezużytecznych i dlatego nie musi być przypięty.</span><span class="sxs-lookup"><span data-stu-id="b1c01-126">You can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="b1c01-127">W tym celu należy użyć [ `stackalloc` operatora](../operators/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="b1c01-127">To do that use the [`stackalloc` operator](../operators/stackalloc.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b1c01-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b1c01-128">C# language specification</span></span>

<span data-ttu-id="b1c01-129">Aby uzyskać więcej informacji, zobacz sekcję [FIXED Statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="b1c01-129">For more information, see [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1c01-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1c01-130">See also</span></span>

- [<span data-ttu-id="b1c01-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b1c01-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b1c01-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b1c01-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b1c01-133">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="b1c01-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b1c01-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="b1c01-134">unsafe</span></span>](unsafe.md)
- [<span data-ttu-id="b1c01-135">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="b1c01-135">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="b1c01-136">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="b1c01-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
