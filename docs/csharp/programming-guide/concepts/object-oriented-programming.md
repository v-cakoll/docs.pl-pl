---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6da28e97a33e962d4926a3b65d0fdf388c252d9a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="object-oriented-programming-c"></a>Programowanie zorientowane obiektowo (C#)
C# zapewnia pełną obsługę programowanie zorientowane obiektowo, łącznie z hermetyzacji, dziedziczenia i polimorfizm.  
  
 *Hermetyzacja* oznacza, że grupy powiązane właściwości, metod i inne elementy członkowskie są traktowane jako pojedyncza jednostka lub obiekt.  
  
 *Dziedziczenie* opisuje może tworzyć nowe klasy oparte na istniejącej klasy.  
  
 *Polimorfizm* oznacza, że może mieć wielu klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody na różne sposoby.  
  
 W tej sekcji opisano następujące kwestie:  
  
-   [Klasy i obiekty](#Classes)  
  
    -   [Członkowie klasy](#Members)  
  
         [Właściwości i pola](#Properties)  
  
         [Metody](#Methods)  
  
         [Konstruktory](#Constructors)  
  
         [Finalizatory](#Finalizers)  
  
         [Zdarzenia](#Events)  
  
         [Klasy zagnieżdżone](#NestedClasses)  
  
    -   [Modyfikatory dostępu i poziomy dostępu](#AccessModifiers)  
  
    -   [Utworzenie wystąpienia klasy](#InstantiatingClasses)  
  
    -   [Klasy statyczne i elementów członkowskich](#Static)  
  
    -   [Typy anonimowe](#AnonymousTypes)  
  
-   [Dziedziczenie](#Inheritance)  
  
    -   [Zastępowanie elementów członkowskich](#Overriding)  
  
-   [Interfejsy](#Interfaces)  
  
-   [Typy ogólne](#Generics)  
  
-   [Delegaci](#Delegates)  
  
##  <a name="Classes"></a> Klasy i obiekty  
 Warunki *klasy* i *obiektu* są czasami używane zamiennie, ale w rzeczywistości opisano klasy *typu* obiektów, gdy obiekty są użyteczne  *wystąpienia* klas. Dlatego utworzenie obiektu jest nazywany *wystąpienia*. Przy użyciu odpowiednio planu, klasa to umożliwi, a obiekt jest budynku z tego planu.  
  
 Aby zdefiniować klasy:  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 C# są także światła wersja klasy o nazwie *struktury* są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i chcesz używać zbyt dużej ilości pamięci do tego.  
  
 Aby zdefiniować strukturę:  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> Członkowie klasy  
 Każda klasa może mieć różne *klasy elementów członkowskich* zawierające właściwości, które opisują dane klasy, metody definiujące zachowanie klasy i zdarzenia, które zapewniają komunikację między różnych klas i obiektów.  
  
####  <a name="Properties"></a> Właściwości i pola  
 Pola i właściwości reprezentują informacje, która zawiera obiekt. Pola są podobne do zmiennych, ponieważ może być odczytany lub ustawić bezpośrednio.  
  
 Aby zdefiniować pola:  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 Właściwości mają get i ustaw procedur, które zapewniają większą kontrolę w sposób ustawiona lub zwrócona wartości.  
  
 C# służy do utworzenia prywatnej pola do przechowywania wartości właściwości lub użyj tak zwane właściwości zaimplementowane automatycznie utworzyć w tym polu automatycznie w tle, które zapewniają podstawowa logika procedury właściwości.  
  
 Aby zdefiniować właściwości zaimplementowane automatycznie:  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 Jeśli musisz wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i podaj podstawowa logika do przechowywania i pobierania jej:  
  
```csharp  
class SampleClass  
{  
    private int _sample;  
    public int Sample  
    {  
        // Return the value stored in a field.  
        get { return _sample; }  
        // Store the value in the field.  
        set { _sample = value; }  
    }  
}  
```  
  
 Większość właściwości mają metody lub procedury zarówno Ustawianie i pobieranie wartości właściwości. Można jednak utworzyć właściwości tylko do odczytu lub w trybie tylko do zapisu, aby uniemożliwić ich modyfikacji lub odczytu. W języku C#, można pominąć `get` lub `set` metody property. Jednak automatycznie implementowane właściwości nie może być tylko do odczytu lub w trybie tylko do zapisu.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [get](../../../csharp/language-reference/keywords/get.md)  
  
-   [set](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> Metody  
 A *metody* to operacja, którą można wykonać obiektu.  
  
 Aby zdefiniować metody klasy:  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 Klasa może mieć wielu implementacji lub *przeciążenia*, metody różne liczby parametrów ani typów parametrów.  
  
 Aby można było przeciążyć metodę:  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 W większości przypadków należy zadeklarować metody w ramach definicji klasy. Jednak C# obsługuje również *metody rozszerzenia* umożliwiające dodawanie metody do istniejącej klasy poza rzeczywiste definicji klasy.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Metody rozszerzeń](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> Konstruktory  
 Konstruktory są metody klasy, które są wykonywane automatycznie, gdy utworzono obiekt danego typu. Konstruktory zainicjować zazwyczaj elementy członkowskie danych nowego obiektu. Konstruktor można uruchomić tylko raz, podczas tworzenia klasy. Ponadto w Konstruktorze kod zawsze uruchamiany przed innymi kod w klasie. Jednak w taki sam sposób jak w przypadku innych metod, można utworzyć wielu przeciążeń konstruktora.  
  
 Aby zdefiniować konstruktora dla klasy:  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 Aby uzyskać więcej informacji, zobacz:  
  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md).  
  
####  <a name="Finalizers"></a> Finalizatory  
 Finalizatory są używane do destruct wystąpień klas. W programie .NET Framework moduł zbierający elementy bezużyteczne automatycznie zarządza alokacji i wersji pamięci dla zarządzanych obiektów w aplikacji. Jednakże nadal może być konieczne finalizatorów, aby oczyścić wszelkie niezarządzane zasoby, tworzonych przez aplikację. Może istnieć tylko jedna finalizatory klasy.  
  
 Aby uzyskać więcej informacji na temat finalizatory i wyrzucanie elementów bezużytecznych w programie .NET Framework, zobacz [wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).  
  
####  <a name="Events"></a> Zdarzenia  
 Zdarzenia włączyć klasę lub obiekt, aby powiadomić innych grup lub obiektów, kiedy coś odsetek występuje. Klasa, która wysyła (lub zgłasza) zdarzenia jest nazywany *wydawcy* i klasy, które odbierać (lub dojścia) zdarzenia są nazywane *subskrybentów*. Aby uzyskać więcej informacji o zdarzeniach, sposób ich pojawienia się i obsługi, zobacz [zdarzenia](../../../standard/events/index.md).  
  
-   Aby zadeklarować zdarzenia w klasie, użyj [zdarzeń](../../../csharp/language-reference/keywords/event.md) — słowo kluczowe.  
  
-   Aby zgłosić zdarzenie, wywołania delegata zdarzenia.  
  
-   Aby subskrybować zdarzenia, użyj `+=` operatora; Aby anulować subskrypcję zdarzenia, użyj `-=` operatora.  
  
####  <a name="NestedClasses"></a> Klasy zagnieżdżone  
 Nosi nazwę klasy zdefiniowanej w klasie innej *zagnieżdżonych*. Domyślnie zagnieżdżona klasa jest prywatne.  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 Można utworzyć wystąpienia klasy zagnieżdżonej, należy użyć nazwy klasy kontenera znak kropki (.) i po niej nazwę klasy zagnieżdżonej:  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> Modyfikatory dostępu i poziomy dostępu  
 Wszystkie klasy i elementów członkowskich klasy można określić poziom dostępu zapewniają do innych klas przy użyciu *modyfikatorów dostępu*.  
  
 Dostępne są następujące modyfikatorów dostępu:  
  
|C# Modifier|Definicja|  
|------------------|----------------|  
|[public](../../../csharp/language-reference/keywords/public.md)|Typ lub element członkowski jest możliwy przez inny kod, w tym samym zestawie lub innego zestawu, który odwołuje się on.|  
|[private](../../../csharp/language-reference/keywords/private.md)|Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy.|  
|[protected](../../../csharp/language-reference/keywords/protected.md)|Typ lub element członkowski, jest możliwy tylko przez kod w tej samej klasy lub w klasie pochodnej.|  
|[internal](../../../csharp/language-reference/keywords/internal.md)|Typ lub element członkowski jest możliwy przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.|  
|[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)|Typ lub element członkowski jest dostępna przez dowolny kod w tym samym zestawie lub dowolnej klasy pochodnej w innym zestawie.|  
|[private protected](../../../csharp/language-reference/keywords/private-protected.md)|Typ lub element członkowski jest możliwy przez kod w tej samej klasy lub w klasie pochodnej w zestawie klasy podstawowej.|  
  
 Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
###  <a name="InstantiatingClasses"></a> Utworzenie wystąpienia klasy  
 Do utworzenia obiektu, należy utworzyć wystąpienia klasy lub utworzyć wystąpienia klasy.  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 Po utworzenie wystąpienia klasy, można przypisać wartości do właściwości i pola wystąpienia i wywołania metody klasy.  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatory obiektów:  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [new, operator](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> Klasy statyczne i elementów członkowskich  
 Statyczny element członkowski klasy jest właściwość, procedura lub pola, które jest współużytkowana przez wszystkie wystąpienia klasy.  
  
 Do definiowania statycznego elementu członkowskiego:  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 Aby uzyskać dostęp do statycznego elementu członkowskiego, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 Klasy statyczne w języku C# mieć tylko statyczne elementy członkowskie i nie można utworzyć wystąpienia. Statyczne elementy członkowskie także nie może uzyskać dostępu właściwości niestatycznego pola lub metody  
  
 Aby uzyskać więcej informacji, zobacz: [statycznych](../../../csharp/language-reference/keywords/static.md).  
  
###  <a name="AnonymousTypes"></a> Typy anonimowe  
 Typy anonimowe umożliwiają tworzenie obiektów bez pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma używać nazwy i zawiera właściwości, które określisz w odwołaniu do obiektu.  
  
 Można utworzyć wystąpienia typu anonimowego:  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Aby uzyskać więcej informacji, zobacz: [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
##  <a name="Inheritance"></a> Dziedziczenie  
 Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa rozszerza i modyfikuje zachowanie, który jest zdefiniowany w innej klasy. Klasa, której członkami są dziedziczone jest nazywana *klasa podstawowa*, i nosi nazwę klasy, która dziedziczy tych członków *klasy*. Jednak wszystkie klasy w języku C# niejawnie dziedziczyć <xref:System.Object> klasy, która obsługuje hierarchii klas .NET i udostępnia usługi niskiego poziomu dla wszystkich klas.  
  
> [!NOTE]
>  C# nie obsługuje wielu dziedziczenia. Oznacza to można określić tylko jedną klasę podstawową dla klasy pochodnej.  
  
 Dziedziczenie z klasy podstawowej:  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 Domyślnie wszystkie klasy mogą być dziedziczone. Jednak można określić, czy nie mogą być używane jako klasę podstawową klasy lub utworzyć klasę, która może służyć jako klasę podstawową tylko.  
  
 Aby określić, że klasa nie można użyć jako klasy podstawowej:  
  
```csharp  
public sealed class A { }  
```  
  
 Aby określić, że klasa może służyć jako klasę podstawową tylko i nie można utworzyć wystąpienia:  
  
```csharp  
public abstract class B { }  
```  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> Zastępowanie elementów członkowskich  
 Domyślnie Klasa pochodna dziedziczy wszystkie elementy członkowskie ze swojej klasy podstawowej. Aby zmienić zachowanie dziedziczony element członkowski, należy go zastąpić. Oznacza to można zdefiniować nowej implementacji metody, właściwości lub zdarzenia w klasie pochodnej.  
  
 Następujących modyfikatorów są używane do kontrolowania sposobu przesłonięcia właściwości i metody:  
  
|C# Modifier|Definicja|  
|------------------|----------------|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Umożliwia elementu członkowskiego klasy do zastąpienia w klasie pochodnej.|  
|[override](../../../csharp/language-reference/keywords/override.md)|Zastępuje członka wirtualnego (możliwym do zastąpienia) zdefiniowana w klasie podstawowej.|  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Wymaga, aby element członkowski klasy do zastąpienia w klasie pochodnej.|  
|[new, modyfikator](../../../csharp/language-reference/keywords/new-modifier.md)|Ukrywa element członkowski dziedziczona z klasy podstawowej|  
  
##  <a name="Interfaces"></a> Interfejsy  
 Interfejsy, takich jak klasy, zdefiniuj zbiór właściwości, metod i zdarzeń. Jednak w przeciwieństwie do klasy, interfejsy nie dostarcza implementacji. Są implementowane przez klasy i zdefiniowane jako osobne jednostki z klas. Interfejs reprezentuje kontraktu, w tym klasy, która implementuje interfejs musi implementować każdego aspektu ten interfejs, dokładnie tak, jak jest zdefiniowany.  
  
 Aby zdefiniować interfejsu:  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 Aby zaimplementować interfejs w klasie:  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 Aby uzyskać więcej informacji, zobacz:  
  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a> Typy ogólne  
 Klasy, struktury, interfejsy i metody w programie .NET Framework mogą zawierać *parametry typu* definiującą typów obiektów, które mogą przechowywać lub użyć. Najbardziej typowym przykładem typów ogólnych jest kolekcją, w którym można określić typ obiektów, które mają być przechowywane w kolekcji.  
  
 Aby zdefiniować klasy ogólnej:  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 Można utworzyć wystąpienia klasy generycznej:  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Typy ogólne](~/docs/standard/generics/index.md)  
  
-   [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a> Obiekty delegowane  
 A *delegować* jest typ, który określa podpis metody i można udostępnić odwołanie do dowolnej metody zgodnego podpisu. Można wywołać (lub wywołać) metoda za pośrednictwem pełnomocnika. Delegaty służą do przekazywania metod jako argumentów do innych metod.  
  
> [!NOTE]
>  Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).  
  
 Do utworzenia delegata:  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 Aby utworzyć odwołanie do metody, która odpowiada podpisu określony na podstawie delegata:  
  
```csharp  
class SampleClass  
{  
    // Method that matches the SampleDelegate signature.  
    public static void sampleMethod(string message)  
    {  
        // Add code here.  
    }  
    // Method that instantiates the delegate.  
    void SampleDelegate()  
    {  
        SampleDelegate sd = sampleMethod;  
        sd("Sample string");  
    }  
}  
```  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
