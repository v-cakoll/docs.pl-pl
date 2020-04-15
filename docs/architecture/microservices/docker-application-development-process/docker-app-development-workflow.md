---
title: Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker
description: Poznaj szczegóły przepływu pracy do tworzenia aplikacji opartych na platformie Docker. Rozpocznij krok po kroku i zapoznaj się z niektórymi szczegółami, aby zoptymalizować pliki dockerfiles i zakończyć uproszczonym przepływem pracy dostępnym podczas korzystania z programu Visual Studio.
ms.date: 01/30/2020
ms.openlocfilehash: 2f380c840e186c345f9222aa6b0cf1097a74874e
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389204"
---
# <a name="development-workflow-for-docker-apps"></a>Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker

Cykl życia tworzenia aplikacji rozpoczyna się na komputerze, jako deweloper, gdzie kod aplikacji przy użyciu preferowanego języka i przetestować go lokalnie. Dzięki temu przepływowi pracy, niezależnie od wybranego języka, struktury i platformy, zawsze tworzysz i testujesz kontenery platformy Docker, ale robisz to lokalnie.

Każdy kontener (wystąpienie obrazu platformy Docker) zawiera następujące składniki:

- Wybór systemu operacyjnego, na przykład dystrybucja systemu Linux, Windows Nano Server lub Windows Server Core.

- Pliki dodane podczas tworzenia, na przykład kod źródłowy i pliki binarne aplikacji.

- Informacje o konfiguracji, takie jak ustawienia środowiska i zależności.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Przepływ pracy do tworzenia aplikacji opartych na kontenerach platformy Docker

W tej sekcji opisano przepływ pracy tworzenia *pętli wewnętrznej* dla aplikacji opartych na kontenerze platformy Docker. Przepływ pracy pętli wewnętrznej oznacza, że nie bierze pod uwagę szerszego przepływu pracy DevOps, który może obejmować do wdrożenia produkcyjnego i skupia się tylko na pracy deweloperskiej wykonanej na komputerze dewelopera. Początkowe kroki konfigurowania środowiska nie są uwzględniane, ponieważ te kroki są wykonywane tylko raz.

Aplikacja składa się z własnych usług oraz dodatkowych bibliotek (zależności). Poniżej przedstawiono podstawowe kroki, które zwykle należy wykonać podczas tworzenia aplikacji platformy Docker, jak pokazano na rysunku 5-1.

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram przedstawiający 7 kroków, które należy wykonać w celu utworzenia aplikacji konteneryzowanej.":::
Proces tworzenia aplikacji platformy Docker: 1 — kodowanie aplikacji, 2 — Write Dockerfile/s, 3 - Tworzenie obrazów zdefiniowanych w witrynie Dockerfile/s, 4 - (opcjonalnie) Tworzenie usług w pliku docker-compose.yml, 5 - Uruchom kontener lub aplikację docker-compose, 6 - Przetestuj aplikację lub mikrousługi, 7 - Wypychanie do repozytorium i powtarzanie.
:::image-end:::

**Rysunek 5-1.** Przepływ pracy krok po kroku do tworzenia aplikacji konteneryzowanych platformy Docker

W tej sekcji cały ten proces jest szczegółowy i każdy główny krok jest wyjaśnione przez koncentrując się na środowisku programu Visual Studio.

