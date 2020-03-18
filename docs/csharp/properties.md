---
title: Właściwości
description: Dowiedz się więcej o właściwościach języka C#, które obejmują funkcje sprawdzania poprawności, obliczone wartości, ocenę z opóźnieniem i powiadomienia o zmianie właściwości.
ms.technology: csharp-fundamentals
ms.date: 04/25/2018
ms.openlocfilehash: bda8a4f58f71b57248296dd4ba9f9bf4cbed40d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399414"
---
# <a name="properties"></a>Właściwości

Właściwości są pierwszej klasy obywateli w języku C#. Język definiuje składnię, która umożliwia deweloperom napisać kod, który dokładnie wyraża ich intencji projektu.

Właściwości zachowują się jak pola, gdy są one dostępne.
Jednak w przeciwieństwie do pól właściwości są implementowane za pomocą akcesorów, które definiują instrukcje wykonywane, gdy właściwość jest dostępna lub przypisana.

## <a name="property-syntax"></a>Składnia właściwości

Składnia właściwości jest naturalnym rozszerzeniem pól. Pole definiuje lokalizację magazynu:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Definicja właściwości zawiera deklaracje dla `get` a i `set` akcesor, który pobiera i przypisuje wartość tej właściwości:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Powyższa składnia jest składnią *właściwości auto.* Kompilator generuje lokalizację magazynu dla pola, które tworzy tworzenie zapasowe właściwości. Kompilator implementuje również `get` treść `set` i akcesorów.

Czasami należy zainicjować właściwość do wartości innej niż domyślna dla jej typu.  C# umożliwia, że przez ustawienie wartości po nawias zamykający dla właściwości. Może wolisz wartość początkową `FirstName` dla właściwości jest `null`pusty ciąg, a nie . Należy określić, że jak pokazano poniżej:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Konkretne inicjowanie jest najbardziej przydatne dla właściwości tylko do odczytu, jak widać w dalszej części tego artykułu.

Możesz również samodzielnie zdefiniować miejsce do magazynowania, jak pokazano poniżej:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Gdy implementacja właściwości jest pojedynczym wyrażeniem, można użyć *elementów członkowskich zabudowanych wyrażeniem* dla programu rozdzielania lub ustawiania:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Ta uproszczona składnia będzie używana w stosownych przypadkach w tym artykule.

Definicja właściwości pokazana powyżej jest właściwością odczytu i zapisu. Zwróć `value` uwagę na słowo kluczowe w set akcesor. Akcesor `set` zawsze ma `value`jeden parametr o nazwie . Akcesor `get` musi zwrócić wartość, która jest konwertowalna do typu właściwości (w`string` tym przykładzie).

To podstawy składni. Istnieje wiele różnych odmian, które obsługują różne idiomy projektowe. Przyjrzyjmy się i poznajmy opcje składni dla każdego z nich.

## <a name="scenarios"></a>Scenariusze

Powyższe przykłady wykazały jeden z najprostszych przypadków definicji właściwości: właściwość odczytu i zapisu bez sprawdzania poprawności. Zapisując odpowiedni kod w `get` `set` akcesorach i, można utworzyć wiele różnych scenariuszy.

### <a name="validation"></a>Sprawdzanie poprawności

Można napisać kod `set` w akcesor, aby upewnić się, że wartości reprezentowane przez właściwość są zawsze prawidłowe. Załóżmy na przykład, `Person` że jedna reguła dla klasy jest taka, że nazwa nie może być pusta ani biała. Można napisać, że w następujący sposób:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Powyższy przykład można uprościć`throw` za pomocą wyrażenia jako część sprawdzania poprawności modułu ustawiającego właściwości:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

Powyższy przykład wymusza regułę, że imię nie może być puste lub biały znak. Jeśli deweloper pisze

```csharp
hero.FirstName = "";
```

To zadanie rzuca `ArgumentException`. Ponieważ akcesor zestawu właściwości musi mieć typ zwracania void, zgłaszasz błędy w akcesorze zestawu, zgłaszając wyjątek.

Tę samą składnię można rozszerzyć na wszystko, co jest potrzebne w scenariuszu. Można sprawdzić relacje między różnymi właściwościami lub sprawdzić poprawność w stosunku do wszelkich warunków zewnętrznych. Wszystkie prawidłowe instrukcje C# są prawidłowe w akcesor właściwości.

### <a name="read-only"></a>Tylko odczyt

Do tego momentu wszystkie definicje właściwości, które widziałeś są właściwości odczytu/zapisu z akcesorów publicznych. To nie jedyna prawidłowa dostępność dla właściwości.
Można utworzyć właściwości tylko do odczytu lub nadać inny dostęp do zestawu i uzyskać akcesory. Załóżmy, że klasa `Person` powinna tylko `FirstName` włączyć zmianę wartości właściwości z innych metod w tej klasie. Można nadać ustawioną `public`dostępność akcesora `private` zamiast:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Teraz `FirstName` właściwość jest dostępna z dowolnego kodu, ale można przypisać tylko z `Person` innego kodu w klasie.

Można dodać dowolny modyfikator dostępu ograniczającego do zestawu lub uzyskać akcesorów. Każdy modyfikator dostępu, który można umieścić na poszczególnych akcesora musi być bardziej ograniczona niż modyfikator dostępu w definicji właściwości. Powyżej jest legalne, `FirstName` ponieważ `public`nieruchomość jest , `private`ale zestaw akcesor jest . Nie można zadeklarować `private` właściwość `public` z akcesorem. Deklaracje majątkowe `protected`mogą `internal` `protected internal`być również `private`deklarowane , , lub nawet .

