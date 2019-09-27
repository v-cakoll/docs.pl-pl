---
title: Korzystanie z funkcji dopasowania wzorców w celu poszerzenia typów danych
description: W tym zaawansowanym samouczku pokazano, jak używać technik dopasowywania wzorców do tworzenia funkcji przy użyciu danych i algorytmów, które są tworzone osobno.
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: 036a6bcda04771eb8cf3699af8756e83bb144389
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332353"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Samouczek: Używanie funkcji dopasowywania wzorców do zwiększania typów danych

C#7 wprowadzono podstawowe funkcje dopasowania do wzorca. Te funkcje są rozszerzane C# w 8 przy użyciu nowych wyrażeń i wzorców. Można napisać funkcję, która zachowuje się tak, jakby rozszerzone typy, które mogą znajdować się w innych bibliotekach. Innym zastosowaniem wzorców jest tworzenie funkcji wymaganych przez aplikację, która nie jest podstawową funkcją rozszerzania typu.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
>
> - Rozpoznaj sytuacje, w których należy użyć dopasowania do wzorca.
> - Używaj wyrażeń dopasowania wzorców, aby zaimplementować zachowanie na podstawie typów i wartości właściwości.
> - Połącz dopasowania wzorców z innymi technikami, aby utworzyć kompletne algorytmy.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0. C# 8 kompilator jest dostępny w programie [Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).

W C# tym samouczku założono, że wiesz już, jak i .NET, w tym Visual Studio lub interfejs wiersza polecenia platformy .NET Core.

## <a name="scenarios-for-pattern-matching"></a>Scenariusze dotyczące dopasowywania wzorców

Nowoczesne programowanie często obejmuje Integrowanie danych z wielu źródeł i prezentowanie informacji oraz uzyskiwanie wglądu w dane przy użyciu jednej spójnej aplikacji. Ty i Twój zespół nie będzie mieć kontroli ani dostępu dla wszystkich typów, które reprezentują dane przychodzące.

Klasyczny projekt zorientowany obiektowo wywoła do tworzenia typów w aplikacji, które reprezentują każdy typ danych z tych wielu źródeł danych. Następnie aplikacja będzie współpracować z tymi nowymi typami, konstruktorami dziedziczenia, tworzyć metody wirtualne i implementować abstrakcje. Te techniki działają i czasami są najlepszymi narzędziami. Innym razem można napisać mniej kodu. Można napisać bardziej czysty kod przy użyciu technik, które dzielą dane z operacji, które manipulują tymi danymi.

W tym samouczku utworzysz i zbadasz aplikację, która pobiera dane przychodzące z kilku źródeł zewnętrznych w jednym scenariuszu. Zobaczysz, jak **dopasowanie wzorca** zapewnia wydajny sposób użycia i przetwarzania tych danych w sposób, który nie jest częścią oryginalnego systemu.

Rozważmy główny obszar metropolitalnych, który korzysta z opłat i cen w czasie szczytu do zarządzania ruchem. Napiszesz aplikację, która oblicza opłaty dla pojazdu na podstawie jego typu. Późniejsze ulepszenia obejmują ceny na podstawie liczby osób w danym jeździe. Dalsze ulepszenia zwiększają ceny na podstawie czasu i dnia tygodnia.

Z tego krótkiego opisu można szybko szkicować hierarchię obiektów, aby modelować ten system. Jednak dane pochodzą z wielu źródeł, takich jak inne systemy zarządzania rejestracją pojazdów. Te systemy zapewniają różne klasy do modelowania danych i nie masz modelu pojedynczego obiektu, którego można użyć. W tym samouczku zostaną użyte te uproszczone klasy do modelowania danych pojazdu z tych systemów zewnętrznych, jak pokazano w poniższym kodzie:

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Możesz pobrać kod początkowy z repozytorium usługi GitHub [/przykłady](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) . Można zobaczyć, że klasy pojazdu pochodzą z różnych systemów i znajdują się w różnych przestrzeniach nazw. Nie `System.Object` można użyć żadnej wspólnej klasy bazowej.

## <a name="pattern-matching-designs"></a>Projekty dopasowania wzorców

W scenariuszu używanym w tym samouczku przedstawiono rodzaje problemów, których dopasowanie do wzorców jest odpowiednie do rozwiązania:

- Obiekty potrzebne do pracy nie należą do hierarchii obiektów pasujących do Twoich celów. Być może pracujesz z klasami, które są częścią niepowiązanych systemów.
- Dodawane funkcje nie są częścią abstrakcji rdzeni dla tych klas. Opłaty za przejazd przez pojazd *zmieniają* się w zależności od typu pojazdów, ale opłata nie jest podstawową funkcją pojazdu.

Gdy *kształt* danych i *operacje* na tych danych nie są opisane razem, funkcje dopasowania wzorców w programie C# ułatwiają pracę z.

## <a name="implement-the-basic-toll-calculations"></a>Implementowanie podstawowych obliczeń opłat

Najbardziej podstawowe obliczenia płatne bazują wyłącznie na typie pojazdu:

- A `Car` to $2,00.
- A `Taxi` to $3,50.
- A `Bus` to $5,00.
- A `DeliveryTruck` to $10,00

Utwórz nową `TollCalculator` klasę i Implementuj dopasowanie wzorców w typie pojazdu, aby uzyskać kwotę opłaty. Poniższy kod pokazuje początkową implementację `TollCalculator`.

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

Poprzedni kod używa **wyrażenia Switch** (nie takiego samego jak [`switch`](../language-reference/keywords/switch.md) instrukcja), które sprawdza **wzorzec typu**. **Wyrażenie Switch** zaczyna się od zmiennej, `vehicle` w poprzednim kodzie `switch` , po słowie kluczowym. Następnie wszystkie **ramiona przełączania** są umieszczone w nawiasach klamrowych. Wyrażenie wprowadza inne udoskonalenia do składni otaczającej `switch` instrukcję. `switch` `case` Słowo kluczowe jest pomijane, a wynik każdego ARM jest wyrażeniem. Ostatnie dwie poręcze zawierają nową funkcję języka. `{ }` Przypadek dopasowuje dowolny obiekt o wartości innej niż null, który nie jest zgodny z wcześniejszą ARM. Ten ARM przechwytuje wszystkie nieprawidłowe typy przesłane do tej metody.  `{ }` Przypadek musi być zgodny z przypadkami dla każdego typu pojazdu. Jeśli zamówienie zostało cofnięte, `{ }` pierwszeństwo ma. Na `null` koniec wzorzec wykrywa, `null` kiedy jest przenoszona do tej metody. `null` Wzorzec może być ostatni, ponieważ wzorce innych typów pasują tylko do niezerowego obiektu o poprawnym typie.

Możesz przetestować ten kod przy użyciu następującego kodu w `Program.cs`:

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

Ten kod jest zawarty w projekcie początkowym, ale jest oznaczony jako komentarz. Usuń Komentarze i możesz sprawdzić, które z nich zapisano.

Zaczynasz widzieć, jak wzorce mogą pomóc w tworzeniu algorytmów, w których kod i dane są oddzielone. `switch` Wyrażenie testuje typ i tworzy różne wartości na podstawie wyników. To tylko początek.

## <a name="add-occupancy-pricing"></a>Dodawanie cen użytkowania

Urząd certyfikacji jest odpowiedzialny za przemieszczenie pojazdów z maksymalną wydajnością. Zdecydowały się naliczać więcej czasu, gdy pojazdy mają mniej osób i zachęcają do pełnych pojazdów, oferując niższą cenę:

- Samochody i taksówke bez pasażerów płatją dodatkową $0,50.
- Samochody i taksówki z dwoma pasażerami otrzymują rabat w wysokości $0,50.
- Samochody i taksówki z trzema lub większą liczbą osób uzyskują rabat $1,00.
- W przypadku magistrali, które mają mniej niż 50%, pełna opłata wynosi $2,00.
- Magistrale, które mają więcej niż 90%, uzyskają rabat $1,00.

Te reguły można zaimplementować przy użyciu **wzorca właściwości** w tym samym wyrażeniu przełącznika. Wzorzec właściwości bada właściwości obiektu po ustaleniu typu. Pojedynczy przypadek dla `Car` rozszerzania do czterech różnych przypadków:

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

Pierwsze trzy przypadki testują typ jako a `Car`, a następnie sprawdzają wartość `Passengers` właściwości. Jeśli oba te wartości są zgodne, to wyrażenie jest oceniane i zwracane.