Podczas korzystania z podejścia do tworzenia edytora/interfejsu wiersza polecenia (na przykład Visual Studio Code plus Docker CLI w systemie macOS lub Windows), musisz znać każdy krok, zazwyczaj bardziej szczegółowo niż w przypadku korzystania z programu Visual Studio. Aby uzyskać więcej informacji na temat pracy w środowisku interfejsu wiersza polecenia, zobacz cykl [życia aplikacji docker konteneryzowany](https://aka.ms/dockerlifecycleebook/)e-book za pomocą platform i narzędzi firmy Microsoft .

Podczas korzystania z programu Visual Studio 2019 wiele z tych kroków jest obsługiwanych za Ciebie, co znacznie zwiększa produktywność. Jest to szczególnie ważne, gdy używasz programu Visual Studio 2019 i kierowania aplikacji wielu kontenerów. Na przykład za pomocą jednego kliknięcia `Dockerfile` myszą visual studio dodaje i `docker-compose.yml` plik do projektów z konfiguracji aplikacji. Po uruchomieniu aplikacji w programie Visual Studio, tworzy obraz platformy Docker i uruchamia aplikację wielu kontenerów bezpośrednio w programie Docker; pozwala nawet debugować kilka kontenerów naraz. Te funkcje zwiększą szybkość rozwoju.

Jednak tylko dlatego, że visual studio sprawia, że te kroki automatyczne nie oznacza, że nie trzeba wiedzieć, co się dzieje pod docker. W związku z tym następujące wskazówki szczegółowe każdy krok.

![Obraz dla kroku 1.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Rozpocznij kodowanie i utwórz początkową aplikację lub usługę bazową bazową

Tworzenie aplikacji platformy Docker jest podobny do sposobu tworzenia aplikacji bez platformy Docker. Różnica polega na tym, że podczas tworzenia platformy Docker wdrażasz i testujesz aplikację lub usługi uruchomione w kontenerach platformy Docker w środowisku lokalnym (instalator maszyny wirtualnej z systemem Linux przez platformę Docker lub bezpośrednio windows, jeśli używasz kontenerów systemu Windows).

### <a name="set-up-your-local-environment-with-visual-studio"></a>Konfigurowanie środowiska lokalnego za pomocą programu Visual Studio

Aby rozpocząć, upewnij się, że masz zainstalowaną wersję [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) dla systemu Windows, jak wyjaśniono w poniższych instrukcjach:

[Wprowadzenie do platformy Docker CE dla systemu Windows](https://docs.docker.com/docker-for-windows/)

Ponadto potrzebujesz programu Visual Studio 2019 w wersji 16.4 lub nowszej z zainstalowanym obciążeniem **deweloperskim .NET Core,** jak pokazano na rysunku 5-2.

![Zrzut ekranu przedstawiający wybór rozwoju międzyplatformowego .NET Core.](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

**Rysunek 5-2**. Wybieranie **wieloplatformowego obciążenia programistycznego .NET Core** podczas konfiguracji programu Visual Studio 2019

Można rozpocząć kodowanie aplikacji w zwykły .NET (zwykle w .NET Core, jeśli planujesz używać kontenerów) jeszcze przed włączeniem platformy Docker w aplikacji i wdrażania i testowania w docker. Jednak zaleca się, aby rozpocząć pracę nad programem Docker tak szybko, jak to możliwe, ponieważ będzie to rzeczywiste środowisko i wszelkie problemy można odnajdyć tak szybko, jak to możliwe. Jest to zalecane, ponieważ visual studio sprawia, że tak łatwo pracować z platformyą Docker, że prawie czuje się przejrzysty — najlepszy przykład podczas debugowania aplikacji wielu kontenerów z programu Visual Studio.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Wprowadzenie do platformy Docker CE dla systemu Windows** \
  <https://docs.docker.com/docker-for-windows/>

- **Visual Studio 2019** \
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Obraz dla kroku 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Tworzenie pliku dockerfile powiązanego z istniejącym obrazem bazowym platformy .NET

Potrzebujesz pliku Dockerfile dla każdego niestandardowego obrazu, który chcesz utworzyć; potrzebujesz również dockerfile dla każdego kontenera do wdrożenia, czy wdrażać automatycznie z programu Visual Studio lub ręcznie przy użyciu interfejsu wiersza polecenia platformy Docker (docker uruchamiania i tworzenia docker polecenia). Jeśli aplikacja zawiera jedną usługę niestandardową, potrzebujesz jednego pliku Dockerfile. Jeśli aplikacja zawiera wiele usług (jak w architekturze mikrousług), potrzebujesz jednego pliku Dockerfile dla każdej usługi.

Plik Docker jest umieszczany w folderze głównym aplikacji lub usługi. Zawiera polecenia, które informują platformy Docker, jak skonfigurować i uruchomić aplikację lub usługę w kontenerze. Można ręcznie utworzyć plik Dockerfile w kodzie i dodać go do projektu wraz z zależnościami .NET.

W programie Visual Studio i jego narzędziach dla platformy Docker to zadanie wymaga tylko kilku kliknięć myszą. Podczas tworzenia nowego projektu w programie Visual Studio 2019 istnieje opcja o nazwie **Włącz obsługę platformy Docker**, jak pokazano na rysunku 5-3.

![Zrzut ekranu przedstawiający pole wyboru Włącz obsługę platformy Docker.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

**Rysunek 5-3**. Włączanie obsługi platformy Docker podczas tworzenia nowego projektu ASP.NET Core w programie Visual Studio 2019

Można również włączyć obsługę platformy Docker w istniejącym projekcie aplikacji sieci Web ASP.NET Core, klikając prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierając **pozycję Dodaj** > **obsługę platformy Docker...**, jak pokazano na rysunku 5-4.

![Zrzut ekranu przedstawiający opcję Obsługa platformy Docker w menu Dodaj.](./media/docker-app-development-workflow/add-docker-support-option.png)

**Rysunek 5-4**. Włączanie obsługi platformy Docker w istniejącym projekcie programu Visual Studio 2019

Ta akcja dodaje *Dockerfile* do projektu z wymaganą konfiguracją i jest dostępna tylko w projektach ASP.NET Core.

W podobny sposób program Visual Studio `docker-compose.yml` może również dodać plik dla całego rozwiązania z opcją **Dodaj > Obsługę Koordynatora Kontenera...**. W kroku 4 przyjrzymy się tej opcji bardziej szczegółowo.

### <a name="using-an-existing-official-net-docker-image"></a>Korzystanie z istniejącego oficjalnego obrazu platformy Docker .NET

Zwykle tworzysz niestandardowy obraz kontenera na obrazie podstawowym, który można uzyskać z oficjalnego repozytorium, takiego jak rejestr [Centrum platformy Docker.](https://hub.docker.com/) To jest dokładnie to, co dzieje się w ramach obejmuje po włączeniu obsługi platformy Docker w programie Visual Studio. Plik Dockerfile użyje `dotnet/core/aspnet` istniejącego obrazu.

Wcześniej wyjaśniliśmy, których obrazów platformy Docker i repozytoriów można użyć, w zależności od struktury i systemu operacyjnego, który wybrałeś. Na przykład, jeśli chcesz użyć ASP.NET Core (Linux lub Windows), `mcr.microsoft.com/dotnet/core/aspnet:3.1`obraz do użycia jest . W związku z tym wystarczy określić, jaki podstawowy obraz platformy Docker będzie używany dla kontenera. Można to zrobić, dodając `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` do dockerfile. Zostanie to automatycznie wykonane przez program Visual Studio, ale jeśli chcesz zaktualizować wersję, zaktualizujesz tę wartość.

Korzystanie z oficjalnego repozytorium obrazów platformy .NET z usługi Docker Hub z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym rozwoju, testowania i produkcji).

W poniższym przykładzie przedstawiono przykładowy plik dockerfile dla kontenera ASP.NET Core.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

W tym przypadku obraz jest oparty na wersji 3.1 oficjalnego obrazu core docker ASP.NET (multi-arch dla Linuksa i Windowsa). Jest to `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`ustawienie . (Aby uzyskać więcej informacji na temat tego obrazu podstawowego, zobacz stronę [Obraz platformy Docker .NET](https://hub.docker.com/_/microsoft-dotnet-core/) Core). W pliku Dockerfile należy również poinstruować platformy Docker, aby nasłuchiwał na porcie TCP, który będzie używany w czasie wykonywania (w tym przypadku port 80, skonfigurowany z ustawieniem EXPOSE).

Można określić dodatkowe ustawienia konfiguracji w Dockerfile, w zależności od języka i struktury, którego używasz. Na przykład wiersz ENTRYPOINT `["dotnet", "MySingleContainerWebApp.dll"]` z informuje docker, aby uruchomić aplikację .NET Core. Jeśli używasz SDK i .NET Core CLI (dotnet CLI) do tworzenia i uruchamiania aplikacji .NET, to ustawienie będzie inne. Najważniejsze jest to, że linia ENTRYPOINT i inne ustawienia będą się różnić w zależności od języka i platformy, którą wybierzesz dla aplikacji.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Tworzenie obrazów platformy Docker dla aplikacji core platformy .NET** \
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- **Zbuduj swój własny obraz**. W oficjalnej dokumentacji platformy Docker.\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- **Na bieżąco z obrazami kontenerów .NET** \
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- **Używanie platformy .NET i platformy Docker razem — Aktualizacja dockerCon 2018** \
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a>Korzystanie z repozytoriów obrazów wielokołowych

Pojedyncze repozytorium może zawierać warianty platformy, takie jak obraz systemu Linux i obraz systemu Windows. Ta funkcja umożliwia dostawcom, takim jak Microsoft (twórcom obrazów podstawowych), tworzenie jednego repozytorium obejmującego wiele platform (czyli Linux i Windows). Na przykład repozytorium [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) dostępne w rejestrze Docker Hub zapewnia obsługę systemów Linux i Windows Nano Server przy użyciu tej samej nazwy repozytorium.

Jeśli określisz tag, kierowanie na platformę, która jest jawna, jak w następujących przypadkach:

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  Obiekty docelowe: .NET Core 3.1 tylko w systemie Linux

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  Obiekty docelowe: .NET Core 3.1 tylko w systemie Windows Nano Server

Jeśli jednak określisz tę samą nazwę obrazu, nawet przy użyciu tego `aspnet` samego znacznika, obrazy wielokołowe (takie jak obraz) będą używać wersji systemu Linux lub Windows w zależności od wdrażającego systemu operacyjnego hosta platformy Docker, jak pokazano w poniższym przykładzie:

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  Multi-arch: .NET Core 3.1 tylko w systemie Linux lub Windows Nano Server w zależności od systemu operacyjnego hosta platformy Docker

W ten sposób, po wyciągnięciu obrazu z hosta systemu Windows, będzie ciągnąć wariant systemu Windows, a wyciągając tę samą nazwę obrazu z hosta Linuksa pociągnie wariant Linuksa.

### <a name="multi-stage-builds-in-dockerfile"></a>Kompilacje wieloetapowe w pliku Dockerfile

Plik Docker jest podobny do skryptu wsadowego. Podobnie jak w przypadku konieczności skonfigurowania komputera z wiersza polecenia.

Zaczyna się od obrazu podstawowego, który konfiguruje kontekst początkowy, to jak system plików startowych, który znajduje się na górze systemu operacyjnego hosta. Nie jest to system operacyjny, ale można myśleć o nim jak "" OS wewnątrz pojemnika.

Wykonanie każdego wiersza polecenia tworzy nową warstwę w systemie plików ze zmianami z poprzedniego, dzięki czemu po połączeniu powstaje system plików.

Ponieważ każda nowa warstwa "opiera się" na poprzedniej, a wynikowy rozmiar obrazu zwiększa się z każdym poleceniem, obrazy mogą być bardzo duże, jeśli muszą zawierać, na przykład zestaw SDK potrzebny do tworzenia i publikowania aplikacji.

To jest, gdy wieloetapowe kompilacje dostać się do działki (z Docker 17.05 i wyższe), aby zrobić swoją magię.

Podstawową ideą jest to, że można oddzielić proces wykonywania dockerfile etapami, gdzie etap jest obrazem początkowym, po którym następuje jedno lub więcej poleceń, a ostatni etap określa ostateczny rozmiar obrazu.

Krótko mówiąc, kompilacje wieloetapowe umożliwiają dzielenie tworzenia w różnych "fazach", a następnie montaż końcowego obrazu, biorąc tylko odpowiednie katalogi z etapów pośrednich. Ogólna strategia korzystania z tej funkcji jest:

1. Użyj podstawowego obrazu SDK (nie ma znaczenia, jak duży), ze wszystkim potrzebnym do tworzenia i publikowania aplikacji w folderze, a następnie

2. Użyj obrazu bazowego, małego obrazu tylko w czasie wykonywania i skopiuj folder publikowania z poprzedniego etapu, aby uzyskać mały obraz końcowy.

Prawdopodobnie najlepszym sposobem, aby zrozumieć wieloetapowe przechodzi Dockerfile szczegółowo, wiersz po wierszu, więc zacznijmy od początkowego Dockerfile utworzone przez program Visual Studio podczas dodawania docker pomocy technicznej do projektu i dostanie się do niektórych optymalizacji później.

Początkowy plik dockerfile może wyglądać mniej więcej tak:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks …
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

A oto szczegóły, wiersz po wierszu:

- **#1 liniowy:** Rozpocznij etap od "małego" obrazu podstawowego tylko do wykonywania, nazwij go **bazą w** celach informacyjnych.

- **#2 liniowy:** Utwórz **katalog /app** na obrazie.

- **#3 liniowy:** Odsłonić port **80**.

- **#5 liniowe:** Rozpocznij nowy etap od "dużego" obrazu do budowania/publikowania. Call it **build** w celach informacyjnych.

- **#6 liniowy:** Utwórz katalog **/src** na obrazie.

- **#7 liniowe:** Do linii 16, skopiować odwołuje **.csproj** plików projektu, aby móc przywrócić pakiety później.

- **#17 liniowe:** Przywracanie pakietów dla projektu **Catalog.API** i projektów, do których istnieje odwołanie.

- **#18 liniowy:** Skopiuj **całe drzewo katalogów dla rozwiązania** (z wyjątkiem plików/katalogów zawartych w pliku **.dockerignore)** do katalogu **/src** na obrazie.

- **#19 liniowy:** Zmień bieżący folder na projekt **Catalog.API.**

- **#20 liniowy:** Tworzenie projektu (i innych zależności projektu) i dane wyjściowe do **katalogu /app** w obrazie.

- **#22 liniowy:** Rozpocznij nowy etap kontynuując od kompilacji. Nazwij go **opublikować** w celach informacyjnych.

- **#23 liniowe:** Publikowanie projektu (i zależności) i dane wyjściowe do **katalogu /app** w obrazie.

- **#25 liniowy:** Rozpocznij nowy etap kontynuując od **podstawy** i nazwij go **końcowym**.

- **#26 liniowe:** Zmień bieżący katalog na **/app**.

- **#27 liniowy:** Skopiuj **katalog /app** z **publikowania** etapowego do bieżącego katalogu.

- **#28 liniowy:** Zdefiniuj polecenie do uruchomienia po uruchomieniu kontenera.

Teraz przyjrzyjmy się niektórym optymalizacjom, aby poprawić wydajność całego procesu, co w przypadku eShopOnContainers oznacza około 22 minut lub więcej, aby zbudować kompletne rozwiązanie w kontenerach systemu Linux.

Skorzystasz z funkcji pamięci podręcznej warstw platformy Docker, co jest dość proste: jeśli obraz podstawowy i polecenia są takie same jak niektóre wcześniej wykonane, można po prostu użyć warstwy wynikowej bez konieczności wykonywania poleceń, oszczędzając w ten sposób trochę czasu.

Skupmy się więc na etapie **budowania,** linie 5-6 są w większości takie same, ale linie 7-17 różnią się dla każdej usługi z eShopOnContainers, więc muszą wykonywać za każdym razem, jednak jeśli zmienisz linie 7-16 na:

```Dockerfile
COPY . .
```

Wtedy byłoby tak samo dla każdej usługi, to skopiować całe rozwiązanie i stworzyłby większą warstwę, ale:

1. Proces kopiowania zostanie wykonany tylko za pierwszym razem (i podczas przebudowy w przypadku zmiany pliku) i będzie używał pamięci podręcznej dla wszystkich innych usług i

2. Ponieważ większy obraz występuje w fazie pośredniej, nie ma wpływu na końcowy rozmiar obrazu.

Następna znacząca optymalizacja obejmuje polecenie wykonywane w wierszu `restore` 17, które jest również różne dla każdej usługi eShopOnContainers. Jeśli zmienisz ten wiersz na just:

```Dockerfile
RUN dotnet restore
```

Przywróciłoby pakiety dla całego rozwiązania, ale potem znowu zrobiłoby to tylko raz, zamiast 15 razy z obecną strategią.

Jednak `dotnet restore` działa tylko wtedy, gdy w folderze znajduje się pojedynczy plik projektu lub rozwiązania, więc osiągnięcie tego jest nieco bardziej skomplikowane i sposób rozwiązania go, bez wchodzenia w zbyt wiele szczegółów, jest to:

1. Dodaj następujące wiersze do **.dockerignore:**

   - `*.sln`, aby zignorować wszystkie pliki rozwiązań w głównym drzewie folderów

   - `!eShopOnContainers-ServicesAndWebApps.sln`, aby uwzględnić tylko ten plik rozwiązania.

2. Dołącz `/ignoreprojectextensions:.dcproj` argument `dotnet restore`do , więc również ignoruje docker-compose projektu i tylko przywraca pakiety dla rozwiązania eShopOnContainers-ServicesAndWebApps.

Dla ostatecznej optymalizacji, to po prostu zdarza się, że linia 20 jest zbędna, jak linia 23 również buduje aplikację i przychodzi w istocie, tuż po wierszu 20, więc nie ma innego czasochłonne polecenia.

Wynikowy plik jest wtedy:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -o /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a>Tworzenie obrazu bazowego od podstaw

Można utworzyć własny obraz bazowy platformy Docker od podstaw. Ten scenariusz nie jest zalecane dla kogoś, kto zaczyna się od platformy Docker, ale jeśli chcesz ustawić określone bity własnego obrazu podstawowego, można to zrobić.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Obrazy .NET Core z wieloma łukami**.\
  <https://github.com/dotnet/announcements/issues/14>

- **Tworzenie obrazu bazowego**. Oficjalna dokumentacja platformy Docker.\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Obraz dla kroku 3.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Tworzenie niestandardowych obrazów platformy Docker i osadzanie w nich aplikacji lub usługi

Dla każdej usługi w aplikacji należy utworzyć powiązany obraz. Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, wystarczy jeden obraz.

Należy zauważyć, że obrazy platformy Docker są tworzone automatycznie w programie Visual Studio. Poniższe kroki są potrzebne tylko dla przepływu pracy edytora/interfejsu wiersza polecenia i wyjaśnione w celu uzyskania jasności co się dzieje pod spodem.

Jako deweloper musisz rozwijać i testować lokalnie, dopóki nie wypchniesz ukończonej funkcji lub zmienisz system kontroli źródła (na przykład na GitHub). Oznacza to, że należy utworzyć obrazy platformy Docker i wdrożyć kontenery na lokalnym hoście platformy Docker (Windows lub Linux VM) i uruchomić, przetestować i debugować dla tych kontenerów lokalnych.

Aby utworzyć obraz niestandardowy w środowisku lokalnym przy użyciu interfejsu wiersza polecenia platformy Docker i pliku Dockerfile, można użyć polecenia kompilacji platformy docker, jak na rysunku 5-5.

![Zrzut ekranu przedstawiający dane wyjściowe konsoli polecenia kompilacji platformy docker.](./media/docker-app-development-workflow/run-docker-build-command.png)

**Rysunek 5-5**. Tworzenie niestandardowego obrazu platformy Docker

Opcjonalnie zamiast bezpośrednio uruchamiać kompilację platformy docker z folderu projektu, można najpierw wygenerować folder z `dotnet publish`możliwością wdrożenia `docker build` z wymaganymi bibliotekami i plikami binarnymi platformy .NET, uruchamiając program ,a następnie użyć polecenia.

Spowoduje to utworzenie obrazu platformy `cesardl/netcore-webapi-microservice-docker:first`Docker o nazwie . W takim przypadku :first to tag reprezentujący określoną wersję. Ten krok można powtórzyć dla każdego obrazu niestandardowego, który należy utworzyć dla złożonej aplikacji platformy Docker.

Gdy aplikacja jest wykonana z wielu kontenerów (oznacza to, że jest `docker-compose up --build` to aplikacja wielu kontenerów), można również użyć polecenia do tworzenia wszystkich powiązanych obrazów za pomocą jednego polecenia przy użyciu metadanych ujawnionych w powiązanych plikach docker-compose.yml.

Istniejące obrazy można znaleźć w repozytorium lokalnym za pomocą polecenia obrazy platformy docker, jak pokazano na rysunku 5-6.

![Wyjście konsoli z obrazów dokowane polecenia, pokazując istniejące obrazy.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

**Rysunek 5-6.** Wyświetlanie istniejących obrazów przy użyciu polecenia Obrazy docker

### <a name="creating-docker-images-with-visual-studio"></a>Tworzenie obrazów platformy Docker za pomocą programu Visual Studio

Korzystając z programu Visual Studio do utworzenia projektu z obsługą platformy Docker, nie można jawnie utworzyć obraz. Zamiast tego obraz jest tworzony po naciśnięciu **klawisza F5** (lub **Ctrl-F5),** aby uruchomić dockerized aplikacji lub usługi. Ten krok jest automatyczny w programie Visual Studio i nie zobaczysz, że tak się stanie, ale ważne jest, aby wiedzieć, co się dzieje pod spodem.

![Obraz opcjonalnego kroku 4.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Definiowanie usług w pliku docker-compose.yml podczas tworzenia aplikacji platformy Docker z wieloma kontenerami

Plik [docker-compose.yml](https://docs.docker.com/compose/compose-file/) umożliwia zdefiniowanie zestawu powiązanych usług, które mają być wdrożone jako skomponowana aplikacja z poleceniami wdrażania. Konfiguruje również jego relacje zależności i konfiguracji w czasie wykonywania.

Aby użyć pliku docker-compose.yml, należy utworzyć plik w głównym lub głównym folderze rozwiązania, z zawartością podobną do tej w poniższym przykładzie:

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

Ten plik docker-compose.yml jest uproszczoną i scaloną wersją. Zawiera statyczne dane konfiguracyjne dla każdego kontenera (takie jak nazwa obrazu niestandardowego), który jest zawsze wymagany, oraz informacje o konfiguracji, które mogą zależeć od środowiska wdrażania, takie jak parametry połączenia. W późniejszych sekcjach dowiesz się, jak podzielić konfigurację docker-compose.yml na wiele plików docker-compose i zastąpić wartości w zależności od środowiska i typu wykonania (debugowanie lub wydanie).

Przykład pliku docker-compose.yml definiuje cztery `webmvc` usługi: usługę (aplikacja sieci web), `basket-api`dwie mikrousługi `sqldata`(`ordering-api` i ) i jeden kontener źródła danych, oparty na programie SQL Server dla systemu Linux uruchomionym jako kontener. Każda usługa zostanie wdrożona jako kontener, więc obraz platformy Docker jest wymagany dla każdego.

Plik docker-compose.yml określa nie tylko, jakie kontenery są używane, ale także sposób ich indywidualnej konfiguracji. Na przykład `webmvc` definicja kontenera w pliku .yml:

- Używa wstępnie utworzonego `eshop/web:latest` obrazu. Można jednak również skonfigurować obraz, który ma być zbudowany jako część wykonywania docker-compose z dodatkową konfiguracją opartą na sekcji kompilacji: w pliku docker-compose.

- Inicjuje dwie zmienne środowiskowe (CatalogUrl i OrderingUrl).

- Przekazuje narażony port 80 w kontenerze do portu zewnętrznego 80 na komputerze-hoście.

- Łączy aplikację sieci web z usługą katalogowania i zamawiania z ustawieniem depends_on. Powoduje to, że usługa czekać, aż te usługi są uruchamiane.

Firma Docker-compose.yml zostanie ponownie przeanalizowana w pliku docker-compose.yml w dalszej części, gdy omówimy sposób implementowania mikrousług i aplikacji z wieloma kontenerami.

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a>Praca z docker-compose.yml w programie Visual Studio 2019

Oprócz dodawania Dockerfile do projektu, jak wspomniano wcześniej, Visual Studio 2017 (od wersji 15.8 na) można dodać obsługę koordynatora doklin y do rozwiązania.

Po dodaniu obsługi orchestrator kontenera, jak pokazano na rysunku 5-7, po raz pierwszy visual studio tworzy Dockerfile dla `docker-compose*.yml` projektu i tworzy nowy (usługa sekcji) projektu w rozwiązaniu z kilku plików globalnych, a następnie dodaje projekt do tych plików. Następnie można otworzyć pliki docker-compose.yml i zaktualizować je o dodatkowe funkcje.

Musisz powtórzyć tę operację w każdym projekcie, który chcesz uwzględnić w pliku docker-compose.yml.

W momencie pisania tego tekstu visual studio obsługuje **docker compose** i **Kubernetes/Helm** orchestrators.

![Zrzut ekranu przedstawiający opcję Obsługa koordynatora kontenerów w menu kontekstowym projektu.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

**Rysunek 5-7**. Dodawanie pomocy technicznej platformy Docker w programie Visual Studio 2019 przez kliknięcie prawym przyciskiem myszy projektu ASP.NET Core

Po dodaniu obsługi koordynatora do rozwiązania w programie Visual Studio zostanie `docker-compose.dcproj` również wyświetlony nowy węzeł (w pliku projektu) w Eksploratorze rozwiązań, który zawiera dodane pliki docker-compose.yml, jak pokazano na rysunku 5-8.

![Zrzut ekranu przedstawiający węzeł docker-compose w Eksploratorze rozwiązań.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

**Rysunek 5-8**. Węzeł drzewa **docker-compose** dodany w Eksploratorze rozwiązań programu Visual Studio 2019

Za pomocą polecenia można wdrożyć aplikację z wieloma kontenerami za pomocą `docker-compose up` jednego pliku docker-compose.yml. Jednak Visual Studio dodaje ich grupę, dzięki czemu można zastąpić wartości w zależności od środowiska (rozwoju lub produkcji) i typu wykonania (release lub debug). Ta funkcja zostanie wyjaśniona w późniejszych sekcjach.

![Obraz kroku 5.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Tworzenie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, można go uruchomić, wdrażając go na hoście platformy Docker (maszyna wirtualna lub serwer fizyczny). Jeśli jednak aplikacja zawiera wiele usług, można wdrożyć ją jako złożoną aplikację, używając pojedynczego polecenia interfejsu wiersza polecenia (`docker-compose up)`lub z programem Visual Studio, który użyje tego polecenia w ramach okładek. Przyjrzyjmy się różnym opcjom.

### <a name="option-a-running-a-single-container-application"></a>Opcja A: Uruchamianie aplikacji z jednym kontenerem

#### <a name="using-docker-cli"></a>Korzystanie z interfejsu wiersza polecenia platformy Docker

Kontener platformy Docker można `docker run` uruchomić za pomocą polecenia, jak pokazano na rysunku 5-9:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Powyższe polecenie utworzy nowe wystąpienie kontenera z określonego obrazu, za każdym razem, gdy jest uruchamiane. Za pomocą `--name` parametru można nadać nazwę kontenerowi, a następnie użyć `docker start {name}` (lub użyć identyfikatora kontenera lub nazwy automatycznej) do uruchomienia istniejącego wystąpienia kontenera.

![Zrzut ekranu przedstawiający kontener platformy Docker przy użyciu polecenia uruchom docker.](./media/docker-app-development-workflow/use-docker-run-command.png)

**Rysunek 5-9**. Uruchamianie kontenera platformy Docker przy użyciu polecenia uruchom docker

W takim przypadku polecenie wiąże port wewnętrzny 5000 kontenera z portem 80 komputera hosta. Oznacza to, że host nasłuchuje na porcie 80 i przekazuje do portu 5000 w kontenerze.

Wyświetlony skrót jest identyfikatorem kontenera i jest również przypisany losowa `--name` nazwa czytelna, jeśli opcja nie jest używana.

#### <a name="using-visual-studio"></a>Korzystanie z programu Visual Studio

Jeśli nie dodano obsługi koordynatora kontenera, można również uruchomić aplikację jednego kontenera w programie Visual Studio, naciskając **Ctrl-F5** i można również użyć **F5** do debugowania aplikacji w kontenerze. Kontener jest uruchamiany lokalnie przy użyciu uruchamiania platformy docker.

### <a name="option-b-running-a-multi-container-application"></a>Opcja B: Uruchamianie aplikacji wielokontenerowej

W większości scenariuszy przedsiębiorstw aplikacja platformy Docker będzie składać się z wielu usług, co oznacza, że należy uruchomić aplikację wielu kontenerów, jak pokazano na rysunku 5-10.

![Maszyna wirtualna z kilkoma kontenerami platformy Docker](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

**Rysunek 5-10**. Maszyna wirtualna z wdrożonymi kontenerami platformy Docker

#### <a name="using-docker-cli"></a>Korzystanie z interfejsu wiersza polecenia platformy Docker

Aby uruchomić aplikację wielu kontenerów z interfejsem `docker-compose up` wiersza polecenia platformy Docker, należy użyć polecenia. To polecenie używa pliku **docker-compose.yml,** który masz na poziomie rozwiązania do wdrożenia aplikacji z wieloma kontenerami. Rysunek 5-11 przedstawia wyniki podczas uruchamiania polecenia z głównego katalogu rozwiązania, który zawiera plik docker-compose.yml.

![Widok ekranu podczas uruchamiania polecenia docker-compose up](./media/docker-app-development-workflow/results-docker-compose-up.png)

**Rysunek 5-11**. Przykładowe wyniki podczas uruchamiania polecenia docker-compose up

Po uruchomieniu polecenia docker-compose up aplikacja i jej powiązane kontenery są wdrażane na hoście platformy Docker, jak pokazano na rysunku 5-10.

#### <a name="using-visual-studio"></a>Korzystanie z programu Visual Studio

Uruchamianie aplikacji z wieloma kontenerami przy użyciu programu Visual Studio 2019 nie może uzyskać żadnych prostszych. Wystarczy nacisnąć **klawisze Ctrl-F5,** aby uruchomić lub **F5** do debugowania, jak zwykle, konfigurowanie projektu **docker-compose** jako projektu uruchamiania.  Visual Studio obsługuje wszystkie potrzebne ustawienia, dzięki czemu można tworzyć punkty przerwania jak zwykle i debugować, co ostatecznie stać się niezależne procesy uruchomione w "zdalnych serwerach", z debugerem już dołączone, tak po prostu.

Jak wspomniano wcześniej, za każdym razem, gdy dodajesz obsługę rozwiązania platformy Docker do projektu w ramach rozwiązania, ten projekt jest skonfigurowany w globalnym pliku docker-compose.yml, który umożliwia uruchamianie lub debugowanie całego rozwiązania naraz. Visual Studio uruchomi jeden kontener dla każdego projektu, który ma włączoną obsługę rozwiązań platformy Docker i wykona wszystkie kroki wewnętrzne dla Ciebie (dotnet publikowania, docker kompilacji, itp.).

Jeśli chcesz rzucić okiem na wszystkie zuchwałość, spójrz na plik:

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Ważnym punktem jest to, że, jak pokazano na rysunku 5-12, w programie Visual Studio 2019 istnieje dodatkowe polecenie **platformy Docker** dla akcji klucza F5. Ta opcja umożliwia uruchamianie lub debugowanie aplikacji z wieloma kontenerami przez uruchomienie wszystkich kontenerów zdefiniowanych w plikach docker-compose.yml na poziomie rozwiązania. Możliwość debugowania rozwiązań wielu kontenerów oznacza, że można ustawić kilka punktów przerwania, każdy punkt przerwania w innym projekcie (kontenerze), a podczas debugowania z programu Visual Studio zatrzymasz się w punktach przerwania zdefiniowanych w różnych projektach i uruchomionych na różnych kontenerach.

![Zrzut ekranu przedstawiający pasek narzędzi debugowania z uruchomionym projektem docker-compose.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

**Rysunek 5-12**. Uruchamianie aplikacji z wieloma kontenerami w programie Visual Studio 2019

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Wdrażanie kontenera ASP.NET na zdalnym hoście platformy Docker** \
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Uwaga dotycząca testowania i wdrażania za pomocą koordynatorów

Docker-compose up i docker uruchom polecenia (lub uruchamianie i debugowanie kontenerów w programie Visual Studio) są odpowiednie do testowania kontenerów w środowisku programistycznym. Ale nie należy używać tego podejścia dla wdrożeń produkcyjnych, gdzie należy kierować orchestrators jak [Kubernetes](https://kubernetes.io/) lub [sieci szkieletowej usług.](https://azure.microsoft.com/services/service-fabric/) Jeśli używasz kubernetes, należy użyć [zasobników](https://kubernetes.io/docs/concepts/workloads/pods/pod/) do organizowania kontenerów i [usług](https://kubernetes.io/docs/concepts/services-networking/service/) do ich sieci. [Wdrożeń](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) służy również do organizowania tworzenia i modyfikowania zasobników.

![Obraz dla kroku 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Testowanie aplikacji platformy Docker przy użyciu lokalnego hosta platformy Docker

Ten krok będzie się różnić w zależności od tego, co robi aplikacja. W prostej aplikacji sieci Web .NET Core, która jest wdrażana jako pojedynczy kontener lub usługa, można uzyskać dostęp do usługi, otwierając przeglądarkę na hoście platformy Docker i przechodząc do tej witryny, jak pokazano na rysunku 5-13. (Jeśli konfiguracja w pliku Dockerfile mapuje kontener na port na hoście, który ma mniej niż 80, dołącz port hosta w adresie URL).

![Zrzut ekranu odpowiedzi z localhost/API/values.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

**Rysunek 5-13**. Przykład testowania aplikacji platformy Docker lokalnie przy użyciu localhost

Jeśli localhost nie wskazuje adresu IP hosta platformy Docker (domyślnie podczas korzystania z platformy Docker CE, powinien), aby przejść do usługi, użyj adresu IP karty sieciowej komputera.

Należy zauważyć, że ten adres URL w przeglądarce używa portu 80 dla określonego przykładu kontenera, który został omówiony. Jednak wewnętrznie żądania są przekierowywane do portu 5000, ponieważ w ten sposób został wdrożony za pomocą polecenia uruchamiania platformy docker, jak wyjaśniono w poprzednim kroku.

Można również przetestować aplikację za pomocą curl z terminala, jak pokazano na rysunku 5-14. W instalacji platformy Docker w systemie Windows domyślny adres IP hosta platformy Docker jest zawsze 10.0.75.1 oprócz rzeczywistego adresu IP komputera.

![Wyjście konsoli z http://10.0.75.1/API/values coraz z curl.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

**Rysunek 5-14**. Przykład testowania aplikacji platformy Docker lokalnie przy użyciu curl

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a>Testowanie i debugowanie kontenerów za pomocą programu Visual Studio 2019

Podczas uruchamiania i debugowania kontenerów za pomocą programu Visual Studio 2019 można debugować aplikację .NET w taki sam sposób, jak podczas uruchamiania bez kontenerów.

### <a name="testing-and-debugging-without-visual-studio"></a>Testowanie i debugowanie bez programu Visual Studio

Jeśli tworzysz przy użyciu podejścia edytora/interfejsu wiersza polecenia, debugowanie kontenerów jest trudniejsze i prawdopodobnie będziesz chciał debugować, generując ślady.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Debugowanie aplikacji w lokalnym kontenerze platformy Docker** \
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- **Steve Lasker. Tworzenie, debugowanie, wdrażanie ASP.NET podstawowych aplikacji za pomocą platformy Docker.** Wideo. \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Uproszczony przepływ pracy podczas tworzenia kontenerów za pomocą programu Visual Studio

Skutecznie przepływu pracy podczas korzystania z programu Visual Studio jest o wiele prostsze niż w przypadku korzystania z edytora/interfejsu wiersza polecenia podejście. Większość kroków wymaganych przez program Docker związane z plikiem Dockerfile i docker-compose.yml są ukryte lub uproszczone przez program Visual Studio, jak pokazano na rysunku 5-15.

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram przedstawiający pięć uproszczonych kroków, które należy wykonać w celu utworzenia aplikacji.":::
Proces tworzenia aplikacji platformy Docker: 1 — kodowanie aplikacji, 2 — Write Dockerfile/s, 3 - Tworzenie obrazów zdefiniowanych w witrynie Dockerfile/s, 4 - (opcjonalnie) Tworzenie usług w pliku docker-compose.yml, 5 - Uruchom kontener lub aplikację docker-compose, 6 - Przetestuj aplikację lub mikrousługi, 7 - Wypychanie do repozytorium i powtarzanie.
:::image-end:::

**Rysunek 5-15**. Uproszczony przepływ pracy podczas tworzenia programu Visual Studio

Ponadto należy wykonać krok 2 (dodawanie obsługi platformy Docker do projektów) tylko raz. W związku z tym przepływ pracy jest podobny do zwykłych zadań programistycznych podczas korzystania z platformy .NET dla innych programów deweloperskich. Musisz wiedzieć, co się dzieje w ramach okładek (proces kompilacji obrazu, jakie obrazy podstawowe używasz, wdrażanie kontenerów, itp.), a czasami trzeba będzie również edytować Plik Dockerfile lub docker-compose.yml pliku, aby dostosować zachowania. Ale większość pracy jest znacznie uproszczone przy użyciu programu Visual Studio, dzięki czemu o wiele bardziej wydajne.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Steve Lasker. Program .NET Docker Development w programie Visual Studio (2017)** \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Konfigurowanie kontenerów systemu Windows za pomocą poleceń programu PowerShell w pliku dockerfile

[Kontenery systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umożliwiają konwertowanie istniejących aplikacji systemu Windows na obrazy platformy Docker i wdrażanie ich przy tym samym narzędziom, co reszta ekosystemu platformy Docker. Aby użyć kontenerów systemu Windows, należy uruchomić polecenia programu PowerShell w pliku Dockerfile, jak pokazano w poniższym przykładzie:

```Dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

W takim przypadku używamy obrazu podstawowego Windows Server Core (ustawienie OD) i instalujemy usługi IIS za pomocą polecenia programu PowerShell (ustawienie RUN). W podobny sposób można również użyć poleceń programu PowerShell do skonfigurowania dodatkowych składników, takich jak ASP.NET 4.x, .NET 4.6 lub innego oprogramowania systemu Windows. Na przykład następujące polecenie w pliku dockerfile konfiguruje ASP.NET 4.5:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Zasoby dodatkowe

- **aspnet-docker/Dockerfile.** Przykład polecenia programu PowerShell do uruchamiania z plików dockerfiles w celu uwzględnienia funkcji systemu Windows.\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](../multi-container-microservice-net-applications/index.md)
