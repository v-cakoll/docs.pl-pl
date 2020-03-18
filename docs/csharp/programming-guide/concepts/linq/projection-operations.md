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
# <a name="projection-operations-c"></a>Operacje projekcji (C#)
Rzutowanie odnosi się do operacji przekształcania obiektu w nowy formularz, który często składa się tylko z tych właściwości, które będą następnie używane. Za pomocą projekcji, można skonstruować nowy typ, który jest zbudowany z każdego obiektu. Można rzutować właściwość i wykonać na niej funkcję matematyczną. Można również rzutować oryginalny obiekt bez jego zmiany.  
  
 Standardowe metody operatora kwerendy, które wykonują projekcję są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Wybierz pozycję|Projekty wartości, które są oparte na funkcji transformacji.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|Selectmany|Projekty sekwencje wartości, które są oparte na funkcji transformacji, a następnie spłaszcza je w jedną sekwencję.|Używanie `from` wielu klauzul|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażenia kwerendy  
  
### <a name="select"></a>Wybierz pozycję  
 W poniższym `select` przykładzie użyto klauzuli do rzutu pierwszej litery z każdego ciągu na liście ciągów.  
  
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
  
### <a name="selectmany"></a>Selectmany  
 W poniższym `from` przykładzie użyto wielu klauzul do rzutowania każdego wyrazu z każdego ciągu na liście ciągów.  
  
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
  
## <a name="select-versus-selectmany"></a>Wybierz w porównaniu z SelectMany  
 Praca obu `Select()` i `SelectMany()` jest do produkcji wartości wynikowej (lub wartości) z wartości źródłowych. `Select()`generuje jedną wartość wyniku dla każdej wartości źródłowego. Ogólny wynik jest zatem kolekcja, która ma taką samą liczbę elementów jak kolekcja źródłowa. Z drugiej `SelectMany()` strony daje pojedynczy wynik ogólny, który zawiera połączone kolekcje podrzędne z każdej wartości źródłowej. Funkcja transformacji, która jest przekazywana jako argument, musi zwracać `SelectMany()` wyliczalną sekwencję wartości dla każdej wartości źródłowej. Te wyliczalne sekwencje są następnie `SelectMany()` łączone przez utworzenie jednej dużej sekwencji.  
  
 Na poniższych dwóch ilustracjach przedstawiono różnicę koncepcyjną między akcjami tych dwóch metod. W każdym przypadku załóżmy, że funkcja selektora (transformacji) wybiera tablicę kwiatów z każdej wartości źródłowej.  
  
 Ta ilustracja `Select()` przedstawia, jak zwraca kolekcji, która ma taką samą liczbę elementów jak kolekcji źródłowej.  
  
 ![Grafika przedstawiająca akcję Wybierz&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 Ta ilustracja `SelectMany()` przedstawia, jak łączy pośrednią sekwencję tablic w jedną wartość wyniku końcowego, która zawiera każdą wartość z każdej tablicy pośredniej.  
  
 ![Grafika przedstawiająca akcję SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a>Przykład kodu  
 W poniższym przykładzie porównano zachowanie `Select()` i `SelectMany()`. Kod tworzy "bukiet" kwiatów, biorąc pierwsze dwa elementy z każdej listy nazw kwiatów w kolekcji źródłowej. W tym przykładzie "pojedyncza wartość", <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> która używa funkcji przekształcania jest sama kolekcja wartości. Wymaga to `foreach` dodatkowej pętli, aby wyliczyć każdy ciąg w każdej podsekwencji.  
  
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

- <xref:System.Linq>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [klauzula wyboru](../../../language-reference/keywords/select-clause.md)
- [Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [Jak podzielić plik na wiele plików przy użyciu grup (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
