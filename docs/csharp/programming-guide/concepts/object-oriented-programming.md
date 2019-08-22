---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 50b38833582ebe46836ccfab4e1ebeb98b53a96e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659869"
---
# <a name="object-oriented-programming-c"></a>Programowanie zorientowane obiektowo (C#)

C#zapewnia pełną obsługę programowania zorientowanego obiektowo, w tym hermetyzację, dziedziczenie i polimorfizm.

*Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich jest traktowana jako pojedyncza jednostka lub obiekt.

*Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.

*Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, nawet jeśli każda klasa implementuje te same właściwości lub metody na różne sposoby.

W tej sekcji opisano następujące pojęcia:

- [Klasy i obiekty](#Classes)

  - [Elementy członkowskie klasy](#Members)

    - [Właściwości i pola](#Properties)

    - [Metody](#Methods)

    - [Konstruktory](#Constructors)

    - [Finalizatory](#Finalizers)

    - [Zdarzenia](#Events)

    - [Klasy zagnieżdżone](#NestedClasses)

  - [Modyfikatory dostępu i poziomy dostępu](#AccessModifiers)

  - [Tworzenie wystąpień klas](#InstantiatingClasses)

  - [Klasy statyczne i składowe](#Static)

  - [Typy anonimowe](#AnonymousTypes)

- [Dziedziczenie](#Inheritance)

  - [Zastępowanie elementów członkowskich](#Overriding)

- [Interfejsy](#Interfaces)

- [Typy ogólne](#Generics)

- [Delegaty](#Delegates)

## <a name="Classes"></a>Klasy i obiekty

Terminy *Klasa* i *obiekt* są czasami używane zamiennie, ale w rzeczywistości klasy opisują *Typ* obiektów, natomiast obiekty są użyteczne *wystąpienia* klas. W związku z tym czynność tworzenia obiektu jest nazywana *tworzeniem wystąpień*. Korzystając z strategii analogowej, Klasa jest planem, a obiekt jest kompilacją utworzoną z tego planu.

Aby zdefiniować klasę:

```csharp
class SampleClass
{
}
```

C#zapewnia również uproszczoną wersję klas o nazwie *Structures* , które są przydatne, gdy trzeba utworzyć dużą tablicę obiektów i nie należy zużywać zbyt dużej ilości pamięci.

Aby zdefiniować strukturę:

```csharp
struct SampleStruct
{
}
```

Aby uzyskać więcej informacji, zobacz:

- [class](../../language-reference/keywords/class.md)

- [struct](../../language-reference/keywords/struct.md)

### <a name="Members"></a>Elementy członkowskie klasy

Każda klasa może mieć różne *składowe klasy* , które zawierają właściwości opisujące dane klasy, metody definiujące zachowanie klasy oraz zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.

#### <a name="Properties"></a>Właściwości i pola

Pola i właściwości reprezentują informacje, które zawiera obiekt. Pola są podobne do zmiennych, ponieważ mogą być odczytywane lub ustawiane bezpośrednio.

Aby zdefiniować pole:

```csharp
class SampleClass
{
    public string sampleField;
}
```

Właściwości mają procedury pobierania i ustawiania, które zapewniają większą kontrolę nad sposobem ustawiania lub zwracania wartości.

C#umożliwia utworzenie prywatnego pola do przechowywania wartości właściwości lub użycie, tak zwane automatycznie implementowane właściwości, które tworzą to pole automatycznie w tle i zapewniają podstawową logikę dla procedur właściwości.

Aby zdefiniować zaimplementowaną Właściwość:

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Jeśli trzeba wykonać pewne dodatkowe operacje odczytu i zapisu wartości właściwości, Zdefiniuj pole do przechowywania wartości właściwości i podaj podstawową logikę do przechowywania i pobierania:

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

Większość właściwości ma metody lub procedury ustawiające i pobierające wartość właściwości. Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie. W C#, możesz pominąć `get` metodę lub `set` właściwość. Jednak właściwości zaimplementowane domyślnie nie mogą być tylko do odczytu lub tylko do zapisu.

Aby uzyskać więcej informacji, zobacz:

- [get](../../language-reference/keywords/get.md)

- [set](../../language-reference/keywords/set.md)

#### <a name="Methods"></a>Form

*Metoda* jest akcją, którą obiekt może wykonać.

Aby zdefiniować metodę klasy:

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

Klasa może mieć kilka implementacji lub *przeciążenia*tej samej metody, które różnią się liczbą parametrów lub typów parametrów.

Aby przeciążyć metodę:

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

W większości przypadków deklaruje metodę w ramach definicji klasy. Program C# obsługuje jednak również *metody rozszerzające* , które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.

Aby uzyskać więcej informacji, zobacz:

- [Metody](../classes-and-structs/methods.md)

- [Metody rozszerzeń](../classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a> Konstruktory

Konstruktory są metodami klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu. Konstruktory zazwyczaj inicjują elementy członkowskie danych nowego obiektu. Konstruktor można uruchomić tylko raz podczas tworzenia klasy. Ponadto kod w konstruktorze zawsze jest uruchamiany przed jakimkolwiek innym kodem w klasie. Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób jak w przypadku innych metod.

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

[Konstruktory](../classes-and-structs/constructors.md).

#### <a name="Finalizers"></a> Finalizatory

Finalizatory są używane do destruktora wystąpień klas. W .NET Framework Moduł wyrzucania elementów bezużytecznych automatycznie zarządza alokacją i ilością pamięci dla obiektów zarządzanych w aplikacji. Jednak nadal mogą być potrzebne finalizatory do czyszczenia wszystkich niezarządzanych zasobów tworzonych przez aplikację. Dla klasy może istnieć tylko jeden finalizator.

Aby uzyskać więcej informacji na temat finalizatorów i wyrzucania elementów bezużytecznych w .NET Framework, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).

#### <a name="Events"></a>Wydarzeniach

Zdarzenia umożliwiają klasie lub obiektowi powiadamianie innych klas lub obiektów w przypadku wystąpienia czegoś zainteresowania. Klasa, która wysyła (lub podnosi) zdarzenie, jest nazywana wydawcą i klasy, które odbierają (lub obsługują) zdarzenie są nazywane *subskrybentami*. Aby uzyskać więcej informacji o zdarzeniach, sposobie ich podniesienia i obsłudze, zobacz [zdarzenia](../../../standard/events/index.md).

- Aby zadeklarować zdarzenie w klasie, użyj słowa kluczowego [zdarzenia](../../language-reference/keywords/event.md) .

- Aby zgłosić zdarzenie, wywołaj delegata zdarzenia.

- Aby subskrybować zdarzenie, użyj `+=` operatora; aby anulować subskrypcję zdarzenia, `-=` Użyj operatora.

#### <a name="NestedClasses"></a>Klasy zagnieżdżone

Klasa zdefiniowana w innej klasie jest nazywana *zagnieżdżoną*. Domyślnie Klasa zagnieżdżona jest prywatna.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

Aby utworzyć wystąpienie klasy zagnieżdżonej, użyj nazwy klasy kontenera, po której następuje kropka, a następnie po której następuje nazwa klasy zagnieżdżonej:

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a>Modyfikatory dostępu i poziomy dostępu

Wszystkie klasy i elementy członkowskie klasy mogą określać poziom dostępu udostępniany innym klasom przy użyciu *modyfikatorów dostępu*.

Dostępne są następujące Modyfikatory dostępu:

|C#Modyfikator|Definicja|
|------------------|----------------|
|[public](../../language-reference/keywords/public.md)|Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego innego kodu w tym samym zestawie lub innym zestawie, który odwołuje się do niego.|
|[private](../../language-reference/keywords/private.md)|Do typu lub elementu członkowskiego można uzyskać dostęp tylko w kodzie w tej samej klasie.|
|[protected](../../language-reference/keywords/protected.md)|Do typu lub elementu członkowskiego można uzyskać dostęp tylko za pomocą kodu w tej samej klasie lub w klasie pochodnej.|
|[internal](../../language-reference/keywords/internal.md)|Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie, ale nie z innego zestawu.|
|[protected internal](../../language-reference/keywords/protected-internal.md)|Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie.|
|[private protected](../../language-reference/keywords/private-protected.md)|Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą kodu w tej samej klasie lub w klasie pochodnej w ramach zestawu klasy bazowej.|

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md).

### <a name="InstantiatingClasses"></a>Tworzenie wystąpień klas

Aby utworzyć obiekt, należy utworzyć wystąpienie klasy, lub stworzyć wystąpienia klasy.

```csharp
SampleClass sampleObject = new SampleClass();
```

Po utworzeniu wystąpienia klasy można przypisać wartości do właściwości i pól wystąpienia oraz wywołać metody klasy.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatorów obiektów:

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

Aby uzyskać więcej informacji, zobacz:

- [new, operator](../../language-reference/operators/new-operator.md)

- [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a>Klasy statyczne i składowe

Statyczny element członkowski klasy jest właściwością, procedurą lub polem, które są współużytkowane przez wszystkie wystąpienia klasy.

Aby zdefiniować statyczną składową:

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

Klasy statyczne w C# programie mają tylko statyczne elementy członkowskie i nie można tworzyć ich wystąpień. Statyczne elementy członkowskie również nie mogą uzyskać dostępu do właściwości niestatycznych, pól ani metod

Aby uzyskać więcej informacji, zobacz: [static](../../language-reference/keywords/static.md).

### <a name="AnonymousTypes"></a>Typy anonimowe

Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma użytecznej nazwy i zawiera właściwości określone w deklaracji obiektu.

Aby utworzyć wystąpienie typu anonimowego:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../classes-and-structs/anonymous-types.md).

## <a name="Inheritance"></a>Strukturze

Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa, rozszerza i modyfikuje zachowanie zdefiniowane w innej klasie. Klasa, której członkowie są dziedziczone jest nazywana *klasą bazową*, a Klasa, która dziedziczy tych członków, nosi nazwę *klasy pochodnej*. Jednak wszystkie klasy w C# niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.

> [!NOTE]
> C#nie obsługuje dziedziczenia wielokrotnego. Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.

Aby dziedziczyć z klasy bazowej:

```csharp
class DerivedClass:BaseClass {}
```

Domyślnie wszystkie klasy mogą być dziedziczone. Można jednak określić, czy Klasa nie może być używana jako klasa bazowa, ani utworzyć klasy, która może być używana tylko jako klasa bazowa.

Aby określić, że Klasa nie może być używana jako klasa bazowa:

```csharp
public sealed class A { }
```

Aby określić, że Klasa może być używana tylko jako klasa bazowa i nie można utworzyć wystąpienia:

```csharp
public abstract class B { }
```

Aby uzyskać więcej informacji, zobacz:

- [sealed](../../language-reference/keywords/sealed.md)

- [abstract](../../language-reference/keywords/abstract.md)

### <a name="Overriding"></a>Zastępowanie elementów członkowskich

Domyślnie Klasa pochodna dziedziczy wszystkich członków z jej klasy bazowej. Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić. Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.

Poniższe Modyfikatory służą do kontrolowania sposobu przesłania właściwości i metod:

|C#Modyfikator|Definicja|
|------------------|----------------|
|[virtual](../../language-reference/keywords/virtual.md)|Zezwala na przesłanianie składowej klasy w klasie pochodnej.|
|[override](../../language-reference/keywords/override.md)|Przesłania element członkowski wirtualny (zastępujący) zdefiniowany w klasie bazowej.|
|[abstract](../../language-reference/keywords/abstract.md)|Wymaga, aby element członkowski klasy był zastępowany w klasie pochodnej.|
|[new, modyfikator](../../language-reference/keywords/new-modifier.md)|Ukrywa składową dziedziczoną z klasy bazowej|

## <a name="Interfaces"></a>Interfejsów

Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń. Ale w przeciwieństwie do klas, interfejsy nie zapewniają implementacji. Są one implementowane przez klasy i zdefiniowane jako osobne jednostki z klas. Interfejs reprezentuje kontrakt, w którym Klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.

Aby zdefiniować interfejs:

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

[Interfejsy](../interfaces/index.md)

[interface](../../language-reference/keywords/interface.md)

## <a name="Generics"></a>Typy ogólne

Klasy, struktury, interfejsy i metody w .NET Framework mogą zawierać *parametry typu* , które definiują typy obiektów, które mogą być przechowywane lub używane. Najbardziej typowym przykładem typów ogólnych jest kolekcja, w której można określić typ obiektów, które mają być przechowywane w kolekcji.

Aby zdefiniować klasę generyczną:

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Aby utworzyć wystąpienie klasy generycznej:

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Aby uzyskać więcej informacji, zobacz:

- [Typy ogólne](../../../standard/generics/index.md)

- [Typy ogólne](../generics/index.md)

## <a name="Delegates"></a>Delegat

*Delegat* jest typem, który definiuje sygnaturę metody i może podać odwołanie do dowolnej metody ze zgodną sygnaturą. Metodę można wywołać (lub wywołać) za pomocą delegata. Delegaty służą do przekazywania metod jako argumentów do innych metod.

> [!NOTE]
> Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Aby uzyskać więcej informacji o używaniu delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).

Aby utworzyć delegata:

```csharp
public delegate void SampleDelegate(string str);
```

Aby utworzyć odwołanie do metody, która jest zgodna z sygnaturą określoną przez delegata:

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

- [Delegaty](../delegates/index.md)

- [delegate](../../language-reference/keywords/delegate.md)

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
