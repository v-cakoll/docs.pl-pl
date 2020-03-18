---
title: Korzystanie z indeksatorów — przewodnik programowania C#
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628166"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="8b3da-102">Korzystanie z indeksatorów (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="8b3da-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="8b3da-103">Indeksatory to wygoda składni, która umożliwia tworzenie [klasy,](../../language-reference/keywords/class.md) [struktury](../../language-reference/builtin-types/struct.md)lub [interfejsu,](../../language-reference/keywords/interface.md) do którego aplikacje klienckie mają dostęp tak samo jak tablica.</span><span class="sxs-lookup"><span data-stu-id="8b3da-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access just as an array.</span></span> <span data-ttu-id="8b3da-104">Indeksatory są najczęściej implementowane w typach, których głównym celem jest hermetyzowanie wewnętrznej kolekcji lub tablicy.</span><span class="sxs-lookup"><span data-stu-id="8b3da-104">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="8b3da-105">Załóżmy na przykład, `TempRecord` że masz klasę, która reprezentuje temperaturę w Fahrenheita zarejestrowaną w 10 różnych momentach w okresie 24 godzin.</span><span class="sxs-lookup"><span data-stu-id="8b3da-105">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24 hour period.</span></span> <span data-ttu-id="8b3da-106">Klasa zawiera tablicę `temps` `float[]` typu do przechowywania wartości temperatury.</span><span class="sxs-lookup"><span data-stu-id="8b3da-106">The class contains an array `temps` of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="8b3da-107">Implementując indeksator w tej klasie, klienci `TempRecord` mogą `float temp = tr[4]` uzyskać dostęp `float temp = tr.temps[4]`do temperatury w wystąpieniu, jak zamiast jako .</span><span class="sxs-lookup"><span data-stu-id="8b3da-107">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tr[4]` instead of as `float temp = tr.temps[4]`.</span></span> <span data-ttu-id="8b3da-108">Notacja indeksatora nie tylko upraszcza składnię aplikacji klienckich; to również sprawia, że klasa i jej cel bardziej intuicyjne dla innych programistów, aby zrozumieć.</span><span class="sxs-lookup"><span data-stu-id="8b3da-108">The indexer notation not only simplifies the syntax for client applications; it also makes the class and its purpose more intuitive for other developers to understand.</span></span>  
  
<span data-ttu-id="8b3da-109">Aby zadeklarować indeksatora w klasie lub strukturze, użyj [tego](../../language-reference/keywords/this.md) słowa kluczowego, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8b3da-109">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a><span data-ttu-id="8b3da-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b3da-110">Remarks</span></span>

