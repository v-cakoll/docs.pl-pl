---
title: Właściwości
description: Dowiedz się więcej o języku C# właściwości, które obejmują funkcje sprawdzania poprawności, obliczana wartości, obliczanie leniwe i zmienić właściwości powiadomienia.
ms.date: 04/25/2018
ms.openlocfilehash: d4fa7b6117bec63c41318dd4bcc3850ce55a5907
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="properties"></a>Właściwości

Właściwości są pierwszej klasie obywateli w języku C#. Język definiuje składnię, która umożliwia deweloperom pisanie kodu, który dokładnie odzwierciedla cele ich projektu.

Właściwości przypominają pola, gdy są one używane.
Jednak w przeciwieństwie do pola, właściwości są implementowane przy użyciu metody dostępu definiujące instrukcje wykonywane, gdy właściwość jest dostępne lub przypisany.

## <a name="property-syntax"></a>Składnia właściwości

Składnia właściwości jest stanowi naturalne rozszerzenie do pól. Pole określa lokalizację magazynu:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Definicja właściwości zawiera deklaracje dla `get` i `set` dostępu, która pobiera i przypisuje wartość tej właściwości:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Składnia pokazanym powyżej jest *automatycznie właściwości* składni. Kompilator generuje lokalizację przechowywania dla pola, które wykonuje kopię zapasową właściwości. Kompilator implementuje również treści `get` i `set` metody dostępu.

Czasami należy zainicjować właściwość na wartość inną niż domyślna dla jego typu.  C# umożliwia który przez ustawienie wartości nawiasem zamykającym dla właściwości. Możesz wybrać wartość początkową `FirstName` właściwość jako ciąg pusty zamiast `null`. Należy wprowadzić ten w sposób przedstawiony poniżej:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Inicjowanie określonych jest najbardziej przydatny w przypadku właściwości tylko do odczytu, jak można zauważyć w dalszej części tego artykułu.

Istnieje także możliwość zdefiniowania magazynu użytkownika, jak pokazano poniżej:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Jeśli implementacja właściwości jest jedno wyrażenie, możesz użyć *zabudowanych wyrażenia elementów członkowskich* metody pobierającej lub ustawiającej:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Tej składni uproszczoną będą używane, jeśli to możliwe, w tym artykule.

Definicja właściwości pokazanym powyżej jest właściwością odczytu i zapisu. Zwróć uwagę, słowo kluczowe `value` w metody dostępu set. `set` Akcesor zawsze ma jeden parametr o nazwie `value`. `get` Akcesora musi zwracać wartość do przekonwertowania na typ właściwości (`string` w tym przykładzie).

To podstawy składni. Istnieje wiele różnych odmiany, które obsługują szereg idioms inny projekt. Umożliwia Eksplorowanie i Dowiedz się dla każdej opcji składni.

## <a name="scenarios"></a>Scenariusze

Powyższych przykładach pokazano, co najprostszym przypadków definicji właściwości: właściwości odczytu / zapisu o nie sprawdzania poprawności. Pisanie kodu mają w `get` i `set` metody dostępu, możesz utworzyć wiele różnych scenariuszy.

### <a name="validation"></a>Walidacja

Możesz pisać kod `set` dostępu, aby upewnić się, czy wartości reprezentowane przez właściwość zawsze są prawidłowe. Na przykład, załóżmy, że jedną regułę `Person` klasy jest, że nazwa nie może być puste lub biały znak. Czy zapisz ją w następujący sposób:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Poprzedni przykład, można uprościć przy użyciu`throw` wyrażenia w ramach sprawdzania poprawności metody ustawiającej właściwość:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

W powyższym przykładzie wymusza zasadę czy imię nie może być puste lub biały znak. Jeśli zapisuje dewelopera

```csharp
hero.FirstName = "";
```

Przypisanie zgłasza `ArgumentException`. Ponieważ metodą dostępu set właściwości musi mieć zwracanego typu void, należy włączyć raportowanie błędów metody dostępu set przez Zgłaszanie wyjątku.

Można rozszerzyć tej samej składni na niczego wymagane w danym scenariuszu. Sprawdź relacje między inne właściwości lub sprawdzania poprawności żadnych warunków zewnętrznych. Wszystkie prawidłowe C# instrukcje są prawidłowe w akcesor właściwości.

### <a name="read-only"></a>tylko do odczytu

Do tego momentu wszystkich przejrzanych definicji właściwości są właściwości odczytu/zapisu z metod dostępu publicznego. To nie jest jedyną poprawną ułatwień dostępu dla właściwości.
Można utworzyć właściwości tylko do odczytu, lub zapewniają różne ułatwień dostępu w zestawie i metody dostępu get. Załóżmy, że Twoje `Person` klasy należy włączyć tylko zmiana wartości `FirstName` właściwości z innych metod tej klasy. Możesz podać metody dostępu set `private` dostępności zamiast `public`:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Teraz `FirstName` właściwości są dostępne z kodu, ale można go przypisać tylko z innego kodu w `Person` klasy.

Można dodać żadnych modyfikator dostępu ograniczające albo zestaw lub metody dostępu get. Wszelkie modyfikator dostępu umieszczony na poszczególnych akcesora musi być bardziej ograniczone niż modyfikatora dostępu w definicji właściwości. Powyższe jest dozwolony ponieważ `FirstName` właściwość jest `public`, ale set jest `private`. Nie można deklarować `private` właściwości o `public` metody dostępu. Deklaracje właściwości również mogą być deklarowane `protected`, `internal`, `protected internal`, a nawet `private`.

Jest również prawne do umieszczenia na bardziej restrykcyjne modyfikator `get` metody dostępu. Na przykład można mieć `public` właściwości, ograniczając jednocześnie `get` metody dostępu `private`. W tym scenariuszu rzadko odbywa się w praktyce.

