---
title: Zaktualizuj bazę kodu w celu użycia typów referencyjnych dopuszczających wartości null
description: Wybierz najlepszą strategię uaktualniania bazy kodu do używania typów referencyjnych dopuszczających wartość null.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5909eb9ffe1f5398fc2eb74848b82f8fe9516548
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975334"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizowanie bibliotek do używania typów referencyjnych dopuszczających wartości null i przekazywanie reguł dopuszczających wartość null do wywoływania

Dodanie [typów referencyjnych dopuszczających wartość null](nullable-references.md) oznacza, czy można zadeklarować, czy `null` wartość jest dozwolona, czy nieoczekiwana dla każdej zmiennej. Ponadto można zastosować wiele atrybutów `AllowNull`:, `DisallowNull`, `MaybeNull` `NotNull` `NotNullWhen`,,, `MaybeNullWhen`, i `NotNullIfNotNull` aby całkowicie opisać Stany null argumentu i wartości zwracane. Zapewnia to doskonałe środowisko podczas pisania kodu. Są wyświetlane ostrzeżenia, jeśli zmienna niedopuszczający wartości null może być `null`ustawiona na wartość. Są wyświetlane ostrzeżenia, jeśli zmienna dopuszczająca wartość null nie jest sprawdzana przed usunięciem odwołania do niej. Aktualizowanie bibliotek może zająć trochę czasu, ale Payoffs. Więcej informacji udostępnianych kompilatorowi o tym, *kiedy* `null` wartość jest dozwolona lub zabroniona, użytkownicy otrzymają lepszych ostrzeżeń dotyczących interfejsu API. Zacznijmy od znanego przykładu. Wyobraź sobie, że biblioteka zawiera następujący interfejs API do pobrania ciągu zasobu:

```csharp
bool TryGetMessage(string key, out string message)
```

Poprzedni przykład jest zgodny ze znajomym `Try*` wzorcem w programie .NET. Istnieją dwa argumenty odwołania dla tego interfejsu API: `key` i `message` parametru. Ten interfejs API ma następujące reguły dotyczące wartości null tych argumentów:

- Obiekty wywołujące nie `null` powinny być przekazywane jako `key`argument dla elementu.
- Obiekty wywołujące mogą przekazywać zmienną, której `null` wartość jest argumentem `message`dla.
- Jeśli `TryGetMessage` Metoda zwraca `true`, wartość `message` nie jest równa null. Jeśli wartość zwracana jest `false,` wartością parametru `message` (i jego stan zerowy) ma wartość null.

Reguła dla `key` może być całkowicie wyrażona przez typ zmiennej: `key` powinien być typem referencyjnym, który nie dopuszcza wartości null. `message` Parametr jest bardziej skomplikowany. Umożliwia `null` jako argument, ale gwarantuje, że w przypadku powodzenia ten `out` argument nie ma wartości null. W tych scenariuszach potrzebujesz bogatszego słownictwa do opisywania oczekiwań.

Aktualizacja biblioteki dla odwołań do wartości null wymaga więcej niż `?` przestawianie niektórych zmiennych i nazw typów. Powyższy przykład pokazuje, że należy przejrzeć interfejsy API i uwzględnić oczekiwania dla każdego argumentu wejściowego. Należy wziąć pod uwagę gwarancje wartości zwracanej, `out` a `ref` także wszystkie lub argumenty dla zwracanej metody. Następnie Przekaż te reguły do kompilatora, a kompilator dostarczy ostrzeżenia, gdy wywołujący nie przestrzegają tych reguł.

To działanie jest czasochłonne. Zacznijmy od strategii, aby dowiedzieć się, jak Twoja biblioteka lub aplikacja doznała wartości null, a także zrównoważyć inne wymagania i elementy dostarczane. Zobaczysz, jak zrównoważyć bieżące programowanie, włączając typy referencyjne dopuszczające wartość null. Nauczysz się wyzwań dla definicji typów ogólnych. Dowiesz się, jak zastosować atrybuty do opisywania warunków wstępnych i postanowień dotyczących poszczególnych interfejsów API.

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Wybierz strategię dla typów referencyjnych dopuszczających wartość null

Pierwszy wybór polega na tym, czy typy odwołań dopuszczające wartość null mają być domyślnie włączone czy wyłączone. Istnieją dwie strategie:

