---
title: volatile — C# odwołania
ms.custom: seodec18
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 7200432780cb5a65bc5420b41c5dbd2e27a2c01f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633116"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="600ee-102">volatile (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="600ee-102">volatile (C# Reference)</span></span>

<span data-ttu-id="600ee-103">`volatile` — Słowo kluczowe wskazuje, że pola mogą zostać zmodyfikowane przez wiele wątków, które są wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="600ee-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="600ee-104">Kompilator, system plików środowiska uruchomieniowego i sprzętu może zmienić kolejność operacji odczytu i zapisu do lokalizacji pamięci, ze względu na wydajność.</span><span class="sxs-lookup"><span data-stu-id="600ee-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="600ee-105">Pola, które są zadeklarowane `volatile` nie podlegają Optymalizacje te.</span><span class="sxs-lookup"><span data-stu-id="600ee-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="600ee-106">Dodawanie `volatile` modyfikator gwarantuje, że wszystkie wątki będzie przestrzegać volatile zapisów wykonywane przez inny wątek, w kolejności, w którym zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="600ee-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="600ee-107">Nie ma żadnej gwarancji, pojedynczy całkowita kolejności volatile zapisów wyświetlanego ze wszystkich wątków wykonania.</span><span class="sxs-lookup"><span data-stu-id="600ee-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="600ee-108">`volatile` — Słowo kluczowe mogą być stosowane do pól z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="600ee-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="600ee-109">Typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="600ee-109">Reference types.</span></span>
- <span data-ttu-id="600ee-110">Typy wskaźników (w niebezpiecznym kontekście).</span><span class="sxs-lookup"><span data-stu-id="600ee-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="600ee-111">Należy pamiętać, że chociaż wskaźnika, sama może być nietrwałe, obiekt, który wskazuje nie może.</span><span class="sxs-lookup"><span data-stu-id="600ee-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="600ee-112">Innymi słowy nie można zadeklarować "wskaźnik volatile."</span><span class="sxs-lookup"><span data-stu-id="600ee-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="600ee-113">Proste typy, takie jak `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, i `bool`.</span><span class="sxs-lookup"><span data-stu-id="600ee-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="600ee-114">`enum` Typu z jednym z następujących typów podstawowych: `byte`, `sbyte`, `short`, `ushort`, `int`, lub `uint`.</span><span class="sxs-lookup"><span data-stu-id="600ee-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="600ee-115">Parametry typu ogólnego, znane jako typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="600ee-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="600ee-116"><xref:System.IntPtr> i <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="600ee-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="600ee-117">Inne typy, w tym `double` i `long`, nie można oznaczyć `volatile` ponieważ odczyty i zapisy do pól z tych typów, nie można zagwarantować niepodzielnych.</span><span class="sxs-lookup"><span data-stu-id="600ee-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="600ee-118">Aby chronić wielowątkowych dostęp do tych typów pól, użyj <xref:System.Threading.Interlocked> elementy członkowskie klasy lub ochrona dostępu przy użyciu [ `lock` ](lock-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="600ee-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="600ee-119">`volatile` — Słowo kluczowe może być stosowany tylko do pól `class` lub `struct`.</span><span class="sxs-lookup"><span data-stu-id="600ee-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="600ee-120">Nie można zadeklarować zmienne lokalne `volatile`.</span><span class="sxs-lookup"><span data-stu-id="600ee-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="600ee-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="600ee-121">Example</span></span>

<span data-ttu-id="600ee-122">Poniższy przykład pokazuje sposób deklarowania zmiennej pole publiczne `volatile`.</span><span class="sxs-lookup"><span data-stu-id="600ee-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="600ee-123">Poniższy przykład pokazuje, jak wątek wiadomości pomocniczych lub procesu roboczego można tworzyć i używany do wykonywania przetwarzania równolegle z wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="600ee-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="600ee-124">Aby uzyskać więcej informacji o wielowątkowości, zobacz [zarządzana wątkowość](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="600ee-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="600ee-125">Za pomocą `volatile` modyfikator dodane do deklaracji `_shouldStop` w miejscu, zawsze uzyskasz takie same wyniki (podobnie jak fragment, jak pokazano w poprzednim kodzie).</span><span class="sxs-lookup"><span data-stu-id="600ee-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="600ee-126">Jednak bez ten modyfikator na `_shouldStop` elementu członkowskiego, zachowanie jest nieprzewidywalne.</span><span class="sxs-lookup"><span data-stu-id="600ee-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="600ee-127">`DoWork` Metoda może zoptymalizować dostęp do elementu członkowskiego, wynikiem odczytywanie nieaktualnych danych.</span><span class="sxs-lookup"><span data-stu-id="600ee-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="600ee-128">Ze względu na charakter programowania wielowątkowe liczba odczytów starych jest nieprzewidywalne.</span><span class="sxs-lookup"><span data-stu-id="600ee-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="600ee-129">Różnych tras program generuje wyniki nieco inny.</span><span class="sxs-lookup"><span data-stu-id="600ee-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="600ee-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="600ee-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="600ee-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="600ee-131">See also</span></span>

- [<span data-ttu-id="600ee-132">C#Specyfikacja języka: volatile — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="600ee-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="600ee-133">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="600ee-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="600ee-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="600ee-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="600ee-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="600ee-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="600ee-136">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="600ee-136">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="600ee-137">instrukcji "Lock"</span><span class="sxs-lookup"><span data-stu-id="600ee-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
