---
title: Pamięć<T> i zakres<T> wytyczne dotyczące użycia
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 728f360d2e8f93ebdf2b17fec39477b95ed11357
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063283"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="8b844-102">Pamięć\<T > i zakres\<T > wytyczne dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="8b844-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="8b844-103">.NET core zawiera wiele typów, które reprezentują dowolnego niego ciągły region pamięci.</span><span class="sxs-lookup"><span data-stu-id="8b844-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="8b844-104">.NET core 2.0 wprowadzono <xref:System.Span%601> i <xref:System.ReadOnlySpan%601>, buforów pamięci uproszczone, które mogą być wspierany przez, które są zarządzane lub niezarządzane pamięci.</span><span class="sxs-lookup"><span data-stu-id="8b844-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="8b844-105">Te typy mogą być przechowywane w stosie, dlatego mogą nie nadaje się do liczby scenariuszy, w tym wywołania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="8b844-105">Because these types can be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="8b844-106">.NET core 2.1 dodaje szereg dodatkowych typów, w tym <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, i <xref:System.Buffers.MemoryPool%601>.</span><span class="sxs-lookup"><span data-stu-id="8b844-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="8b844-107">Podobnie jak <xref:System.Span%601>, <xref:System.Memory%601> i jego powiązanych typów może być zabezpieczony za pomocą zarządzanych i niezarządzanych pamięci.</span><span class="sxs-lookup"><span data-stu-id="8b844-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="8b844-108">W odróżnieniu od <xref:System.Span%601>, <xref:System.Memory%601> mogą być przechowywane tylko na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="8b844-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can only be stored on the managed heap.</span></span>

<span data-ttu-id="8b844-109">Zarówno <xref:System.Span%601> i <xref:System.Memory%601> są buforów danych strukturalnych, który może służyć w potokach.</span><span class="sxs-lookup"><span data-stu-id="8b844-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="8b844-110">Oznacza to, że są one przeznaczone tak, aby niektóre lub wszystkie dane mogą być skutecznie przekazywane do składniki w potoku, które mogą je przetworzyć i opcjonalnie modyfikują bufor.</span><span class="sxs-lookup"><span data-stu-id="8b844-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="8b844-111">Ponieważ <xref:System.Memory%601> i jej powiązane typy można uzyskać dostęp przez kilka składników lub przez wiele wątków, ważne jest, deweloperzy wykonać niektóre wytyczne standardowego użycia, aby utworzyć niezawodny kod.</span><span class="sxs-lookup"><span data-stu-id="8b844-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="8b844-112">Właściciele, klientów i zarządzanie okresem istnienia</span><span class="sxs-lookup"><span data-stu-id="8b844-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="8b844-113">Ponieważ bufory można przekazać wokół między interfejsami API, a ponieważ buforów czasami dostęp jest możliwy z wielu wątków, należy wziąć pod uwagę zarządzanie okresem istnienia.</span><span class="sxs-lookup"><span data-stu-id="8b844-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="8b844-114">Istnieją trzy podstawowe pojęcia:</span><span class="sxs-lookup"><span data-stu-id="8b844-114">There are three core concepts:</span></span>

