---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 13466b717d0676c2db5edf4c98a4ead3e673b96c
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44706200"
---
# <a name="rest-client"></a>Klient REST

## <a name="introduction"></a>Wprowadzenie
W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#. Dowiesz się:
*   Podstawowe narzędzia .NET Core interfejsu wiersza polecenia (CLI).
*   Omówienie funkcji języka C#.
*   Zarządzanie zależnościami z NuGet
*   Połączenia HTTP
*   Przetwarzanie informacji w formacie JSON
*   Zarządzanie konfiguracją za pomocą atrybutów. 

Skompiluj aplikację, która wysyła żądania HTTP do usługi REST w usłudze GitHub. Będziesz odczytu informacji w formacie JSON, a następnie przekonwertować pakietu JSON na obiekty języka C#. Na koniec zobaczysz sposób pracy z obiektami w języku C#.

Istnieje wiele funkcji, w tym samouczku. Utworzymy je jedno po drugim.

Jeśli wolisz postępuj zgodnie ze szczegółowymi [próbki końcowej](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) w tym temacie, możesz ją pobrać. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne
Należy skonfigurować maszynę, aby uruchomić platformy .NET core. Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony. Windows, Linux, macOS lub w kontenerze platformy Docker, mogą uruchamiać tę aplikację. Musisz zainstalować wybrany edytor kodu. Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/), która jest typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.
## <a name="create-the-application"></a>Tworzenie aplikacji
Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji. Upewnij się, że sposób bieżącego katalogu. Wpisz polecenie `dotnet new console` w wierszu polecenia. Spowoduje to utworzenie plikach startowych dla podstawowych aplikacji "Hello World".