W podobny sposób można również rozwijać przypadki wypadków:

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

W poprzednim przykładzie `when` klauzula została pominięta w ostatecznym przypadku.

Następnie Zaimplementuj reguły użytkowania, rozszerzając przypadki dla magistrali, jak pokazano w następującym przykładzie:

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

Urząd opłat nie jest zaangażowany w liczbę pasażerów w wagonach dostawczych. Zamiast tego dostosowują kwotę opłat w oparciu o klasę wagi wózków w następujący sposób:

- Samochody ciężarowe przekraczające 5000 funtów są obciążane dodatkowymi $5,00.
- Wózki lekkie poniżej 3000 funtów otrzymują rabat $2,00.

Ta reguła jest zaimplementowana przy użyciu następującego kodu:

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Poprzedni kod pokazuje `when` klauzulę ramienia przełącznika. `when` Klauzula służy do testowania warunków innych niż równość dla właściwości. Po zakończeniu będziesz mieć metodę, która wygląda podobnie do następującej:

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

Wiele z tych broni przełączania to przykłady **wzorców cyklicznych**. Na przykład `Car { Passengers: 1}` pokazuje stały wzorzec wewnątrz wzorca właściwości.

Ten kod może być mniej powtarzany przy użyciu przełączników zagnieżdżonych. Te `Car` i`Taxi` oba mają cztery różne ramiona w powyższych przykładach. W obu przypadkach można utworzyć wzorzec typu, który jest przesyłany do wzorca właściwości. Ta technika jest pokazana w poniższym kodzie:

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

W powyższym przykładzie, przy użyciu wyrażenia cyklicznego oznacza, że `Car` nie `Taxi` powtarzasz broni i zawiera poręcze potomne, które testują wartość właściwości. Ta technika nie jest używana jako `Bus` broń `DeliveryTruck` i, ponieważ te poręcze są zakresami testowania dla właściwości, a nie do wartości dyskretnych.

## <a name="add-peak-pricing"></a>Dodawanie cen szczytowych

W przypadku ostatecznej funkcji urząd opłat umożliwia dodanie cen szczytowych z uwzględnieniem czasu. W godzinach rano i wieczorem szczytu opłaty są napadane podwójnie. Ta reguła ma wpływ tylko na ruch w jednym kierunku: przychodzące do miasta rano i wychodzące w godzinie wieczorem szczytu. W innym czasie w ciągu dnia roboczego opłata zostanie zwiększona o 50%. Późne i wczesne rano, opłaty są ograniczone o 25%. W weekendie jest to normalna stawka, niezależnie od czasu.

Użyjesz dopasowania do wzorca dla tej funkcji, ale będziesz zintegrować ją z innymi technikami. Można utworzyć wyrażenie dopasowania pojedynczego wzorca, które będzie uwzględniać wszystkie kombinacje kierunku, dzień tygodnia i godzinę. Wynikiem będzie wyrażenie złożone. Trudno jest czytać i trudny do zrozumienia. Dzięki temu trudno jest zapewnić poprawność. Zamiast tego Połącz te metody, aby utworzyć krotkę wartości, która zwięzłie opisuje wszystkie te Stany. Następnie użyj dopasowania wzorca, aby obliczyć mnożnik dla opłaty za połączenie. Krotka zawiera trzy warunki dyskretne:

- Dzień jest dniem tygodnia lub weekendem.
- Pasmo czasu, w którym jest zbierane połączenie płatne.
- Kierunek znajduje się w mieście lub na zewnątrz miasta.

W poniższej tabeli przedstawiono kombinacje wartości wejściowych i mnożnik cen szczytowych:

| Dzień        | Time         | Direction | Premium |
| ---------- | ------------ | --------- |--------:|
| Dzień tygodnia    | rano szczytu | Dotycząc   | x 2,00  |
| Dzień tygodnia    | rano szczytu | Wyjściowy  | x 1,00  |
| Dzień tygodnia    | telefonu      | Dotycząc   | x 1,50  |
| Dzień tygodnia    | telefonu      | Wyjściowy  | x 1,50  |
| Dzień tygodnia    | szczytu wieczór | Dotycząc   | x 1,00  |
| Dzień tygodnia    | szczytu wieczór | Wyjściowy  | x 2,00  |
| Dzień tygodnia    | Przelewy    | Dotycząc   | x 0,75  |
| Dzień tygodnia    | Przelewy    | Wyjściowy  | x 0,75  |
| Weekend    | rano szczytu | Dotycząc   | x 1,00  |
| Weekend    | rano szczytu | Wyjściowy  | x 1,00  |
| Weekend    | telefonu      | Dotycząc   | x 1,00  |
| Weekend    | telefonu      | Wyjściowy  | x 1,00  |
| Weekend    | szczytu wieczór | Dotycząc   | x 1,00  |
| Weekend    | szczytu wieczór | Wyjściowy  | x 1,00  |
| Weekend    | Przelewy    | Dotycząc   | x 1,00  |
| Weekend    | Przelewy    | Wyjściowy  | x 1,00  |

Istnieją 16 różnych kombinacji trzech zmiennych. Łącząc niektóre warunki, można uprościć ostateczne wyrażenie Switch.

System, który zbiera opłaty, używa <xref:System.DateTime> struktury dla czasu, w którym nastąpiła opłata. Kompiluj metody Członkowskie, które tworzą zmienne z powyższej tabeli. Poniższa funkcja używa wyrażenia przełącznika dopasowania wzorca, aby określić, czy <xref:System.DateTime> element reprezentuje weekend czy dzień tygodnia:

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

Ta metoda działa, ale jest repetitious. Można uprościć ten sposób, jak pokazano w poniższym kodzie:

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Następnie Dodaj podobną funkcję, aby przydzielić czas do bloków:

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Poprzednia metoda nie używa dopasowania do wzorca. Jest to wyraźniejsze użycie dobrze znanego `if` zestawienia instrukcji. Dodaj prywatny `enum` , aby przekonwertować każdy zakres czasu na wartość dyskretną.

Po utworzeniu tych metod można użyć innego `switch` wyrażenia z **wzorcem spójności** , aby obliczyć cenę Premium. Można utworzyć `switch` wyrażenie ze wszystkimi 16 bronią:

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Powyższy kod działa, ale można go uprościć. Wszystkie osiem kombinacji dla weekendu mają te same opłaty za połączenie płatne. Można zastąpić wszystkie osiem następującymi wierszami:

```csharp
(false, _, _) => 1.0m,
```

Ruch przychodzący i wychodzący ma ten sam mnożnik w ciągu dnia tygodnia Daytime i w godzinach nocnych. Te cztery broń przełączania można zastąpić następującymi dwoma wierszami:

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

Kod powinien wyglądać podobnie do następującego kodu po obu tych zmianach:

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

Na koniec możesz usunąć dwie szczytu godziny, które będą obciążane stałą cenę. Po usunięciu tych broni można zastąpić `false` element Odrzuć (`_`) w końcowej aktywacji. Następująca metoda została zakończona:

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

Ten przykład wyróżnia jedną z zalet dopasowania do wzorca: gałęzie wzorców są oceniane w kolejności. W przypadku zmiany rozmieszczenia w taki sposób, aby wcześniejsza gałąź obsługiwała jeden z przyszłych przypadków, kompilator ostrzega o nieosiągalnym kodzie. Te reguły języka ułatwiają wykonywanie powyższych uproszczeń bez obaw, że kod nie uległ zmianie.

Dopasowanie wzorców sprawia, że niektóre typy kodu są bardziej czytelne i oferują alternatywę dla technik zorientowanych obiektowo, gdy nie można dodać kodu do klas. Chmura powoduje, że dane i funkcje mogą się na bieżąco. *Kształt* danych i *operacje* na nim nie są koniecznie opisane razem. W tym samouczku wykorzystano istniejące dane w sposób całkowicie różny od oryginalnej funkcji. Dopasowywanie do wzorca daje możliwość zapisu funkcji, która overrode te typy, nawet jeśli nie można ich zwiększyć.

## <a name="next-steps"></a>Następne kroki

Gotowy kod można pobrać z repozytorium usługi GitHub [/przykłady](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) . Eksploruj własne wzorce i Dodaj tę technikę do zwykłych działań związanych z kodowaniem. Uczenie tych technik umożliwia innym sposobem podejścia problemów i tworzenia nowych funkcji.