- <span data-ttu-id="8b844-115">**Własność**.</span><span class="sxs-lookup"><span data-stu-id="8b844-115">**Ownership**.</span></span> <span data-ttu-id="8b844-116">Właściciel wystąpienie buforu jest odpowiedzialny za zarządzanie okresem istnienia, w tym zniszczenie buforu, gdy nie jest już używana.</span><span class="sxs-lookup"><span data-stu-id="8b844-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="8b844-117">Wszystkie bufory zostały jednego właściciela.</span><span class="sxs-lookup"><span data-stu-id="8b844-117">All buffers have a single owner.</span></span> <span data-ttu-id="8b844-118">Ogólnie rzecz biorąc właściciel jest składnik, który utworzył buforu lub te, które otrzymały buforu z fabryki.</span><span class="sxs-lookup"><span data-stu-id="8b844-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="8b844-119">Można również przenieść własność; **Składnik A** można zwalnia bufor do **B składnika**, w tym momencie **składnik A** nie mogą korzystać z buforu, i **składnika B**  staje się odpowiedzialny za zniszczenie buforu, gdy nie jest już używana.</span><span class="sxs-lookup"><span data-stu-id="8b844-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="8b844-120">**Użycie**.</span><span class="sxs-lookup"><span data-stu-id="8b844-120">**Consumption**.</span></span> <span data-ttu-id="8b844-121">Konsument wystąpienie buforu może użyć wystąpienia buforu przez odczytanie z niego i prawdopodobnie zapisywania.</span><span class="sxs-lookup"><span data-stu-id="8b844-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="8b844-122">Bufory może mieć jednego użytkownika w czasie, ile pewien mechanizm synchronizacji zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="8b844-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="8b844-123">Należy pamiętać o tym, czy active konsumenta bufor niekoniecznie właściciela buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="8b844-124">**Dzierżawy**.</span><span class="sxs-lookup"><span data-stu-id="8b844-124">**Lease**.</span></span> <span data-ttu-id="8b844-125">Dzierżawa jest czas, który może być konsumenta buforu określonego składnika.</span><span class="sxs-lookup"><span data-stu-id="8b844-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="8b844-126">Poniższy przykład pseudo-kodu przedstawiono te trzy pojęcia.</span><span class="sxs-lookup"><span data-stu-id="8b844-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="8b844-127">Zawiera on `Main` metody, która tworzy wystąpienie <xref:System.Memory%601> bufora o typie <xref:System.Char>, wywołania `WriteInt32ToBuffer` metodę, aby zapisać ciąg reprezentujący liczbę całkowitą do buforu, a następnie wywołuje `DisplayBufferToConsole` metodę, aby wyświetlić wartość bufor.</span><span class="sxs-lookup"><span data-stu-id="8b844-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

