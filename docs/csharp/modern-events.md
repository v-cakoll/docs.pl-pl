---
title: Zaktualizowany wzorzec zdarzenia rdzenia .NET
description: Dowiedz się, jak wzorzec zdarzenia .NET Core umożliwia elastyczność zgodności z poprzednimi wersjami i jak zaimplementować bezpieczne przetwarzanie zdarzeń z subskrybentami asynchronii.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: c8858158ede761db8a3002beb26e521880f77feb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170439"
---
# <a name="the-updated-net-core-event-pattern"></a>Zaktualizowany wzorzec zdarzenia rdzenia .NET

[Wstecz](event-pattern.md)

W poprzednim artykule omówiono najczęstsze wzorce zdarzeń. .NET Core ma bardziej zrelaksowany wzór. W tej wersji `EventHandler<TEventArgs>` definicja nie ma już `TEventArgs` ograniczenia, które musi `System.EventArgs`być klasą wywodzącą się z .

Zwiększa to elastyczność i jest zgodne z poprzednimi wersjami. Zacznijmy od elastyczności. Klasa System.EventArgs wprowadza jedną `MemberwiseClone()`metodę: , która tworzy płytką kopię obiektu.
Metoda ta musi używać odbicia w celu zaimplementowania `EventArgs`jego funkcji dla dowolnej klasy pochodzącej z . Ta funkcja jest łatwiejsze do utworzenia w określonej klasie pochodnej. Oznacza to, że wynikające z System.EventArgs jest ograniczeniem, które ogranicza projekty, ale nie zapewnia żadnych dodatkowych korzyści.
W rzeczywistości można zmienić definicje `FileFoundArgs` `SearchDirectoryArgs` i tak, aby nie `EventArgs`pochodzą one z .
Program będzie działał dokładnie tak samo.

Można również zmienić `SearchDirectoryArgs` strukturę, jeśli włożysz jeszcze jedną zmianę:

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

Dodatkową zmianą jest wywołanie konstruktora bez parametrów przed wejściem do konstruktora, który inicjuje wszystkie pola. Bez tego dodatku reguły Języka C# zgłaszałyby, że właściwości są dostępne przed ich przypisaniem.

Nie należy zmieniać `FileFoundArgs` z klasy (typ odwołania) na strukturę (typ wartości). Dzieje się tak, ponieważ protokół do obsługi anulowania wymaga, aby argumenty zdarzenia były przekazywane przez odwołanie. Jeśli ta sama zmiana została wniesiona, klasa wyszukiwania plików nigdy nie będzie mogła zaobserwować żadnych zmian dokonanych przez subskrybentów zdarzeń. Nowa kopia struktury będzie używana dla każdego subskrybenta, a ta kopia będzie inną kopią niż ta widoczna dla obiektu wyszukiwania plików.

Następnie zastanówmy się, jak ta zmiana może być wstecznie zgodna.
Usunięcie ograniczenia nie ma wpływu na istniejący kod. Wszystkie istniejące typy argumentów zdarzeń nadal pochodzą z `System.EventArgs`.
Wsteczna kompatybilność jest jednym z głównych powodów, `System.EventArgs`dla których będą nadal pochodzić z . Wszystkich istniejących subskrybentów zdarzeń będą subskrybentami zdarzenia, które następuje klasyczny wzorzec.

Zgodnie z podobną logiką każdy typ argumentu zdarzenia utworzony teraz nie będzie miał żadnych subskrybentów w istniejących baz kodu. Nowe typy zdarzeń, które `System.EventArgs` nie pochodzą z nie spowoduje przerwania tych baz kodu.

## <a name="events-with-async-subscribers"></a>Wydarzenia z subskrybentami Async

Masz jeden końcowy wzorzec, aby dowiedzieć się: Jak poprawnie napisać subskrybentów zdarzeń, które wywołają kod asynchronii. Wyzwanie jest opisane w artykule na [async i czekają](async.md). Metody asynchroniczne mogą mieć typ zwracania void, ale jest to zdecydowanie odradzane. Gdy kod subskrybenta zdarzenia wywołuje metodę asynchronia, nie `async void` masz wyboru, jak tylko utworzyć metodę. Wymaga tego podpis programu obsługi zdarzeń.

Musisz pogodzić to przeciwstawne wskazówki. W jakiś sposób musisz `async void` stworzyć bezpieczną metodę. Podstawy wzoru, który musisz zaimplementować, są poniżej:

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

Po pierwsze należy zauważyć, że program obsługi jest oznaczony jako program obsługi asynchronicznej. Ponieważ jest on przypisany do typu delegata obsługi zdarzeń, będzie miał typ zwracany void. Oznacza to, że należy postępować zgodnie z wzorcem pokazano w programie obsługi i nie zezwalaj na wszelkie wyjątki, które mają być odrzucane z kontekstu programu obsługi asynchronicznej. Ponieważ nie zwraca zadania, nie ma żadnego zadania, które można zgłosić błąd, wprowadzając stan błędu. Ponieważ metoda jest async, metoda nie można po prostu zgłosić wyjątek. (Metoda wywołująca ma dalsze wykonywanie, ponieważ jest `async`.) Rzeczywiste zachowanie środowiska uruchomieniowego zostanie zdefiniowane inaczej dla różnych środowisk. Może zakończyć wątek lub proces, który jest właścicielem wątku lub pozostawić proces w stanie nieokreślony. Wszystkie te potencjalne wyniki są wysoce niepożądane.

Dlatego należy owinąć await instrukcji dla zadania asynchronicznego w swoim własnym bloku try. Jeśli powoduje to wadliwe zadanie, można rejestrować błąd. Jeśli jest to błąd, z którego aplikacja nie może odzyskać, można zamknąć program szybko i z wdziękiem

Są to główne aktualizacje wzorca zdarzeń .NET. Zobaczysz wiele przykładów wcześniejszych wersji w bibliotekach, z których pracujesz. Jednak należy zrozumieć, jakie są najnowsze wzorce, jak również.

Następny artykuł z tej serii pomaga `delegates` `events` odróżnić użycie i w projektach. Są to podobne pojęcia, a ten artykuł pomoże Ci podjąć najlepszą decyzję dla twoich programów.

[Dalej](distinguish-delegates-events.md)
