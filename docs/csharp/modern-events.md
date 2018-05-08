---
title: Wzorzec zdarzenie Core zaktualizowanej platformy .NET
description: Dowiedz się, jak wzorzec zdarzenia platformy .NET Core umożliwia elastyczność zapewnienia zgodności i implementowania przetwarzania zdarzeń bezpieczne z subskrybentami asynchronicznego.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: d0ad85479265041d895039d6c72f1f9909ea5fa8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="the-updated-net-core-event-pattern"></a>Wzorzec zdarzenie Core zaktualizowanej platformy .NET

[Poprzednie](event-pattern.md)

Poprzednim artykule opisano najbardziej typowe wzorce zdarzeń. Oprogramowanie .NET core ma użycie wzorca. W tej wersji `EventHandler<TEventArgs>` definicja zawiera już ograniczenie który `TEventArgs` musi być klasą pochodną `System.EventArgs`.

Zwiększa to elastyczność dla Ciebie i jest wstecznie zgodna. Zacznijmy od elastyczność. Klasa System.EventArgs wprowadza jedną metodę: `MemberwiseClone()`, który tworzy kopię pobieżną obiektu.
Metoda musi używać odbicia w celu wdrożenia jego działanie dla wszystkich klas pochodnych `EventArgs`. Ta funkcjonalność jest łatwiejsze do tworzenia w określonej klasy pochodnej. Które skutecznie oznacza, że pochodny System.EventArgs ograniczenia, które ogranicza projektów, ale nie ma żadnych dodatkowych korzyści.
W rzeczywistości zmienia się z definicjami `FileFoundArgs` i `SearchDirectoryArgs` tak, aby nie pochodzą one od `EventArgs`.
Program będzie działać dokładnie tak samo.

Można również zmienić `SearchDirectoryArgs` strukturę, jeśli wprowadzisz zmiany więcej jeden:

```csharp  
internal struct SearchDirectoryArgs  
{  
    internal string CurrentSearchDirectory { get; }  
    internal int TotalDirs { get; }  
    internal int CompletedDirs { get; }  
    
    internal SearchDirectoryArgs(string dir, int totalDirs, 
        int completedDirs) : this()  
    {  
        CurrentSearchDirectory = dir;  
        TotalDirs = totalDirs;  
        CompletedDirs = completedDirs;  
    }  
}  
```   

Dodatkowe zmiana ma na celu wywołania konstruktora domyślnego przed wprowadzeniem Konstruktor, który inicjuje wszystkie pola. Bez tego dodatku reguły języka C# rozpoczną przesyłanie raportów, że właściwości są dostępne przed zostały przypisane.

Nie należy zmieniać `FileFoundArgs` z klasy (typ odwołania) na strukturę (typ wartości). To, ponieważ protokół obsługi anulowania wymaga, czy argumenty zdarzeń są przekazywane przez odwołanie. Jeśli wprowadzono zmiany w tej samej klasy wyszukiwania plików nigdy nie można obserwować zmiany wprowadzone przez wszystkich subskrybentów zdarzeń. Nową kopię struktury będzie używany na potrzeby każdego subskrybenta, a tej kopii będzie kopię innego niż widoczne dla obiekt wyszukiwania plików.

Następnie zastanówmy się, jak ta zmiana może być wstecznie zgodne.
Usunięcie ograniczenie nie ma wpływu na istniejący kod. Wszystkie istniejące typy argumentów zdarzenia nadal pochodzić od `System.EventArgs`.
Zapewnienia zgodności jest główną przyczyną Dlaczego będą one nadal pochodzić od `System.EventArgs`. Wszystkie istniejące subskrybentów zdarzeń będzie subskrybentów do zdarzenia, a następnie klasycznego wzorzec.

Po każdym podobne logiki codebases utworzony typ teraz nie będzie zawierało żadnych subskrybentów w żadnych istniejących argumentu zdarzenia. Nowe typy zdarzeń, które nie pochodzą z `System.EventArgs` będzie przerwać tych codebases.

## <a name="events-with-async-subscribers"></a>Zdarzenia z subskrybentami Async

Masz jeden wzorzec końcowego Aby dowiedzieć się więcej: jak poprawnie zapisać subskrybentów zdarzeń, wywołujące kod asynchronicznego. Żądanie jest opisany w artykule na [async i await](async.md). Metody asynchroniczne może mieć zwracanego typu void, ale jest to zdecydowanie niezalecane. Gdy kod subskrybenta zdarzeń wywołuje metody asynchronicznej, masz nie choice, a do utworzenia `async void` metody. Podpis programu obsługi zdarzeń wymagają.

Należy uzgodnić tych przeciwna wskazówek. Aplikacja, należy utworzyć sejfie `async void` metody. Podstawowe informacje potrzebne do zaimplementowania wzorca się poniżej:

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

Po pierwsze Zwróć uwagę, czy program obsługi jest oznaczony jako program obsługi asynchronicznego. Ponieważ jest ona obecnie przypisywana do programu obsługi zdarzeń typ delegowany, będzie mieć zwrócony typ void. Oznacza to, należy zgodne ze wzorcem wyświetlany w obsłudze, a nie zezwalaj na wyjątki zostanie wygenerowany poza kontekstem obsługi async. Ponieważ nie zwraca zadania, brak nie można zgłosić błąd, wprowadzając stan zadania. Ponieważ metoda jest asynchroniczne, metody nie można po prostu zgłosić wyjątek. (Nadal wykonanie wywołania metody, ponieważ jest on `async`.) Rzeczywiste działanie zostanie określony inaczej dla różnych środowisk. Może zakończyć wątek, może zakończyć program lub mogłoby to spowodować program nieokreślony stan. Żaden z tych nie jest dobrym wyników.

Dlatego powinna być zawijana instrukcja await asynchroniczne zadanie w własne bloku try. Jeśli powoduje ona błędnej zadań, możesz zalogować się kod błędu. Jeśli jest błąd, z którego nie można odzyskać aplikacji, można zamknąć program szybko i bezpiecznie

Są to wprowadzono znaczące aktualizacje z wzorcem zdarzenia platformy .NET. Zostanie wyświetlone wiele przykładów starszych wersji w pracy z bibliotekami. Jednak należy zrozumieć, jakie najnowsze wzorce są również.

W tym artykule pomaga odróżnić przy użyciu `delegates` i `events` w projektach. Są one podobne pojęcia i ten artykuł pomoże Ci podjęcie najlepszych decyzji programów.

[Next](distinguish-delegates-events.md)
