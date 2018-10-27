---
title: Mikrousługi hostowane na platformie Docker-C#
description: Dowiedz się, jak utworzyć asp.net podstawowych usług, które są uruchamiane w kontenerach platformy Docker
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b1f7159a222ab4d68715844e9997ca922676bc80
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454489"
---
# <a name="microservices-hosted-in-docker"></a>Mikrousługi hostowane na platformie Docker

Ten samouczek zawiera szczegółowe zadania, które są niezbędne do tworzenia i wdrażania mikrousług platformy ASP.NET Core w kontenerze platformy Docker. W trakcie tego samouczka dowiesz się:

* Jak wygenerować aplikację ASP.NET Core.
* Jak utworzyć środowisko deweloperskie platformy Docker.
* Jak utworzyć obraz platformy Docker, na podstawie istniejącego obrazu.
* Jak wdrożyć usługę w kontenerze platformy Docker.

Po drodze widoczna jest także niektóre C# funkcji języka:

* Jak konwertować C# obiektów do ładunków JSON.
* Jak utworzyć niemodyfikowalny obiektów transferu danych.
* Instrukcje przetwarzania przychodzących żądań HTTP i generowanie odpowiedzi HTTP.
* Jak pracować z typami wartości null.

Możesz [wyświetlić lub pobrać przykładową aplikację](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) w tym temacie. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="why-docker"></a>Dlaczego Docker?

Docker sprawia, że łatwo jest tworzyć obrazy standardowych maszyn do hostowania usługi w centrum danych lub w chmurze publicznej. Docker umożliwia Skonfiguruj obraz i Replikuj ją w razie potrzeby skalowania w instalacji aplikacji.

