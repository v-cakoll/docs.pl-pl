---
title: Standardowe wzorce zdarzeń platformy .NET
description: Więcej informacji na temat wzorce zdarzeń platformy .NET oraz jak utworzyć źródła zdarzeń w wersji standard i subskrybowanie i przetworzyć standardowych zdarzeń w kodzie.
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: cd1ead318529d1afc5b27ff8710cebcaae9b7bc3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062969"
---
# <a name="standard-net-event-patterns"></a>Standardowe wzorce zdarzeń platformy .NET

[Poprzednie](events-overview.md)

Zdarzenia .NET zazwyczaj korzystają z kilku znanych wzorców. Standaryzacji na tych wzorców oznacza, że deweloperzy mogą korzystać z wiedzy na temat tych standardowe wzorce, które mogą być stosowane do dowolnego programu zdarzenia platformy .NET.

Przejdźmy przez te standardowe wzorce, dzięki czemu będziesz mieć wiedzy umożliwiających tworzenie źródła zdarzeń w wersji standard i subskrybowanie i przetwarzanie standardowych zdarzeń w kodzie.

## <a name="event-delegate-signatures"></a>Podpisy delegata zdarzenia

Standardowa podpis delegata zdarzenia platformy .NET jest:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Typ zwracany jest typ void. Zdarzenia są oparte na delegatach i są obiekty delegowane multiemisji. Dla dowolnego źródła zdarzeń, który obsługuje wielu subskrybentów. Pojedynczą wartość zwracana z metody nie przeprowadzać skalowanie do wielu subskrybentów zdarzeń. Które zwracają wartość jest adresem źródła zdarzeń po podnoszenie zdarzenia? Później w tym artykule pokazano, jak utworzyć protokołów zdarzeń, które obsługują subskrybentów zdarzeń tych informacji raportu, aby źródło zdarzenia.

Lista argumentów zawiera dwa argumenty: nadawcy i argumenty zdarzeń. Typ czasu kompilacji `sender` jest `System.Object`, nawet jeśli wiesz, prawdopodobnie bardziej pochodnego typu, które zawsze są poprawne. Zgodnie z Konwencją, należy użyć `object`.

Drugi argument zazwyczaj został typ, który jest tworzony na podstawie `System.EventArgs`. (Znajduje się w [następnej sekcji](modern-events.md) , ta Konwencja przestaną być wymuszane.) Jeśli danego typu zdarzenia nie wymaga żadnych dodatkowych argumentów, nadal zapewni obu argumentów.
Jest wartością specjalną `EventArgs.Empty` o konieczności użycia, aby wskazać, że zdarzenia nie zawiera żadnych dodatkowych informacji.

Utwórzmy klasę, która wyświetla listę plików w katalogu lub jego podkatalogach, które wzorca. Ten składnik wywołuje zdarzenie, dla każdego pliku wykrył, że pasuje do wzorca.

Przy użyciu modelu zdarzeń zapewnia kilka korzyści projektu. Możesz utworzyć wiele odbiorników zdarzeń, które wykonują różne akcje, gdy zostanie znaleziony używanych plików. Łączenie różnych odbiorników można tworzyć bardziej niezawodne algorytmy.

Poniżej przedstawiono deklaracji argumentów zdarzenie początkowe służące do znajdowania używanych plików: 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

Mimo że ten typ wygląda typu małe, tylko dane, postępuj zgodnie z Konwencją i przywołać (`class`) typu. Oznacza to obiekt argument zostanie przekazany przez odwołanie, a wszelkie aktualizacje danych ma być wyświetlana przez wszystkich subskrybentów. Pierwsza wersja jest obiektem niezmienne. Wolisz należy wprowadzić właściwości w swojej typ argumentu zdarzenia niezmiennego. W ten sposób jednego abonenta nie można zmienić wartości, zanim zobaczy innego subskrybenta, ich. (Istnieją wyjątki od tego, jak można zauważyć poniżej.)  

