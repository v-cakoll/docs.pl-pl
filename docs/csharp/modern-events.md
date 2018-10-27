---
title: Wzorzec zdarzeń zaktualizowane środowiska .NET Core
description: Dowiedz się, jak wzorzec zdarzeń platformy .NET Core umożliwia elastyczność dzięki wstecznej zgodności oraz sposób implementacji przetwarzanie zdarzeń bezpieczne subskrybentami async.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 3cab80a0f4fcd3343fdeff265135f1503c036514
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188485"
---
# <a name="the-updated-net-core-event-pattern"></a>Wzorzec zdarzeń zaktualizowane środowiska .NET Core

[Poprzednie](event-pattern.md)

Poprzednim artykule omówiono najbardziej typowe wzorce zdarzeń. .NET core zawiera wzorzec mniej restrykcyjne. W tej wersji `EventHandler<TEventArgs>` definicja zawiera już ograniczenie, `TEventArgs` musi być klasą pochodną `System.EventArgs`.

Zwiększa elastyczność i jest wstecznie zgodna. Zacznijmy od elastyczność. Klasa System.EventArgs wprowadza jednej metody: `MemberwiseClone()`, która tworzy płytką kopię obiektu.
Metoda musi używać odbicia w celu wdrożenia jej funkcjonalność dla dowolnej klasy pochodnej `EventArgs`. Funkcja jest łatwiejsze do utworzenia w określonej klasie pochodnej. Oznacza to skutecznie pochodząca od System.EventArgs to ograniczenie, które ogranicza projektów, ale nie zapewnia żadnych dodatkowych korzyści.
W rzeczywistości można zmieniać definicje typów elementów `FileFoundArgs` i `SearchDirectoryArgs` tak, aby nie pochodzą one od `EventArgs`.
Program będzie działać tak samo.

Możesz również zmienić `SearchDirectoryArgs` na strukturę co więcej zmiany:

[!code-csharp[SearchDir](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Define search directory event")]

Kolejna zmiana jest wywołanie konstruktora domyślnego przed wchodzenie do konstruktora, która inicjuje wszystkie pola. Bez tego dodatku, regułami C# może zgłosić, że właściwości są dostępne przed zostały przypisane.

Nie należy zmieniać `FileFoundArgs` z klasy (typ odwołania) na strukturę (typ wartości). To, ponieważ protokół obsługę anulowania, wymaga, że argumenty zdarzenia są przekazywane przez odwołanie. Jeśli wprowadzono tę samą zmianę klasa wyszukiwania pliku nigdy nie może obserwować zmiany wprowadzone przez wszystkich subskrybentów zdarzeń. Nową kopię struktury będzie używana dla każdego subskrybenta, a tej kopii będzie kopię innej niż ta, widoczne dla obiektu wyszukiwania pliku.

Następnie zastanówmy się, jak ta zmiana może być wstecznie zgodne.
Usuwanie ograniczenia, nie ma wpływu na istniejący kod. Wszelkie istniejące typy argumentów zdarzenia dziedziczą z `System.EventArgs`.
Wstecz zgodność jest główną przyczyną Dlaczego będą one nadal dziedziczyć `System.EventArgs`. Żadnych istniejących subskrybentów zdarzeń będzie subskrybentów do zdarzenia, a następnie klasycznego wzorca.

Po każdym podobnej logiki argumentu zdarzenia utworzony typ teraz nie będzie zawierało żadnych subskrybentów w żadnych istniejących bazach kodu. Nowe typy zdarzeń, które nie pochodzą z `System.EventArgs` będzie przerwać tych ścieżek bazowych kodu.

## <a name="events-with-async-subscribers"></a>Zdarzenia przy użyciu Async subskrybentów

Masz jeden wzorzec końcowego Aby dowiedzieć się więcej: jak poprawnie zapisać subskrybentów zdarzeń, które wywołują kod asynchroniczny. Żądania został opisany w artykule na [async i await](async.md). Metody asynchroniczne mogą mieć zwracać typ void, ale jest zdecydowanie odradzane. Gdy kod dla subskrybentów zdarzeń wywołuje metody asynchronicznej, masz nie wyboru, a do utworzenia `async void` metody. Podpis programu obsługi zdarzeń go wymaga.

Należy uzgodnić tych wskazówkach przeciwstawnym. Jakiś sposób, należy utworzyć bezpiecznego `async void` metody. Podstawowe informacje potrzebne do zaimplementowania wzorca znajdują się poniżej:

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

Najpierw zwróć uwagę, że program obsługi jest oznaczona jako async obsługi. Ponieważ jest ona obecnie przypisywana do obsługi zdarzeń typ delegata, ma zwracać typ void. Oznacza to, musi wykonać wzoru pokazanego w procedurze obsługi i zezwala na wszystkie wyjątki zostanie wygenerowany poza kontekstem programu async obsługi. Ponieważ zwraca zadanie, nie istnieje żadne zadanie, które mogą zgłosić błąd, wprowadzając stanie błędnym. Ponieważ metoda async, metoda po prostu nie można zgłosić wyjątek. (Wywoływania metody ma kontynuowanie wykonywania, ponieważ jest on `async`.) Rzeczywiste działanie zostanie określony inaczej dla różnych środowisk. Może rozwiązać niniejszą wątku, może rozwiązać niniejszą program lub może on pozostawić program w stanie nieokreślony. Żaden z nich są dobre wyniki.

Dlatego zawijania instrukcji czekania asynchroniczne zadanie w własne bloku try. To spowodować uszkodzoną zadań, po zalogowaniu błędu. Jeśli jest to błąd, z którego nie można odzyskać aplikacji, można zakończyć program, szybko i bezpiecznie

Są ważne aktualizacje wzorce zdarzeń platformy .NET. Zobaczysz wiele przykładów wcześniejszych wersji w bibliotekach, z którymi pracujesz. Jednak należy zrozumieć, jakie najnowsze wzorce są również.

Następny artykuł w tej serii pomaga rozróżnić przy użyciu `delegates` i `events` w projektach. Są one podobne pojęcia, a ten artykuł pomoże Ci najlepszych decyzji programów.

[Next](distinguish-delegates-events.md)
