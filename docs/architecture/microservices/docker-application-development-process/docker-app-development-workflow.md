---
title: Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker
description: Zapoznaj się ze szczegółami przepływu pracy do tworzenia aplikacji opartych na platformie Docker. Rozpocznij krok po kroku i dostać się do niektórych szczegółów, aby zoptymalizować Pliki Dockerfiles i zakończyć uproszczony przepływ pracy dostępny podczas korzystania z programu Visual Studio.
ms.date: 01/30/2020
ms.openlocfilehash: c58ea2436027968143777a19286a1a0a72107717
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401642"
---
# <a name="development-workflow-for-docker-apps"></a>Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker

Cykl rozwoju aplikacji rozpoczyna się na komputerze, jako deweloper, gdzie kod aplikacji przy użyciu preferowanego języka i przetestować go lokalnie. Dzięki temu przepływowi pracy, niezależnie od wybranego języka, struktury i platformy, zawsze tworzysz i testujesz kontenery platformy Docker, ale robisz to lokalnie.

Każdy kontener (wystąpienie obrazu platformy Docker) zawiera następujące składniki:

- Wybór systemu operacyjnego, na przykład dystrybucja systemu Linux, Windows Nano Server lub Windows Server Core.

- Pliki dodawane podczas tworzenia, na przykład kod źródłowy i pliki binarne aplikacji.

- Informacje o konfiguracji, takie jak ustawienia środowiska i zależności.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Przepływ pracy do tworzenia aplikacji opartych na kontenerach platformy Docker

W tej sekcji *opisano* przepływ pracy tworzenia pętli wewnętrznej dla aplikacji opartych na kontenerach platformy Docker. Przepływ pracy w pętli wewnętrznej oznacza, że nie uwzględnia szerszego przepływu pracy DevOps, który może obejmować do wdrożenia produkcyjnego i po prostu koncentruje się na pracach rozwojowych wykonywanych na komputerze dewelopera. Początkowe kroki konfigurowania środowiska nie są uwzględniane, ponieważ te kroki są wykonywane tylko raz.

Aplikacja składa się z własnych usług oraz dodatkowych bibliotek (zależności). Poniżej przedstawiono podstawowe kroki, które zwykle wykonuje się podczas tworzenia aplikacji platformy Docker, jak pokazano na rysunku 5-1.

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram przedstawiający 7 kroków potrzebnych do utworzenia aplikacji konteneryzowanej.":::
Proces tworzenia aplikacji platformy Docker: 1 - Kod aplikacji, 2 - Pisanie dockerfile/s, 3 - Tworzenie obrazów zdefiniowanych w dockerfile/s, 4 - (opcjonalnie) Compose usługi w pliku docker-compose.yml, 5 - Uruchom kontener lub docker-compose aplikacji, 6 - Testowanie aplikacji lub mikrousług, 7 - Push to repo i powtórz.
:::image-end:::

**Rysunek 5-1.** Przepływ pracy krok po kroku do tworzenia aplikacji konteneryzowanych platformy Docker

W tej sekcji cały ten proces jest szczegółowy i każdy ważny krok jest wyjaśniony przez skupienie się na środowisku programu Visual Studio.

