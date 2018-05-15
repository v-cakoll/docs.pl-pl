---
title: fixed — Instrukcja (odwołanie w C#)
ms.date: 04/20/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e1664f508cb861ffa73b800eeb0da3a1f1cdc432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="4e3d2-102">fixed — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4e3d2-102">fixed Statement (C# Reference)</span></span>

<span data-ttu-id="4e3d2-103">`fixed` Instrukcji uniemożliwia przemieszczanie zmienną ruchomy moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="4e3d2-104">`fixed` Instrukcji jest dozwolona tylko w [niebezpieczne](unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-104">The `fixed` statement is only permitted in an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="4e3d2-105">`Fixed` można również utworzyć [stały rozmiar buforów](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="4e3d2-105">`Fixed` can also be used to create [fixed size buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

<span data-ttu-id="4e3d2-106">`fixed` Instrukcja ustawia wskaźnik zarządzanych zmienną i "numerów PIN" zmiennej podczas wykonywania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="4e3d2-107">Wskaźniki do ruchomy zarządzanych zmienne są przydatne tylko w `fixed` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-107">Pointers to movable managed variables are useful only in a `fixed` context.</span></span> <span data-ttu-id="4e3d2-108">Bez `fixed` kontekstu, wyrzucanie elementów bezużytecznych można przenosić zmienne nieprzewidywalny.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-108">Without a `fixed` context, garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="4e3d2-109">Kompilator języka C# tylko można przypisać wskaźnik do zmiennej zarządzanych w `fixed` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-109">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

<span data-ttu-id="4e3d2-110">Wskaźnik można zainicjować za pomocą tablicy, ciąg, buforu o stałym rozmiarze lub adresu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-110">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="4e3d2-111">Poniższy przykład przedstawia użycie zmiennej adresów, tablic i ciągów.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-111">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="4e3d2-112">Aby uzyskać więcej informacji na temat bufory o ustalonym rozmiarze, zobacz [buforów o rozmiarze stałym](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="4e3d2-112">For more information about fixed-size buffers, see [Fixed Size Buffers](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

<span data-ttu-id="4e3d2-113">Jeśli są one ten sam typ można zainicjować wielu wskaźniki w jednej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="4e3d2-113">Multiple pointers can be initialized in one statement if they are all the same type:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

<span data-ttu-id="4e3d2-114">Aby zainicjować wskaźników różnych typów, po prostu zagnieździć `fixed` instrukcje, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-114">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

<span data-ttu-id="4e3d2-115">Po wykonaniu kodu w instrukcji zmiennych przypiętych są odpiąć i wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-115">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="4e3d2-116">W związku z tym nie wskazują na tych zmiennych poza `fixed` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-116">Therefore, do not point to those variables outside the `fixed` statement.</span></span> <span data-ttu-id="4e3d2-117">Zmienne zadeklarowane w `fixed` zestawienie ograniczone do tej instrukcji, ułatwiając to:</span><span class="sxs-lookup"><span data-stu-id="4e3d2-117">The variables declared in the `fixed` statement are scoped to that statement, making this easier:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

<span data-ttu-id="4e3d2-118">Wskaźniki zainicjowany w `fixed` instrukcje są zmienne tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-118">Pointers initialized in `fixed` statements are readonly variables.</span></span> <span data-ttu-id="4e3d2-119">Jeśli chcesz zmodyfikować wartość wskaźnika należy zadeklarować Druga zmienna wskaźnika i zmodyfikować to.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-119">If you want to modify the pointer value, you must declare a second pointer variable, and modify that.</span></span> <span data-ttu-id="4e3d2-120">Zmienna zadeklarowana w `fixed` instrukcji nie można zmodyfikować:</span><span class="sxs-lookup"><span data-stu-id="4e3d2-120">The variable declared in the `fixed` statement cannot be modified:</span></span>

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


<span data-ttu-id="4e3d2-121">W trybie bezpiecznym można przydzielić pamięci na stosie, w którym nie podlega wyrzucanie elementów bezużytecznych i dlatego nie trzeba przypięty.</span><span class="sxs-lookup"><span data-stu-id="4e3d2-121">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="4e3d2-122">Aby uzyskać więcej informacji, zobacz [stackalloc](stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="4e3d2-122">For more information, see [stackalloc](stackalloc.md).</span></span>

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="4e3d2-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4e3d2-123">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4e3d2-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e3d2-124">See Also</span></span>

 [<span data-ttu-id="4e3d2-125">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="4e3d2-125">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="4e3d2-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4e3d2-126">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="4e3d2-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="4e3d2-127">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="4e3d2-128">unsafe</span><span class="sxs-lookup"><span data-stu-id="4e3d2-128">unsafe</span></span>](unsafe.md)  
 [<span data-ttu-id="4e3d2-129">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="4e3d2-129">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
