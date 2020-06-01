---
title: Programowanie zorientowane obiektowo (C#)
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 98dd5147ab54375ec851ccd9b981a68098a53270
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241893"
---
# <a name="object-oriented-programming-c"></a>Programowanie zorientowane obiektowo (C#)

Język C# zapewnia pełną obsługę programowania zorientowanego obiektowo, w tym hermetyzację, dziedziczenie i polimorfizm.

- *Hermetyzacja* oznacza, że grupa powiązanych właściwości, metod i innych elementów członkowskich jest traktowana jako pojedyncza jednostka lub obiekt.
- *Dziedziczenie* opisuje możliwość tworzenia nowych klas na podstawie istniejącej klasy.
- *Polimorfizm* oznacza, że można mieć wiele klas, które mogą być używane zamiennie, nawet jeśli każda klasa implementuje te same właściwości lub metody na różne sposoby.

## <a name="classes-and-objects"></a>Klasy i obiekty

*Kategoria warunki i* *obiekt* opisują *Typ* obiektów i *wystąpienia* klas odpowiednio. W związku z tym czynność tworzenia obiektu jest nazywana *tworzeniem wystąpień*. Korzystając z strategii analogowej, Klasa jest planem, a obiekt jest kompilacją utworzoną z tego planu.

Aby zdefiniować klasę:

```csharp
class SampleClass
{
}
```

Język C# udostępnia również typy nazywane *strukturami* , które są przydatne, gdy nie potrzebujesz obsługi dziedziczenia lub polimorfizmu.

Aby zdefiniować strukturę:

```csharp
struct SampleStruct
{
}
```

Aby uzyskać więcej informacji, zobacz artykuły w słowach kluczowych [klasy](../../language-reference/keywords/class.md) i [struktury](../../language-reference/builtin-types/struct.md) .

### <a name="class-members"></a>Elementy członkowskie klasy

Każda klasa może mieć różne *składowe klasy* , które zawierają właściwości opisujące dane klasy, metody definiujące zachowanie klasy oraz zdarzenia, które zapewniają komunikację między różnymi klasami i obiektami.

#### <a name="properties-and-fields"></a>Właściwości i pola

Pola i właściwości reprezentują informacje, które zawiera obiekt. Pola są podobne do zmiennych, ponieważ mogą być odczytywane lub ustawiane bezpośrednio, zgodnie z odpowiednimi modyfikatorami dostępu.

Aby zdefiniować pole, do którego można uzyskać dostęp z wystąpień klasy:

```csharp
public class SampleClass
{
    string sampleField;
}
```

Właściwości mają `get` i `set` metody dostępu, które zapewniają większą kontrolę nad sposobem ustawiania lub zwracania wartości.

Język C# umożliwia utworzenie prywatnego pola do przechowywania wartości właściwości lub użycie automatycznie wdrożonych właściwości, które tworzą to pole automatycznie w tle i zapewniają podstawową logikę dla procedur właściwości.

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
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

Większość właściwości ma metody lub procedury ustawiające i pobierające wartość właściwości. Można jednak utworzyć właściwości tylko do odczytu lub tylko do zapisu, aby uniemożliwić ich modyfikację lub odczytanie. W języku C# można pominąć `get` `set` metodę lub właściwość. Jednak właściwości zaimplementowane domyślnie nie mogą być tylko do zapisu. Właściwości, które są implementowane w trybie tylko do odczytu, można ustawić w konstruktorach klasy zawierającej.

Aby uzyskać więcej informacji, zobacz:

- [get](../../language-reference/keywords/get.md)
- [zbiór](../../language-reference/keywords/set.md)

#### <a name="methods"></a>Metody

*Metoda* jest akcją, którą obiekt może wykonać.

Aby zdefiniować metodę klasy:

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

Klasa może mieć kilka implementacji lub *przeciążenia*tej samej metody, które różnią się liczbą parametrów lub typów parametrów.

Aby przeciążyć metodę:

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

W większości przypadków deklaruje metodę w ramach definicji klasy. Jednak w języku C# obsługiwane są również *metody rozszerzające* , które umożliwiają dodawanie metod do istniejącej klasy poza rzeczywistą definicją klasy.

Aby uzyskać więcej informacji, zobacz:

- [Metody](../classes-and-structs/methods.md)
- [Metody rozszerzania](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a>Konstruktory

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

Aby uzyskać więcej informacji, zobacz [konstruktory](../classes-and-structs/constructors.md).

#### <a name="finalizers"></a>Finalizatory

Finalizator jest używany do destruktora wystąpień klas. W programie .NET moduł zbierający elementy bezużyteczne automatycznie zarządza alokacją i ilością pamięci dla zarządzanych obiektów w aplikacji. Jednak nadal mogą być potrzebne finalizatory do czyszczenia wszystkich niezarządzanych zasobów tworzonych przez aplikację. Może istnieć tylko jeden finalizator dla klasy.

Aby uzyskać więcej informacji na temat finalizatorów i wyrzucania elementów bezużytecznych w programie .NET, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Zdarzenia

Zdarzenia umożliwiają klasie lub obiektowi powiadamianie innych klas lub obiektów w przypadku wystąpienia czegoś zainteresowania. Klasa, która wysyła (lub podnosi) zdarzenie, jest nazywana *wydawcą* i klasy, które odbierają (lub obsługują) zdarzenie są nazywane *subskrybentami*. Aby uzyskać więcej informacji o zdarzeniach, sposobie ich podniesienia i obsłudze, zobacz [zdarzenia](../../../standard/events/index.md).

- Aby zadeklarować zdarzenie w klasie, użyj słowa kluczowego [zdarzenia](../../language-reference/keywords/event.md) .
- Aby zgłosić zdarzenie, wywołaj delegata zdarzenia.
- Aby subskrybować zdarzenie, użyj `+=` operatora; aby anulować subskrypcję zdarzenia, użyj `-=` operatora.

#### <a name="nested-classes"></a>Klasy zagnieżdżone

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

### <a name="access-modifiers-and-access-levels"></a>Modyfikatory dostępu i poziomy dostępu

Wszystkie klasy i elementy członkowskie klasy mogą określać poziom dostępu udostępniany innym klasom przy użyciu *modyfikatorów dostępu*.

Dostępne są następujące Modyfikatory dostępu:

| Modyfikator języka C# | Definicja |
|--|--|
| [public](../../language-reference/keywords/public.md) | Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego innego kodu w tym samym zestawie lub innym zestawie, który odwołuje się do niego. |
| [private](../../language-reference/keywords/private.md) | Do typu lub elementu członkowskiego można uzyskać dostęp tylko w kodzie w tej samej klasie. |
| [protected](../../language-reference/keywords/protected.md) | Do typu lub elementu członkowskiego można uzyskać dostęp tylko za pomocą kodu w tej samej klasie lub w klasie pochodnej. |
| [internal](../../language-reference/keywords/internal.md) | Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie, ale nie z innego zestawu. |
| [protected internal](../../language-reference/keywords/protected-internal.md) | Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą dowolnego kodu w tym samym zestawie lub przez dowolną klasę pochodną w innym zestawie. |
| [private protected](../../language-reference/keywords/private-protected.md) | Do typu lub elementu członkowskiego można uzyskać dostęp za pomocą kodu w tej samej klasie lub w klasie pochodnej w ramach zestawu klasy bazowej. |

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md).

### <a name="instantiating-classes"></a>Tworzenie wystąpień klas

Aby utworzyć obiekt, należy utworzyć wystąpienie klasy, lub stworzyć wystąpienia klasy.

```csharp
SampleClass sampleObject = new SampleClass();
```

Po utworzeniu wystąpienia klasy można przypisać wartości do właściwości i pól wystąpienia oraz wywołać metody klasy.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

Aby przypisać wartości do właściwości podczas procesu tworzenia wystąpienia klasy, należy użyć inicjatorów obiektów:

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

Aby uzyskać więcej informacji, zobacz:

- [Operator new](../../language-reference/operators/new-operator.md)
- [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a>Klasy statyczne i składowe

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

Klasy statyczne w języku C# mają tylko statyczne elementy członkowskie i nie można tworzyć wystąpień. Statyczne elementy członkowskie również nie mogą uzyskać dostępu do właściwości niestatycznych, pól ani metod

Aby uzyskać więcej informacji, zobacz: [static](../../language-reference/keywords/static.md).

### <a name="anonymous-types"></a>Typy anonimowe

Typy anonimowe umożliwiają tworzenie obiektów bez konieczności pisania definicji klasy dla typu danych. Zamiast tego kompilator generuje klasę dla Ciebie. Klasa nie ma użytecznej nazwy i zawiera właściwości określone w deklaracji obiektu.

Aby utworzyć wystąpienie typu anonimowego:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

Aby uzyskać więcej informacji, zobacz: [Typy anonimowe](../classes-and-structs/anonymous-types.md).

## <a name="inheritance"></a>Dziedziczenie

Dziedziczenie umożliwia utworzenie nowej klasy, która ponownie używa, rozszerza i modyfikuje zachowanie zdefiniowane w innej klasie. Klasa, której członkowie są dziedziczone jest nazywana *klasą bazową*, a Klasa, która dziedziczy tych członków, nosi nazwę *klasy pochodnej*. Jednak wszystkie klasy w języku C# niejawnie dziedziczą z <xref:System.Object> klasy, która obsługuje hierarchię klas .NET i zapewnia usługi niskiego poziomu dla wszystkich klas.

> [!NOTE]
> Język C# nie obsługuje dziedziczenia wielokrotnego. Oznacza to, że można określić tylko jedną klasę bazową dla klasy pochodnej.

Aby dziedziczyć z klasy bazowej:

```csharp
class DerivedClass:BaseClass { }
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
- [streszczeń](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a>Zastępowanie elementów członkowskich

Domyślnie Klasa pochodna dziedziczy wszystkich członków z jej klasy bazowej. Jeśli chcesz zmienić zachowanie dziedziczonego elementu członkowskiego, musisz go zastąpić. Oznacza to, że można zdefiniować nową implementację metody, właściwości lub zdarzenia w klasie pochodnej.

Poniższe Modyfikatory służą do kontrolowania sposobu przesłania właściwości i metod:

| Modyfikator języka C# | Definicja |
|--|--|
| [virtual](../../language-reference/keywords/virtual.md) | Zezwala na przesłanianie składowej klasy w klasie pochodnej. |
| [override](../../language-reference/keywords/override.md) | Przesłania element członkowski wirtualny (zastępujący) zdefiniowany w klasie bazowej. |
| [streszczeń](../../language-reference/keywords/abstract.md) | Wymaga, aby element członkowski klasy był zastępowany w klasie pochodnej. |
| [new, modyfikator](../../language-reference/keywords/new-modifier.md) | Ukrywa składową dziedziczoną z klasy bazowej |

## <a name="interfaces"></a>Interfejsy

Interfejsy, takie jak klasy, definiują zestaw właściwości, metod i zdarzeń. Ale w przeciwieństwie do klas, interfejsy nie zapewniają implementacji. Są one implementowane przez klasy i zdefiniowane jako osobne jednostki z klas. Interfejs reprezentuje kontrakt, w którym Klasa implementująca interfejs musi implementować każdy aspekt tego interfejsu dokładnie tak, jak jest zdefiniowany.

Aby zdefiniować interfejs:

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

Aby zaimplementować interfejs w klasie:

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

Aby uzyskać więcej informacji, zobacz artykuł Przewodnik programowania dotyczący [interfejsów](../interfaces/index.md) i artykułu referencyjnego języka dla słowa kluczowego [Interface](../../language-reference/keywords/interface.md) .

## <a name="generics"></a>Typy ogólne

Klasy, struktury, interfejsy i metody w programie .NET mogą zawierać *parametry typu* , które definiują typy obiektów, które mogą być przechowywane lub używane. Najbardziej typowym przykładem typów ogólnych jest kolekcja, w której można określić typ obiektów, które mają być przechowywane w kolekcji.

Aby zdefiniować klasę generyczną:

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Aby utworzyć wystąpienie klasy generycznej:

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Aby uzyskać więcej informacji, zobacz:

- [Typy ogólne w .NET](../../../standard/generics/index.md)
- [Typy ogólne — Przewodnik programowania w języku C#](../generics/index.md)

## <a name="delegates"></a>Delegaci

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
    public static void SampleMethod(string message)
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

Aby uzyskać więcej informacji, zobacz artykuł Przewodnik programowania dotyczący [delegatów](../delegates/index.md) i artykuł referencyjny języka w słowie kluczowym [delegata](../../language-reference/builtin-types/reference-types.md) .

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
