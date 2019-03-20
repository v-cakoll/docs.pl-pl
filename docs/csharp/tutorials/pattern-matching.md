---
title: Użyj funkcji dopasowywania wzorca, aby rozszerzyć typy danych
description: W tym samouczku zaawansowane pokazuje, jak tworzyć funkcje przy użyciu danych i algorytmy, które są tworzone oddzielnie za pomocą metod dopasowania do wzorca.
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: 78b7215631a3988cff1ab942b677bcd5205e311c
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185834"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Samouczek: Aby rozszerzyć typy danych przy użyciu funkcji dopasowywania wzorca

C#7 wprowadzono podstawowy wzorzec dopasowywania funkcji. Te funkcje zostały rozszerzone w C# 8 za pomocą nowego wyrażenia i wzorce. Można napisać funkcji, który zachowuje się tak, jakby rozszerzone typy, które mogą być w innych bibliotekach. Innym zastosowaniem wzorców jest tworzenie funkcji wymaganych przez aplikację, która nie jest podstawową cechą typ zostanie przedłużony.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
> * Rozpoznaje sytuacji, w którym dopasowywania do wzorca powinny być używane.
> * Aby zaimplementować zachowanie na podstawie typu i wartości właściwości, należy wykonać wyrażeniach dopasowania do wzorca.
> * Połącz dopasowania z innymi technikami, aby utworzyć pełną algorytmów do wzorca.

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować komputer do uruchamiania platformę .NET Core, w tym C# kompilatora 8.0 (wersja zapoznawcza). C# 8 kompilatora w wersji zapoznawczej jest dostępna przy użyciu najnowszej [2019 usługi Visual Studio w wersji zapoznawczej](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), lub r [.NET Core 3.0 w wersji zapoznawczej](https://dotnet.microsoft.com/download/dotnet-core/3.0).

W tym samouczku założono, kiedy znasz już C# i .NET, w tym Visual Studio lub interfejsu wiersza polecenia platformy .NET Core.

## <a name="scenarios-for-pattern-matching"></a>Scenariusze dotyczące dopasowywania do wzorca

Nowoczesne tworzenie oprogramowania często obejmuje integrowanie danych z wielu źródeł i prezentowanie informacji i szczegółowe informacje na podstawie tych danych w jednej aplikacji cohesive. Ty i Twój zespół nie będzie miał formant lub uzyskania dostępu do wszystkich typów, które reprezentują dane przychodzące.

Klasyczne projektowanie zorientowane obiektowo wywoływałby do tworzenia typów w aplikacji, który reprezentuje każdego typu danych te dane z wielu źródeł. Następnie aplikacja będzie pracować z tych nowych typów, tworzenie hierarchii dziedziczenia, tworzenie metod wirtualnych i zaimplementować abstrakcje. Techniki te działają i czasami są najlepsze narzędzia. Czasami można napisać mniejszej ilości kodu. Można napisać więcej zwykłego kodu przy użyciu technik, które rozdziela się dane przed operacjami, które manipulowania tych danych.

W tym samouczku utworzysz i zapoznaj się z aplikacji, która przyjmuje dane przychodzące z kilku źródeł zewnętrznych dla jednego scenariusza. Zobaczysz jak **dopasowywania do wzorca** umożliwia wydajne wykorzystanie i przetworzyć te dane w sposób, który nie był części systemu, oryginalnym.

Należy wziąć pod uwagę głównych Miasto używanej drogi i ceny godziny szczytu do zarządzania ruchem. Możesz napisać aplikację, który oblicza drogi pojazdu na podstawie jego typu. Ulepszenia nowsze dołączania, cen, na podstawie liczby użytkowników w pojeździe. Dalsze udoskonalenia dodać, ceny, oparte na godzinę i dzień tygodnia.

