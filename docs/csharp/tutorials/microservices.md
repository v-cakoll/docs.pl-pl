---
title: Mikrousług hostowanych w Docker - C#
description: Dowiedz się, jak utworzyć asp.net podstawowe usługi, które są uruchamiane w kontenerach Docker
ms.date: 02/03/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: eacfa87e465e5f7737dbd2bfc4c6a77ffc5531c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="microservices-hosted-in-docker"></a>Mikrousług hostowanych w Docker

W tym samouczku opisano zadania niezbędne do tworzenia i wdrażania mikrousługi platformy ASP.NET Core w kontenerze Docker. W trakcie tego samouczka dowiesz się:

* Sposób generowania aplikacji platformy ASP.NET Core za pomocą narzędzia Yeoman
* Jak utworzyć środowisko deweloperskie Docker
* Jak utworzyć obraz Docker na podstawie istniejącego obrazu.
* Jak wdrożyć usługę w kontenerze Docker.

Na bieżąco zostanie wyświetlony również pewne funkcje języka C#:

* Jak konwertować obiekty C# ładunek JSON.
* Jak tworzyć obiekty niezmienne transferu danych
* Jak do przetwarzania przychodzących żądań HTTP oraz do generowania odpowiedzi HTTP
* Jak pracować z typów wartości null

Możesz [wyświetlić lub pobrać przykładową aplikację](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) dla tego tematu. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="why-docker"></a>Dlaczego Docker?

Docker można łatwo tworzyć obrazy standardowe maszyny do hostowania usług w centrum danych lub w chmurze publicznej. Docker umożliwia konfigurowanie obrazu i replikować ją w razie potrzeby można skalować instalacji aplikacji.

Cały kod w tym samouczku będzie działać w dowolnym środowisku .NET Core.
Dodatkowe zadania dotyczące instalacji Docker będzie działać dla aplikacji platformy ASP.NET Core. 

## <a name="prerequisites"></a>Wymagania wstępne
Należy skonfigurować komputer, aby uruchomić oprogramowanie .NET core. Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.
Można uruchomić tej aplikacji, w systemie Windows, Ubuntu Linux, macOS lub w kontenerze Docker. Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych. Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora. Można jednak użyć dowolnego narzędzia potrafisz.

