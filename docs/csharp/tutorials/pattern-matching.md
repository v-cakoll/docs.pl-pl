---
title: Rozszerzanie typów danych za pomocą funkcji dopasowywania wzorców
description: Ten zaawansowany samouczek pokazuje, jak używać technik dopasowywania wzorców do tworzenia funkcji przy użyciu danych i algorytmów, które są tworzone oddzielnie.
ms.date: 03/13/2019
ms-technology: csharp-whats-new
ms.custom: mvc
ms.openlocfilehash: df1054d8e0ec2b2539e6a1d00bf353d8ca927397
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156535"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Samouczek: Korzystanie z funkcji dopasowywania wzorców w celu rozszerzenia typów danych

C# 7 wprowadzono podstawowe funkcje dopasowywania wzorców. Te funkcje są rozszerzone w języku C# 8 z nowych wyrażeń i wzorców. Można napisać funkcje, które zachowują się tak, jakby rozszerzone typy, które mogą znajdować się w innych bibliotekach. Innym zastosowaniem wzorców jest tworzenie funkcji, które aplikacja wymaga, która nie jest podstawową funkcją typu jest rozszerzony.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Rozpoznaj sytuacje, w których należy używać dopasowywania wzorców.
> - Użyj wyrażenia dopasowywania wzorców, aby zaimplementować zachowanie na podstawie typów i wartości właściwości.
> - Połącz dopasowywanie wzorców z innymi technikami, aby utworzyć kompletne algorytmy.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilator C# 8.0. Kompilator C# 8 jest dostępny począwszy od [programu Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).

W tym samouczku przyjęto założenie, że znasz c# i .NET, w tym visual studio lub .NET Core CLI.

## <a name="scenarios-for-pattern-matching"></a>Scenariusze dopasowywania wzorców

Nowoczesny rozwój często obejmuje integrację danych z wielu źródeł oraz prezentowanie informacji i spostrzeżeń z tych danych w jednej, spoistej aplikacji. Ty i Twój zespół nie będziecie mieli kontroli ani dostępu dla wszystkich typów reprezentujących przychodzące dane.

Klasyczny projekt obiektowy będzie wywoływać tworzenie typów w aplikacji, które reprezentują każdy typ danych z tych wielu źródeł danych. Następnie aplikacja będzie działać z tych nowych typów, budować hierarchie dziedziczenia, tworzenie metod wirtualnych i implementować abstrakcje. Te techniki działają, a czasami są najlepszymi narzędziami. Innym razem można napisać mniej kodu. Można napisać bardziej przejrzysty kod przy użyciu technik, które oddzielają dane od operacji, które manipulują tymi danymi.

W tym samouczku utworzysz i eksplorujesz aplikację, która pobiera dane przychodzące z kilku źródeł zewnętrznych dla jednego scenariusza. Zobaczysz, jak **dopasowanie wzorca** zapewnia skuteczny sposób używania i przetwarzania tych danych w sposób, który nie był częścią oryginalnego systemu.

Rozważmy główny obszar metropolitalny, który korzysta z opłat drogowych i cen w godzinach szczytu do zarządzania ruchem. Piszesz aplikację, która oblicza opłaty za pojazd na podstawie jego typu. Późniejsze ulepszenia obejmują ceny oparte na liczbie osób znajdujących się w pojeździe. Dalsze ulepszenia dodają ceny na podstawie czasu i dnia tygodnia.

Z tego krótkiego opisu być może szybko naszkicowaliście hierarchię obiektów, aby modelować ten system. Jednak twoje dane pochodzą z wielu źródeł, takich jak inne systemy zarządzania rejestracją pojazdów. Systemy te zapewniają różne klasy do modelu tych danych i nie masz jednego modelu obiektu, którego można użyć. W tym samouczku użyjesz tych uproszczonych klas do modelowania danych pojazdu z tych systemów zewnętrznych, jak pokazano w poniższym kodzie:

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Kod startowy można pobrać z repozytorium GitHub/sample.You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository. Widać, że klasy pojazdów są z różnych systemów i znajdują się w różnych przestrzeniach nazw. Nie wspólnej klasy podstawowej, inne niż `System.Object` mogą być lewarowane.

## <a name="pattern-matching-designs"></a>Wzory pasujące do wzorców

Scenariusz użyty w tym samouczku podkreśla rodzaje problemów, które dopasowywanie wzorców jest dobrze nadaje się do rozwiązania:

