---
title: Wytyczne dotyczące użycia struktur Memory<T> i Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121961"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="15f83-102">Wytyczne dotyczące użycia struktur Memory\<T > i Span\<T></span><span class="sxs-lookup"><span data-stu-id="15f83-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="15f83-103">.NET Core zawiera wiele typów, które reprezentują dowolny ciągły region pamięci.</span><span class="sxs-lookup"><span data-stu-id="15f83-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="15f83-104">.NET Core 2.0 wprowadzone <xref:System.Span%601> i <xref:System.ReadOnlySpan%601>, które są lekkie bufory pamięci, które mogą być wspierane przez pamięć zarządzaną lub niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="15f83-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="15f83-105">Ponieważ te typy mogą być przechowywane tylko na stosie, są one nieodpowiednie dla wielu scenariuszy, w tym wywołania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="15f83-105">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="15f83-106">.NET Core 2.1 dodaje szereg dodatkowych <xref:System.Memory%601> <xref:System.ReadOnlyMemory%601>typów, w tym , , <xref:System.Buffers.IMemoryOwner%601>, i <xref:System.Buffers.MemoryPool%601>.</span><span class="sxs-lookup"><span data-stu-id="15f83-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="15f83-107">Podobnie <xref:System.Span%601> <xref:System.Memory%601> jak , a jego powiązane typy mogą być wspierane przez pamięć zarządzaną i niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="15f83-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="15f83-108">W <xref:System.Span%601> <xref:System.Memory%601> przeciwieństwie do , mogą być przechowywane na zarządzanym stercie.</span><span class="sxs-lookup"><span data-stu-id="15f83-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="15f83-109">Oba <xref:System.Span%601> <xref:System.Memory%601> i są bufory danych strukturalnych, które mogą być używane w potokach.</span><span class="sxs-lookup"><span data-stu-id="15f83-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="15f83-110">Oznacza to, że są one zaprojektowane tak, aby niektóre lub wszystkie dane mogą być efektywnie przekazywane do składników w potoku, które mogą je przetwarzać i opcjonalnie modyfikować buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="15f83-111">Ponieważ <xref:System.Memory%601> i jego powiązanych typów są dostępne przez wiele składników lub przez wiele wątków, ważne jest, aby deweloperzy przestrzegali niektórych standardowych wytycznych użycia do tworzenia niezawodnego kodu.</span><span class="sxs-lookup"><span data-stu-id="15f83-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="15f83-112">Właściciele, konsumenci i zarządzanie całym życiem</span><span class="sxs-lookup"><span data-stu-id="15f83-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="15f83-113">Ponieważ bufory mogą być przekazywane między interfejsami API, a ponieważ bufory są czasami dostępne z wielu wątków, należy wziąć pod uwagę zarządzanie okresem istnienia.</span><span class="sxs-lookup"><span data-stu-id="15f83-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="15f83-114">Istnieją trzy podstawowe pojęcia:</span><span class="sxs-lookup"><span data-stu-id="15f83-114">There are three core concepts:</span></span>

