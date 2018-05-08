---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: Ten samouczek zawiera szereg funkcji .NET Core i języka C#.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: bc3c23b277b233efba9f32cc49b29ac905f3abc8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="rest-client"></a>Klient REST

## <a name="introduction"></a>Wprowadzenie
Ten samouczek zawiera szereg funkcji .NET Core i języka C#. Dowiesz się:
*   Podstawowe informacje dotyczące programu .NET Core interfejsu wiersza polecenia (CLI).
*   Omówienie funkcji języka C#.
*   Zarządzanie zależności nuget
*   Połączenia HTTP
*   Przetwarzanie informacji dotyczących JSON
*   Zarządzanie konfiguracją z atrybutami. 

Będzie utworzyć aplikację, która wystawia żądania HTTP dla usługi REST w usłudze GitHub. Zostanie odczytu informacji w formacie JSON oraz konwersji pakietu JSON na obiekty C#. Na koniec zostanie wyświetlone sposób pracy z obiektami C#.

Istnieje wiele funkcji, w tym samouczku. Utworzymy je jeden po drugim.

Jeśli wolisz wykonaj, wraz z [próbki](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu możesz pobrać go. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne
Należy skonfigurować komputer z usługami .NET core. Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony. Można uruchomić tej aplikacji, w systemie Windows, Linux, macOS lub w kontenerze Docker. Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych. Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/), która jest typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.
## <a name="create-the-application"></a>Tworzenie aplikacji
Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji. Upewnij się, że sposób bieżącego katalogu. Wpisz polecenie `dotnet new console` w wierszu polecenia. Spowoduje to utworzenie plików starter podstawowe aplikacji "Hello World".