- Obiekty, z którymi musisz pracować, nie znajdują się w hierarchii obiektów, która pasuje do twoich celów. Być może pracujesz z klasami, które są częścią niepowiązanych systemów.
- Funkcje, które dodajesz nie jest częścią podstawowej abstrakcji dla tych klas. Opłata za przejazd pobierana przez pojazd *zmienia się* w przypadku różnych typów pojazdów, ale opłata za przejazd nie jest podstawową funkcją pojazdu.

Gdy *kształt* danych i *operacje* na tych danych nie są opisane razem, funkcje dopasowywania wzorców w języku C# ułatwiają pracę z.

## <a name="implement-the-basic-toll-calculations"></a>Wdrożenie podstawowych obliczeń opłat drogowych

Najbardziej podstawowe obliczenie opłaty drogowej zależy tylko od typu pojazdu:

- A `Car` wynosi $2.00.
- A `Taxi` wynosi $3.50.
- A `Bus` wynosi $5.00.
- A `DeliveryTruck` jest $10.00

Utwórz `TollCalculator` nową klasę i zaimplementuj dopasowanie wzorców na typie pojazdu, aby uzyskać kwotę opłaty drogowej. Poniższy kod przedstawia wstępną `TollCalculator`implementację pliku .

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

Poprzedni kod używa **wyrażenia przełącznika** (nie [`switch`](../language-reference/keywords/switch.md) takie samo jak instrukcja), która testuje **wzorzec typu**. **Wyrażenie przełącznika** rozpoczyna się `vehicle` od zmiennej w poprzednim `switch` kodzie, po której następuje słowo kluczowe. Następnie przychodzi wszystkie **ramiona przełącznika** wewnątrz kręcone szelki. Wyrażenie `switch` sprawia, że inne udoskonalenia do `switch` składni, która otacza instrukcję. Słowo `case` kluczowe jest pomijane, a wynik każdego ramienia jest wyrażeniem. Ostatnie dwa ramiona pokazują nową funkcję językową. Sprawa `{ }` pasuje do dowolnego obiektu innego niż null, który nie był zgodny z wcześniejszym ramieniem. To ramię przechwytuje wszelkie niepoprawne typy przekazane do tej metody.  Sprawa `{ }` musi być zgodna z przypadkami dla każdego typu pojazdu. Gdyby zamówienie zostało odwrócone, `{ }` sprawa miałaby pierwszeństwo. Na koniec `null` wzorzec `null` wykrywa, gdy a jest przekazywana do tej metody. Wzorzec `null` może być ostatni, ponieważ inne wzorce typu odpowiadają tylko obiektowi inne niż null poprawnego typu.

Można przetestować ten kod za `Program.cs`pomocą następującego kodu w:

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
                Console.WriteLine("Caught an argument exception when using the wrong type");
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

Ten kod jest uwzględniony w projekcie startowym, ale jest komentowany. Usuń komentarze i możesz sprawdzić, co napisałeś.

Zaczynasz widzieć, jak wzorce mogą pomóc w tworzeniu algorytmów, w których kod i dane są oddzielne. Wyrażenie `switch` testuje typ i generuje różne wartości na podstawie wyników. To dopiero początek.

## <a name="add-occupancy-pricing"></a>Dodaj ceny obłożenia

Organ pobierający opłaty drogowe chce zachęcić pojazdy do poruszania się z maksymalną przepustowością. Zdecydowali się pobierać wyższe opłaty, gdy pojazdy mają mniej pasażerów, i zachęcać do pełnych pojazdów, oferując niższe ceny:

- Samochody i taksówki bez pasażerów zapłacić dodatkowe 0,50 dolarów.
- Samochody i taksówki z dwoma pasażerami otrzymują zniżkę w wysokości 0,50 USD.
- Samochody i taksówki z trzema lub więcej pasażerami otrzymują zniżkę w wysokości 1,00 USD.
- Autobusy, które są mniej niż 50% pełne zapłacić dodatkowe 2,00 dolarów.
- Autobusy, które są więcej niż 90% pełne dostać 1,00 dolarów zniżki.

