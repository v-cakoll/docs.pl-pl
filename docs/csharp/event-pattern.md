---
title: Standardowe wzorce zdarzenia platformy .NET
description: Więcej informacji na temat wzorców zdarzeń .NET i tworzenie źródła zdarzeń w wersji standard i subskrypcji i przetworzyć standardowych zdarzeń w kodzie.
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 9bd9f71726647966dd1e4426b260484decb048c6
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827251"
---
# <a name="standard-net-event-patterns"></a>Standardowe wzorce zdarzenia platformy .NET

[Poprzednie](events-overview.md)

Zdarzenia platformy .NET zazwyczaj należy wykonać kilka znane wzorce. Standaryzacja te wzorce oznacza, że deweloperzy mogą korzystać z wiedzę na temat tych standardowe wzorce, które mogą być stosowane do dowolnego programu zdarzenia platformy .NET.

Przejdźmy przy użyciu tych wzorców standardowe, konieczne będzie wiedzy, które należy utworzyć źródła zdarzeń w wersji standard i subskrybowanie i przetworzyć standardowych zdarzeń w kodzie.

## <a name="event-delegate-signatures"></a>Podpisy delegata zdarzenia

Standardowa podpis dla delegata zdarzenia .NET jest:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Typ zwracany jest typ void. Zdarzenia są oparte na delegatów i są obiekty delegowane multiemisji. Obsługujący wiele subskrybentów dla dowolnego źródła zdarzenia. Pojedynczy wartość zwracana z metody nie skalować do wielu subskrybentów zdarzeń. Które zwracają wartość oznacza Zobacz źródło zdarzeń po wywołaniem zdarzenia? W dalszej części tego artykułu zobaczysz sposobu tworzenia zdarzeń protokołów, które obsługują subskrybentów zdarzeń informacji raportu ze źródłem zdarzeń.

Lista argumentów zawiera dwa argumenty: nadawcy i argumenty zdarzenia. Typ czasu kompilacji `sender` jest `System.Object`, nawet jeśli wiesz, prawdopodobnie bardziej pochodny typ, który zawsze są poprawne. Konwencja, użyj `object`.

Drugi argument zwykle został typ, który pochodzi od `System.EventArgs`. (Będzie [następnej sekcji](modern-events.md) która Konwencja przestaną być wymuszane.) Jeśli danego typu zdarzenia nie wymaga żadnych dodatkowych argumentów, nadal zapewni oba argumenty.
Jest wartością specjalną `EventArgs.Empty` należy używać do określenia, że zdarzenie nie zawiera żadnych dodatkowych informacji.

Utworzymy klasę, która zawiera listę plików w katalogu lub jego podkatalogach przestrzeganie wzorca. Ten składnik wywołuje zdarzenie, dla każdego pliku znaleźć odpowiadającego wzorzec.

Przy użyciu modelu zdarzeń zawiera niektóre zalety projektu. Możesz utworzyć wiele odbiorników zdarzeń, wykonujących różne akcje po znalezieniu używanych plików. Łączenie różnych odbiorników można tworzyć bardziej niezawodne algorytmów.

Oto deklaracji argument początkowej zdarzenia do znajdowania używanych plików: 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

Mimo że ten typ wygląda jak typ małe, tylko dane, postępuj zgodnie z Konwencją i odnieść (`class`) typu. Oznacza to obiekt argument zostanie przekazany przez odwołanie, a wszelkie zmiany danych ma być wyświetlana przez wszystkich subskrybentów. Pierwsza wersja jest niezmienialny obiektu. Należy wolisz właściwości były czcionką argument zdarzenia niezmienialny. Dzięki temu jeden subskrybent nie można zmienić wartości, przed subskrybenta innego będzie je widział. (Istnieją wyjątki od tej reguły, jak można zauważyć poniżej.)  

Następnie należy utworzyć deklaracji zdarzenia w klasie FileSearcher. Wykorzystanie `EventHandler<T>` typ oznacza, że nie trzeba tworzyć jeszcze innej definicji typu. Po prostu użyć specjalizacji ogólnego.

Umożliwia wypełnianie klasy FileSearcher do wyszukiwania plików zgodnych ze wzorcem i wywołaj zdarzenie prawidłowe, gdy zostanie wykryta dopasowania.