Cały kod w tym samouczku będą działać w dowolnym środowisku .NET Core.
Dodatkowe zadania instalacji platformy Docker będzie działać w przypadku aplikacji ASP.NET Core. 

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować maszynę w taki sposób, aby uruchomić platformy .NET Core. Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony.
Windows, Linux, macOS lub w kontenerze platformy Docker, mogą uruchamiać tę aplikację.
Musisz zainstalować wybrany edytor kodu. Opisy poniżej użycia [programu Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.

Należy również zainstalować aparat platformy Docker. Zobacz [strona instalacji platformy Docker](https://docs.docker.com/install/overview/) instrukcje dla danej platformy.
Platformy docker można zainstalować w wiele dystrybucji systemu Linux, macOS lub Windows. Strona wyżej zawiera sekcje dla każdego z dostępnych instalacji.

## <a name="create-the-application"></a>Tworzenie aplikacji

Teraz, po zainstalowaniu wszystkie narzędzia, należy utworzyć nową aplikację platformy ASP.NET Core w katalogu o nazwie "WeatherMicroservice", wykonując następujące polecenie w powłoce Ulubione:

```console
dotnet new web -o WeatherMicroservice
```

`dotnet` Polecenie zostanie uruchomione narzędzia niezbędne do tworzenia aplikacji .NET. Każdy zlecenie wykonuje inne polecenie.

`dotnet new` Polecenie służy do tworzenia.Net Core projektów.

`-o WeatherMicroservice` Po opcji `dotnet new` polecenie służy do lokalizację, aby utworzyć aplikację platformy ASP.NET Core.

Dla tego mikrousług chcemy, aby aplikacja sieci web najprostszy, najbardziej lekki jest to możliwe, więc użyliśmy "Platformy ASP.NET Core puste" szablonu, określając jego krótką nazwę `web`.

Szablon tworzy cztery pliki:

* Plik Startup.cs. Zawiera podstawę aplikacji.
* Plik Program.cs. Zawiera punkt wejścia aplikacji.
* Plik WeatherMicroservice.csproj. Jest to plik kompilacji dla aplikacji.
* Plik Properties/launchSettings.json. Zawiera ustawienia debugowania, używane przez środowiska IDE.

Teraz możesz uruchomić aplikację wygenerowanego szablonu:

```console
dotnet run
```

To polecenie spowoduje najpierw przywrócenie zależności wymagane do kompilowania aplikacji i późniejszego kompilowania aplikacji.

Domyślna konfiguracja nasłuchuje `http://localhost:5000`. Możesz otworzyć przeglądarkę i przejdź do tej strony i wyświetlić "Hello World!" Komunikat.

Po wykonaniu tych czynności można zamknąć aplikację, naciskając klawisz <kbd>Ctrl</kbd>+<kbd>C</kbd>.

### <a name="anatomy-of-an-aspnet-core-application"></a>Anatomia aplikacji ASP.NET Core

Teraz, gdy masz utworzoną aplikację, Przyjrzyjmy się jak ta funkcja jest zaimplementowana. Istnieją dwa wygenerowanych plików, które są szczególnie istotne w tym momencie: WeatherMicroservice.csproj i pliku Startup.cs. 

Plik .csproj zawiera informacje o projekcie.
Są dwa węzły, które są najbardziej interesujących `<TargetFramework>` i `<PackageReference>`.

`<TargetFramework>` Węzła Określa wersję platformy .NET, która może uruchomić tę aplikację.

Każdy `<PackageReference>` węzła jest używany do określenia pakietu, który jest wymagany dla tej aplikacji.

Aplikacja została zaimplementowana w pliku Startup.cs. Ten plik zawiera klasę uruchamiania.

Te dwie metody są wywoływane przez infrastrukturę platformy ASP.NET Core, aby skonfigurować i uruchomić aplikację. `ConfigureServices` Metoda opisano usługi, które są niezbędne dla tej aplikacji. W przypadku tworzenia zwarte mikrousług, dzięki czemu nie trzeba skonfigurować wszelkie zależności. `Configure` Metoda konfiguruje programy obsługi dla przychodzących żądań HTTP. Szablon generuje prosty program obsługi, który odpowiada na każde żądanie z tekstu "Hello World!".

## <a name="build-a-microservice"></a>Tworzenie mikrousług

Usługi, możesz zacząć tworzyć będzie dostarczać raporty o pogodzie z dowolnego miejsca na świecie. W przypadku aplikacji produkcyjnej wywoływałby niektóre usługi w celu pobrania danych o pogodzie. W naszym przykładzie polega na wygenerowaniu prognozę pogody losowych. 

Istnieje kilka zadań, które należy wykonać w celu zaimplementowania naszej usługi pogody losowe:

* Analizowanie żądania przychodzącego, które można odczytać szerokości i długości geograficznej.
* Generowanie losowe dane prognozy.
* Konwertuj losowych danych prognozowania z C# obiektów na pakiety JSON.
* Ustaw nagłówek odpowiedzi, aby wskazać, że Twoja usługa wysyła kopię JSON.
* Zapisu odpowiedzi.

W kolejnych sekcjach opisano każdy z tych kroków.

### <a name="parsing-the-query-string"></a>Podczas analizowania ciągu zapytania

Rozpocznie się analizując ciąg zapytania. Usługa będzie akceptować "lat" i "long" argumentów dla ciągu zapytania w tym formularzu:

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

Wszystkie zmiany, należy wprowadzić są w wyrażeniu lambda zdefiniowany jako argument do `app.Run` w klasie uruchamiania.

Argument wyrażenia lambda jest `HttpContext` dla żądania. Jednym z jego właściwości jest `Request` obiektu. `Request` Obiekt ma `Query` właściwość, która zawiera słownik wszystkich wartości na ciąg zapytania dla żądania. Dodawanie pierwszego ma na celu znalezienie wartości szerokości i długości geograficznej:

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

`Query` Słownika wartości są `StringValue` typu. Tego typu może zawierać kolekcji ciągów. Dla usługi pogody każda wartość jest pojedynczy ciąg. Dlatego jest wywołanie `FirstOrDefault()` w powyższym kodzie. 

Następnie należy Konwertowanie ciągów na wartości podwójnej precyzji. Ta metoda służy do przekonwertowania ciągu na wartość o podwójnej precyzji jest `double.TryParse()`:

```csharp
bool TryParse(string s, out double result);
```

Ta metoda wykorzystuje C# się parametry, aby wskazać, jeśli ciąg wejściowy można przekonwertować na wartość typu double. Jeśli ciąg reprezentuje prawidłowy reprezentację wartość o podwójnej precyzji, metoda zwraca wartość true, a `result` argument zawiera wartość. Jeśli ciąg nie reprezentuje prawidłową wartość o podwójnej precyzji, metoda zwraca wartość false.

Możesz dostosować tego interfejsu API przy użyciu *— metoda rozszerzenia* zwracającego *nullable double*. A *typem wartościowym* to typ, który reprezentuje określony typ wartości i można również przechowywać braku lub wartość null. Typ dopuszczający wartość null jest reprezentowany przez dołączenie `?` znak do deklaracji typu. 

Metody rozszerzające są metody, które są zdefiniowane jako metody statyczne, ale przez dodanie `this` modyfikator w pierwszym parametrze może być wywoływany tak, jakby są członkami tej klasy. Metody rozszerzające można zdefiniować tylko w klasach statycznych. Poniżej przedstawiono definicję klasy zawierającej metodę rozszerzenia dla analizy:

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

Przed wywołaniem metody rozszerzenia, zmień bieżącą kulturę niezmienną:

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

Daje to gwarancję, że analizuje Twojej aplikacji liczby takie same na dowolnym serwerze, niezależnie od jego kultury domyślnej.

Teraz można metody rozszerzenia konwertować argumenty ciągu zapytania z typem double:

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

Aby łatwo przetestować kod przetwarzania, zaktualizuj odpowiedzi, aby uwzględnić wartości argumentów:

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

W tym momencie można uruchomić aplikacji sieci web i czy działa analizy kodu. Dodawanie wartości do żądania sieci web w przeglądarce i powinna wyświetlić zaktualizowane wyniki.

### <a name="build-a-random-weather-forecast"></a>Tworzenie losowego prognozę pogody

Kolejnego zadania jest tworzenie losowego prognozę pogody. Zacznijmy od kontener danych, który zawiera wartości, które chcesz uzyskać prognozę pogody:

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions =
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HighTemperatureFahrenheit { get; }
    public int LowTemperatureFahrenheit { get; }
    public int AverageWindSpeedMph { get; }
    public string Condition { get; }
}
```

Następnie można utworzyć konstruktora, który losowo ustawia te wartości. Ten konstruktor korzysta z wartości dla szerokości i długości geograficznej, inicjator `Random` generator liczb. Oznacza to, że prognozy dla tej samej lokalizacji jest taka sama. Jeśli zmienisz argumenty dla szerokości i długości geograficznej, uzyskasz różne prognozy (z powodu uruchamiania innego materiału siewnego).

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

Można teraz wygenerować prognozy 5-dniowy w metodzie odpowiedzi:

```csharp
if (latitude.HasValue && longitude.HasValue)
{
    var forecast = new List<WeatherReport>();
    for (var days = 1; days <= 5; days++)
    {
        forecast.Add(new WeatherReport(latitude.Value, longitude.Value, days));
    }
}
```

### <a name="build-the-json-response"></a>Tworzenie odpowiedź w formacie JSON

Zadanie kodu końcowego na serwerze polega na przekonwertowaniu `WeatherReport` listy w dokumencie JSON i Wyślij z powrotem do klienta. Zacznijmy od utworzenia dokumentu JSON. Serializator Newtonsoft JSON dodasz do listy zależności. Możesz to zrobić za pomocą następujących `dotnet` polecenia:

```console
dotnet add package Newtonsoft.Json
```

Następnie należy użyć `JsonConvert` klasę umożliwiającą zapisanie obiektu na ciąg:

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

Powyższy kod konwertuje obiekt prognozy (lista `WeatherForecast` obiektów) do dokumentu JSON. Po skonstruowaniu dokumentu odpowiedzi, Ustaw typ zawartości `application/json`i zapisać ciąg.

Aplikacja zostanie teraz uruchomiona i zwraca losową prognozy.

## <a name="build-a-docker-image"></a>Zbuduj obraz Docker

Nasze ostatnim zadaniem jest do uruchamiania aplikacji na platformie Docker. Utworzymy kontener platformy Docker działającą obrazu platformy Docker, który reprezentuje naszej aplikacji.

A ***obrazu platformy Docker*** jest plikiem, który definiuje środowisko do uruchamiania aplikacji.

A ***kontener platformy Docker*** reprezentuje uruchomionego wystąpienia obrazu platformy Docker.

Analogicznie, można traktować *obrazu platformy Docker* jako *klasy*i *kontener platformy Docker* jako obiekt lub wystąpienie tej klasy.  

Następujący plik Dockerfile będzie służyć do naszych potrzeb:

```
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

Zajmijmy się jego zawartość.

Pierwszy wiersz określa obrazu źródłowego, używana do tworzenia aplikacji:

```
FROM microsoft/dotnet:2.1-sdk AS build
```

Docker umożliwia skonfigurowanie obraz maszyny, na podstawie szablonu źródłowego. Oznacza, nie musisz podać wszystkie parametry maszyny, podczas uruchamiania, wystarczy podać wszelkie zmiany. Zmiany w tym miejscu będzie zawierać naszej aplikacji.

W tym przykładzie użyjemy `2.1-sdk` wersję `dotnet` obrazu. To jest najprostszym sposobem utworzenia działającego środowiska Docker. Ten obraz zawiera środowisko uruchomieniowe platformy .NET Core i .NET Core SDK.
Który sprawia, że łatwiej rozpocząć pracę i skompilować, ale utworzyć większy obraz, dlatego użyjemy tego obrazu do tworzenia aplikacji i inny obraz do jej uruchomienia.

Następne wiersze instalacji i skompilować aplikację:

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

Spowoduje to kopiowanie pliku projektu z bieżącego katalogu, do maszyny Wirtualnej platformy Docker i Przywróć wszystkie pakiety. Przy użyciu interfejsu wiersza polecenia platformy dotnet oznacza, że obraz platformy Docker musi zawierać zestaw .NET Core SDK. Po tym kopiowane pozostałej części aplikacji, a `dotnet
publish` polecenie kompiluje i pakiety aplikacji.

Na koniec Utwórz drugi obraz platformy Docker, który uruchamia aplikację:

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

Używa tego obrazu `2.1-aspnetcore-runtime` wersję `dotnet` obrazu, który zawiera wszystkie elementy niezbędne do uruchamiania aplikacji ASP.NET Core, ale nie zawiera zestawu .NET Core SDK. Oznacza to, ten obraz nie może służyć do tworzenia aplikacji .NET Core, ale zapewnia także finalnego obrazu mniejsze.

Aby działało, możemy skopiować zbudowanych aplikacji z pierwszy obraz do drugiej.

`ENTRYPOINT` Polecenia informowania platformy Docker, jakie polecenia uruchamia usługę.

## <a name="building-and-running-the-image-in-a-container"></a>Tworzenie i uruchamianie obrazu w kontenerze

Umożliwia tworzenie obrazu i uruchom usługę w kontenerze platformy Docker. Nie chcesz, wszystkie pliki z katalogu lokalnego do obrazu. Zamiast tego będziesz tworzyć aplikacji w kontenerze. Utworzysz `.dockerignore` plik, aby określić katalogi, które nie są kopiowane do obrazu. Nie chcesz dowolne zasoby kompilacji skopiowane. Określ kompilację i publikowanie katalogów w `.dockerignore` pliku:

```
bin/*
obj/*
out/*
```

Tworzenia obrazów przy użyciu `docker build` polecenia. Uruchom następujące polecenie z katalogu zawierającego kod w języku.

```console
docker build -t weather-microservice .
```

To polecenie powoduje utworzenie obrazu kontenera na podstawie informacji z pliku Dockerfile. `-t` Argument zawiera tag lub nazwę dla tego obrazu kontenera. W powyższym wierszu polecenia jest znacznika używany w kontenerze platformy Docker `weather-microservice`. Po wykonaniu tego polecenia, masz kontener gotowe do uruchomienia nowej usługi. 

Uruchom następujące polecenie, aby uruchomić kontenera i uruchomić usługi:

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

`-d` Opcji oznacza, że uruchomienia kontenera odłączona od bieżącego terminalu. Oznacza to, że dane wyjściowe polecenia nie będą widzieć w terminalu. `-p` Opcja wskazuje mapowanie portów między usługą i hosta. W tym miejscu mówi, że wszystkie żądania przychodzącego na porcie 80 powinien być przekazywany do portu 80 w kontenerze. Za pomocą 80 zastępuje port, który nasłuchuje usługi, i jest domyślnym portem dla aplikacji produkcyjnych. `--name` Argument nazwy działającym kontenerem. Jest wygodną nazwę, której można użyć do pracy z tego kontenera.

Możesz zobaczyć, czy obraz jest uruchomiona, sprawdzając polecenia:

```console
docker ps
```

Jeśli Twój kontener działa, zobaczysz wiersza, który jest wyświetlany w uruchomionych procesów. (Może być tylko jeden).

Usługi można sprawdzić, otwierając przeglądarkę i przejdź do hosta lokalnego i określenie szerokości i długości geograficznej:

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a>Dołączanie do uruchomionego kontenera

Po uruchomieniu usługi w oknie polecenia można uzyskać informacje diagnostyczne drukowania dla każdego żądania. Nie widzisz tych informacji, gdy kontener jest uruchomiony w trybie odłączonym. Platformy Docker dołączyć polecenia umożliwia dołączanie do uruchomionego kontenera, dzięki czemu można wyświetlić informacje dziennika.  Uruchom następujące polecenie z poziomu okna polecenia:

```console
docker attach --sig-proxy=false hello-docker
```

`--sig-proxy=false` Argument oznacza, że <kbd>Ctrl</kbd>+<kbd>C</kbd> polecenia nie są wysyłane do procesu kontenera, lecz raczej zatrzymać `docker attach` polecenia. Ostatni argument jest nazwa nadana kontenera w `docker run` polecenia. 

> [!NOTE]
> Przypisany identyfikator kontenera platformy Docker można również użyć do odwoływania się do dowolnego kontenera. Jeśli nie określono nazwy kontenera w `docker run` należy użyć identyfikator kontenera.

Otwórz przeglądarkę i przejdź do usługi. Zostaną wyświetlone komunikaty diagnostyczne w oknie polecenia z dołączonym uruchomionego kontenera.

Naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>C</kbd> można zatrzymać procesu dołączania.

Po zakończeniu pracy z kontenera, możesz zatrzymać:

```console
docker stop hello-docker
```

Kontener i obraz jest nadal dostępna w przypadku ponownego uruchomienia.  Jeśli chcesz usunąć kontener z komputera, należy użyć tego polecenia:

```console
docker rm hello-docker
```

Jeśli chcesz usunąć nieużywane obrazy z komputera, należy użyć tego polecenia:

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a>Wniosek 

W ramach tego samouczka skompilowane mikrousług platformy ASP.NET Core, a wyposażony w kilka funkcji proste.

Wbudowane obrazu kontenera na potrzeby usługi Docker i uruchomienia kontenera na komputerze. Dołączony oknie terminalu do usługi i dostrzegła komunikaty diagnostyczne z poziomu usługi.

Po drodze pokazano kilka funkcji C# języka w działaniu.
