---
title: Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker
description: Poznaj szczegóły przepływu pracy do tworzenia aplikacji opartych na platformie Docker. Rozpocznij krok po kroku i Uzyskaj do niektórych szczegółów, aby zoptymalizować pliki Dockerfile oraz kończyć się znakiem uproszczonego przepływu pracy dostępna przy użyciu programu Visual Studio.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 3fb5c06f8ed58b45a3ee669931d8c3118b3dc314
ms.sourcegitcommit: 8080271c246b57f4fb68c28369634bff46843424
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2019
ms.locfileid: "59553878"
---
# <a name="development-workflow-for-docker-apps"></a>Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker

Cyklu tworzenia aplikacji rozpoczyna się na komputerze, jako programista, gdy kod aplikacji przy użyciu preferowanego języka i przetestować go lokalnie. W tym przepływie pracy, niezależnie od tego, które języków i platformy możesz są zawsze opracowywania i testowania kontenerów platformy Docker, ale sposób lokalnie.

Każdy kontener (wystąpienia obrazu platformy Docker) obejmuje następujące składniki:

- Opcji wyboru systemu operacyjnego, na przykład Linux dystrybucji Windows Nano Server i Windows Server Core.

- Pliki dodane podczas tworzenia aplikacji, na przykład źródła danych binarnych kodu i aplikacji.

- Informacje o konfiguracji, takie jak ustawienia środowiska i zależności.

## <a name="workflow-for-developing-docker-container-based-applications"></a>Przepływ pracy na potrzeby tworzenia aplikacji opartych na kontenerach platformy Docker

W tej sekcji opisano *pętli wewnętrzny* przepływ pracy tworzenia oprogramowania dla aplikacji opartych na kontenerach platformy Docker. Przepływ pracy wewnętrznej pętli oznacza, że nie rozważa szersze DevOps przepływu pracy, który może zawierać maksymalnie wdrożenia produkcyjnego, a po prostu koncentruje się na rozwoju pracy na komputerze dewelopera. Początkowe kroki konfigurowania środowiska nie są uwzględnione, ponieważ te kroki są wykonywane tylko raz.

Aplikacja składa się z własnych usług, a także dodatkowe biblioteki (zależności). Poniżej przedstawiono podstawowe kroki, które zwykle wykonać podczas kompilowania aplikacji platformy Docker, jak pokazano w rysunek 5-1.

![Proces programowania dla aplikacji platformy Docker: 1 - kodu aplikacji, 2 - zapisu pliku Dockerfile/s, 3 — Tworzenie obrazów zdefiniowanych w pliku Dockerfile/s, 4 - (opcjonalnie) usług Compose w pliku docker-compose.yml, 5, - uruchomienia kontenera lub docker-compose aplikacji, 6 - testów aplikacji sieci Web lub mikrousług, 7 - wypychania do repozytorium i powtórz tę czynność. ](./media/image1.png)

**Rysunek 5-1.** Instrukcje krok po kroku przepływu pracy do tworzenia aplikacji kontenerowych nimi platformy Docker

W tej sekcji opisano szczegółowo całego tego procesu i na każdym kroku głównych zostało wyjaśnione, skupiając się na środowisko Visual Studio.

