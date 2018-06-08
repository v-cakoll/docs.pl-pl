---
title: fixed — Instrukcja (odwołanie w C#)
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 28c8e9bd078e07a185f541214aa5b5ff79018ff5
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826997"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="9dcfe-102">fixed — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9dcfe-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="9dcfe-103">`fixed` Instrukcji uniemożliwia przemieszczanie zmienną ruchomy moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="9dcfe-104">`fixed` Instrukcji jest dozwolona tylko w [niebezpieczne](unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="9dcfe-105">`fixed` można również utworzyć [stały rozmiar buforów](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="9dcfe-105">`fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="9dcfe-106">`fixed` Instrukcja ustawia wskaźnik zarządzanych zmienną i "numerów PIN" zmiennej podczas wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="9dcfe-107">Wskaźniki do ruchomy zarządzanych zmienne są przydatne tylko w `fixed` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="9dcfe-108">Bez `fixed` kontekstu, wyrzucanie elementów bezużytecznych można przenosić zmienne nieprzewidywalny.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="9dcfe-109">Kompilator języka C# tylko można przypisać wskaźnik do zmiennej zarządzanych w `fixed` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="9dcfe-110">Wskaźnik można zainicjować za pomocą tablicy, ciąg, buforu o stałym rozmiarze lub adresu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="9dcfe-111">Poniższy przykład przedstawia użycie zmiennej adresów, tablic i ciągów.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="9dcfe-112">Aby uzyskać więcej informacji na temat bufory o ustalonym rozmiarze, zobacz [buforów o rozmiarze stałym](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="9dcfe-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="9dcfe-113">Począwszy od C# 7.3, `fixed` instrukcji działa na dodatkowe typy poza tablic ciągów, bufory o ustalonym rozmiarze albo niezarządzane zmiennych.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-113">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed-size buffers, or unmanaged variables.</span></span> <span data-ttu-id="9dcfe-114">Dowolnego typu, który implementuje metodę o nazwie `GetPinnableReference` może zostać unieruchomiony.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-114">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="9dcfe-115">`GetPinnableReference` Musi zwracać `ref` zmienną typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-115">The `GetPinnableReference` must return a `ref` variable to an unmanaged type.</span></span> <span data-ttu-id="9dcfe-116">Zobacz temat na [typów wskaźnikowych](../../programming-guide/unsafe-code-pointers/pointer-types.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-116">See the topic on [pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md) for more information.</span></span> <span data-ttu-id="9dcfe-117">Typy .NET <xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> wprowadzone w upewnij .NET Core 2.0 użycia tego wzorca i może zostać unieruchomiony.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-117">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="9dcfe-118">Przedstawiono to w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9dcfe-118">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="9dcfe-119">W przypadku tworzenia typów, które powinny uczestniczyć w tym wzorcu, zobacz <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> przykład implementacja wzorca.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-119">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="9dcfe-120">Jeśli są one ten sam typ można zainicjować wielu wskaźniki w jednej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="9dcfe-120">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="9dcfe-121">Aby zainicjować wskaźników różnych typów, po prostu zagnieździć `fixed` instrukcje, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-121">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="9dcfe-122">Po wykonaniu kodu w instrukcji zmiennych przypiętych są odpiąć i wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-122">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="9dcfe-123">W związku z tym nie wskazują na tych zmiennych poza `fixed` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-123">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="9dcfe-124">Zmienne zadeklarowane w `fixed` zestawienie ograniczone do tej instrukcji, ułatwiając to:</span><span class="sxs-lookup"><span data-stu-id="9dcfe-124">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="9dcfe-125">Wskaźniki zainicjowany w `fixed` instrukcje są zmienne tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-125">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="9dcfe-126">Jeśli chcesz zmodyfikować wartość wskaźnika należy zadeklarować Druga zmienna wskaźnika i zmodyfikować to.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-126">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="9dcfe-127">Zmienna zadeklarowana w `fixed` instrukcji nie można zmodyfikować:</span><span class="sxs-lookup"><span data-stu-id="9dcfe-127">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="9dcfe-128">W trybie bezpiecznym można przydzielić pamięci na stosie, w którym nie podlega wyrzucanie elementów bezużytecznych i dlatego nie trzeba przypięty.</span><span class="sxs-lookup"><span data-stu-id="9dcfe-128">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="9dcfe-129">Aby uzyskać więcej informacji, zobacz [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="9dcfe-129">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="9dcfe-130">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9dcfe-130">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9dcfe-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9dcfe-131">See Also</span></span>

 [<span data-ttu-id="9dcfe-132">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="9dcfe-132">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="9dcfe-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9dcfe-133">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="9dcfe-134">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9dcfe-134">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="9dcfe-135">unsafe</span><span class="sxs-lookup"><span data-stu-id="9dcfe-135">unsafe</span></span>](unsafe.md)  
 [<span data-ttu-id="9dcfe-136">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="9dcfe-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