Przed wprowadzeniem modyfikacji przejdźmy do czynności, aby uruchomić prostej aplikacji Hello World. Po utworzeniu aplikacji, wpisz `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) w wierszu polecenia. To polecenie uruchamia proces przywracania pakietów NuGet. NuGet jest Menedżera pakietów platformy .NET. To polecenie pobiera wszelkie brakujące zależności projektu. Jak jest to nowy projekt, Brak zależności są na miejscu, więc przy pierwszym uruchomieniu pobierze framework .NET Core. Po wykonaniu tego kroku początkowego, wystarczy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) podczas dodawania nowych pakietów zależnych lub zaktualizować wersje zależności.  

Po przywróceniu pakietów, możesz uruchomić `dotnet build`. Wykonuje aparat kompilacji i tworzy aplikację. Na koniec wykonaj `dotnet run` do uruchamiania aplikacji.

## <a name="adding-new-dependencies"></a>Dodawanie nowych zależności
Jest jednym z celów kluczy dla platformy .NET Core aby zminimalizować rozmiar instalacji programu .NET framework. Framework .NET Core aplikacji zawiera najbardziej typowe elementy pełna platformy .NET. Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, Dodaj te zależności do projektu C# (\*.csproj) pliku. W naszym przykładzie, musisz dodać `System.Runtime.Serialization.Json` pakietu dzięki aplikacji może przetworzyć odpowiedzi JSON.

Otwórz z `csproj` pliku projektu. Pierwszy wiersz pliku powinny się wyświetlać jako:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Dodaj następujący kod bezpośrednio po tym wierszu: 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
Większość edytory kodu zapewni uzupełnianie różne wersje tych bibliotek. Zwykle należy używać najnowszej wersji dowolnego pakietu, który zostanie dodany. Jest jednak należy się upewnić, że wersje wszystkich pakietów zgodne i są również zgodne wersji platformy .NET Core aplikacji.

Po wprowadzeniu tych zmian, należy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) ponownie, aby pakiet jest zainstalowany w tym systemie.

## <a name="making-web-requests"></a>Tworzenie żądania sieci Web
Teraz możesz rozpocząć pobieranie danych z sieci web. Ta aplikacja będzie odczytu informacji z [GitHub API](https://developer.github.com/v3/). Załóżmy uzyskania informacji na temat projektów w ramach [.NET Foundation](http://www.dotnetfoundation.org/) parasola. Można będzie uruchomić w żądaniu skierowanym do interfejsu API usługi GitHub można pobrać informacji dotyczących projektów. Punkt końcowy będzie potrzebny jest: [ https://api.github.com/orgs/dotnet/repos ](https://api.github.com/orgs/dotnet/repos). Chcesz pobrać wszystkie informacje dotyczące tych projektów, więc użyjesz żądanie HTTP GET.
Przeglądarka używa również żądania HTTP GET, więc możesz wkleić, że adres URL do przeglądarki, aby zobaczyć, jakie informacje należy będziesz otrzymywać i przetwarzania.

Możesz użyć <xref:System.Net.Http.HttpClient> klasy żądań sieci web. Wszystkie nowoczesne interfejsów API architektury .NET, takich jak <xref:System.Net.Http.HttpClient> obsługuje tylko asynchroniczne metody interfejsów API jego długotrwałe.
Rozpocznij metody asynchronicznej. Podczas tworzenia funkcjonalność aplikacji będzie Wypełnij implementacji. Uruchamianie przez otwarcie `program.cs` plików w katalogu projektu i dodaniu następującą metodę do `Program` klasy:

```csharp
private static async Task ProcessRepositories()
{
    
}
```

Musisz dodać `using` instrukcji w górnej części programu `Main` metody co program rozpoznaje kompilatora C# <xref:System.Threading.Tasks.Task> typu:

```csharp
using System.Threading.Tasks;
```

Jeśli w tym momencie skompilowanie projektu uzyskasz ostrzeżenie wygenerowany dla tej metody, ponieważ nie zawiera żadnego `await` operatory i będzie wykonywana synchronicznie. Ignoruj, który obecnie; należy dodać `await` operatorów jako należy wypełnić w metodzie.

Następnie zmienić nazwę przestrzeń nazw zdefiniowana w `namespace` instrukcji domyślne `ConsoleApp` do `WebAPIClient`. Później zdefiniujemy `repo` klasy w tej przestrzeni nazw.

Następnie zaktualizuj `Main` metodę do wywołania tej metody. `ProcessRepositories` Metoda zwraca zadania i nie należy zamknąć program przed zakończeniem tego zadania. W związku z tym należy użyć `Wait` metodę, aby zablokować i poczekaj na zakończenie zadania:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Masz teraz program, który nie działa, ale nie jej asynchronicznie. Załóżmy ją udoskonalać.

Najpierw należy obiektu, który jest w stanie pobrać danych z sieci web; można użyć <xref:System.Net.Http.HttpClient> w tym celu. Ten obiekt obsługuje żądania i odpowiedzi. Utworzyć pojedynczego wystąpienia tego typu w `Program` klasy w pliku Program.cs.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

 Wróć do `ProcessRepositories` wypełnienia w pierwszej wersji i metody:

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

Musisz również dodać dwie nowe za pomocą instrukcji u góry pliku dla tego skompilować:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Ta wersja pierwszy sprawia, że żądania sieci web, aby zapoznać się z listą wszystkich repozytoriów w ramach organizacji foundation dotnet. (Identyfikator gitHub .NET Foundation jest "dotnet"). Skonfiguruj kilka pierwszych wierszy <xref:System.Net.Http.HttpClient> dla tego żądania. Najpierw jest skonfigurowany do akceptowania odpowiedzi GitHub JSON.
Ten format jest po prostu JSON. Następnego wiersza dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu. Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne do pobrania informacji z usługi GitHub.

Po skonfigurowaniu <xref:System.Net.Http.HttpClient>, wprowadź sieci web żądania i pobierania odpowiedzi. W tej wersji pierwszej, użyj <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodne metody. Ta metoda wygody uruchamia zadanie, które wysyła żądanie sieci web, a następnie po powrocie z żądania go odczytuje w strumieniu odpowiedzi i wyodrębnia zawartość ze strumienia. Treść odpowiedzi jest zwracany jako <xref:System.String>. Ten ciąg jest dostępna po zakończeniu zadania. 

Końcowe dwa wiersze w tej metody await tego zadania, a następnie wydrukuj odpowiedzi do konsoli.
Tworzenie aplikacji i uruchom go. Ostrzeżenie kompilacji zostanie usunięty, ponieważ `ProcessRepositories` teraz zawierać `await` operatora. Zobaczysz, że dużo wyświetlanie JSON sformatowanego tekstu.   

## <a name="processing-the-json-result"></a>Przetwarzanie wyniku JSON

W tym momencie napisanych kod, aby pobrać odpowiedzi z serwera sieci web i wyświetlić tekst, który znajduje się w tej odpowiedzi. Następnie możemy przekonwertować tę odpowiedź JSON na obiekty C#.

Serializator JSON konwertuje dane JSON na obiekty C#. Najpierw jest określenie typu klasy C# zawierają informacje, które korzystać z tej odpowiedzi. Tym powoli, utworzymy tak rozpoczyna się od prostego C# typu, który zawiera nazwę repozytorium:

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
``` 

