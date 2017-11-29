---
title: Operacje rzutowania (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a05a4f228e64405ba24d967193d9e7a487ae473
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="projection-operations-c"></a><span data-ttu-id="9bda6-102">Operacje rzutowania (C#)</span><span class="sxs-lookup"><span data-stu-id="9bda6-102">Projection Operations (C#)</span></span>
<span data-ttu-id="9bda6-103">Projekcja odwołuje się do operacji przekształcania obiektu na nowy formularz, który często składa się tylko z tych właściwości, które zostaną następnie użyte.</span><span class="sxs-lookup"><span data-stu-id="9bda6-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="9bda6-104">Przy użyciu projekcji, można utworzyć nowy typ, który składa się z każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9bda6-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="9bda6-105">Możesz właściwości projektu i funkcji matematycznych w nim.</span><span class="sxs-lookup"><span data-stu-id="9bda6-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="9bda6-106">Można także wyświetlać oryginalny obiekt, bez jego zmiany.</span><span class="sxs-lookup"><span data-stu-id="9bda6-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="9bda6-107">Metody — operator zapytań standardowe, wykonujących projekcji są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9bda6-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9bda6-108">Metody</span><span class="sxs-lookup"><span data-stu-id="9bda6-108">Methods</span></span>  
  
|<span data-ttu-id="9bda6-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="9bda6-109">Method Name</span></span>|<span data-ttu-id="9bda6-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9bda6-110">Description</span></span>|<span data-ttu-id="9bda6-111">Składnia wyrażenia zapytania C#</span><span class="sxs-lookup"><span data-stu-id="9bda6-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="9bda6-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="9bda6-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="9bda6-113">Wybierz</span><span class="sxs-lookup"><span data-stu-id="9bda6-113">Select</span></span>|<span data-ttu-id="9bda6-114">Wartości projektów, które są oparte na funkcji przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="9bda6-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9bda6-115">Operacja SelectMany</span><span class="sxs-lookup"><span data-stu-id="9bda6-115">SelectMany</span></span>|<span data-ttu-id="9bda6-116">Projekty sekwencji wartości, które są oparte na funkcji przekształcenia i spłaszcza je w jedną sekwencję.</span><span class="sxs-lookup"><span data-stu-id="9bda6-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="9bda6-117">Używanych jest wiele `from` klauzule</span><span class="sxs-lookup"><span data-stu-id="9bda6-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="9bda6-118">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="9bda6-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="9bda6-119">Wybierz</span><span class="sxs-lookup"><span data-stu-id="9bda6-119">Select</span></span>  
 <span data-ttu-id="9bda6-120">W poniższym przykładzie użyto `select` klauzuli do projektu pierwszą literę każdego ciągu na liście ciągów.</span><span class="sxs-lookup"><span data-stu-id="9bda6-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
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
  
### <a name="selectmany"></a><span data-ttu-id="9bda6-121">Operacja SelectMany</span><span class="sxs-lookup"><span data-stu-id="9bda6-121">SelectMany</span></span>  
 <span data-ttu-id="9bda6-122">W poniższym przykładzie użyto wielu `from` klauzule projektu każdego wyrazu z każdym ciągu na liście ciągów.</span><span class="sxs-lookup"><span data-stu-id="9bda6-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
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
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="9bda6-123">Wybierz, a operacja SelectMany</span><span class="sxs-lookup"><span data-stu-id="9bda6-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="9bda6-124">Praca obu `Select()` i `SelectMany()` ma wartość wyniku (lub wartości) z wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="9bda6-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="9bda6-125">`Select()`tworzy jedną wartość wyniku dla każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="9bda6-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="9bda6-126">Wynik ogólny w związku z tym jest kolekcja, która ma taką samą liczbę elementów jako kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="9bda6-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="9bda6-127">Z kolei `SelectMany()` tworzy jeden wynik ogólny zawierający połączonych podkolekcji od każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="9bda6-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="9bda6-128">Przekazywany jako argument do funkcji przekształcenia `SelectMany()` musi zwracać wyliczalny sekwencji wartości dla każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="9bda6-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="9bda6-129">Te wyliczalny sekwencje są następnie połączonych przez `SelectMany()` można utworzyć jedną dużą sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9bda6-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="9bda6-130">Na poniższych ilustracjach dwóch przedstawiono koncepcyjnej różnica między działaniami te dwie metody.</span><span class="sxs-lookup"><span data-stu-id="9bda6-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="9bda6-131">W każdym przypadku założono, że funkcja selektora (transform) wybiera tablicy kwiatów z każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="9bda6-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="9bda6-132">Ta ilustracja przedstawia sposób `Select()` zwraca kolekcję, która ma taką samą liczbę elementów jako kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="9bda6-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="9bda6-133">![Ilustracja akcji wybierz &#40; &#41; ] (../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="9bda6-133">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="9bda6-134">Ta ilustracja przedstawia sposób `SelectMany()` łączy pośredniego sekwencji tablic w jedną wartość wynik końcowy zawierający wartość każdej z poszczególnych pośrednia tablicy.</span><span class="sxs-lookup"><span data-stu-id="9bda6-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="9bda6-135">![Grafika przedstawiająca akcji operacja SelectMany &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "Operacja SelectMany")</span><span class="sxs-lookup"><span data-stu-id="9bda6-135">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="9bda6-136">Przykład kodu</span><span class="sxs-lookup"><span data-stu-id="9bda6-136">Code Example</span></span>  
 <span data-ttu-id="9bda6-137">Poniższy przykład porównuje zachowanie `Select()` i `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="9bda6-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="9bda6-138">Kod tworzy "bouquet" kwiatów, wykonując dwóch pierwszych elementów z każdej listy nazw kwiat w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="9bda6-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="9bda6-139">W tym przykładzie "pojedyncza wartość" który funkcji przekształcenia <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> używa jest kolekcją wartości.</span><span class="sxs-lookup"><span data-stu-id="9bda6-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="9bda6-140">Wymaga to nadmiarowe `foreach` pętli, aby można było wyliczyć każdy ciąg w każdej podrzędnej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9bda6-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9bda6-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bda6-141">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="9bda6-142">Operatory standardowe zapytań — omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="9bda6-142">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="9bda6-143">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="9bda6-143">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)  
 [<span data-ttu-id="9bda6-144">Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9bda6-144">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [<span data-ttu-id="9bda6-145">Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9bda6-145">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
