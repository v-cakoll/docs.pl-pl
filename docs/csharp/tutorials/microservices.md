---
title: Mikrousług hostowanych w Docker - C#
description: Dowiedz się, jak utworzyć asp.net podstawowe usługi, które są uruchamiane w kontenerach Docker
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 1f4b38243beb1210b1374bd701fac66b2fa72cc5
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106353"
---
# <a name="microservices-hosted-in-docker"></a>Mikrousług hostowanych w Docker

W tym samouczku opisano zadania niezbędne do tworzenia i wdrażania mikrousługi platformy ASP.NET Core w kontenerze Docker. W trakcie tego samouczka dowiesz się:

* Jak wygenerować aplikacji platformy ASP.NET Core.
* Jak utworzyć środowisko deweloperskie Docker.
* Jak utworzyć obraz Docker na podstawie istniejącego obrazu.
* Jak wdrożyć usługę w kontenerze Docker.

Na bieżąco zostanie wyświetlony również pewne funkcje języka C#:

* Jak konwertować obiekty C# ładunek JSON.
* Jak utworzyć obiekty niezmienne transferu danych.
* Jak do przetwarzania przychodzących żądań HTTP oraz do generowania odpowiedzi HTTP.
* Jak pracować z typów wartości null.

Możesz [wyświetlić lub pobrać przykładową aplikację](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) dla tego tematu. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="why-docker"></a>Dlaczego Docker?

Docker można łatwo tworzyć obrazy standardowe maszyny do hostowania usług w centrum danych lub w chmurze publicznej. Docker umożliwia konfigurowanie obrazu i replikować ją w razie potrzeby można skalować instalacji aplikacji.

Cały kod w tym samouczku będzie działać w dowolnym środowisku .NET Core.
Dodatkowe zadania dotyczące instalacji Docker będzie działać dla aplikacji platformy ASP.NET Core. 

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować komputer, aby uruchomić oprogramowanie .NET Core. Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.
Można uruchomić tej aplikacji, w systemie Windows, Linux, macOS lub w kontenerze Docker.
Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych. Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.