- Włącz typy referencyjne dopuszczające wartość null dla całego projektu i wyłącz je w kodzie, który nie jest gotowy.
- Włącz tylko typy referencyjne dopuszczające wartość null dla kodu, który jest oznaczony adnotacją dla typów referencyjnych dopuszczających wartość null.

Pierwsza strategia działa najlepiej, gdy dodajesz inne funkcje do biblioteki, gdy zaktualizujesz ją do typów referencyjnych dopuszczających wartość null. Cały nowy projekt ma świadomość dopuszczający wartość null. Gdy aktualizujesz istniejący kod, włączasz typy odwołań do wartości null w tych klasach.

Postępując zgodnie z pierwszą strategią, wykonaj następujące czynności:

1. Włącz typy referencyjne dopuszczające wartość null dla całego projektu `<Nullable>enable</Nullable>` przez dodanie elementu do plików *csproj* .
1. Dodaj `#nullable disable` pragmę do każdego pliku źródłowego w projekcie.
1. Podczas pracy nad każdym plikiem Usuń pragmę i rozwiąż wszelkie ostrzeżenia.

Ta pierwsza strategia ma więcej zadań z góry, aby dodać pragmę do każdego pliku. Korzyść polega na tym, że każdy nowy plik kodu dodany do projektu będzie miał włączoną wartość null. Każda nowa służbowa będzie mieć świadomość wartości null; należy zaktualizować tylko istniejący kod.

Druga strategia działa lepiej, jeśli biblioteka jest ogólnie stabilna, a głównym celem rozwoju jest przyjęcie typów referencyjnych dopuszczających wartość null. W przypadku dodawania adnotacji do interfejsów API należy włączyć typy odwołań do wartości null. Po zakończeniu włączać dla całego projektu typy referencyjne dopuszczające wartość null.

Postępując zgodnie z tą drugą strategią, należy wykonać następujące czynności:

1. Dodaj `#nullable enable` pragmę do pliku, dla którego chcesz wprowadzić wartość null.
1. Rozwiązywanie wszelkich ostrzeżeń.
1. Wykonaj te dwa pierwsze kroki, dopóki cała biblioteka nie doznała wartości null.
1. Włącz Typy dopuszczające wartość null dla całego projektu przez `<Nullable>enable</Nullable>` dodanie elementu do plików *csproj* .
1. Usuń `#nullable enable` dyrektywy pragma, ponieważ nie są już potrzebne.

Ta druga strategia ma mniej pracy z góry. Wadą jest to, że pierwsze zadanie podczas tworzenia nowego pliku to dodanie dyrektywy pragma i przekazanie jej do wartości null. Jeśli wszyscy deweloperzy w zespole zapomnili, nowy kod jest teraz w zaległości prac, aby umożliwić sobie dopełnienie kodu do wartości null.

Które z tych strategii są wybierane, zależy od tego, jak dużo aktywnego programowania odbywa się w projekcie. Im bardziej dojrzały i stabilny projekt, tym lepiej druga strategia. Im więcej funkcji jest opracowywanych, tym lepsza jest pierwsza strategia.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Czy ostrzeżenia o wartościach null wprowadzają istotne zmiany?

Przed włączeniem typów referencyjnych dopuszczających wartości null, zmienne są uznawane za *Oblivious dopuszczające wartość null*. Po włączeniu typów referencyjnych dopuszczających wartości null wszystkie te zmienne *nie dopuszczają wartości null*. Kompilator będzie wystawiał ostrzeżenia, jeśli te zmienne nie są zainicjowane do wartości innych niż null.

Inne prawdopodobnie Źródło ostrzeżeń ma zwracane wartości, gdy wartość nie została zainicjowana.

Pierwszym krokiem w rozwiązywaniu ostrzeżeń kompilatora jest użycie `?` adnotacji dla parametrów i zwracanych typów, aby wskazać, kiedy argumenty lub wartości zwracane mogą mieć wartość null. Gdy zmienne odwołania nie mogą mieć wartości null, oryginalna deklaracja jest poprawna. W takim przypadku cel nie tylko naprawi ostrzeżenia. Im bardziej istotny jest sposób, aby kompilator mógł zrozumieć zamiar dla potencjalnych wartości null. Podczas badania ostrzeżeń możesz przejść do następnej głównej decyzji dotyczącej biblioteki. Czy chcesz rozważyć modyfikowanie sygnatur interfejsów API, aby dokładniej komunikować swój projekt? Lepszym podpisem interfejsu API `TryGetMessage` dla metody analizowanej wcześniej mogą być:

```csharp
string? TryGetMessage(string key);
```

