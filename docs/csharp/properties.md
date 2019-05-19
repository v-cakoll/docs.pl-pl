---
title: Właściwości
description: Dowiedz się więcej o C# właściwości, które zawierają funkcje sprawdzania poprawności, obliczonych wartości, obliczanie z opóźnieniem i zmienić właściwości powiadomienia.
ms.date: 04/25/2018
ms.openlocfilehash: e8b6955da1f36673962339785b0bfb012343acf8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878279"
---
# <a name="properties"></a>Właściwości

Właściwości są obywatelami pierwszej klasy w C#. Język definiuje składnia, która umożliwia programistom pisanie kodu, który dokładnie odzwierciedla ich celem projektu.

Właściwości zachowują się jak pola, gdy są one używane.
Jednak w przeciwieństwie do pola, właściwości są implementowane za pomocą metody dostępu, które definiują instrukcje wykonania, gdy właściwość jest dostępny lub przypisane.

## <a name="property-syntax"></a>Składnia właściwości

Składnia właściwości jest naturalnym rozszerzeniem pola. Pole definiuje lokalizację magazynu:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Definicja właściwości zawiera deklaracje dla `get` i `set` metodę dostępu, która pobiera i przypisuje wartość tej właściwości:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Składnia powyżej jest *auto-właściwości* składni. Kompilator generuje lokalizację magazynu dla pola, które tworzy kopię zapasową właściwości. Kompilator implementuje również treści `get` i `set` metod dostępu.

Czasami musisz zainicjować właściwość, która ma wartość inną niż domyślna dla tego typu.  C#Umożliwia, ustawiając wartość po zamykającego nawiasu klamrowego dla właściwości. Lepiej wartość początkową dla `FirstName` właściwość, aby być ciągiem pustym zamiast `null`. Określ, jak pokazano poniżej:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Inicjowanie określonych jest najbardziej przydatne do właściwości tylko do odczytu, jak zobaczysz w dalszej części tego artykułu.

Można również definiować magazynu samodzielnie, jak pokazano poniżej:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Jeśli implementacja właściwości jest pojedyncze wyrażenie, możesz użyć *elementy członkowskie z wyrażeniem* dla metody pobierającej lub ustawiającej:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

To uproszczoną składnię będzie używany, gdy to stosowne, w tym artykule.

Definicja właściwości przedstawionych powyżej jest właściwością odczytu i zapisu. Zwróć uwagę, słowo kluczowe `value` w metodzie dostępu set. `set` Akcesor zawsze ma jeden parametr o nazwie `value`. `get` Dostępu musi zwracać wartość, która jest konwertowany na typ właściwości (`string` w tym przykładzie).

To podstawy składni. Istnieje wiele różnych odmiany, które obsługują szereg idiomy innego projektu. Umożliwia Eksplorowanie i Dowiedz się opcje składnię dla każdego.

## <a name="scenarios"></a>Scenariusze

Powyższe przykłady wykazało, że jeden z najprostszym przypadków definicji właściwości: właściwości odczytu / zapisu o nie nastąpi sprawdzanie poprawności. Pisząc kod chcesz w `get` i `set` metod dostępu, możesz utworzyć wiele różnych scenariuszy.

### <a name="validation"></a>Walidacja

Można wpisać kod w `set` metody dostępu, upewnij się, że wartości, reprezentowane przez właściwość zawsze prawidłowe. Na przykład, załóżmy, że jedna reguła dla `Person` klasa jest, że nazwa nie może być puste lub biały znak. Czy zapisać, w następujący sposób:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Poprzedni przykład można uprościć za pomocą`throw` wyrażenia w ramach sprawdzania poprawności metody ustawiającej właściwość:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

W powyższym przykładzie wymusza, zasada, że imię nie może być pusta lub biały znak. Jeśli Deweloper zapisuje

```csharp
hero.FirstName = "";
```

