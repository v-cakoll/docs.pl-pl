---
title: Standardowe wzorce zdarzeń platformy .NET
description: Dowiedz się więcej o wzorcach zdarzeń programu .NET oraz o tym, jak tworzyć standardowe źródła zdarzeń oraz subskrybować i przetwarzać zdarzenia standardowe w kodzie.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: dec516767e43a6bf4edfa555e34f3adcc21a46e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146144"
---
# <a name="standard-net-event-patterns"></a>Standardowe wzorce zdarzeń platformy .NET

[Wstecz](events-overview.md)

Zdarzenia .NET zazwyczaj wykonaj kilka znanych wzorców. Standaryzacja tych wzorców oznacza, że deweloperzy mogą wykorzystać wiedzę na temat tych wzorców standardowych, które mogą być stosowane do dowolnego programu zdarzeń .NET.

Przejdźmy przez te wzorce standardowe, dzięki czemu będziesz miał całą wiedzę potrzebną do tworzenia standardowych źródeł zdarzeń i subskrybowania i przetwarzania standardowych zdarzeń w kodzie.

## <a name="event-delegate-signatures"></a>Podpisy delegatów zdarzeń

Standardowy podpis pełnomocnika zdarzenia .NET to:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Typ zwracany jest nieważny. Zdarzenia są oparte na delegatów i są delegatów multiemisji. Który obsługuje wielu subskrybentów dla dowolnego źródła zdarzeń. Pojedyncza wartość zwracana z metody nie jest skalowana do wielu subskrybentów zdarzeń. Jaką wartość zwracaną widzi źródło zdarzenia po zgłoszeniu zdarzenia? W dalszej części tego artykułu zobaczysz, jak utworzyć protokoły zdarzeń, które obsługują subskrybentów zdarzeń, które zgłaszają informacje do źródła zdarzenia.

Lista argumentów zawiera dwa argumenty: nadawcę i argumenty zdarzenia. Typ czasu kompilacji `sender` `System.Object`jest , nawet jeśli prawdopodobnie znasz typ bardziej pochodny, który zawsze będzie poprawny. Zgodnie z `object`konwencją użyj .

Drugi argument jest zazwyczaj typem, który `System.EventArgs`pochodzi od . (W [następnej sekcji](modern-events.md) zobaczysz, że ta konwencja nie jest już wymuszana). Jeśli typ zdarzenia nie wymaga żadnych dodatkowych argumentów, nadal będzie podać oba argumenty.
Istnieje specjalna wartość, `EventArgs.Empty` której należy użyć do oznaczenia, że zdarzenie nie zawiera żadnych dodatkowych informacji.

Skompilujmy klasę, która wyświetla listę plików w katalogu lub dowolną z jego podkatalogów, które postępują zgodnie z wzorcem. Ten składnik wywołuje zdarzenie dla każdego znalezionego pliku, które pasuje do wzorca.

Korzystanie z modelu zdarzeń zapewnia pewne zalety projektu. Można utworzyć wiele detektorów zdarzeń, które wykonują różne akcje po znalezieniu poszukiwanego pliku. Łączenie różnych odbiorników można utworzyć bardziej niezawodne algorytmy.

Oto wstępne oświadczenie argument zdarzenia dla znalezienia poszukiwanego pliku:

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

Mimo że ten typ wygląda jak mały typ tylko do danych, należy`class`postępować zgodnie z konwencją i uczynić go odwołaniem ( ) typu. Oznacza to, że obiekt argumentu będą przekazywane przez odwołanie, a wszelkie aktualizacje danych będą wyświetlane przez wszystkich subskrybentów. Pierwsza wersja jest obiektem niezmiennym. Wolisz, aby właściwości w typie argumentu zdarzenia były niezmienne. W ten sposób jeden subskrybent nie może zmienić wartości, zanim inny subskrybent je zobaczy. (Istnieją wyjątki od tej reguły, jak widać poniżej.)  