Reguły te można zaimplementować przy użyciu **wzorca właściwości** w tym samym wyrażeniu przełącznika. Wzorzec właściwości sprawdza właściwości obiektu po określeniu typu. Pojedynczy przypadek dla `Car` rozszerza się do czterech różnych przypadków:

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1 }       => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    // ...
};
```

Pierwsze trzy przypadki przetestować `Car`typ jako , a `Passengers` następnie sprawdzić wartość właściwości. Jeśli oba zgodne, to wyrażenie jest oceniane i zwracane.

Można również rozszerzyć sprawy dotyczące taksówek w podobny sposób:

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

W poprzednim przykładzie klauzula `when` została pominięta w ostatnim przypadku.

Następnie należy wdrożyć zasady obłożenia, rozszerzając sprawy dla autobusów, jak pokazano w poniższym przykładzie:

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

Organ pobierający opłaty nie zajmuje się liczbą pasażerów w samochodach dostawczych. Zamiast tego dostosowują kwotę opłaty drogowej na podstawie klasy wagowej samochodów ciężarowych w następujący sposób:

- Samochody ciężarowe powyżej 5000 funtów są płatne dodatkowe 5,00 dolarów.
- Lekkie ciężarówki poniżej 3000 funtów otrzymują zniżkę w wysokości 2,00 USD.

Ta reguła jest implementowana przy następującym kodzie:

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Poprzedni kod zawiera `when` klauzulę ramienia przełącznika. Klauzula `when` służy do testowania warunków innych niż równości we właściwości. Po zakończeniu będziesz mieć metodę, która wygląda podobnie do następujących:

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1}        => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

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

    { }     => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
    null    => throw new ArgumentNullException(nameof(vehicle))
};
```

Wiele z tych ramion przełącznika są przykładami **rekurencyjne wzory**. Na przykład `Car { Passengers: 1}` pokazuje stały wzorzec wewnątrz wzorca właściwości.

Można sprawić, że ten kod będzie mniej powtarzalny przy użyciu przełączników zagnieżdżonych. Oba `Car` `Taxi` mają cztery różne ramiona w poprzednich przykładach. W obu przypadkach można utworzyć wzorzec typu, który zasila wzorzec właściwości. Ta technika jest pokazana w następującym kodzie:

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

W poprzednim przykładzie użycie wyrażenia cyklicznego oznacza, że nie powtarzasz `Car` i `Taxi` ramion zawierających ramiona podrzędne, które testują wartość właściwości. Ta technika nie jest `Bus` `DeliveryTruck` używana dla i broni, ponieważ te ramiona są zakresy testowania właściwości, a nie wartości dyskretne.

## <a name="add-peak-pricing"></a>Dodawanie cen szczytowych

W przypadku końcowej funkcji urząd opłat drogowych chce dodać ceny szczytowe zależne od czasu. W godzinach porannych i wieczornych w godzinach szczytu opłaty są podwojone. Zasada ta wpływa tylko na ruch w jednym kierunku: przychodzące do miasta rano, a wychodzące w godzinach szczytu wieczorem. W innych okresach dnia pracy opłaty drogowe wzrastają o 50%. Późną nocą i wczesnym rankiem opłaty drogowe są zmniejszane o 25%. W weekend, jest to normalna stawka, niezależnie od czasu.

Użyjesz dopasowywania wzorców dla tej funkcji, ale zintegrujesz ją z innymi technikami. Można utworzyć wyrażenie dopasowania pojedynczego wzorca, które uwzględniałoby wszystkie kombinacje kierunku, dnia tygodnia i godziny. Rezultatem byłoby skomplikowane wyrażenie. Byłoby to trudne do odczytania i trudne do zrozumienia. To sprawia, że trudno jest zapewnić poprawność. Zamiast tego połączyć te metody, aby zbudować krotkę wartości, które zwięźle opisuje wszystkie te stany. Następnie użyj dopasowania wzorca, aby obliczyć mnożnik dla opłaty drogowej. Krotka zawiera trzy dyskretne warunki:

- Dzień to dzień powszedni lub weekend.
- Pasmo czasu, w którym pobierana jest opłata drogowa.
- Kierunek jest do miasta lub poza miastem

W poniższej tabeli przedstawiono kombinacje wartości wejściowych i mnożnik cen szczytowych:

