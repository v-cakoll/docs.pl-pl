---
title: Programowanie obiektowe (C#)
ms.date: 02/08/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 01d6f55bf0752f902f351675c4596abbb8ac85c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627893"
---
# <a name="object-oriented-programming-c"></a>Programowanie obiektowe (C#)

C# zapewnia pełną obsługę programowania obiektowego, w tym hermetyzacji, dziedziczenia i polimorfizmu.

- *Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich są traktowane jako pojedyncza jednostka lub obiekt.
- *Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.
- *Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, mimo że każda klasa implementuje te same właściwości lub metody na różne sposoby.

## <a name="classes-and-objects"></a>Klasy i obiekty

Terminy *klasy* i *obiektu* opisują *typ* obiektów i *wystąpienia* klas, odpowiednio. Tak więc akt tworzenia obiektu nazywa się *tworzeniem wystąpienia*. Przy użyciu analogii planu, klasa jest plan, a obiekt jest budynek wykonany z tego planu.

Aby zdefiniować klasę:

```csharp
class SampleClass
{
}
```

C# zawiera również typy o nazwie *struktur,* które są przydatne, gdy nie potrzebujesz wsparcia dla dziedziczenia lub polimorfizmu.

Aby zdefiniować strukturę:

```csharp
struct SampleStruct
{
}
```

Aby uzyskać więcej informacji, zobacz artykuły na [temat klas](../../language-reference/keywords/class.md) i słów kluczowych [struktury.](../../language-reference/builtin-types/struct.md)

### <a name="class-members"></a>Członkowie klasy

Każda klasa może mieć różne *elementy członkowskie klasy,* które zawierają właściwości, które opisują dane klasy, metody, które definiują zachowanie klasy i zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.

#### <a name="properties-and-fields"></a>Właściwości i pola

Pola i właściwości reprezentują informacje zawarte w obiekcie. Pola są jak zmienne, ponieważ mogą być odczytywane lub ustawiane bezpośrednio, z zastrzeżeniem odpowiednich modyfikatorów dostępu.

Aby zdefiniować pole, do których można uzyskać dostęp z poziomu wystąpień klasy:

```csharp
public class SampleClass
{
    string sampleField;
}
```

Właściwości mają `get` `set` i akcesorów, które zapewniają większą kontrolę nad jak wartości są ustawiane lub zwracane.

C# umożliwia utworzenie pola prywatnego do przechowywania wartości właściwości lub użyć właściwości autoimplementowane, które tworzą to pole automatycznie za kulisami i zapewniają podstawową logikę dla procedur właściwości.

Aby zdefiniować właściwość implementowane automatycznie:

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Jeśli konieczne jest wykonanie dodatkowych operacji odczytu i zapisu wartości właściwości, należy zdefiniować pole do przechowywania wartości właściwości i podać podstawową logikę przechowywania i pobierania jej:

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

Większość właściwości mają metody lub procedury zarówno ustawić i uzyskać wartość właściwości. Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby ograniczyć ich modyfikowanie lub odczytywanie. W języku `get` C#, można `set` pominąć lub metody właściwości. Jednak właściwości implementowane automatycznie nie mogą być tylko do zapisu. Właściwości autoimplementowane tylko do odczytu można ustawić w konstruktorów klasy zawierającej.

Aby uzyskać więcej informacji, zobacz:

- [get](../../language-reference/keywords/get.md)

- [Ustawić](../../language-reference/keywords/set.md)

#### <a name="methods"></a>Metody

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
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

W większości przypadków deklarujesz metodę w definicji klasy. Jednak C# obsługuje również *metody rozszerzenia,* które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicję klasy.

Aby uzyskać więcej informacji, zobacz:

- [Metody](../classes-and-structs/methods.md)
- [Metody rozszerzeń](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a>Konstruktorów

Konstruktory są metody klasy, które są wykonywane automatycznie po utworzeniu obiektu danego typu. Konstruktorzy zwykle inicjowania elementów członkowskich danych nowego obiektu. Konstruktora można uruchomić tylko raz, gdy klasa jest tworzony. Ponadto kod w konstruktorze zawsze działa przed innym kodem w klasie. Można jednak utworzyć wiele przeciążeń konstruktora w taki sam sposób, jak dla każdej innej metody.

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

Aby uzyskać więcej informacji, zobacz [Konstruktora](../classes-and-structs/constructors.md).

#### <a name="finalizers"></a>Finalizatory

Finalizatory są używane do nimniejszania wystąpień klas. W platformie .NET Framework moduł zbierający elementy bezużyteczne automatycznie zarządza alokacją i zwalnianiem pamięci dla obiektów zarządzanych w aplikacji. Jednak nadal może być konieczne finalizatorów do czyszczenia wszystkich zasobów niezarządzanych, które tworzy aplikacja. Może istnieć tylko jeden finalizatorów dla klasy.

Aby uzyskać więcej informacji na temat finalizatorów i wyrzucania elementów bezużytecznych w platformie .NET Framework, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Zdarzenia

Zdarzenia umożliwiają klasy lub obiektu, aby powiadomić inne klasy lub obiekty, gdy coś interesującego występuje. Klasa, która wysyła (lub wywołuje) zdarzenie jest wywoływana *wydawcy* i klas, które odbierają (lub doobsługi) zdarzenie są nazywane *subskrybentów*. Aby uzyskać więcej informacji o zdarzeniach, jak są one wywoływane i obsługiwane, zobacz [Zdarzenia](../../../standard/events/index.md).

- Aby zadeklarować zdarzenie w klasie, użyj słowa kluczowego [zdarzenia.](../../language-reference/keywords/event.md)

- Aby wywołać zdarzenie, wywołać delegata zdarzenia.

- Aby subskrybować `+=` zdarzenie, użyj operatora; aby zrezygnować z subskrypcji `-=` wydarzenia, skorzystaj z operatora.

#### <a name="nested-classes"></a>Klasy zagnieżdżone

Klasa zdefiniowana w innej klasie jest *nazywana zagnieżdżonym*. Domyślnie klasa zagnieżdżona jest prywatna.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

Aby utworzyć wystąpienie klasy zagnieżdżonej, należy użyć nazwy klasy kontenera, po której następuje kropka, a następnie nazwa klasy zagnieżdżonej:

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modyfikatory dostępu i poziomy dostępu

Wszystkie klasy i elementy członkowskie klasy można określić, jaki poziom dostępu zapewniają do innych klas przy użyciu *modyfikatorów dostępu*.

Dostępne są następujące modyfikatory dostępu:

|Modyfikator Języka C#|Definicja|
|------------------|----------------|
|[Publicznego](../../language-reference/keywords/public.md)|Typ lub element członkowski są dostępne przez inny kod w tym samym zestawie lub innego zestawu, który odwołuje się do niego.|
|[Prywatny](../../language-reference/keywords/private.md)|Typ lub element członkowski są dostępne tylko przez kod w tej samej klasie.|
|[protected](../../language-reference/keywords/protected.md)|Typ lub element członkowski jest dostępny tylko przez kod w tej samej klasie lub w klasie pochodnej.|
|[Wewnętrznego](../../language-reference/keywords/internal.md)|Typ lub element członkowski są dostępne przez dowolny kod w tym samym zestawie, ale nie z innego zestawu.|
|[protected internal](../../language-reference/keywords/protected-internal.md)|Typ lub element członkowski są dostępne przez dowolny kod w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie.|
|[private protected](../../language-reference/keywords/private-protected.md)|Typ lub element członkowski są dostępne przez kod w tej samej klasie lub w klasie pochodnej w zestawie klasy podstawowej.|

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md).

### <a name="instantiating-classes"></a>Tworzenie wystąpienia klas

Aby utworzyć obiekt, należy utworzyć utworzenie klasy lub utworzyć wystąpienie klasy.

```csharp
SampleClass sampleObject = new SampleClass();
```

Po ujmowaniu klasy można przypisać wartości do właściwości i pól wystąpienia i wywołać metody klasy.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

Aby przypisać wartości do właściwości podczas procesu wystąpienia klasy, należy użyć inicjatorów obiektów:

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

Aby uzyskać więcej informacji, zobacz:

- [new, operator](../../language-reference/operators/new-operator.md)
- [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a>Klasy statyczne i elementy członkowskie

Statyczny element członkowski klasy jest właściwością, procedurą lub polem współużytkowane przez wszystkie wystąpienia klasy.

Aby zdefiniować statyczny element członkowski:

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

Aby uzyskać dostęp do statycznego elementu członkowskiego, użyj nazwy klasy bez tworzenia obiektu tej klasy:

```csharp
Console.WriteLine(SampleClass.SampleString);
```

Klasy statyczne w języku C# mają tylko elementy członkowskie statyczne i nie można utworzyć wystąpienia. Elementy statyczny nie mogą również uzyskiwać dostępu do właściwości, pól lub metod niestatycznych

Aby uzyskać więcej informacji, zobacz: [static](../../language-reference/keywords/static.md).

### <a name="anonymous-types"></a>Typy anonimowe

Typy anonimowe umożliwiają tworzenie obiektów bez zapisywania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma nazwy użytkowej i zawiera właściwości określone w deklarowaniu obiektu.

Aby utworzyć wystąpienie typu anonimowego:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../classes-and-structs/anonymous-types.md).

## <a name="inheritance"></a>Dziedziczenie

Dziedziczenie umożliwia utworzenie nowej klasy, która używa ponownie, rozszerza i modyfikuje zachowanie, które jest zdefiniowane w innej klasie. Klasa, której elementy członkowskie są dziedziczone jest nazywany *klasy podstawowej*, a klasa, która dziedziczy te elementy członkowskie jest *wywoływana klasy pochodnej*. Jednak wszystkie klasy w języku C# niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.

> [!NOTE]
> C# nie obsługuje wiele dziedziczenia. Oznacza to, że można określić tylko jedną klasę podstawową dla klasy pochodnej.

Dziedziczyć z klasy podstawowej:

```csharp
class DerivedClass:BaseClass {}
```

Domyślnie wszystkie klasy mogą być dziedziczone. Można jednak określić, czy klasa nie może być używana jako klasa podstawowa, lub utworzyć klasę, która może być używana tylko jako klasa podstawowa.

Aby określić, że klasa nie może być używana jako klasa podstawowa:

```csharp
public sealed class A { }
```

Aby określić, że klasa może służyć tylko jako klasa podstawowa i nie można utworzyć wystąpienia:

```csharp
public abstract class B { }
```

Aby uzyskać więcej informacji, zobacz:

- [sealed](../../language-reference/keywords/sealed.md)

- [Abstrakcja](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a>Nadrzędne elementy członkowskie

Domyślnie klasa pochodna dziedziczy wszystkie elementy członkowskie z jego klasy podstawowej. Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić. Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.

Następujące modyfikatory są używane do kontrolowania sposobu zastępowania właściwości i metod:

|Modyfikator Języka C#|Definicja|
|------------------|----------------|
|[virtual](../../language-reference/keywords/virtual.md)|Umożliwia zastępowanie elementu członkowskiego klasy w klasie pochodnej.|
|[override](../../language-reference/keywords/override.md)|Zastępuje wirtualny (overridable) element członkowski zdefiniowany w klasie podstawowej.|
|[Abstrakcja](../../language-reference/keywords/abstract.md)|Wymaga, aby element członkowski klasy został zastąpiony w klasie pochodnej.|
|[new, modyfikator](../../language-reference/keywords/new-modifier.md)|Ukrywa element członkowski odziedziczony z klasy podstawowej|

## <a name="interfaces"></a>Interfejsy

Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń. Ale w przeciwieństwie do klas interfejsy nie zapewniają implementacji. Są one implementowane przez klasy i zdefiniowane jako oddzielne jednostki z klas. Interfejs reprezentuje kontrakt, w tym klasy, która implementuje interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.

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

Aby uzyskać więcej informacji, zobacz artykuł przewodnik programowania na [interfejsy](../interfaces/index.md) i artykuł odwołania do języka na [interfejs](../../language-reference/keywords/interface.md) słowo kluczowe.

## <a name="generics"></a>Typy ogólne

Klasy, struktury, interfejsy i metody w platformie .NET Framework mogą zawierać *parametry typu* definiujące typy obiektów, które mogą przechowywać lub używać. Najczęstszym przykładem typów ogólnych jest kolekcja, gdzie można określić typ obiektów, które mają być przechowywane w kolekcji.

Aby zdefiniować klasę rodzajową:

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

- [Typy ogólne](../../../standard/generics/index.md)

- [Typy ogólne](../generics/index.md)

## <a name="delegates"></a>Delegaty

*Pełnomocnik* jest typem, który definiuje podpis metody i może zapewnić odwołanie do dowolnej metody z zgodnym podpisem. Można wywołać (lub wywołać) metodę za pośrednictwem pełnomocnika. Delegaty służą do przekazywania metod jako argumentów do innych metod.

> [!NOTE]
> Programy obsługi zdarzeń to po prostu metody, które są wywoływane za pośrednictwem delegatów. Aby uzyskać więcej informacji na temat używania pełnomocników w obsłudze zdarzeń, zobacz [Zdarzenia](../../../standard/events/index.md).

Aby utworzyć pełnomocnika:

```csharp
public delegate void SampleDelegate(string str);
```

Aby utworzyć odwołanie do metody, która pasuje do podpisu określonego przez pełnomocnika:

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

Aby uzyskać więcej informacji, zobacz artykuł przewodnik programowania na [delegatów](../delegates/index.md) i artykuł odwołania do języka na słowo kluczowe [pełnomocnika.](../../language-reference/builtin-types/reference-types.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