Następnie należy utworzyć deklarację zdarzenia w FileSearcher klasy. Wykorzystanie `EventHandler<T>` tego typu oznacza, że nie trzeba tworzyć jeszcze innej definicji typu. Wystarczy użyć ogólnej specjalizacji.

Wypełnijmy FileSearcher klasy, aby wyszukać pliki, które pasują do wzorca i podnieść poprawne zdarzenie, gdy dopasowanie jest wykrywany.

[!code-csharp[FileSearcher](../../samples/snippets/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a>Definiowanie i podnoszenie zdarzeń podobnych do pola

Najprostszym sposobem dodania zdarzenia do klasy jest zadeklarowanie tego zdarzenia jako pola publicznego, jak w poprzednim przykładzie:

[!code-csharp[DeclareEvent](../../samples/snippets/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

Wygląda na to, że deklaruje pole publiczne, które wydaje się być złą praktyką obiektową. Chcesz chronić dostęp do danych za pomocą właściwości lub metod. Chociaż może to wyglądać na złe praktyki, kod generowany przez kompilator tworzy otoki, dzięki czemu obiekty zdarzeń są dostępne tylko w bezpieczny sposób. Jedynymi operacjami dostępnymi w zdarzeniu przypominanym z pola są program obsługi dodawania:

[!code-csharp[DeclareEventHandler](../../samples/snippets/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

i usuń program obsługi:

[!code-csharp[RemoveEventHandler](../../samples/snippets/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

Należy zauważyć, że istnieje zmienna lokalna dla programu obsługi. Jeśli używasz ciała lambda, usunięcie nie będzie działać poprawnie. Byłoby to inne wystąpienie delegata i po cichu nic nie robić.

Kod poza klasą nie może wywołać zdarzenia, ani nie może wykonywać żadnych innych operacji.

## <a name="returning-values-from-event-subscribers"></a>Zwracanie wartości od subskrybentów zdarzeń

Twoja prosta wersja działa dobrze. Dodajmy kolejną funkcję: Anulowanie.

Po wywołaniu znalezionego zdarzenia, detektory powinny być w stanie zatrzymać dalsze przetwarzanie, jeśli ten plik jest ten ostatni poszukiwany.

Programy obsługi zdarzeń nie zwracają wartość, więc należy komunikować się, że w inny sposób. Standardowy wzorzec zdarzenia używa EventArgs obiektu do uwzględnienia pól, które subskrybenci zdarzeń mogą używać do komunikowania się anulować.

Istnieją dwa różne wzorce, które mogą być używane, na podstawie semantyki anuluj umowy. W obu przypadkach do zdarzenia znalezionego pliku zostanie dodane pole logiczne.

Jeden wzorzec pozwoli jeden subskrybent anulować operację.
Dla tego wzorca nowe pole `false`jest inicjowane do . Każdy subskrybent może go `true`zmienić na . Po wszystkich subskrybentów widzieli zdarzenie wywoływane, FileSearcher składnik sprawdza wartość logiczną i wykonuje akcję.

Drugi wzorzec tylko anulować operację, jeśli wszyscy subskrybenci chcieli operacji anulowane. W tym wzorcu nowe pole jest inicjowane, aby wskazać, że operacja powinna zostać anulowana, a każdy subskrybent może ją zmienić, aby wskazać, że operacja powinna być kontynuowana.
Po wszystkich subskrybentów widzieli zdarzenie wywoływane, FileSearcher składnik sprawdza wartość logiczną i wykonuje akcję. Istnieje jeden dodatkowy krok w tym wzorcu: składnik musi wiedzieć, czy subskrybenci widzieli zdarzenie. Jeśli nie ma subskrybentów, pole będzie oznaczać anuluj niepoprawnie.

Zaimplementujmy pierwszą wersję dla tego przykładu. Do `FileFoundArgs` typu należy dodać pole `CancelRequested` logiczne o nazwie:

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgs "Update event arguments")]

To nowe pole jest automatycznie `false`inicjowane do wartości domyślnej dla pola logicznego, dzięki czemu nie można anulować przypadkowo. Jedyną inną zmianą w składniku jest sprawdzenie flagi po zgłoszeniu zdarzenia, aby sprawdzić, czy którykolwiek z subskrybentów zażądał anulowania:

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

Jedną z zalet tego wzorca jest to, że nie jest to przełomowa zmiana.
Żaden z subskrybentów zażądał anulowania wcześniej i nadal nie są. Żaden z kodu subskrybenta wymaga aktualizacji, chyba że chce obsługiwać nowy protokół anulowania. Jest bardzo luźno sprzęgł.

Zaktualizujmy subskrybenta tak, aby żądał anulowania po znalezieniu pierwszego pliku wykonywalnego:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Dodawanie innej deklaracji zdarzenia

Dodajmy jeszcze jedną funkcję i zademonstrujmy inne idiomy języka dla zdarzeń. Dodajmy przeciążenie `Search` metody, która przechodzi przez wszystkie podkatalogi w poszukiwaniu plików.

Może to być długa operacja w katalogu z wieloma podkatalogami. Dodajmy zdarzenie, które zostanie podniesione po rozpoczęciu każdego nowego wyszukiwania w katalogu. Dzięki temu subskrybenci śledzić postęp i zaktualizować użytkownika w miarę postępu. Wszystkie przykłady, które zostały utworzone do tej pory są publiczne. Zróbmy to wydarzenie wewnętrzne. Oznacza to, że można również dokonać typów używanych dla argumentów wewnętrzny, jak również.

Rozpoczniesz od utworzenia nowej klasy pochodnej EventArgs do raportowania nowego katalogu i postępu.

[!code-csharp[DirEventArgs](../../samples/snippets/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Ponownie można wykonać zalecenia, aby niezmienny typ odwołania dla argumentów zdarzenia.

Następnie zdefiniuj zdarzenie. Tym razem użyjesz innej składni. Oprócz używania składni pola, można jawnie utworzyć właściwość, z dodawaniem i usuwaniem programów obsługi. W tym przykładzie nie będzie potrzebny dodatkowy kod w tych programach obsługi, ale to pokazuje, jak można je utworzyć.

[!code-csharp[Declare event with add and remove handlers](../../samples/snippets/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

Na wiele sposobów kod, który piszesz w tym miejscu odzwierciedla kod kompilator generuje dla definicji zdarzeń pola, które widziałeś wcześniej. Zdarzenie można utworzyć przy użyciu składni bardzo podobnej do tej używanej dla [właściwości](properties.md). Należy zauważyć, że programy `add` obsługi `remove`mają różne nazwy: i . Są one wywoływane, aby zapisać się do zdarzenia lub zrezygnować z wydarzenia. Należy zauważyć, że należy również zadeklarować prywatne pole zapasowe do przechowywania zmiennej zdarzenia. Jest inicjowany do wartości null.

Następnie dodajmy przeciążenie `Search` metody, która przechodzi przez podkatalogi i wywołuje oba zdarzenia. Najprostszym sposobem osiągnięcia tego celu jest użycie argumentu domyślnego w celu określenia, że chcesz przeszukać wszystkie katalogi:

[!code-csharp[SearchImplementation](../../samples/snippets/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

W tym momencie można uruchomić aplikację wywołującą przeciążenie do wyszukiwania wszystkich podkatalogów. Nie ma subskrybentów `ChangeDirectory` na nowe wydarzenie, ale przy użyciu `?.Invoke()` idiomu zapewnia, że to działa poprawnie.

 Dodajmy program obsługi, aby napisać wiersz, który pokazuje postęp w oknie konsoli.

[!code-csharp[Search](../../samples/snippets/csharp/events/Program.cs#Search "Declare event handler")]

Widzieliście wzorce, które są przestrzegane w całym ekosystemie .NET.
Ucząc się tych wzorców i konwencji, będziesz pisać idiomatyczne C# i .NET szybko.

Następnie zobaczysz pewne zmiany w tych wzorców w najnowszej wersji .NET.

[Dalej](modern-events.md)