Wartość zwracana wskazuje powodzenie lub niepowodzenie i przenosi wartość w przypadku znalezienia wartości. W wielu przypadkach zmiana sygnatur interfejsów API może poprawić sposób, w jaki komunikują się wartości null.

Jednak w przypadku bibliotek publicznych lub bibliotek z dużymi bazami użytkowników można preferować nie wprowadzać żadnych zmian sygnatury interfejsu API. W tych przypadkach i innych wspólnych wzorców można zastosować atrybuty, aby dokładniej zdefiniować, kiedy może być `null`argument lub wartość zwracana. Bez względu na to, czy można zmienić powierzchnię interfejsu API, prawdopodobnie okaże się, że tylko adnotacje typu nie są `null` wystarczające do opisywania wartości argumentów lub zwracanych wartości. W tych przypadkach można zastosować atrybuty, aby dokładniej opisać interfejs API.

## <a name="attributes-extend-type-annotations"></a>Atrybuty rozszerzonego typu

Dodano kilka atrybutów w celu wyrażenia dodatkowych informacji o stanie null zmiennych. Wszystkie kod, który zapisano przed C# 8 wprowadziły typy odwołań dopuszczających wartości null, miał *wartość null Oblivious*. Oznacza to, że jakakolwiek zmienna typu referencyjnego może mieć wartość null, ale sprawdzanie wartości null nie jest wymagane. Gdy kod *dopuszcza wartość null*, te reguły zostaną zmienione. Typy odwołań nigdy nie powinny być `null` wartościami, a typy referencyjne dopuszczające wartość null `null` muszą zostać sprawdzone przed usunięciem odwołania.

Reguły interfejsów API mogą być bardziej skomplikowane, jak pokazano w scenariuszu `TryGetValue` interfejsu API. Wiele interfejsów API ma bardziej złożone reguły dla sytuacji, gdy zmienne mogą być `null`lub niemożliwe. W takich przypadkach atrybuty są używane do wyrażania tych reguł. Atrybuty opisujące semantykę interfejsu API znajdują się w artykule na temat [atrybutów, które wpływają na analizę wartości null](./language-reference/attributes/nullable-analysis.md).

## <a name="generic-definitions-and-nullability"></a>Definicje generyczne i wartości null

Poprawne powiadamianie o stanie null typów ogólnych i metod ogólnych wymaga szczególnej uwagi. Wynika to z faktu, że typ wartości null i typ referencyjny dopuszczający wartość null są zasadniczo różne. Jest `int?` synonimem dla `Nullable<int>`, w którym `string?` jest `string` atrybut dodany przez kompilator. Wynika to z tego, że kompilator nie może wygenerować `T?` poprawnego kodu `T` dla programu `class` bez znajomości `struct`if lub.

Nie oznacza to, że nie można użyć typu dopuszczającego wartości null (typu wartości lub typu referencyjnego) jako argumentu typu dla zamkniętego typu ogólnego. Oba `List<string?>` i `List<int?>` są prawidłowymi wystąpieniami `List<T>`.

Oznacza to, że nie można użyć `T?` w deklaracji klasy generycznej ani metody bez ograniczeń. Na przykład <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> nie zostanie zmieniony na Return `T?`. Ograniczenie to można przezwyciężyć, dodając `struct` ograniczenie `class` or. W przypadku każdego z tych ograniczeń kompilator wie, jak generować kod dla obu `T` i. `T?`

Możesz chcieć ograniczyć typy używane dla argumentu typu ogólnego jako niedopuszczające wartości null. Można to zrobić, dodając `notnull` ograniczenie dla tego argumentu typu. Po zastosowaniu tego ograniczenia argument typu nie może być typem dopuszczającym wartość null.

## <a name="late-initialized-properties-data-transfer-objects-and-nullability"></a>Właściwości późnego inicjowania, Transfer danych obiektów i wartości null

Wskazanie wartości null właściwości, które są opóźnione, oznacza ustawienie po konstrukcji, może wymagać specjalnego założenia, aby zapewnić, że Klasa nadal prawidłowo wyraża pierwotny cel projektowania.

Typy zawierające właściwości z opóźnieniem, takie jak obiekty Transfer danych (DTO), często są tworzone przez bibliotekę zewnętrzną, taką jak baza danych ORM (mapowanie relacyjne obiektów), Deserializator lub inny składnik, który automatycznie wypełnia właściwości z innego źródła.

