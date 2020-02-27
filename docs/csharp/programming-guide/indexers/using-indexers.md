---
title: Korzystanie z indeksatorów C# — Przewodnik programowania
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628166"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="11d0d-102">Korzystanie z indeksatorówC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="11d0d-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="11d0d-103">Indeksatory to wygoda składni, która umożliwia tworzenie [klasy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md)lub [interfejsu](../../language-reference/keywords/interface.md) , które aplikacje klienckie mogą uzyskiwać dostęp do samego siebie jako tablicy.</span><span class="sxs-lookup"><span data-stu-id="11d0d-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="11d0d-104">Indeksatory są najczęściej implementowane w typach, których głównym celem jest hermetyzacja wewnętrznej kolekcji lub tablicy.</span><span class="sxs-lookup"><span data-stu-id="11d0d-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="11d0d-105">Załóżmy na przykład, że masz klasę `TempRecord`, która reprezentuje temperaturę w Fahrenheita w ciągu 10 różnych razy w okresie 24 godzin.</span><span class="sxs-lookup"><span data-stu-id="11d0d-105">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="11d0d-106">Klasa zawiera tablicę `temps` typu `float[]` do przechowywania wartości temperatury.</span><span class="sxs-lookup"><span data-stu-id="11d0d-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="11d0d-107">Implementując indeksator w tej klasie, klienci mogą uzyskać dostęp do temperatury w wystąpieniu `TempRecord` jako `float temp = tr[4]`, a nie jako `float temp = tr.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="11d0d-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="11d0d-108">Notacja indeksatora nie tylko upraszcza składnię aplikacji klienckich; sprawia również, że Klasa i jej cel są bardziej intuicyjne dla innych deweloperów do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="11d0d-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="11d0d-109">Aby zadeklarować indeksator dla klasy lub struktury, użyj słowa kluczowego [this](../../language-reference/keywords/this.md) , jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="11d0d-109">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="11d0d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11d0d-110">Remarks</span></span>

