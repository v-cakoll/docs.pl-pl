---
title: Operacje projekcjiC#()
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: a2a2ae762d63d5ff26c7018caef1a83558042fb5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346528"
---
# <a name="projection-operations-c"></a><span data-ttu-id="c3924-102">Operacje projekcjiC#()</span><span class="sxs-lookup"><span data-stu-id="c3924-102">Projection Operations (C#)</span></span>
<span data-ttu-id="c3924-103">Projekcja odnosi się do operacji przekształcenia obiektu w nowy formularz, który często składa się tylko z tych właściwości, które zostaną następnie użyte.</span><span class="sxs-lookup"><span data-stu-id="c3924-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="c3924-104">Korzystając z projekcji, można utworzyć nowy typ, który jest zbudowany z każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c3924-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="c3924-105">Można projektować Właściwość i wykonywać na niej funkcję matematyczną.</span><span class="sxs-lookup"><span data-stu-id="c3924-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="c3924-106">Możesz również projektować oryginalny obiekt bez zmieniania go.</span><span class="sxs-lookup"><span data-stu-id="c3924-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="c3924-107">W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują projekcję.</span><span class="sxs-lookup"><span data-stu-id="c3924-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3924-108">Metody</span><span class="sxs-lookup"><span data-stu-id="c3924-108">Methods</span></span>  
  
|<span data-ttu-id="c3924-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="c3924-109">Method Name</span></span>|<span data-ttu-id="c3924-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c3924-110">Description</span></span>|<span data-ttu-id="c3924-111">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="c3924-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="c3924-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="c3924-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="c3924-113">Wybierz</span><span class="sxs-lookup"><span data-stu-id="c3924-113">Select</span></span>|<span data-ttu-id="c3924-114">Project wartości, które są oparte na funkcji transformacji.</span><span class="sxs-lookup"><span data-stu-id="c3924-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c3924-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="c3924-115">SelectMany</span></span>|<span data-ttu-id="c3924-116">Projektuje sekwencje wartości, które są oparte na funkcji transformacji, a następnie spłaszcza je w jedną sekwencję.</span><span class="sxs-lookup"><span data-stu-id="c3924-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="c3924-117">Użyj wielu klauzul `from`</span><span class="sxs-lookup"><span data-stu-id="c3924-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="c3924-118">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="c3924-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="c3924-119">Wybierz</span><span class="sxs-lookup"><span data-stu-id="c3924-119">Select</span></span>  
 <span data-ttu-id="c3924-120">W poniższym przykładzie zastosowano klauzulę `select`, aby zaprojektować pierwszą literę z każdego ciągu na liście ciągów.</span><span class="sxs-lookup"><span data-stu-id="c3924-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="c3924-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="c3924-121">SelectMany</span></span>  
 <span data-ttu-id="c3924-122">W poniższym przykładzie zastosowano wiele klauzul `from`, aby zaprojektować każdy wyraz z każdego ciągu na liście ciągów.</span><span class="sxs-lookup"><span data-stu-id="c3924-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="c3924-123">Wybierz i SelectMany</span><span class="sxs-lookup"><span data-stu-id="c3924-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="c3924-124">Prace obu `Select()` i `SelectMany()` to generowanie wartości wyniku (lub wartości) z wartości źródłowych.</span><span class="sxs-lookup"><span data-stu-id="c3924-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="c3924-125">`Select()` tworzy jedną wartość wynikową dla każdej wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="c3924-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="c3924-126">Ogólny wynik to kolekcja, która ma taką samą liczbę elementów jak kolekcja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="c3924-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="c3924-127">Natomiast `SelectMany()` generuje pojedynczy wynik ogólny, który zawiera połączone podkolekcje z każdej wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="c3924-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="c3924-128">Funkcja transformacji, która jest przenoszona jako argument do `SelectMany()` musi zwracać wyliczalną sekwencję wartości dla każdej wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="c3924-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="c3924-129">Te wyliczalne sekwencje są następnie łączone przez `SelectMany()`, aby utworzyć jedną dużą sekwencję.</span><span class="sxs-lookup"><span data-stu-id="c3924-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="c3924-130">Poniższe dwa ilustracje pokazują różnicę koncepcyjną między działaniami tych dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="c3924-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="c3924-131">W każdym przypadku Załóżmy, że funkcja selektor (Transform) wybiera tablicę kwiatów z każdej wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="c3924-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="c3924-132">Na tej ilustracji przedstawiono sposób, w jaki `Select()` zwraca kolekcję, która ma taką samą liczbę elementów jak kolekcja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="c3924-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Ilustracja przedstawiająca akcję wyboru&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="c3924-134">Ta ilustracja przedstawia sposób, w jaki `SelectMany()` łączy pośrednią sekwencję tablic w jedną końcową wartość wynikową, która zawiera każdą wartość z każdej tablicy pośredniej.</span><span class="sxs-lookup"><span data-stu-id="c3924-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![Ilustracja przedstawiająca akcję SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="c3924-136">Przykład kodu</span><span class="sxs-lookup"><span data-stu-id="c3924-136">Code Example</span></span>  
 <span data-ttu-id="c3924-137">Poniższy przykład porównuje zachowanie `Select()` i `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="c3924-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="c3924-138">Kod tworzy "bukiet" kwiatów, pobierając pierwsze dwa elementy z każdej listy nazw kwiatów w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="c3924-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="c3924-139">W tym przykładzie "pojedyncza wartość", którą funkcja transformacji <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> używa, jest sama kolekcją wartości.</span><span class="sxs-lookup"><span data-stu-id="c3924-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="c3924-140">Wymaga to dodatkowej pętli `foreach`, aby wyliczyć każdy ciąg w każdej sekwencji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="c3924-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3924-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3924-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c3924-142">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="c3924-142">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="c3924-143">select, klauzula</span><span class="sxs-lookup"><span data-stu-id="c3924-143">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="c3924-144">Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c3924-144">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="c3924-145">Jak podzielić plik na wiele plików przy użyciu grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c3924-145">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