Podczas korzystania z podejście do tworzenia edytora/CLI (na przykład programu Visual Studio Code oraz interfejsu wiersza polecenia platformy Docker w systemie macOS lub Windows), musisz wiedzieć każdego kroku, zazwyczaj bardziej szczegółowo niż w przypadku korzystania z programu Visual Studio. Aby uzyskać więcej informacji na temat pracy w środowisku interfejsu wiersza polecenia, zobacz książki elektronicznej [cykl życia aplikacji kontenerowych nimi platformy Docker z Platforms i narzędzi Microsoft](https://aka.ms/dockerlifecycleebook/).

Podczas korzystania z programu Visual Studio 2017, wiele z tych kroków są obsługiwane dla Ciebie, co znacznie zwiększa wydajność pracy. Jest to szczególnie istotne, przy użyciu programu Visual Studio 2017 i przeznaczone dla aplikacji obsługującej wiele kontenerów. Na przykład tylko jednym kliknięciem, Visual Studio dodaje plik Dockerfile i docker-compose.yml do swoich projektów za pomocą konfiguracji dla aplikacji. Po uruchomieniu aplikacji w programie Visual Studio tworzy obraz platformy Docker i uruchamia aplikację obsługującą wiele kontenerów bezpośrednio na platformie Docker; Umożliwia ona nawet jednocześnie debugowanie kilka kontenerów. Te funkcje będą zwiększyć szybkość rozwoju.

Po prostu, ponieważ program Visual Studio sprawia, że te kroki są automatyczne nie oznacza to jednak, że nie musisz wiedzieć, co się dzieje na dole z platformą Docker. W związku z tym korzystając ze wskazówek szczegóły każdego kroku.

![1 — kodu aplikacji](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Rozpocznij kodowanie i tworzenie początkowej aplikacja lub usługa linii bazowej

Tworzenie aplikacji platformy Docker to podobnie, jak opracować aplikację bez platformy Docker. Różnica jest, że podczas tworzenia dla platformy Docker, możesz teraz wdrażanie i testowanie aplikacji lub usług działających w kontenerach platformy Docker w środowisku lokalnym, albo (konfiguracja maszyny Wirtualnej systemu Linux przez platformę Docker), albo Windows bezpośrednio, jeśli przy użyciu kontenerów Windows.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Konfigurowanie środowiska lokalnego z programem Visual Studio

Aby rozpocząć, upewnij się, że masz [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) dla Windows zainstalowany zgodnie z opisem w poniższych instrukcjach:

[Wprowadzenie do platformy Docker CE dla Windows](https://docs.docker.com/docker-for-windows/)

Ponadto konieczne Visual Studio 2017 w wersji 15.7 lub nowszej z **programowanie dla wielu platform .NET Core** obciążenia zainstalowany, jak pokazano w rysunek 5-2.

![.NET core wieloplatformowego opracowywania aplikacji obciążenia wybór podczas instalacji programu Visual Studio.](./media/image3.png)

**Rysunek 5-2**. Wybieranie **programowanie dla wielu platform .NET Core** obciążenie podczas instalacji programu Visual Studio 2017

Możesz rozpocząć kodowanie swoją aplikację w zwykły .NET (zwykle w .NET Core, jeśli planowane jest korzystanie z kontenerów), nawet przed włączeniem platformy Docker w aplikacji i wdrażanie i testowanie na platformie Docker. Jednak zaleca się uruchamiania nad platformy Docker tak szybko, jak to możliwe, ponieważ się rzeczywistego środowiska i wszelkie problemy, które mogą być wykrywane tak szybko, jak to możliwe. To zaleca się, ponieważ dzięki programowi Visual Studio tak łatwe do pracy z rozwiązaniem Docker, że niemal pozornie przezroczyste — najlepszy przykład podczas debugowania aplikacji obsługującej wiele kontenerów za pomocą programu Visual Studio.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Wprowadzenie do platformy Docker CE dla Windows** \
  [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)

- **Visual Studio 2017** \
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![2 — pisanie plików Dockerfile](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Tworzenie pliku Dockerfile związane z istniejącego obrazu podstawowego platformy .NET

Potrzebujesz pliku Dockerfile dla niestandardowego obrazu, z którą chcesz skompilować; należy również plik Dockerfile dla każdego kontenera do wdrożenia, czy wdrożyć automatycznie z programu Visual Studio lub ręcznie przy użyciu interfejsu wiersza polecenia platformy Docker (docker, uruchom i docker-compose poleceń). Jeśli aplikacja zawiera pojedynczą usługę niestandardowych, konieczne będzie pojedynczego pliku Dockerfile. Jeśli aplikacja zawiera wiele usług (tak jak w architekturze mikrousług), należy jeden plik Dockerfile dla każdej usługi.

Plik Dockerfile znajduje się w folderze głównym aplikacji lub usługi. Zawiera polecenia, określające sposób konfigurowania i uruchamiania aplikacji lub usługi w kontenerze platformy Docker. Można ręcznie utworzyć plik Dockerfile w kodzie i dodać go do projektu, wraz z zależności .NET.

Korzystając z programu Visual Studio i jego narzędzi platformy Docker to zadanie wymaga tylko kilku kliknięć myszą. Po utworzeniu nowego projektu w programie Visual Studio 2017 jest dostępna opcja o nazwie **Obsługa Włączanie kontenerów (Docker)**, jak pokazano w rysunek 5-3.

![Włącz obsługę platformy Docker wyboru podczas tworzenia nowego projektu ASP.NET Core w programie Visual Studio 2017](./media/image5.png)

**Rysunek 5-3**. Włączanie obsługi platformy Docker, podczas tworzenia nowego projektu ASP.NET Core w programie Visual Studio 2017

Można również włączyć obsługę platformy Docker w istniejącym projekcie aplikacji sieci web platformy ASP.NET Core, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **Dodaj** > **obsługę platformy Docker** , jak pokazano na rysunku 5-4.

![Dodaj opcję menu pomocy technicznej platformy Docker w programie Visual Studio](./media/image6.png)

**Rysunek 5-4**. Włączanie obsługi platformy Docker w istniejącym projekcie programu Visual Studio 2017

Ta akcja spowoduje dodanie *pliku Dockerfile* do projektu za pomocą wymaganej konfiguracji i jest dostępna tylko w projektach programu ASP.NET Core.

W podobny sposób, program Visual Studio można również dodać plik docker-compose.yml dla całego rozwiązania z opcją **Dodaj > Obsługa Orkiestratora kontenerów**. W kroku 4 przedstawimy zagadnienia związane z tej opcji bardziej szczegółowo.

### <a name="using-an-existing-official-net-docker-image"></a>Przy użyciu istniejących oficjalnego obrazu Docker w programie .NET

Zazwyczaj Tworzenie niestandardowego obrazu kontenera na podstawie obrazu podstawowego, otrzymasz od oficjalnego repozytorium, takiego jak [usługi Docker Hub](https://hub.docker.com/) rejestru. To jest dokładnie co się dzieje w tle po włączeniu obsługi platformy Docker w programie Visual Studio. Z pliku Dockerfile użyje istniejącej `aspnetcore` obrazu.

Wcześniej opisano firma Microsoft, które obrazów platformy Docker i repozytoriów, można użyć w zależności od framework i systemu operacyjnego zostały wybrane. Na przykład, jeśli chcesz użyć programu ASP.NET Core (Linux lub Windows), jest obrazu do użycia `mcr.microsoft.com/dotnet/core/aspnet:2.2`. W związku z tym wystarczy określić, jakie podstawowego obrazu platformy Docker, który będzie używany dla kontenera. Można to zrobić, dodając `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` do Twojego pliku Dockerfile. To zostanie przeprowadzona przez program Visual Studio, ale w przypadku zaktualizowania wersji zaktualizuj tę wartość.

Oficjalna repozytorium obrazów platformy .NET z usługi Docker Hub przy użyciu numeru wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowanie, testowanie i produkcja).

Poniższy kod przedstawia przykładowy plik Dockerfile dla kontenera platformy ASP.NET Core.

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

W tym przypadku obraz, który zależy od wersji 2.2 oficjalny obraz platformy Docker programu ASP.NET Core (wielu arch dla systemów Linux i Windows). Jest to ustawienie `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`. (Aby uzyskać więcej informacji na temat tego obrazu podstawowego zobacz [obrazu platformy Docker programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) strony.) W pliku Dockerfile trzeba będzie również poinstruować platformy Docker do nasłuchiwania na porcie TCP, używane w czasie wykonywania (w tym przypadku port 80, zgodnie z konfiguracją z ustawieniem UDOSTĘPNIAJĄ).

Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz. Na przykład wiersz punktu wejścia z `["dotnet", "MySingleContainerWebApp.dll"]` platformy docker, aby uruchomić aplikację .NET Core. Jeśli używasz zestawu SDK i .NET Core interfejsu wiersza polecenia (interfejsu wiersza polecenia platformy dotnet) aby skompilować i uruchomić aplikację .NET, to ustawienie będzie inny. Mierzenie to, że wiersz punktu wejścia i inne ustawienia będą różnić w zależności od języka i platformy, wybrany dla aplikacji.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Tworzenie obrazów platformy Docker dla aplikacji .NET Core** \
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- **Tworzenie własnego obrazu**. W oficjalnej dokumentacji platformy Docker. \
  [https://docs.docker.com/engine/tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)

- **Uzyskuje obrazów kontenerów platformy .NET** \
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- **Przy użyciu platformy .NET i Docker wspólnie - DockerCon 2018 Update** \
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a>Przy użyciu repozytoriów wielu architektury obrazu

Jednym repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows obraz. Ta funkcja umożliwia dostawców, takich jak Microsoft (obraz podstawowy dla twórców) do utworzenia pojedynczego repozytorium na pokrycie wiele platform (dotyczy to systemów Linux i Windows). Na przykład [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repozytorium, które są dostępne w rejestrze usługi Docker Hub zapewnia obsługę dla systemów Linux i Windows Nano Server przy użyciu tej samej nazwy repozytorium.

Jeśli określony tag, przeznaczonych dla platformy, która jest jawne, takich jak w następujących przypadkach:

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  Cele: .NET Core 2.2 tylko do środowiska uruchomieniowego w systemie Linux

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  Cele: .NET Core 2.2 tylko do środowiska uruchomieniowego na serwerze Windows Nano Server

Jednak jeśli określisz taką samą nazwę obrazu, nawet w przypadku tego samego tagu wielu architektury obrazów (takich jak `aspnetcore` obrazu) będą używać systemu Linux lub Windows wersji w zależności od systemu operacyjnego hosta platformy Docker jest wdrażany, jak pokazano w poniższym przykładzie:

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  Wiele arch: .NET Core 2.2 w czasie wykonywania tylko w systemie Linux lub Windows Nano Server w zależności od systemu operacyjnego hosta platformy Docker

Dzięki temu podczas ściągnąć obraz z hosta Windows go każda będzie ściągać wariant Windows i ściągania taką samą nazwę obrazu na hoście z systemem Linux każda będzie ściągać wariantów systemu Linux.

### <a name="multi-stage-builds-in-dockerfile"></a>Wieloetapowe kompilacje w pliku Dockerfile

Plik Dockerfile jest podobny do skryptu wsadowego. Podobnie jak co możesz zrobić, jeśli trzeba było skonfigurować na maszynie z poziomu wiersza polecenia.

Zaczyna się od obraz podstawowy, który konfiguruje początkowe kontekstu, takich jak system plików uruchamiania, który znajduje się na podstawie systemu operacyjnego hosta. Nie jest system operacyjny, ale można traktować jeśli np. "" system operacyjny w kontenerze.

Wykonanie każdego wiersza polecenia tworzy nową warstwę w systemie plików z uwzględnieniem zmian od poprzedniej wersji, tak aby w połączeniu, generuje wynikowy systemu plików.

Ponieważ każdy nową warstwę "opiera się" na podstawie poprzedniego i wynikowy rozmiar obrazu zwiększa się wraz z każdego polecenia, obrazy mogą uzyskać bardzo duże, jeśli mają obejmować, na przykład zestaw SDK potrzebne do tworzenia i publikowania aplikacji.

Jest to, gdzie uzyskać wieloetapowych kompilacji do kreślenia (z 17.05 platformy Docker i nowszych) w ich magic.

Podstawowe chodzi o to możliwość oddzielenia proces wykonywania pliku Dockerfile w etapach, gdzie etap jest obrazem początkowej następuje co najmniej jedno polecenie, a ostatni etap Określa rozmiar obrazu końcowego.

Krótko mówiąc kompilacje wieloetapowych Zezwalaj na tworzenie różnych "etapach" Dzielenie i zmontować finalnego obrazu przełączania tylko odpowiednich katalogów z etapów pośrednich. Jest ogólną strategią, aby użyć tej funkcji:

1. Za pomocą podstawowego obrazu zestawu SDK (nie ma znaczenia, jak duże), ze wszystkim, co jest potrzebne do tworzenia i publikowania aplikacji do folderu i następnie

2. Korzystanie z obrazu podstawowego, małe, tylko do środowiska uruchomieniowego i skopiowanie folderu publikowania z poprzedniego etapu, aby wygenerować mały obraz końcowego.

Prawdopodobnie najlepszym sposobem, aby dowiedzieć się, że wieloetapowych przechodzi przez plik Dockerfile szczegółowo, wiersz po wierszu, więc zaczyna się od początkowego pliku Dockerfile, tworzone przez program Visual Studio, podczas dodawania Docker obsługują do projektu i uzyskasz do niektóre optymalizacje później.

Początkowy pliku Dockerfile może wyglądać mniej więcej tak:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
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

A Oto szczegółowe informacje, wiersz po wierszu:

1. Rozpocząć etap za pomocą "małe" obrazu podstawowego tylko do środowiska uruchomieniowego, mu **podstawowy** dla odwołania.
2. Tworzenie **App** katalogu na obrazie.
3. Uwidocznić port **80**.
<!-- skip -->
5. Rozpocznij nowy etap z obrazem "large" Tworzenie/publikowania go wywoływać **kompilacji** dla odwołania.
6. Utwórz katalog **/src** na obrazie.
7. Maksymalnie 16 wiersza, skopiuj przywoływane projekty **.csproj** plików, aby można było później przywrócić pakietów.
<!-- skip -->
17. Przywracanie pakietów dla **Catalog.API** projektów i projektów występujących w odwołaniu.
18. Kopiowanie **wszystkich drzewo katalogów dla rozwiązania** (z wyjątkiem plików/katalogów, zawarte w **.dockerignore** plik) z do **/src** katalogu na obrazie.
19. Zmień bieżący folder do **Catalog.API** projektu.
20. Tworzenie projektu (i inne zależności projektu) i dane wyjściowe do **App** katalogu na obrazie.
<!-- skip -->
22. Rozpocznij nowy etap, kontynuując kompilacji, wywołać go **publikowania** dla odwołania.
23. Publikowanie projektu (zależności) i dane wyjściowe do **App** katalogu na obrazie.
<!-- skip -->
25. Rozpocznij nowy etap, kontynuując **podstawowy** i nadać mu **końcowe**
26. Zmień bieżący katalog na **App**
27. Kopiuj **App** katalogu od etapu **publikowania** do bieżącego katalogu
28. Definiowanie polecenia do uruchomienia po uruchomieniu kontenera.

Teraz Przyjrzyjmy się niektóre optymalizacje w celu zwiększenia wydajności całego procesu, oznacza to, w przypadku ramach aplikacji eShopOnContainers, około 22 minut lub dłużej tworzyć kompletne rozwiązanie w kontenerach systemu Linux.

Będziesz korzystać z platformy Docker warstwy pamięci podręcznej funkcji, która jest dość prosta: Jeśli obrazu podstawowego i polecenia są takie same, jak niektóre wcześniej wykonywanego, wynikowy warstwę, bez potrzeby po prostu można użyć do wykonania polecenia, dzięki czemu można oszczędzić trochę czasu.

Dlatego Skupmy się na **kompilacji** etapie linii 5 – 6 są prawie takie same, ale wiersze 7-17 różnią się dla każdej usługi w ramach aplikacji eShopOnContainers, więc można wykonać każdy jeden raz, jednak jeśli zmienisz linii 7-16, aby:

```
COPY . .
```

Następnie możesz ją w taki sam dla każdej usługi może spowodować skopiowanie całego rozwiązania i utworzyć większy warstwy, ale:

1) Proces kopiowania będzie można wykonać tylko po raz pierwszy (i podczas odbudowywania w przypadku modyfikacji pliku) i użyć pamięci podręcznej dla wszystkich innych usług i

2) Ponieważ większy obraz występuje w fazie przejściowej go, nie wpływa na rozmiar obrazu końcowego.

Obejmuje dalej optymalizacji znaczące `restore` wykonano w wierszu 17, polecenia, który również jest inny dla każdej usługi w ramach aplikacji eShopOnContainers. Jeśli zmienisz tylko ten wiersz:

```console
RUN dotnet restore
```

Będzie ona przywrócenia pakietów dla całego rozwiązania, ale następnie ponownie go samo jak tylko raz zamiast 15 razy dzięki strategii w bieżącym zakresie.

Jednak `dotnet restore` tylko działa w przypadku pojedynczego projektu lub pliku rozwiązania w folderze, więc realizacji tego jest nieco bardziej skomplikowane i o sposobie jego rozwiązania, bez pobierania do zbyt wiele szczegółów, to:

1) Dodaj następujące wiersze do **.dockerignore**:

   - `*.sln`, aby ignorować wszystkie pliki rozwiązania w drzewie folderów głównych

   - `!eShopOnContainers-ServicesAndWebApps.sln`, aby uwzględnić ten plik rozwiązania.

2) Obejmują `/ignoreprojectextensions:.dcproj` argument `dotnet restore`, więc ignoruje także projektu docker-compose i przywrócenie tylko pakiety dla rozwiązania w ramach aplikacji eShopOnContainers ServicesAndWebApps.

Końcowe optymalizacji te rzeczy dzieją wierszu 20 jest nadmiarowa, jako wiersz 23 również tworzy aplikację i powróci do trybu, w zasadzie bezpośrednio po wierszu 20, dzięki czemu przechodzi innego polecenia czasochłonne.

Wynikowy plik jest następnie:

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS publish
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

### <a name="creating-your-base-image-from-scratch"></a>Tworzenie obrazu podstawowego od podstaw

Można utworzyć własny obraz podstawowy platformy Docker, od podstaw. W tym scenariuszu nie jest zalecane w przypadku osobą, która jest uruchamiana przy użyciu rozwiązania Docker, ale jeśli chcesz ustawić bity określonego obrazu podstawowego, możesz to zrobić.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Wielu architektury obrazów platformy .NET Core**. \
  [https://github.com/dotnet/announcements/issues/14](https://github.com/dotnet/announcements/issues/14)

- **Tworzenie obrazu podstawowego**. Oficjalna dokumentacja platformy Docker. \
  [https://docs.docker.com/engine/userguide/eng-image/baseimages/](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![3 — Tworzenie obrazów zdefiniowany z numerem plików Dockerfile](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Tworzenie niestandardowych obrazów platformy Docker i osadzanie aplikacji lub usługi w nich

Dla każdej usługi w aplikacji należy utworzyć obraz powiązane. Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, wystarczy pojedynczego obrazu.

Należy pamiętać, że obrazy platformy Docker są tworzone automatycznie dla Ciebie w programie Visual Studio. Poniższe kroki są tylko potrzebne dla przepływu pracy edytorze/interfejsu wiersza polecenia i wyjaśnione w celu uściślenia, o co się stanie, poniżej.

Jako deweloper musisz opracowywać i testować lokalnie, przed wypchnięciem ukończonych funkcji lub zmień wartość na system kontroli źródła (na przykład w usłudze GitHub). Oznacza to, że trzeba tworzenie obrazów platformy Docker i wdrażanie kontenerów do lokalnego hosta platformy Docker (Windows lub maszyny Wirtualnej systemu Linux) i uruchamianie, testowanie i debugowanie względem tych kontenerów lokalnego.

Aby utworzyć niestandardowy obraz w środowisku lokalnym przy użyciu interfejsu wiersza polecenia platformy Docker i z pliku Dockerfile, można użyć polecenia kompilacji platformy docker, tak jak rysunek 5-5.

![Ekran postępu tworzenia obrazu platformy Docker](./media/image8.png)

**Rysunek 5-5**. Tworzenie niestandardowego obrazu platformy Docker

Opcjonalnie, zamiast bezpośredniego uruchamiania kompilacji platformy docker z folderu projektu, można najpierw wygenerować folder do wdrożenia z wymaganych bibliotek .NET i pliki binarne, uruchamiając `dotnet publish`, a następnie użyj `docker build` polecenia.

Spowoduje to utworzenie obrazu platformy Docker o nazwie `cesardl/netcore-webapi-microservice-docker:first`. W tym przypadku: pierwszy to znacznik reprezentujący określonej wersji. Za Powtórz ten krok dla każdego obrazu niestandardowego, potrzebne do tworzenia aplikacji platformy Docker złożone.

Jeśli aplikacja składa się z wielu kontenerów (czyli jest aplikację obsługującą wiele kontenerów), możesz również użyć `docker-compose up --build` polecenie, aby skompilować wszystkie obrazy powiązane z jednym poleceniem, posługując się metadanymi ujawnione w pliki docker-compose.yml pokrewne .

Można znaleźć istniejących obrazów w repozytorium lokalnym za pomocą platformy docker polecenie obrazów, jak pokazano w rysunek 5 – 6.

![Wyświetl ekran obrazów z polecenia obrazów platformy docker](./media/image9.png)

**Rysunek 5 – 6.** Wyświetlanie istniejących obrazów za pomocą polecenia obrazów platformy docker

### <a name="creating-docker-images-with-visual-studio"></a>Tworzenie obrazów platformy Docker za pomocą programu Visual Studio

Podczas tworzenia projektu z obsługą platformy Docker przy użyciu programu Visual Studio, nie są jawnie tworzone obrazu. Zamiast tego obrazu zostanie utworzony po naciśnięciu klawisza **F5** (lub **Ctrl-F5**) do uruchamiania dockerized aplikacji lub usługi. Ten krok jest automatycznie w programie Visual Studio i nie będziesz widzieć praca, ale jest ważne, że wiesz, co się dzieje na dole.

![4 — (opcjonalnie) usług Compose w pliku docker-compose.yml](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania aplikacji platformy Docker z wieloma kontenerami

[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku pozwala zdefiniować zestaw powiązanych usług, który można wdrożyć jako złożone aplikacji za pomocą poleceń wdrażania. Konfiguruje również jego relacji zależności i konfiguracji czasu wykonywania.

Aby użyć pliku docker-compose.yml, musisz utworzyć głównego pliku lub folderu głównego rozwiązania z zawartością, podobnie jak w poniższym przykładzie:

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

Ten plik docker-compose.yml jest nieco uproszczona i scalone. Zawiera on statyczne dane konfiguracji dla każdego kontenera (na przykład nazwa obrazu niestandardowego), który jest zawsze wymagany i informacje o konfiguracji, które mogą być zależne od środowiska wdrażania, takie jak parametry połączenia. W kolejnych sekcjach dowiesz się, jak do podziału docker-compose.yml konfiguracji na wiele docker-compose plików i zastąpienie wartości w zależności od typu środowiska i wykonywanie (debugowanie lub wydanie).

Przykład pliku docker-compose.yml definiuje czterema usługami: `webmvc` usługi (aplikacja sieci web), dwie mikrousługi (`ordering.api` i `basket.api`) i danych z jednego źródła, `sql.data`zgodnie z programu SQL Server dla systemu Linux uruchomiony jako kontener. Każda usługa zostanie wdrożony jako kontener, dzięki czemu obraz platformy Docker jest wymagana dla każdego.

Plik docker-compose.yml określa nie tylko jakie kontenery są używane, ale ich indywidualnie konfiguracji. Na przykład `webmvc` definicja kontenera w plik yml:

- Używa wstępnie utworzonych `eshop/web:latest` obrazu. Jednakże można także skonfigurować obraz, który ma zostać utworzony jako część narzędzia docker compose wykonywania bez dodatkowej konfiguracji oparte na kompilację: sekcji w pliku docker-compose.

- Inicjuje dwóch zmiennych środowiskowych (adres URL katalogu i OrderingUrl).

- Przekazuje narażonych port 80 w kontenerze na zewnętrzny port 80 na maszynie hosta.

- Linki w aplikacji sieci web do wykazu i kolejność usługi z ustawieniem depends_on. Powoduje to, że usługa poczekaj, aż te usługi są uruchomione.

Firma Microsoft będzie ponownie plik docker-compose.yml w dalszej części tego tematu, gdy opisujemy sposób implementacji aplikacji obsługującej wiele kontenerów i mikrousług.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Praca z docker-compose.yml w programie Visual Studio 2017

Oprócz dodawania pliku Dockerfile do projektu, jak wspomniano wcześniej, Visual Studio 2017 (z 15.8 na) można dodać obsługę programu orchestrator narzędzia Docker Compose do rozwiązania.

Podczas dodawania obsługi orkiestratora kontenerów, jak pokazano w rysunek 5 – 7 po raz pierwszy, Visual Studio tworzy plik Dockerfile dla projektu i tworzy nowy projekt (sekcja service) w Twoim rozwiązaniu przy użyciu kilku globalnego `docker-compose*.yml` pliki, a następnie dodanie Projekt do tych plików. Następnie można otworzyć pliki docker-compose.yml i zaktualizować je z dodatkowymi funkcjami.

Należy powtórzyć ten formularz, działania każdego projektu, które mają zostać uwzględnione w pliku docker-compose.yml.

W momencie pisania tego dokumentu program Visual Studio obsługuje koordynatorów narzędzia Docker Compose i Service Fabric.

![Opcja menu kontekstowego, aby dodać obsługę programu orchestrator do projektu programu ASP.NET Core](./media/image21.png)

**Rysunek 5 – 7**. Dodanie obsługi platformy Docker w programie Visual Studio 2017, klikając prawym przyciskiem myszy projekt ASP.NET Core

Po dodaniu obsługi orkiestratora do rozwiązania w programie Visual Studio, pojawi się także nowy węzeł (w `docker-compose.dcproj` pliku projektu) w Eksploratorze rozwiązań, który zawiera pliki docker-compose.yml dodano, jak pokazano w rysunek 5 – 8.

![docker-compose węzła w Eksploratorze rozwiązań](./media/image11.png)

**Rysunek 5 – 8**. **Narzędzia docker compose** węzła drzewa dodane w Eksploratorze rozwiązań 2017 r. w usłudze Visual Studio

Można wdrożyć aplikację obsługującą wiele kontenerów za pomocą pliku docker-compose.yml pojedynczego przy użyciu `docker-compose up` polecenia. Jednak program Visual Studio dodaje grupę z nich, dzięki czemu można zastąpić wartości w zależności od środowiska (programowania lub produkcji) i typ wykonywania (wydania lub debugowania). Ta funkcja zostaną wyjaśnione w kolejnych sekcjach.

![5 — uruchamianie kontenerów lub złożony aplikacji](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Kompilowanie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, możesz uruchomić go przez wdrożenie jej do hosta platformy Docker (maszyny Wirtualnej lub serwera fizycznego). Jednak jeśli aplikacja zawiera wiele usług, możesz go wdrożyć jako złożone aplikacji, za pomocą jednego polecenia interfejsu wiersza polecenia (docker-compose się), lub za pomocą programu Visual Studio, które korzystają z tego polecenia w sposób niewidoczny. Przyjrzyjmy się różne opcje.

### <a name="option-a-running-a-single-container-application"></a>Option A: Uruchamianie aplikacji jednego kontenera

#### <a name="using-docker-cli"></a>Za pomocą interfejsu wiersza polecenia platformy Docker

Można uruchomić kontener platformy Docker przy użyciu `docker run` polecenia, jak pokazano w rysunek 5-9:

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Powyższe polecenie spowoduje utworzenie nowego wystąpienia kontenera z określonego obrazu, za każdym razem, gdy jest uruchomiony. Możesz użyć `--name` parametr nadaj nazwę kontenera, a następnie użyć `docker start {name}` (lub kontenerze o identyfikatorze lub nazwie automatyczne) w celu uruchomienia istniejącego wystąpienia kontenera.

![Wyświetl ekran podczas uruchamiania kontenera platformy Docker za pomocą platformy docker, uruchom polecenie](./media/image13.png)

**Rysunek 5-9**. Uruchamianie kontenera platformy Docker za pomocą platformy docker, uruchom polecenie

W takim przypadku polecenie wiąże wewnętrznego portu 5000 kontenera do portu 80 maszyny hosta. Oznacza to, że host jest nasłuchuje na porcie 80 i przekazywania do portu 5000 kontenera.

Wartość skrótu, wyświetlany jest identyfikator kontenera i również został przypisany losowe czytelna nazwa Jeśli `--name` opcja nie jest używana.

#### <a name="using-visual-studio"></a>Za pomocą programu Visual Studio

Jeśli jeszcze nie została dodana obsługa orkiestratora kontenerów, można również uruchomić aplikację jeden kontener w programie Visual Studio, naciskając klawisz **Ctrl-F5** i można również użyć **F5** do debugowania aplikacji w kontenerze. Kontener działa lokalnie przy użyciu platformy docker, uruchom.

### <a name="option-b-running-a-multi-container-application"></a>Opcja B: Uruchamianie aplikacji z wieloma kontenerami

W większości przypadków enterprise aplikację platformy Docker będzie składać się z wielu usług, co oznacza, że należy uruchomić aplikację obsługującą wiele kontenerów, jak pokazano na rysunku 5-10.

![Maszyny Wirtualnej za pomocą wielu kontenerów platformy Docker](./media/image14.png)

**Rysunek 5 – 10**. Maszyny Wirtualnej przy użyciu kontenerów Docker wdrożonych

#### <a name="using-docker-cli"></a>Za pomocą interfejsu wiersza polecenia platformy Docker

Aby uruchomić aplikację obsługującą wiele kontenerów za pomocą interfejsu wiersza polecenia platformy Docker, należy użyć `docker-compose up` polecenia. To polecenie używa **docker-compose.yml** pliku, że masz na poziomie rozwiązania, aby wdrożyć aplikację obsługującą wiele kontenerów. Rysunek 5 – 11 przedstawia wyniki przy uruchamianiu polecenia z katalogiem głównym rozwiązania, który zawiera plik docker-compose.yml.

![Ekranu widoku podczas uruchamiania narzędzia docker compose się polecenia](./media/image15.png)

**Rysunek 5 – 11**. Przykład powoduje podczas uruchamiania narzędzia docker compose się polecenia

Po platformy docker-compose się polecenia uruchomienia, aplikacji i jej powiązane kontenery są wdrażane w sieci hosta platformy Docker, jak pokazano na rysunku 5-10.

#### <a name="using-visual-studio"></a>Za pomocą programu Visual Studio

Uruchamianie aplikacji z wieloma kontenerami za pomocą programu Visual Studio 2017 nie można pobrać wszystkie prostsze. Wystarczy nacisnąć klawisz **Ctrl-F5** do uruchomienia lub **F5** do debugowania, jak zwykle — Konfigurowanie **narzędzia docker compose** projekt jako projekt startowy.  Visual Studio obsługuje wszystkie ustawienia potrzebne, aby można było utworzyć punktów przerwania w zwykły sposób i debugowania, co ostatecznie stają się niezależnych procesy działające w "serwerów zdalnych", po prostu taką jak ta.

Jak wspomniano wcześniej, podczas dodawania każdego kolejnego obsługę rozwiązań platformy Docker do projektu w ramach rozwiązania, projektu jest skonfigurowany w pliku globalnego docker-compose.yml (poziomie rozwiązania), który umożliwia uruchamiania lub debugowania całego rozwiązania tylko raz. Program Visual Studio uruchomi jeden kontener dla każdego projektu, który ma włączoną obsługę rozwiązań platformy Docker i wykonaj wszystkie kroki wewnętrznego dla Ciebie (dotnet publikowania, docker kompilacji itd.).

Jeśli chcesz wykonać rzut oka na wszystkich drudgery, zapoznaj się z pliku:

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

Istotną kwestią jest, jak pokazano na rysunku 5-12, w programie Visual Studio 2017 dodatkowego **Docker** polecenie, aby uzyskać kluczowe działania F5. Ta opcja pozwala uruchomić lub debugować aplikację obsługującą wiele kontenerów przez uruchomienie wszystkich kontenerów, które są zdefiniowane w plikach docker-compose.yml na poziomie rozwiązania. Możliwość debugowania rozwiązań do obsługi wielu kontenerów oznacza, że można ustawić kilka punktów przerwania, w każdym punkcie przerwania, które znajdują się w innym projekcie (kontenera), a podczas debugowania w programie Visual Studio przestanie w punktach przerwania, zdefiniowane w różnych projektach i uruchomiona na różnych kontenerów.

![Visual Studio debugowania narzędzi systemem-projektów docker compose](./media/image16.png)

**Rysunek 5 – 12**. Uruchamianie aplikacji obsługującej wiele kontenerów w programie Visual Studio 2017

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Wdrażanie kontenera platformy ASP.NET ha zdalnym hoście platformy Docker** \
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Uwaga dotycząca testowanie i wdrażanie przy użyciu koordynatorów

Narzędzia docker compose się i platformy docker, Uruchom polecenia (lub uruchamianie i debugowanie kontenerów w programie Visual Studio) są odpowiednie do testowania kontenerów w środowisku programistycznym. Jednak to podejście nie należy używać w przypadku wdrożeń produkcyjnych, w którym powinien dotyczyć koordynatorów, takich jak [Kubernetes](https://kubernetes.io/) lub [usługi Service Fabric](https://azure.microsoft.com/services/service-fabric/). Jeśli używasz usługi Kubernetes, trzeba użyć [zasobników](https://kubernetes.io/docs/concepts/workloads/pods/pod/) do organizowania kontenerów i [usług](https://kubernetes.io/docs/concepts/services-networking/service/) do ich sieci. Możesz także użyć [wdrożeń](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) do organizowania zasobnika tworzenia i modyfikacji.

![6 — testowanie aplikacji sieci Web lub mikrousług](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Testowanie aplikacji platformy Docker za pomocą lokalnego hosta platformy Docker

W tym kroku różnią się w zależności od tego, co robi aplikacji. W prostej aplikacji sieci Web platformy .NET Core, który jest wdrażany jako jeden kontener lub usługi uzyskać dostęp do usługi, otwierając przeglądarki na hoście platformy Docker i przechodząc do tej lokacji, jak pokazano w rysunek 5-13. (Jeśli konfiguracji w pliku Dockerfile kontenera jest mapowany na port na hoście, który jest inna niż 80, obejmuje port hosta w adresie URL).

![Widok przeglądarki odpowiedzi HTTP punktu końcowego interfejsu API](./media/image18.png)

**Rysunek 5-13**. Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu localhost

Adres IP hosta w przypadku platformy Docker nie wskazuje localhost (domyślnie, gdy za pomocą platformy Docker CE, powinien), aby przejść do usługi, użyj adresu IP karty sieciowej komputera.

Należy pamiętać, że ten adres URL w przeglądarce korzysta z portu 80 na przykład kontenerem omawiana. Jednak wewnętrznie żądania nastąpi przekierowanie do portu 5000, ponieważ było jak miała być wdrożona przy użyciu rozwiązania docker, uruchom polecenie, zgodnie z opisem w poprzednim kroku.

Możesz również przetestować aplikację przy użyciu programu curl w terminalu, jak pokazano w rysunek 5-14. W przypadku instalacji platformy Docker na Windows domyślny adres IP hosta platformy Docker jest zawsze 10.0.75.1 Oprócz rzeczywistego adresu IP tego komputera.

![Wyświetl ekran odpowiedzi punktu końcowego interfejsu API za pomocą programu curl](./media/image19.png)

**Rysunek 5-14**. Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu programu curl

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Testowanie i debugowanie kontenerów przy użyciu programu Visual Studio 2017

Gdy uruchamianie i debugowanie kontenerów za pomocą programu Visual Studio 2017, tak jak w przypadku braku pojemników można debugować aplikację platformy .NET w taki sam sposób.

### <a name="testing-and-debugging-without-visual-studio"></a>Testowanie i debugowanie bez programu Visual Studio

Jeżeli projektujesz przy użyciu podejścia edytora/CLI debugowanie kontenerów jest trudniejsze, i chcesz debugować, generując ślady.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Debugowanie aplikacji w lokalnym kontenerze Docker** \
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- **Steve Lasker. Kompilowanie, debugowanie, wdrażanie aplikacji platformy ASP.NET Core przy użyciu platformy Docker.** Film wideo. \
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Uproszczone przepływu pracy podczas tworzenia kontenerów przy użyciu programu Visual Studio

Skutecznie przepływ pracy przy użyciu programu Visual Studio jest znacznie prostsze niż w przypadku użycia podejście edytora/interfejsu wiersza polecenia. Większość czynności wymagane przez platformę Docker związane z pliku Dockerfile i pliki docker-compose.yml są ukryte lub uproszczone przez program Visual Studio, jak pokazano w rysunek 5 – 15.

![Uproszczony przepływu pracy opracowywania kontenera za pomocą programu Visual Studio: 1 — kodu aplikacji, 2 - Obsługa Dodaj platformy Docker do projektów (tylko raz), 3 - uruchomienia kontenera lub rozwiązania docker-compose aplikacji, 4 - Test aplikacji sieci Web lub mikrousług, 5 - wypychania do repozytorium i powtórz tę czynność.](./media/image20.png)

**Rysunek 5 – 15**. Uproszczone przepływu pracy podczas tworzenia w programie Visual Studio

Ponadto należy wykonać tylko raz w kroku 2 (Dodawanie obsługę platformy Docker do swoich projektów). W związku z tym przepływ pracy jest podobne do zadań rozwoju zwykle, gdy przy użyciu platformy .NET do tworzenia innych aplikacji. Musisz wiedzieć, co się dzieje dzieje się w tle (procesu tworzenia obrazu, jakie obrazy podstawowe korzystasz, wdrażanie kontenerów, itp.) i czasami również należy edytować plik Dockerfile lub docker-compose.yml dostosowywania zachowania. Jednak większość pracy jest znacznie uproszczone przy użyciu programu Visual Studio, co możesz o wiele bardziej produktywne.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Steve Lasker. Programowanie na platformie .NET platformy docker przy użyciu programu Visual Studio 2017** \
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Używanie poleceń programu PowerShell w pliku Dockerfile do konfigurowania kontenerów Windows 

[Kontenery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umożliwiają konwertowanie istniejących aplikacji Windows obrazów platformy Docker i wdrożyć je przy użyciu tych samych narzędzi, jak w pozostałych ekosystemie Docker. Aby użyć kontenery Windows, możesz uruchomić poleceń programu PowerShell w pliku Dockerfile, jak pokazano w poniższym przykładzie:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

W tym przypadku jesteśmy przy użyciu obrazu podstawowego systemu Windows Server Core (ustawienie FROM) i instalowanie usług IIS za pomocą polecenia programu PowerShell (Ustawienie Uruchom). W podobny sposób można również użyć poleceń programu PowerShell do skonfigurowania dodatkowych składników, takich jak ASP.NET 4.x, .NET 4.6 lub innego oprogramowania Windows. Na przykład następujące polecenie w pliku Dockerfile konfiguruje ASP.NET 4.5:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Dodatkowe zasoby

- **aspnet-docker/Dockerfile.** Przykładowe polecenia programu PowerShell do uruchamiania z plików dockerfile w celu uwzględnienia funkcji Windows. \
  [https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile](https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile)

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](../multi-container-microservice-net-applications/index.md)