Przypisanie zgłasza `ArgumentException`. Ponieważ dostępu set z właściwość musi zwracać typ void, możesz zgłaszać błędy w metody dostępu set, zostanie zgłoszony wyjątek.

Możesz rozszerzyć ten tej samej składni, aby wszystkie potrzebne w tym scenariuszu. Możesz sprawdzić relacje między różnymi właściwościami lub przeprowadzić walidacji względem żadnych warunków zewnętrznych. Dowolne, prawidłowe C# są prawidłowe w metoda dostępu do właściwości.

### <a name="read-only"></a>tylko do odczytu

Do tej pory wszystkie definicje właściwości przejrzanych są publiczne metody dostępu właściwości odczytu/zapisu. To nie jedyne prawidłowe ułatwień dostępu dla właściwości.
Można utworzyć właściwości tylko do odczytu, lub oferowanie różnej dostępności zestawu i pobieranie metod dostępu. Załóżmy, że Twoje `Person` klasy należy włączyć tylko zmiana wartości `FirstName` właściwości z innych metod w tej klasie. Można nadać metody dostępu set `private` ułatwień dostępu, zamiast `public`:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Teraz `FirstName` właściwości są dostępne z dowolnego kodu, ale można przypisać tylko z innym kodem `Person` klasy.

Można dodać żadnych modyfikator dostępu ograniczające albo zestaw lub uzyskaj metod dostępu. Wszelkie modyfikator dostępu, które można umieścić na poszczególne metody dostępu musi być bardziej ograniczone niż modyfikator dostępu dla definicji właściwości. Powyżej jest legalna ponieważ `FirstName` właściwość `public`, ale metody dostępu set `private`. Nie można zadeklarować `private` właściwość o `public` metody dostępu. Deklaracje właściwości mogą być także zadeklarowane `protected`, `internal`, `protected internal`, lub nawet `private`.

Jest również dozwolone umieść modyfikator bardziej restrykcyjne na `get` metody dostępu. Na przykład można mieć `public` właściwości, ograniczając jednocześnie `get` metody dostępu `private`. Ten scenariusz rzadko odbywa się w praktyce.

Można również ograniczyć modyfikacje właściwości, tak że można ustawić tylko w konstruktorze lub inicjatorze właściwości. Możesz zmodyfikować `Person` klasy, więc w następujący sposób:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Ta funkcja jest najczęściej używana do inicjowania kolekcji, które są widoczne jako właściwości tylko do odczytu:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Obliczone właściwości

Właściwość nie trzeba zwrócić wartość pola elementu członkowskiego. Można utworzyć właściwości, które zwracają obliczoną wartością. Możemy rozwinąć `Person` obiekt do zwrotu pełną nazwę, obliczana przez złączenie imiona i nazwiska:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

Przykład powyżej używa [Interpolacja ciągów](../csharp/language-reference/tokens/interpolated.md) funkcję, aby utworzyć sformatowany ciąg, aby uzyskać pełną nazwę.

Można również użyć *wyrażeniem składowej*, który zapewnia bardziej zwięzły sposób tworzenia obliczone `FullName` właściwości:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*Elementy członkowskie z wyrażeniem* użyj *wyrażenia lambda* Składnia służąca do definiowania metod, które zawierać pojedyncze wyrażenie. W tym miejscu to wyrażenie zwraca pełną nazwę obiektu osoba.

### <a name="cached-evaluated-properties"></a>Właściwości ocenianą pamięci podręcznej