[!code-csharp[FileSearxcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="definining-and-raising-field-like-events"></a>Definining i wywoływanie zdarzeń podobnych pola

Najprostszym sposobem, aby dodać zdarzenie do własnej klasy jest można zadeklarować tego zdarzenia jako pole publiczne, tak jak w poprzednim przykładzie:

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

To prawdopodobnie jest deklarowanie publiczne pola, które wydają się być zły zorientowane obiektowo rozwiązaniem. Chcesz chronić dostęp do danych za pośrednictwem właściwości lub metody. Gdy to, że wygląda jak rozwiązaniem zły kod wygenerowany przez kompilator tworzenie otok tak, aby obiekty zdarzeń można uzyskać tylko w sposób bezpieczne. Tylko operacje dostępne dla zdarzeń podobnych pola są Dodaj program obsługi:

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

i usunąć program obsługi:

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

Należy pamiętać, że zmienna lokalna dla programu obsługi. Jeśli używasz treści Wyrażenie lambda, Usuń nie będzie działać poprawnie. Może być inne wystąpienie delegata i dyskretnej nic nie rób.

Kod poza klasy nie mogą wywoływać zdarzeń ani nie można wykonać innych operacji.

## <a name="returning-values-from-event-subscribers"></a>Zwracanie wartości z subskrybentów zdarzeń

Proste wersji działa prawidłowo. Dodajmy inna funkcja: anulowania.

Po podniesieniu zdarzenia znaleziono odbiorników powinno być możliwe zatrzymać dalsze przetwarzanie, jeśli ten plik jest, że ostatni poszukiwania.

Obsługi zdarzeń nie zwraca wartości, więc należy do komunikowania się, że w inny sposób. Wzorzec zdarzeń w wersji standard używa obiektu EventArgs zawierać pól, które subskrybenci zdarzeń mogą używać do komunikowania się Anuluj.

Istnieją dwa różne wzorce, które mogłyby zostać użyte, oparte na semantykę kontraktu Anuluj. W obu przypadkach warto polem EventArguments zdarzenia znaleziony plik. 

Wzorzec co pozwoliłoby żadnych jednego abonenta anulować operację.
Dla tego wzorca nowego pola jest ustawiana na `false`. Wszelkie subskrybenta można go zmienić `true`. Po wszystkich subskrybentów jak już wspomniano Zdarzenie wywoływane, składnik FileSearcher sprawdza, czy wartość logiczną i podejmuje działania.

Drugi wzorzec tylko czy anulować operację, jeśli operacja została anulowana wszystkich subskrybentów. W tym wzorcu nowego pola jest ustawiana na wskazują, należy anulować operacji oraz wszystkie subskrybent może zmienić wskazująca, że należy kontynuować operacji.
Po wszystkich subskrybentów jak już wspomniano Zdarzenie wywoływane, składnik FileSearcher sprawdza typu boolean i podejmuje działania. Brak jednego dodatkowego kroku w tym wzorcu: składnik musi wiedzieć, jeśli zdarzenie przejrzane żadnych subskrybentów. Jeśli nie ma żadnych subskrybentów, pole wskazuje cancel niepoprawnie.

Umożliwia wdrożenie pierwszej wersji dla tego przykładu. Konieczne jest dodanie polem o nazwie `CancelRequested` do `FileFoundArgs` typu:

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

To nowe pole jest automatycznie ustawiana na `false`, wartością domyślną dla polem, więc nie można anulować przypadkowo. Jedyną inną zmianą do składnika jest sprawdzanie flagę po wywoływanie zdarzeń, aby zobaczyć, jeśli dowolne subskrybentów żądanych anulowania:

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

Jedną z zalet tego wzorca jest, że nie jest istotne zmiany.
Brak subskrybentów żądanie anulowania przed i nadal nie są one. Żaden kod subskrybenta nie musi aktualizacji, chyba że chcą, aby obsługiwać nowy protokół Anuluj. Bardzo luźno jest powiązane.

Teraz należy zaktualizować subskrybenta, tak aby żądania anulowania po znalezieniu pierwszy plik wykonywalny:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Dodawanie innego deklaracja zdarzenia

Teraz Dodaj jedną funkcję więcej i Wykaż innych idioms języka dla zdarzeń. Dodajmy przeciążenia `Search()` metody, który przechodzi przez wszystkie podkatalogi w poszukiwaniu plików.

Ten można pobrać jako długotrwałej operacji w katalogu za dużo podkatalogów. Dodajmy zdarzenie, które pobiera wywoływane, gdy rozpoczyna się każdego nowego wyszukiwania w katalogu. Dzięki temu subskrybentów śledzić postęp i zaktualizować użytkownika dotyczące postępu. Wszystkie przykłady dotąd utworzony są publiczne. Upewnijmy tego Zdarzenie wewnętrzne. Oznacza to, że należy również wybrać typy używane dla argumentów wewnętrzny również.

Będzie rozpoczyna się od utworzenia nowej klasy EventArgs pochodnych dla raportowania nowy katalog i postępu. 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Ponownie mogą postępować zgodnie z zaleceniami aby typu niezmienne odwołania dla argumentów zdarzenia.

Następnie określ zdarzenia. Tym razem użyjesz innej składni. Oprócz przy użyciu składni pola, można jawnie utworzyć właściwości, z Dodaj i usuń programy obsługi. W tym przykładzie nie wymaga dodatkowego kodu w tych programów obsługi, ale oznacza to, jak należy je utworzyć.

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

Na wiele sposobów kod, który można zapisać tutaj duplikatów kodu kompilator generuje definicje zdarzeń pola przedstawiono wcześniej. Utwórz zdarzenie przy użyciu składni bardzo podobne do celów [właściwości](properties.md). Powiadomienie, że obsługi mają różne nazwy elementu: `add` i `remove`. Są one nazywane subskrypcji zdarzenia lub zrezygnować z zdarzenia. Zwróć uwagę, czy też należy zadeklarować polem zapasowym prywatnych do przechowywania zmiennej zdarzeń. Jest on zainicjowany do wartości null.

Następnie możemy dodać przeciążenia metody Search(), która jest przesyłany w podkatalogach i zgłasza obu zdarzeń. W tym celu najłatwiej Użyj domyślnego argumentu, aby określić, czy chcesz wyszukać wszystkich katalogów:

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

W tym momencie można uruchomić aplikacji wywoływania przeciążenia wszystkie podkatalogi wyszukiwania. Na nowe nie ma żadnych subskrybentów `ChangeDirectory` zdarzeń, ale przy użyciu `?.Invoke()` idiom gwarantuje, że to działa prawidłowo.

 Dodajmy obsługi do zapisywania wiersza, który będzie wyświetlany postęp w oknie konsoli. 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

Przedstawiono wzorców, które zostaną wykonane przez cały ekosystem .NET.
Przez nauki tych wzorców i konwencje napiszesz idiomatyczne C# i .NET szybko.

Następnie zostanie wyświetlony pewne zmiany w tych wzorców w najnowszej wersji programu .NET.

[Next](modern-events.md)