Umieść kod powyżej w nowym pliku o nazwie "repo.cs". Ta wersja klasy reprezentuje to najprostsza ścieżka do przetwarzania danych JSON. Nazwa klasy i nazwę elementu członkowskiego zgodne nazw używanych w pakiecie JSON zamiast następujących konwencji C#. Użytkownik będzie rozwiązać ten problem, zapewniając niektóre atrybuty konfiguracji później. Ta klasa przedstawia inną ważną funkcją JSON serializacji i deserializacji: nie wszystkie pola w pakiecie JSON są częścią tej klasy.
Serializator JSON zignoruje informacje, które nie są uwzględnione w typie klasy używane.
Ta funkcja umożliwia tworzenie typów współpracujących z tylko podzestaw pól w pakiecie JSON.

Teraz, po utworzeniu typu teraz do deserializacji. Musisz utworzyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiektu. Ten obiekt musi znać typu CLR Oczekiwano pakietu JSON pobiera. Pakiet z witryny GitHub zawiera sekwencję repozytoriów, więc `List<repo>` jest nieprawidłowego typu. Dodaj następujący wiersz do Twojej `ProcessRepositories` metody:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Używasz dwóch nowych przestrzeni nazw, więc musisz dodać te również:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

Następnie użyjesz serializatora do konwertowania JSON do obiektów C#. Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> w Twojej `ProcessRepositories` metody za pomocą następujących dwóch wierszy:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Należy zauważyć, że używasz teraz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Serializator używa strumienia zamiast ciągu jako źródło. Załóżmy opisano kilka funkcji języka C#, które są używane w drugim wierszu powyżej. Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> jest `await` wyrażenia. Await wyrażenia może występować niemal z dowolnego miejsca w kodzie, nawet jeśli do chwili, tylko przedstawiono je w ramach instrukcji przypisania.

Po drugie `as` operator konwertuje z typu czasu kompilacji `object` do `List<repo>`. Deklaracja <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, że zwraca wartość typu obiektu <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Zwraca typ określony podczas jego skonstruowany (`List<repo>` w ramach tego samouczka). Jeśli konwersja nie powiedzie się, `as` operatora daje w wyniku `null`, zamiast generowania wyjątku.

Prawie gotowe z tej sekcji. Teraz, konwersji kodu JSON do obiektów C#, umożliwia wyświetlanie nazwy każdego repozytorium. Zamień wiersze do odczytu:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

z następujących czynności:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Kompilowanie i uruchamianie aplikacji. Będzie on Wydrukuj nazwy repozytoriów, które są częścią .NET Foundation.

## <a name="controlling-serialization"></a>Kontrolowanie serializacji

