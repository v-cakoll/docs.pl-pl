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
# <a name="projection-operations-c"></a>Operacje rzutowania (C#)
Projekcja odnosi się do operacji przekształcania obiektu w nowy formularz, który często składa się tylko z tych właściwości, które zostaną następnie użyte. Korzystając z funkcji projekcji, możesz utworzyć nowy typ, który jest zbudowany z każdego obiektu. Można właściwość projektu i wykonywać w niej funkcji matematycznych. Można również projektu oryginalnego obiektu, nie zmieniając go.  
  
 Metody standardowego operatora zapytań, które wykonują rzutowania są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń zapytania języka C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Wybierz|Wartości projektów, które są oparte na funkcji przekształcenia.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|Projekty sekwencje wartości, które są oparte na funkcji przekształcenia i spłaszcza je do jednej sekwencji.|Używanych jest wiele `from` klauzule|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
  
### <a name="select"></a>Wybierz  
 W poniższym przykładzie użyto `select` klauzuli do projektu pierwszą literę każdego ciągu w postaci listy ciągów.  
  
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
  
### <a name="selectmany"></a>SelectMany  
 W poniższym przykładzie użyto wielu `from` klauzul do projektu każdy wyraz z każdego ciągu w postaci listy ciągów.  
  
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
  
## <a name="select-versus-selectmany"></a>Wybierz i SelectMany  
 Pracę obu `Select()` i `SelectMany()` jest do tworzenia wartości wyniku (lub wartości) z wartości źródłowe. `Select()` Tworzy jednej wartości wyniku dla każdej wartości źródła. Ogólny wynik jest w związku z tym kolekcji, który ma taką samą liczbę elementów jako kolekcja źródłowa. Z kolei `SelectMany()` tworzy jeden wynik ogólny, który zawiera połączonych podkolekcji od każdej wartości źródła. Funkcja transformacji, który jest przekazywany jako argument do `SelectMany()` musi zwracać wyliczalny sekwencję wartości dla każdej wartości źródła. Te sekwencje wyliczalny są następnie łączone przez `SelectMany()` do utworzenia jednej sekwencji dużych.  
  
 Na poniższych ilustracjach dwóch przedstawiono koncepcyjny różnica między akcje te dwie metody. W każdym przypadku założono, że funkcja selektor (przekształcenia) wybiera tablicy kwiatów od każdej wartości źródła.  
  
 Ta ilustracja przedstawia sposób `Select()` zwraca kolekcję, która ma taką samą liczbę elementów jako kolekcja źródłowa.  
  
 ![Ilustracja akcji wybierz&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Ta ilustracja przedstawia sposób `SelectMany()` łączy pośrednich sekwencję tablic w jedną wartość na wynik końcowy zawierający wartość każdej z każdej macierzy pośrednich.  
  
 ![Grafika przedstawiająca akcji SelectMany&#40;&#41;. ](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### <a name="code-example"></a>Przykład kodu  
 W poniższym przykładzie porównano zachowanie `Select()` i `SelectMany()`. Ten kod tworzy "bouquet" kwiatów, pobierając dwóch pierwszych elementów z każdego listę nazw Kwiatek w kolekcji źródłowej. W tym przykładzie "pojedyncza wartość", funkcja transformacji <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> używa jest kolekcją wartości. Ta migracja wymaga nadmiarowe `foreach` pętli, aby można było wyliczyć każdego ciągu w każdej podrzędnej sekwencji.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [select, klauzula](../../../../csharp/language-reference/keywords/select-clause.md)
- [Instrukcje: Wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Instrukcje: Dzielenie pliku na kilka plików za pomocą grup (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
