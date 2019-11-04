---
title: volatile — C# odwołanie
ms.custom: seodec18
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: e72173ba1b91f03ccb1c15ca6451ac997666bc7f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422129"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="f6864-102">volatile (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f6864-102">volatile (C# Reference)</span></span>

<span data-ttu-id="f6864-103">Słowo kluczowe `volatile` wskazuje, że pole może być modyfikowane przez wiele wątków, które są wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="f6864-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="f6864-104">Kompilator, system środowiska uruchomieniowego i nawet sprzęt mogą zmieniać rozmieszczenie odczytów i zapisów w lokalizacjach pamięci ze względu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="f6864-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="f6864-105">Pola, które są zadeklarowane `volatile` nie podlegają tym optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="f6864-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="f6864-106">Dodanie modyfikatora `volatile` gwarantuje, że wszystkie wątki będą obserwować nietrwałe zapisy wykonywane przez dowolny wątek w kolejności, w której zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="f6864-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="f6864-107">Nie istnieje gwarancja pojedynczej kolejności zapisów nietrwałych w postaci zaobserwowanej ze wszystkich wątków wykonania.</span><span class="sxs-lookup"><span data-stu-id="f6864-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="f6864-108">Słowo kluczowe `volatile` można zastosować do pól tych typów:</span><span class="sxs-lookup"><span data-stu-id="f6864-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="f6864-109">Typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="f6864-109">Reference types.</span></span>
- <span data-ttu-id="f6864-110">Typy wskaźnika (w niebezpiecznym kontekście).</span><span class="sxs-lookup"><span data-stu-id="f6864-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="f6864-111">Należy zauważyć, że chociaż wskaźnik może być nietrwały, obiekt, do którego wskazuje element, nie może.</span><span class="sxs-lookup"><span data-stu-id="f6864-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="f6864-112">Innymi słowy, nie można zadeklarować "wskaźnika do nietrwałego".</span><span class="sxs-lookup"><span data-stu-id="f6864-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="f6864-113">Typy proste, takie jak `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`i `bool`.</span><span class="sxs-lookup"><span data-stu-id="f6864-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="f6864-114">Typ `enum` z jednym z następujących typów podstawowych: `byte`, `sbyte`, `short`, `ushort`, `int`lub `uint`.</span><span class="sxs-lookup"><span data-stu-id="f6864-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="f6864-115">Parametry typu ogólnego znane jako typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="f6864-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="f6864-116"><xref:System.IntPtr> i <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="f6864-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="f6864-117">Inne typy, w tym `double` i `long`, nie mogą być oznaczone jako `volatile` ponieważ operacje odczytu i zapisu do pól tych typów nie mogą być niepodzielne.</span><span class="sxs-lookup"><span data-stu-id="f6864-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="f6864-118">Aby chronić wielowątkowy dostęp do tych typów pól, Użyj elementów członkowskich klasy <xref:System.Threading.Interlocked> lub Włącz ochronę dostępu przy użyciu instrukcji [`lock`](lock-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="f6864-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="f6864-119">Słowo kluczowe `volatile` może być stosowane tylko do pól `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="f6864-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="f6864-120">Nie można zadeklarować zmiennych lokalnych `volatile`.</span><span class="sxs-lookup"><span data-stu-id="f6864-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="f6864-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6864-121">Example</span></span>

<span data-ttu-id="f6864-122">Poniższy przykład pokazuje, jak zadeklarować zmienną pola publicznego jako `volatile`.</span><span class="sxs-lookup"><span data-stu-id="f6864-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="f6864-123">W poniższym przykładzie pokazano, jak można utworzyć wątek pomocniczy lub proces roboczy, który będzie używany do przetwarzania równolegle z elementem wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="f6864-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="f6864-124">Aby uzyskać więcej informacji na temat wielowątkowości, zobacz [zarządzane wątki](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="f6864-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="f6864-125">Po dodaniu modyfikatora `volatile` do deklaracji `_shouldStop` na miejscu zawsze uzyskasz te same wyniki (podobnie jak w powyższym fragmencie kodu).</span><span class="sxs-lookup"><span data-stu-id="f6864-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="f6864-126">Jednak bez tego modyfikatora dla elementu członkowskiego `_shouldStop` zachowanie jest nieprzewidywalne.</span><span class="sxs-lookup"><span data-stu-id="f6864-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="f6864-127">Metoda `DoWork` może zoptymalizować dostęp do elementu członkowskiego, co spowoduje odczytanie starych danych.</span><span class="sxs-lookup"><span data-stu-id="f6864-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="f6864-128">Ze względu na charakter programowania wielowątkowego liczba nieodświeżonych odczytów jest nieprzewidywalne.</span><span class="sxs-lookup"><span data-stu-id="f6864-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="f6864-129">Różne uruchomienia programu będą dawać nieco inne wyniki.</span><span class="sxs-lookup"><span data-stu-id="f6864-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f6864-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f6864-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f6864-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6864-131">See also</span></span>

- [<span data-ttu-id="f6864-132">C#Specyfikacja języka: słowo kluczowe volatile</span><span class="sxs-lookup"><span data-stu-id="f6864-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="f6864-133">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="f6864-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f6864-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f6864-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f6864-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f6864-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f6864-136">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="f6864-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f6864-137">lock — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="f6864-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
