---
title: Wytyczne dotyczące użycia struktur Memory<T> i Span<T>
description: W tym artykule opisano pamięć <T> i zakres <T> , które są buforami danych strukturalnych w programie .NET Core, które mogą być używane w potokach.
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: b9405d746c141308c7d984dac9da0d65d1048d1e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380011"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="95c55-103">Wytyczne dotyczące użycia struktur Memory\<T > i Span\<T></span><span class="sxs-lookup"><span data-stu-id="95c55-103">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="95c55-104">Platforma .NET Core zawiera wiele typów, które reprezentują dowolny ciągły region pamięci.</span><span class="sxs-lookup"><span data-stu-id="95c55-104">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="95c55-105">Wdrożono program .NET Core 2,0 <xref:System.Span%601> i <xref:System.ReadOnlySpan%601> są to lekkie bufory pamięci, które mogą być obsługiwane przez pamięć zarządzaną lub niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="95c55-105">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="95c55-106">Ponieważ te typy mogą być przechowywane na stosie, są one nieodpowiednie dla wielu scenariuszy, w tym wywołań metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="95c55-106">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="95c55-107">Program .NET Core 2,1 dodaje wiele typów dodatkowych, takich jak <xref:System.Memory%601> , <xref:System.ReadOnlyMemory%601> , <xref:System.Buffers.IMemoryOwner%601> i <xref:System.Buffers.MemoryPool%601> .</span><span class="sxs-lookup"><span data-stu-id="95c55-107">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="95c55-108">Podobnie jak w <xref:System.Span%601> przypadku, gdy <xref:System.Memory%601> jego typy pokrewne mogą być obsługiwane przez pamięć zarządzaną i niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="95c55-108">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="95c55-109">W przeciwieństwie do <xref:System.Span%601> <xref:System.Memory%601> programu, można je przechowywać na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="95c55-109">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="95c55-110">Zarówno <xref:System.Span%601> , jak i <xref:System.Memory%601> są buforami danych strukturalnych, które mogą być używane w potokach.</span><span class="sxs-lookup"><span data-stu-id="95c55-110">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="95c55-111">Oznacza to, że zostały zaprojektowane tak, aby niektóre lub wszystkie dane mogły być efektywnie przesyłane do składników w potoku, które mogą je przetworzyć i opcjonalnie zmodyfikować bufor.</span><span class="sxs-lookup"><span data-stu-id="95c55-111">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="95c55-112">Ze względu na to, <xref:System.Memory%601> że i powiązane z nim typy są dostępne przez wiele składników lub przez wiele wątków, ważne jest, aby deweloperzy przestrzegali niektórych standardowych wytycznych dotyczących użycia w celu utworzenia niezawodnego kodu.</span><span class="sxs-lookup"><span data-stu-id="95c55-112">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="95c55-113">Właściciele, konsumenci i zarządzanie okresem istnienia</span><span class="sxs-lookup"><span data-stu-id="95c55-113">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="95c55-114">Ponieważ bufory mogą być przesyłane między interfejsami API, a ponieważ bufory mogą być dostępne z wielu wątków, ważne jest, aby wziąć pod uwagę zarządzanie okresem istnienia.</span><span class="sxs-lookup"><span data-stu-id="95c55-114">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="95c55-115">Istnieją trzy podstawowe koncepcje:</span><span class="sxs-lookup"><span data-stu-id="95c55-115">There are three core concepts:</span></span>

