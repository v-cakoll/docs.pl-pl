---
title: Zaktualizowany wzorzec zdarzeń platformy .NET Core
description: Dowiedz się, w jaki sposób wzorzec zdarzeń platformy .NET Core umożliwia elastyczność z poprzednią zgodnością i jak zaimplementować bezpieczne przetwarzanie zdarzeń za pomocą subskrybentów asynchronicznych.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 85fa4fd111a9eab01c1d32949d9fcc5f6300e33c
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798881"
---
# <a name="the-updated-net-core-event-pattern"></a>Zaktualizowany wzorzec zdarzeń platformy .NET Core

[Ubiegł](event-pattern.md)

W poprzednim artykule omówiono najczęstsze wzorce zdarzeń. Platforma .NET Core ma bardziej swobodny wzorzec. W tej wersji definicja `EventHandler<TEventArgs>` nie ma już ograniczenia, które `TEventArgs` musi być klasą pochodną `System.EventArgs`.

Zwiększa to elastyczność i jest zgodna z poprzednimi wersjami. Zacznijmy od elastyczności. Klasa System. EventArgs wprowadza jedną metodę: `MemberwiseClone()`, która tworzy skróconą kopię obiektu.
Ta metoda musi używać odbicia w celu zaimplementowania jej funkcjonalności dla każdej klasy pochodnej z `EventArgs`. Ta funkcja jest łatwiejsza do utworzenia w określonej klasie pochodnej. To efektywnie oznacza, że pochodny from system. EventArgs to ograniczenie, które ogranicza Twoje projekty, ale nie zapewnia dodatkowej korzyści.
W rzeczywistości można zmienić definicje `FileFoundArgs` i `SearchDirectoryArgs`, aby nie pochodzą one z `EventArgs`.
Program będzie działał dokładnie tak samo.

Możesz również zmienić `SearchDirectoryArgs` na strukturę, jeśli wprowadzisz nową zmianę:

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

Dodatkowa zmiana polega na wywołaniu konstruktora bez parametrów przed wprowadzeniem konstruktora, który inicjuje wszystkie pola. Bez tego dołączenia reguły C# będą zgłaszać dostęp do właściwości przed ich przypisaniem.

Nie należy zmieniać `FileFoundArgs` z klasy (typ odwołania) do struktury (typ wartości). Wynika to z faktu, że protokół do obsługi anulowania wymaga, aby argumenty zdarzenia zostały przekazane przez odwołanie. Jeśli została wprowadzona taka sama zmiana, Klasa wyszukiwania plików nigdy nie zaobserwuje żadnych zmian dokonanych przez żadnego z subskrybentów zdarzeń. Nowa kopia struktury będzie używana dla każdego subskrybenta, a kopia będzie inną kopią niż ta, która jest widoczna dla obiektu wyszukiwanie plików.

Następnie Rozważmy, jak ta zmiana może być zgodna z poprzednimi wersjami.
Usunięcie ograniczenia nie ma wpływu na żaden istniejący kod. Wszystkie istniejące typy argumentów zdarzeń nadal pochodzą z `System.EventArgs`.
Zgodność z poprzednimi wersjami to jeden z głównych powodów, dla których nadal będą pochodzić z `System.EventArgs`. Wszyscy istniejący Subskrybenci zdarzeń będą subskrybentami zdarzeń, które przestrzegają wzorca klasycznego.

Podobnie jak w przypadku podobnej logiki, każdy typ argumentu zdarzenia utworzony teraz nie może mieć żadnych subskrybentów w żadnej z istniejących baz kodu. Nowe typy zdarzeń, które nie pochodzą z `System.EventArgs`, nie spowodują przerwania tych baz kodu.

## <a name="events-with-async-subscribers"></a>Zdarzenia z subskrybentami asynchronicznymi

Masz jeden ostateczny wzorzec, aby dowiedzieć się: jak poprawnie napisać abonentów zdarzeń, które wywołują kod asynchroniczny. Wyzwanie zostało opisane w artykule dotyczącym [Async i await](async.md). Metody asynchroniczne mogą mieć typ zwracany void, ale nie jest to zdecydowanie odradzane. Gdy kod abonenta zdarzenia wywołuje metodę asynchroniczną, nie ma możliwości wyboru, ale do utworzenia metody `async void`. Podpis procedury obsługi zdarzeń wymaga tego.

Należy uzgodnić te przeciwstawne wskazówki. W dowolny sposób należy utworzyć bezpieczną metodę `async void`. Poniżej przedstawiono podstawowe informacje na temat wzorca, który należy zaimplementować:

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

Najpierw należy zauważyć, że program obsługi jest oznaczony jako procedura obsługi asynchronicznej. Ponieważ jest przypisywany do typu delegata programu obsługi zdarzeń, będzie miał typ zwracany void. Oznacza to, że należy postępować zgodnie z wzorcem wyświetlanym w obsłudze i nie zezwalać na wyrzucanie wyjątków z kontekstu procedury obsługi asynchronicznej. Ponieważ nie zwraca zadania, nie istnieje zadanie, które może zgłosić błąd, wprowadzając stan błędu. Ponieważ metoda jest asynchroniczna, metoda nie może po prostu zgłosić wyjątku. (Metoda wywołująca kontynuuje wykonywanie, ponieważ jest `async`.) Rzeczywiste zachowanie środowiska uruchomieniowego zostanie zdefiniowane inaczej dla różnych środowisk. Może zakończyć wątek lub proces, który jest właścicielem wątku, lub pozostawić proces w nieokreślonym stanie. Wszystkie te potencjalne wyniki są wysoce niepożądane.

Dlatego należy zawinąć instrukcję await dla zadania asynchronicznego we własnym bloku try. Jeśli zadanie spowoduje wystąpienie błędu, można go zarejestrować. Jeśli jest to błąd, z którego aplikacja nie może odzyskać, można szybko i bezpiecznie zakończyć działanie programu

Są to główne aktualizacje wzorca zdarzeń platformy .NET. Zobaczysz wiele przykładów wcześniejszych wersji w bibliotekach, z którymi pracujesz. Należy jednak zrozumieć, jakie są również Najnowsze wzorce.

Następny artykuł z tej serii ułatwia rozróżnienie między `delegates`ami i `events` w projektach. Są to podobne koncepcje i ten artykuł pomoże Ci w podejmowaniu najlepszej decyzji dla programów.

[Next](distinguish-delegates-events.md)