Aby dodać więcej funkcji umożliwia adresów `repo` wpisać i dołączyć je zgodne z konwencjami więcej standard języka C#. Można to zrobić przez dodawanie adnotacji do `repo` to typ *atrybuty* które kontrolują sposób działania serializator JSON. W Twoim przypadku użyjesz tych atrybutów do definiowania mapowania między nazwami kluczy JSON oraz języka C# klasy i element członkowski nazwy. Są dwa atrybuty używane `DataContract` atrybutu i `DataMember` atrybutu. Konwencja, wszystkie klasy atrybutu kończyć się sufiksem `Attribute`. Nie trzeba jednak używają tego sufiksu, po zastosowaniu atrybutu. 

`DataContract` i `DataMember` atrybutów znajdują się w innej biblioteki, musisz dodać do pliku projektu C# jako zależność tej biblioteki. Dodaj następujący wiersz do `<ItemGroup>` sekcji w pliku projektu:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Po zapisaniu pliku Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) można pobrać tego pakietu.

Następnie otwórz folder `repo.cs` pliku. Teraz Zmień nazwę Pascal przypadków użycia i pełni pełnych nazwę `Repository`. Chcemy nadal mapowanie węzłów 'repozytorium' JSON do tego typu, musisz dodać `DataContract` atrybutu deklaracji klasy. Zostanie ustawiona `Name` właściwości atrybutu nazwy węzłów JSON, które mapują do tego typu:

```csharp
[DataContract(Name="repo")]
public class Repository
```

<xref:System.Runtime.Serialization.DataContractAttribute> Jest elementem członkowskim <xref:System.Runtime.Serialization> przestrzeni nazw, dlatego należy dodać odpowiednią `using` instrukcji w górnej części pliku:

```csharp
using System.Runtime.Serialization;
```

Zmieniono nazwę `repo` klasy do `Repository`, więc musisz wprowadzić taką samą nazwę, zmiany w pliku Program.cs (niektóre edytory może obsługiwać Refaktoryzacja zmiany nazwy, która automatycznie wprowadzić tę zmianę:)

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

Następnie można wprowadzić te same zmiany z `name` pole przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute> klasy. Wprowadź następujące zmiany do deklaracji `name` w repo.cs:

```csharp
[DataMember(Name="name")]
public string Name;
```

Ta zmiana oznacza, że trzeba będzie zmienić kod, który zapisuje nazwy każdego repozytorium w pliku program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Czy `dotnet build` następuje `dotnet run` się upewnić, że masz mapowania poprawne. Tych samych danych wyjściowych jako przed powinna zostać wyświetlona. Przed możemy przetworzyć więcej właściwości z serwera sieci web, można wprowadzić jeden więcej zmiana `Repository` klasy. `Name` Element członkowski jest polem publicznie. Nie jest dobrym rozwiązaniem zorientowane obiektowo, więc warto zmienić właściwości. Dla naszych celów, firma Microsoft nie ma potrzeby żadnych szczególnych kod wymagany do uruchomienia podczas pobierania lub ustawiania właściwości, ale zmiana właściwości ułatwia później dodać tych zmian bez przerywania kodu, który używa `Repository` klasy.

