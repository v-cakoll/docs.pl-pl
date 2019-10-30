---
title: Standardowe wzorce zdarzeń platformy .NET
description: Dowiedz się więcej o wzorcach zdarzeń .NET i sposobach tworzenia standardowych źródeł zdarzeń oraz subskrybowania i przetwarzania standardowych zdarzeń w kodzie.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: a050dc9a11470ff3b71488ce2ab4b92e607aa9b0
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037171"
---
# <a name="standard-net-event-patterns"></a>Standardowe wzorce zdarzeń platformy .NET

[Ubiegł](events-overview.md)

Zdarzenia platformy .NET zwykle są zgodne z kilkoma znanymi wzorcami. Ujednolicenie tych wzorców oznacza, że deweloperzy mogą korzystać z wiedzy o standardowych wzorcach, które można zastosować do dowolnego programu zdarzeń platformy .NET.

Przyjrzyjmy się tym standardowym wzorcem, dzięki czemu będziesz mieć wszystkie informacje potrzebne do tworzenia standardowych źródeł zdarzeń oraz subskrybować i przetwarzać standardowe zdarzenia w kodzie.

## <a name="event-delegate-signatures"></a>Sygnatury delegatów zdarzeń

Podpis standardowy dla delegata zdarzenia .NET to:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Zwracany typ to void. Zdarzenia są oparte na delegatach i są delegatami multiemisji. Obsługuje wielu subskrybentów dla każdego źródła zdarzeń. Pojedyncza wartość zwracana z metody nie jest skalowana do wielu subskrybentów zdarzeń. Która wartość zwracana jest wyświetlana przez Źródło zdarzenia po podwyższeniu poziomu zdarzenia? W dalszej części tego artykułu zobaczysz, jak utworzyć protokoły zdarzeń obsługujące Subskrybenci zdarzeń, które zgłaszają informacje do źródła zdarzeń.

Lista argumentów zawiera dwa argumenty: nadawca i argumenty zdarzenia. Typ czasu kompilacji `sender` jest `System.Object`, nawet jeśli prawdopodobnie znasz bardziej pochodny typ, który zawsze będzie prawidłowy. Zgodnie z Konwencją Użyj `object`.

Drugi argument jest zazwyczaj typem, który jest pochodną `System.EventArgs`. (Zobaczysz w [następnej sekcji](modern-events.md) , że ta konwencja nie jest już wymuszana). Jeśli typ zdarzenia nie wymaga żadnych dodatkowych argumentów, nadal będą dostępne oba argumenty.
Istnieje specjalna wartość `EventArgs.Empty`, która powinna być używana do określenia, że zdarzenie nie zawiera żadnych dodatkowych informacji.

Utwórzmy klasę, która wyświetla listę plików w katalogu lub dowolnego podkatalogów, które są zgodne ze wzorcem. Ten składnik zgłasza zdarzenie dla każdego znalezionego pliku, który pasuje do wzorca.

Korzystanie z modelu zdarzeń zapewnia pewne zalety projektowania. Można utworzyć wiele detektorów zdarzeń, które wykonują różne akcje po znalezieniu szukanego pliku. Łącząc różne detektory, można tworzyć bardziej niezawodne algorytmy.

Oto początkowa deklaracja argumentu zdarzenia do znajdowania szukanego pliku: 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

Mimo że ten typ wygląda jak mały typ danych, należy przestrzegać Konwencji i wprowadzić jako typ odwołania (`class`). Oznacza to, że obiekt argumentu zostanie przesłany przez odwołanie, a wszystkie aktualizacje danych będą widoczne dla wszystkich subskrybentów. Pierwsza wersja jest niezmiennym obiektem. Należy preferować, aby właściwości w typie argumentu zdarzenia były niezmienne. Dzięki temu jeden subskrybent nie może zmienić wartości przed ich wyświetleniem przez innego subskrybenta. (Istnieją wyjątki dotyczące tego, jak pokazano poniżej).  