- <span data-ttu-id="15f83-115">**Własność**.</span><span class="sxs-lookup"><span data-stu-id="15f83-115">**Ownership**.</span></span> <span data-ttu-id="15f83-116">Właściciel wystąpienia buforu jest odpowiedzialny za zarządzanie okresem istnienia, w tym niszczenie buforu, gdy nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="15f83-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="15f83-117">Wszystkie bufory mają jednego właściciela.</span><span class="sxs-lookup"><span data-stu-id="15f83-117">All buffers have a single owner.</span></span> <span data-ttu-id="15f83-118">Zazwyczaj właściciel jest składnikiem, który utworzył bufor lub który odebrał bufor z fabryki.</span><span class="sxs-lookup"><span data-stu-id="15f83-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="15f83-119">Własność może również zostać przeniesiona; **Component-A** może zrezygnować z kontroli nad buforem do **Składnik-B**, w którym to momencie **Component-A** może już nie używać buforu, a **Component-B** staje się odpowiedzialny za zniszczenie buforu, gdy nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="15f83-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="15f83-120">**Zużycie**.</span><span class="sxs-lookup"><span data-stu-id="15f83-120">**Consumption**.</span></span> <span data-ttu-id="15f83-121">Konsument wystąpienia buforu może używać wystąpienia buforu, odczytując z niego i ewentualnie zapisując do niego.</span><span class="sxs-lookup"><span data-stu-id="15f83-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="15f83-122">Bufory mogą mieć jednego konsumenta naraz, chyba że podano jakiś mechanizm synchronizacji zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="15f83-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="15f83-123">Należy zauważyć, że aktywny konsument buforu niekoniecznie jest właścicielem buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="15f83-124">**Leasing**.</span><span class="sxs-lookup"><span data-stu-id="15f83-124">**Lease**.</span></span> <span data-ttu-id="15f83-125">Dzierżawa to czas, przez jaki dany składnik może być konsumentem buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="15f83-126">Poniższy przykład pseudokodu ilustruje te trzy pojęcia.</span><span class="sxs-lookup"><span data-stu-id="15f83-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="15f83-127">Zawiera `Main` metodę, która tworzy <xref:System.Memory%601> bufor typu, <xref:System.Char>wywołuje `WriteInt32ToBuffer` metodę do zapisu reprezentacji ciągu liczby całkowitej do buforu, a następnie wywołuje `DisplayBufferToConsole` metodę, aby wyświetlić wartość buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

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

<span data-ttu-id="15f83-128">Metoda `Main` tworzy bufor (w tym <xref:System.Span%601> przypadku wystąpienie) i tak jest jego właścicielem.</span><span class="sxs-lookup"><span data-stu-id="15f83-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="15f83-129">W `Main` związku z tym jest odpowiedzialny za zniszczenie buforu, gdy nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="15f83-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="15f83-130">Czyni to przez wywołanie <xref:System.Span%601.Clear?displayProperty=nameWithType> metody buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="15f83-131">(Metoda <xref:System.Span%601.Clear> w tym miejscu faktycznie czyści <xref:System.Span%601> pamięć buforu; struktura nie ma w rzeczywistości metody, która niszczy bufor).)</span><span class="sxs-lookup"><span data-stu-id="15f83-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="15f83-132">Bufor ma dwóch `WriteInt32ToBuffer` konsumentów `DisplayBufferToConsole`i .</span><span class="sxs-lookup"><span data-stu-id="15f83-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="15f83-133">Jest tylko jeden konsument naraz `WriteInt32ToBuffer`(najpierw , potem `DisplayBufferToConsole`), a żaden z konsumentów nie jest właścicielem bufora.</span><span class="sxs-lookup"><span data-stu-id="15f83-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="15f83-134">Należy również zauważyć, że "konsument" w tym kontekście nie oznacza widok tylko do odczytu buforu; konsumenci mogą modyfikować zawartość buforu, `WriteInt32ToBuffer` podobnie jak w przypadku widoku odczytu/zapisu buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="15f83-135">Metoda `WriteInt32ToBuffer` ma dzierżawy na (może zużywać) buformiędzy rozpoczęciem wywołania metody i czas zwraca metoda.</span><span class="sxs-lookup"><span data-stu-id="15f83-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="15f83-136">Podobnie ma `DisplayBufferToConsole` dzierżawy w buforze podczas wykonywania i dzierżawy jest zwalniany, gdy metoda rozwija.</span><span class="sxs-lookup"><span data-stu-id="15f83-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="15f83-137">(Nie ma API do zarządzania leasingiem; "leasing" jest sprawą koncepcyjną.)</span><span class="sxs-lookup"><span data-stu-id="15f83-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="15f83-138">Pamięć\<T> i model właściciela/konsumenta</span><span class="sxs-lookup"><span data-stu-id="15f83-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="15f83-139">Jak zauważa [sekcja Właściciele, konsumenci i zarządzanie okresem istnienia,](#owners-consumers-and-lifetime-management) bufor zawsze ma właściciela.</span><span class="sxs-lookup"><span data-stu-id="15f83-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="15f83-140">Program .NET Core obsługuje dwa modele własności:</span><span class="sxs-lookup"><span data-stu-id="15f83-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="15f83-141">Model, który obsługuje pojedynczej własności.</span><span class="sxs-lookup"><span data-stu-id="15f83-141">A model that supports single ownership.</span></span> <span data-ttu-id="15f83-142">Bufor ma jednego właściciela przez cały okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="15f83-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="15f83-143">Model, który obsługuje przeniesienie własności.</span><span class="sxs-lookup"><span data-stu-id="15f83-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="15f83-144">Własność buforu może zostać przeniesiona z jego pierwotnego właściciela (jego twórcy) do innego składnika, który następnie staje się odpowiedzialny za zarządzanie okresem istnienia buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="15f83-145">Ten właściciel może z kolei przenieść własność na inny składnik itd.</span><span class="sxs-lookup"><span data-stu-id="15f83-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="15f83-146">Interfejs służy <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> do jawnego zarządzania własnością buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="15f83-147"><xref:System.Buffers.IMemoryOwner%601>obsługuje oba modele własności.</span><span class="sxs-lookup"><span data-stu-id="15f83-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="15f83-148">Składnik, który <xref:System.Buffers.IMemoryOwner%601> ma odwołanie jest właścicielem buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="15f83-149">W poniższym <xref:System.Buffers.IMemoryOwner%601?> przykładzie użyto wystąpienia <xref:System.Memory%601> w celu odzwierciedlenia własności buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="15f83-150">Możemy również napisać ten [`using`](../../csharp/language-reference/keywords/using-statement.md)przykład z:</span><span class="sxs-lookup"><span data-stu-id="15f83-150">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="15f83-151">W tym kodzie:</span><span class="sxs-lookup"><span data-stu-id="15f83-151">In this code:</span></span>