Korzystając z metody tworzenia edytora/wiersza wiersza wiersza (na przykład Visual Studio Code plus Docker CLI w systemie macOS lub Windows), musisz znać każdy krok, zazwyczaj bardziej szczegółowo niż w przypadku korzystania z programu Visual Studio. Aby uzyskać więcej informacji na temat pracy w środowisku interfejsów firm cli, zobacz [cykl życia aplikacji dokowania konteneryzowanego e-booka z platformami i narzędziami firmy Microsoft](https://aka.ms/dockerlifecycleebook/).

Gdy używasz programu Visual Studio 2019, wiele z tych kroków jest obsługiwanych dla Ciebie, co znacznie zwiększa produktywność. Jest to szczególnie ważne, gdy używasz programu Visual Studio 2019 i jest przeznaczony dla aplikacji wielokontenerowych. Na przykład za pomocą jednego kliknięcia `Dockerfile` myszy `docker-compose.yml` program Visual Studio dodaje plik i plik do projektów z konfiguracją dla aplikacji. Po uruchomieniu aplikacji w programie Visual Studio tworzy obraz platformy Docker i uruchamia aplikację wielokontenerową bezpośrednio w platformie Docker; umożliwia nawet debugowanie kilku kontenerów jednocześnie. Te funkcje zwiększą szybkość rozwoju.

Jednak tylko dlatego, że visual studio sprawia, że te kroki automatyczne nie oznacza, że nie trzeba wiedzieć, co się dzieje pod platformą Docker. W związku z tym następujące wskazówki szczegółowo co krok.

![Obraz dla kroku 1.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Rozpoczynanie kodowania i tworzenie początkowej aplikacji lub linii bazowej usługi

Tworzenie aplikacji platformy Docker jest podobny do sposobu tworzenia aplikacji bez platformy Docker. Różnica polega na tym, że podczas opracowywania dla platformy Docker wdrażasz i testujesz aplikację lub usługi uruchomione w kontenerach platformy Docker w środowisku lokalnym (konfiguracja maszyny Wirtualnej systemu Linux przez platformę Docker lub bezpośrednio system Windows, jeśli używasz kontenerów systemu Windows).

### <a name="set-up-your-local-environment-with-visual-studio"></a>Konfigurowanie środowiska lokalnego za pomocą programu Visual Studio

Aby rozpocząć, upewnij się, że masz zainstalowaną [wersję Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) dla systemu Windows, jak wyjaśniono w poniższych instrukcjach:

[Wprowadzenie do platformy Docker CE dla systemu Windows](https://docs.docker.com/docker-for-windows/)

Ponadto potrzebne jest program Visual Studio 2019 w wersji 16.4 lub nowszej, z zainstalowanym obciążeniem **programistycznym .NET Core dla wielu platform,** jak pokazano na rysunku 5-2.

![Zrzut ekranu przedstawiający wybór rozwoju wielu platform .NET Core.](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

**Rysunek 5-2**. Wybieranie **wieloplatformowego obciążenia programistycznego programu .NET Core** podczas instalacji programu Visual Studio 2019

Można rozpocząć kodowanie aplikacji w zwykły .NET (zwykle w .NET Core, jeśli planujesz używać kontenerów) nawet przed włączeniem platformy Docker w aplikacji i wdrażania i testowania w platformie Docker. Zaleca się jednak, aby rozpocząć pracę nad platformą Docker tak szybko, jak to możliwe, ponieważ będzie to rzeczywiste środowisko i wszelkie problemy mogą być wykrywane tak szybko, jak to możliwe. Jest to zalecane, ponieważ visual studio sprawia, że tak łatwo pracować z platformą Docker, że prawie czuje się przezroczysty — najlepszym przykładem podczas debugowania aplikacji wielokontenerowych z programu Visual Studio.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Wprowadzenie do platformy Docker CE dla systemu Windows** \
  <https://docs.docker.com/docker-for-windows/>

- **Studio Wizualne 2019** \
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Obraz dla kroku 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Tworzenie pliku Dockerfile powiązanego z istniejącym obrazem podstawowym platformy .NET

Potrzebny jest plik Dockerfile dla każdego niestandardowego obrazu, który chcesz zbudować; potrzebny jest również plik Dockerfile dla każdego kontenera do wdrożenia, niezależnie od tego, czy wdrażasz automatycznie z programu Visual Studio, czy ręcznie przy użyciu polecenia docker CLI (docker run i docker-compose). Jeśli aplikacja zawiera jedną usługę niestandardową, potrzebujesz jednego pliku Dockerfile. Jeśli aplikacja zawiera wiele usług (jak w architekturze mikrousług), potrzebujesz jednego pliku Dockerfile dla każdej usługi.

Plik Dockerfile jest umieszczany w folderze głównym aplikacji lub usługi. Zawiera polecenia, które informują platformę Docker, jak skonfigurować i uruchomić aplikację lub usługę w kontenerze. Można ręcznie utworzyć plik Dockerfile w kodzie i dodać go do projektu wraz z zależnościami .NET.

Dzięki programowi Visual Studio i jego narzędziom do platformy Docker to zadanie wymaga tylko kilku kliknięć myszą. Podczas tworzenia nowego projektu w programie Visual Studio 2019 istnieje opcja o nazwie **Włącz obsługę platformy Docker**, jak pokazano na rysunku 5-3.

![Zrzut ekranu przedstawiający pole wyboru Włącz obsługę platformy Docker.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

**Rysunek 5-3**. Włączanie obsługi platformy Docker podczas tworzenia nowego projektu ASP.NET Core w programie Visual Studio 2019

Obsługę platformy Docker można również włączyć w istniejącym projekcie aplikacji sieci Web ASP.NET Core, klikając projekt prawym przyciskiem myszy w **Eksploratorze rozwiązań** i wybierając polecenie **Dodaj** > **obsługę platformy Docker...**, jak pokazano na rysunku 5-4.

![Zrzut ekranu przedstawiający opcję Docker Support w menu Dodaj.](./media/docker-app-development-workflow/add-docker-support-option.png)

**Rysunek 5-4**. Włączanie obsługi platformy Docker w istniejącym projekcie programu Visual Studio 2019

Ta akcja dodaje *plik Dockerfile* do projektu z wymaganą konfiguracją i jest dostępna tylko w ASP.NET projektów Core.

W podobny sposób program Visual Studio `docker-compose.yml` może również dodać plik dla całego rozwiązania z opcją **Dodaj > Obsługę koordynatora kontenerów...**. W kroku 4 przeanalizujemy tę opcję bardziej szczegółowo.

### <a name="using-an-existing-official-net-docker-image"></a>Korzystanie z istniejącego oficjalnego obrazu platformy Docker platformy .NET

Zazwyczaj tworzysz niestandardowy obraz dla kontenera na obrazie bazowym uzyskanym z oficjalnego repozytorium, takiego jak rejestr [docker hub.](https://hub.docker.com/) To jest dokładnie to, co dzieje się w ramach obejmuje po włączeniu obsługi platformy Docker w programie Visual Studio. Plik Dockerfile użyje `dotnet/core/aspnet` istniejącego obrazu.

Wcześniej wyjaśniliśmy, które obrazy platformy Docker i repozytorów można użyć, w zależności od struktury i os wybrałeś. Na przykład, jeśli chcesz użyć ASP.NET Core (Linux lub `mcr.microsoft.com/dotnet/core/aspnet:3.1`Windows), obraz do użycia jest . W związku z tym wystarczy określić, jaki podstawowy obraz platformy Docker będzie używany dla kontenera. Można to zrobić, dodając `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` do pliku Dockerfile. To będzie wykonywane automatycznie przez program Visual Studio, ale jeśli chcesz zaktualizować wersję, należy zaktualizować tę wartość.

Przy użyciu oficjalnego repozytorium obrazów .NET z usługi Docker Hub z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym rozwoju, testowania i produkcji).

W poniższym przykładzie przedstawiono przykładowy plik Dockerfile dla kontenera ASP.NET Core.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

W tym przypadku obraz jest oparty na wersji 3.1 oficjalnego ASP.NET obrazu core docker (multi-arch dla Linuksa i Windows). Jest to `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`ustawienie . (Aby uzyskać więcej informacji na temat tego obrazu podstawowego, zobacz stronę [obrazu docker .NET).](https://hub.docker.com/_/microsoft-dotnet-core/) W pliku Dockerfile należy również poinstruować platformę Docker, aby nasłuchiwać na porcie TCP, którego będziesz używać w czasie wykonywania (w tym przypadku port 80, zgodnie z ustawieniem EXPOSE).

Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz. Na przykład wiersz ENTRYPOINT `["dotnet", "MySingleContainerWebApp.dll"]` z nakazem platformy Docker o uruchomieniu aplikacji .NET Core. Jeśli używasz sdk i .NET Core CLI (dotnet CLI) do tworzenia i uruchamiania aplikacji .NET, to ustawienie będzie inna. Najważniejsze jest to, że linia ENTRYPOINT i inne ustawienia będą się różnić w zależności od języka i platformy wybranej dla aplikacji.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Tworzenie obrazów platformy Docker dla aplikacji .NET Core** \
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- **Zbuduj swój własny obraz**. W oficjalnej dokumentacji platformy Docker.\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- **Aktualizowanie obrazów kontenerów .NET** \
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- **Korzystanie z platformy .NET i platformy Docker Razem — aktualizacja dockerCon 2018** \
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a>Korzystanie z repozytoriów obrazów wielołukowych

Pojedyncze reppo może zawierać warianty platformy, takie jak obraz systemu Linux i obraz systemu Windows. Ta funkcja umożliwia dostawcom takim jak Microsoft (twórcy obrazów bazowych) tworzenie jednego reponu na wiele platform (czyli Linux i Windows). Na przykład repozytorium [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) dostępne w rejestrze docker hub zapewnia obsługę systemów Linux i Windows Nano Server przy użyciu tej samej nazwy repozytorium.

Jeśli określisz tag, kierowanie na platformę, która jest jawna, jak w następujących przypadkach:

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  Obiekty docelowe: tylko w czasie wykonywania programu .NET Core 3.1 w systemie Linux

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  Obiekty docelowe: tylko środowisko uruchomieniowe programu .NET Core 3.1 w systemie Windows Nano Server

Jeśli jednak określisz tę samą nazwę obrazu, nawet w przypadku `aspnet` tego samego tagu, obrazy wielołukowe (takie jak obraz) będą używać wersji systemu Linux lub Windows w zależności od wdrażanego systemu operacyjnego hosta platformy Docker, jak pokazano w poniższym przykładzie:

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  Wielołukowy: tylko środowisko uruchomieniowe programu .NET Core 3.1 w systemie Linux lub Windows Nano Server w zależności od systemu operacyjnego hosta platformy Docker

W ten sposób, gdy wyciągniesz obraz z hosta systemu Windows, wyciągnie wariant systemu Windows, a pociągnięcie tej samej nazwy obrazu z hosta Linuksa pociągnie wariant Linuksa.

### <a name="multi-stage-builds-in-dockerfile"></a>Kompilacje wieloetapowe w pliku Dockerfile

Plik Dockerfile jest podobny do skryptu wsadowego. Podobnie jak w przypadku konieczności skonfigurowania komputera z wiersza polecenia.

Zaczyna się od obrazu podstawowego, który konfiguruje kontekst początkowy, to jak system plików startowych, który znajduje się na górze systemu operacyjnego hosta. To nie jest system operacyjny, ale można myśleć o tym jak "" OS wewnątrz pojemnika.

Wykonanie każdego wiersza polecenia tworzy nową warstwę w systemie plików ze zmianami z poprzedniego, tak, że po połączeniu, produkować wynikowy system plików.

Ponieważ każda nowa warstwa "opiera się" na poprzedniej, a wynikowy rozmiar obrazu zwiększa się z każdym poleceniem, obrazy mogą być bardzo duże, jeśli muszą zawierać, na przykład, zestaw SDK potrzebny do utworzenia i opublikowania aplikacji.

To jest, gdy wieloetapowe kompilacje dostać się do działki (z Docker 17.05 i wyższe), aby zrobić swoją magię.

Podstawową ideą jest to, że można oddzielić proces wykonywania dockerfile etapami, gdzie etap jest obrazem początkowym, po którym następuje jedno lub więcej poleceń, a ostatni etap określa ostateczny rozmiar obrazu.

Krótko mówiąc, kompilacje wieloetapowe umożliwiają dzielenie kreacji w różnych "fazach", a następnie montaż końcowego obrazu, biorąc tylko odpowiednie katalogi z etapów pośrednich. Ogólna strategia korzystania z tej funkcji jest:

1. Użyj podstawowego obrazu SDK (nie ma znaczenia, jak duży), ze wszystkim, co potrzebne do tworzenia i publikowania aplikacji w folderze, a następnie

2. Użyj obrazu podstawowego, małego, tylko do wykonywania i skopiuj folder publikowania z poprzedniego etapu, aby utworzyć mały obraz końcowy.

Prawdopodobnie najlepszym sposobem, aby zrozumieć wielostopniowy przechodzi przez Dockerfile w szczegółach, wiersz po wierszu, więc zacznijmy od początkowego Dockerfile utworzone przez program Visual Studio podczas dodawania obsługi platformy Docker do projektu i dostanie się do niektórych optymalizacji później.

Początkowy Plik Dockerfile może wyglądać mniej więcej tak:

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

I to są szczegóły, wiersz po wierszu:

- **#1 liniowy:** Rozpocznij etap z "małym" obrazem podstawowym tylko w czasie wykonywania, nazwij go **bazą** referencyjną.

- **#2 liniowy:** Utwórz katalog **/app** na obrazie.

- **#3 liniowy:** Udostępnij port **80**.

- **#5 liniowy:** Rozpocznij nowy etap z "dużym" obrazem do budowania/publikowania. Wywołaj **kompilację** w celach informacyjnych.

- **#6 liniowy:** Utwórz katalog **/src** na obrazie.

- **#7 liniowy:** Do linii 16, kopiuj odwołuje się do plików projektu **csproj,** aby móc przywrócić pakiety później.

- **#17 liniowy:** Przywracanie pakietów dla projektu **Catalog.API** i projektów, do których istnieje odwołanie.

- **#18 liniowy:** Skopiuj **całe drzewo katalogów dla rozwiązania** (z wyjątkiem plików/katalogów zawartych w pliku **.dockerignore)** do katalogu **/src** w obrazie.

- **#19 liniowy:** Zmień bieżący folder na projekt **Catalog.API.**

- **#20 liniowy:** Skompiluj projekt (i inne zależności projektu) i dane wyjściowe do katalogu **/app** na obrazie.

- **#22 liniowy:** Rozpocznij nowy etap kontynuując od kompilacji. Wywołaj **to opublikować** w celach informacyjnych.

- **#23 liniowy:** Opublikuj projekt (i zależności) i dane wyjściowe do katalogu **/app** na obrazie.

- **#25 linii:** Rozpocznij nowy etap kontynuując od **bazy** i nazwij go **ostatnim**.

- **#26 liniowy:** Zmień bieżący katalog na **/app**.

- **#27 liniowy:** Skopiuj katalog **/app** z etapu **publikowania** do bieżącego katalogu.

- **#28 liniowy:** Zdefiniuj polecenie do uruchomienia po uruchomieniu kontenera.

Teraz przeanalizujmy niektóre optymalizacje, aby poprawić wydajność całego procesu, który w przypadku eShopOnContainers oznacza około 22 minut lub więcej, aby utworzyć kompletne rozwiązanie w kontenerach systemu Linux.

Skorzystasz z funkcji pamięci podręcznej warstwy platformy Docker, co jest dość proste: jeśli obraz podstawowy i polecenia są takie same jak niektóre wcześniej wykonane, może po prostu użyć warstwy wynikowej bez konieczności wykonywania poleceń, oszczędzając w ten sposób trochę czasu.

Skupmy się więc na etapie **kompilacji,** linie 5-6 są w większości takie same, ale linie 7-17 są różne dla każdej usługi z eShopOnContainers, więc muszą wykonać za każdym razem, jednak jeśli zmieniłeś linie 7-16 na:

```Dockerfile
COPY . .
```

Wtedy byłoby tak samo dla każdej usługi, to skopiować całe rozwiązanie i stworzyłby większą warstwę, ale:

1. Proces kopiowania zostanie wykonany tylko po raz pierwszy (i podczas przebudowy, jeśli plik zostanie zmieniony) i będzie używać pamięci podręcznej dla wszystkich innych usług i

2. Ponieważ większy obraz występuje na etapie pośrednim, nie ma to wpływu na ostateczny rozmiar obrazu.

Następna optymalizacja `restore` znacząca obejmuje polecenie wykonywane w wierszu 17, który jest również inny dla każdej usługi eShopOnContainers. Jeśli zmienisz ten wiersz na sprawiedliwy:

```Dockerfile
RUN dotnet restore
```

Przywróciłby pakiety dla całego rozwiązania, ale potem znowu zrobiłby to tylko raz, zamiast 15 razy z obecną strategią.

Jednak `dotnet restore` uruchamia się tylko wtedy, gdy w folderze znajduje się jeden plik projektu lub rozwiązania, więc osiągnięcie tego jest nieco bardziej skomplikowane, a sposób jego rozwiązania, bez wchodzenia w zbyt wiele szczegółów, jest następujące:

1. Dodaj następujące wiersze do **.dockerignore:**

   - `*.sln`, aby zignorować wszystkie pliki rozwiązania w drzewie folderów głównych

   - `!eShopOnContainers-ServicesAndWebApps.sln`, aby uwzględnić tylko ten plik rozwiązania.

2. Dołącz `/ignoreprojectextensions:.dcproj` argument `dotnet restore`do , więc ignoruje również projekt docker-compose i przywraca tylko pakiety dla rozwiązania eShopOnContainers-ServicesAndWebApps.

Dla ostatecznej optymalizacji, to po prostu zdarza się, że linia 20 jest zbędne, jak linia 23 również buduje aplikację i przychodzi, w istocie, zaraz po wierszu 20, więc nie idzie kolejne czasochłonne polecenie.

Wynikowym plikiem jest wtedy:

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
10  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a>Tworzenie obrazu bazowego od podstaw

Można utworzyć własny obraz podstawowy platformy Docker od podstaw. Ten scenariusz nie jest zalecany dla osoby, która zaczyna się od platformy Docker, ale jeśli chcesz ustawić określone bity własnego obrazu podstawowego, możesz to zrobić.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Wielołukowe obrazy .NET Core**.\
  <https://github.com/dotnet/announcements/issues/14>

- **Utwórz obraz podstawowy**. Oficjalna dokumentacja platformy Docker.\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Obraz dla kroku 3.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Tworzenie niestandardowych obrazów platformy Docker i osadzanie w nich aplikacji lub usługi

Dla każdej usługi w aplikacji należy utworzyć powiązany obraz. Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, wystarczy jeden obraz.

Należy zauważyć, że obrazy platformy Docker są tworzone automatycznie dla Ciebie w programie Visual Studio. Poniższe kroki są potrzebne tylko dla przepływu pracy edytora/interfejsu i wyjaśnione dla jasności co do tego, co dzieje się pod spodem.

Jako deweloper musisz opracowywać i testować lokalnie, dopóki nie wypchniesz ukończonej funkcji lub nie zmienisz systemu kontroli źródła (na przykład na GitHub). Oznacza to, że należy utworzyć obrazy platformy Docker i wdrożyć kontenery na lokalnym hoście platformy Docker (Windows lub Linux VM) i uruchomić, przetestować i debugować względem tych kontenerów lokalnych.

Aby utworzyć obraz niestandardowy w środowisku lokalnym przy użyciu polecenia docker CLI i pliku Dockerfile, można użyć polecenia kompilacji platformy docker, jak na rysunku 5-5.

![Zrzut ekranu przedstawiający dane wyjściowe konsoli polecenia kompilacji platformy docker.](./media/docker-app-development-workflow/run-docker-build-command.png)

**Rysunek 5-5**. Tworzenie niestandardowego obrazu platformy Docker

Opcjonalnie zamiast bezpośrednio uruchamiać kompilację docker z folderu projektu, można najpierw wygenerować folder z możliwością wdrożenia z wymaganymi bibliotekami i plikami binarnymi .NET, uruchamiając , `dotnet publish`a następnie użyć `docker build` polecenia.

Spowoduje to utworzenie obrazu platformy `cesardl/netcore-webapi-microservice-docker:first`Docker o nazwie . W takim przypadku :first jest tagreprezentujący określoną wersję. Ten krok można powtórzyć dla każdego niestandardowego obrazu, który należy utworzyć dla skomponowanej aplikacji platformy Docker.

Gdy aplikacja jest wykonana z wielu kontenerów (oznacza to, że jest `docker-compose up --build` aplikacją wielokontenerową), można również użyć polecenia do tworzenia wszystkich powiązanych obrazów za pomocą jednego polecenia przy użyciu metadanych uwidacznianych w powiązanych plikach docker-compose.yml.

Istniejące obrazy można znaleźć w lokalnym repozytorium za pomocą polecenia obrazy dokowane, jak pokazano na rysunku 5-6.

![Wyjście konsoli z obrazów dokatki poleceń, pokazujące istniejące obrazy.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

**Rysunek 5-6.** Wyświetlanie istniejących obrazów za pomocą polecenia Obrazy dokowane

### <a name="creating-docker-images-with-visual-studio"></a>Tworzenie obrazów platformy Docker za pomocą programu Visual Studio

Korzystając z programu Visual Studio do tworzenia projektu z obsługą platformy Docker, nie jawnie utworzyć obraz. Zamiast tego obraz jest tworzony po naciśnięciu **klawisza F5** (lub **Ctrl-F5),** aby uruchomić dockerized aplikacji lub usługi. Ten krok jest automatyczny w programie Visual Studio i nie zobaczysz, że tak się stanie, ale ważne jest, aby wiedzieć, co się dzieje pod spodem.

![Obraz dla opcjonalnego kroku 4.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Definiowanie usług w pliku docker-compose.yml podczas tworzenia aplikacji platformy Docker dla wielu kontenerów

Plik [docker-compose.yml](https://docs.docker.com/compose/compose-file/) umożliwia zdefiniowanie zestawu powiązanych usług, które mają zostać wdrożone jako skomponowana aplikacja z poleceniami wdrażania. Konfiguruje również relacje zależności i konfigurację w czasie wykonywania.

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

Ten plik docker-compose.yml jest wersją uproszczoną i scaloną. Zawiera statyczne dane konfiguracyjne dla każdego kontenera (takie jak nazwa obrazu niestandardowego), który jest zawsze wymagany, oraz informacje o konfiguracji, które mogą zależeć od środowiska wdrażania, takie jak parametry połączenia. W kolejnych sekcjach dowiesz się, jak podzielić konfigurację docker-compose.yml na wiele plików docker-compose i zastąpić wartości w zależności od środowiska i typu wykonywania (debugowania lub wydania).

Przykład pliku docker-compose.yml definiuje cztery `webmvc` usługi: usługę (aplikację sieci`ordering-api` web), dwie mikrousługi ( i `basket-api`) i jeden kontener źródła danych, `sqldata`oparty na programie SQL Server dla systemu Linux uruchomionym jako kontener. Każda usługa zostanie wdrożona jako kontener, więc obraz platformy Docker jest wymagany dla każdego.

Plik docker-compose.yml określa nie tylko, jakie kontenery są używane, ale sposób ich indywidualnej konfiguracji. Na przykład `webmvc` definicja kontenera w pliku yml:

- Używa wstępnie utworzonego `eshop/web:latest` obrazu. Można jednak również skonfigurować obraz, który ma być zbudowany jako część wykonywania docker-compose z dodatkową konfiguracją opartą na kompilacji: sekcja w pliku docker-compose.

- Inicjuje dwie zmienne środowiskowe (CatalogUrl i OrderingUrl).

- Przesyła dalej odsłonięty port 80 na kontenerze do portu zewnętrznego 80 na komputerze hosta.

- Łączy aplikację internetową z usługą katalogową i zamawiania z ustawieniem depends_on. Powoduje to, że usługa czekać, aż te usługi są uruchamiane.

Będziemy ponownie plik docker-compose.yml w dalszej sekcji, gdy omówimy sposób implementowania mikrousług i aplikacji wielokontenerowych.

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a>Praca z docker-compose.yml w programie Visual Studio 2019

Oprócz dodawania pliku Dockerfile do projektu, jak wspomnieliśmy wcześniej, Visual Studio 2017 (od wersji 15.8 na) można dodać obsługę koordynatora docker Compose do rozwiązania.

Po dodaniu obsługi koordynatora kontenerów, jak pokazano na rysunku 5-7, po raz pierwszy program Visual Studio tworzy plik Dockerfile `docker-compose*.yml` dla projektu i tworzy nowy (sekcja usługi) projektu w rozwiązaniu z kilku plików globalnych, a następnie dodaje projekt do tych plików. Następnie można otworzyć pliki docker-compose.yml i zaktualizować je za pomocą dodatkowych funkcji.

Musisz powtórzyć ten formularz operacji każdego projektu, który chcesz uwzględnić w pliku docker-compose.yml.

W czasie tego pisania visual studio obsługuje **Docker Compose** i **Kubernetes/Helm** koordynatorów.

![Zrzut ekranu przedstawiający opcję Obsługa koordynatora kontenerów w menu kontekstowym projektu.](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

**Rysunek 5-7**. Dodawanie obsługi platformy Docker w programie Visual Studio 2019 przez kliknięcie prawym przyciskiem myszy projektu ASP.NET Core

Po dodaniu obsługi koordynatora do rozwiązania w programie Visual Studio zostanie wyświetlony `docker-compose.dcproj` nowy węzeł (w pliku projektu) w Eksploratorze rozwiązań zawierający dodane pliki docker-compose.yml, jak pokazano na rysunku 5-8.

![Zrzut ekranu przedstawiający węzeł docker-compose w Eksploratorze rozwiązań.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

**Rysunek 5-8**. Węzeł drzewa **docker-compose** dodany w Eksploratorze rozwiązań programu Visual Studio 2019

Można wdrożyć aplikację wielokontenerową z pojedynczym plikiem docker-compose.yml za pomocą `docker-compose up` polecenia. Program Visual Studio dodaje jednak grupę z nich, dzięki czemu można zastąpić wartości w zależności od środowiska (rozwoju lub produkcji) i typu wykonywania (wydania lub debugowania). Ta funkcja zostanie wyjaśniona w kolejnych sekcjach.

![Obraz dla kroku 5.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Tworzenie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, można go uruchomić, wdrażając go na hoście platformy Docker (maszyna wirtualna lub serwer fizyczny). Jeśli jednak aplikacja zawiera wiele usług, można ją wdrożyć jako złożoną aplikację, używając jednego polecenia wiersza polecenia (lub`docker-compose up)`programu Visual Studio, które użyje tego polecenia pod osłonami. Spójrzmy na różne opcje.

### <a name="option-a-running-a-single-container-application"></a>Opcja A: Uruchamianie aplikacji z jednym kontenerem

#### <a name="using-docker-cli"></a>Korzystanie z funkcji CLI platformy Docker

Kontener platformy Docker można `docker run` uruchomić za pomocą polecenia, jak pokazano na rysunku 5-9:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Powyższe polecenie utworzy nowe wystąpienie kontenera z określonego obrazu, za każdym razem, gdy jest uruchamiany. Parametr służy `--name` do nadania nazwy kontenerowi, `docker start {name}` a następnie użyć (lub użyć identyfikatora kontenera lub nazwy automatycznej) do uruchomienia istniejącego wystąpienia kontenera.

![Zrzut ekranu przedstawiający kontener platformy Docker przy użyciu polecenia docker run.](./media/docker-app-development-workflow/use-docker-run-command.png)

**Rysunek 5-9**. Uruchamianie kontenera platformy Docker przy użyciu polecenia uruchamiania platformy dokowane

W takim przypadku polecenie wiąże port wewnętrzny 5000 kontenera do portu 80 komputera hosta. Oznacza to, że host nasłuchuje na porcie 80 i przekazuje do portu 5000 w kontenerze.

Wyświetlany skrót jest identyfikatorem kontenera i jest również przypisany losową czytelną nazwę, `--name` jeśli opcja nie jest używana.

#### <a name="using-visual-studio"></a>Korzystanie z programu Visual Studio

Jeśli nie dodano obsługę koordynatora kontenerów, można również uruchomić aplikację pojedynczego kontenera w programie Visual Studio, naciskając **klawisze Ctrl-F5** i można również użyć **f5** do debugowania aplikacji w kontenerze. Kontener jest uruchamiany lokalnie przy użyciu platformy docker run.

### <a name="option-b-running-a-multi-container-application"></a>Opcja B: Uruchamianie aplikacji wielokontenerowej

W większości scenariuszy przedsiębiorstwa aplikacja platformy Docker będzie składać się z wielu usług, co oznacza, że należy uruchomić aplikację wielokontenerową, jak pokazano na rysunku 5-10.

![Maszyna wirtualna z kilkoma kontenerami platformy Docker](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

**Rysunek 5-10**. Maszyna wirtualna z wdrożonymi kontenerami platformy Docker

#### <a name="using-docker-cli"></a>Korzystanie z funkcji CLI platformy Docker

Aby uruchomić aplikację wielokontenerową za pomocą polecenia CLI platformy Docker, należy użyć tego `docker-compose up` polecenia. To polecenie używa pliku **docker-compose.yml,** który masz na poziomie rozwiązania do wdrażania aplikacji wielokontenerowej. Rysunek 5-11 przedstawia wyniki po uruchomieniu polecenia z katalogu głównego rozwiązania, który zawiera plik docker-compose.yml.

![Widok ekranu podczas uruchamiania polecenia docker-compose up](./media/docker-app-development-workflow/results-docker-compose-up.png)

**Rysunek 5-11**. Przykładowe wyniki podczas uruchamiania polecenia docker-compose up

Po uruchomieniu polecenia docker-compose się, aplikacja i powiązane kontenery są wdrażane na hoście platformy Docker, jak przedstawiono na rysunku 5-10.

#### <a name="using-visual-studio"></a>Korzystanie z programu Visual Studio

Uruchomienie aplikacji wielokontenerowej przy użyciu programu Visual Studio 2019 nie może uzyskać żadnych prostsze. Wystarczy nacisnąć **klawiszctrl-F5,** aby uruchomić lub **F5** do debugowania, jak zwykle, konfigurowanie projektu **docker-compose** jako projekt uruchamiania.  Visual Studio obsługuje wszystkie potrzebne ustawienia, dzięki czemu można tworzyć punkty przerwania, jak zwykle i debugować, co w końcu stają się niezależne procesy uruchomione w "serwery zdalne", z debugera już dołączone. właśnie w ten sposób.

Jak wspomniano wcześniej, za każdym razem, gdy dodajesz obsługę rozwiązania platformy Docker do projektu w ramach rozwiązania, ten projekt jest skonfigurowany w pliku docker-compose.yml na poziomie globalnym (na poziomie rozwiązania), który umożliwia jednoczesne uruchamianie lub debugowanie całego rozwiązania. Program Visual Studio uruchomi jeden kontener dla każdego projektu, który ma włączoną obsługę rozwiązania platformy Docker i wykonaj wszystkie wewnętrzne kroki (dotnet publish, docker build itp.).

Jeśli chcesz rzucić okiem na wszystkie znoju, spojrzeć na plik:

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Ważną kwestią jest to, że, jak pokazano na rysunku 5-12, w programie Visual Studio 2019 istnieje dodatkowe polecenie **platformy Docker** dla akcji klawisza F5. Ta opcja umożliwia uruchamianie lub debugowanie aplikacji wielokontenerowej przez uruchomienie wszystkich kontenerów zdefiniowanych w plikach docker-compose.yml na poziomie rozwiązania. Możliwość debugowania rozwiązań z wieloma kontenerami oznacza, że można ustawić kilka punktów przerwania, każdy punkt przerwania w innym projekcie (kontenerze), a podczas debugowania z programu Visual Studio zatrzymasz się w punktach przerwania zdefiniowanych w różnych projektach i uruchomionyna różnych pojemników.

![Zrzut ekranu przedstawiający pasek narzędzi debugowania z projektem docker-compose.](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

**Rysunek 5-12**. Uruchamianie aplikacji wielokontenerowych w programie Visual Studio 2019

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Wdrażanie kontenera ASP.NET na zdalnym hoście platformy Docker** \
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Uwaga dotycząca testowania i wdrażania z koordynatorami

Polecenia docker-compose up i docker run (lub uruchamianie i debugowanie kontenerów w programie Visual Studio) są odpowiednie do testowania kontenerów w środowisku programistycznym. Nie należy jednak używać tego podejścia do wdrożeń produkcyjnych, gdzie należy kierować koordynatorów, takich jak [Kubernetes](https://kubernetes.io/) lub [sieci szkieletowej usług](https://azure.microsoft.com/services/service-fabric/). Jeśli używasz Kubernetes, musisz użyć [zasobników](https://kubernetes.io/docs/concepts/workloads/pods/pod/) do organizowania kontenerów i [usług](https://kubernetes.io/docs/concepts/services-networking/service/) do ich sieci. [Wdrożenia](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) można również użyć do organizowania tworzenia zasobników i modyfikacji.

![Obraz dla kroku 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Testowanie aplikacji platformy Docker przy użyciu lokalnego hosta platformy Docker

Ten krok będzie się różnić w zależności od tego, co aplikacja robi. W prostej aplikacji sieci Web .NET Core, która jest wdrażana jako pojedynczy kontener lub usługa, można uzyskać dostęp do usługi, otwierając przeglądarkę na hoście platformy Docker i przechodząc do tej witryny, jak pokazano na rysunku 5-13. (Jeśli konfiguracja w pliku Dockerfile mapuje kontener na port na hoście, który jest inny niż 80, dołącz port hosta w adresie URL).

![Zrzut ekranu przedstawiający odpowiedź z localhost/API/values.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

**Rysunek 5-13**. Przykład testowania aplikacji platformy Docker lokalnie przy użyciu localhost

Jeśli host lokalny nie wskazuje adresu IP hosta platformy Docker (domyślnie podczas korzystania z platformy Docker CE), aby przejść do usługi, użyj adresu IP karty sieciowej komputera.

Należy zauważyć, że ten adres URL w przeglądarce używa portu 80 dla danego przykładu kontenera, o których mówi się. Jednak wewnętrznie żądania są przekierowywane do portu 5000, ponieważ w ten sposób został wdrożony za pomocą polecenia docker run, jak wyjaśniono w poprzednim kroku.

Można również przetestować aplikację za pomocą curl z zacisku, jak pokazano na rysunku 5-14. W instalacji platformy Docker w systemie Windows domyślny adres IP hosta platformy Docker jest zawsze 10.0.75.1 oprócz rzeczywistego adresu IP komputera.

![Wyjście konsoli z http://10.0.75.1/API/values coraz z curl.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

**Rysunek 5-14**. Przykład testowania aplikacji Platformy Docker lokalnie za pomocą curl

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a>Testowanie i debugowanie kontenerów w programie Visual Studio 2019

Podczas uruchamiania i debugowania kontenerów za pomocą programu Visual Studio 2019 można debugować aplikację .NET w taki sam sposób, jak podczas uruchamiania bez kontenerów.

### <a name="testing-and-debugging-without-visual-studio"></a>Testowanie i debugowanie bez programu Visual Studio

Jeśli tworzysz przy użyciu podejścia editor/CLI, debugowanie kontenerów jest trudniejsze i prawdopodobnie będziesz chciał debugować, generując ślady.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Debugowanie aplikacji w lokalnym kontenerze platformy Docker** \
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- **Steve Lasker. Tworzenie, debugowanie, wdrażanie ASP.NET podstawowych aplikacji za pomocą platformy Docker.** Wideo. \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Uproszczony przepływ pracy podczas opracowywania kontenerów za pomocą programu Visual Studio

Skutecznie przepływu pracy podczas korzystania z programu Visual Studio jest o wiele prostsze niż w przypadku korzystania z podejścia edytora/interfejsu i biorącego pod niego. Większość kroków wymaganych przez platformę Docker związane z plikidockerfile i docker-compose.yml są ukryte lub uproszczone przez Visual Studio, jak pokazano na rysunku 5-15.

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram przedstawiający pięć uproszczonych kroków potrzebnych do utworzenia aplikacji.":::
Proces tworzenia aplikacji platformy Docker: 1 - Kod aplikacji, 2 - Pisanie dockerfile/s, 3 - Tworzenie obrazów zdefiniowanych w dockerfile/s, 4 - (opcjonalnie) Compose usługi w pliku docker-compose.yml, 5 - Uruchom kontener lub docker-compose aplikacji, 6 - Testowanie aplikacji lub mikrousług, 7 - Push to repo i powtórz.
:::image-end:::

**Rysunek 5-15**. Uproszczony przepływ pracy podczas tworzenia za pomocą programu Visual Studio

Ponadto należy wykonać krok 2 (dodawanie obsługi platformy Docker do projektów) tylko raz. W związku z tym przepływ pracy jest podobny do zwykłych zadań programistycznych podczas korzystania z .NET dla innych deweloperów. Musisz wiedzieć, co dzieje się pod okładkami (proces kompilacji obrazu, jakie obrazy podstawowe używasz, wdrażanie kontenerów, itp.), a czasami trzeba będzie również edytować Plik Dockerfile lub docker-compose.yml, aby dostosować zachowania. Jednak większość pracy jest znacznie uproszczona za pomocą programu Visual Studio, dzięki czemu można o wiele bardziej produktywne.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Steve Lasker. Program .NET Docker Development z visual studio (2017)** \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Konfigurowanie kontenerów systemu Windows za pomocą poleceń programu PowerShell w pliku Dockerfile

[Kontenery systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umożliwiają konwertowanie istniejących aplikacji systemu Windows na obrazy platformy Docker i wdrażanie ich przy tym i w tych samych narzędziach, co pozostałe urządzenia do każdowe. Aby korzystać z kontenerów systemu Windows, w pliku Dockerfile są uruchamiane polecenia programu PowerShell, jak pokazano w poniższym przykładzie:

```Dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

W takim przypadku używamy obrazu podstawowego windows server core (ustawienia FROM) i instalowania usług IIS za pomocą polecenia PowerShell (ustawienie RUN). W podobny sposób można również użyć poleceń programu PowerShell do skonfigurowania dodatkowych składników, takich jak ASP.NET 4.x, .NET 4.6 lub innego oprogramowania windows. Na przykład następujące polecenie w pliku Dockerfile konfiguruje ASP.NET 4.5:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Zasoby dodatkowe

- **aspnet-docker/Dockerfile.** Przykładowe polecenia programu PowerShell do uruchamiania z plików dokparatorów w celu uwzględnienia funkcji systemu Windows.\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](../multi-container-microservice-net-applications/index.md)