Następnie musimy utworzyć deklarację zdarzenia w klasie FileSearcher. Korzystanie z typu `EventHandler<T>` oznacza, że nie trzeba tworzyć jeszcze innej definicji typu. Wystarczy użyć ogólnej specjalizacji.

Wypełnijmy klasę FileSearcher, aby wyszukać pliki pasujące do wzorca, i podnieść poprawne zdarzenie, gdy zostanie odnalezione dopasowanie.

[!code-csharp[FileSearcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a>Definiowanie i podnoszenie zdarzeń przypominających pola

Najprostszym sposobem dodania zdarzenia do klasy jest zadeklarowanie tego zdarzenia jako pola publicznego, jak w poprzednim przykładzie:

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

Wygląda na to, że deklaruje pole publiczne, które wydaje się być niewłaściwym sposobem postępowania zorientowanego obiektowo. Chcesz chronić dostęp do danych za poorednictwem właściwości lub metod. Chociaż może to wyglądać jak niewłaściwe rozwiązanie, kod wygenerowany przez kompilator tworzy otoki, tak aby obiekty zdarzeń były dostępne tylko w bezpieczny sposób. Jedyne operacje dostępne na zdarzeniu podobnym do pola to procedura obsługi dodawania:

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

i Usuń procedurę obsługi:

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

Należy zauważyć, że dla programu obsługi istnieje zmienna lokalna. Jeśli użyto treści wyrażenia lambda, usuwanie nie będzie działało poprawnie. Będzie ono innym wystąpieniem delegata i w trybie dyskretnym nic nie rób.

Kod poza klasą nie może zgłosić zdarzenia, ani nie może wykonać żadnych innych operacji.

## <a name="returning-values-from-event-subscribers"></a>Zwracanie wartości z subskrybentów zdarzeń

Twoja wersja prosta działa prawidłowo. Dodajmy kolejną funkcję: anulowanie.

Po podniesieniu wykrytego zdarzenia odbiorniki powinny być w stanie przerwać dalsze przetwarzanie, jeśli ten plik jest ostatnim z nich.

Programy obsługi zdarzeń nie zwracają wartości, dlatego należy komunikować się w inny sposób. Standardowy wzorzec zdarzeń używa obiektu EventArgs do dołączania pól, których Subskrybenci mogą używać do komunikowania się z anulowaniem.

Istnieją dwa różne wzorce, których można użyć na podstawie semantyki kontraktu anulowania. W obu przypadkach należy dodać pole Boolean do EventArguments dla znalezionego zdarzenia pliku. 

Jeden wzorzec zezwoli jednemu subskrybentowi na anulowanie operacji.
Dla tego wzorca nowe pole jest inicjowane w celu `false`. Każdy subskrybent może zmienić go na `true`. Gdy Wszyscy subskrybenci napotkają zgłoszone zdarzenie, składnik FileSearcher analizuje wartość logiczną i wykonuje akcję.

Drugi wzorzec spowoduje anulowanie operacji tylko wtedy, gdy Wszyscy subskrybenci chcieli operacja została anulowana. W tym wzorcu nowe pole jest inicjowane w celu wskazania, że operacja powinna zostać anulowana, a każdy subskrybent może ją zmienić, aby wskazać, że operacja powinna być kontynuowana.
Gdy Wszyscy subskrybenci napotkają zgłoszone zdarzenie, składnik FileSearcher analizuje wartość logiczną i wykonuje akcję. Ten wzorzec zawiera jeden dodatkowy krok: składnik musi wiedzieć, czy każdy subskrybent widział zdarzenie. Jeśli nie ma subskrybentów, pole wskazuje nieprawidłowe anulowanie.

Zaimplementujmy pierwszą wersję dla tego przykładu. Należy dodać pole Boolean o nazwie `CancelRequested` do typu `FileFoundArgs`:

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

To nowe pole jest automatycznie inicjowane w celu `false`, wartości domyślnej pola Boolean, więc nie można go anulować przypadkowo. Jedyną inną zmianą w składniku jest sprawdzenie flagi po podniesieniu zdarzenia, aby sprawdzić, czy którykolwiek z subskrybentów zażądał anulowania:

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

Jedną z zalet tego wzorca jest to, że nie jest to istotna zmiana.
Żaden z subskrybentów nie zażądał anulowania przed i nadal nie jest. Żaden kod subskrybenta nie wymaga aktualizacji, chyba że chcą obsługiwać nowy protokół anulowania. Jest ona bardzo luźno powiązana.

Zaktualizujmy subskrybenta, aby zażądał anulowania po znalezieniu pierwszego pliku wykonywalnego:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Dodawanie kolejnej deklaracji zdarzenia

Dodajmy jeszcze jedną funkcję i zademonstrowasz inne idiomy języka dla zdarzeń. Dodajmy Przeciążenie metody `Search`, która przechodzi przez wszystkie podkatalogi w poszukiwaniu plików.

Może to być długotrwała operacja w katalogu z wieloma katalogami podrzędnymi. Dodajmy zdarzenie, które zostanie wywołane po rozpoczęciu każdego nowego wyszukiwania w katalogu. Dzięki temu Subskrybenci mogą śledzić postęp i aktualizować użytkownika w miarę postępu. Wszystkie utworzone dotąd przykłady są publiczne. Utwórzmy to zdarzenie wewnętrzne. Oznacza to, że można również uczynić typy używane dla argumentów wewnętrznie.

Zacznij od utworzenia nowej klasy pochodnej EventArgs na potrzeby raportowania nowego katalogu i postępu. 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Ponownie można postępować zgodnie z zaleceniami, aby utworzyć niezmienny typ referencyjny dla argumentów zdarzeń.

Następnie zdefiniuj zdarzenie. Tym razem użyjesz innej składni. Oprócz używania składni pola można jawnie utworzyć właściwość z obsługą dodawania i usuwania. W tym przykładzie nie będzie potrzebny dodatkowy kod w tych procedurach obsługi, ale pokazano, jak je utworzyć.

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

Na wiele sposobów kod napisany w tym miejscu odzwierciedla kod wygenerowany przez kompilator dla definicji zdarzenia pól, które wcześniej były widoczne. Tworzysz wydarzenie przy użyciu składni podobnej do tej, która jest używana do [Właściwości](properties.md). Należy zauważyć, że programy obsługi mają różne nazwy: `add` i `remove`. Są one wywoływane, aby subskrybować zdarzenie lub anulować subskrypcję zdarzenia. Zwróć uwagę, że należy również zadeklarować prywatne pole zapasowe do przechowywania zmiennej zdarzenia. Jest ona zainicjowana na wartość null.

Następnie Dodajmy Przeciążenie metody `Search`, która przechodzi podkatalogi i wywołuje oba zdarzenia. Najprostszym sposobem osiągnięcia tego celu jest użycie domyślnego argumentu w celu określenia, czy chcesz przeszukać wszystkie katalogi:

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

W tym momencie można uruchomić aplikację wywołującą Przeciążenie do przeszukiwania wszystkich podkatalogów. Nie ma subskrybentów nowego zdarzenia `ChangeDirectory`, ale użycie `?.Invoke()` idiom gwarantuje, że działa poprawnie.

 Dodajmy procedurę obsługi, aby napisać wiersz pokazujący postęp w oknie konsoli. 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

Pojawiły się wzorce, które są obserwowane w całym ekosystemie platformy .NET.
Poznanie tych wzorców i Konwencji umożliwia szybkie pisanie idiomatyczne C# i platformy .NET.

Następnie zobaczysz pewne zmiany w tych wzorcach w najnowszej wersji programu .NET.

[Next](modern-events.md)