<span data-ttu-id="8b844-128">`Main` Metoda tworzy buforu (w tym przypadku <xref:System.Span%601> wystąpienia) i dlatego jest jego właścicielem.</span><span class="sxs-lookup"><span data-stu-id="8b844-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="8b844-129">W związku z tym `Main` jest odpowiedzialny za zniszczenie buforu, gdy nie jest już używana.</span><span class="sxs-lookup"><span data-stu-id="8b844-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="8b844-130">Jest to realizowane przez wywołanie metody buforu <xref:System.Span%601.Clear?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8b844-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8b844-131">( <xref:System.Span%601.Clear> Metoda tutaj faktycznie Czyści pamięć buforu; <xref:System.Span%601> struktura faktycznie nie zawiera metody, która niszczy buforu.)</span><span class="sxs-lookup"><span data-stu-id="8b844-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="8b844-132">Bufor składa się z dwóch konsumentów `WriteInt32ToBuffer` i `DisplayBufferToConsole`.</span><span class="sxs-lookup"><span data-stu-id="8b844-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="8b844-133">Istnieje tylko jednego użytkownika w czasie (pierwszy `WriteInt32ToBuffer`, następnie `DisplayBufferToConsole`), a właścicielem żadnego konsumentów buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="8b844-134">Należy zauważyć, że "klienta" w tym kontekście nie implikują widok tylko do odczytu buforu; klientów można modyfikować zawartość buforu jako `WriteInt32ToBuffer` się dzieje, jeśli widok odczytu/zapisu buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="8b844-135">`WriteInt32ToBuffer` Metoda ma dzierżawę (mogą wykorzystywać) buforu między początkiem wywołania metody a czas, metoda zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="8b844-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="8b844-136">Podobnie `DisplayBufferToConsole` ma dzierżawę na buforze, podczas wykonywania i dzierżawy jest zwalniany, gdy metoda rozwija.</span><span class="sxs-lookup"><span data-stu-id="8b844-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="8b844-137">(Nie ma żadnych interfejsów API do zarządzania dzierżawy; "dzierżawy" jest kwestią koncepcyjny).</span><span class="sxs-lookup"><span data-stu-id="8b844-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="8b844-138">Pamięć\<T > i model właściciela i odbiorcy</span><span class="sxs-lookup"><span data-stu-id="8b844-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="8b844-139">Jako [właściciele, klientów i zarządzanie okresem istnienia](#owners-consumers-and-lifetime-management) informacje o sekcji, bufor zawsze ma właściciela.</span><span class="sxs-lookup"><span data-stu-id="8b844-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="8b844-140">Program .NET core obsługuje dwa modele własności:</span><span class="sxs-lookup"><span data-stu-id="8b844-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="8b844-141">Model, który obsługuje jednego właściciela.</span><span class="sxs-lookup"><span data-stu-id="8b844-141">A model that supports single ownership.</span></span> <span data-ttu-id="8b844-142">Bufor składa się z jednego właściciela dla jego cały okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="8b844-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="8b844-143">Model, który obsługuje przenoszenie własności.</span><span class="sxs-lookup"><span data-stu-id="8b844-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="8b844-144">Własność buforu można przenieść z jej właścicielem (twórcy) do innego składnika, która staje się odpowiedzialni za zarządzanie okresem istnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="8b844-145">Ten właściciel z kolei może przenieść własność na innego składnika i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8b844-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="8b844-146">Możesz użyć <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interfejsu jawnego zarządzania własności buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="8b844-147"><xref:System.Buffers.IMemoryOwner%601> obsługuje oba modele własności.</span><span class="sxs-lookup"><span data-stu-id="8b844-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="8b844-148">Składnik, który ma <xref:System.Buffers.IMemoryOwner%601> odwołanie jest właścicielem buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="8b844-149">W poniższym przykładzie użyto <xref:System.Buffers.IMemoryOwner%601?> wystąpienia, aby odzwierciedlić własności <xref:System.Memory%601> buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="8b844-150">Ten przykład z można także napisać [ `using` ](~/docs/csharp/language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="8b844-150">We can also write this example with the [`using`](~/docs/csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="8b844-151">W tym kodzie:</span><span class="sxs-lookup"><span data-stu-id="8b844-151">In this code:</span></span>

- <span data-ttu-id="8b844-152">`Main` Metoda zawiera odwołanie do <xref:System.Buffers.IMemoryOwner%601> wystąpienia, więc `Main` metody jest właścicielem buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="8b844-153">`WriteInt32ToBuffer` i `DisplayBufferToConsole` akceptować metod <xref:System.Memory%601> jako publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="8b844-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="8b844-154">W związku z tym są one konsumentów buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="8b844-155">I tylko zużywają go jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="8b844-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="8b844-156">Mimo że `WriteInt32ToBuffer` metoda jest przeznaczona do zapisu wartości w buforze `DisplayBufferToConsole` metoda nie jest.</span><span class="sxs-lookup"><span data-stu-id="8b844-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="8b844-157">Aby to odzwierciedlić go może zaakceptowali argumentu typu <xref:System.ReadOnlyMemory%601>.</span><span class="sxs-lookup"><span data-stu-id="8b844-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="8b844-158">Aby uzyskać dodatkowe informacje na temat <xref:System.ReadOnlyMemory%601>, zobacz [reguły nr 2: Użyj ReadOnlySpan\<T > lub ReadOnlyMemory\<T >, jeśli bufor ma być tylko do odczytu](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="8b844-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="8b844-159">"Ownerless" pamięci\<T > wystąpień</span><span class="sxs-lookup"><span data-stu-id="8b844-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="8b844-160">Możesz utworzyć <xref:System.Memory%601> wystąpienia bez użycia <xref:System.Buffers.IMemoryOwner%601>.</span><span class="sxs-lookup"><span data-stu-id="8b844-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="8b844-161">W tym przypadku własności buforu jest niejawny zamiast jawnego i tylko model jednego właściciela jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="8b844-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="8b844-162">Można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="8b844-162">You can do this by:</span></span>

- <span data-ttu-id="8b844-163">Wywołanie jednej z <xref:System.Memory%601> konstruktory bezpośrednio, przekazując `T[]`, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8b844-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="8b844-164">Wywoływanie [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) metodę rozszerzenia, aby wygenerować `ReadOnlyMemory<char>` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8b844-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="8b844-165">Metody, która początkowo <xref:System.Memory%601> wystąpienie jest niejawne właściciela buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="8b844-166">Własność nie można przenosić do innych składników, ponieważ nie istnieje żadne <xref:System.Buffers.IMemoryOwner%601> wystąpienia w celu ułatwienia transferu.</span><span class="sxs-lookup"><span data-stu-id="8b844-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="8b844-167">(Jako alternatywę, można także wyobrazić sobie, moduł odśmiecania pamięci środowiska wykonawczego jest właścicielem buforu i wszystkie metody tylko używanie buforu.)</span><span class="sxs-lookup"><span data-stu-id="8b844-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="8b844-168">Wytyczne dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="8b844-168">Usage guidelines</span></span>

<span data-ttu-id="8b844-169">Ponieważ blok pamięci jest właścicielem, ale jest przeznaczona do przekazania do wielu składników, z których część może działać po bloku pamięci jednocześnie, to ważne, aby ustanowić wytyczne dotyczące korzystania z obu <xref:System.Memory%601> i <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="8b844-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="8b844-170">Wytyczne są niezbędne, ponieważ:</span><span class="sxs-lookup"><span data-stu-id="8b844-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="8b844-171">Istnieje możliwość dla składnika, aby zachować odwołanie do bloku pamięci, po jego właściciela została wydana go.</span><span class="sxs-lookup"><span data-stu-id="8b844-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="8b844-172">Istnieje możliwość dla składnika może działać w buforze w tym samym czasie, który inny składnik działa na nim w procesie uszkodzenie danych w buforze.</span><span class="sxs-lookup"><span data-stu-id="8b844-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="8b844-173">While przydzielanych ze stosów rodzaj <xref:System.Span%601> optymalizację wydajności i sprawia, że <xref:System.Span%601> preferowany typ pracy w bloku pamięci, ona też przedmioty <xref:System.Span%601> niektóre główne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8b844-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="8b844-174">Ważne jest, aby wiedzieć, kiedy należy używać <xref:System.Span%601> i kiedy należy używać <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="8b844-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="8b844-175">Oto Nasze zalecenia dotyczące korzystania z pomyślnie <xref:System.Memory%601> i jej powiązane typy.</span><span class="sxs-lookup"><span data-stu-id="8b844-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="8b844-176">Należy pamiętać, że wskazówki, które ma zastosowanie do <xref:System.Memory%601> i <xref:System.Span%601> dotyczy także <xref:System.ReadOnlyMemory%601> i <xref:System.ReadOnlySpan%601> , chyba że firma Microsoft wyraźnie należy pamiętać, w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="8b844-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="8b844-177">**Reguła #1: Synchroniczne interfejsu API, należy użyć zakresu\<T > zamiast pamięci\<T > jako parametru, jeśli jest to możliwe.**</span><span class="sxs-lookup"><span data-stu-id="8b844-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="8b844-178"><xref:System.Span%601> jest bardziej wszechstronna niż <xref:System.Memory%601> i może reprezentować szeroką gamę buforów pamięci ciągłej.</span><span class="sxs-lookup"><span data-stu-id="8b844-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="8b844-179"><xref:System.Span%601> Ponadto zapewnia większą wydajność niż <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="8b844-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="8b844-180">Na koniec można użyć <xref:System.Memory%601.Span?displayProperty=nameWithType> właściwości, aby przekonwertować <xref:System.Memory%601> wystąpienia do <xref:System.Span%601>, chociaż zakresu\<T > - do - pamięci\<T > Konwersja nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="8b844-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="8b844-181">Tak, jeśli mają swoje obiekty wywołujące <xref:System.Memory%601> wystąpienia będą możliwe do wywołania metody z <xref:System.Span%601> parametry mimo to.</span><span class="sxs-lookup"><span data-stu-id="8b844-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="8b844-182">Za pomocą parametru typu <xref:System.Span%601> zamiast typu <xref:System.Memory%601> umożliwia też zapisu poprawne konsumencki implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="8b844-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="8b844-183">Automatycznie uzyskasz kontroli czasu kompilacji, aby upewnić się, że użytkownik nie próbujesz uzyskać dostęp w buforze poza dzierżawy Twojej formy, (uzyskać więcej informacji na ten temat poniżej).</span><span class="sxs-lookup"><span data-stu-id="8b844-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="8b844-184">Czasami musisz użyć <xref:System.Memory%601> parametr zamiast <xref:System.Span%601> parametru, nawet jeśli jesteś w pełni synchroniczne.</span><span class="sxs-lookup"><span data-stu-id="8b844-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="8b844-185">Przykład interfejsu API, który zależy Twoja praca akceptuje tylko <xref:System.Memory%601> argumentów.</span><span class="sxs-lookup"><span data-stu-id="8b844-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="8b844-186">Jest to poprawne, ale należy pamiętać o kompromisy związane, korzystając z <xref:System.Memory%601> synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="8b844-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="8b844-187">**Reguła #2: Użyj ReadOnlySpan\<T > lub ReadOnlyMemory\<T >, jeśli bufor ma być tylko do odczytu.**</span><span class="sxs-lookup"><span data-stu-id="8b844-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="8b844-188">W przypadku wcześniejszych przykładów `DisplayBufferToConsole` odczytuje tylko metody z buforu; go nie modyfikuje zawartość buforu.</span><span class="sxs-lookup"><span data-stu-id="8b844-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="8b844-189">Podpis metody należy je zmienić poniżej.</span><span class="sxs-lookup"><span data-stu-id="8b844-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="8b844-190">W rzeczywistości Jeśli połączono tej reguły i zasady nr 1, możemy zrobić jeszcze lepiej i ponowne zapisywanie adresów podpis metody:</span><span class="sxs-lookup"><span data-stu-id="8b844-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="8b844-191">`DisplayBufferToConsole` Metoda współpracuje teraz z niemal każdego typu buforu imaginable: `T[]`, Magazyn jest przydzielany za pomocą [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md)i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8b844-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), and so on.</span></span> <span data-ttu-id="8b844-192">Możesz nawet przekazać <xref:System.String> bezpośrednio do niego!</span><span class="sxs-lookup"><span data-stu-id="8b844-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="8b844-193">**Reguła #3: Jeśli metoda akceptuje pamięci\<T > i zwraca `void`, nie można używać pamięci\<T > wystąpienie, po powrocie z metody.**</span><span class="sxs-lookup"><span data-stu-id="8b844-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="8b844-194">Odnosi się to do pojęcia "dzierżawa" wspomnianych wcześniej.</span><span class="sxs-lookup"><span data-stu-id="8b844-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="8b844-195">Dzierżawa metodę zwracającą typ void <xref:System.Memory%601> wystąpienia rozpoczyna się po wprowadzeniu metody i go kończy się, gdy metoda kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="8b844-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="8b844-196">Rozważmy następujący przykład wywołuje `Log` w pętli, na podstawie danych wejściowych z konsoli.</span><span class="sxs-lookup"><span data-stu-id="8b844-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="8b844-197">Jeśli `Log` jest metodą synchroniczną pełni ten kod będzie działać zgodnie z oczekiwaniami, ponieważ istnieje tylko jeden aktywny konsumenta wystąpienia pamięci w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="8b844-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="8b844-198">Ale zamiast tego Załóżmy, że `Log` ma tę implementację.</span><span class="sxs-lookup"><span data-stu-id="8b844-198">But imagine instead that `Log` has this implementation.</span></span>

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

<span data-ttu-id="8b844-199">W tej implementacji `Log` narusza swojej dzierżawy, ponieważ nadal próbuje ona użyć <xref:System.Memory%601> wystąpienia w tle po zwrócił oryginalną metodę.</span><span class="sxs-lookup"><span data-stu-id="8b844-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="8b844-200">`Main` Metoda można zmutować bufora podczas `Log` próbuje odczytać z niego, co może spowodować uszkodzenie danych.</span><span class="sxs-lookup"><span data-stu-id="8b844-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="8b844-201">Istnieje kilka sposobów, aby rozwiązać ten problem:</span><span class="sxs-lookup"><span data-stu-id="8b844-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="8b844-202">`Log` Metoda może zwracać <xref:System.Threading.Tasks.Task> zamiast `void`, jako wykonania następujących `Log` metody.</span><span class="sxs-lookup"><span data-stu-id="8b844-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="8b844-203">`Log` Zamiast tego można zaimplementować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8b844-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="8b844-204">**Reguła #4: Jeśli metoda akceptuje pamięci\<T > i zwraca klasę Task, nie można używać pamięć\<T > wystąpienie po przejścia do zadań, aby stan końcowy.**</span><span class="sxs-lookup"><span data-stu-id="8b844-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="8b844-205">Jest to po prostu wariant async reguły nr 3.</span><span class="sxs-lookup"><span data-stu-id="8b844-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="8b844-206">`Log` Metody z poprzedniego przykładu mogą być zapisywane w następujący sposób są zgodne z tą regułą:</span><span class="sxs-lookup"><span data-stu-id="8b844-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="8b844-207">W tym miejscu "Stan końcowy" oznacza, że wystąpił błąd przejścia do zadań, aby ukończone, lub anulowane stanu.</span><span class="sxs-lookup"><span data-stu-id="8b844-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="8b844-208">Innymi słowy "Stan końcowy" oznacza "wszystko, co mogłoby spowodować await throw lub kontynuować wykonywanie."</span><span class="sxs-lookup"><span data-stu-id="8b844-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="8b844-209">Te wskazówki dotyczą metod, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, lub dowolny typ podobne.</span><span class="sxs-lookup"><span data-stu-id="8b844-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="8b844-210">**Reguła #5: Jeśli konstruktora akceptuje pamięci\<T > jako parametru, metodami wystąpień w utworzonym obiekcie są zakłada się, że konsumenci pamięci\<T > wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="8b844-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="8b844-211">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="8b844-211">Consider the following example:</span></span>

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

<span data-ttu-id="8b844-212">W tym miejscu `OddValueExtractor` Konstruktor akceptuje `ReadOnlyMemory<int>` jako parametr konstruktora sam Konstruktor więc konsumenta `ReadOnlyMemory<int>` wystąpienie, a wszystkie metody wystąpienia, w zwracanej wartości są również konsumentów oryginalny `ReadOnlyMemory<int>` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="8b844-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="8b844-213">Oznacza to, że `TryReadNextOddValue` zużywa `ReadOnlyMemory<int>` wystąpienia, nawet jeśli wystąpienie nie jest przekazywana bezpośrednio do `TryReadNextOddValue` metody.</span><span class="sxs-lookup"><span data-stu-id="8b844-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="8b844-214">**Reguła #6: Jeśli masz można ustawić pamięci\<T > — właściwości z określonym typem (lub metodą wystąpienia równoważne) od typu, metody wystąpienia obiektu, na którym są zakłada się, że konsumenci pamięci\<T > wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="8b844-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="8b844-215">Jest to tylko w wariancie reguły nr 5.</span><span class="sxs-lookup"><span data-stu-id="8b844-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="8b844-216">Ta reguła istnieje, ponieważ metod ustawiających właściwości lub metody równoważne są uznawane za przechwytywanie i zachować swoje dane wejściowe, więc metodami wystąpień w tym samym obiekcie mogących wykorzystywać przechwyconego stanu.</span><span class="sxs-lookup"><span data-stu-id="8b844-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="8b844-217">Poniższy przykład wyzwala tej reguły:</span><span class="sxs-lookup"><span data-stu-id="8b844-217">The following example triggers this rule:</span></span>

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

<span data-ttu-id="8b844-218">**Reguła #7: Jeśli masz IMemoryOwner\<T > odwołania, należy w pewnym punktu usuwać je lub przenieść własność (ale nie obu).**</span><span class="sxs-lookup"><span data-stu-id="8b844-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="8b844-219">Ponieważ <xref:System.Memory%601> wystąpienia może być zabezpieczony za pomocą zarządzanych lub niezarządzanych pamięci, należy wywołać właściciela <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> gdy praca jest wykonywana na <xref:System.Memory%601> wystąpienie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="8b844-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="8b844-220">Alternatywnie właściciel może przenieść własność <xref:System.Buffers.IMemoryOwner%601> wystąpienia inny składnik, w tym momencie uzyskiwania składnik jest odpowiedzialny za wywołanie <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> w odpowiednim czasie (więcej informacji na ten temat poniżej).</span><span class="sxs-lookup"><span data-stu-id="8b844-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="8b844-221">Nie można wywołać <xref:System.Buffers.MemoryPool%601.Dispose%2A> metoda może prowadzić do przecieków pamięci niezarządzanej lub innych spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="8b844-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="8b844-222">Ta reguła obowiązuje także kod, który wywołuje fabryki metod, takich jak <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b844-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8b844-223">Obiekt wywołujący staje się właścicielem zwracanego <xref:System.Buffers.IMemoryOwner%601> i jest odpowiedzialny za usuwanie wystąpienia, po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="8b844-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="8b844-224">**Reguła #8: Jeśli masz IMemoryOwner\<T > parametru w swojej powierzchni interfejsu API są akceptowane własności tego wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="8b844-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="8b844-225">Akceptowanie wystąpienia tego typu sygnalizuje, że zamierza przejąć prawo własności tego wystąpienia składnika.</span><span class="sxs-lookup"><span data-stu-id="8b844-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="8b844-226">Składnik staje się odpowiedzialny za właściwe usuwania zgodnie z reguły #7.</span><span class="sxs-lookup"><span data-stu-id="8b844-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="8b844-227">Dowolny składnik, który przenosi własności <xref:System.Buffers.IMemoryOwner%601> wystąpienia do innego składnika już nie należy używać tego wystąpienia, po zakończeniu wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="8b844-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b844-228">Jeśli konstruktora akceptuje <xref:System.Buffers.IMemoryOwner%601> jako parametru, jego typ powinien implementować <xref:System.IDisposable>i <xref:System.IDisposable.Dispose%2A> powinny wywoływać metodę <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b844-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8b844-229">**Reguła #9: Jeżeli metoda synchroniczna p/invoke, interfejs API powinien akceptować zakres\<T > jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="8b844-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="8b844-230">Zgodnie z zasadą #1 <xref:System.Span%601> ogólnie jest poprawnego typu na potrzeby synchronicznych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="8b844-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="8b844-231">Możesz przypiąć <xref:System.Span%601> wystąpień za pośrednictwem [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) — słowo kluczowe, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8b844-231">You can pin <xref:System.Span%601> instances via the [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="8b844-232">W poprzednim przykładzie `pbData` może mieć wartości null, jeśli na przykład zakres danych wejściowych jest pusta.</span><span class="sxs-lookup"><span data-stu-id="8b844-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="8b844-233">Jeśli metoda wyeksportowanego absolutnie wymaga, aby `pbData` wartości inne niż null, nawet jeśli `cbData` wynosi 0, metody można zaimplementować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8b844-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="8b844-234">**Reguła #10: Jeżeli metodą asynchroniczną p/invoke, interfejs API powinien akceptować pamięci\<T > jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="8b844-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="8b844-235">Ponieważ nie można użyć [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) — słowo kluczowe w operacji asynchronicznych, możesz użyć <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> metodę, aby przypiąć <xref:System.Memory%601> wystąpień, niezależnie od rodzaju ciągłej pamięci, które reprezentuje wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="8b844-235">Since you cannot use the [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="8b844-236">Poniższy przykład pokazuje, jak wykonać wywołanie asynchroniczne p/invoke za pomocą tego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="8b844-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)state;
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a><span data-ttu-id="8b844-237">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b844-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