- <span data-ttu-id="15f83-152">Metoda `Main` przechowuje odwołanie do <xref:System.Buffers.IMemoryOwner%601> wystąpienia, `Main` więc metoda jest właścicielem buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="15f83-153">Metody `WriteInt32ToBuffer` `DisplayBufferToConsole` i zaakceptować <xref:System.Memory%601> jako publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="15f83-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="15f83-154">W związku z tym są konsumentami buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="15f83-155">I spożywają go tylko jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="15f83-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="15f83-156">Mimo `WriteInt32ToBuffer` że metoda jest przeznaczona do zapisu `DisplayBufferToConsole` wartości do buforu, metoda nie jest.</span><span class="sxs-lookup"><span data-stu-id="15f83-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="15f83-157">Aby to odzwierciedlić, mógł zaakceptować argument <xref:System.ReadOnlyMemory%601>typu .</span><span class="sxs-lookup"><span data-stu-id="15f83-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="15f83-158">Aby uzyskać <xref:System.ReadOnlyMemory%601>dodatkowe informacje na temat , zobacz [reguła #2: Użyj\<ReadOnlySpan T> lub ReadOnlyMemory\<T>, jeśli bufor powinien być tylko do odczytu](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="15f83-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="15f83-159">Wystąpienia> pamięci\<"Ownerless" Memory T</span><span class="sxs-lookup"><span data-stu-id="15f83-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="15f83-160">Można utworzyć <xref:System.Memory%601> wystąpienie bez <xref:System.Buffers.IMemoryOwner%601>użycia .</span><span class="sxs-lookup"><span data-stu-id="15f83-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="15f83-161">W takim przypadku własność buforu jest niejawna, a nie jawna i obsługiwany jest tylko model jednego właściciela.</span><span class="sxs-lookup"><span data-stu-id="15f83-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="15f83-162">Można to zrobić przez:</span><span class="sxs-lookup"><span data-stu-id="15f83-162">You can do this by:</span></span>

- <span data-ttu-id="15f83-163">Wywołanie jednego <xref:System.Memory%601> z konstruktorów `T[]`bezpośrednio, przekazując w , jak w poniższym przykładzie nie.</span><span class="sxs-lookup"><span data-stu-id="15f83-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="15f83-164">Wywołanie [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) metody rozszerzenia `ReadOnlyMemory<char>` do tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="15f83-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="15f83-165">Metoda, która początkowo <xref:System.Memory%601> tworzy wystąpienie jest niejawnym właścicielem buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="15f83-166">Własność nie może zostać przeniesiona na <xref:System.Buffers.IMemoryOwner%601> żaden inny składnik, ponieważ nie ma żadnego przypadku ułatwiającego przeniesienie.</span><span class="sxs-lookup"><span data-stu-id="15f83-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="15f83-167">(Alternatywnie można również sobie wyobrazić, że moduł zbierający elementy bezużyteczne w czasie wykonywania jest właścicielem buforu, a wszystkie metody po prostu zużywają bufor).</span><span class="sxs-lookup"><span data-stu-id="15f83-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="15f83-168">Wskazówki dotyczące użytkowania</span><span class="sxs-lookup"><span data-stu-id="15f83-168">Usage guidelines</span></span>

<span data-ttu-id="15f83-169">Ponieważ blok pamięci jest własnością, ale jest przeznaczony do przekazania do wielu składników, z których niektóre mogą działać <xref:System.Memory%601> na <xref:System.Span%601>określonym bloku pamięci jednocześnie, ważne jest, aby ustanowić wytyczne dotyczące korzystania z obu i .</span><span class="sxs-lookup"><span data-stu-id="15f83-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="15f83-170">Wytyczne są niezbędne, ponieważ:</span><span class="sxs-lookup"><span data-stu-id="15f83-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="15f83-171">Jest możliwe dla składnika, aby zachować odwołanie do bloku pamięci po jego właściciel zwolnił go.</span><span class="sxs-lookup"><span data-stu-id="15f83-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="15f83-172">Jest możliwe dla składnika do pracy w buforze w tym samym czasie, że inny składnik działa na nim, w procesie uszkodzenia danych w buforze.</span><span class="sxs-lookup"><span data-stu-id="15f83-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="15f83-173">Podczas gdy charakter przydzielonego stosoptymalizuje <xref:System.Span%601> wydajność i sprawia, że <xref:System.Span%601> preferowany typ do pracy w bloku pamięci, podlega również <xref:System.Span%601> niektórych głównych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="15f83-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="15f83-174">Ważne jest, aby wiedzieć, <xref:System.Span%601> kiedy i <xref:System.Memory%601>kiedy używać .</span><span class="sxs-lookup"><span data-stu-id="15f83-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="15f83-175">Poniżej przedstawiono nasze zalecenia dotyczące <xref:System.Memory%601> pomyślnego korzystania z niego i powiązanych z nim typów.</span><span class="sxs-lookup"><span data-stu-id="15f83-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="15f83-176">Należy pamiętać, że <xref:System.Memory%601> wskazówki, które mają zastosowanie do i <xref:System.Span%601> odnosi się również do <xref:System.ReadOnlyMemory%601> i <xref:System.ReadOnlySpan%601> chyba że wyraźnie zanotujemy inaczej.</span><span class="sxs-lookup"><span data-stu-id="15f83-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="15f83-177">**Reguła #1: W przypadku synchronicznego\<interfejsu API\<należy użyć span T> zamiast pamięci T> jako parametr, jeśli to możliwe.**</span><span class="sxs-lookup"><span data-stu-id="15f83-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="15f83-178"><xref:System.Span%601>jest bardziej wszechstronny <xref:System.Memory%601> niż i może reprezentować szerszą gamę ciągłych buforów pamięci.</span><span class="sxs-lookup"><span data-stu-id="15f83-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="15f83-179"><xref:System.Span%601>oferuje również lepszą <xref:System.Memory%601>wydajność niż .</span><span class="sxs-lookup"><span data-stu-id="15f83-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="15f83-180">Na koniec można <xref:System.Memory%601.Span?displayProperty=nameWithType> użyć właściwości <xref:System.Memory%601> do konwersji <xref:System.Span%601>wystąpienia do\<, chociaż Span T>-to-Memory\<T> konwersja nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="15f83-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="15f83-181">Więc jeśli dzwoniący stało <xref:System.Memory%601> się wystąpienie, będą mogli wywołać metody <xref:System.Span%601> z parametrami i tak.</span><span class="sxs-lookup"><span data-stu-id="15f83-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="15f83-182">Przy użyciu parametru <xref:System.Span%601> typu <xref:System.Memory%601> zamiast typu pomaga również napisać implementację metody poprawne.</span><span class="sxs-lookup"><span data-stu-id="15f83-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="15f83-183">Automatycznie otrzymasz czeki w czasie kompilacji, aby upewnić się, że nie próbujesz uzyskać dostępu do buforu poza dzierżawą metody (więcej na ten temat później).</span><span class="sxs-lookup"><span data-stu-id="15f83-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="15f83-184">Czasami trzeba będzie użyć <xref:System.Memory%601> parametru zamiast <xref:System.Span%601> parametru, nawet jeśli jesteś w pełni synchroniczny.</span><span class="sxs-lookup"><span data-stu-id="15f83-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="15f83-185">Być może interfejs API, który <xref:System.Memory%601> zależy akceptuje tylko argumenty.</span><span class="sxs-lookup"><span data-stu-id="15f83-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="15f83-186">Jest to w porządku, ale należy pamiętać o <xref:System.Memory%601> kompromisów związanych z korzystaniem synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="15f83-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="15f83-187">**Reguła #2: Użyj\<readonlySpan T\<> lub ReadOnlyMemory T>, jeśli bufor powinien być tylko do odczytu.**</span><span class="sxs-lookup"><span data-stu-id="15f83-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="15f83-188">We wcześniejszych przykładach `DisplayBufferToConsole` metoda odczytuje tylko z buforu; nie modyfikuje zawartości buforu.</span><span class="sxs-lookup"><span data-stu-id="15f83-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="15f83-189">Podpis metody należy zmienić na następujący.</span><span class="sxs-lookup"><span data-stu-id="15f83-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="15f83-190">W rzeczywistości, jeśli połączymy tę regułę i regułę #1, możemy zrobić jeszcze lepiej i przepisać podpis metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="15f83-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="15f83-191">Metoda `DisplayBufferToConsole` działa teraz z praktycznie każdym `T[]`typem buforu, jaki można sobie wyobrazić: , magazyn przydzielony z [stackalloc](../../csharp/language-reference/operators/stackalloc.md)i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="15f83-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="15f83-192">Można nawet przekazać <xref:System.String> bezpośrednio do niego!</span><span class="sxs-lookup"><span data-stu-id="15f83-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="15f83-193">**Reguła #3: Jeśli metoda\<akceptuje> `void`pamięci T i\<zwraca, nie należy używać wystąpienia> pamięci T po powrocie metody.**</span><span class="sxs-lookup"><span data-stu-id="15f83-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="15f83-194">Odnosi się to do wspomnianej wcześniej koncepcji "leasingu".</span><span class="sxs-lookup"><span data-stu-id="15f83-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="15f83-195">Dzierżawa metody zwracania unieważnienia <xref:System.Memory%601> w wystąpieniu rozpoczyna się po wprowadzeniu metody i kończy się po zamknięciu metody.</span><span class="sxs-lookup"><span data-stu-id="15f83-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="15f83-196">Należy wziąć pod uwagę `Log` następujący przykład, który wywołuje w pętli na podstawie danych wejściowych z konsoli.</span><span class="sxs-lookup"><span data-stu-id="15f83-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="15f83-197">Jeśli `Log` jest w pełni synchroniczną metodą, ten kod będzie zachowywać się zgodnie z oczekiwaniami, ponieważ istnieje tylko jeden aktywny konsument wystąpienia pamięci w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="15f83-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="15f83-198">Ale wyobraźcie `Log` sobie, że ma to wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="15f83-198">But imagine instead that `Log` has this implementation.</span></span>

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

<span data-ttu-id="15f83-199">W tej `Log` implementacji narusza jego dzierżawy, <xref:System.Memory%601> ponieważ nadal próbuje użyć wystąpienia w tle po zwróceniu oryginalnej metody.</span><span class="sxs-lookup"><span data-stu-id="15f83-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="15f83-200">Metoda `Main` może mutować buforpodczas `Log` próby odczytu z niego, co może spowodować uszkodzenie danych.</span><span class="sxs-lookup"><span data-stu-id="15f83-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="15f83-201">Istnieje kilka sposobów rozwiązania tego problemu:</span><span class="sxs-lookup"><span data-stu-id="15f83-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="15f83-202">Metoda `Log` może zwrócić <xref:System.Threading.Tasks.Task> zamiast `void`, jak wykonuje `Log` następująca implementacja metody.</span><span class="sxs-lookup"><span data-stu-id="15f83-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="15f83-203">`Log`zamiast tego można zaimplementować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="15f83-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="15f83-204">**Reguła #4: Jeśli metoda\<akceptuje> pamięci T i zwraca zadanie, nie można używać wystąpienia> pamięci\<T po przejściu zadania do stanu terminala.**</span><span class="sxs-lookup"><span data-stu-id="15f83-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="15f83-205">To tylko asynchroniczne warianty reguły #3.</span><span class="sxs-lookup"><span data-stu-id="15f83-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="15f83-206">Metoda `Log` z wcześniejszego przykładu może być napisana w następujący sposób, aby zachować zgodność z tą regułą:</span><span class="sxs-lookup"><span data-stu-id="15f83-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="15f83-207">W tym miejscu "stan terminala" oznacza, że zadanie przechodzi do stanu ukończonego, uszkodzonego lub anulowanego.</span><span class="sxs-lookup"><span data-stu-id="15f83-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="15f83-208">Innymi słowy,"stan końcowy" oznacza "wszystko, co spowodowałoby oczekiwanie na rzut lub kontynuowanie egzekucji".</span><span class="sxs-lookup"><span data-stu-id="15f83-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="15f83-209">Niniejsze wskazówki dotyczą metod, <xref:System.Threading.Tasks.Task>które <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask%601>zwracają , , lub podobnego typu.</span><span class="sxs-lookup"><span data-stu-id="15f83-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="15f83-210">**Reguła #5: Jeśli konstruktor akceptuje pamięć\<T> jako parametr, metody wystąpienia na\<skonstruowanym obiekcie są uważane za konsumentów wystąpienia> pamięci T.**</span><span class="sxs-lookup"><span data-stu-id="15f83-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="15f83-211">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="15f83-211">Consider the following example:</span></span>

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

<span data-ttu-id="15f83-212">W tym `OddValueExtractor` miejscu konstruktor akceptuje `ReadOnlyMemory<int>` jako parametr konstruktora, więc `ReadOnlyMemory<int>` sam konstruktor jest konsumentem wystąpienia, a `ReadOnlyMemory<int>` wszystkie metody wystąpienia zwracanej wartości są również konsumentami oryginalnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="15f83-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="15f83-213">Oznacza to, `TryReadNextOddValue` że `ReadOnlyMemory<int>` zużywa wystąpienie, mimo że wystąpienie `TryReadNextOddValue` nie jest przekazywane bezpośrednio do metody.</span><span class="sxs-lookup"><span data-stu-id="15f83-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="15f83-214">**Reguła #6: Jeśli masz\<właściwość typu> typu ddefiniowaną pamięć T (lub równoważną metodę wystąpienia) na typie, metody wystąpienia tego obiektu są uważane za konsumentów wystąpienia> memory\<T.**</span><span class="sxs-lookup"><span data-stu-id="15f83-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="15f83-215">To jest naprawdę tylko wariant zasady #5.</span><span class="sxs-lookup"><span data-stu-id="15f83-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="15f83-216">Ta reguła istnieje, ponieważ ustawiaczy właściwości lub równoważne metody są zakładane do przechwytywania i utrwalić swoje dane wejściowe, więc metody wystąpienia na tym samym obiekcie może korzystać ze stanu przechwyconego.</span><span class="sxs-lookup"><span data-stu-id="15f83-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="15f83-217">W poniższym przykładzie wyzwoliono następującą regułę:</span><span class="sxs-lookup"><span data-stu-id="15f83-217">The following example triggers this rule:</span></span>

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

<span data-ttu-id="15f83-218">**Reguła #7: Jeśli masz\<iMemoryOwner T> odwołania, należy w pewnym momencie usunąć go lub przenieść jego własności (ale nie oba).**</span><span class="sxs-lookup"><span data-stu-id="15f83-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="15f83-219">Ponieważ <xref:System.Memory%601> wystąpienie może być wspierane przez pamięć zarządzaną lub <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> niezarządzaną, właściciel <xref:System.Memory%601> musi wywołać po zakończeniu pracy wykonywanej w wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="15f83-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="15f83-220">Alternatywnie właściciel może przenieść własność <xref:System.Buffers.IMemoryOwner%601> wystąpienia na inny składnik, w którym to momencie <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> składnik przejmujący staje się odpowiedzialny za wywołanie w odpowiednim czasie (więcej na ten temat później).</span><span class="sxs-lookup"><span data-stu-id="15f83-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="15f83-221">Niepowodzenie wywołania <xref:System.Buffers.MemoryPool%601.Dispose%2A> metody może prowadzić do przecieków pamięci niezarządzanej lub pogorszenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="15f83-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="15f83-222">Ta reguła ma również zastosowanie do <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>kodu, który wywołuje metody fabryczne, takie jak .</span><span class="sxs-lookup"><span data-stu-id="15f83-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="15f83-223">Obiekt wywołujący staje się właścicielem <xref:System.Buffers.IMemoryOwner%601> zwróconego i jest odpowiedzialny za usuwanie wystąpienia po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="15f83-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="15f83-224">**Reguła #8: Jeśli masz\<parametr IMemoryOwner T> na powierzchni interfejsu API, akceptujesz własność tego wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="15f83-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="15f83-225">Zaakceptowanie wystąpienia tego typu sygnalizuje, że składnik zamierza przejąć na własność to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="15f83-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="15f83-226">Twój składnik staje się odpowiedzialny za prawidłowe usuwanie zgodnie z zasadą #7.</span><span class="sxs-lookup"><span data-stu-id="15f83-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="15f83-227">Każdy składnik, który <xref:System.Buffers.IMemoryOwner%601> przenosi własność wystąpienia do innego składnika nie należy już używać tego wystąpienia po zakończeniu wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="15f83-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15f83-228">Jeśli konstruktor <xref:System.Buffers.IMemoryOwner%601> akceptuje jako parametr, <xref:System.IDisposable>jego typ <xref:System.IDisposable.Dispose%2A> powinien <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>implementować , a metoda powinna wywołać .</span><span class="sxs-lookup"><span data-stu-id="15f83-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="15f83-229">**Reguła #9: Jeśli zawijasz synchroniczną metodę p/invoke, interfejs API powinien zaakceptować> Span\<T jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="15f83-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="15f83-230">Zgodnie z regułą #1, <xref:System.Span%601> jest zazwyczaj poprawny typ do użycia dla synchronicznych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="15f83-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="15f83-231">Wystąpienia można <xref:System.Span%601> przypiąć za pomocą słowa kluczowego, [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15f83-231">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

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

<span data-ttu-id="15f83-232">W poprzednim przykładzie `pbData` może być null, jeśli na przykład zakres wejściowy jest pusty.</span><span class="sxs-lookup"><span data-stu-id="15f83-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="15f83-233">Jeśli wyeksportowana metoda `pbData` absolutnie wymaga, aby `cbData` być non-null, nawet jeśli jest 0, metoda może być zaimplementowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="15f83-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

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

<span data-ttu-id="15f83-234">**Reguła #10: Jeśli zawijasz metodę asynchroniczną p/invoke, interfejs API powinien akceptować> pamięci\<T jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="15f83-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="15f83-235">Ponieważ nie można [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) użyć słowa kluczowego w operacjach asynchronicznych, należy użyć <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> metody do przypinania <xref:System.Memory%601> wystąpień, niezależnie od rodzaju ciągłej pamięci, którą reprezentuje wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="15f83-235">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="15f83-236">W poniższym przykładzie pokazano, jak używać tego interfejsu API do wykonywania asynchronicznego wywołania p/invoke.</span><span class="sxs-lookup"><span data-stu-id="15f83-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="15f83-237">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15f83-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
