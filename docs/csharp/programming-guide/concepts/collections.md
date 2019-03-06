---
title: Kolekcje (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: d5e3aeab2e035ec2b5f97fd41c84ffa7625ba0b4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373442"
---
# <a name="collections-c"></a>Kolekcje (C#)
W przypadku wielu aplikacji, dla których chcesz utworzyć grupy i zarządzać nimi powiązanych obiektów. Istnieją dwa sposoby grupowania obiektów: poprzez tworzenie tablic obiektów oraz poprzez tworzenie kolekcji obiektów.  
  
 Tablice są najbardziej przydatne do tworzenia i pracy ze stałą liczbą jednoznacznie silnych obiektów. Aby uzyskać informacje na temat tablic, zobacz [tablic](../../../csharp/programming-guide/arrays/index.md).  
  
 Kolekcje zapewniają bardziej elastyczny sposób pracy z grupami obiektów. W odróżnieniu od tablic grupa obiektów, którymi pracujesz można zwiększyć lub zmniejszyć dynamicznie, potrzeb zmiany aplikacji. W niektórych kolekcjach można przypisać klawisz do dowolnych obiektów umieszczonych do kolekcji, tak aby pozwala na szybkie pobranie obiektu przy użyciu klucza.  
  
 Kolekcja jest klasą, więc należy zadeklarować wystąpienia klasy, aby można było dodać elementy do tej kolekcji.  
  
 Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólna kolekcja wymusza typ bezpieczeństwa tak, aby żaden typ danych można dodać do niego. Po pobraniu elementu z kolekcji generycznej, nie trzeba określać jego typu danych, ani go konwertować.  
  
> [!NOTE]
>  W przykładach w tym temacie zawierają [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy dla `System.Collections.Generic` i `System.Linq` przestrzeni nazw.  
  
 **W tym temacie**  
  
-   [Za pomocą prostej kolekcji](#BKMK_SimpleCollection)  
  
-   [Rodzaje kolekcji](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic Classes](#BKMK_Generic)  
  
    -   [System.Collections.Concurrent Classes](#BKMK_Concurrent)  
  
    -   [System.Collections Classes](#BKMK_Collections)  
  
-   [Implementowanie kolekcji par klucz/wartość](#BKMK_KeyValuePairs)  
  
-   [Za pomocą LINQ do dostępu do kolekcji](#BKMK_LINQ)  
  
-   [Sortowanie kolekcji](#BKMK_Sorting)  
  
-   [Definiowanie kolekcji niestandardowej](#BKMK_CustomCollection)  
  
-   [Iteratory](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Za pomocą prostej kolekcji  
 W przykładach w tej sekcji użyto ogólnego <xref:System.Collections.Generic.List%601> klasy, która umożliwia pracę z silnie typizowanej listy obiektów.  
  
 Poniższy przykład tworzy listę ciągów i następnie iterację przez ciągi przy użyciu [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji.  
  
```csharp  
// Create a list of strings.  
var salmons = new List<string>();  
salmons.Add("chinook");  
salmons.Add("coho");  
salmons.Add("pink");  
salmons.Add("sockeye");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 Jeśli zawartość kolekcji jest znana z wyprzedzeniem, można użyć *inicjatora kolekcji* do zainicjowania dla kolekcji. Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Poniższy przykład jest taka sama, jak w poprzednim przykładzie, z wyjątkiem inicjatora kolekcji jest używana do dodawania elementów do kolekcji.  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 Możesz użyć [dla](../../../csharp/language-reference/keywords/for.md) instrukcji zamiast `foreach` instrukcję do iterowania po kolekcji. Osiągniesz to uzyskując dostęp do elementów kolekcji przez pozycję indeksu. Indeks elementów zaczyna się od 0 i kończy się liczbą elementów pomniejszoną o 1.  
  
 Poniższy przykład wykonuje iterację przez elementy kolekcji za pomocą `for` zamiast `foreach`.  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
for (var index = 0; index < salmons.Count; index++)  
{  
    Console.Write(salmons[index] + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 Poniższy przykład usuwa element z kolekcji określając obiekt do usunięcia.  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Remove an element from the list by specifying  
// the object.  
salmons.Remove("coho");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook pink sockeye  
```  
  
 Poniższy przykład usuwa elementy z listy ogólnej. Zamiast `foreach` instrukcji [dla](../../../csharp/language-reference/keywords/for.md) używana jest instrukcja, która dokonuje iteracji w kolejności malejącej. Jest to spowodowane <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda powoduje, że elementy po usuniętym elemencie muszą mieć niższą wartość indeksu.  
  
```csharp  
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
// Remove odd numbers.  
for (var index = numbers.Count - 1; index >= 0; index--)  
{  
    if (numbers[index] % 2 == 1)  
    {  
        // Remove the element by specifying  
        // the zero-based index in the list.  
        numbers.RemoveAt(index);  
    }  
}  
  
// Iterate through the list.  
// A lambda expression is placed in the ForEach method  
// of the List(T) object.  
numbers.ForEach(  
    number => Console.Write(number + " "));  
// Output: 0 2 4 6 8  
```  
  
 Aby uzyskać typ elementów w <xref:System.Collections.Generic.List%601>, można również definiować własne klasy. W poniższym przykładzie `Galaxy` klasę, która jest używana przez <xref:System.Collections.Generic.List%601> jest zdefiniowana w kodzie.  
  
```csharp  
private static void IterateThroughList()  
{  
    var theGalaxies = new List<Galaxy>  
        {  
            new Galaxy() { Name="Tadpole", MegaLightYears=400},  
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},  
            new Galaxy() { Name="Milky Way", MegaLightYears=0},  
            new Galaxy() { Name="Andromeda", MegaLightYears=3}  
        };  
  
    foreach (Galaxy theGalaxy in theGalaxies)  
    {  
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);  
    }  
  
    // Output:  
    //  Tadpole  400  
    //  Pinwheel  25  
    //  Milky Way  0  
    //  Andromeda  3  
}  
  
public class Galaxy  
{  
    public string Name { get; set; }  
    public int MegaLightYears { get; set; }  
}  
```  

<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a>Rodzaje kolekcji 
 Wiele typowych kolekcji jest dostarczanych przez program .NET Framework. Każdy typu kolekcji jest przeznaczony do określonego celu.  
  
 W tej sekcji opisano niektóre typowe klasy kolekcji:  
  
-   <xref:System.Collections.Generic> Klasy  
  
-   <xref:System.Collections.Concurrent> Klasy  
  
-   <xref:System.Collections> Klasy  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic Classes  
 Możesz utworzyć ogólną kolekcję używając jednej z klas w <xref:System.Collections.Generic> przestrzeni nazw. Ogólna kolekcja jest przydatna w przypadku, gdy każdy element w kolekcji ma ten sam typ danych. Ogólna kolekcja wymusza silne wpisywanie, zezwalając tylko na żądane dane typu ma zostać dodana.  
  
 W poniższej tabeli wymieniono niektóre z najczęściej używanych klas <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw:  

|Class|Opis| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|Przedstawia kolekcję par klucz wartość, które są zorganizowane na podstawie klucza.|  
|<xref:System.Collections.Generic.List%601>|Reprezentuje listę obiektów, które mogą być udostępniane przez indeks. Udostępnia metody do wyszukiwania, sortowania i modyfikowania list.|  
|<xref:System.Collections.Generic.Queue%601>|Reprezentuje pierwszy na wejściu, pierwszy FIFO kolekcji obiektów.|  
|<xref:System.Collections.Generic.SortedList%602>|Przedstawia kolekcję par klucz wartość, które są sortowane według klucza, w oparciu o związaną <xref:System.Collections.Generic.IComparer%601> implementacji.|  
|<xref:System.Collections.Generic.Stack%601>|Reprezentuje ostatni na wejściu, pierwszy LIFO kolekcji obiektów.|  
  
 Aby uzyskać więcej informacji, zobacz [powszechnie używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md), i <xref:System.Collections.Generic>.  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>System.Collections.Concurrent Classes  
 W .NET Framework 4 lub nowszej, kolekcje w programie <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają efektywne działania wątków do uzyskiwania dostępu do elementów kolekcji z wielu wątków.  
  
 Klasy w <xref:System.Collections.Concurrent> przestrzeni nazw powinny być używane zamiast odpowiednich typów w <xref:System.Collections.Generic?displayProperty=nameWithType> i <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw w każdym przypadku, gdy wiele wątków jednocześnie uzyskują kolekcji. Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../standard/collections/thread-safe/index.md) i <xref:System.Collections.Concurrent>.  
  
 Niektóre klasy uwzględnione w <xref:System.Collections.Concurrent> nazw są <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>System.Collections Classes  
 Klasy w <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw nie przechowują elementów jako specjalnie typowanych obiektów, ale jako obiekty typu `Object`.  
  
 Jeśli to możliwe, należy używać ogólnych kolekcji w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw, zamiast typów odziedziczonych w `System.Collections` przestrzeni nazw.  
  
 W poniższej tabeli wymieniono niektóre z najczęściej używanych klas w `System.Collections` przestrzeni nazw:  
  
|Class|Opis|  
|---|---|  
|<xref:System.Collections.ArrayList>|Reprezentuje tablicę obiektów, których rozmiar jest dynamicznie zwiększany w miarę wymagane.|  
|<xref:System.Collections.Hashtable>|Przedstawia kolekcję par klucz wartość, które są zorganizowane na podstawie kodu skrótu klucza.|  
|<xref:System.Collections.Queue>|Reprezentuje pierwszy na wejściu, pierwszy FIFO kolekcji obiektów.|  
|<xref:System.Collections.Stack>|Reprezentuje ostatni na wejściu, pierwszy LIFO kolekcji obiektów.|  
  
 <xref:System.Collections.Specialized> Przestrzeń nazw zawiera specjalistyczne i silnie typizowanych klas kolekcji, takich jak kolekcje wyłącznie ciągów i listy powiązane i słowniki hybrydowe.  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementowanie kolekcji par klucz/wartość  
 <xref:System.Collections.Generic.Dictionary%602> Kolekcji ogólnej umożliwia dostęp do elementów w kolekcji za pomocą klucza każdego elementu. Każdy dodatkem do słownika składa się z wartości i skojarzonego z nim klucza. Pobieranie wartości przy użyciu własnego klucza jest szybkie ponieważ `Dictionary` klasy jest implementowany jako tabelę mieszania.  
  
 Poniższy przykład tworzy `Dictionary` kolekcji i wykonuje iteracje przez słownik za pomocą `foreach` instrukcji.  
  
```csharp  
private static void IterateThruDictionary()  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    foreach (KeyValuePair<string, Element> kvp in elements)  
    {  
        Element theElement = kvp.Value;  
  
        Console.WriteLine("key: " + kvp.Key);  
        Console.WriteLine("values: " + theElement.Symbol + " " +  
            theElement.Name + " " + theElement.AtomicNumber);  
    }  
}  
  
private static Dictionary<string, Element> BuildDictionary()  
{  
    var elements = new Dictionary<string, Element>();  
  
    AddToDictionary(elements, "K", "Potassium", 19);  
    AddToDictionary(elements, "Ca", "Calcium", 20);  
    AddToDictionary(elements, "Sc", "Scandium", 21);  
    AddToDictionary(elements, "Ti", "Titanium", 22);  
  
    return elements;  
}  
  
private static void AddToDictionary(Dictionary<string, Element> elements,  
    string symbol, string name, int atomicNumber)  
{  
    Element theElement = new Element();  
  
    theElement.Symbol = symbol;  
    theElement.Name = name;  
    theElement.AtomicNumber = atomicNumber;  
  
    elements.Add(key: theElement.Symbol, value: theElement);  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  
  
 Zamiast tego za pomocą inicjatora kolekcji tworzyć `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody przy użyciu następującej metody.  
  
```csharp  
private static Dictionary<string, Element> BuildDictionary2()  
{  
    return new Dictionary<string, Element>  
    {  
        {"K",  
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        {"Ca",  
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        {"Sc",  
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        {"Ti",  
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
```  
  
 W poniższym przykładzie użyto <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> metody i <xref:System.Collections.Generic.Dictionary%602.Item%2A> właściwość `Dictionary` szybko znaleźć element według klucza. `Item` Właściwość pozwala na dostęp do elementu w `elements` kolekcji przy użyciu `elements[symbol]` w języku C#.  
  
```csharp  
private static void FindInDictionary(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    if (elements.ContainsKey(symbol) == false)  
    {  
        Console.WriteLine(symbol + " not found");  
    }  
    else  
    {  
        Element theElement = elements[symbol];  
        Console.WriteLine("found: " + theElement.Name);  
    }  
}  
```  
  
 W poniższym przykładzie zamiast użyto <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda szybko znaleźć element według klucza.  
  
```csharp  
private static void FindInDictionary2(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    Element theElement = null;  
    if (elements.TryGetValue(symbol, out theElement) == false)  
        Console.WriteLine(symbol + " not found");  
    else  
        Console.WriteLine("found: " + theElement.Name);  
}  
```  

<a name="BKMK_LINQ"></a>
## <a name="using-linq-to-access-a-collection"></a>Za pomocą LINQ do dostępu do kolekcji  
 LINQ (Language-Integrated Query) może służyć do dostępu do kolekcji. Zapytania LINQ zapewniają filtrowanie, porządkowanie i możliwości grupowania. Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Poniższy przykład wykonuje zapytanie LINQ na ogólnej `List`. Zapytanie LINQ zwraca inną kolekcję, która zawiera wyniki.  
  
```csharp  
private static void ShowLINQ()  
{  
    List<Element> elements = BuildList();  
  
    // LINQ Query.  
    var subset = from theElement in elements  
                 where theElement.AtomicNumber < 22  
                 orderby theElement.Name  
                 select theElement;  
  
    foreach (Element theElement in subset)  
    {  
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);  
    }  
  
    // Output:  
    //  Calcium 20  
    //  Potassium 19  
    //  Scandium 21  
}  
  
private static List<Element> BuildList()  
{  
    return new List<Element>  
    {  
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  

<a name="BKMK_Sorting"></a>
## <a name="sorting-a-collection"></a>Sortowanie kolekcji  
 Poniżej przedstawiono przykładową procedurę sortowania zbioru. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601>. `Car` Klasy implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda zaimplementowana.  
  
 Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metody tworzy pojedyncze porównanie, który jest używane do sortowania. Kod napisany przez użytkownika w `CompareTo` metoda zwraca wartość dla każdego porównania bieżącego obiektu z innego obiektu. Wartość zwracana jest mniejsza niż zero, jeżeli bieżący obiekt jest mniejszy niż inny obiekt, większa niż zero, jeśli bieżący obiekt jest większy niż inny obiekt i zero czy są równe. Umożliwia to definiowanie w kodzie kryteriów dla większych niż, mniejsze więc równa.  
  
 W `ListCars` metody `cars.Sort()` instrukcji sortuje listy. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, że `CompareTo` metoda zostaje wywołana automatycznie dla `Car` obiekty w `List`.  
  
```csharp  
private static void ListCars()  
{  
    var cars = new List<Car>  
    {  
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},  
        { new Car() { Name = "car2", Color = "red", Speed = 50}},  
        { new Car() { Name = "car3", Color = "green", Speed = 10}},  
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},  
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},  
        { new Car() { Name = "car6", Color = "red", Speed = 60}},  
        { new Car() { Name = "car7", Color = "green", Speed = 50}}  
    };  
  
    // Sort the cars by color alphabetically, and then by speed  
    // in descending order.  
    cars.Sort();  
  
    // View all of the cars.  
    foreach (Car thisCar in cars)  
    {  
        Console.Write(thisCar.Color.PadRight(5) + " ");  
        Console.Write(thisCar.Speed.ToString() + " ");  
        Console.Write(thisCar.Name);  
        Console.WriteLine();  
    }  
  
    // Output:  
    //  blue  50 car4  
    //  blue  30 car5  
    //  blue  20 car1  
    //  green 50 car7  
    //  green 10 car3  
    //  red   60 car6  
    //  red   50 car2  
}  
  
public class Car : IComparable<Car>  
{  
    public string Name { get; set; }  
    public int Speed { get; set; }  
    public string Color { get; set; }  
  
    public int CompareTo(Car other)  
    {  
        // A call to this method makes a single comparison that is  
        // used for sorting.  
  
        // Determine the relative order of the objects being compared.  
        // Sort by color alphabetically, and then by speed in  
        // descending order.  
  
        // Compare the colors.  
        int compare;  
        compare = String.Compare(this.Color, other.Color, true);  
  
        // If the colors are the same, compare the speeds.  
        if (compare == 0)  
        {  
            compare = this.Speed.CompareTo(other.Speed);  
  
            // Use descending order for speed.  
            compare = -compare;  
        }  
  
        return compare;  
    }  
}  
```  
  
<a name="BKMK_CustomCollection"></a>
## <a name="defining-a-custom-collection"></a>Definiowanie kolekcji niestandardowej  
 Można zdefiniować kolekcję implementując <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.IEnumerable> interfejsu.  
  
 Chociaż można zdefiniować kolekcję niestandardową, to zazwyczaj lepiej jest użyć zamiast tego kolekcje, które znajdują się w .NET Framework, które są opisane w [rodzaje kolekcji](#BKMK_KindsOfCollections) we wcześniejszej części tego tematu.  
  
 W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors`. Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda zaimplementowana.  
  
 `GetEnumerator` Metoda zwraca wystąpienie `ColorEnumerator` klasy. `ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, aby <xref:System.Collections.IEnumerator.Current%2A> właściwości <xref:System.Collections.IEnumerator.MoveNext%2A> metody i <xref:System.Collections.IEnumerator.Reset%2A> metoda zaimplementowana.  
  
```csharp  
private static void ListColors()  
{  
    var colors = new AllColors();  
  
    foreach (Color theColor in colors)  
    {  
        Console.Write(theColor.Name + " ");  
    }  
    Console.WriteLine();  
    // Output: red blue green  
}  
  
// Collection class.  
public class AllColors : System.Collections.IEnumerable  
{  
    Color[] _colors =  
    {  
        new Color() { Name = "red" },  
        new Color() { Name = "blue" },  
        new Color() { Name = "green" }  
    };  
  
    public System.Collections.IEnumerator GetEnumerator()  
    {  
        return new ColorEnumerator(_colors);  
  
        // Instead of creating a custom enumerator, you could  
        // use the GetEnumerator of the array.  
        //return _colors.GetEnumerator();  
    }  
  
    // Custom enumerator.  
    private class ColorEnumerator : System.Collections.IEnumerator  
    {  
        private Color[] _colors;  
        private int _position = -1;  
  
        public ColorEnumerator(Color[] colors)  
        {  
            _colors = colors;  
        }  
  
        object System.Collections.IEnumerator.Current  
        {  
            get  
            {  
                return _colors[_position];  
            }  
        }  
  
        bool System.Collections.IEnumerator.MoveNext()  
        {  
            _position++;  
            return (_position < _colors.Length);  
        }  
  
        void System.Collections.IEnumerator.Reset()  
        {  
            _position = -1;  
        }  
    }  
}  
  
// Element class.  
public class Color  
{  
    public string Name { get; set; }  
}  
```  

<a name="BKMK_Iterators"></a> 
## <a name="iterators"></a>Iteratory  
 *Iteratora* służy do wykonywania niestandardowych iteracji przez kolekcję. Iteracją może być metodą lub `get` metody dostępu. Używa iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcja zwraca każdy element kolekcji naraz.  
  
 Wywołujesz iterację używając [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji. Każda iteracja `foreach` pętli wywołuje iteratora. Gdy `yield return` osiągnięciu instrukcji w iteratorze, wyrażenie jest zwracane, a bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji w przy następnym wywołaniu iteratora.  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory (C#)](../../../csharp/programming-guide/concepts/iterators.md).  
  
 Poniższy przykład wykorzystuje metodę iteratora. Metoda iteratora ma `yield return` instrukcji, która znajduje się wewnątrz [dla](../../../csharp/language-reference/keywords/for.md) pętli. W `ListEvenNumbers` metody, każda iteracja `foreach` treść instrukcji tworzy wywołanie metody iteracyjnej, która przechodzi do następnej `yield return` instrukcji.  
  
```csharp  
private static void ListEvenNumbers()  
{  
    foreach (int number in EvenSequence(5, 18))  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    Console.WriteLine();  
    // Output: 6 8 10 12 14 16 18  
}  
  
private static IEnumerable<int> EvenSequence(  
    int firstNumber, int lastNumber)  
{  
    // Yield even numbers in the range.  
    for (var number = firstNumber; number <= lastNumber; number++)  
    {  
        if (number % 2 == 0)  
        {  
            yield return number;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [Koncepcje programowania (C#)](../../../csharp/programming-guide/concepts/index.md)
- [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ to Objects (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [Równoległe LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [Kolekcje i struktury danych](../../../standard/collections/index.md)
- [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)
- [Porównywanie i sortowanie w ramach kolekcji](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Kiedy należy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)