| Day        | Time         | Kierunek | Premium |
| ---------- | ------------ | --------- |--------:|
| Dzień tygodnia    | poranny pośpiech | przychodzące   | x 2.00  |
| Dzień tygodnia    | poranny pośpiech | Wychodzących  | x 1.00  |
| Dzień tygodnia    | Dzień      | przychodzące   | x 1,50  |
| Dzień tygodnia    | Dzień      | Wychodzących  | x 1,50  |
| Dzień tygodnia    | wieczorny pośpiech | przychodzące   | x 1.00  |
| Dzień tygodnia    | wieczorny pośpiech | Wychodzących  | x 2.00  |
| Dzień tygodnia    | Noc    | przychodzące   | x 0,75  |
| Dzień tygodnia    | Noc    | Wychodzących  | x 0,75  |
| Weekend    | poranny pośpiech | przychodzące   | x 1.00  |
| Weekend    | poranny pośpiech | Wychodzących  | x 1.00  |
| Weekend    | Dzień      | przychodzące   | x 1.00  |
| Weekend    | Dzień      | Wychodzących  | x 1.00  |
| Weekend    | wieczorny pośpiech | przychodzące   | x 1.00  |
| Weekend    | wieczorny pośpiech | Wychodzących  | x 1.00  |
| Weekend    | Noc    | przychodzące   | x 1.00  |
| Weekend    | Noc    | Wychodzących  | x 1.00  |

Istnieje 16 różnych kombinacji trzech zmiennych. Łącząc niektóre warunki, uprościsz wyrażenie przełącznika końcowego.

System, który pobiera opłaty za <xref:System.DateTime> przejazd, wykorzystuje strukturę w momencie pobrania opłaty drogowej. Tworzenie metod członkowskich, które tworzą zmienne z poprzedniej tabeli. Następująca funkcja używa wyrażenia przełącznika pasującego do wzorca, <xref:System.DateTime> aby wyrazić, czy reprezentuje weekend, czy dzień tygodnia:

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

Ta metoda działa, ale jest powtarzalna. Można go uprościć, jak pokazano w poniższym kodzie:

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Następnie dodaj podobną funkcję, aby kategoryzować czas do bloków:

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Poprzednia metoda nie używa dopasowania wzorca. Jest to jaśniejsze przy użyciu `if` znanej kaskady stwierdzeń. Aby przekonwertować `enum` każdy zakres czasu na wartość dyskretną, należy dodać wartość prywatną.

Po utworzeniu tych metod można `switch` użyć innego wyrażenia ze **wzorcem krotki** do obliczania premii cenowej. Można zbudować `switch` wyrażenie z wszystkich 16 broni:

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Powyższy kod działa, ale można go uprościć. Wszystkie osiem kombinacji na weekend ma taką samą opłatę. Możesz zastąpić wszystkie osiem następującym wierszem:

```csharp
(false, _, _) => 1.0m,
```

Ruch przychodzący i wychodzący mają ten sam mnożnik w ciągu dnia w dni powszednie i w godzinach nocnych. Te cztery ramiona przełącznika można zastąpić następującymi dwiema liniami:

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

Kod powinien wyglądać jak następujący kod po tych dwóch zmianach:

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

Na koniec możesz usunąć dwa godziny szczytu, które płacą normalną cenę. Po usunięciu tych ramion można `false` zastąpić je`_`odrzutem ( ) w ostatnim ramieniu przełącznika. Będziesz mieć następującą gotową metodę:

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

W tym przykładzie wyróżniono jedną z zalet dopasowywania wzorców: gałęzie wzorca są oceniane w kolejności. Jeśli zmienisz ich tak, że wcześniejsza gałąź obsługuje jeden z późniejszych przypadków, kompilator ostrzega o nieosiągalny kod. Te reguły języka ułatwiły wykonanie poprzednich uproszczeń z pewnością, że kod się nie zmienił.

Dopasowywanie wzorców sprawia, że niektóre typy kodu są bardziej czytelne i oferują alternatywę dla technik obiektowych, gdy nie można dodać kodu do klas. Chmura powoduje, że dane i funkcje są rozstawione. *Kształt* danych i *operacje* na nim nie muszą być opisane razem. W tym samouczku zużyłeś istniejące dane w zupełnie inny sposób niż jego oryginalna funkcja. Dopasowanie wzorca dało możliwość pisania funkcji, które overrode tych typów, nawet jeśli nie można rozszerzyć je.

## <a name="next-steps"></a>Następne kroki

Gotowy kod można pobrać z repozytorium GitHub [dotnet/samples.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) Eksploruj wzorce samodzielnie i dodaj tę technikę do swoich regularnych działań związanych z kodowaniem. Nauka tych technik daje inny sposób podejścia do problemów i tworzenia nowych funkcji.
