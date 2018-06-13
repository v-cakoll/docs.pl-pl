---
title: Operacje rzutowania (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: f4d1f7531ee69ebdbfb4ccd283f9f5dcb2f000af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647647"
---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="0f91e-102">Operacje rzutowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f91e-102">Projection Operations (Visual Basic)</span></span>
<span data-ttu-id="0f91e-103">Projekcja odwołuje się do operacji przekształcania obiektu na nowy formularz, który często składa się tylko z tych właściwości, które zostaną następnie użyte.</span><span class="sxs-lookup"><span data-stu-id="0f91e-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="0f91e-104">Przy użyciu projekcji, można utworzyć nowy typ, który składa się z każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="0f91e-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="0f91e-105">Możesz właściwości projektu i funkcji matematycznych w nim.</span><span class="sxs-lookup"><span data-stu-id="0f91e-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="0f91e-106">Można także wyświetlać oryginalny obiekt, bez jego zmiany.</span><span class="sxs-lookup"><span data-stu-id="0f91e-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="0f91e-107">Metody — operator zapytań standardowe, wykonujących projekcji są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="0f91e-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f91e-108">Metody</span><span class="sxs-lookup"><span data-stu-id="0f91e-108">Methods</span></span>  
  
|<span data-ttu-id="0f91e-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="0f91e-109">Method Name</span></span>|<span data-ttu-id="0f91e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0f91e-110">Description</span></span>|<span data-ttu-id="0f91e-111">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f91e-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="0f91e-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="0f91e-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="0f91e-113">Wybierz</span><span class="sxs-lookup"><span data-stu-id="0f91e-113">Select</span></span>|<span data-ttu-id="0f91e-114">Wartości projektów, które są oparte na funkcji przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="0f91e-114">Projects values that are based on a transform function.</span></span>|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f91e-115">Operacja SelectMany</span><span class="sxs-lookup"><span data-stu-id="0f91e-115">SelectMany</span></span>|<span data-ttu-id="0f91e-116">Projekty sekwencji wartości, które są oparte na funkcji przekształcenia i spłaszcza je w jedną sekwencję.</span><span class="sxs-lookup"><span data-stu-id="0f91e-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="0f91e-117">Używanych jest wiele `From` klauzule</span><span class="sxs-lookup"><span data-stu-id="0f91e-117">Use multiple `From` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="0f91e-118">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="0f91e-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="0f91e-119">Wybierz</span><span class="sxs-lookup"><span data-stu-id="0f91e-119">Select</span></span>  
 <span data-ttu-id="0f91e-120">W poniższym przykładzie użyto `Select` klauzuli do projektu pierwszą literę każdego ciągu na liście ciągów.</span><span class="sxs-lookup"><span data-stu-id="0f91e-120">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a><span data-ttu-id="0f91e-121">Operacja SelectMany</span><span class="sxs-lookup"><span data-stu-id="0f91e-121">SelectMany</span></span>  
 <span data-ttu-id="0f91e-122">W poniższym przykładzie użyto wielu `From` klauzule projektu każdego wyrazu z każdym ciągu na liście ciągów.</span><span class="sxs-lookup"><span data-stu-id="0f91e-122">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="0f91e-123">Wybierz, a operacja SelectMany</span><span class="sxs-lookup"><span data-stu-id="0f91e-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="0f91e-124">Praca obu `Select()` i `SelectMany()` ma wartość wyniku (lub wartości) z wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="0f91e-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="0f91e-125">`Select()` tworzy jedną wartość wyniku dla każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="0f91e-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="0f91e-126">Wynik ogólny w związku z tym jest kolekcja, która ma taką samą liczbę elementów jako kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="0f91e-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="0f91e-127">Z kolei `SelectMany()` tworzy jeden wynik ogólny zawierający połączonych podkolekcji od każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="0f91e-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="0f91e-128">Przekazywany jako argument do funkcji przekształcenia `SelectMany()` musi zwracać wyliczalny sekwencji wartości dla każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="0f91e-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="0f91e-129">Te wyliczalny sekwencje są następnie połączonych przez `SelectMany()` można utworzyć jedną dużą sekwencji.</span><span class="sxs-lookup"><span data-stu-id="0f91e-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="0f91e-130">Na poniższych ilustracjach dwóch przedstawiono koncepcyjnej różnica między działaniami te dwie metody.</span><span class="sxs-lookup"><span data-stu-id="0f91e-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="0f91e-131">W każdym przypadku założono, że funkcja selektora (transform) wybiera tablicy kwiatów z każdej wartości źródła.</span><span class="sxs-lookup"><span data-stu-id="0f91e-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="0f91e-132">Ta ilustracja przedstawia sposób `Select()` zwraca kolekcję, która ma taką samą liczbę elementów jako kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="0f91e-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="0f91e-133">![Ilustracja akcji wybierz&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="0f91e-133">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="0f91e-134">Ta ilustracja przedstawia sposób `SelectMany()` łączy pośredniego sekwencji tablic w jedną wartość wynik końcowy zawierający wartość każdej z poszczególnych pośrednia tablicy.</span><span class="sxs-lookup"><span data-stu-id="0f91e-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="0f91e-135">![Grafika przedstawiająca akcji operacja SelectMany&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "Operacja SelectMany")</span><span class="sxs-lookup"><span data-stu-id="0f91e-135">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="0f91e-136">Przykład kodu</span><span class="sxs-lookup"><span data-stu-id="0f91e-136">Code Example</span></span>  
 <span data-ttu-id="0f91e-137">Poniższy przykład porównuje zachowanie `Select()` i `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="0f91e-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="0f91e-138">Kod tworzy "bouquet" kwiatów, wykonując dwóch pierwszych elementów z każdej listy nazw kwiat w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="0f91e-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="0f91e-139">W tym przykładzie "pojedyncza wartość" który funkcji przekształcenia <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> używa jest kolekcją wartości.</span><span class="sxs-lookup"><span data-stu-id="0f91e-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="0f91e-140">Wymaga to nadmiarowe `For Each` pętli, aby można było wyliczyć każdy ciąg w każdej podrzędnej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="0f91e-140">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f91e-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f91e-141">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="0f91e-142">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f91e-142">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="0f91e-143">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="0f91e-143">Select Clause</span></span>](../../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="0f91e-144">Porady: łączenie danych za pomocą sprzężeń</span><span class="sxs-lookup"><span data-stu-id="0f91e-144">How to: Combine Data with Joins</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)  
 [<span data-ttu-id="0f91e-145">Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f91e-145">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [<span data-ttu-id="0f91e-146">Instrukcje: zwracanie wyniku zapytania LINQ jako określonego typu</span><span class="sxs-lookup"><span data-stu-id="0f91e-146">How to: Return a LINQ Query Result as a Specific Type</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)  
 [<span data-ttu-id="0f91e-147">Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f91e-147">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