Usuń definicję pola i zastąp go przy użyciu [automatycznie implementowanej właściwości](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

Kompilator generuje treści `get` i `set` metody dostępu, a także pole prywatne do przechowywania nazwy. Mogą być podobne do następujący kod, który można ręcznie wpisać:

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Można wprowadzić jeden więcej zmiany przed dodaniem nowych funkcji. `ProcessRepositories` Metody można wykonywać zadania asynchronicznego i zwracać kolekcji repozytoriów. Możemy zwrócić `List<Repository>` z tej metody i Przenieś kod, który zapisuje informacje w `Main` metody.

Zmiana podpisu `ProcessRepositories` do zwrócenia zadania, których wynikiem jest lista z `Repository` obiektów:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Następnie tylko zwrócić repozytoria po przetworzeniu JSON odpowiedzi:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Kompilator generuje `Task<T>` obiektu dla zwracany, ponieważ został oznaczony tej metody jako `async`.
Następnie zmodyfikujmy `Main` metodę, tak aby przechwytywać tych wyników i zapisuje nazwy repozytorium do konsoli. Twoje `Main` metody teraz wygląda następująco:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Uzyskiwanie dostępu do `Result` właściwości zadania blokuje dopiero po ukończeniu zadania. Zwykle wolisz `await` ukończenia zadania, jak w `ProcessRepositories` metody, ale nie jest dozwolona w `Main` metody.

## <a name="reading-more-information"></a>Odczytywanie więcej informacji

Teraz zakończyć to przez przetwarzanie kilka kolejnych właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub. Nie ma do pobrania wszystko, ale Dodawanie kilka właściwości przedstawiono kilka więcej funkcji języka C#.

Zacznijmy od dodania więcej kilka typów prostych do `Repository` definicji klasy. Te właściwości są dodawane do tej klasy:

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

Te właściwości mają wbudowane konwersji z typu ciąg (czyli zawierać pakiety JSON) na typ docelowy. <xref:System.Uri> Typu może być nowe dla Ciebie. Reprezentuje identyfikator URI, lub w tym przypadku adresu URL. W przypadku liczby `Uri` i `int` typy pakietów JSON zawiera dane, które nie konwertować na typ docelowy, akcja serializacji spowoduje zgłoszenie wyjątku.

Po dodaniu tych aktualizacji `Main` metodę w celu wyświetlenia tych elementów:

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```
Jako ostatni krok możemy dodać informacje z ostatniej operacji wypychania. Te informacje jest sformatowany w ten sposób w formacie JSON odpowiedzi:

```json
2016-02-08T21:27:00Z
```

Ten format nie wykonuj żadnych standard .NET <xref:System.DateTime> formatów. Z tego powodu konieczne jest napisanie metody konwersji niestandardowej. Ponadto nie pożądane nieprzetworzony ciąg uwidoczniona dla użytkowników z `Repository` klasy. Atrybuty można kontrolować to również. Najpierw należy zdefiniować `private` właściwości, w którym będą przechowywane reprezentację ciągu daty godziny w Twojej `Repository` klasy:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

`DataMember` Atrybut informuje serializator czy to powinna zostać przetworzona, mimo że nie jest publicznym elementem członkowskim. Następnie należy napisać publicznej właściwości tylko do odczytu, który konwertuje ciąg na prawidłową <xref:System.DateTime> obiektu i zwraca go <xref:System.DateTime>:

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

Przejdź przez nowe konstrukcje powyżej. `IgnoreDataMember` Atrybut serializator informuje, że ten typ nie należy do odczytu ani zapisywane z dowolnych obiektów JSON. Ta właściwość zawiera tylko `get` metody dostępu. Brak nie `set` dostępu. To, jak zdefiniować *tylko do odczytu* właściwości w języku C#. (Tak, możesz utworzyć *tylko do zapisu* wynosi właściwości w języku C#, ale ich wartości.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metody analizowania ciągu i tworzy <xref:System.DateTime> przy użyciu formatu podana wartość daty i dodaje dodatkowe metadane na `DateTime` przy użyciu `CultureInfo` obiektu. W przypadku niepowodzenia operacji analizowania metody dostępu właściwości zgłasza wyjątek.

Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy dodać <xref:System.Globalization> przestrzeni nazw do `using` instrukcje w `repo.cs`:

```csharp
using System.Globalization;
```

Na koniec należy dodać więcej jeden wyjściowy instrukcji w konsoli i wszystko jest gotowe do tworzenia i ponownie uruchom tę aplikację:

```csharp
Console.WriteLine(repo.LastPush);
```

Używana wersja teraz powinna być zgodna. [gotowej próbki](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).
 
## <a name="conclusion"></a>Wniosek

W tym samouczku pokazano, jak żądania sieci web, wynik analizy i Wyświetl właściwości tych wyników. Możesz także dodano nowe pakiety jako zależności w projekcie. Przedstawiono niektóre funkcje języka C# obsługujące zorientowane obiektowo technik.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
