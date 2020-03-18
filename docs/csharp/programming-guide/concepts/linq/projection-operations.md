---
title: Operacje projekcji (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: f76eeeb779ab08a575e758a9d974573b700ae652
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168339"
---
# <a name="projection-operations-c"></a><span data-ttu-id="5cff2-102">Operacje projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="5cff2-102">Projection Operations (C#)</span></span>
<span data-ttu-id="5cff2-103">Rzutowanie odnosi się do operacji przekształcania obiektu w nowy formularz, który często składa się tylko z tych właściwości, które będą następnie używane.</span><span class="sxs-lookup"><span data-stu-id="5cff2-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="5cff2-104">Za pomocą projekcji, można skonstruować nowy typ, który jest zbudowany z każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5cff2-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="5cff2-105">Można rzutować właściwość i wykonać na niej funkcję matematyczną.</span><span class="sxs-lookup"><span data-stu-id="5cff2-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="5cff2-106">Można również rzutować oryginalny obiekt bez jego zmiany.</span><span class="sxs-lookup"><span data-stu-id="5cff2-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="5cff2-107">Standardowe metody operatora kwerendy, które wykonują projekcję są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="5cff2-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5cff2-108">Metody</span><span class="sxs-lookup"><span data-stu-id="5cff2-108">Methods</span></span>  
  
|<span data-ttu-id="5cff2-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="5cff2-109">Method Name</span></span>|<span data-ttu-id="5cff2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5cff2-110">Description</span></span>|<span data-ttu-id="5cff2-111">Składnia wyrażenia kwerendy c#</span><span class="sxs-lookup"><span data-stu-id="5cff2-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="5cff2-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="5cff2-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="5cff2-113">Wybierz pozycję</span><span class="sxs-lookup"><span data-stu-id="5cff2-113">Select</span></span>|<span data-ttu-id="5cff2-114">Projekty wartości, które są oparte na funkcji transformacji.</span><span class="sxs-lookup"><span data-stu-id="5cff2-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5cff2-115">Selectmany</span><span class="sxs-lookup"><span data-stu-id="5cff2-115">SelectMany</span></span>|<span data-ttu-id="5cff2-116">Projekty sekwencje wartości, które są oparte na funkcji transformacji, a następnie spłaszcza je w jedną sekwencję.</span><span class="sxs-lookup"><span data-stu-id="5cff2-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="5cff2-117">Używanie `from` wielu klauzul</span><span class="sxs-lookup"><span data-stu-id="5cff2-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="5cff2-118">Przykłady składni wyrażenia kwerendy</span><span class="sxs-lookup"><span data-stu-id="5cff2-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="5cff2-119">Wybierz pozycję</span><span class="sxs-lookup"><span data-stu-id="5cff2-119">Select</span></span>  
 <span data-ttu-id="5cff2-120">W poniższym `select` przykładzie użyto klauzuli do rzutu pierwszej litery z każdego ciągu na liście ciągów.</span><span class="sxs-lookup"><span data-stu-id="5cff2-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a><span data-ttu-id="5cff2-121">Selectmany</span><span class="sxs-lookup"><span data-stu-id="5cff2-121">SelectMany</span></span>  
 <span data-ttu-id="5cff2-122">W poniższym `from` przykładzie użyto wielu klauzul do rzutowania każdego wyrazu z każdego ciągu na liście ciągów.</span><span class="sxs-lookup"><span data-stu-id="5cff2-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="5cff2-123">Wybierz w porównaniu z SelectMany</span><span class="sxs-lookup"><span data-stu-id="5cff2-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="5cff2-124">Praca obu `Select()` i `SelectMany()` jest do produkcji wartości wynikowej (lub wartości) z wartości źródłowych.</span><span class="sxs-lookup"><span data-stu-id="5cff2-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="5cff2-125">`Select()`generuje jedną wartość wyniku dla każdej wartości źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5cff2-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="5cff2-126">Ogólny wynik jest zatem kolekcja, która ma taką samą liczbę elementów jak kolekcja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="5cff2-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="5cff2-127">Z drugiej `SelectMany()` strony daje pojedynczy wynik ogólny, który zawiera połączone kolekcje podrzędne z każdej wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="5cff2-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="5cff2-128">Funkcja transformacji, która jest przekazywana jako argument, musi zwracać `SelectMany()` wyliczalną sekwencję wartości dla każdej wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="5cff2-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="5cff2-129">Te wyliczalne sekwencje są następnie `SelectMany()` łączone przez utworzenie jednej dużej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5cff2-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="5cff2-130">Na poniższych dwóch ilustracjach przedstawiono różnicę koncepcyjną między akcjami tych dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="5cff2-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="5cff2-131">W każdym przypadku załóżmy, że funkcja selektora (transformacji) wybiera tablicę kwiatów z każdej wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="5cff2-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="5cff2-132">Ta ilustracja `Select()` przedstawia, jak zwraca kolekcji, która ma taką samą liczbę elementów jak kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="5cff2-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Grafika przedstawiająca akcję Wybierz&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="5cff2-134">Ta ilustracja `SelectMany()` przedstawia, jak łączy pośrednią sekwencję tablic w jedną wartość wyniku końcowego, która zawiera każdą wartość z każdej tablicy pośredniej.</span><span class="sxs-lookup"><span data-stu-id="5cff2-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![Grafika przedstawiająca akcję SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="5cff2-136">Przykład kodu</span><span class="sxs-lookup"><span data-stu-id="5cff2-136">Code Example</span></span>  
 <span data-ttu-id="5cff2-137">W poniższym przykładzie porównano zachowanie `Select()` i `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="5cff2-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="5cff2-138">Kod tworzy "bukiet" kwiatów, biorąc pierwsze dwa elementy z każdej listy nazw kwiatów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="5cff2-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="5cff2-139">W tym przykładzie "pojedyncza wartość", <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> która używa funkcji przekształcania jest sama kolekcja wartości.</span><span class="sxs-lookup"><span data-stu-id="5cff2-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="5cff2-140">Wymaga to `foreach` dodatkowej pętli, aby wyliczyć każdy ciąg w każdej podsekwencji.</span><span class="sxs-lookup"><span data-stu-id="5cff2-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cff2-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cff2-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5cff2-142">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="5cff2-142">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="5cff2-143">klauzula wyboru</span><span class="sxs-lookup"><span data-stu-id="5cff2-143">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="5cff2-144">Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5cff2-144">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="5cff2-145">Jak podzielić plik na wiele plików przy użyciu grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5cff2-145">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