<span data-ttu-id="8b3da-111">Typ indeksatora i typ jego parametrów musi być co najmniej tak samo dostępne jak indeksator sam.</span><span class="sxs-lookup"><span data-stu-id="8b3da-111">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="8b3da-112">Aby uzyskać więcej informacji na temat poziomów ułatwień dostępu, zobacz [Modyfikatory programu Access](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="8b3da-112">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="8b3da-113">Aby uzyskać więcej informacji na temat używania indeksatorów z interfejsem, zobacz [Indeksatory interfejsu](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="8b3da-113">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>  
  
 <span data-ttu-id="8b3da-114">Podpis indeksatora składa się z liczby i typów jego parametrów formalnych.</span><span class="sxs-lookup"><span data-stu-id="8b3da-114">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="8b3da-115">Nie zawiera typu indeksatora lub nazwy parametrów formalnych.</span><span class="sxs-lookup"><span data-stu-id="8b3da-115">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="8b3da-116">Jeśli deklarujesz więcej niż jeden indeksator w tej samej klasie, muszą mieć różne podpisy.</span><span class="sxs-lookup"><span data-stu-id="8b3da-116">If you declare more than one indexer in the same class, they must have different signatures.</span></span>  
  
 <span data-ttu-id="8b3da-117">Wartość indeksatora nie jest klasyfikowana jako zmienna; w związku z tym nie można przekazać wartość indeksatora jako [ref](../../language-reference/keywords/ref.md) lub [out](../../language-reference/keywords/out-parameter-modifier.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="8b3da-117">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>  
  
 <span data-ttu-id="8b3da-118">Aby zapewnić indeksatorowi nazwę, z którego <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>mogą używać inne języki, użyj , jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8b3da-118">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

<span data-ttu-id="8b3da-119">Ten indeksator będzie `TheItem`miał nazwę .</span><span class="sxs-lookup"><span data-stu-id="8b3da-119">This indexer will have the name `TheItem`.</span></span> <span data-ttu-id="8b3da-120">Niepodanie atrybutu name `Item` spowoduje ustawienie domyślnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8b3da-120">Not providing the name attribute would make `Item` the default name.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="8b3da-121">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="8b3da-121">Example 1</span></span>  
  
<span data-ttu-id="8b3da-122">W poniższym przykładzie pokazano, `temps`jak zadeklarować pole tablicy prywatnej i indeksatora.</span><span class="sxs-lookup"><span data-stu-id="8b3da-122">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="8b3da-123">Indeksator umożliwia bezpośredni dostęp `tempRecord[i]`do wystąpienia .</span><span class="sxs-lookup"><span data-stu-id="8b3da-123">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="8b3da-124">Alternatywą dla indeksatora jest zadeklarowanie [public](../../language-reference/keywords/public.md) tablicy jako publicznego `tempRecord.temps[i]`elementu członkowskiego i dostęp do jej członków, bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8b3da-124">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>  
  
 <span data-ttu-id="8b3da-125">Należy zauważyć, że gdy dostęp indeksatora jest `Console.Write` oceniana, na przykład w instrukcji, [get](../../language-reference/keywords/get.md) akcesor jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="8b3da-125">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="8b3da-126">W związku `get` z tym jeśli nie ma akcesor istnieje, występuje błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b3da-126">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a><span data-ttu-id="8b3da-127">Indeksowanie przy użyciu innych wartości</span><span class="sxs-lookup"><span data-stu-id="8b3da-127">Indexing using other values</span></span>

<span data-ttu-id="8b3da-128">C# nie ogranicza typ parametru indeksatora do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="8b3da-128">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="8b3da-129">Na przykład może być przydatne użycie ciągu z indeksatorem.</span><span class="sxs-lookup"><span data-stu-id="8b3da-129">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="8b3da-130">Taki indeksator może być implementowany przez wyszukanie ciągu w kolekcji i zwrócenie odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="8b3da-130">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="8b3da-131">Jako akcesory mogą być przeciążone, ciąg i całkowita wersja może współistnieć.</span><span class="sxs-lookup"><span data-stu-id="8b3da-131">As accessors can be overloaded, the string and integer versions can co-exist.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="8b3da-132">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="8b3da-132">Example 2</span></span>  
  
<span data-ttu-id="8b3da-133">W poniższym przykładzie deklaruje klasę, która przechowuje dni tygodnia.</span><span class="sxs-lookup"><span data-stu-id="8b3da-133">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="8b3da-134">Akcesor `get` przyjmuje ciąg, nazwę dnia i zwraca odpowiednią liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="8b3da-134">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="8b3da-135">Na przykład "Niedziela" zwraca 0, "Poniedziałek" zwraca 1 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8b3da-135">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8b3da-136">Solidne programowanie</span><span class="sxs-lookup"><span data-stu-id="8b3da-136">Robust programming</span></span>

 <span data-ttu-id="8b3da-137">Istnieją dwa główne sposoby poprawy bezpieczeństwa i niezawodności indeksatorów:</span><span class="sxs-lookup"><span data-stu-id="8b3da-137">There are two main ways in which the security and reliability of indexers can be improved:</span></span>  
  
- <span data-ttu-id="8b3da-138">Pamiętaj, aby uwzględnić jakiś typ strategii obsługi błędów, aby obsłużyć prawdopodobieństwo przekazywania kodu klienta w nieprawidłowej wartości indeksu.</span><span class="sxs-lookup"><span data-stu-id="8b3da-138">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="8b3da-139">W pierwszym przykładzie wcześniej w tym temacie TempRecord klasa zawiera Length właściwość, która umożliwia kod klienta, aby zweryfikować dane wejściowe przed przekazaniem go do indeksatora.</span><span class="sxs-lookup"><span data-stu-id="8b3da-139">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="8b3da-140">Można również umieścić kod obsługi błędów wewnątrz indeksatora się.</span><span class="sxs-lookup"><span data-stu-id="8b3da-140">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="8b3da-141">Pamiętaj, aby udokumentować dla użytkowników wszelkie wyjątki, które można zgłosić wewnątrz akcesora indeksatora.</span><span class="sxs-lookup"><span data-stu-id="8b3da-141">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>  
  
- <span data-ttu-id="8b3da-142">Ustaw dostępność [get](../../language-reference/keywords/get.md) i [set](../../language-reference/keywords/set.md) akcesorów być tak restrykcyjne, jak jest to uzasadnione.</span><span class="sxs-lookup"><span data-stu-id="8b3da-142">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="8b3da-143">Jest to ważne `set` w szczególności dla akcesora.</span><span class="sxs-lookup"><span data-stu-id="8b3da-143">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="8b3da-144">Aby uzyskać więcej informacji, zobacz [Ograniczanie ułatwień dostępu .](../classes-and-structs/restricting-accessor-accessibility.md)</span><span class="sxs-lookup"><span data-stu-id="8b3da-144">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b3da-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b3da-145">See also</span></span>

- [<span data-ttu-id="8b3da-146">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="8b3da-146">C# Programming Guide</span></span>](../index.md)
- <span data-ttu-id="8b3da-147">[Indexers](./index.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="8b3da-147">[Indexers](./index.md)</span></span>
- [<span data-ttu-id="8b3da-148">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8b3da-148">Properties</span></span>](../classes-and-structs/properties.md)