Należy również zainstalować aparatem platformy Docker. Zobacz [strona instalacji Docker](http://www.docker.com/products/docker) instrukcje dla danej platformy.
Docker można zainstalować wiele dystrybucje systemu Linux, macOS lub systemu Windows. Strona powyżej zawiera sekcje do każdego z dostępnych instalacji.

Większość składników musi zostać zainstalowana, są wykonywane przez Menedżera pakietów. Jeśli masz Menedżera pakietów w node.js `npm` zainstalowany, możesz pominąć ten krok. W przeciwnym razie zainstaluj najnowszą NodeJs z [nodejs.org](https://nodejs.org) której zostanie zainstalowany Menedżer pakietów npm. 

Na tym etapie należy zainstalować wiele narzędzi wiersza polecenia, które obsługuje platformy ASP.NET core programowanie. Szablony wiersza polecenia, użyj narzędzia Yeoman, Grunt, Bower i Gulp. Jeśli masz je zainstalowane, które dobrze, w przeciwnym razie wpisz następujące polecenie w ulubionych powłoki:

`npm install -g yo bower grunt-cli gulp`

`-g` Opcja wskazuje, że jest on zainstalowany globalne, a te narzędzia są dostępne całym systemie. (Zakresy lokalnej instalacji pakietu do pojedynczego projektu). Po zainstalowaniu te podstawowe narzędzia, musisz zainstalować generatory szablonu platformy ASP.NET narzędzia yeoman:

`npm install -g generator-aspnet`

## <a name="create-the-application"></a>Tworzenie aplikacji

Teraz, po zainstalowaniu wszystkich narzędzi do tworzenia nowej aplikacji platformy ASP.NET Core. Aby użyć generatora wiersza polecenia, należy wykonać następujące polecenie narzędzia yeoman w ulubionych powłoki:

`yo aspnet`

To polecenie wyświetla monit o wybranie rodzaju aplikacji, w którym chcesz utworzyć. Dla tego mikrousługi mają aplikacji sieci web najprostszy, najbardziej lekkie możliwe, dlatego wybierz pustą aplikację sieci Web. Szablon wyświetli monit o podanie nazwy. Wybierz "WeatherMicroservice". 

Szablon tworzy osiem plików:

* .Gitignore dostosowany do aplikacji platformy ASP.NET Core.
* Pliku Startup.cs. Zawiera podstawę aplikacji.
* Plik Program.cs. Zawiera punkt wejścia aplikacji.
* Plik WeatherMicroservice.csproj. To jest plik kompilacji dla aplikacji.
* Plik Dockerfile. Ten skrypt tworzy obraz Docker dla aplikacji.
* A README.md. Zawiera linki do innych zasobów platformy ASP.NET Core.
* Plik web.config. Zawiera podstawowe informacje o konfiguracji.
* Plik runtimeconfig.template.json. Zawiera ustawienia debugowania używane przez IDEs.

Teraz możesz uruchomić aplikacji szablonu wygenerowany. Który ma odbywa się za pomocą szereg narzędzi wiersza polecenia. `dotnet` Polecenia są uruchamiane narzędzia niezbędne do tworzenia aplikacji .NET. Inne polecenie wykonuje każdego zlecenia

Pierwszym krokiem jest, aby przywrócić wszystkie zależności:

```console
dotnet restore
```

Przywracania DotNet stosuje Menedżera pakietów NuGet w celu zainstalowania wymaganych pakietów do katalogu aplikacji. Generuje plik project.json.lock. Ten plik zawiera informacje dotyczące każdego pakietu, do którego istnieje odwołanie. Po przywróceniu wszystkie zależności, należy skompilować aplikację:

```console
dotnet build
```
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

I po utworzeniu aplikacji, należy uruchomić z wiersza polecenia:

```console
dotnet run
```

Domyślna konfiguracja nasłuchuje `http://localhost:5000`. Można otworzyć przeglądarkę i przejdź do strony i "Witaj świecie!" w temacie Komunikat.

### <a name="anatomy-of-an-aspnet-core-application"></a>Anatomia aplikacji platformy ASP.NET Core

Teraz gdy masz utworzoną aplikację, Przyjrzyjmy się implementowania tej funkcji. Istnieją dwa wygenerowanych plików, które są w tym momencie zastosowanie szczególnie: pliku project.json i pliku Startup.cs. 

Project.JSON zawiera informacje o projekcie. Dwa węzły, które często będzie współpracować są 'zależności' i 'struktury'. Węzeł zależności zawiera listę wszystkich pakietów, które są wymagane dla tej aplikacji.
W tej chwili jest węzłem małych wymagające tylko pakiety, które uruchomić serwera sieci web.

Węzeł 'struktury' Określa wersje i konfiguracje programu .NET framework, która może uruchomić tę aplikację.

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

### <a name="parsing-the-query-string"></a>Podczas analizowania ciągu zapytania.

Zostaną analizując ciąg zapytania. Usługa będzie akceptować "lat" i "long" argumentów dla ciągu zapytania w tym formularzu:

`http://localhost:5000/?lat=-35.55&long=-12.35`  

Wszystkie zmiany, które należy podjąć są zdefiniowane jako argument wyrażenia lambda `app.Run` w klasie uruchamiania.

Argument na wyrażeniu lambda jest `HttpContext` dla żądania. Jedną z właściwości jest `Request` obiektu. `Request` Obiekt ma `Query` właściwość, która zawiera słownik wszystkich wartości na ciąg zapytania dla żądania. Dodanie pierwszy jest to znalezienie wartości szerokości i długości geograficznej:

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

Słownik wartości zapytania są `StringValue` typu. Tego typu może zawierać kolekcji ciągów. Usługi pogodzie każda wartość jest pojedynczy ciąg. Dlatego jest wywołanie `FirstOrDefault()` w powyższym kodzie. 

Następnie należy konwertować ciągi na symulacyjnych. Metoda służy do przekonwertowania ciągu na wartość typu double jest `double.TryParse()`:

```csharp
bool TryParse(string s, out double result);
```

Ta metoda wykorzystuje C# limit parametrów, aby wskazać, czy ciąg wejściowy można przekonwertować na wartość typu double. Jeśli ciąg reprezentują reprezentację prawidłową wartość o podwójnej precyzji, metoda zwraca wartość true i `result` argument zawiera wartość. Jeśli ciąg nie reprezentuje prawidłową wartość o podwójnej precyzji, metoda zwraca wartość false.

Istnieje możliwość dostosowania tego interfejsu API przy użyciu *— metoda rozszerzenia* zwracającą *wartości null typu double*. A *typ dopuszczający wartość null wartości* jest typem, który reprezentuje pewien typ wartości i również przechowywane braku lub wartość null. Typ dopuszczający wartość null jest reprezentowana przez dodanie `?` znak do deklaracji typu. 

Metody rozszerzenia są metody, które są zdefiniowane jako metody statyczne, ale przez dodanie `this` modyfikator w pierwszym parametrze można wywołać tak, jakby są oni członkami tej klasy. Metody rozszerzenia można zdefiniować tylko w klasach statycznych. Poniżej przedstawiono definicję klasy zawierające metody rozszerzenia dla analizy:

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

`default(double?)` Wyrażenie zwraca wartość domyślną `double?` typu. Czy wartość domyślna to wartość null (lub nie).

Ta metoda rozszerzenia służy do konwertowania argumenty ciągu zapytania do typu double:

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

Aby łatwo testowania analizy kodu, należy zaktualizować odpowiedzi, aby uwzględnić wartości argumentów:

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

W tym momencie można uruchomić aplikacji sieci web i czy działa analizy kodu. Dodawanie wartości do żądania sieci web w przeglądarce i powinna zostać wyświetlona zaktualizowanych wyników.

### <a name="build-a-random-weather-forecast"></a>Losowe prognozie pogody kompilacji

Następnym zadaniem jest losowe prognozie pogody kompilacji. Zacznijmy od kontener danych, który zawiera wartości, które mają dla prognozie pogody:

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

Następnie utwórz konstruktora, który losowo ustawia te wartości. Ten konstruktor korzysta wartości szerokości i długości geograficznej jako zalążek generatora liczb losowych. Oznacza to, że prognozy dla tej samej lokalizacji jest taka sama. Jeśli zmienisz argumenty współrzędne geograficzne, otrzymasz różnych prognozy (ponieważ rozpoczyna różnych inicjatora.)

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

Teraz można wygenerować prognozy 5 dni w metodę odpowiedzi:

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]

### <a name="build-the-json-response"></a>Tworzenie odpowiedź w formacie JSON.

Zadanie kodu końcowego na serwerze jest konwertowanie tablicy WeatherReport pakietów JSON, a następnie Wyślij to do klienta. Zacznijmy od utworzenia pakietu JSON. Serializator JSON NewtonSoft zostanie dodana do listy zależności. Możesz zrobić tego za pomocą `dotnet` interfejsu wiersza polecenia:

```
dotnet add package Newtonsoft.Json
```

Następnie należy użyć `JsonConvert` klasa umożliwiająca zapisanie obiektu na ciąg:

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

Powyższy kod konwertuje obiekt prognozy (lista `WeatherForecast` obiekty) w pakiecie JSON. Po skonstruowaniu pakiet odpowiedzi, Ustaw typ zawartości `application/json`i zapisać ciąg.

Teraz aplikacji działa i zwraca losowe prognoz.

## <a name="build-a-docker-image"></a>Utwórz obraz Docker

Nasze ostatnim zadaniem jest aby uruchomić aplikację w Docker. Utworzymy kontener Docker uruchomionym obrazem Docker reprezentujący naszej aplikacji.

A ***Docker obrazu*** jest plik definiujący środowisko do uruchamiania aplikacji.

A ***kontenera Docker*** reprezentuje działającego wystąpienia obrazu Docker.

Analogicznie, można traktować *obrazu Docker* jako *klasy*i *kontenera Docker* jako obiekt lub wystąpienia tej klasy.  

Plik Dockerfile utworzonej przez szablon ASP.NET będzie służyć do naszej celów. Przejdźmy za pośrednictwem jego zawartość.

Pierwszy wiersz określa obrazu źródłowego:

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

Docker pozwala na skonfigurowanie obraz maszyny, na podstawie szablonu źródłowego. To oznacza, nie trzeba podać parametry maszyny, podczas uruchamiania, wystarczy podać wszelkie zmiany. Zmiany w tym miejscu należy dołączyć naszej aplikacji.

W tym przykładzie pierwsze użyjemy `1.1-sdk-msbuild` wersja obrazu dotnet. Jest to najprostszy sposób tworzenia działającego środowiska Docker. Ten obraz to podstawowego środowiska wykonawczego platformy dotnet i dotnet zestawu SDK. Który ułatwia rozpoczęcie pracy i kompilacji, ale utworzyć większy obraz.

Następne pięć wierszy Instalatora i skompilować aplikację:

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore 

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Spowoduje to skopiuj plik projektu z bieżącego katalogu do maszyny Wirtualnej platformy Docker i przywrócić wszystkie pakiety. Użycie dotnet interfejsu wiersza polecenia oznacza, że obraz Docker musi zawierać .NET Core SDK. Po wykonaniu tej pozostałej części aplikacji są kopiowane i dotnet publikowanie polecenie kompilacji i pakiety aplikacji.

Aplikacja jest uruchamiana w ostatnim wierszu pliku:

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

Odwołuje się tego skonfigurowanego portu `--server.urls` argument `dotnet` w ostatnim wierszu plik Dockerfile. `ENTRYPOINT` Polecenie informuje Docker, jakie polecenia i opcje wiersza polecenia Uruchom usługę. 

## <a name="building-and-running-the-image-in-a-container"></a>Tworzenie i uruchamianie obrazu w kontenerze.

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
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

`-d` Opcja oznacza, że Uruchom kontenera odłączona od bieżącego terminala. Oznacza to, że dane wyjściowe polecenia nie będą widzieć w terminalu. `-p` Opcja wskazuje mapowanie portów między usługą i hosta. W tym miejscu mówi, że wszystkie żądania przychodzącego na porcie 80 powinny zostać przekazane port 5000 w kontenerze. Za pomocą 5000 odpowiada port, którego nasłuchuje usługi z określonego w powyższym plik Dockerfile argumenty wiersza polecenia. `--name` Argument nazwy użytkownika uruchomionych kontenera. Jest to nazwa wygodny, używanej do pracy z tego kontenera. 

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

Podczas korzystania z usługi w oknie polecenia mogliby zobaczyć informacje diagnostyczne drukowane dla każdego żądania. Gdy z kontenera działa w trybie odłączony nie widzisz tych informacji. Polecenie Dołącz Docker umożliwia dołączanie do uruchomionego kontenera tak, aby informacje dziennika.  W oknie polecenie Uruchom następujące polecenie:

```console
docker attach --sig-proxy=false hello-docker
```

`--sig-proxy=false` Argumentu oznacza, że `Ctrl-C` poleceń nie wysyłana do procesu kontenera, ale raczej zatrzymać `docker attach` polecenia. Ostatni argument jest nazwa kontenera w `docker run` polecenia. 

> [!NOTE]
> Umożliwia także Docker przypisany identyfikator kontenera do odwoływania się do dowolnego kontenera. Jeśli nie określono nazwę Twojej kontenera w `docker run` musisz użyć identyfikatora kontenera.

Otwórz przeglądarkę i przejdź do usługi. Zostanie wyświetlone komunikaty diagnostyczne w systemie windows polecenie z dołączonego uruchomionych kontenera.

Naciśnij klawisz `Ctrl-C` można zatrzymać procesu dołączania.

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