<span data-ttu-id="11d0d-111">Typ indeksatora i typ jego parametrów muszą być co najmniej tak samo samo jak indeksator.</span><span class="sxs-lookup"><span data-stu-id="11d0d-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="11d0d-112">Aby uzyskać więcej informacji na temat poziomów ułatwień dostępu, zobacz [Modyfikatory dostępu](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="11d0d-112">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="11d0d-113">Aby uzyskać więcej informacji na temat używania indeksatorów z interfejsem, zobacz [indeksatory interfejsów](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="11d0d-113">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="11d0d-114">Podpis indeksatora składa się z liczby i typów jego parametrów formalnych.</span><span class="sxs-lookup"><span data-stu-id="11d0d-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="11d0d-115">Nie zawiera typu indeksatora ani nazw parametrów formalnych.</span><span class="sxs-lookup"><span data-stu-id="11d0d-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="11d0d-116">Jeśli zadeklarujesz więcej niż jeden indeksator w tej samej klasie, muszą mieć różne podpisy.</span><span class="sxs-lookup"><span data-stu-id="11d0d-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="11d0d-117">Wartość indeksatora nie została sklasyfikowana jako zmienna; w związku z tym nie można przekazać wartości indeksatora jako parametru [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="11d0d-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="11d0d-118">Aby podać indeksator z nazwą, która może być używana przez inne języki, użyj <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="11d0d-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="11d0d-119">Ten indeksator będzie miał nazwę `TheItem`.</span><span class="sxs-lookup"><span data-stu-id="11d0d-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="11d0d-120">Niedostarczenie atrybutu Name spowodowałoby `Item` nazwy domyślnej.</span><span class="sxs-lookup"><span data-stu-id="11d0d-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="11d0d-121">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="11d0d-121">Example 1</span></span>  
  
<span data-ttu-id="11d0d-122">Poniższy przykład pokazuje, jak zadeklarować pole tablicy prywatnej, `temps`i indeksator.</span><span class="sxs-lookup"><span data-stu-id="11d0d-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="11d0d-123">Indeksator umożliwia bezpośredni dostęp do wystąpienia `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="11d0d-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="11d0d-124">Alternatywą dla korzystania z indeksatora jest zadeklarowanie tablicy jako członka [publicznego](../../language-reference/keywords/public.md) i dostęp do jej członków, `tempRecord.temps[i]`, bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="11d0d-124">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="11d0d-125">Należy zauważyć, że gdy jest oceniany dostęp indeksatora, na przykład w instrukcji `Console.Write`, metoda dostępu [Get](../../language-reference/keywords/get.md) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="11d0d-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="11d0d-126">W związku z tym, jeśli nie istnieje metoda dostępu `get`, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="11d0d-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="11d0d-127">Indeksowanie przy użyciu innych wartości</span><span class="sxs-lookup"><span data-stu-id="11d0d-127">Indexing using other values</span></span>

<span data-ttu-id="11d0d-128">C#nie ogranicza typu parametru indeksatora do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="11d0d-128">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="11d0d-129">Na przykład przydatne może być użycie ciągu z indeksatorem.</span><span class="sxs-lookup"><span data-stu-id="11d0d-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="11d0d-130">Takie indeksatory mogą być implementowane przez wyszukanie ciągu w kolekcji i zwrócenie odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="11d0d-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="11d0d-131">W miarę jak metody dostępu mogą być przeciążone, wersje typu String i Integer mogą współistnieć.</span><span class="sxs-lookup"><span data-stu-id="11d0d-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="11d0d-132">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="11d0d-132">Example 2</span></span>  
  
<span data-ttu-id="11d0d-133">Poniższy przykład deklaruje klasę, w której są przechowywane dni tygodnia.</span><span class="sxs-lookup"><span data-stu-id="11d0d-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="11d0d-134">Metoda dostępu `get` przyjmuje ciąg, nazwę dnia i zwraca odpowiednią liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="11d0d-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="11d0d-135">Na przykład "Niedziela" zwraca 0, "poniedziałek" zwraca 1 itd.</span><span class="sxs-lookup"><span data-stu-id="11d0d-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="11d0d-136">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="11d0d-136">Robust programming</span></span>

 <span data-ttu-id="11d0d-137">Istnieją dwa główne sposoby, w których można ulepszyć zabezpieczenia i niezawodność indeksatorów:</span><span class="sxs-lookup"><span data-stu-id="11d0d-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="11d0d-138">Należy pamiętać o uwzględnieniu niektórych typów strategii obsługi błędów, aby obsłużyć prawdopodobieństwo przekazania kodu klienta w nieprawidłowej wartości indeksu.</span><span class="sxs-lookup"><span data-stu-id="11d0d-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="11d0d-139">W pierwszym przykładzie wcześniej w tym temacie Klasa TempRecord zawiera właściwość length, która umożliwia zweryfikowanie danych wejściowych przed przekazaniem ich do indeksatora.</span><span class="sxs-lookup"><span data-stu-id="11d0d-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="11d0d-140">Można również umieścić kod obsługi błędu wewnątrz indeksatora.</span><span class="sxs-lookup"><span data-stu-id="11d0d-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="11d0d-141">Upewnij się, że dla użytkowników występują wyjątki, które można zgłosić w metodzie dostępu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="11d0d-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="11d0d-142">Ustaw dostępność metod dostępu [Get](../../language-reference/keywords/get.md) i [Set](../../language-reference/keywords/set.md) tak, aby były tak restrykcyjne, jak to uzasadnione.</span><span class="sxs-lookup"><span data-stu-id="11d0d-142">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="11d0d-143">Jest to ważne w przypadku metody dostępu `set` w szczególności.</span><span class="sxs-lookup"><span data-stu-id="11d0d-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="11d0d-144">Aby uzyskać więcej informacji, zobacz [ograniczanie dostępności metody](../classes-and-structs/restricting-accessor-accessibility.md)dostępu.</span><span class="sxs-lookup"><span data-stu-id="11d0d-144">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d0d-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11d0d-145">See also</span></span>

- [<span data-ttu-id="11d0d-146">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="11d0d-146">C# Programming Guide</span></span>](../index.md)
- <span data-ttu-id="11d0d-147">[Indexers](./index.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="11d0d-147">[Indexers](./index.md)</span></span>
- [<span data-ttu-id="11d0d-148">Właściwości</span><span class="sxs-lookup"><span data-stu-id="11d0d-148">Properties</span></span>](../classes-and-structs/properties.md)
