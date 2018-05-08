---
title: Kolekcje (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 85cbabf74a702a4d6442a29c3cf3d7b726ab38da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="collections-c"></a>Kolekcje (C#)
Dla wielu aplikacji, dla których chcesz Utwórz i Zarządzaj grupami powiązanych obiektów. Istnieją dwa sposoby do obiektów grup: tworzenie tablic obiektów oraz tworzenie kolekcji obiektów.  
  
 Tablice są najbardziej przydatne do tworzenia i Praca z stała liczba silnie typizowanych obiektów. Aby uzyskać informacje dotyczące tablic, zobacz [tablice](../../../csharp/programming-guide/arrays/index.md).  
  
 Kolekcje umożliwiają bardziej elastyczne do pracy z grupy obiektów. W przeciwieństwie do tablic grupy obiektów, którymi współpracujesz można zwiększyć lub zmniejszyć dynamicznie, musi mieć zmiany aplikacji. Niektóre zbiory klucza można przypisać do wszystkich obiektów, które można umieścić w kolekcji, tak, aby szybko można pobrać obiektu przy użyciu klucza.  
  
 Kolekcja jest klasa, więc należy zadeklarować wystąpienia klasy, aby można było dodać elementy do tej kolekcji.  
  
 Jeśli kolekcja zawiera elementy tylko jednego typu danych, możesz użyć jednej z klas w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw. Ogólnej kolekcji wymusza zabezpieczenie typów, dzięki czemu można dodać do niego inny typ danych. Podczas pobierania elementu z kolekcji uniwersalnej, nie trzeba określić jego typu danych albo przekonwertować go.  
  
> [!NOTE]
>  Przykłady w tym temacie, można dołączyć [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy `System.Collections.Generic` i `System.Linq` przestrzeni nazw.  
  
 **W tym temacie**  
  
-   [Przy użyciu prostych kolekcji](#BKMK_SimpleCollection)  
  
-   [Typy kolekcji](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic Classes](#BKMK_Generic)  
  
    -   [Klasy System.Collections.Concurrent](#BKMK_Concurrent)  
  
    -   [System.Collections — klasy](#BKMK_Collections)  
  
-   [Implementowanie kolekcję par klucz/wartość](#BKMK_KeyValuePairs)  
  
-   [Otwieranie kolekcji za pomocą LINQ](#BKMK_LINQ)  
  
-   [Sortowanie kolekcji](#BKMK_Sorting)  
  
-   [Definiowanie kolekcji niestandardowej](#BKMK_CustomCollection)  
  
-   [Iteratory](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Przy użyciu prostych kolekcji  
 Przykłady w tej sekcji używać ogólnych <xref:System.Collections.Generic.List%601> klasy, która umożliwia pracę z silnie typizowaną listę obiektów.  
  
 Poniższy przykład tworzy listę ciągów i następnie iteruje ciągi za pomocą lub [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji.  
  
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
  
 Jeśli zawartość kolekcji są znane z wyprzedzeniem, możesz użyć *inicjatora kolekcji* do zainicjowania dla kolekcji. Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Poniższy przykład jest taki sam, jak poprzedni przykład, z wyjątkiem inicjatora kolekcji służy do dodawania elementów do kolekcji.  
  
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
  
 Można użyć [dla](../../../csharp/language-reference/keywords/for.md) instrukcji zamiast `foreach` instrukcji do iterowania po kolekcji. Można to zrobić, należy podczas uzyskiwania dostępu do elementów kolekcji przez indeks. Indeks elementów rozpoczyna się od 0 i kończy się liczbę element pomniejszonej o 1.  
  
 Poniższy przykład iterację elementów kolekcji za pomocą `for` zamiast `foreach`.  
  
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
  
 Poniższy przykład umożliwia usunięcie elementu z kolekcji, określając obiekt do usunięcia.  
  
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
  
 Poniższy przykład umożliwia usunięcie elementów z listy ogólnej. Zamiast `foreach` instrukcji, [dla](../../../csharp/language-reference/keywords/for.md) używana jest instrukcja, która wykonuje iterację w kolejności malejącej. Jest to spowodowane <xref:System.Collections.Generic.List%601.RemoveAt%2A> metoda powoduje elementów po usunięty element ma niższą wartość indeksu.  
  
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
  
 Dla typu elementów w <xref:System.Collections.Generic.List%601>, możesz również definiować własne klasy. W poniższym przykładzie `Galaxy` klasy, która jest używana przez <xref:System.Collections.Generic.List%601> jest zdefiniowany w kodzie.  
  
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
## <a name="kinds-of-collections"></a>Typy kolekcji 
 Wielu typowych kolekcji są dostarczane przez program .NET Framework. Każdy typ kolekcji jest przeznaczony dla określonego celu.  
  
 W tej sekcji opisano niektóre typowe klasy kolekcji:  
  
-   <xref:System.Collections.Generic> Klasy  
  
-   <xref:System.Collections.Concurrent> Klasy  
  
-   <xref:System.Collections> Klasy  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic Classes  
 Można utworzyć kolekcję ogólną za pomocą jednej z klas w <xref:System.Collections.Generic> przestrzeni nazw. Ogólnej kolekcji jest przydatne, gdy każdy element w kolekcji ma ten sam typ danych. Wymusza ogólnej kolekcji silne wpisywanie, zezwalając tylko żądanych danych typu do dodania.  
  
 W poniższej tabeli przedstawiono niektóre często używane klasy <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw:  

|Class|Opis| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|Reprezentuje kolekcję pary klucz wartość, które są zorganizowane według klucza.|  
|<xref:System.Collections.Generic.List%601>|Reprezentuje listę obiektów, które mogą być udostępniane przez indeks. Udostępnia metody do wyszukiwania, sortowania i modyfikowania list.|  
|<xref:System.Collections.Generic.Queue%601>|Reprezentuje pierwszy w pierwszym FIFO kolekcji obiektów.|  
|<xref:System.Collections.Generic.SortedList%602>|Reprezentuje kolekcję par klucz/wartość, które są sortowane według klucza opartego na skojarzonym <xref:System.Collections.Generic.IComparer%601> implementacji.|  
|<xref:System.Collections.Generic.Stack%601>|Reprezentuje ostatni w pierwszym LIFO kolekcji obiektów.|  
  
 Aby uzyskać dodatkowe informacje, zobacz [często używane typy kolekcji](../../../standard/collections/commonly-used-collection-types.md), [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md), i <xref:System.Collections.Generic>.  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>System.Collections.Concurrent Classes  
 W programie .NET Framework 4 lub nowszego, kolekcje w <xref:System.Collections.Concurrent> przestrzeni nazw zapewniają wydajność operacji wątkowo do uzyskiwania dostępu do kolekcji elementów, wiele wątków.  
  
 Klasy w <xref:System.Collections.Concurrent> przestrzeń nazw powinna być używana zamiast odpowiednie typy w <xref:System.Collections.Generic?displayProperty=nameWithType> i <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw w każdym przypadku, gdy wiele wątków jednocześnie uzyskują kolekcji. Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../standard/collections/thread-safe/index.md) i <xref:System.Collections.Concurrent>.  
  
 Niektóre klasy uwzględnione w <xref:System.Collections.Concurrent> przestrzeni nazw są <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, i <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>System.Collections — klasy  
 Klasy w <xref:System.Collections?displayProperty=nameWithType> przestrzeni nazw nie należy przechowywać elementów, w szczególności obiektów określonego typu, ale jako obiekty typu `Object`.  
  
 Jeśli to możliwe, należy użyć kolekcje ogólne w <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw lub <xref:System.Collections.Concurrent> przestrzeni nazw zamiast starsze typy w `System.Collections` przestrzeni nazw.  
  
 W poniższej tabeli przedstawiono niektóre często używane klasy w `System.Collections` przestrzeni nazw:  
  
|Class|Opis|  
|---|---|  
|<xref:System.Collections.ArrayList>|Reprezentuje tablicę obiektów, którego rozmiar jest dynamicznie zwiększony jako wymagane.|  
|<xref:System.Collections.Hashtable>|Reprezentuje kolekcję pary klucz wartość, które są podzielone na podstawie kodu skrótu klucza.|  
|<xref:System.Collections.Queue>|Reprezentuje pierwszy w pierwszym FIFO kolekcji obiektów.|  
|<xref:System.Collections.Stack>|Reprezentuje ostatni w pierwszym LIFO kolekcji obiektów.|  
  
 <xref:System.Collections.Specialized> Przestrzeń nazw zawiera klasy specjalistyczne i jednoznacznie kolekcji, takie jak kolekcji tylko do ciągów i słowników połączone listy i hybrydowych.  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementowanie kolekcję par klucz/wartość  
 <xref:System.Collections.Generic.Dictionary%602> Kolekcji ogólnych umożliwia dostęp do elementów w kolekcji przy użyciu klucza każdego elementu. Każda dodatkowa do słownika składa się z wartością i skojarzonego z nim klucza. Pobieranie wartości przy użyciu swojego klucza jest szybkie, ponieważ `Dictionary` klasy jest zaimplementowany jako tablicy skrótów.  
  
 Poniższy przykład tworzy `Dictionary` kolekcji i iteruje po słowniku przy użyciu `foreach` instrukcji.  
  
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
  
 Aby zamiast tego użyj inicjatora kolekcji, aby utworzyć `Dictionary` kolekcji, można zastąpić `BuildDictionary` i `AddToDictionary` metody przy użyciu następującej metody.  
  
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
  
 W poniższym przykładzie użyto <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> — metoda i <xref:System.Collections.Generic.Dictionary%602.Item%2A> właściwość `Dictionary` można szybko znaleźć elementu według klucza. `Item` Właściwość umożliwia dostęp do elementu w `elements` kolekcji przy użyciu `elements[symbol]` w języku C#.  
  
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
  
 W poniższym przykładzie zamiast niego użyto <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody szybko znaleźć elementu według klucza.  
  
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
## <a name="using-linq-to-access-a-collection"></a>Otwieranie kolekcji za pomocą LINQ  
 LINQ (zapytania język Language-Integrated) można uzyskać dostępu do kolekcji. Zapytania LINQ zapewniają filtrowanie, kolejność i grupowanie możliwości. Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 W poniższym przykładzie uruchamiane zapytania LINQ względem ogólnego `List`. Zapytania LINQ zwraca innej kolekcji z wynikami.  
  
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
 Poniższy przykład przedstawia procedurę sortowanie kolekcji. Przykład sortuje wystąpienia `Car` klasy, które są przechowywane w <xref:System.Collections.Generic.List%601>. `Car` Klasa implementuje <xref:System.IComparable%601> interfejs, który wymaga, aby <xref:System.IComparable%601.CompareTo%2A> metoda zaimplementowana.  
  
 Każde wywołanie <xref:System.IComparable%601.CompareTo%2A> metoda pozwala jednym porównanie, które jest używane do sortowania. Napisany przez użytkownika kod `CompareTo` metoda zwraca wartość dla każdego porównania bieżący obiekt z innym obiektem. Wartość zwracana jest mniejsza niż zero, jeśli bieżący obiekt jest mniejsza od drugiego obiektu, większa niż zero, jeśli bieżący obiekt jest większy niż drugi obiekt i zero czy są równe. Dzięki temu można zdefiniować w kodzie kryteria większa niż poniżej, a równa.  
  
 W `ListCars` metody `cars.Sort()` instrukcji sortuje listę. To wywołanie <xref:System.Collections.Generic.List%601.Sort%2A> metody <xref:System.Collections.Generic.List%601> powoduje, że `CompareTo` wywoływanej automatycznie dla metody `Car` obiekty w `List`.  
  
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
 Należy zdefiniować kolekcję zaimplementowanie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.IEnumerable> interfejsu. Aby uzyskać dodatkowe informacje, zobacz [porady: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).  
  
 Mimo że można zdefiniować niestandardowej kolekcji, jest zazwyczaj lepiej jest użyć kolekcje, które znajdują się w programie .NET Framework, które zostały opisane w [rodzaje kolekcji](#BKMK_KindsOfCollections) wcześniej w tym temacie.  
  
 W poniższym przykładzie zdefiniowano klasę kolekcji niestandardowej o nazwie `AllColors`. Ta klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga, aby <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda zaimplementowana.  
  
 `GetEnumerator` Metoda zwraca wystąpienie klasy `ColorEnumerator` klasy. `ColorEnumerator` implementuje <xref:System.Collections.IEnumerator> interfejs, który wymaga, aby <xref:System.Collections.IEnumerator.Current%2A> właściwość <xref:System.Collections.IEnumerator.MoveNext%2A> metody i <xref:System.Collections.IEnumerator.Reset%2A> metoda zaimplementowana.  
  
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
##  <a name="iterators"></a>Iteratory  
 *Iterator* służy do przeprowadzania niestandardowej iteracji w kolekcji. Iterator może być metodą lub `get` dostępu. Używa iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcji, aby zwracany był każdy element kolekcji jednym naraz.  
  
 Należy wywołać przy użyciu iteratora [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji. Każdej iteracji `foreach` pętli wywołuje iteratora. Gdy `yield return` iteratora osiągnie instrukcję, wyrażenie jest zwracany i są przechowywane w bieżącej lokalizacji w kodzie. Wykonanie jest ponownie z tej lokalizacji iteratora jest wywoływana przy następnym uruchomieniu.  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory (C#)](../../../csharp/programming-guide/concepts/iterators.md).  
  
 W poniższym przykładzie użyto metody iteracyjnej. Iterator — metoda ma `yield return` instrukcji, która znajduje się wewnątrz [dla](../../../csharp/language-reference/keywords/for.md) pętli. W `ListEvenNumbers` metoda, każdej iteracji `foreach` treść instrukcji tworzy wywołanie do metody iteracyjne, który przechodzi do następnego `yield return` instrukcji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Koncepcje programowania (C#)](../../../csharp/programming-guide/concepts/index.md)  
 [Option Strict, instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [LINQ do obiektów (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [Równoległe LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [Kolekcje i struktury danych](../../../standard/collections/index.md)  
 [Tworzenie i operowanie nimi kolekcje](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [Wybieranie klasy kolekcji](../../../standard/collections/selecting-a-collection-class.md)  
 [Porównywanie i sortowanie w ramach kolekcji](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [Kiedy należy używać kolekcji ogólnych](../../../standard/collections/when-to-use-generic-collections.md)  
 [Instrukcje: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)
