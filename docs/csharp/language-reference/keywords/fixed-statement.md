---
title: fixed — Instrukcja (odwołanie w C#)
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 021fc3bd63922394bd70495bd4335b068fc51cdd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213968"
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="c7106-102">fixed — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c7106-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="c7106-103">`fixed` Instrukcji zapobiega przemieszczanie zmienną ruchome moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="c7106-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="c7106-104">`fixed` Instrukcji jest dozwolona tylko w [niebezpieczne](unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="c7106-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="c7106-105">`fixed` można również utworzyć [stałych buforów o rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="c7106-105">`fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="c7106-106">`fixed` Instrukcja ustawia wskaźnik zarządzanego zmiennej i "przypięć" tej zmiennej podczas wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c7106-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="c7106-107">Wskaźniki do zmiennych, ruchome zarządzane są przydatne tylko w `fixed` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="c7106-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="c7106-108">Bez `fixed` kontekstu, wyrzucanie elementów bezużytecznych może przenosić zmienne nieprzewidywalny.</span><span class="sxs-lookup"><span data-stu-id="c7106-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="c7106-109">Kompilator języka C# tylko umożliwia przypisywanie wskaźnik do zmiennej zarządzanych w `fixed` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c7106-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="c7106-110">Aby zainicjować wskaźnik, należy za pomocą tablicy, ciąg, bufora o stałym rozmiarze lub adres zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c7106-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="c7106-111">Poniższy przykład ilustruje użycie zmiennej adresów, tablic i ciągów.</span><span class="sxs-lookup"><span data-stu-id="c7106-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="c7106-112">Aby uzyskać więcej informacji o stałym rozmiarze buforów, zobacz [ustalony rozmiar buforów](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="c7106-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="c7106-113">Począwszy od C# 7.3, `fixed` instrukcji operuje na dodatkowe typy poza tablice, ciągi, bufory o stałym rozmiarze lub niezarządzanego zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c7106-113">Starting with C# 7.3, the `fixed` statement operates on additional types beyond arrays, strings, fixed-size buffers, or unmanaged variables.</span></span> <span data-ttu-id="c7106-114">Dowolny typ, który implementuje metodę o nazwie `GetPinnableReference` można przypiąć.</span><span class="sxs-lookup"><span data-stu-id="c7106-114">Any type that implements a method named `GetPinnableReference` can be pinned.</span></span> <span data-ttu-id="c7106-115">`GetPinnableReference` Musi zwracać `ref` zmienną typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c7106-115">The `GetPinnableReference` must return a `ref` variable to an unmanaged type.</span></span> <span data-ttu-id="c7106-116">Zobacz temat w [typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="c7106-116">See the topic on [pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md) for more information.</span></span> <span data-ttu-id="c7106-117">Typy .NET <xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> wprowadzone w programie .NET Core 2.0 upewnij Użyj tego wzorca i mogą być przypinane.</span><span class="sxs-lookup"><span data-stu-id="c7106-117">The .NET types <xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> introduced in .NET Core 2.0 make use of this pattern and can be pinned.</span></span> <span data-ttu-id="c7106-118">Jest to pokazane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c7106-118">This is shown in the following example:</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

<span data-ttu-id="c7106-119">Jeśli tworzysz typy, które należy wziąć udział w tym wzorcu, zobacz <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> przykład implementacja wzorca.</span><span class="sxs-lookup"><span data-stu-id="c7106-119">If you are creating types that should participate in this pattern, see <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> for an example of implementing the pattern.</span></span>

<span data-ttu-id="c7106-120">Mogą być inicjowane wielu wskaźników w jednej instrukcji, jeśli są tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="c7106-120">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="c7106-121">Aby zainicjować wskaźników różnego typu, po prostu zagnieździć `fixed` instrukcje, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c7106-121">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="c7106-122">Po wykonaniu kodu w instrukcji wszystkie przypięte zmienne są nieprzypięte i wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c7106-122">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="c7106-123">W związku z tym, nie mogą wskazywać tych zmiennych na zewnątrz `fixed` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c7106-123">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="c7106-124">Zmienne zadeklarowane w `fixed` instrukcji są ograniczone do tej instrukcji, ułatwiając to:</span><span class="sxs-lookup"><span data-stu-id="c7106-124">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="c7106-125">Wskaźniki są inicjowane w `fixed` instrukcje są zmienne tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="c7106-125">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="c7106-126">Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować zmienną drugi wskaźnik i zmodyfikować to.</span><span class="sxs-lookup"><span data-stu-id="c7106-126">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="c7106-127">Zmienna zadeklarowana w `fixed` instrukcji nie można zmodyfikować:</span><span class="sxs-lookup"><span data-stu-id="c7106-127">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="c7106-128">W trybie bezpiecznym można przydzielić pamięci na stosie, w którym nie podlega wyrzucania elementów bezużytecznych i dlatego nie trzeba przypiąć.</span><span class="sxs-lookup"><span data-stu-id="c7106-128">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="c7106-129">Aby uzyskać więcej informacji, zobacz [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="c7106-129">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="c7106-130">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c7106-130">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c7106-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7106-131">See Also</span></span>

- [<span data-ttu-id="c7106-132">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c7106-132">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="c7106-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c7106-133">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="c7106-134">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c7106-134">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="c7106-135">unsafe</span><span class="sxs-lookup"><span data-stu-id="c7106-135">unsafe</span></span>](unsafe.md)  
- [<span data-ttu-id="c7106-136">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="c7106-136">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