Przed rozpoczęciem wprowadzania modyfikacji, Przejdźmy przez czynności, aby uruchomić prostej aplikacji Hello World. Po utworzeniu aplikacji wpisz `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) w wierszu polecenia. To polecenie uruchamia proces przywracania pakietów NuGet. NuGet to Menedżer pakietów .NET. To polecenie pobiera wszystkich brakujących zależności dla Twojego projektu. Jak jest to nowy projekt, żaden z zależności jest w miejscu, dzięki czemu przy pierwszym uruchomieniu pobierze platformę .NET Core. Po wykonaniu tego kroku początkowego, wystarczy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) podczas dodawania nowych pakietów zależnych lub zaktualizować wersje tych zależności.  

Po przywróceniu pakietów, możesz uruchomić `dotnet build`. Wykonuje aparat kompilacji i tworzy aplikację. Na koniec wykonaj `dotnet run` do uruchamiania aplikacji.

## <a name="adding-new-dependencies"></a>Dodawanie nowych zależności
Jednym z celów projektowania klucza dla platformy .NET Core jest minimalizacja rozmiaru instalacji programu .NET. Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, możesz dodać te zależności w projekcie języka C# (\*.csproj) pliku. W tym przykładzie należy dodać `System.Runtime.Serialization.Json` pakietu, dzięki czemu aplikacja może przetworzyć odpowiedzi JSON.

Otwórz swoje `csproj` pliku projektu. Pierwszy wiersz w pliku powinny się wyświetlać jako:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Dodaj następujący kod bezpośrednio po tym wierszu: 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
Większość edytory kodu zapewni uzupełnianie przez różne wersje tych bibliotek. Zazwyczaj będziesz chciał użyć najnowszej wersji dowolnego pakietu, który dodajesz. Jednak należy się upewnić, że są zgodne wersje wszystkich pakietów i są również zgodne wersję platformy aplikacji .NET Core.

Po wprowadzeniu tych zmian, należy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) ponownie, aby pakiet jest zainstalowany w systemie.

## <a name="making-web-requests"></a>Tworzenie żądania sieci Web
Teraz możesz rozpocząć pobieranie danych z sieci web. W tej aplikacji będzie odczytu informacji z [interfejsu API usługi GitHub](https://developer.github.com/v3/). Spróbujmy odczytać informacji na temat projektów w ramach [.NET Foundation](http://www.dotnetfoundation.org/) ogólny. Można będzie uruchomić w żądaniu skierowanym do interfejsu API usługi GitHub, aby pobrać informacje na temat projektów. Punkt końcowy będziesz używał jest: [ https://api.github.com/orgs/dotnet/repos ](https://api.github.com/orgs/dotnet/repos). Chcesz pobrać wszystkie informacje dotyczące tych projektów, dzięki czemu będziesz używać żądanie HTTP GET.
Przeglądarka używa także żądania HTTP GET, dzięki czemu można wkleić, że adres URL w przeglądarce, aby zobaczyć, jakie informacje należy będziesz otrzymywać i przetwarzania.

Możesz użyć <xref:System.Net.Http.HttpClient> klasy żądań sieci web. Wszystkie nowoczesnych interfejsów API programu .NET, takich jak <xref:System.Net.Http.HttpClient> obsługuje tylko metody asynchroniczne dla długotrwałych interfejsów API.
Rozpocznij metodą asynchroniczną. Podczas tworzenia funkcjonalność aplikacji będzie wypełniana w implementacji. Zacznij od otwarcia `program.cs` plik w katalogu projektu i dodawanie następującą metodę do `Program` klasy:

```csharp
private static async Task ProcessRepositories()
{
    
}
```

Musisz dodać `using` instrukcji w górnej części Twojej `Main` metoda tak, aby kompilator języka C# rozpoznaje <xref:System.Threading.Tasks.Task> typu:

```csharp
using System.Threading.Tasks;
```

Jeśli na tym etapie tworzenia projektu uzyskasz ostrzeżenia generowane dla tej metody, ponieważ nie zawiera żadnego `await` operatorów i zostanie ona uruchomiona synchronicznie. Zignoruje teraz; następnie dodasz `await` operatorów jako możesz wypełnić w metodzie.

Następnie zmień nazwę przestrzeni nazw, zdefiniowane w `namespace` instrukcji domyślne `ConsoleApp` do `WebAPIClient`. Później zdefiniujemy `repo` klasy w tej przestrzeni nazw.

Następnie zaktualizuj `Main` metodę do wywołania tej metody. `ProcessRepositories` Metoda zwraca klasę Task, i nie należy zakończyć program, przed zakończeniem zadania. W związku z tym, należy użyć `Wait` metodę, aby zablokować i poczekaj na zakończenie zadania:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Teraz masz program, nic nie robi, ale zajmuje asynchronicznie. Możemy ją ulepszyć.

Najpierw należy obiekt, który jest w stanie pobrać danych z sieci web; Możesz użyć <xref:System.Net.Http.HttpClient> Aby to zrobić. Ten obiekt obsługuje żądania i odpowiedzi. Utwórz wystąpienie jedno wystąpienie tego typu w `Program` klasy w pliku Program.cs.

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

 Wróć do `ProcessRepositories` metody i wypełnij pierwszą wersję:

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

Musisz również dodać dwie nowe przy użyciu instrukcji w górnej części pliku, w tym do skompilowania:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Ta pierwsza wersja sprawia, że żądanie sieci web, aby zapoznać się z listą wszystkich repozytoriów w ramach organizacji foundation dotnet. (Identyfikator gitHub .NET Foundation jest "dotnet"). Pierwszych kilka wierszy, ustawianie <xref:System.Net.Http.HttpClient> dla tego żądania. Najpierw jest skonfigurowany do akceptowania odpowiedziami JSON usługi GitHub.
Ten format jest po prostu JSON. Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu. Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne w celu pobrania informacji z usługi GitHub.

Po skonfigurowaniu <xref:System.Net.Http.HttpClient>, upewnij sieci web, żądania i pobierania odpowiedzi. W pierwszej wersji, możesz użyć <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna metoda. Ta wygodna metoda uruchamia zadanie, które wysyła żądanie sieci web, a następnie po powrocie z żądania go odczytuje w strumieniu odpowiedzi i wyodrębnia zawartość ze strumienia. Treść odpowiedzi jest zwracana jako <xref:System.String>. Ten ciąg jest dostępna po zakończeniu zadania. 

Ostatnie dwie linie ta metoda poczekać na zadanie, a następnie wydrukuj odpowiedzi do konsoli.
Tworzenie aplikacji i uruchom go. Ostrzeżenie kompilacji ma teraz, ponieważ `ProcessRepositories` teraz zawierać `await` operatora. Zobaczysz, że długie wyświetlanie JSON sformatowanego tekstu.   

## <a name="processing-the-json-result"></a>Przetwarzanie wyników JSON

W tym momencie został napisany kod, aby pobrać odpowiedzi z serwera sieci web oraz wyświetlać tekst, który znajduje się w tej odpowiedzi. Następnie możemy przekonwertować odpowiedź JSON na obiekty języka C#.

Serializator JSON konwertuje dane JSON na obiekty języka C#. Pierwsze zadanie jest zdefiniowanie typu klasy C# zawiera informacje, które od tej odpowiedzi. Utwórzmy tym powoli, więc rozpoczyna się od prostego języka C# typ, który zawiera nazwę repozytorium:

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

Powyższy kod należy umieścić w nowym pliku o nazwie "repo.cs". Ta wersja klasy reprezentuje to najprostsza ścieżka do przetwarzania danych JSON. Nazwa klasy i nazwę elementu członkowskiego zgodne nazwy używane w pakiecie JSON zamiast następujących konwencji języka C#. Można to naprawić, zapewniając niektóre atrybuty konfiguracji później. Ta klasa przedstawia inną ważną cechą JSON serializacji i deserializacji: nie wszystkie pola w pakiecie JSON należą do tej klasy.
Serializator JSON będzie ignorować informacje, które nie są objęte na typ klasy, które są używane.
Ta funkcja sprawia, że łatwiej tworzyć typy, które działają z tylko podzestaw pól w pakiecie JSON.

Teraz, po utworzeniu typu, możemy zdeserializuj ją. Musisz utworzyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiektu. Ten obiekt musi znać typ CLR Oczekiwano pakietu JSON pobiera. Pakiet z repozytorium GitHub zawiera sekwencję repozytoriów, więc `List<repo>` jest poprawnego typu. Dodaj następujący wiersz do Twojej `ProcessRepositories` metody:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Używasz dwie nowe przestrzenie nazw, więc należy dodać te także:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

Następnie użyjemy serializatora do przekonwertowania formatu JSON na obiekty języka C#. Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> w swojej `ProcessRepositories` metody za pomocą następujących dwóch wierszy:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Należy zauważyć, że używasz teraz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Serializator używa strumienia zamiast ciągu jako źródło. Możemy wyjaśnić kilka funkcji języka C#, które są używane w drugim wierszu powyżej. Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> jest `await` wyrażenia. Await wyrażeń może znajdować się praktycznie dowolnym miejscu w kodzie, mimo że do chwili obecnej, tylko przedstawiono je w ramach instrukcji przypisania.

Po drugie `as` operator konwertuje typ czasu kompilacji `object` do `List<repo>`. Deklaracja <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, że funkcja zwraca obiekt typu <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Zwraca typ określony podczas jego skonstruowano (`List<repo>` w ramach tego samouczka). Jeśli konwersja nie powiedzie, `as` operatora daje w wyniku `null`, zamiast zgłaszać wyjątek.

Prawie gotowe z tą sekcją. Teraz, za pomocą pliku JSON zostały konwertowane na obiekty języka C#, możemy wyświetlić nazwę każdego repozytorium. Zamień wiersze, które odczytują:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

z następujących czynności:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Skompilować i uruchomić aplikację. Zostanie ona wydrukowana nazwy repozytoria, które są częścią .NET Foundation.

## <a name="controlling-serialization"></a>Kontrolowanie serializacji

Zanim dodasz więcej funkcji, możemy adresów `repo` wpisz i przypisz ją konwencjami bardziej standard języka C#. Możesz to zrobić poprzez dodawanie adnotacji do `repo` to typ *atrybuty* które kontrolują, jak działa serializator JSON. W Twoim przypadku użyjesz tych atrybutów do definiowania mapowania między nazwami kluczy JSON i języka C# nazwy klas i składowych. Są dwa atrybuty używane `DataContract` atrybutu i `DataMember` atrybutu. Zgodnie z Konwencją wszystkie klasy atrybutu kończyć się sufiksem `Attribute`. Jednak nie należy używać tego sufiksu, po zastosowaniu atrybutu. 

`DataContract` i `DataMember` atrybuty są w innej biblioteki, więc musisz dodać tej biblioteki do pliku projektu C# jako zależność. Dodaj następujący wiersz do `<ItemGroup>` sekcji w pliku projektu:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Po zapisaniu pliku Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) do pobrania tego pakietu.

Następnie otwórz `repo.cs` pliku. Zmienimy nazwę pisanymi wielkimi literami, a w pełni pisowni nazwiska `Repository`. Firma Microsoft nadal chcesz mapy JSON "repo" węzłów do tego typu, więc musisz dodać `DataContract` atrybutu deklaracji klasy. Użytkownik ustawia `Name` właściwość atrybutu nazwy węzłów JSON, które mapują do tego typu:

```csharp
[DataContract(Name="repo")]
public class Repository
```

<xref:System.Runtime.Serialization.DataContractAttribute> Jest elementem członkowskim <xref:System.Runtime.Serialization> przestrzeni nazw, więc należy dodać odpowiedni `using` instrukcji w górnej części pliku:

```csharp
using System.Runtime.Serialization;
```

Zmieniono nazwę elementu `repo` klasy `Repository`, więc musisz wprowadzić taką samą nazwę, zmiany w pliku Program.cs (niektóre edytory mogą obsługiwać Refaktoryzacja zmiany nazwy, automatycznie wprowadzić tę zmianę:)

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

Następnie można wprowadzić tę samą zmianę z `name` pola przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute> klasy. Wprowadź następujące zmiany do deklaracji `name` pole repo.cs:

```csharp
[DataMember(Name="name")]
public string Name;
```

Ta zmiana oznacza, że zajdzie potrzeba zmiany kodu, który zapisuje nazwy każdego repozytorium w pliku program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Czy `dotnet build` następuje `dotnet run` się upewnić, że masz mapowania poprawne. Ten sam wynik jako przed powinny być widoczne. Zanim będziemy przetwarzać więcej właściwości z serwera sieci web, upewnijmy się, co więcej zmian `Repository` klasy. `Name` Składowa jest polem dostępny publicznie. Nie jest dobrą praktyką zorientowane obiektowo, więc Zmieńmy go do właściwości. Dla naszych potrzeb, potrzebujemy dowolnego konkretnego kodu, który uruchamiany, gdy pobieranie lub ustawianie właściwości, ale zmiana właściwości ułatwia dodawanie tych zmian w przyszłości, bez przerywania wszelki kod, który używa `Repository` klasy.

Usuń definicję pola i zastąp go wartością [automatycznie implementowana właściwość](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

Kompilator generuje treści `get` i `set` metod dostępu, a także prywatnego pola do przechowywania nazwy. Będzie podobny do poniższego kodu, który można ręcznie wpisać:

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Upewnijmy się, co więcej zmian przed dodaniem nowych funkcji. `ProcessRepositories` Zwracają kolekcję repozytoriów i oferuje Praca asynchroniczna metoda. Powrócimy `List<Repository>` z tej metody, a następnie przenieść kod, który zapisuje informacje w `Main` metody.

Zmień podpis `ProcessRepositories` zwracany typ task, którego wynikiem jest lista z `Repository` obiektów:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Następnie, po prostu zwraca repozytoriów po przetworzeniu odpowiedź w formacie JSON:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Kompilator generuje `Task<T>` obiekt do zwrotu, ponieważ został oznaczony jako tej metody jako `async`.
Następnie zmodyfikujmy `Main` metodę, tak że przechwytuje te wyniki i zapisuje każdej nazwy repozytorium do konsoli. Twoje `Main` metoda wygląda teraz następująco:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Uzyskiwanie dostępu do `Result` właściwość zadania blokuje, dopóki zadanie zostało ukończone. Zazwyczaj chcesz `await` ukończenia zadania, jak `ProcessRepositories` metody, ale nie jest dozwolona w `Main` metody.

## <a name="reading-more-information"></a>Odczytywanie informacji

Teraz zakończyć to przez przetwarzanie kilka innych właściwości w pakiecie JSON wysyłana z interfejsu API usługi GitHub. Nie będzie konieczności Pobierz wszystko, ale dodanie kilka właściwości zademonstruje kilka więcej funkcji języka C#.

Zacznijmy od dodania kilka więcej typów prostych do `Repository` definicji klasy. Dodaj następujące właściwości dla tej klasy:

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

Te właściwości mają wbudowane definicje konwersji z typu string (czyli zawierać pakiety JSON) na typ docelowy. <xref:System.Uri> Typ może być dla Ciebie nowe. Reprezentuje identyfikator URI, lub w tym przypadku adresu URL. W przypadku właściwości `Uri` i `int` typy pakietów JSON zawiera dane, które nie konwersji na typ docelowy, akcja serializacji spowoduje zgłoszenie wyjątku.

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
W ostatnim kroku Dodajmy informacji z ostatniej operacji wypychania. Te informacje są sformatowane w ten sposób, w odpowiedzi JSON:

```json
2016-02-08T21:27:00Z
```

Ten format nie jest zgodna z dowolnego programu standard .NET <xref:System.DateTime> formatów. Z tego powodu musisz napisać metodę konwersji niestandardowych. Ponadto najprawdopodobniej nie chcesz, nieprzetworzonego ciągu widoczna dla użytkowników z `Repository` klasy. Atrybuty można kontrolować oznacza również. Najpierw należy zdefiniować `private` właściwość, która będzie przechowywać reprezentację ciągu daty, godziny w swojej `Repository` klasy:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

`DataMember` Atrybut informuje serializator, powinna to być przetworzone, mimo że nie ma publicznej składowej. Następnie należy napisać właściwość publiczna tylko do odczytu, która konwertuje ciąg na prawidłowym <xref:System.DateTime> obiektu i zwraca ją <xref:System.DateTime>:

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

Zajmijmy się nowe konstrukcje powyżej. `IgnoreDataMember` Atrybutu powoduje, że tego typu nie należy do odczytu ani zapisane z dowolnych obiektów JSON i że, serializator. Ta właściwość zawiera tylko `get` metody dostępu. Istnieje nie `set` metody dostępu. To, jak zdefiniować *tylko do odczytu* właściwość w języku C#. (Tak, możesz utworzyć *tylko do zapisu* właściwości w języku C#, ale ich wartość jest ograniczona.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metoda analizowania ciągu i tworzy <xref:System.DateTime> przy użyciu podanej daty w formacie, a następnie dodaje dodatkowe metadane `DateTime` przy użyciu `CultureInfo` obiektu. Metoda dostępu właściwości zgłasza wyjątek, w przypadku niepowodzenia operacji analizy.

Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy dodać <xref:System.Globalization> przestrzeń nazw `using` instrukcji w `repo.cs`:

```csharp
using System.Globalization;
```

Na koniec należy dodać jeden wyjściowy więcej instrukcji, w konsoli i wszystko będzie gotowe skompilować i ponownie uruchomić tę aplikację:

```csharp
Console.WriteLine(repo.LastPush);
```

Twoja wersja powinna być teraz zgodna [gotowych przykładowych](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).
 
## <a name="conclusion"></a>Wniosek

W tym samouczku pokazano, jak wysyłać żądania sieci web, przeanalizować wynik i wyświetlić właściwości tych wyników. Ponadto dodano nowe pakiety jako zależności w projekcie. Przedstawiono niektóre funkcje języka C#, które obsługują technik zorientowane obiektowo.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
