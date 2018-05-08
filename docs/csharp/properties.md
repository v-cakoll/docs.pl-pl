---
title: Właściwości
description: Dowiedz się więcej o języku C# właściwości, które obejmują funkcje sprawdzania poprawności, obliczana wartości, obliczanie leniwe i zmienić właściwości powiadomienia.
ms.date: 04/03/2017
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 3fcb0c7394093bbb00986e51179504327049ca4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="properties"></a>Właściwości

Właściwości są pierwszej klasie obywateli w języku C#. Język definiuje składnię, która umożliwia deweloperom pisanie kodu, który dokładnie odzwierciedla cele ich projektu.

Właściwości przypominają pola, gdy są one używane.
Jednak w przeciwieństwie do pola, właściwości są implementowane przy użyciu metody dostępu definiujące instrukcje wykonywane, gdy właściwość jest dostępne lub przypisany.

## <a name="property-syntax"></a>Składnia właściwości

Składnia właściwości jest stanowi naturalne rozszerzenie do pól. Pole określa lokalizację magazynu:

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

Definicja właściwości zawiera deklaracje dla `get` i `set` dostępu, która pobiera i przypisuje wartość tej właściwości:

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

Składnia pokazanym powyżej jest *automatycznie właściwości* składni. Kompilator generuje lokalizację przechowywania dla pola, które wykonuje kopię zapasową właściwości. Kompilator implementuje również treści `get` i `set` metody dostępu.

Czasami należy zainicjować właściwość na wartość inną niż domyślna dla jego typu.  C# umożliwia który przez ustawienie wartości nawiasem zamykającym dla właściwości. Możesz wybrać wartość początkową `FirstName` właściwość jako ciąg pusty zamiast `null`. Należy wprowadzić ten w sposób przedstawiony poniżej:

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

Jest to najbardziej przydatny w przypadku właściwości tylko do odczytu, jak można zauważyć w dalszej części tego tematu.

Istnieje także możliwość zdefiniowania magazynu użytkownika, jak pokazano poniżej:

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Jeśli implementacja właściwości jest jedno wyrażenie, możesz użyć *zabudowanych wyrażenia elementów członkowskich* metody pobierającej lub ustawiającej:

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Tej składni uproszczoną będą używane, jeśli to możliwe, w tym temacie.

Definicja właściwości pokazanym powyżej jest właściwością odczytu i zapisu. Zwróć uwagę, słowo kluczowe `value` w metody dostępu set. `set` Akcesor zawsze ma jeden parametr o nazwie `value`. `get` Akcesora musi zwracać wartość do przekonwertowania na typ właściwości (`string` w tym przykładzie).
 
To podstawy składni. Istnieje wiele różnych odmiany, które obsługują szereg idioms inny projekt. Umożliwia Eksplorowanie te i Dowiedz się opcje Składnia dla każdego.

## <a name="scenarios"></a>Scenariusze

Powyższych przykładach pokazano, co najprostszym przypadków definicji właściwości: właściwości odczytu / zapisu o nie sprawdzania poprawności. Pisanie kodu mają w `get` i `set` metody dostępu, możesz utworzyć wiele różnych scenariuszy.

### <a name="validation"></a>Walidacja

Możesz pisać kod `set` dostępu, aby upewnić się, czy wartości reprezentowane przez właściwość zawsze są prawidłowe. Na przykład, załóżmy, że jedną regułę `Person` klasy jest, że nazwa nie może być puste lub biały znak. Czy zapisz ją w następujący sposób:

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

W powyższym przykładzie wymusza zasadę czy imię nie może być puste lub biały znak. Jeśli zapisuje dewelopera

```csharp
hero.FirstName = "";
```

Przypisanie zgłasza `ArgumentException`. Ponieważ metodą dostępu set właściwości musi mieć zwracanego typu void, należy włączyć raportowanie błędów metody dostępu set przez Zgłaszanie wyjątku.

To jest prostym przypadku weryfikacji. Można rozszerzyć tej samej składni na niczego wymagane w danym scenariuszu. Sprawdź relacje między inne właściwości lub sprawdzania poprawności żadnych warunków zewnętrznych. Wszystkie prawidłowe C# instrukcje są prawidłowe w akcesor właściwości.

### <a name="read-only"></a>tylko do odczytu

Do tego momentu wszystkich przejrzanych definicji właściwości są właściwości odczytu/zapisu z metod dostępu publicznego. To nie jest jedyną poprawną ułatwień dostępu dla właściwości.
Można utworzyć właściwości tylko do odczytu, lub zapewniają różne ułatwień dostępu w zestawie i metody dostępu get. Załóżmy, że Twoje `Person` klasy należy włączyć tylko zmiana wartości `FirstName` właściwości z innych metod tej klasy. Możesz podać metody dostępu set `private` dostępności zamiast `public`:

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

Teraz `FirstName` właściwości są dostępne z kodu, ale można go przypisać tylko z innego kodu w `Person` klasy.