Jest to również legalne, aby umieścić `get` bardziej restrykcyjny modyfikator na akcesor. Na przykład można mieć `public` właściwość, ale `get` ograniczyć `private`akcesor do . Ten scenariusz jest rzadko wykonywany w praktyce.

Można również ograniczyć modyfikacje do właściwości, dzięki czemu można ustawić tylko w konstruktorze lub inicjatora właściwości. Klasę można `Person` zmodyfikować w następujący sposób:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Ta funkcja jest najczęściej używana do inicjowania kolekcji, które są udostępniane jako właściwości tylko do odczytu:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Właściwości obliczeniowe

Właściwość nie musi po prostu zwracać wartość pola elementu członkowskiego. Można utworzyć właściwości, które zwracają obliczoną wartość. Rozwińmy obiekt, `Person` aby zwrócić pełną nazwę, obliczoną przez łączenie imienia i nazwiska:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

W powyższym przykładzie użyto funkcji [interpolacji ciągu](./language-reference/tokens/interpolated.md) do utworzenia sformatowanego ciągu dla pełnej nazwy.

Można również użyć *elementu członkowskiego opartego na wyrażeniu,* który `FullName` zapewnia bardziej zwięzły sposób tworzenia właściwości obliczeniowej:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*Elementy członkowskie zabudowane wyrażeniem* używają składni *wyrażenia lambda* do definiowania metod zawierających pojedyncze wyrażenie. W tym miejscu to wyrażenie zwraca pełną nazwę dla obiektu osoby.

### <a name="cached-evaluated-properties"></a>Buforowane oceniane właściwości

Można mieszać pojęcie właściwości obliczeniowej z magazynu i utworzyć *buforowane oceniane właściwości*.  Na przykład można zaktualizować `FullName` właściwość, tak aby formatowanie ciągu miało miejsce tylko przy pierwszym dostępie:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Powyższy kod zawiera jednak błąd. Jeśli kod aktualizuje wartość `FirstName` `LastName` lub właściwość, wcześniej `fullName` oceniane pole jest nieprawidłowe. `set` Można zmodyfikować akcesory `FirstName` i `fullName` `LastName` właściwości tak, aby pole jest obliczane ponownie:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Ta ostateczna wersja `FullName` ocenia właściwość tylko wtedy, gdy jest to potrzebne.
Jeśli wcześniej obliczona wersja jest prawidłowa, jest używana. Jeśli inna zmiana stanu unieważni poprzednio obliczoną wersję, zostanie ponownie obliczona. Deweloperzy, którzy używają tej klasy nie trzeba znać szczegóły implementacji. Żadna z tych zmian wewnętrznych nie wpływa na użycie obiektu Person. Jest to kluczowa przyczyna używania właściwości do uwidaczniania elementów członkowskich danych obiektu.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Dołączanie atrybutów do właściwości zaimplementowanych automatycznie

Począwszy od języka C# 7.3 atrybuty pola można dołączyć do wygenerowanego przez kompilatora pola zapasowego we właściwościach implementowanych automatycznie. Rozważmy na przykład poprawkę `Person` do klasy, która `Id` dodaje unikatową właściwość całkowitą.
Można napisać`Id` właściwość przy użyciu właściwości auto-implemented, ale projekt `Id` nie powoduje utrwalenia właściwości. Można <xref:System.NonSerializedAttribute> dołączyć tylko do pól, a nie właściwości. Do pola <xref:System.NonSerializedAttribute> zapasowego `Id` właściwości można dołączyć za `field:` pomocą specyfikatora atrybutu, jak pokazano w poniższym przykładzie:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Ta technika działa dla dowolnego atrybutu dołączonego do pola zapasowego we właściwości implementowane automatycznie.

### <a name="implementing-inotifypropertychanged"></a>Implementowanie iNotifyPropertyChanged

Końcowy scenariusz, w którym należy napisać kod w akcesor właściwości jest obsługa interfejsu używanego <xref:System.ComponentModel.INotifyPropertyChanged> do powiadamiania klientów powiązania danych, że wartość została zmieniona. Gdy wartość właściwości zmienia się, obiekt <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> wywołuje zdarzenie, aby wskazać zmianę. Biblioteki powiązania danych z kolei aktualizują elementy wyświetlania na podstawie tej zmiany. Poniższy kod pokazuje, jak `INotifyPropertyChanged` można `FirstName` zaimplementować dla właściwości tej klasy osoby.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

Operator `?.` jest nazywany *operatorem warunkowym zerowym*. Sprawdza odniesienie zerowe przed dokonaniem oceny prawej strony operatora. Wynik końcowy jest, że jeśli nie `PropertyChanged` ma żadnych subskrybentów zdarzenia, kod, aby podnieść zdarzenie nie jest wykonywana. To rzucać `NullReferenceException` bez tej kontroli w tym przypadku. Aby uzyskać więcej [`events`](events-overview.md)informacji, zobacz . W tym przykładzie `nameof` użyto również nowego operatora do konwersji z symbolu nazwy właściwości na jego reprezentację tekstu.
Za `nameof` pomocą można zmniejszyć błędy, gdy błędnie wpisał nazwę właściwości.

Ponownie implementowanie <xref:System.ComponentModel.INotifyPropertyChanged> jest przykładem przypadku, w którym można napisać kod w akcesorów do obsługi scenariuszy, których potrzebujesz.

## <a name="summing-up"></a>Podsumowanie

Właściwości są formą inteligentnych pól w klasie lub obiekcie. Z zewnątrz obiektu pojawiają się one jak pola w obiekcie. Jednak właściwości można zaimplementować przy użyciu pełnej palety funkcji języka C#.
Można podać sprawdzanie poprawności, różne ułatwienia dostępu, oceny z opóźnieniem lub wszelkie wymagania, których potrzebują scenariusze.