Można również ograniczyć modyfikacji właściwości, dzięki czemu można ustawić tylko w konstruktorze lub inicjatorze właściwości. Można zmodyfikować `Person` klasy, w następujący sposób:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Ta funkcja jest najczęściej używana do inicjowania kolekcji, które są dostępne jako właściwości tylko do odczytu:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Właściwości obliczanej

Właściwość nie trzeba po prostu zwrócić wartość pola elementu członkowskiego. Można utworzyć właściwości, które zwracają obliczoną wartość. Umożliwia rozwijanie `Person` obiektu do zwrócenia pełną nazwę, obliczone przez łączenie imiona i nazwiska:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

Przykład powyżej używa [ciągu interpolacji](../csharp/language-reference/tokens/interpolated.md) funkcję, aby utworzyć ciąg sformatowany dla pełnej nazwy.

Można również użyć *zabudowanych wyrażenie elementu członkowskiego*, który zapewnia bardziej zwięzły sposób utworzyć obliczone `FullName` właściwości:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*Członkowie zabudowanych wyrażenie* użyj *wyrażenia lambda* składni, aby zdefiniować metody, które zawierają jedno wyrażenie. W tym miejscu tego wyrażenia zwraca pełną nazwę dla obiekt osoby.

### <a name="cached-evaluated-properties"></a>Właściwości obliczane w pamięci podręcznej

Można mieszać pojęcie właściwości obliczanej z magazynem i utworzyć *buforowane właściwości szacowanych*.  Na przykład można zaktualizować `FullName` właściwości tak, aby tylko ciągu formatowania wystąpił uzyskiwał został po raz pierwszy:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Powyższy kod zawiera usterkę, mimo że. Jeśli kod aktualizuje wartość albo `FirstName` lub `LastName` właściwości, wcześniej ocenionych `fullName` pole jest nieprawidłowe. Możesz zmodyfikować `set` metod dostępu `FirstName` i `LastName` właściwości, aby `fullName` pola jest obliczane ponownie:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Wynikiem tej wersji ostatecznej `FullName` właściwość tylko w razie potrzeby.
Jeśli poprzednio obliczonej wersji jest prawidłowy, jest używany. Jeśli inna zmiana stanu unieważnia poprzednio obliczonej wersji, zostaną obliczone go ponownie. Deweloperzy korzystający z tej klasy nie trzeba znać szczegóły implementacji. Żadna z tych zmian wewnętrzny wpływa na użycie obiektu osoby. To klucza Przyczyna przy użyciu właściwości do udostępnienia danych elementów członkowskich obiektu.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Dołączanie atrybuty do właściwości zaimplementowane automatycznie

Począwszy od 7.3 C#, atrybuty pól może zostać dołączona do pola zapasowy wygenerowanego przez kompilator automatycznie implementowane właściwości. Rozważmy na przykład zmiana `Person` klasy, która dodaje całkowitą liczbą unikatowych `Id` właściwości.
Możesz zapisać`Id` właściwości przy użyciu automatycznie implementowanych właściwości, ale projekt wymagają utrwalanie `Id` właściwości. <xref:System.NonSerializedAttribute> Może zostać dołączona tyko do pól, nie właściwości. Możesz dołączyć <xref:System.NonSerializedAttribute> do pola zapasowy `Id` właściwości przy użyciu `field:` Specyfikator atrybutu, jak pokazano w poniższym przykładzie:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Ta metoda działa w przypadku każdego atrybutu, który można dołączyć do pola zapasowy we właściwości zaimplementowane automatycznie.

### <a name="implementing-inotifypropertychanged"></a>Implementowanie interfejsu INotifyPropertyChanged

Końcowe scenariusz, w których należy napisać kod w metodzie dostępu właściwości służy do obsługi <xref:System.ComponentModel.INotifyPropertyChanged> interfejs używany do powiadamiania klientów powiązania danych, które wartość została zmieniona. Po zmianie wartości właściwości obiektu zgłasza <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> zdarzeń, aby wskazać zmianę. Powiązanie bibliotek, danych z kolei aktualizacji wyświetlanych elementów oparte na tej zmiany. Poniższy kod przedstawia sposób czy implementuje `INotifyPropertyChanged` dla `FirstName` właściwości tej klasy osoby.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

`?.` Operator jest nazywany *null operator warunkowy*. Sprawdza odwołanie o wartości null przed obliczeniem po prawej stronie operatora. W rezultacie jest to, że jeśli nie ma żadnych subskrybentów `PropertyChanged` zdarzeń, kod, aby zgłosić zdarzenie nie jest wykonywana. Go spowoduje zgłoszenie `NullReferenceException` bez to w takim przypadku Sprawdź. Aby uzyskać więcej informacji, zobacz [`events`](delegates-events.md). W tym przykładzie również używa nowego `nameof` operatora konwersji z symbol nazwa właściwości jego reprezentacja tekstowa.
Przy użyciu `nameof` może zmniejszyć liczbę błędów, gdzie ma została błędnie wpisana nazwa właściwości.

Implementowanie ponownie <xref:System.ComponentModel.INotifyPropertyChanged> przykładem przypadek, w którym można napisać kod w metod dostępu do sieci na potrzeby obsługi scenariuszy należy.

## <a name="summing-up"></a>Podsumowanie

Właściwości są formę inteligentne pola w klasie lub obiektu. Z poza obiekt, pojawią się one takich jak pola obiektu. Jednak właściwości można zaimplementować korzystanie z palety pełnej funkcjonalności C#.
Możesz podać sprawdzania poprawności, różnych ułatwień dostępu, obliczanie leniwe lub żadnych wymagań dotyczących scenariuszy, należy.