Rozważmy następujące klasy DTO przed włączeniem typów referencyjnych dopuszczających wartości null, które reprezentują studenta:

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string VehicleRegistration { get; set; }
}
```

Celem projektowania (wskazywanym w tym przypadku `Required` przez atrybut) jest sugeruje, że w tym systemie właściwości `FirstName` i `LastName` są **obowiązkowe**, a tym samym nie wartości null.

`VehicleRegistration` Właściwość nie jest **obowiązkowa**, więc może mieć wartość null.

W przypadku włączania typów referencyjnych dopuszczających wartości null można wskazać DTO, które właściwości mogą dopuszczać wartości null, spójne z pierwotnym zamiarem:

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

Dla tego DTO jedyną właściwością, która może mieć wartość null ``VehicleRegistration``, jest.

Jednak kompilator generuje `CS8618` ostrzeżenia dla obu `FirstName` i `LastName`, wskazujący, że właściwości niedopuszczające wartości null są inicjowane.

Dostępne są trzy opcje, które umożliwiają rozwiązanie ostrzeżeń kompilatora w taki sposób, aby zachować oryginalny cel. Wszystkie te opcje są prawidłowe; należy wybrać ten, który najlepiej odpowiada stylowi kodowania i wymaganiom projektu.

### <a name="initialize-in-the-constructor"></a>Zainicjuj w konstruktorze

Idealnym sposobem na rozwiązanie niezainicjowanych ostrzeżeń jest zainicjowanie właściwości w konstruktorze:

```csharp
class Student
{
    public Student(string firstName, string lastName)
    {
        FirstName = firstName;
        LastName = lastName;
    }

    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

Takie podejście działa tylko wtedy, gdy biblioteka używana do tworzenia wystąpienia klasy obsługuje przekazywanie parametrów w konstruktorze.

Ponadto biblioteka może obsługiwać przekazywanie *niektórych* właściwości w konstruktorze, ale nie wszystkich.
Na przykład EF Core obsługuje [powiązanie konstruktora](/ef/core/modeling/constructors) dla normalnych właściwości kolumn, ale nie właściwości nawigacji.

Zapoznaj się z dokumentacją biblioteki, która tworzy wystąpienie klasy, aby zrozumieć zakres, do którego obsługuje powiązanie konstruktora.

### <a name="property-with-nullable-backing-field"></a>Właściwość z polem zapasowym dopuszczającym wartość null

Jeśli powiązanie konstruktora nie będzie działało dla Ciebie, jednym ze sposobów na zaradzenie sobie z tym problemem jest posiadanie właściwości niedopuszczających wartości null przy użyciu pola zapasowego dopuszczającego wartość null:

```csharp
private string? _firstName;

[Required]
public string FirstName
{
    set => _firstName = value;
    get => _firstName
           ?? throw new InvalidOperationException("Uninitialized " + nameof(FirstName))
}
```

W tym scenariuszu, jeśli `FirstName` dostęp do właściwości zostanie uzyskany przed jej zainicjowaniem, kod zgłosi `InvalidOperationException`, ponieważ kontrakt interfejsu API został użyty nieprawidłowo.

Należy wziąć pod uwagę, że niektóre biblioteki mogą mieć specjalne uwagi dotyczące korzystania z pól zapasowych. Na przykład może być konieczne skonfigurowanie EF Core, aby prawidłowo używać [pól zapasowych](/ef/core/modeling/backing-field) .

### <a name="initialize-the-property-to-null"></a>Zainicjuj Właściwość wartością null

Terser alternatywą dla korzystania z pola zapasowego dopuszczającego wartość null lub jeśli biblioteka, która tworzy wystąpienie klasy, nie jest zgodna z tym podejściem, można po prostu `null` zainicjować właściwość bezpośrednio, z pomocą operatora null-łagodniejszej (`!`):

```csharp
[Required]
public string FirstName { get; set; } = null!;

[Required]
public string LastName { get; set; } = null!;

public string? VehicleRegistration { get; set; }
```

W czasie wykonywania nigdy nie będzie obserwować rzeczywistej wartości null, chyba że w wyniku błędu programowania, uzyskując dostęp do właściwości, zanim zostanie on prawidłowo zainicjowany.

## <a name="see-also"></a>Zobacz też

- [Migrowanie istniejącej bazy kodu do odwołań do wartości null](tutorials/upgrade-to-nullable-references.md)
- [Praca z typami odwołań do wartości null w EF Core](/ef/core/miscellaneous/nullable-reference-types)