Możesz mieszać koncepcji obliczona właściwość z magazynu i utworzyć *buforowane szacowanych*.  Na przykład, można zaktualizować `FullName` właściwość tak, aby tylko formatowanie ciągów wystąpiły po raz pierwszy uzyskano go:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Powyższy kod zawiera usterkę, mimo że. Jeśli kod aktualizuje wartość jednej `FirstName` lub `LastName` właściwość, wcześniej ocenianą `fullName` pole jest nieprawidłowe. Możesz zmodyfikować `set` metod dostępu `FirstName` i `LastName` właściwość tak, aby `fullName` pole jest obliczane ponownie:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Daje w wyniku tej wersji ostatecznej `FullName` właściwości tylko wtedy, gdy jest to wymagane.
Jeśli poprzednio obliczonej wersji jest prawidłowy, jest używany. Jeśli inna zmiana stanu unieważnia wcześniej obliczeniowe wersji, zostaną obliczone go ponownie. Deweloperzy korzystający z tej klasy nie trzeba wiedzieć, szczegółowe informacje o implementacji. Żadna z tych wewnętrznych zmian wpływa na korzystanie z obiektu osoby. To jest powód klucza do używania właściwości do udostępnienia danych elementów członkowskich obiektu.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Trwa dołączanie atrybutów, które mają automatycznie implementowanych właściwości

Począwszy od C# 7.3, atrybuty pól mogą być dołączane do pola pomocniczego wygenerowanego przez kompilator automatycznie implementowane właściwości. Na przykład, należy wziąć pod uwagę poprawkę do `Person` klasę, która dodaje całkowitą liczbą unikatowych `Id` właściwości.
Piszesz`Id` właściwości przy użyciu automatycznie implementowanych właściwości, ale projekt, nie wywołuje potrzeby utrwalania `Id` właściwości. <xref:System.NonSerializedAttribute> Mogą być dołączane tylko do pól, a nie właściwości. Możesz dołączyć <xref:System.NonSerializedAttribute> na pole zapasowe dla `Id` właściwości przy użyciu `field:` Specyfikator atrybutu, jak pokazano w poniższym przykładzie:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Ta metoda działa w przypadku każdego atrybutu, który można dołączyć do pola pomocniczego na automatycznie implementowane właściwości.

### <a name="implementing-inotifypropertychanged"></a>Implementing INotifyPropertyChanged

Końcowe scenariusz, w których trzeba napisać kod w metodzie dostępu właściwości służy do obsługi <xref:System.ComponentModel.INotifyPropertyChanged> interfejs używany do powiadamiania klientów powiązania danych, których wartość została zmieniona. Po zmianie wartości właściwości, wywołuje obiekt <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> zdarzenie, aby wskazać zmianę. Dane, tworzenie powiązań bibliotek, z kolei zaktualizować wyświetlanych elementów w oparciu o zmiany. Poniższy kod pokazuje, jak możesz również zaimplementować `INotifyPropertyChanged` dla `FirstName` właściwości tej klasy osoby.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

`?.` Operator jest nazywany *operatora warunkowego wartości null*. Sprawdza odwołanie o wartości null ewaluacją po prawej stronie operatora. Wynik końcowy jest to, że w przypadku subskrybentów do `PropertyChanged` zdarzeń, kod, aby wygenerować zdarzenie nie jest wykonywany. Będzie ona zgłaszają `NullReferenceException` bez to sprawdzać w takiej sytuacji. Aby uzyskać więcej informacji, zobacz [`events`](events-overview.md). W tym przykładzie użyto również nowe `nameof` operatora konwersji z symboli nazwy właściwości na jego reprezentację tekstową.
Za pomocą `nameof` można zmniejszyć liczbę błędów, w którym błędnie wpisano nazwę właściwości.

Implementowanie ponownie <xref:System.ComponentModel.INotifyPropertyChanged> jest przykładem przypadek, w którym można wpisać kod w swojej metody dostępu na potrzeby scenariuszy należy.

## <a name="summing-up"></a>Podsumowanie

Właściwości są formą inteligentne pola w klasie lub obiektu. Z poza nim, są wyświetlane takie jak pola obiektu. Jednak właściwości można zaimplementować przy użyciu pełnej paletę C# funkcji.
Możesz podać sprawdzania poprawności, różnej dostępności, obliczanie z opóźnieniem lub wszelkie wymagania potrzebnych dla swoich scenariuszy.