Z tego krótkiego opisu może mieć szybko ustalonej hierarchię obiektów do modelu tego systemu. Jednak danych pochodzi z wielu źródeł, takich jak inne systemy zarządzania rejestracji vehicle. Te systemy Podaj różnych klas do modelu danych, a nie masz modelu pojedynczy obiekt, w których można użyć. W tym samouczku użyjesz tych klas uproszczona do modelu danych pojazdu z systemów zewnętrznych, jak pokazano w poniższym kodzie:

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Możesz pobrać kod początkowy, od [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) repozytorium GitHub. Widać klasy pojazdu pochodzą z różnych systemów i znajdują się w różnych obszarach nazw. Nie wspólnej bazy klasy innej niż `System.Object` nadającego się.

## <a name="pattern-matching-designs"></a>Wzorzec dopasowania projektów

Scenariusz używane w tym samouczek najważniejsze funkcje rodzaje problemów, które dopasowanie wzorca jest dobrze nadaje się do rozwiązania:

- Obiekty, które są potrzebne do pracy z nie występują w hierarchię obiektów, która pasuje do określonych celów. Możliwe, że pracujesz z klasami, które są częścią niepowiązanych systemów.
- Funkcje, które dodajesz nie jest częścią abstrakcji core dla tych klas. Płatny sposób zapłaty pojazdu *zmiany* dla różnych typów pojazdów, ale płatny nie jest podstawowa funkcja pojazdu.

Gdy *kształt* danych i *operacji* na tym dane nie zostały opisane razem, funkcje dopasowania wzorca C# ułatwienia pracy z.

## <a name="implement-the-basic-toll-calculations"></a>Implementowanie obliczeń płatny podstawowe

Najbardziej podstawowa obliczeń płatny opiera się tylko pod względem typu pojazdów:

- Element `Car` jest $2.00.
- Element `Taxi` jest 3.50 $.
- Element `Bus` jest 5,00 zł.
- Element `DeliveryTruck` jest 10,00 zł

