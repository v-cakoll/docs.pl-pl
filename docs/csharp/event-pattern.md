---
title: Standardowe wzorce zdarzenia platformy .NET
description: "Więcej informacji na temat wzorców zdarzeń .NET i tworzenie źródła zdarzeń w wersji standard i subskrypcji i przetworzyć standardowych zdarzeń w kodzie."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: ff36438ab02ae6822d7df8425a615aef2ddbf2f2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

Mimo że ten typ wygląda jak typ małe, tylko dane, postępuj zgodnie z Konwencją i odnieść (`class`) typu. Oznacza to obiekt argument zostanie przekazany przez odwołanie, a wszelkie zmiany danych ma być wyświetlana przez wszystkich subskrybentów. Pierwsza wersja jest niezmienialny obiektu. Należy wolisz właściwości były czcionką argument zdarzenia niezmienialny. Dzięki temu jeden subskrybent nie można zmienić wartości, przed subskrybenta innego będzie je widział. (Istnieją wyjątki od tej reguły, jak można zauważyć poniżej.)  

Następnie należy utworzyć deklaracji zdarzenia w klasie FileSearcher. Wykorzystanie `EventHandler<T>` typ oznacza, że nie trzeba tworzyć jeszcze innej definicji typu. Po prostu użyć specjalizacji ogólnego.

Umożliwia wypełnianie klasy FileSearcher do wyszukiwania plików zgodnych ze wzorcem i wywołaj zdarzenie prawidłowe, gdy zostanie wykryta dopasowania.

```csharp
public class FileSearcher
{
    public event EventHandler<FileFoundArgs> FileFound;

    public void Search(string directory, string searchPattern)
    {
        foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
        {
            FileFound?.Invoke(this, new FileFoundArgs(file));
        }
    }
}
```

## <a name="definining-and-raising-field-like-events"></a>Definining i wywoływanie zdarzeń podobnych pola

Najprostszym sposobem, aby dodać zdarzenie do własnej klasy jest można zadeklarować tego zdarzenia jako pole publiczne, tak jak w powyższym przykładzie:

```csharp
public event EventHandler<FileFoundArgs> FileFound;
```

To prawdopodobnie jest deklarowanie publiczne pola, które wydają się być zły obiektowej rozwiązaniem. Chcesz chronić dostęp do danych za pośrednictwem właściwości lub metody. Gdy to, że wygląda jak rozwiązaniem zły kod wygenerowany przez kompilator tworzenie otok tak, aby obiekty zdarzeń można uzyskać tylko w sposób bezpieczne. Tylko operacje dostępne dla zdarzeń podobnych pola są Dodaj program obsługi:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);
lister.FileFound += onFileFound;
```

i usunąć program obsługi:

```csharp
lister.FileFound -= onFileFound;
```

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

Umożliwia wdrożenie pierwszej wersji dla tego przykładu. Konieczne jest dodanie polem z typem FileFoundEventArgs:

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }
    public bool CancelRequested { get; set; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

Powinien być inicjowany tego nowego pola na wartość false, nie Anuluj bez powodu. To wartością domyślną dla polem, tak że odbywa się automatycznie. Jedyną inną zmianą do składnika jest sprawdzanie flagę po wywoływanie zdarzeń, aby zobaczyć, jeśli dowolne subskrybentów żądanych anulowania:

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

```csharp
internal class SearchDirectoryArgs : EventArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs)
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
``` 

Ponownie mogą postępować zgodnie z zaleceniami aby typu niezmienne odwołania dla argumentów zdarzenia.

Następnie określ zdarzenia. Tym razem użyjesz innej składni. Oprócz przy użyciu składni pola, można jawnie utworzyć właściwości, z Dodaj i usuń programy obsługi. W tym przykładzie nie wymaga dodatkowego kodu w tych programów obsługi, w tym projekcie, ale oznacza to, jak należy je utworzyć.

```csharp
internal event EventHandler<SearchDirectoryArgs> DirectoryChanged
{
    add { directoryChanged += value; }
    remove { directoryChanged -= value; }
}
private EventHandler<SearchDirectoryArgs> directoryChanged;
```

W może sposoby, zapisywany kod, w tym miejscu wstecznych się, że kod kompilator generuje się definicje zdarzeń pól przedstawiono wcześniej. Utwórz zdarzenie przy użyciu składni bardzo podobne do celów [właściwości](properties.md). Powiadomienie, że obsługi mają różne nazwy elementu: `add` i `remove`. Są one nazywane subskrypcji zdarzenia lub zrezygnować z zdarzenia. Zwróć uwagę, czy też należy zadeklarować polem zapasowym prywatnych do przechowywania zmiennej zdarzeń. Jest on zainicjowany do wartości null.

Następnie możemy dodać przeciążenia metody Search(), która jest przesyłany w podkatalogach i zgłasza obu zdarzeń. W tym celu najłatwiej Użyj domyślnego argumentu, aby określić, czy chcesz wyszukać wszystkich katalogów:

```csharp
public void Search(string directory, string searchPattern, bool searchSubDirs = false)
{
    if (searchSubDirs)
    {
        var allDirectories = Directory.GetDirectories(directory, "*.*", SearchOption.AllDirectories);
        var completedDirs = 0;
        var totalDirs = allDirectories.Length + 1;
        foreach (var dir in allDirectories)
        {
            directoryChanged?.Invoke(this,
                new SearchDirectoryArgs(dir, totalDirs, completedDirs++));
            // Recursively search this child directory:
            SearchDirectory(dir, searchPattern);
        }
        // Include the Current Directory:
        directoryChanged?.Invoke(this,
            new SearchDirectoryArgs(directory, totalDirs, completedDirs++));
        SearchDirectory(directory, searchPattern);
    }
    else
    {
        SearchDirectory(directory, searchPattern);
    }
}

private void SearchDirectory(string directory, string searchPattern)
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

W tym momencie można uruchomić aplikacji wywoływania przeciążenia wszystkie podkatalogi wyszukiwania. Na nowe nie ma żadnych subskrybentów `ChangeDirectory` zdarzeń, ale przy użyciu `?.Invoke()` idiom gwarantuje, że to działa prawidłowo.

 Dodajmy obsługi do zapisywania wiersza, który będzie wyświetlany postęp w oknie konsoli. 

```csharp
lister.DirectoryChanged += (sender, eventArgs) =>
{
    Console.Write($"Entering '{eventArgs.CurrentSearchDirectory}'.");
    Console.WriteLine($" {eventArgs.CompletedDirs} of {eventArgs.TotalDirs} completed...");
};
```

Przedstawiono wzorców, które zostaną wykonane przez cały ekosystem .NET.
Przez nauki tych wzorców i konwencje napiszesz idiomatyczne C# i .NET szybko.

Następnie zostanie wyświetlony pewne zmiany w tych wzorców w najnowszej wersji programu .NET.

[Next](modern-events.md)
