---
title: volatile — odwołanie do języka C#
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712848"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="fdfec-102">volatile (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fdfec-102">volatile (C# Reference)</span></span>

<span data-ttu-id="fdfec-103">Słowo `volatile` kluczowe wskazuje, że pole może być modyfikowane przez wiele wątków, które są wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="fdfec-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="fdfec-104">Kompilator, system wykonywania, a nawet sprzęt może zmienić rozmieszczenie odczytów i zapisów w lokalizacjach pamięci ze względu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="fdfec-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="fdfec-105">Pola, które `volatile` są zadeklarowane nie podlegają tych optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="fdfec-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="fdfec-106">Dodanie `volatile` modyfikatora zapewnia, że wszystkie wątki będą obserwować lotnych zapisów wykonywanych przez inny wątek w kolejności, w jakiej zostały one wykonane.</span><span class="sxs-lookup"><span data-stu-id="fdfec-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="fdfec-107">Nie ma żadnej gwarancji pojedynczej całkowitej kolejności nietrwałych zapisów, jak widać ze wszystkich wątków wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fdfec-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="fdfec-108">Słowo `volatile` kluczowe można zastosować do pól tego typu:</span><span class="sxs-lookup"><span data-stu-id="fdfec-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="fdfec-109">Typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="fdfec-109">Reference types.</span></span>
- <span data-ttu-id="fdfec-110">Typy wskaźników (w niebezpiecznym kontekście).</span><span class="sxs-lookup"><span data-stu-id="fdfec-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="fdfec-111">Należy zauważyć, że chociaż sam wskaźnik może być lotny, obiekt, który wskazuje nie może.</span><span class="sxs-lookup"><span data-stu-id="fdfec-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="fdfec-112">Innymi słowy nie można zadeklarować "wskaźnik do volatile."</span><span class="sxs-lookup"><span data-stu-id="fdfec-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="fdfec-113">Proste typy, `sbyte` `byte`takie `short` `ushort`jak `int` `uint`, `char` `float`, `bool`, , , i .</span><span class="sxs-lookup"><span data-stu-id="fdfec-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="fdfec-114">Typ `enum` z jednym z następujących `byte`typów `sbyte` `short`bazowych: , , `ushort`, `int`, lub `uint`.</span><span class="sxs-lookup"><span data-stu-id="fdfec-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="fdfec-115">Ogólne parametry typu znane jako typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="fdfec-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="fdfec-116"><xref:System.IntPtr>i <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="fdfec-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="fdfec-117">Inne typy, `double` `long`w tym `volatile` i , nie mogą być oznaczone, ponieważ odczyty i zapisy pól tych typów nie mogą być zagwarantowane jako atomowej.</span><span class="sxs-lookup"><span data-stu-id="fdfec-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="fdfec-118">Aby chronić dostęp wielowątkowy do tych typów <xref:System.Threading.Interlocked> pól, należy użyć [`lock`](lock-statement.md) elementów członkowskich klasy lub ochrony dostępu przy użyciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="fdfec-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="fdfec-119">Słowo `volatile` kluczowe można zastosować tylko do `class` `struct`pól lub .</span><span class="sxs-lookup"><span data-stu-id="fdfec-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="fdfec-120">Nie można zadeklarować `volatile`zmiennych lokalnych .</span><span class="sxs-lookup"><span data-stu-id="fdfec-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="fdfec-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="fdfec-121">Example</span></span>

<span data-ttu-id="fdfec-122">W poniższym przykładzie pokazano, jak `volatile`zadeklarować zmienną pola publicznego jako .</span><span class="sxs-lookup"><span data-stu-id="fdfec-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="fdfec-123">W poniższym przykładzie pokazano, jak można utworzyć wątek pomocniczy lub roboczy i wykorzystać do wykonywania przetwarzania równolegle z wątkiem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="fdfec-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="fdfec-124">Aby uzyskać więcej informacji na temat wielowątkowości, zobacz [Managed Threading](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="fdfec-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="fdfec-125">Po `volatile` dodaniu modyfikatora do deklaracji `_shouldStop` w miejscu, zawsze otrzymasz te same wyniki (podobne do fragmentu pokazanego w poprzednim kodzie).</span><span class="sxs-lookup"><span data-stu-id="fdfec-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="fdfec-126">Jednak bez tego modyfikatora na `_shouldStop` element członkowski, zachowanie jest nieprzewidywalne.</span><span class="sxs-lookup"><span data-stu-id="fdfec-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="fdfec-127">Metoda `DoWork` może zoptymalizować dostęp do elementu członkowskiego, co powoduje odczyt starych danych.</span><span class="sxs-lookup"><span data-stu-id="fdfec-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="fdfec-128">Ze względu na charakter programowania wielowątkowego liczba starych odczytów jest nieprzewidywalna.</span><span class="sxs-lookup"><span data-stu-id="fdfec-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="fdfec-129">Różne przebiegi programu będą dawać nieco inne wyniki.</span><span class="sxs-lookup"><span data-stu-id="fdfec-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fdfec-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fdfec-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fdfec-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdfec-131">See also</span></span>

- [<span data-ttu-id="fdfec-132">Specyfikacja języka języka Języka Języka C#: volatile — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="fdfec-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="fdfec-133">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="fdfec-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fdfec-134">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="fdfec-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fdfec-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="fdfec-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fdfec-136">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="fdfec-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="fdfec-137">instrukcja blokady</span><span class="sxs-lookup"><span data-stu-id="fdfec-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