- <span data-ttu-id="95c55-116">**Własność**.</span><span class="sxs-lookup"><span data-stu-id="95c55-116">**Ownership**.</span></span> <span data-ttu-id="95c55-117">Właściciel wystąpienia buforu jest odpowiedzialny za zarządzanie okresem istnienia, w tym niszczenie bufora, gdy nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="95c55-117">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="95c55-118">Wszystkie bufory mają jednego właściciela.</span><span class="sxs-lookup"><span data-stu-id="95c55-118">All buffers have a single owner.</span></span> <span data-ttu-id="95c55-119">Zazwyczaj właścicielem jest składnik, który utworzył bufor lub odebrał bufor od fabryki.</span><span class="sxs-lookup"><span data-stu-id="95c55-119">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="95c55-120">Własność można także przenieść; **Składnik-a** może nawiązać kontrolę nad buforem ze **składnikiem B**, gdzie **składnik-a** nie może już korzystać z bufora, a **składnik-b** jest odpowiedzialny za niszczenie bufora, gdy nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="95c55-120">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="95c55-121">**Użycie**.</span><span class="sxs-lookup"><span data-stu-id="95c55-121">**Consumption**.</span></span> <span data-ttu-id="95c55-122">Odbiorca wystąpienia buforu może używać wystąpienia buforu przez odczyt z niego i prawdopodobnie zapis.</span><span class="sxs-lookup"><span data-stu-id="95c55-122">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="95c55-123">Bufory mogą mieć jednego konsumenta w danym momencie, chyba że zostanie podany zewnętrzny mechanizm synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="95c55-123">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="95c55-124">Aktywny konsument buforu nie musi być właścicielem bufora.</span><span class="sxs-lookup"><span data-stu-id="95c55-124">The active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="95c55-125">**Dzierżawa**.</span><span class="sxs-lookup"><span data-stu-id="95c55-125">**Lease**.</span></span> <span data-ttu-id="95c55-126">Dzierżawa to długość czasu, przez jaki dany składnik może być odbiorcą buforu.</span><span class="sxs-lookup"><span data-stu-id="95c55-126">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="95c55-127">Poniższy przykład pseudo kodu ilustruje te trzy koncepcje.</span><span class="sxs-lookup"><span data-stu-id="95c55-127">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="95c55-128">Zawiera `Main` metodę, która tworzy wystąpienie <xref:System.Memory%601> buforu typu <xref:System.Char> , wywołuje `WriteInt32ToBuffer` metodę w celu zapisania ciągu reprezentującego liczbę całkowitą do bufora, a następnie wywołuje `DisplayBufferToConsole` metodę, aby wyświetlić wartość buforu.</span><span class="sxs-lookup"><span data-stu-id="95c55-128">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

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