Utwórz nową `TollCalculator` klasy i implementuje dopasowania do wzorca w pojeździe można pobrać kwota opłaty.

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    public class TollCalculator
    {
        public decimal CalculateToll(object vehicle) =>
            vehicle switch
        {
            Car c           => 2.00m,
            Taxi t          => 3.50m,
            Bus b           => 5.00m,
            DeliveryTruck t => 10.00m,
            { }             => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null            => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

W poprzednim kodzie użyto **wyrażenie switch** (nie taka sama, jak [ `switch` ](../language-reference/keywords/switch.md) instrukcji), które testują **wpisz wzór**. A **wyrażenie switch** rozpoczyna się od zmiennej, `vehicle` w poprzednim kodzie, a następnie `switch` — słowo kluczowe. Następnie wszystkie nadchodzi **Przełącz arms** umieszczone w nawiasach klamrowych. `switch` Wyrażenie sprawia, że pozostałe elementy składni, która otacza `switch` instrukcji. `case` — Słowo kluczowe zostanie pominięty, a wynik każdego arm jest wyrażeniem. Ostatnie dwa arms wyświetlenie nowej funkcji języka. `{ }` Przypadek pasuje do dowolnego obiektu inną niż null, który nie pasuje do wcześniejszych arm. Ta arm połowy wszelkie nieprawidłowe typy przekazane do tej metody. Na koniec `null` przechwytuje wzorca, gdy `null` jest przekazywany do tej metody. `null` Wzorzec może być ostatnie, ponieważ inne wzorce typ zgodny tylko obiektów innych niż null poprawnego typu.

Możesz przetestować ten kod, używając następującego kodu w `Program.cs`:

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            var tollCalc = new TollCalculator();

            var car = new Car();
            var taxi = new Taxi();
            var bus = new Bus();
            var truck = new DeliveryTruck();

            Console.WriteLine($"The toll for a car is {tollCalc.CalculateToll(car)}");
            Console.WriteLine($"The toll for a taxi is {tollCalc.CalculateToll(taxi)}");
            Console.WriteLine($"The toll for a bus is {tollCalc.CalculateToll(bus)}");
            Console.WriteLine($"The toll for a truck is {tollCalc.CalculateToll(truck)}");

            try
            {
                tollCalc.CalculateToll("this will fail");
            }
            catch (ArgumentException e)
            {
                Console.WriteLine("Caught an argument exception when using the wrong type", DayOfWeek.Friday);
            }
            try
            {
                tollCalc.CalculateToll(null);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

Ten kod znajduje się projekt startowy, ale są oznaczone jako komentarz. Usuń komentarze i można przetestować zostały zapisane.

Trwa uruchamianie zobaczyć, jak wzorce mogą pomóc tworzyć algorytmów, której kod i dane są niezależne. `switch` Wyrażenie sprawdza typ i tworzy różne wartości, w oparciu o wyniki. To dopiero początek.

## <a name="add-occupancy-pricing"></a>Dodaj rozszerzenia ceny

Urząd płatny chce, aby zachęcić pojazdów przechodzić z maksymalną wydajnością. Decydujesz się one do bardziej pojazdów mają mniejszą liczbę osób, gdy zachęcać pojazdów pełną, udostępniając niższe ceny:

- Samochodów i taksówek za pomocą pasażerowie nie zapłacić dodatkowy 0,50 USD.
- Uzyskaj rabat w wysokości 0,50, samochodów i taksówek za pomocą dwóch pasażerów.
- Uzyskaj Rabat $1.00, samochodów i taksówek za pomocą trzech lub więcej osób.
- Autobusów, które są mniej niż 50% zapełnienia zapłacić dodatkowy $2.00.
- Autobusów, które są ponad 90% zapełnienia uzyskać rabat $1.00.

Te reguły można zaimplementować przy użyciu **wzorzec właściwość** w tym samym wyrażenie switch. Wzorzec właściwość sprawdza, czy właściwości obiektu po określeniu typu. W przypadku pojedynczego `Car` rozwija do czterech różnych przypadków:

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1 }       => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c when c.Passengers > 2 => 2.00m - 1.0m,

    // ...
};
```

Pierwsze trzy przypadki testów typ jako `Car`, następnie sprawdź wartość `Passengers` właściwości. Jeśli obie są zgodne, to wyrażenie jest oceniana i zwracana. Pokazuje końcowego klauzuli `when` klauzuli arm przełącznika. Możesz użyć `when` klauzulę, aby przetestować warunki niż równość dla właściwości. W powyższym przykładzie `when` klauzuli testy, aby zobaczyć, że są więcej niż 2 pasażerów w samochodu. Ściśle rzecz ujmując nie jest konieczne, w tym przykładzie.

Może także zwiększyć przypadków dla taksówek w podobny sposób:

```csharp
vehicle switch
{
    // ...

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    // ...
};
```

W powyższym przykładzie `when` na ostatnim przypadku pominięcia klauzuli.

Następnie należy zaimplementować reguły zajętość rozwijając przypadków autobusów, jak pokazano w poniższym przykładzie:

```csharp
vehicle switch
{
    // ...

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    // ...
};
```

Urząd płatny nie jest związana z liczby pasażerów ciężarówek dostarczania. Zamiast tego są opłaty za bardziej oparte na klasę wagi ciężarówek. Ciężarówek ponad 5000 modułów równoważenia obciążenia jest naliczana dodatkowa 5.00 $. Ciężarówek światła w obszarze 3000 lbs otrzymują rabat w wysokości $2.00. Tej reguły jest implementowane za pomocą następującego kodu:

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Gdy wszystko będzie gotowe, będziesz mieć na metodę, która wygląda podobnie do następujących:

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1}        => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c when c.Passengers > 2 => 2.00m - 1.0m,

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Wiele z nich Przełącz arms są przykładami **wzorców cyklicznego**. Na przykład `Car { Passengers: 1}` pokazuje wzór stałej wewnątrz wzorzec właściwości.

Możesz wprowadzić ten kod mniej powtarzalne, za pomocą przełączników zagnieżdżonych. `Car` i `Taxi` mają czterech różnych arms w powyższych przykładach. W obu przypadkach można utworzyć wzorzec typ, który trafiają do wzorca właściwości. W poniższym kodzie pokazano tej techniki:

```csharp
public decimal CalculateToll(object vehicle) =>
    vehicle switch
    {
        Car c => c.Passengers switch
        {
            0 => 2.00m + 0.5m,
            1 => 2.0m,
            2 => 2.0m - 0.5m,
            _ => 2.00m - 1.0m
        },

        Taxi t => t.Fares switch
        {
            0 => 3.50m + 1.00m,
            1 => 3.50m,
            2 => 3.50m - 0.50m,
            _ => 3.50m - 1.00m
        },

        Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
        Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
        Bus b => 5.00m,

        DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
        DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
        DeliveryTruck t => 10.00m,

        { }  => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

W poprzednim przykładzie, za pomocą wyrażenia cyklicznego oznacza, że nie powtarzaj `Car` i `Taxi` arms zawierający arms podrzędne, które testują wartości właściwości. Ta technika nie jest używany dla `Bus` i `DeliveryTruck` aktywacji, ponieważ te arms testujesz zakresów dla właściwości wartości dyskretnych nie.

## <a name="add-peak-pricing"></a>Dodaj ceny szczytowa

Dla funkcji końcowego urząd płatny chce dodać ceny szczytowa poufnych czasowo. Podczas rano i wieczorem łazienkowych godzin zostaną podwojone drogi. Tej reguły ma wpływ tylko na ruch sieciowy w jeden kierunek: przychodzący do miasta rano i wychodzących w ciągu godziny łazienkowych wieczór. W innych przypadkach w pracy drogi Zwiększ o 50%. Godziny nocne i wcześnie rano, drogi zostały zredukowane przez 25%. Weekend jest normalną szybkość, niezależnie od tego, w tym czasie.

Użyjesz dopasowywania do wzorca dla tej funkcji, ale będzie zintegrować ją z innymi technikami. Można utworzyć wyrażenie dopasowania do wzorca pojedynczej będzie uwzględnić wszystkie kombinacje kierunku, dnia tygodnia i godzinę. Wynik byłby skomplikowanego wyrażenia. Jest trudny do odczytania i trudne do zrozumienia. Które czyni go trudno sprawdzić ich poprawność. Zamiast tego należy połączyć te metody do tworzenia krotki wartości, która zwięźle opisuje te stany. Następnie użyj dopasowywania wzorców do obliczania mnożnik dla płatny. Spójna kolekcja znajdująca się zawiera trzy osobne warunki:

- Dzień jest dniem powszednim lub weekendy.
- Pasmo czas, kiedy są zbierane płatny.
- Kierunek to miasto lub miejscowość

W poniższej tabeli przedstawiono kombinacje wartości wejściowe i ze szczytową, cennik mnożnik:

| Dzień        | Godzina         | Kierunek | Premium |
| ---------- | ------------ | --------- |--------:|
| Dzień tygodnia    | łazienkowych rano | Dla ruchu przychodzącego   | x 2.00  |
| Dzień tygodnia    | łazienkowych rano | Wychodzące  | x 1.00  |
| Dzień tygodnia    | za dnia      | Dla ruchu przychodzącego   | x 1.50  |
| Dzień tygodnia    | za dnia      | Wychodzące  | x 1.50  |
| Dzień tygodnia    | łazienkowych wieczorem | Dla ruchu przychodzącego   | x 1.00  |
| Dzień tygodnia    | łazienkowych wieczorem | Wychodzące  | x 2.00  |
| Dzień tygodnia    | procesu na noc    | Dla ruchu przychodzącego   | x wartość 0,75  |
| Dzień tygodnia    | procesu na noc    | Wychodzące  | x wartość 0,75  |
| Weekend    | łazienkowych rano | Dla ruchu przychodzącego   | x 1.00  |
| Weekend    | łazienkowych rano | Wychodzące  | x 1.00  |
| Weekend    | za dnia      | Dla ruchu przychodzącego   | x 1.00  |
| Weekend    | za dnia      | Wychodzące  | x 1.00  |
| Weekend    | łazienkowych wieczorem | Dla ruchu przychodzącego   | x 1.00  |
| Weekend    | łazienkowych wieczorem | Wychodzące  | x 1.00  |
| Weekend    | procesu na noc    | Dla ruchu przychodzącego   | x 1.00  |
| Weekend    | procesu na noc    | Wychodzące  | x 1.00  |

Istnieją różne kombinacje 16 trzech zmiennych. Łącząc niektóre warunki uprościmy wyrażenie switch końcowej.

System, który zbiera drogi używa <xref:System.DateTime> struktury przez czas, kiedy został zebrany płatny. Tworzenie metody elementu członkowskiego, które Utwórz zmienne z powyższej tabeli. Poniższa funkcja używa przełącznika wyrażeniu dopasowania do wzorca do express czy <xref:System.DateTime> reprezentuje weekend lub dzień tygodnia:

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday    => true,
        DayOfWeek.Tuesday   => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday  => true,
        DayOfWeek.Friday    => true,
        DayOfWeek.Saturday  => false,
        DayOfWeek.Sunday    => false
    };
```

Ta metoda działa, ale jest monotonnych. Można uprościć, jak pokazano w poniższym kodzie:

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Następnie dodaj podobną funkcję do kategoryzowania czasu z bloków:

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Poprzednia metoda nie używa dopasowywania do wzorca. Jest bardziej zrozumiały, przy użyciu dobrze znanych kolejne `if` instrukcji. Dodaj prywatnej `enum` do przekonwertowania każdego zakresu czasu wartości dyskretnych.

Po utworzeniu tych metod, możesz użyć innej `switch` wyrażenie **wzór krotki** do obliczania cenowej premium. Można utworzyć `switch` wyrażenia z wszystkich arms 16:

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Powyżej kod działa, ale można uprościć. Wszystkie kombinacje osiem for weekend mają ten sam numer płatny. Możesz zastąpić wszystkie osiem o następujący wiersz:

```csharp
(false, _, _) => 1.0m,
```

Ruchu przychodzącego i wychodzącego mają ten sam mnożnik podczas za dzień tygodnia, dnia i godziny na następny dzień. Te cztery przełącznika arms, można zastąpić następujące dwa wiersze:

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

Kod powinien wyglądać podobnie do poniższego kodu, po wprowadzeniu tych dwóch zmian:

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true)  => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime,     _)     => 1.50m,
        (true, TimeBand.EveningRush, true)  => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight,   _)     => 0.75m,
        (false, _,                   _)     => 1.00m,
    };
```

Na koniec można usunąć łazienkowych dwie godziny prób wina regularne. Po usunięciu tych arms można zastąpić `false` odrzucić (`_`) w usłudze arm końcowego przełącznika. Będziesz mieć następującą metodę zakończono:

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

W tym przykładzie podkreślono, jedną z zalet dopasowywania do wzorca: wzorzec gałęzie, które są obliczane w kolejności. Jeśli można ponownie rozmieścić je tak, aby starszych gałęzi obsługuje jedną ze spraw nowsze kompilatora ostrzega o. Te reguły języka wprowadzone wykonaj poprzedni definiowaniu bez obaw, że kod nie został zmieniony.

Dopasowanie wzorca zapewnia naturalnych składni wdrożenia różnych rozwiązań, nie należy utworzyć Jeśli używane techniki zorientowane obiektowo. Chmura jest przyczyną, danych i funkcji na żywo od siebie. *Kształt* danych i *operacji* na jej nie są zawsze opisane ze sobą. W tym samouczku istniejące dane jest używane w całkowicie różnych sposobów z jego funkcja pierwotna. Dopasowanie wzorca udostępniła Ci możliwość pisania funkcji, które overrode tych typów, nawet jeśli nie można rozszerzyć je.

## <a name="next-steps"></a>Następne kroki

Możesz pobrać gotowy kod z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) repozytorium GitHub. Poznawanie wzorców na własną rękę, a następnie dodaj tej techniki do regularnego działaniach kodowania. Tych technik uczenia umożliwia innym sposobem podejście do problemów i Utwórz nowe funkcje.
