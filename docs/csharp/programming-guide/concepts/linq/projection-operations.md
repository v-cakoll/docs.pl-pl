---
title: Operacje rzutowania (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: a044982c21246fd4e8c1cbdbb9801ae7b29d05c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="projection-operations-c"></a>Operacje rzutowania (C#)
Projekcja odwołuje się do operacji przekształcania obiektu na nowy formularz, który często składa się tylko z tych właściwości, które zostaną następnie użyte. Przy użyciu projekcji, można utworzyć nowy typ, który składa się z każdego obiektu. Możesz właściwości projektu i funkcji matematycznych w nim. Można także wyświetlać oryginalny obiekt, bez jego zmiany.  
  
 Metody — operator zapytań standardowe, wykonujących projekcji są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Wybierz|Wartości projektów, które są oparte na funkcji przekształcenia.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|Operacja SelectMany|Projekty sekwencji wartości, które są oparte na funkcji przekształcenia i spłaszcza je w jedną sekwencję.|Używanych jest wiele `from` klauzule|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="select"></a>Wybierz  
 W poniższym przykładzie użyto `select` klauzuli do projektu pierwszą literę każdego ciągu na liście ciągów.  
  
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
  
### <a name="selectmany"></a>Operacja SelectMany  
 W poniższym przykładzie użyto wielu `from` klauzule projektu każdego wyrazu z każdym ciągu na liście ciągów.  
  
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
  
## <a name="select-versus-selectmany"></a>Wybierz, a operacja SelectMany  
 Praca obu `Select()` i `SelectMany()` ma wartość wyniku (lub wartości) z wartości źródła. `Select()` tworzy jedną wartość wyniku dla każdej wartości źródła. Wynik ogólny w związku z tym jest kolekcja, która ma taką samą liczbę elementów jako kolekcji źródłowej. Z kolei `SelectMany()` tworzy jeden wynik ogólny zawierający połączonych podkolekcji od każdej wartości źródła. Przekazywany jako argument do funkcji przekształcenia `SelectMany()` musi zwracać wyliczalny sekwencji wartości dla każdej wartości źródła. Te wyliczalny sekwencje są następnie połączonych przez `SelectMany()` można utworzyć jedną dużą sekwencji.  
  
 Na poniższych ilustracjach dwóch przedstawiono koncepcyjnej różnica między działaniami te dwie metody. W każdym przypadku założono, że funkcja selektora (transform) wybiera tablicy kwiatów z każdej wartości źródła.  
  
 Ta ilustracja przedstawia sposób `Select()` zwraca kolekcję, która ma taką samą liczbę elementów jako kolekcji źródłowej.  
  
 ![Ilustracja akcji wybierz&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Ta ilustracja przedstawia sposób `SelectMany()` łączy pośredniego sekwencji tablic w jedną wartość wynik końcowy zawierający wartość każdej z poszczególnych pośrednia tablicy.  
  
 ![Grafika przedstawiająca akcji operacja SelectMany&#40;&#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "Operacja SelectMany")  
  
### <a name="code-example"></a>Przykład kodu  
 Poniższy przykład porównuje zachowanie `Select()` i `SelectMany()`. Kod tworzy "bouquet" kwiatów, wykonując dwóch pierwszych elementów z każdej listy nazw kwiat w kolekcji źródłowej. W tym przykładzie "pojedyncza wartość" który funkcji przekształcenia <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> używa jest kolekcją wartości. Wymaga to nadmiarowe `foreach` pętli, aby można było wyliczyć każdy ciąg w każdej podrzędnej sekwencji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [select, klauzula](../../../../csharp/language-reference/keywords/select-clause.md)  
 [Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
