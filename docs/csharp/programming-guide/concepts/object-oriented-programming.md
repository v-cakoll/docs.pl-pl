---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: a7a3ce1b33d040b337087dfede90b58906c95cbd
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481174"
---
# <a name="object-oriented-programming-c"></a>Programowanie zorientowane obiektowo (C#)

C# zapewnia pełną obsługę programowanie zorientowane obiektowo, łącznie z hermetyzacji, dziedziczenia i polimorfizmu.

*Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i inne elementy członkowskie są traktowane jako pojedyncza jednostka lub obiekt.

*Dziedziczenie* opisuje zdolność do tworzenia nowych klas w oparciu o istniejącą klasą.

*Polimorfizm* oznacza, że może mieć wiele klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody w różny sposób.

W tej sekcji opisano następujące pojęcia:

- [Klasy i obiekty](#Classes)

  - [Elementy członkowskie klasy](#Members)

        [Properties and Fields](#Properties)

        [Methods](#Methods)

        [Constructors](#Constructors)

        [Finalizers](#Finalizers)

        [Events](#Events)

        [Nested Classes](#NestedClasses)

  - [Modyfikatory dostępu i poziomy dostępu](#AccessModifiers)

  - [Tworzenie wystąpienia klasy](#InstantiatingClasses)

  - [Klasy statyczne i członkowie](#Static)

  - [Typy anonimowe](#AnonymousTypes)

- [Dziedziczenie](#Inheritance)

  - [Zastępowanie elementów członkowskich](#Overriding)

- [Interfejsy](#Interfaces)

- [Typy ogólne](#Generics)

- [Delegaty](#Delegates)

## <a name="Classes"></a> Klasy i obiekty

Warunki *klasy* i *obiektu* są czasami stosowane zamiennie, jednak w rzeczywistości klasy opisują *typu* obiektów, podczas gdy obiekty to użytkowe  *wystąpienia* klas. Więc, akt tworzenia obiektu jest nazywany *wystąpienia*. Korzystając z analogii planu, klasa to plan, a obiekt to budynek utworzony z tego planu.

Aby zdefiniować klasę:

```csharp
class SampleClass
{
}
```

C# oferuje także uproszczonej wersji klasy o nazwie *struktury* są przydatne, gdy trzeba utworzyć duże tablice obiektów i czy chcesz zużyć do tego zbyt dużej ilości pamięci.

Aby zdefiniować strukturę:

```csharp
struct SampleStruct
{
}
```

Aby uzyskać więcej informacji, zobacz:

- [class](../../../csharp/language-reference/keywords/class.md)

- [struktura ](../../../csharp/language-reference/keywords/struct.md)

### <a name="Members"></a> Elementy członkowskie klasy

Każda klasa może mieć różne *elementy członkowskie klasy* którzy zawierają właściwości, które opisują dane klasy, metody, które definiują zachowanie klasy i wydarzenia, które zapewniają komunikację między różnych klasami i obiektami.

#### <a name="Properties"></a> Właściwości i pola

Pola i właściwości reprezentują informacje zawarte w obiekcie. Pola przypominają zmienne, ponieważ można je odczytać lub ustawić bezpośrednio.

Aby zdefiniować pole:

```csharp
class SampleClass
{
    public string sampleField;
}
```

Właściwości mają get i ustawić procedur, które zapewniają większą kontrolę nad jak ustawiania lub zwracania wartości.

C# pozwala na tworzenie prywatnego pola do przechowywania wartości właściwości lub użyć tzw automatycznie implementowanych właściwości, które tworzą to pole automatycznie w tle i ustanowiają podstawowe logiki dla procedur właściwość.

Aby zdefiniować automatycznie implementowanej właściwości:

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Jeśli musisz wykonać kilka dodatkowych operacji odczytu i zapisu wartości właściwości, zdefiniuj pole do przechowywania wartości właściwości i Zaoferuj podstawową logikę do przechowywania i pobierania:

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

Większość właściwości posiada metody lub procedury do ustawiania i pobierania wartości właściwości. Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie. W języku C# można pominąć `get` lub `set` metody właściwości. Jednak automatycznie implementowanych właściwości nie może być tylko do odczytu lub tylko do zapisu.

Aby uzyskać więcej informacji, zobacz:

- [get](../../../csharp/language-reference/keywords/get.md)

- [set](../../../csharp/language-reference/keywords/set.md)

#### <a name="Methods"></a> Metody

A *metoda* to działanie, którą obiekt może wykonywać.

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

Klasa może mieć kilka implementacji lub *przeciążenia*, z tej samej metody, które różnią się liczbą typów parametru lub parametrów.

Aby przeciążyć metodę

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

W większości przypadków użytkownik deklaruje metodę w ramach definicji klasy. Jednakże, C# obsługuje również *metody rozszerzenia* umożliwiającą dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.

Aby uzyskać więcej informacji, zobacz:

- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [Metody rozszerzeń](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a> Konstruktory

Konstruktory są metodami klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu. Konstruktory zwykle inicjują członków danych nowego obiektu. Konstruktor można uruchomić tylko raz, po utworzeniu klasy. Ponadto kod w Konstruktorze zawsze jest uruchamiany przed innymi kodami w klasie. Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób jak w przypadku każdej innej metody.

Aby zdefiniować Konstruktor dla klasy:

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

#### <a name="Finalizers"></a> Finalizatory

Finalizatory są używane do niszczenia wystąpień klas. W .NET Framework moduł odśmiecania pamięci automatycznie zarządza alokacją i zwolnieniem pamięci dla obiektów zarządzanych w Twojej aplikacji. Jednakże nadal może być konieczne finalizatorów, aby wyczyścić zasoby niezarządzane, tworzonych przez aplikację. Może istnieć tylko jeden finalizatory klasy.

Aby uzyskać więcej informacji na temat finalizatory i wyrzucania elementów bezużytecznych w .NET Framework, zobacz [wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md).

#### <a name="Events"></a> Zdarzenia

Zdarzenie pozwala klasie lub obiektowi powiadomić inne klasy lub obiektów, kiedy stanie się coś istotnego. Nosi nazwę klasy, która wysyła (lub generuje) zdarzenie *wydawcy* i klasy, otrzymywać (lub uchwyt) zdarzenia, które są nazywane *subskrybentów*. Aby uzyskać więcej informacji na temat zdarzeń, jak ich wywoływania i obsługi, zobacz [zdarzenia](../../../standard/events/index.md).

- Aby zadeklarować zdarzenia w klasie, użyj [zdarzeń](../../../csharp/language-reference/keywords/event.md) — słowo kluczowe.

- Aby wywołać zdarzenie, wywołaj delegat wydarzenia.

- Aby subskrybować zdarzenie, użyj `+=` operatora; Aby anulować subskrypcję zdarzenia, użyj `-=` operatora.

#### <a name="NestedClasses"></a> Klasy zagnieżdżone

Nosi nazwę klasy zdefiniowanej w ramach innej klasy *zagnieżdżonych*. Domyślnie zagnieżdżona klasa jest prywatna.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

Aby utworzyć wystąpienie klasy zagnieżdżonej, należy użyć nazwy klasy kontenera, następuje kropki (.), a następnie według nazwy zagnieżdżonej klasy:

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a> Modyfikatory dostępu i poziomy dostępu

Wszystkie klasy i składowych klasy, można określić poziom dostępu, jaki stanowią dla innych klas przy użyciu *modyfikatorach dostępu*.

Dostępne są następujące modyfikatory dostępu:

|Modyfikator C#|Definicja|
|------------------|----------------|
|[public](../../../csharp/language-reference/keywords/public.md)|Typ lub element członkowski może zostać oceniony przez inny kod, w tym samym zestawie lub w innym zestawie, który odwołuje się do niej.|
|[private](../../../csharp/language-reference/keywords/private.md)|Tylko możliwy typu lub elementu członkowskiego przez kod z tej samej klasy.|
|[protected](../../../csharp/language-reference/keywords/protected.md)|Tylko możliwy typu lub elementu członkowskiego przez kod z tej samej klasy lub w klasie pochodnej.|
|[internal](../../../csharp/language-reference/keywords/internal.md)|Typ lub element członkowski może zostać oceniony przez każdy kod z tego samego zestawu, ale nie z innego zestawu.|
|[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)|Typ lub element członkowski jest możliwy przez każdy kod z tego samego zestawu lub każdą pochodną klasę w innym zestawie.|
|[private protected](../../../csharp/language-reference/keywords/private-protected.md)|Typ lub element członkowski możliwy przez kod z tej samej klasy lub w klasie pochodnej w zestawie klasy bazowej.|

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md). 

### <a name="InstantiatingClasses"></a> Tworzenie wystąpienia klasy

Aby utworzyć obiekt, należy utworzyć wystąpienia klasy lub utworzyć wystąpienie klasy.

```csharp
SampleClass sampleObject = new SampleClass();
```

Po utworzeniu wystąpienia klasy, można przypisać wartości do pól i właściwości instancji i wywołania metod klasy.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

Aby przypisać wartości do właściwości w procesie tworzenia wystąpienia klasy, użyj inicjalizatorów obiektów:

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

Aby uzyskać więcej informacji, zobacz:

- [new, operator](../../../csharp/language-reference/keywords/new-operator.md)

- [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a> Klasy statyczne i członkowie

Statycznej składowej klasy jest właściwość, procedura lub pole, który jest współużytkowany przez wszystkie wystąpienia klasy.

Aby zdefiniować statyczny element członkowski:

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

Aby uzyskać dostęp do statycznej składowej, należy użyć nazwy klasy bez tworzenia obiektu tej klasy:

```csharp
Console.WriteLine(SampleClass.SampleString);
```

Klasy statyczne w języku C# mają tylko statyczne elementy członkowskie i nie można utworzyć wystąpienia. Statyczne elementy członkowskie także nie może uzyskać dostępu niestatycznej właściwości, pól ani metod

Aby uzyskać więcej informacji, zobacz: [statyczne](../../../csharp/language-reference/keywords/static.md).

### <a name="AnonymousTypes"></a> Typy anonimowe

Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma użytecznych nazw i zawiera właściwości, które określisz w odwołaniu do obiektu.

Aby utworzyć wystąpienie typu anonimowego:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).

## <a name="Inheritance"></a> Dziedziczenie

Dziedziczenie umożliwia utworzenie nowej klasy, która używa, rozszerza i modyfikuje zachowanie, która jest zdefiniowana w innej klasy. Nosi nazwę klasy, której członkowie są dziedziczeni *klasy bazowej*, a klasa, która dziedziczy tych członków, jest nazywana *klasy pochodnej*. Jednakże wszystkie klasy w języku C# niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia niskopoziomowe usługi dla wszystkich klas.

> [!NOTE]
> C# nie obsługują wielokrotnego dziedziczenia. Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.

Dziedziczenie z klasy bazowej:

```csharp
class DerivedClass:BaseClass {}
```

Domyślnie wszystkie klasy mogą być dziedziczone. Można jednak określić klasy nie może być używany jako klasa bazowa, czy utworzyć klasę, która może służyć jako klasę bazową tylko.

Aby określić, że klasa nie można użyć jako klasa bazowa:

```csharp
public sealed class A { }
```

Aby określić, że klasa może służyć jako klasę bazową tylko i nie można utworzyć wystąpienia:

```csharp
public abstract class B { }
```

Aby uzyskać więcej informacji, zobacz:

- [sealed](../../../csharp/language-reference/keywords/sealed.md)

- [abstract](../../../csharp/language-reference/keywords/abstract.md)

### <a name="Overriding"></a> Zastępowanie elementów członkowskich

Domyślnie Klasa pochodna dziedziczy wszystkie elementy członkowskie w swojej klasie podstawowej. Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, należy go zastąpić. Oznacza to można zdefiniować nową metodę implementacji metody, właściwości lub zdarzenia w klasie pochodnej.

Następujące Modyfikatory są używane do kontrolowania, jak zastąpić właściwości i metod:

|Modyfikator C#|Definicja|
|------------------|----------------|
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Zezwala na element członkowski klasy został nadpisany w klasie pochodnej.|
|[override](../../../csharp/language-reference/keywords/override.md)|Zastępuje wirtualny element członkowski (przesłanialny) zdefiniowany w klasie bazowej.|
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Wymaga, aby element członkowski klasy został nadpisany w klasie pochodnej.|
|[new, modyfikator](../../../csharp/language-reference/keywords/new-modifier.md)|Ukrywa członka dziedziczonego z klasy bazowej|

## <a name="Interfaces"></a> Interfejsy

Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń. Jednak w przeciwieństwie do klasy, interfejsy nie zapewniają implementacji. One są implementowane przez klasy i definiowane jako osobne jednostki od klas. Interfejs reprezentuje kontrakt, w tym, że klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu, dokładnie tak, jak jest zdefiniowany.

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

[Interfejsy](../../../csharp/programming-guide/interfaces/index.md)

[interface](../../../csharp/language-reference/keywords/interface.md)

## <a name="Generics"></a> Typy ogólne

Klasy, struktury, interfejsy i metody W.NET Framework mogą zawierać *parametry typu* który definiują typy obiektów, które można przechowywać lub używać. Najbardziej typowym przykładem typów ogólnych jest kolekcja, której można określić typ obiektów, które mają być przechowywane w kolekcji.

Aby zdefiniować klasę ogólną:

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Aby utworzyć wystąpienie klasy ogólnej:

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Aby uzyskać więcej informacji, zobacz:

- [Typy ogólne](~/docs/standard/generics/index.md)

- [Typy ogólne](../../../csharp/programming-guide/generics/index.md)

## <a name="Delegates"></a> Delegaty

A *delegować* to typ, który definiuje podpis metody i można podać odwołanie do dowolnej metody mającą zgodny podpis. Można wywołać (lub wywołać) metodę przez delegat. Delegaty służą do przekazywania metod jako argumentów do innych metod.

> [!NOTE]
> Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Aby uzyskać więcej informacji dotyczących używania delegatów w obsłudze zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).

Aby utworzyć delegat:

```csharp
public delegate void SampleDelegate(string str);
```

Aby utworzyć odwołanie do metody, która pasuje do oznaczenia określonego przez delegat:

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

- [Delegaty](../../../csharp/programming-guide/delegates/index.md)

- [delegate](../../../csharp/language-reference/keywords/delegate.md)

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