Można dodać żadnych modyfikator dostępu ograniczające albo zestaw lub metody dostępu get. Wszelkie modyfikator dostępu umieszczony na poszczególnych akcesora musi być bardziej ograniczone niż modyfikatora dostępu w definicji właściwości. Powyższe jest dozwolony ponieważ `FirstName` właściwość jest `public`, ale set jest `private`. Nie można deklarować `private` właściwości o `public` metody dostępu. Deklaracje właściwości również mogą być deklarowane `protected`, `internal`, `protected internal`, `private protected` lub nawet `private`.   

Jest również prawne do umieszczenia na bardziej restrykcyjne modyfikator `get` metody dostępu. Na przykład można mieć `public` właściwości, ograniczając jednocześnie `get` metody dostępu `private`. W tym scenariuszu rzadko odbywa się w praktyce.

Można również ograniczyć modyfikacji właściwości, dzięki czemu można ustawić tylko w konstruktorze lub inicjatorze właściwości. Można zmodyfikować `Person` klasy, w następujący sposób:

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

Ta funkcja jest najczęściej używana do inicjowania kolekcji, które są dostępne jako właściwości tylko do odczytu:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Właściwości obliczanej

Właściwość nie trzeba po prostu zwrócić wartość pola elementu członkowskiego. Można utworzyć właściwości, które zwracają obliczoną wartość. Umożliwia rozwijanie `Person` obiektu do zwrócenia pełną nazwę, obliczone przez łączenie imiona i nazwiska:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

Przykład powyżej używa [ciągu interpolacji](../csharp/language-reference/tokens/interpolated.md) funkcję, aby utworzyć ciąg sformatowany dla pełnej nazwy.

Można również użyć *zabudowanych wyrażenia elementów członkowskich*, który zapewnia bardziej zwięzły sposób utworzyć obliczone `FullName` właściwości:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
*Członkowie zabudowanych wyrażenie* użyj *wyrażenia lambda* składni w celu zdefiniowania metody, która zawiera jedno wyrażenie. W tym miejscu tego wyrażenia zwraca pełną nazwę dla obiekt osoby.

### <a name="lazy-evaluated-properties"></a>Właściwości obliczane opóźnione

Można mieszać pojęcie właściwości obliczanej z magazynem i utworzyć *opóźnieniem obliczone właściwości*.  Na przykład można zaktualizować `FullName` właściwości tak, aby tylko ciągu formatowania wystąpił uzyskiwał został po raz pierwszy:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

Powyższy kod zawiera usterkę, mimo że. Jeśli kod aktualizuje wartość albo `FirstName` lub `LastName` właściwości, wcześniej ocenionych `fullName` pole jest nieprawidłowe. Musisz zaktualizować `set` metod dostępu `FirstName` i `LastName` właściwości, aby `fullName` pola jest obliczane ponownie:

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

Wynikiem tej wersji ostatecznej `FullName` właściwość tylko w razie potrzeby.
Jeśli poprzednio obliczonej wersji jest prawidłowy, jest używany. Jeśli inna zmiana stanu unieważnia poprzednio obliczonej wersji, zostaną obliczone go ponownie. Deweloperzy korzystający z tej klasy nie trzeba znać szczegóły implementacji. Żadna z tych zmian wewnętrzny wpływa na użycie obiektu osoby. To klucza Przyczyna przy użyciu właściwości do udostępnienia danych elementów członkowskich obiektu.
 
### <a name="inotifypropertychanged"></a>Interfejs INotifyPropertyChanged

Końcowe scenariusz, w których należy napisać kod w metodzie dostępu właściwości służy do obsługi `INotifyPropertyChanged` interfejs używany do powiadamiania klientów powiązania danych, które wartość została zmieniona. Po zmianie wartości właściwości obiektu zgłasza `PropertyChanged` zdarzeń, aby wskazać zmianę. Powiązanie bibliotek, danych z kolei aktualizacji wyświetlanych elementów oparte na tej zmiany. Poniższy kod przedstawia sposób czy implementuje `INotifyPropertyChanged` dla `FirstName` właściwości tej klasy osoby.

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

`?.` Operator jest nazywany *null operator warunkowy*. Sprawdza odwołanie o wartości null przed obliczeniem po prawej stronie operatora. W rezultacie jest to, że jeśli nie ma żadnych subskrybentów `PropertyChanged` zdarzeń, kod, aby zgłosić zdarzenie nie jest wykonywana. Go spowoduje zgłoszenie `NullReferenceException` bez to w takim przypadku Sprawdź. Przejrzyj stronę [ `events` ](delegates-events.md) więcej szczegółów. W tym przykładzie również używa nowego `nameof` operatora konwersji z symbol nazwa właściwości jego reprezentacja tekstowa.
Przy użyciu `nameof` może zmniejszyć liczbę błędów, gdzie ma została błędnie wpisana nazwa właściwości.

Ponownie, to przykładem jest przypadek, w którym można napisać kod w metod dostępu do sieci na potrzeby obsługi scenariuszy, które są potrzebne.

## <a name="summing-up"></a>Podsumowanie

Właściwości są formę inteligentne pola w klasie lub obiektu. Z poza obiekt, pojawią się one takich jak pola obiektu. Jednak właściwości można zaimplementować korzystanie z palety pełnej funkcjonalności C#.
Możesz podać sprawdzania poprawności, różnych ułatwień dostępu, obliczanie leniwe lub żadnych wymagań dotyczących scenariuszy, należy.
