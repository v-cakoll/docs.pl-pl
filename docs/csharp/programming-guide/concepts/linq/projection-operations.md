---
title: Operacje rzutowania (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: fa9b1d2a0dc63be89e8a93fd5d234f131a2943e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723956"
---
# <a name="projection-operations-c"></a><span data-ttu-id="307e7-102">Operacje rzutowania (C#)</span><span class="sxs-lookup"><span data-stu-id="307e7-102">Projection Operations (C#)</span></span>
<span data-ttu-id="307e7-103">Projekcja odnosi się do operacji przekształcania obiektu w nowy formularz, który często składa się tylko z tych właściwości, które zostaną następnie użyte.</span><span class="sxs-lookup"><span data-stu-id="307e7-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="307e7-104">Korzystając z funkcji projekcji, możesz utworzyć nowy typ, który jest zbudowany z każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="307e7-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="307e7-105">Można właściwość projektu i wykonywać w niej funkcji matematycznych.</span><span class="sxs-lookup"><span data-stu-id="307e7-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="307e7-106">Można również projektu oryginalnego obiektu, nie zmieniając go.</span><span class="sxs-lookup"><span data-stu-id="307e7-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="307e7-107">Metody standardowego operatora zapytań, które wykonują rzutowania są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="307e7-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="307e7-108">Metody</span><span class="sxs-lookup"><span data-stu-id="307e7-108">Methods</span></span>  
  
|<span data-ttu-id="307e7-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="307e7-109">Method Name</span></span>|<span data-ttu-id="307e7-110">Opis</span><span class="sxs-lookup"><span data-stu-id="307e7-110">Description</span></span>|<span data-ttu-id="307e7-111">Składnia wyrażeń zapytania języka C#</span><span class="sxs-lookup"><span data-stu-id="307e7-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="307e7-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="307e7-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="307e7-113">Wybierz</span><span class="sxs-lookup"><span data-stu-id="307e7-113">Select</span></span>|<span data-ttu-id="307e7-114">Wartości projektów, które są oparte na funkcji przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="307e7-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="307e7-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="307e7-115">SelectMany</span></span>|<span data-ttu-id="307e7-116">Projekty sekwencje wartości, które są oparte na funkcji przekształcenia i spłaszcza je do jednej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="307e7-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="307e7-117">Używanych jest wiele `from` klauzule</span><span class="sxs-lookup"><span data-stu-id="307e7-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="307e7-118">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="307e7-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="307e7-119">Wybierz</span><span class="sxs-lookup"><span data-stu-id="307e7-119">Select</span></span>  
 <span data-ttu-id="307e7-120">W poniższym przykładzie użyto `select` klauzuli do projektu pierwszą literę każdego ciągu w postaci listy ciągów.</span><span class="sxs-lookup"><span data-stu-id="307e7-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="307e7-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="307e7-121">SelectMany</span></span>  
 <span data-ttu-id="307e7-122">W poniższym przykładzie użyto wielu `from` klauzul do projektu każdy wyraz z każdego ciągu w postaci listy ciągów.</span><span class="sxs-lookup"><span data-stu-id="307e7-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="307e7-123">Wybierz i SelectMany</span><span class="sxs-lookup"><span data-stu-id="307e7-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="307e7-124">Pracę obu `Select()` i `SelectMany()` jest do tworzenia wartości wyniku (lub wartości) z wartości źródłowe.</span><span class="sxs-lookup"><span data-stu-id="307e7-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="307e7-125">`Select()` Tworzy jednej wartości wyniku dla każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="307e7-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="307e7-126">Ogólny wynik jest w związku z tym kolekcji, który ma taką samą liczbę elementów jako kolekcja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="307e7-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="307e7-127">Z kolei `SelectMany()` tworzy jeden wynik ogólny, który zawiera połączonych podkolekcji od każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="307e7-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="307e7-128">Funkcja transformacji, który jest przekazywany jako argument do `SelectMany()` musi zwracać wyliczalny sekwencję wartości dla każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="307e7-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="307e7-129">Te sekwencje wyliczalny są następnie łączone przez `SelectMany()` do utworzenia jednej sekwencji dużych.</span><span class="sxs-lookup"><span data-stu-id="307e7-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="307e7-130">Na poniższych ilustracjach dwóch przedstawiono koncepcyjny różnica między akcje te dwie metody.</span><span class="sxs-lookup"><span data-stu-id="307e7-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="307e7-131">W każdym przypadku założono, że funkcja selektor (przekształcenia) wybiera tablicy kwiatów od każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="307e7-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="307e7-132">Ta ilustracja przedstawia sposób `Select()` zwraca kolekcję, która ma taką samą liczbę elementów jako kolekcja źródłowa.</span><span class="sxs-lookup"><span data-stu-id="307e7-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="307e7-133">![Ilustracja akcji wybierz&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="307e7-133">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="307e7-134">Ta ilustracja przedstawia sposób `SelectMany()` łączy pośrednich sekwencję tablic w jedną wartość na wynik końcowy zawierający wartość każdej z każdej macierzy pośrednich.</span><span class="sxs-lookup"><span data-stu-id="307e7-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="307e7-135">![Grafika przedstawiająca akcji SelectMany&#40;&#41;. ](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="307e7-135">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="307e7-136">Przykład kodu</span><span class="sxs-lookup"><span data-stu-id="307e7-136">Code Example</span></span>  
 <span data-ttu-id="307e7-137">W poniższym przykładzie porównano zachowanie `Select()` i `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="307e7-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="307e7-138">Ten kod tworzy "bouquet" kwiatów, pobierając dwóch pierwszych elementów z każdego listę nazw Kwiatek w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="307e7-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="307e7-139">W tym przykładzie "pojedyncza wartość", funkcja transformacji <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> używa jest kolekcją wartości.</span><span class="sxs-lookup"><span data-stu-id="307e7-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="307e7-140">Ta migracja wymaga nadmiarowe `foreach` pętli, aby można było wyliczyć każdego ciągu w każdej podrzędnej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="307e7-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="307e7-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="307e7-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="307e7-142">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="307e7-142">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="307e7-143">select, klauzula</span><span class="sxs-lookup"><span data-stu-id="307e7-143">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
- [<span data-ttu-id="307e7-144">Instrukcje: Wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="307e7-144">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="307e7-145">Instrukcje: Dzielenie pliku na kilka plików za pomocą grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="307e7-145">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