<span data-ttu-id="95c55-129">`Main`Metoda tworzy bufor (w tym przypadku <xref:System.Span%601> wystąpienie) i dlatego jest jego właścicielem.</span><span class="sxs-lookup"><span data-stu-id="95c55-129">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="95c55-130">W związku `Main` z tym, jest odpowiedzialny za niszczenie bufora, gdy nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="95c55-130">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="95c55-131">Robi to przez wywołanie <xref:System.Span%601.Clear?displayProperty=nameWithType> metody buforu.</span><span class="sxs-lookup"><span data-stu-id="95c55-131">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="95c55-132">(W <xref:System.Span%601.Clear> tym miejscu Metoda faktycznie czyści pamięć buforu; <xref:System.Span%601> Struktura nie ma w rzeczywistości metody, która niszczy bufor).</span><span class="sxs-lookup"><span data-stu-id="95c55-132">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="95c55-133">Bufor ma dwóch użytkowników `WriteInt32ToBuffer` i `DisplayBufferToConsole` .</span><span class="sxs-lookup"><span data-stu-id="95c55-133">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="95c55-134">W danym momencie istnieje tylko jeden użytkownik (pierwszy `WriteInt32ToBuffer` `DisplayBufferToConsole` ), a żaden z nich nie jest właścicielem buforu.</span><span class="sxs-lookup"><span data-stu-id="95c55-134">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="95c55-135">Należy zauważyć, że "konsument" w tym kontekście nie implikuje widoku tylko do odczytu buforu; Użytkownicy mogą modyfikować zawartość bufora, tak jak w `WriteInt32ToBuffer` przypadku widoku do odczytu/zapisu w buforze.</span><span class="sxs-lookup"><span data-stu-id="95c55-135">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="95c55-136">`WriteInt32ToBuffer`Metoda ma dzierżawę (może zużywać) bufor między początkiem wywołania metody a czasem zwracanym przez metodę.</span><span class="sxs-lookup"><span data-stu-id="95c55-136">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="95c55-137">Podobnie, `DisplayBufferToConsole` ma dzierżawę w buforze podczas wykonywania, a dzierżawa jest wydawana, gdy metoda zostanie rozwinięcia.</span><span class="sxs-lookup"><span data-stu-id="95c55-137">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="95c55-138">(Nie ma interfejsu API do zarządzania dzierżawą; "dzierżawa" jest kwestią koncepcyjną).</span><span class="sxs-lookup"><span data-stu-id="95c55-138">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="95c55-139">Pamięć \< T> i model właściciel/odbiorca</span><span class="sxs-lookup"><span data-stu-id="95c55-139">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="95c55-140">W przypadku, gdy [właściciele, odbiorcy i informacje o zarządzaniu okresem istnienia](#owners-consumers-and-lifetime-management) są uwagi, bufor zawsze ma właściciela.</span><span class="sxs-lookup"><span data-stu-id="95c55-140">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="95c55-141">Platforma .NET Core obsługuje dwa modele własności:</span><span class="sxs-lookup"><span data-stu-id="95c55-141">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="95c55-142">Model, który obsługuje pojedyncze własności.</span><span class="sxs-lookup"><span data-stu-id="95c55-142">A model that supports single ownership.</span></span> <span data-ttu-id="95c55-143">Bufor ma jednego właściciela na cały okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="95c55-143">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="95c55-144">Model obsługujący przenoszenie własności.</span><span class="sxs-lookup"><span data-stu-id="95c55-144">A model that supports ownership transfer.</span></span> <span data-ttu-id="95c55-145">Własność buforu można przenieść z jego oryginalnego właściciela (jego twórcy) do innego składnika, który następnie jest odpowiedzialny za zarządzanie okresem istnienia bufora.</span><span class="sxs-lookup"><span data-stu-id="95c55-145">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="95c55-146">Ten właściciel może zmienić własność transferu na inny składnik i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="95c55-146">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="95c55-147"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>Interfejs umożliwia jawne Zarządzanie własnością bufora.</span><span class="sxs-lookup"><span data-stu-id="95c55-147">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="95c55-148"><xref:System.Buffers.IMemoryOwner%601>obsługuje obydwa modele własności.</span><span class="sxs-lookup"><span data-stu-id="95c55-148"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="95c55-149">Składnik zawierający <xref:System.Buffers.IMemoryOwner%601> odwołanie jest właścicielem bufora.</span><span class="sxs-lookup"><span data-stu-id="95c55-149">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="95c55-150">Poniższy przykład używa wystąpienia, <xref:System.Buffers.IMemoryOwner%601?> aby odzwierciedlić własność <xref:System.Memory%601> bufora.</span><span class="sxs-lookup"><span data-stu-id="95c55-150">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="95c55-151">Możemy również napisać ten przykład z [`using`](../../csharp/language-reference/keywords/using-statement.md) :</span><span class="sxs-lookup"><span data-stu-id="95c55-151">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="95c55-152">W tym kodzie:</span><span class="sxs-lookup"><span data-stu-id="95c55-152">In this code:</span></span>

- <span data-ttu-id="95c55-153">`Main`Metoda przechowuje odwołanie do <xref:System.Buffers.IMemoryOwner%601> wystąpienia, dlatego `Main` Metoda jest właścicielem buforu.</span><span class="sxs-lookup"><span data-stu-id="95c55-153">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="95c55-154">`WriteInt32ToBuffer`Metody i `DisplayBufferToConsole` akceptują <xref:System.Memory%601> jako publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="95c55-154">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="95c55-155">W związku z tym są użytkownikami bufora.</span><span class="sxs-lookup"><span data-stu-id="95c55-155">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="95c55-156">I je zużywają jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="95c55-156">And they only consume it one at a time.</span></span>

<span data-ttu-id="95c55-157">Chociaż `WriteInt32ToBuffer` Metoda jest przeznaczona do zapisania wartości w buforze, `DisplayBufferToConsole` Metoda nie jest.</span><span class="sxs-lookup"><span data-stu-id="95c55-157">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="95c55-158">W celu odzwierciedlenia tej wartości może zatwierdzić argument typu <xref:System.ReadOnlyMemory%601> .</span><span class="sxs-lookup"><span data-stu-id="95c55-158">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="95c55-159">Aby uzyskać więcej informacji na temat <xref:System.ReadOnlyMemory%601> , zobacz temat [Rule #2: Użyj ReadOnlySpan \< t> lub ReadOnlyMemory \< t>, jeśli bufor powinien być tylko do odczytu](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="95c55-159">For more information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="95c55-160">Wystąpienia "pamięć bezwłaściciel" \< T> wystąpień</span><span class="sxs-lookup"><span data-stu-id="95c55-160">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="95c55-161">Można utworzyć <xref:System.Memory%601> wystąpienie bez użycia <xref:System.Buffers.IMemoryOwner%601> .</span><span class="sxs-lookup"><span data-stu-id="95c55-161">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="95c55-162">W takim przypadku własność buforu jest niejawna, a nie jawna, a tylko model jednego właściciela jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="95c55-162">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="95c55-163">Można to zrobić, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="95c55-163">You can do this by:</span></span>

- <span data-ttu-id="95c55-164">Wywołanie jednego z <xref:System.Memory%601> konstruktorów bezpośrednio, przekazanie w `T[]` , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="95c55-164">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="95c55-165">Wywoływanie metody rozszerzenia [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) w celu utworzenia `ReadOnlyMemory<char>` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="95c55-165">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="95c55-166">Metoda, która początkowo tworzy <xref:System.Memory%601> wystąpienie, jest niejawnym właścicielem buforu.</span><span class="sxs-lookup"><span data-stu-id="95c55-166">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="95c55-167">Własności nie można przenieść do żadnego innego składnika, ponieważ nie ma żadnego <xref:System.Buffers.IMemoryOwner%601> wystąpienia, aby ułatwić transfer.</span><span class="sxs-lookup"><span data-stu-id="95c55-167">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="95c55-168">(Alternatywnie można również wyobrazić, że moduł wyrzucania elementów bezużytecznych środowiska uruchomieniowego jest właścicielem buforu, a wszystkie metody zużywają bufor).</span><span class="sxs-lookup"><span data-stu-id="95c55-168">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="95c55-169">Zalecenia dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="95c55-169">Usage guidelines</span></span>

<span data-ttu-id="95c55-170">Ponieważ blok pamięci jest własnością, ale jest przeznaczony do przekazywania do wielu składników, a niektóre z nich mogą pracować w konkretnym bloku pamięci jednocześnie, ważne jest ustanowienie wytycznych dotyczących używania obu <xref:System.Memory%601> i <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="95c55-170">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="95c55-171">Wytyczne są niezbędne, ponieważ:</span><span class="sxs-lookup"><span data-stu-id="95c55-171">Guidelines are necessary because:</span></span>

- <span data-ttu-id="95c55-172">Jest możliwe, że składnik zachowuje odwołanie do bloku pamięci po jego udostępnieniu przez jego właściciela.</span><span class="sxs-lookup"><span data-stu-id="95c55-172">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="95c55-173">Składnik może działać w buforze w tym samym czasie, w którym działa inny składnik, w procesie uszkodzonym dane w buforze.</span><span class="sxs-lookup"><span data-stu-id="95c55-173">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="95c55-174">Chociaż przydzielony przez stos charakter <xref:System.Span%601> optymalizuje wydajność i udostępnia <xref:System.Span%601> preferowany typ dla działania w bloku pamięci, to również <xref:System.Span%601> istotne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="95c55-174">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="95c55-175">Ważne jest, aby wiedzieć, kiedy należy użyć <xref:System.Span%601> i kiedy należy używać programu <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="95c55-175">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="95c55-176">Poniżej przedstawiono nasze zalecenia dotyczące pomyślnego użycia <xref:System.Memory%601> i powiązanych typów.</span><span class="sxs-lookup"><span data-stu-id="95c55-176">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="95c55-177">Wskazówki odnoszące się do programu <xref:System.Memory%601> i <xref:System.Span%601> dotyczą także <xref:System.ReadOnlyMemory%601> i, <xref:System.ReadOnlySpan%601> chyba że jawnie zanotujemy inaczej.</span><span class="sxs-lookup"><span data-stu-id="95c55-177">Guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="95c55-178">**Reguła #1: w przypadku synchronicznego interfejsu API należy użyć funkcji span \< t> zamiast pamięci \< t> jako parametru, jeśli jest to możliwe.**</span><span class="sxs-lookup"><span data-stu-id="95c55-178">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="95c55-179"><xref:System.Span%601>jest bardziej uniwersalny niż <xref:System.Memory%601> i może reprezentować szeroką gamę ciągłych buforów pamięci.</span><span class="sxs-lookup"><span data-stu-id="95c55-179"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="95c55-180"><xref:System.Span%601>oferuje również lepszą wydajność niż <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="95c55-180"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="95c55-181">Na koniec można użyć <xref:System.Memory%601.Span?displayProperty=nameWithType> właściwości, aby skonwertować <xref:System.Memory%601> wystąpienie na <xref:System.Span%601> , chociaż \< nie jest możliwe przeprowadzenie konwersji z>> na pamięć \< .</span><span class="sxs-lookup"><span data-stu-id="95c55-181">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="95c55-182">Dlatego jeśli obiekty wywołujące miały <xref:System.Memory%601> wystąpienie, będą mogły wywołać metody z <xref:System.Span%601> parametrami.</span><span class="sxs-lookup"><span data-stu-id="95c55-182">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="95c55-183">Użycie parametru typu <xref:System.Span%601> zamiast typu <xref:System.Memory%601> pomaga napisać poprawną implementację metody zużywanej.</span><span class="sxs-lookup"><span data-stu-id="95c55-183">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="95c55-184">Będziesz automatycznie otrzymywać sprawdzenia czasu kompilacji, aby upewnić się, że nie próbujesz uzyskać dostępu do buforu poza dzierżawą metody (więcej informacji na ten temat).</span><span class="sxs-lookup"><span data-stu-id="95c55-184">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="95c55-185">Czasami musisz użyć <xref:System.Memory%601> parametru zamiast <xref:System.Span%601> parametru, nawet jeśli jest w pełni synchroniczne.</span><span class="sxs-lookup"><span data-stu-id="95c55-185">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="95c55-186">Być może interfejs API, który jest zależny, akceptuje tylko <xref:System.Memory%601> argumenty.</span><span class="sxs-lookup"><span data-stu-id="95c55-186">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="95c55-187">Jest to dokładne, ale należy pamiętać o kompromisach, które są wykorzystywane w przypadku synchronicznego korzystania z programu <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="95c55-187">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="95c55-188">**Reguła #2: Użyj ReadOnlySpan \< t> lub ReadOnlyMemory \<> t, jeśli bufor powinien być tylko do odczytu.**</span><span class="sxs-lookup"><span data-stu-id="95c55-188">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="95c55-189">We wcześniejszych przykładach `DisplayBufferToConsole` Metoda odczytuje tylko dane z bufora; nie modyfikuje zawartości buforu.</span><span class="sxs-lookup"><span data-stu-id="95c55-189">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="95c55-190">Sygnaturę metody należy zmienić na następujący.</span><span class="sxs-lookup"><span data-stu-id="95c55-190">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="95c55-191">W rzeczywistości, Jeśli połączymy tę regułę i #1 reguł, możemy jeszcze bardziej ulepszyć i napisać sygnaturę metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="95c55-191">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="95c55-192">`DisplayBufferToConsole`Metoda działa teraz z niemal każdym typem bufora urojonym: `T[]` , magazynem przydzielonym z [stackalloc](../../csharp/language-reference/operators/stackalloc.md)i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="95c55-192">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="95c55-193">Możesz nawet przekazać <xref:System.String> bezpośrednio do programu!</span><span class="sxs-lookup"><span data-stu-id="95c55-193">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="95c55-194">**Reguła #3: Jeśli metoda akceptuje pamięć \< t> i zwraca `void` , nie należy używać \< wystąpienia pamięci t> po powrocie metody.**</span><span class="sxs-lookup"><span data-stu-id="95c55-194">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="95c55-195">Odnosi się to do pojęcia "Lease" wymienionego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="95c55-195">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="95c55-196">Dzierżawa metody zwracającej wartość void w <xref:System.Memory%601> wystąpieniu rozpoczyna się po wprowadzeniu metody i kończy się po zakończeniu metody.</span><span class="sxs-lookup"><span data-stu-id="95c55-196">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="95c55-197">Rozważmy poniższy przykład, który wywołuje `Log` pętlę na podstawie danych wejściowych z konsoli.</span><span class="sxs-lookup"><span data-stu-id="95c55-197">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="95c55-198">Jeśli `Log` jest to w pełni synchroniczna Metoda, ten kod będzie zachowywać się zgodnie z oczekiwaniami, ponieważ w danym momencie istnieje tylko jeden aktywny użytkownik wystąpienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="95c55-198">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="95c55-199">Ale Wyobraź sobie, że `Log` Ta implementacja jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="95c55-199">But imagine instead that `Log` has this implementation.</span></span>

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

<span data-ttu-id="95c55-200">W tej implementacji `Log` narusza swoją dzierżawę, ponieważ nadal próbuje użyć <xref:System.Memory%601> wystąpienia w tle po zwróceniu pierwotnej metody.</span><span class="sxs-lookup"><span data-stu-id="95c55-200">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="95c55-201">`Main`Metoda może być mutacją buforu podczas `Log` próby odczytu z niego, co może spowodować uszkodzenie danych.</span><span class="sxs-lookup"><span data-stu-id="95c55-201">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="95c55-202">Istnieje kilka sposobów rozwiązania tego problemu:</span><span class="sxs-lookup"><span data-stu-id="95c55-202">There are several ways to resolve this:</span></span>

- <span data-ttu-id="95c55-203">`Log`Metoda może zwrócić <xref:System.Threading.Tasks.Task> zamiast `void` , ponieważ Poniższa implementacja `Log` metody.</span><span class="sxs-lookup"><span data-stu-id="95c55-203">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="95c55-204">`Log`Zamiast tego można zaimplementować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="95c55-204">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="95c55-205">**Reguła #4: Jeśli metoda akceptuje pamięć \< t> i zwraca zadanie, nie należy używać \< wystąpienia pamięci t> po przejściu zadań do stanu terminalu.**</span><span class="sxs-lookup"><span data-stu-id="95c55-205">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="95c55-206">Jest to tylko asynchroniczny wariant reguły #3.</span><span class="sxs-lookup"><span data-stu-id="95c55-206">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="95c55-207">`Log`Metodę z wcześniejszego przykładu można napisać w następujący sposób, aby zachować zgodność z tą regułą:</span><span class="sxs-lookup"><span data-stu-id="95c55-207">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="95c55-208">W tym miejscu "stan terminalu" oznacza, że zadanie przechodzi do stanu ukończone, Niepowodzenie lub anulowane.</span><span class="sxs-lookup"><span data-stu-id="95c55-208">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="95c55-209">Innymi słowy "stan terminalu" oznacza "wszystkie elementy, które mogłyby spowodować, że oczekujące na zgłoszenie lub kontynuowanie wykonywania".</span><span class="sxs-lookup"><span data-stu-id="95c55-209">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="95c55-210">Te wskazówki dotyczą metod, które zwracają <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.ValueTask%601> lub mają podobny typ.</span><span class="sxs-lookup"><span data-stu-id="95c55-210">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="95c55-211">**Reguła #5: Jeśli Konstruktor akceptuje> pamięci \< jako parametr, zakłada się, że metody wystąpienia na skonstruowanym obiekcie są traktowane jako konsumenci z \< wystąpienia pamięci t>.**</span><span class="sxs-lookup"><span data-stu-id="95c55-211">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="95c55-212">Rozważmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="95c55-212">Consider the following example:</span></span>

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

<span data-ttu-id="95c55-213">W tym miejscu `OddValueExtractor` Konstruktor akceptuje `ReadOnlyMemory<int>` jako parametr konstruktora, więc Konstruktor jest odbiorcą `ReadOnlyMemory<int>` wystąpienia, a wszystkie metody wystąpienia w zwracanej wartości są również odbiorcami oryginalnego `ReadOnlyMemory<int>` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="95c55-213">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="95c55-214">Oznacza to, że `TryReadNextOddValue` zużywa `ReadOnlyMemory<int>` wystąpienie, mimo że wystąpienie nie jest bezpośrednio przesyłane do `TryReadNextOddValue` metody.</span><span class="sxs-lookup"><span data-stu-id="95c55-214">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="95c55-215">**Reguła #6: Jeśli \< w danym typie istnieje właściwość set> Table (lub równoważna metoda wystąpienia) dla tego obiektu, zakłada się, że metody wystąpień na tym obiekcie są klientami z \< wystąpienia pamięci T>.**</span><span class="sxs-lookup"><span data-stu-id="95c55-215">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="95c55-216">Jest to tylko wariant reguły #5.</span><span class="sxs-lookup"><span data-stu-id="95c55-216">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="95c55-217">Ta reguła istnieje, ponieważ przyjmuje się, że metody ustawiające właściwości lub równoważne metody przechwytują i utrzymują dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="95c55-217">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="95c55-218">Poniższy przykład wyzwala tę regułę:</span><span class="sxs-lookup"><span data-stu-id="95c55-218">The following example triggers this rule:</span></span>

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

<span data-ttu-id="95c55-219">**#7 reguły: Jeśli masz \< odwołanie IMemoryOwner T>, musisz mieć w pewnym momencie usunąć lub przenieść jego własność (ale nie oba).**</span><span class="sxs-lookup"><span data-stu-id="95c55-219">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="95c55-220">Ponieważ <xref:System.Memory%601> wystąpienie może być obsługiwane przez pamięć zarządzaną lub niezarządzaną, właściciel musi wywołać, <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> gdy działanie wykonane w <xref:System.Memory%601> wystąpieniu zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="95c55-220">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="95c55-221">Alternatywnie właściciel może przenieść własność <xref:System.Buffers.IMemoryOwner%601> wystąpienia do innego składnika, w tym momencie składnik pozyskiwania będzie odpowiedzialny za wywoływanie <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> w odpowiednim czasie (więcej informacji na ten temat).</span><span class="sxs-lookup"><span data-stu-id="95c55-221">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="95c55-222">Niepowodzenie wywołania <xref:System.Buffers.MemoryPool%601.Dispose%2A> metody może prowadzić do niezarządzanych przecieków pamięci lub obniżenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="95c55-222">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="95c55-223">Ta reguła dotyczy również kodu, który wywołuje metody fabryki, takie jak <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="95c55-223">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95c55-224">Obiekt wywołujący zostaje właścicielem zwróconego <xref:System.Buffers.IMemoryOwner%601> i jest odpowiedzialny za likwidację wystąpienia po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="95c55-224">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="95c55-225">**Reguła #8: Jeśli masz \< parametr IMemoryOwner T> na powierzchni interfejsu API, akceptujesz własność tego wystąpienia.**</span><span class="sxs-lookup"><span data-stu-id="95c55-225">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="95c55-226">Zaakceptowanie wystąpienia tego typu sygnalizuje, że składnik zamierza przejąć własność tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="95c55-226">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="95c55-227">Składnik jest odpowiedzialny za poprawność usuwania zgodnie z regułą #7.</span><span class="sxs-lookup"><span data-stu-id="95c55-227">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="95c55-228">Każdy składnik, który przenosi własność <xref:System.Buffers.IMemoryOwner%601> wystąpienia na inny składnik, nie powinien już korzystać z tego wystąpienia po zakończeniu wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="95c55-228">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95c55-229">Jeśli Konstruktor akceptuje <xref:System.Buffers.IMemoryOwner%601> jako parametr, jego typ powinien implementować <xref:System.IDisposable> , a <xref:System.IDisposable.Dispose%2A> Metoda powinna wywołać <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="95c55-229">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="95c55-230">**#9 reguły: w przypadku pakowania synchronicznej metody p/Invoke interfejs API powinien akceptować zakres \< T> jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="95c55-230">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="95c55-231">Zgodnie z regułą #1, <xref:System.Span%601> jest zazwyczaj prawidłowym typem używanym do synchronicznych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="95c55-231">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="95c55-232">Można przypiąć <xref:System.Span%601> wystąpienia za pomocą [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) słowa kluczowego, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="95c55-232">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

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

<span data-ttu-id="95c55-233">W poprzednim przykładzie `pbData` może mieć wartość null, jeśli na przykład zakres wejściowy jest pusty.</span><span class="sxs-lookup"><span data-stu-id="95c55-233">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="95c55-234">Jeśli wyeksportowana Metoda absolutnie wymaga `pbData` , aby nie mieć wartości null, nawet jeśli `cbData` jest równa 0, Metoda może być implementowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="95c55-234">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

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

<span data-ttu-id="95c55-235">**#10 reguły: w przypadku zawijania asynchronicznej metody p/Invoke interfejs API powinien akceptować \<> pamięci jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="95c55-235">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="95c55-236">Ponieważ nie można użyć [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) słowa kluczowego w operacjach asynchronicznych, należy użyć <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> metody <xref:System.Memory%601> , aby przypiąć wystąpienia, niezależnie od rodzaju ciągłej pamięci reprezentowanej przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="95c55-236">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="95c55-237">Poniższy przykład pokazuje, jak używać tego interfejsu API do wykonywania asynchronicznego wywołania p/Invoke.</span><span class="sxs-lookup"><span data-stu-id="95c55-237">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

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
    var actualState = (MyCompletedCallbackState)(handle.Target);
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

## <a name="see-also"></a><span data-ttu-id="95c55-238">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95c55-238">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