Następnie należy utworzyć deklaracja zdarzenia w klasie FileSearcher. Wykorzystując `EventHandler<T>` typ oznacza, że nie trzeba utworzyć kolejny definicji typu. Po prostu użyć ogólnego specjalizacji.

Spróbujmy Wypełnij klasy FileSearcher do wyszukiwania plików, które pasują do wzorca i zgłoś zdarzenie prawidłowe, gdy dopasowanie jest odnalezione.

[!code-csharp[FileSearcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a>Definiowanie i wywoływanie zdarzenia podobne do pól

Najprostszym sposobem, aby dodać wydarzenie do klasy jest można zadeklarować tego zdarzenia jako pole publiczne, jak w poprzednim przykładzie:

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

To wygląda na to jest zadeklarowanie, publiczne pola, które wydają się być złym zwyczajem zorientowane obiektowo. Chcesz chronić dostęp do danych za pomocą właściwości lub metody. Chociaż może to wyglądać jak złym zwyczajem, kod wygenerowany przez kompilator tworzenie otok, tak aby obiekty zdarzeń może zostać oceniony jedynie w bezpieczny sposób. Tylko operacje dostępne dla zdarzenia podobne do pól są Dodaj program obsługi:

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

i Usuń procedurę obsługi:

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

Zwróć uwagę, że zmienna lokalna dla programu obsługi. Jeśli używasz treść wyrażenia lambda, Usuń nie będzie działać poprawnie. Może być inne wystąpienie delegata i dyskretnie nic nie rób.

Kodu spoza klasy nie mogą wywoływać zdarzenia, nie można wykonać żadnych innych operacji.

## <a name="returning-values-from-event-subscribers"></a>Zwracanie wartości od subskrybentów zdarzeń

Proste wersji działa prawidłowo. Dodajmy kolejną funkcją: Anulowanie.

Po podniesieniu znalezionych zdarzeń odbiorników powinno być możliwe zatrzymać dalsze przetwarzanie, jeśli ten plik jest, że ostatni poszukiwania.

Programy obsługi zdarzeń nie zwracają wartości, więc należy do komunikowania się, że w inny sposób. Wzorzec standardowych zdarzeń używa obiektu EventArgs podczas dołączania pól, które zdarzenie subskrybenci mogą używać do komunikowania się Anuluj.

Istnieją dwa różne wzorce, które mogłyby zostać użyte, oparte na semantyce zamówienia, Anuluj. W obu przypadkach dodasz pola logicznych do EventArguments wydarzeniu znaleziony plik. 

Jednym ze wzorców pozwoliłoby każdy jeden subskrybent anulować operację.
Dla tego wzoru nowego pola jest ustawiana na `false`. Każdy subskrybent będzie można go zmienić `true`. Po wszystkim subskrybentom przejrzane zgłoszone zdarzenie, składnik FileSearcher sprawdza, czy wartość logiczna i podejmuje działania.

Drugi wzorzec tylko czy anulować operację, jeśli wszyscy subskrybenci operacja została anulowana. W tym wzorcu nowe pole jest inicjowany do wskazania powinna anulować operację i każdy subskrybent może zmienić go, aby wskazać, że operacja powinna nadal pozostawać.
Po wszystkim subskrybentom przejrzane zgłoszone zdarzenie, składnik FileSearcher sprawdza, czy atrybut typu wartość logiczna i podejmuje działania. Istnieje jeden dodatkowy krok w tym wzorcu: składnik musi znać, jeśli zdarzenie przejrzane żadnych subskrybentów. W przypadku subskrybentów pola wskazuje Anuluj niepoprawnie.

Teraz można zaimplementować pierwsza wersja dla tego przykładu. Należy dodać pola logicznych o nazwie `CancelRequested` do `FileFoundArgs` typu:

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

Do tego nowego pola jest inicjowana automatycznie `false`, wartością domyślną dla polem, dzięki czemu nie anulujesz przypadkowo. Jedyną inną zmianą do składnika jest do sprawdzania flagi po podnoszonego zdarzenia, aby zobaczyć, jeśli dowolny subskrybentów żądano anulowania:

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

Jedną z zalet tego wzorca jest, że nie jest istotną zmianę.
Brak subskrybentów zażądał anulowania przed i nadal nie są one. Brak kodu subskrybenta wymaga aktualizacji, chyba że mają być obsługuje nowy protokół anulowania. Jest bardzo luźno powiązana.

Zaktualizujmy subskrybenta, tak aby żądania anulowania, gdy znajdzie pierwszy plik wykonywalny:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Dodawanie innego deklaracja zdarzenia

Dodajmy jedną funkcję więcej i pokazują innych idiomy języka dla zdarzeń. Dodajmy przeciążenia `Search` metodę, która przechodzi przez wszystkie podkatalogi w poszukiwaniu plików.

To można pobrać jako długotrwałej operacji w katalogu z wielu katalogach podrzędnych. Dodajmy zdarzenia, które pobiera zgłaszane w przypadku każdego nowego wyszukiwania w katalogu rozpoczyna się. Dzięki temu subskrybentów do śledzenia postępu i zaktualizować użytkownika dotyczące postępu. Wszystkie przykłady, utworzonych przez siebie do tej pory były publiczne. Upewnijmy się, to zdarzenie wewnętrzne. Oznacza to, że można również ustawić jako typy również używany dla wewnętrznych argumentów.

Będziesz rozpoczyna się od utworzenia nowej klasy EventArgs pochodne raportowania nowy katalog i postępu. 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Ponownie możesz wykonać zalecenia dotyczące typu odwołania niezmienne argumentów zdarzeń.

Następnie zdefiniuj zdarzenie. Tym razem użyjesz różnej składni. Oprócz używania składni pola, można jawnie Utwórz właściwości, za pomocą Dodaj i usuń programy obsługi. W tym przykładzie nie wymaga dodatkowego kodu w tych procedurach obsługi, ale ten pokazuje, jak należy je utworzyć.

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

Na wiele sposobów kod, który możesz zapisu w tym miejscu duplikatów kodu, kompilator generuje definicje zdarzeń pola przedstawiono wcześniej. Tworzenie zdarzenia za pomocą składni bardzo podobne do celów [właściwości](properties.md). Zwróć uwagę, że programy obsługi mają inne nazwy: `add` i `remove`. Są one nazywane do subskrybowania zdarzenia lub anulować subskrypcję zdarzenia. Należy zauważyć, że również należy zadeklarować polem zapasowym prywatnych do przechowania zmiennej zdarzeń. Jest inicjowany do wartości null.

Następnie Dodajmy przeciążenia `Search` metodę, która przechodzi podkatalogów i wywołuje zarówno zdarzenia. Najprostszym sposobem, aby osiągnąć ten cel jest określenie, że wszystkie katalogi wyszukiwania za pomocą domyślnego argumentu:

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

W tym momencie można uruchomić aplikacji, wywołanie przeciążenia wszystkie podkatalogi wyszukiwania. Na nowym nie ma żadnych subskrybentów `ChangeDirectory` zdarzenia, ale przy użyciu `?.Invoke()` idiom gwarantuje, że to działa prawidłowo.

 Możemy dodać program obsługi do pisania wiersza, która przedstawia postęp w oknie konsoli. 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

Po zapoznaniu wzorców, które są wykonywane w całym ekosystemie platformy .NET.
Dzięki informacjom o tych wzorców i Konwencji, napiszesz idiomatyczną C# i .NET szybko.

Następnie zobaczysz niektóre zmiany w tych wzorców w najnowszej wersji programu .NET.

[Next](modern-events.md)