Należy również zainstalować aparatem platformy Docker. Zobacz [strona instalacji Docker](http://www.docker.com/products/docker) instrukcje dla danej platformy.
Docker można zainstalować wiele dystrybucje systemu Linux, macOS lub systemu Windows. Strona powyżej zawiera sekcje do każdego z dostępnych instalacji.

## <a name="create-the-application"></a>Tworzenie aplikacji

Teraz, po zainstalowaniu wszystkich narzędzi, Utwórz nową aplikację platformy ASP.NET Core w katalogu o nazwie "WeatherMicroservice", wykonując następujące polecenie w ulubionych powłoki:

```console
dotnet new web -o WeatherMicroservice
```

`dotnet` Polecenia są uruchamiane narzędzia niezbędne do tworzenia aplikacji .NET. Każdy zlecenie wykonuje inne polecenie.

`dotnet new` Polecenie służy do tworzenia .net Core projektów.

`-o WeatherMicroservice` Po `dotnet new` polecenie służy do tworzenia aplikacji platformy ASP.NET Core lokalizację.

Dla tego mikrousługi chcemy aplikacji sieci web najprostszy, najbardziej lekkie to możliwe, więc użyliśmy "Core pustego szablonu platformy ASP.NET", określając jej nazwę krótką `web`.

Szablon tworzy cztery pliki:

* Pliku Startup.cs. Zawiera podstawę aplikacji.
* Plik Program.cs. Zawiera punkt wejścia aplikacji.
* Plik WeatherMicroservice.csproj. To jest plik kompilacji dla aplikacji.
* Plik Properties/launchSettings.json. Zawiera ustawienia debugowania używane przez IDEs.

Teraz możesz uruchomić aplikacji szablonu wygenerowanego:

```console
dotnet run
```

To polecenie spowoduje przywrócenie najpierw zależności wymagane do tworzenia aplikacji i późniejszego kompilowania aplikacji.

Domyślna konfiguracja nasłuchuje `http://localhost:5000`. Można otworzyć przeglądarkę i przejdź do strony i "Witaj świecie!" w temacie Komunikat.

Gdy wszystko będzie gotowe, można zamknąć aplikacji, naciskając klawisz <kbd>Ctrl</kbd>+<kbd>C</kbd>.

### <a name="anatomy-of-an-aspnet-core-application"></a>Anatomia aplikacji platformy ASP.NET Core

Teraz gdy masz utworzoną aplikację, Przyjrzyjmy się implementowania tej funkcji. Istnieją dwa wygenerowanych plików, które są w tym momencie zastosowanie szczególnie: WeatherMicroservice.csproj i Startup.cs. 

Pliku .csproj zawiera informacje o projekcie.
Są dwa węzły, które są najbardziej interesujące `<TargetFramework>` i `<PackageReference>`.

`<TargetFramework>` Węzeł określa wersję platformy .NET, która może uruchomić tę aplikację.

Każdy `<PackageReference>` węzła jest używany do określenia pakietu, który jest wymagany dla tej aplikacji.

Aplikacja jest zaimplementowana w pliku Startup.cs. Ten plik zawiera klasę uruchamiania.

Te dwie metody są wywoływane przez infrastrukturę platformy ASP.NET Core, aby skonfigurować i uruchomić aplikację. `ConfigureServices` Metoda opisuje usług, które są niezbędne dla tej aplikacji. Tworzysz mikrousługi gotowa, więc nie trzeba skonfigurować wszelkie zależności. `Configure` Metody konfiguruje obsługi przychodzących żądań HTTP. Szablon generuje prosty program obsługi, który ma odpowiadać na każde żądanie od tekstu "Hello World!".

## <a name="build-a-microservice"></a>Tworzenie mikrousługi

Możesz zacząć kompilacji usługi będzie dostarczać pogody z dowolnego miejsca na całym świecie. W aplikacji produkcyjnej możesz wywołać niektóre usługi do pobierania danych pogody. Dla naszej próbki możemy zostanie wygenerowany losowe prognozie pogody. 

Istnieje wiele zadań, które należy wykonać w celu wdrożenia naszej usługi pogody losowe:

* Analizuje przychodzące żądanie odczytu współrzędne geograficzne.
* Generowanie niektórych losowe dane prognozy.
* Konwertowanie losowe dane prognozy z C# obiektów JSON pakietów.
* Ustaw nagłówek odpowiedzi, aby wskazać, że Twoje wyśle usługi z powrotem JSON.
* Zapisu odpowiedzi.

Kolejnych sekcjach prowadzą użytkownika przez każdy z tych kroków.

### <a name="parsing-the-query-string"></a>Podczas analizowania ciągu zapytania

Zostaną analizując ciąg zapytania. Usługa będzie akceptować "lat" i "long" argumentów dla ciągu zapytania w tym formularzu:

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

Wszystkie zmiany, które należy podjąć są zdefiniowane jako argument wyrażenia lambda `app.Run` w klasie uruchamiania.

Argument na wyrażeniu lambda jest `HttpContext` dla żądania. Jedną z właściwości jest `Request` obiektu. `Request` Obiekt ma `Query` właściwość, która zawiera słownik wszystkich wartości na ciąg zapytania dla żądania. Dodanie pierwszy jest to znalezienie wartości szerokości i długości geograficznej:

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

`Query` Słownika wartości są `StringValue` typu. Tego typu może zawierać kolekcji ciągów. Usługi pogodzie każda wartość jest pojedynczy ciąg. Dlatego jest wywołanie `FirstOrDefault()` w powyższym kodzie. 

Następnie należy konwertować ciągi na symulacyjnych. Metoda służy do przekonwertowania ciągu na wartość typu double jest `double.TryParse()`:

```csharp
bool TryParse(string s, out double result);
```

Ta metoda wykorzystuje C# limit parametrów, aby wskazać, czy ciąg wejściowy można przekonwertować na wartość typu double. Jeśli ciąg reprezentują reprezentację prawidłową wartość o podwójnej precyzji, metoda zwraca wartość true i `result` argument zawiera wartość. Jeśli ciąg nie reprezentuje prawidłową wartość o podwójnej precyzji, metoda zwraca wartość false.

Istnieje możliwość dostosowania tego interfejsu API przy użyciu *— metoda rozszerzenia* zwracającą *wartości null typu double*. A *typ dopuszczający wartość null wartości* jest typem, który reprezentuje pewien typ wartości i również przechowywane braku lub wartość null. Typ dopuszczający wartość null jest reprezentowana przez dodanie `?` znak do deklaracji typu. 

Metody rozszerzenia są metody, które są zdefiniowane jako metody statyczne, ale przez dodanie `this` modyfikator w pierwszym parametrze można wywołać tak, jakby są oni członkami tej klasy. Metody rozszerzenia można zdefiniować tylko w klasach statycznych. Poniżej przedstawiono definicję klasy zawierające metody rozszerzenia dla analizy:

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

Przed wywołaniem metody rozszerzenia, należy zmienić bieżącej kultury invariant:

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

Dzięki temu, że Twojej aplikacji po analizie numery takie same na każdym serwerze, niezależnie od jego domyślną kulturę.

Teraz można użyć — metoda rozszerzenia Aby przekonwertować typu double argumenty ciągu zapytania:

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

Aby łatwo testowania analizy kodu, należy zaktualizować odpowiedzi, aby uwzględnić wartości argumentów:

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

W tym momencie można uruchomić aplikacji sieci web i czy działa analizy kodu. Dodawanie wartości do żądania sieci web w przeglądarce i powinna zostać wyświetlona zaktualizowanych wyników.

### <a name="build-a-random-weather-forecast"></a>Losowe prognozie pogody kompilacji

Następnym zadaniem jest losowe prognozie pogody kompilacji. Zacznijmy od kontener danych, który zawiera wartości, które mają dla prognozie pogody:

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

Następnie utwórz konstruktora, który losowo ustawia te wartości. Ten konstruktor korzysta wartości dla współrzędne geograficzne do inicjatora `Random` generatora liczb. Oznacza to, że prognozy dla tej samej lokalizacji jest taka sama. Jeśli zmienisz argumenty współrzędne geograficzne, uzyskasz różnych prognozy (ponieważ rozpoczynać różnych inicjatora).

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

Teraz można wygenerować prognozy 5 dni w metodę odpowiedzi:

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

Zadanie kodu końcowego na serwerze jest konwersja `WeatherReport` listy w dokumencie JSON i wysyłania, która z powrotem do klienta. Zacznijmy od utworzenia dokumentu JSON. Serializator Newtonsoft JSON zostanie dodana do listy zależności. Możesz to zrobić przy użyciu następujących `dotnet` polecenia:

```console
dotnet add package Newtonsoft.Json
```

Następnie należy użyć `JsonConvert` klasa umożliwiająca zapisanie obiektu na ciąg:

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

Powyższy kod konwertuje obiekt prognozy (lista `WeatherForecast` obiekty) w dokumencie JSON. Po skonstruowaniu dokumentu odpowiedzi, Ustaw typ zawartości `application/json`i zapisać ciąg.

Teraz aplikacji działa i zwraca losowe prognoz.

## <a name="build-a-docker-image"></a>Utwórz obraz Docker

Nasze ostatnim zadaniem jest aby uruchomić aplikację w Docker. Utworzymy kontener Docker uruchomionym obrazem Docker reprezentujący naszej aplikacji.

A ***Docker obrazu*** jest plik definiujący środowisko do uruchamiania aplikacji.

A ***kontenera Docker*** reprezentuje działającego wystąpienia obrazu Docker.

Analogicznie, można traktować *obrazu Docker* jako *klasy*i *kontenera Docker* jako obiekt lub wystąpienia tej klasy.  

Następujący plik Dockerfile będzie służyć do naszej celów:

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

Przejdźmy za pośrednictwem jego zawartość.

Pierwszy wiersz określa obrazu źródłowego używaną do tworzenia aplikacji:

```
FROM microsoft/dotnet:2.1-sdk AS build
```

Docker pozwala na skonfigurowanie obraz maszyny, na podstawie szablonu źródłowego. To oznacza, nie trzeba podać parametry maszyny, podczas uruchamiania, wystarczy podać wszelkie zmiany. Zmiany w tym miejscu należy dołączyć naszej aplikacji.

W tym przykładzie użyjemy `2.1-sdk` wersji `dotnet` obrazu. Jest to najprostszy sposób tworzenia działającego środowiska Docker. Ten obraz zawiera środowisko uruchomieniowe .NET Core i Core SDK platformy .NET.
Który ułatwia rozpoczęcie pracy i kompilacji, ale utworzyć większy obraz, dlatego użyjemy tego obrazu do tworzenia aplikacji i inny obraz go uruchomić.

Następne wiersze Instalatora i skompilować aplikację:

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

Spowoduje to skopiuj plik projektu z bieżącego katalogu do maszyny Wirtualnej platformy Docker i przywrócić wszystkie pakiety. Użycie dotnet interfejsu wiersza polecenia oznacza, że obraz Docker musi zawierać .NET Core SDK. Po wykonaniu tej pozostałej części aplikacji są kopiowane i `dotnet
publish` polecenie tworzy i pakiety aplikacji.

Na koniec utworzymy obraz Docker drugiej, który uruchomi aplikację:

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

Używa tego obrazu `2.1-aspnetcore-runtime` wersji `dotnet` obrazu, który zawiera wszystkie elementy niezbędne do uruchomienia aplikacji platformy ASP.NET Core, ale nie zawiera zestawu SDK .NET Core. Oznacza to, ten obraz nie może służyć do tworzenia aplikacji platformy .NET Core, ale zapewnia także finalnego obrazu mniejsze.

Aby działało, możemy skopiować zbudowanych aplikacji z pierwszego obrazu do drugiej.

`ENTRYPOINT` Polecenie informuje Docker, jakie polecenia uruchamia usługę.

## <a name="building-and-running-the-image-in-a-container"></a>Tworzenie i uruchamianie obrazu w kontenerze

Umożliwia tworzenie obrazu i uruchom usługę w kontenerze Docker. Nie ma wszystkich plików z katalogu lokalnego kopiowane do obrazu. Zamiast tego zostanie utworzenie aplikacji w kontenerze. Utworzysz `.dockerignore` plik, aby określić katalogi, które nie są kopiowane do obrazu. Nie ma żadnego zasoby kompilacji skopiowane. Określ kompilację i publikowanie katalogów w `.dockerignore` pliku:

```
bin/*
obj/*
out/*
```

Tworzenie, przy użyciu obrazu `docker build` polecenia. Uruchom następujące polecenie z katalogu z kodem.

```console
docker build -t weather-microservice .
```

To polecenie tworzy obraz kontenera, zgodnie z informacjami w Twojej plik Dockerfile. `-t` Argument zawiera tag lub nazwę dla tego obrazu kontenera. W powyższym wierszu polecenia jest znacznik kontenera Docker `weather-microservice`. Po zakończeniu wykonywania tego polecenia należy kontener gotowy do uruchomienia nowej usługi. 

Uruchom następujące polecenie, aby uruchomić kontenera i uruchomić usługi:

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

`-d` Opcja oznacza, że Uruchom kontenera odłączona od bieżącego terminala. Oznacza to, że dane wyjściowe polecenia nie będą widzieć w terminalu. `-p` Opcja wskazuje mapowanie portów między usługą i hosta. W tym miejscu mówi, że wszystkie żądania przychodzącego na porcie 80 powinny być przekazywane do portu 80 w kontenerze. Przy użyciu 80 odpowiada port, który nasłuchiwanie usługi, który jest domyślnym portem dla aplikacji produkcyjnych. `--name` Argument nazwy użytkownika uruchomionych kontenera. Jest to nazwa wygodny, używanej do pracy z tego kontenera.

Możesz sprawdzić, czy obraz jest uruchomiony przez sprawdzenie, polecenie:

```console
docker ps
```

Jeśli działa z kontenera, zobaczysz wiersza, który jest wyświetlany w uruchomionych procesów. (Może być tylko jeden).

Usługi można sprawdzić, otwierając przeglądarkę i przechodząc do localhost i określający współrzędne geograficzne:

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a>Dołączanie do uruchomionego kontenera

Po uruchomieniu usługi w oknie polecenia mogliby zobaczyć informacje diagnostyczne drukowane dla każdego żądania. Gdy z kontenera działa w trybie odłączony nie widzisz tych informacji. Polecenie Dołącz Docker umożliwia dołączanie do uruchomionego kontenera tak, aby informacje dziennika.  W oknie polecenie Uruchom następujące polecenie:

```console
docker attach --sig-proxy=false hello-docker
```

`--sig-proxy=false` Argumentu oznacza, że <kbd>Ctrl</kbd>+<kbd>C</kbd> poleceń nie wysyłana do procesu kontenera, ale raczej zatrzymać `docker attach` polecenia. Ostatni argument jest nazwa kontenera w `docker run` polecenia. 

> [!NOTE]
> Umożliwia także Docker przypisany identyfikator kontenera do odwoływania się do dowolnego kontenera. Jeśli nie określono nazwę Twojej kontenera w `docker run` musisz użyć identyfikatora kontenera.

Otwórz przeglądarkę i przejdź do usługi. Zostanie wyświetlone komunikaty diagnostyczne w systemie windows polecenie z dołączonego uruchomionych kontenera.

Naciśnij klawisz <kbd>Ctrl</kbd>+<kbd>C</kbd> można zatrzymać procesu dołączania.

Po zakończeniu pracy z Twojej kontenera, można zatrzymać go:

```console
docker stop hello-docker
```

Kontener i obrazu jest wciąż dostępna na potrzeby ponownego uruchomienia.  Jeśli chcesz usunąć kontener z komputera, możesz użyć tego polecenia:

```console
docker rm hello-docker
```

Jeśli chcesz usunąć nieużywane obrazów z komputera, możesz użyć tego polecenia:

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a>Wniosek 

W tym samouczku wbudowane mikrousługi platformy ASP.NET Core i dodać kilka prostych funkcji.

Wbudowane Docker kontenera obrazu dla tej usługi i uruchomienia tego kontenera na tym komputerze. Dołączone do usługi okno terminalu i był wyświetlany komunikaty diagnostyczne z usługi.

Przeglądania widać kilka funkcji języka C# w akcji.
