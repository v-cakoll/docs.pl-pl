---
title: "Przepływ pracy tworzenia aplikacji Docker"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Przepływ pracy tworzenia aplikacji Docker"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5a53aee4261a5a0bfc25b3520c50cf505b84f287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="development-workflow-for-docker-apps"></a>Przepływ pracy tworzenia aplikacji Docker

Cykl życia programowania aplikacji rozpoczyna się od wszystkich deweloperów maszyny, gdzie dewelopera kodów aplikacji przy użyciu preferowanego języka i sprawdza ją lokalnie. Niezależnie od tego, które języka, framework i platformy wybierze dewelopera, w tym przepływie pracy dewelopera jest zawsze tworzenie i testowanie kontenery Docker, ale w ten sposób lokalnie.

Każdego kontenera (wystąpienia obrazu Docker) obejmuje następujące składniki:

-   Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux, Windows Nano Server lub Windows Server Core).

-   Pliki dodane przez dewelopera (pliki binarne aplikacji itp.).

-   Informacje o konfiguracji (ustawienia środowiska i zależności).

## <a name="workflow-for-developing-docker-container-based-applications"></a>Przepływ pracy umożliwiający projektowanie aplikacji na podstawie kontenera Docker

W tej sekcji opisano *pętli wewnętrzny* przepływ pracy rozwoju aplikacji na podstawie kontenera Docker. Wewnętrzny pętli przepływu pracy oznacza, że jest nie biorąc pod uwagę szerszych DevOps przepływu pracy i po prostu koncentruje się na programowanie pracować na komputerze dewelopera. Początkowe kroki, aby skonfigurować środowisko nie są uwzględnione, ponieważ te są wykonywane tylko raz.

Aplikacja składa się z własnych usług oraz dodatkowych bibliotek (zależności). Poniżej przedstawiono podstawowe kroki, które zwykle wykonać podczas kompilowania aplikacji Docker, zgodnie z opisami w rysunek 5-1.

![](./media/image1.png)

**Rysunek 5-1.** Krok przepływu pracy umożliwiający projektowanie aplikacji konteneryzowanych Docker

W tym przewodniku szczegółowo całego tego procesu i każdy krok głównych tłumaczy koncentrujących się na środowiska Visual Studio.

Korzystając z podejście do tworzenia edytora/interfejsu wiersza polecenia (na przykład Visual Studio Code oraz interfejsu wiersza polecenia Docker na macOS lub Windows), musisz wiedzieć każdy krok zazwyczaj bardziej szczegółowo niż Jeśli używasz programu Visual Studio. Aby uzyskać więcej informacji na temat pracy w środowisku interfejsu wiersza polecenia można znaleźć Książka elektroniczna [cyklem życia aplikacji Docker konteneryzowanych Platforms firmy Microsoft i narzędzia](http://aka.ms/dockerlifecycleebook/).

Jeśli używasz programu Visual Studio 2015 lub Visual Studio 2017 wiele z tych kroków obsługi dla Ciebie, co znacznie zwiększa wydajność pracy. Jest to szczególnie istotne podczas przy użyciu programu Visual Studio 2017 i przeznaczonych dla wielu kontenera aplikacji. Na przykład tylko jednym kliknięciem, Visual Studio dodaje plik Dockerfile i docker-compose.yml pliku swoje projekty z konfiguracją aplikacji. Po uruchomieniu aplikacji w programie Visual Studio tworzy obraz Docker i uruchamia aplikację usługi kontenera bezpośrednio w Docker; Umożliwia ona nawet debugowanie jednocześnie kilka kontenerów. Te funkcje będą zwiększania szybkości rozwoju.

Jednakże wyłącznie z powodu Visual Studio sprawia, że te kroki są automatyczne oznacza, że nie trzeba znać, co się dzieje na dole z Docker. W związku z tym w wytycznych, który jest zgodny, możemy szczegóły każdego kroku.

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Rozpoczęcie kodowania i Utwórz początkową aplikacji lub usługi linii bazowej

Opracowanie aplikacji Docker jest podobny do sposobu opracowywania aplikacji bez rozwiązania Docker. Różnica polega na tym że podczas projektowania dla Docker, wdrażanie i testowanie aplikacji lub usługi działające w kontenerach Docker w środowisku lokalnym. Kontener może być kontenerem Linux lub kontenera systemu Windows.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Konfigurowanie środowiska lokalnego z programem Visual Studio

Aby rozpocząć, upewnij się, że [Docker Community Edition (CE)](https://www.docker.com/community-edition) dla systemu Windows zainstalowane zgodnie z objaśnieniem w poniższych instrukcji:

[Rozpoczynanie pracy z rozwiązaniem Docker CE dla systemu Windows](https://docs.docker.com/docker-for-windows/)

Ponadto należy Visual Studio 2017 r zainstalowane. To jest preferowana przez Visual Studio 2015 z programu Visual Studio Tools dla platformy Docker dodatku, ponieważ Visual Studio 2017 zawiera bardziej zaawansowane obsługę Docker, takich jak obsługa debugowanie kontenerów. Visual Studio 2017 obejmuje narzędzi dla platformy Docker w przypadku wybrania **.NET Core i Docker** obciążenie podczas instalacji, jak pokazano na rysunku 5-2.

![](./media/image3.png)

**Rysunek 5-2**. Wybieranie **.NET Core i Docker** obciążenie podczas instalacji programu Visual Studio 2017 r.

Możesz uruchomić kodowania aplikację w zwykły .NET (zwykle w .NET Core, jeśli planujesz używanie kontenerów), nawet przed włączeniem Docker w aplikacji i wdrażanie i testowanie w Docker. Jednak zaleca się uruchamiania pracuje Docker tak szybko, jak to możliwe, który będzie stanowić rzeczywistego środowiska, ponieważ wszelkie problemy, które mogą być wykrywane tak szybko, jak to możliwe. To zaleca się ponieważ Visual Studio ułatwia więc pracować z Docker że prawie uważa przezroczysty — najlepszy przykład podczas debugowania aplikacji kontenera wielu z programu Visual Studio.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Rozpoczynanie pracy z rozwiązaniem Docker CE dla systemu Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Utwórz plik Dockerfile związane z istniejącego obrazu podstawowego .NET

Plik Dockerfile wymagane dla każdego niestandardowego obrazu, który chcesz utworzyć; należy również plik Dockerfile dla każdego kontenera do wdrożenia, czy wdrożyć automatycznie z programu Visual Studio lub ręcznie przy użyciu interfejsu wiersza polecenia Docker (Uruchom docker i docker-tworzą poleceń). Jeśli aplikacja zawiera pojedynczą usługę niestandardowe, należy pojedynczy plik Dockerfile. Jeśli aplikacja zawiera wiele usług (jak architektura mikrousług), należy jeden plik Dockerfile dla każdej usługi.

Plik Dockerfile znajduje się w folderze głównym aplikacji lub usługi. Zawiera polecenia określające sposób ustawiania i uruchamiania aplikacji lub usługi w kontenerze Docker. Można ręcznie utworzyć plik Dockerfile w kodzie i dodaj go do projektu oraz zależności platformy .NET.

Visual Studio i jej narzędzi dla platformy Docker to zadanie wymaga tylko kilka razy kliknąć myszą. Po utworzeniu nowego projektu w Visual Studio 2017 jest opcja o nazwie **Obsługa Włączanie kontenerów (Docker)**, jak pokazano na rysunku 5-3.

![](./media/image5.png)

**Rysunek 5-3**. Włączanie obsługi platformy Docker, podczas tworzenia nowego projektu w programie Visual Studio 2017 r.

Można również włączyć obsługę Docker na nowy lub istniejący projekt prawym przyciskiem myszy plik projektu w programie Visual Studio i wybierając opcję **Docker Dodaj projekt obsługuje**, jak pokazano na rysunku 5-4.

![](./media/image6.png)

**Rysunek 5-4**. Włączanie obsługi platformy Docker w istniejącego projektu programu Visual Studio 2017 r.

Ta akcja na projekt (np. aplikacji sieci Web ASP.NET lub usługi sieci Web interfejsu API) dodaje plik Dockerfile do projektu z odpowiednią konfiguracją. Dodaje plik docker-compose.yml dla całego rozwiązania. W poniższych sekcjach opisano informacje, który jest przesyłany do każdego z tych plików. Visual Studio można nie tę pracę za Ciebie, ale warto poznać, co prowadzi do plik Dockerfile.

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>Opcja A: tworzenia projektu przy użyciu istniejącego obrazu oficjalnego .NET Docker

Zazwyczaj Tworzenie niestandardowego obrazu z kontenera na podstawowy obraz można uzyskać z oficjalnego repozytorium pod adresem [Centrum Docker](https://hub.docker.com/) rejestru. To dokładnie co się stanie w tle po włączeniu obsługi Docker w programie Visual Studio. Twoje plik Dockerfile użyje istniejącego obrazu aspnetcore.

Wcześniej wyjaśniono firma Microsoft, które obrazy usługi Docker i repozytoriów, można użyć, w zależności od framework i wybrano systemu operacyjnego. Na przykład, jeśli chcesz używać platformy ASP.NET Core (Linux lub Windows), obrazu do użycia firma microsoft / aspnetcore:2.0. W związku z tym wystarczy określić podstawową obrazów Docker będzie używany przez Twoje kontenera. Można to zrobić przez dodanie firmy microsoft / aspnetcore:2.0 do Twojej plik Dockerfile. To zostanie automatycznie wykonane przez program Visual Studio, ale gdyby zaktualizuj wersję, zaktualizuj tę wartość.

Użycie oficjalnego repozytorium obrazów .NET z Centrum Docker z numerem wersji gwarantuje, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowania, testowania i produkcji).

W poniższym przykładzie przedstawiono przykładowy plik Dockerfile kontenera platformy ASP.NET Core.

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

W takim przypadku kontenera jest oparty na wersji 2.0 oficjalnego obrazu platformy ASP.NET Core Docker (wielu arch dla systemów Linux i Windows). Jest to ustawienie `FROM microsoft/aspnetcore:2.0`. (Dodatkowe szczegóły dotyczące tego obrazu podstawowego, zobacz [platformy ASP.NET Core Docker obrazu](https://hub.docker.com/r/microsoft/aspnetcore/) strony i [.NET Core Docker obrazu](https://hub.docker.com/r/microsoft/dotnet/) strony.) W plik Dockerfile należy także poinstruować Docker nasłuchiwanie na porcie TCP, które będą używane w czasie wykonywania (w tym przypadku portu 80, zgodnie z konfiguracją z ustawieniem UWIDACZNIANIE).

Można określić dodatkowe ustawienia konfiguracji w plik Dockerfile, w zależności od języka i framework, którego używasz. Na przykład wiersz punktu wejścia z \["dotnet", "MySingleContainerWebApp.dll"\] informuje Docker na uruchamianie aplikacji .NET Core. Jeśli korzystasz z zestawu SDK i .NET Core interfejsu wiersza polecenia (dotnet interfejsu wiersza polecenia) aby skompilować i uruchomić aplikację .NET, to ustawienie będzie się różnić. Mierzenie jest, że wiersza punktu wejścia i inne ustawienia zostaną inne w zależności od języka i platformy wybrane dla aplikacji.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Tworzenie aplikacji programu .NET Core obrazy usługi Docker**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)

-   **Utwórz własny obraz**. W oficjalnej dokumentacji Docker.
    [*https://docs.docker.com/Engine/Tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>Przy użyciu repozytoria wielu architektury obrazu

Pojedynczy repozytorium może zawierać wariantów platform, takich jak obraz systemu Linux i obrazu systemu Windows. Ta funkcja umożliwia dostawcom, takich jak Microsoft (obraz podstawowy kreatory) tworzyć jednego repozytorium, aby pokrywał się wiele platform (która jest systemu Linux i Windows). Na przykład [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repozytorium, które są dostępne w rejestrze Centrum Docker zapewnia obsługę systemu Linux i Windows Nano Server przy użyciu tej samej nazwie repozytorium.

Jeśli określisz tag, przeznaczonych dla platformy, która jest jawne, takich jak w następujących przypadkach:

-   **Microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **Microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

Ale i jest nowy od połowy 2017, jeśli określisz tej samej nazwie obrazu, nawet z tym samym tagiem, nowych obrazów wielu architektury (na przykład aspnetcore obrazu, który obsługuje wielu arch) będą używać wersji systemu Linux lub Windows, w zależności od platformy Docker systemu operacyjnego hosta wdrażasz , jak pokazano w poniższym przykładzie:

-   **Microsoft / aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

Dzięki temu podczas pobierania obrazu z hostem z systemem Windows, do jego wariant systemu Windows będzie pobierać i ściąganie taką samą nazwę obrazu z hosta systemu Linux będzie pobierać wariant systemu Linux.

### <a name="option-b-creating-your-base-image-from-scratch"></a>Opcja B: tworzenia obrazu podstawowego od podstaw

Można utworzyć własny obraz podstawowy Docker od podstaw. W tym scenariuszu nie jest zalecane dla kogoś, kto jest począwszy Docker, ale jeśli chcesz ustawić określone bity obrazu podstawowego, możesz to zrobić.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wiele architektury .NET Core obrazów**.
https://github.com/DotNet/announcements/issues/14 
-   **Tworzenie obrazu podstawowego**. Oficjalna dokumentacja Docker.
    [*https://docs.docker.com/Engine/userguide/eng-Image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Utwórz niestandardowe obrazy usługi Docker i osadzić w nich usługi lub aplikacji

Dla każdej usługi w aplikacji należy utworzyć obraz pokrewne. Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, wystarczy jeden obraz.

Należy pamiętać, że obrazy usługi Docker są tworzone automatycznie dla Ciebie w programie Visual Studio. Poniższe kroki są tylko potrzebne do edytora/CLI przepływu pracy i wyjaśniono dla jasności informacji na temat efektów poniżej.

Deweloper, musisz opracowanie i przetestowanie lokalnie, dopóki wypychanych ukończone funkcji lub zmień system kontroli źródła (na przykład, aby GitHub). Oznacza to, że trzeba tworzyć obrazy Docker i wdrażanie kontenerów do rozwiązania Docker hosta lokalnego (Windows lub Linux VM) i uruchom, testowanie i debugowanie względem tych kontenerach lokalnego.

Aby utworzyć obraz niestandardowy w środowisku lokalnym przy użyciu interfejsu wiersza polecenia Docker i Twoje plik Dockerfile, służy polecenie docker kompilacji, tak jak rysunek 5-5.

![](./media/image8.png)

**Rysunek 5-5**. Tworzenie niestandardowego obrazu Docker

Opcjonalnie zamiast bezpośredniego uruchamiania kompilacji docker z folderu projektu, najpierw mogą generować folderem można wdrożyć za pomocą wymaganych bibliotek .NET i pliki binarne, uruchamiając dotnet opublikować, a następnie użyj polecenia docker kompilacji.

Spowoduje to utworzenie obrazu Docker o nazwie cesardl/netcore-webapi mikrousługi-docker: pierwszy. W takim przypadku: najpierw jest znacznik reprezentujący określonej wersji. Można Powtórz ten krok dla każdego niestandardowego obrazu potrzebnych do tworzenia aplikacji składa Docker.

Jeśli aplikacja składa się z wielu kontenerów (to znaczy jest aplikacji kontenera wielu), można również użyć rozwiązania docker compose w górę — polecenie kompilacji do kompilacji wszystkich powiązanych obrazy za pomocą jednego polecenia przy użyciu metadanych w pokrewny pliki docker-compose.yml.

Można znaleźć istniejących obrazów w lokalnym repozytorium przy użyciu rozwiązania docker polecenia obrazów, jak pokazano w rysunek 5 – 6.

![](./media/image9.png)

**Rysunek 5-6.** Wyświetlanie istniejących obrazów za pomocą polecenia docker obrazów

### <a name="creating-docker-images-with-visual-studio"></a>Tworzenie obrazów Docker z programem Visual Studio

Używając programu Visual Studio do tworzenia projektu z obsługą Docker, nie jawnie utworzysz obrazu. Zamiast tego obrazu jest tworzony automatycznie podczas naciśnij klawisz F5 i uruchom dockerized aplikacji lub usługi. Ten krok jest automatycznie w programie Visual Studio i nie będzie on być widoczny, ale należy pamiętać, że wiesz, co się dzieje na dole.

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Zdefiniuj usług w rozwiązaniu docker-compose.yml podczas kompilowania aplikacji usługi kontenera Docker

[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku pozwala zdefiniować zestaw usług wdrażanych jako aplikacja składa z poleceń wdrażania.

Aby użyć plik docker-compose.yml, należy utworzyć plik w sieci głównego lub głównego folderu rozwiązania z zawartością, podobnie jak w poniższym przykładzie:

```yml
version: '3'
  
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
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
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

Należy pamiętać, że ten plik docker-compose.yml wersji uproszczonym i scalone. Zawiera dane konfiguracji statycznych dla każdego kontenera (na przykład Nazwa niestandardowego obrazu), zawsze ma to zastosowanie, oraz informacje o konfiguracji, który może być zależna od środowiska wdrażania, takie jak parametry połączenia. W kolejnych sekcjach dowiesz się, jak można podzielić konfiguracji docker-compose.yml w wielu rozwiązania docker compose plików i Zastąp wartości w zależności od typu środowiska i wykonywanie (debugowanie czy wydanie).

Przykładowy plik docker-compose.yml definiuje pięć usługi: Usługa webmvc (aplikacja sieci web), dwa mikrousług (catalog.api i ordering.api) i jednego danych źródła kontenera, sql.data, oparte na serwerze SQL dla systemu Linux uruchomiony jako kontener. Każda usługa jest wdrażana jako kontener, więc obrazu Docker jest wymagane dla każdego.

Plik docker-compose.yml określa nie tylko kontenery, które są używane, ale ich indywidualnie konfiguracji. Na przykład webmvc kontenera definicję w pliku .yml:

-   Używa wbudowanych eshop / sieci web: r obrazu. Jednak można również skonfigurować obraz, który ma zostać utworzony jako część rozwiązania docker compose wykonywania z dodatkową konfigurację oparte na kompilację: sekcji w pliku docker-compose.

-   Inicjuje dwie zmienne środowiskowe (adres URL katalogu i OrderingUrl).

-   Przekazuje dostępnego portu 80 kontenera do portu zewnętrznego 80 na komputerze hosta.

-   Łączy aplikacji sieci web z katalogu i kolejność usługi o zależy od\_na ustawienie. Powoduje to, że usługa poczekać, aż te usługi są uruchomione.

Firma Microsoft będzie ponownie plik docker-compose.yml w dalszej części, gdy firma Microsoft opisano sposobu wdrażania wielu kontenera aplikacji i mikrousług.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Praca z docker-compose.yml w programie Visual Studio 2017 r.

Po dodaniu obsługi rozwiązania Docker do projektu usługi w rozwiązaniu Visual Studio, jak pokazano w rysunek 5-7, Visual Studio dodaje plik Dockerfile do projektu i dodaje sekcji usługi (projekt) w rozwiązaniu docker-compose.yml plików. To łatwy sposób redagowania rozwiązania wielu kontenera. Można następnie otwórz plik docker-compose.yml i zaktualizować je z dodatkowych funkcji.

![](./media/image6.png)

**Rysunek 5-7**. Dodawanie obsługi Docker w Visual Studio 2017, klikając prawym przyciskiem myszy projekt platformy ASP.NET Core

Dodawanie obsługi Docker w programie Visual Studio nie tylko dodaje plik Dockerfile do projektu, ale dodaje informacje o konfiguracji do kilku plików globalne docker-compose.yml ustawionych na poziomie rozwiązania.

Po dodaniu obsługi Docker do rozwiązania w programie Visual Studio widoczne będzie także nowy węzeł (w pliku projektu docker compose.dcproj) w Eksploratorze rozwiązań, zawierający pliki dodane docker-compose.yml, jak pokazano na rysunku 5-8.

![](./media/image11.PNG)

**Rysunek 5 – 8**. **Rozwiązania docker compose** węzła drzewa dodane w Eksploratorze rozwiązań 2017 r w usłudze Visual Studio

Można wdrożyć aplikacji usługi kontenera przy użyciu pliku pojedynczego docker-compose.yml przy użyciu rozwiązania docker compose zapasowej polecenia. Jednak program Visual Studio dodaje grupę z nich, można zastąpić wartości w zależności od środowiska (Programowanie i produkcja) i wykonywania typu (wersja i debugowania). W kolejnych sekcjach opisano tej możliwości.

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Tworzenie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, można uruchomić go przez wdrożenie jej do hosta Docker (maszyny Wirtualnej lub serwerów fizycznych). Jednak jeśli aplikacja zawiera wielu usług, możesz go wdrożyć jako składa aplikacji, za pomocą jednego polecenia interfejsu wiersza polecenia (docker składać się), lub z programem Visual Studio, która będzie używać tego polecenia w obszarze obejmuje. Przyjrzyjmy się różne opcje.

### <a name="option-a-running-a-single-container-with-docker-cli"></a>Opcja A: uruchomiony jeden kontener z interfejsu wiersza polecenia Docker

Kontener Docker przy użyciu rozwiązania docker, uruchom polecenie, tak jak rysunek 5 – 9, można uruchomić:

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**Rysunek 5 – 9**. Uruchomione w kontenerze Docker przy użyciu rozwiązania docker, uruchom polecenie

W takim przypadku polecenie wiąże wewnętrzny port 5000 kontenera do portu 80 komputerze hosta. Oznacza to, że host jest nasłuchiwanie na porcie 80 i przekazywania ich do portu 5000 w kontenerze.

### <a name="option-b-running-a-multi-container-application"></a>Opcja B: uruchamiania wielu kontenera aplikacji

W większości przypadków przedsiębiorstwa aplikacji Docker będzie składać się z wieloma usługami, co oznacza, że należy uruchomić aplikacji kontenera usługi, jak pokazano na rysunku 5-10.

![](./media/image14.png)

**Rysunek 5 – 10**. Maszyna wirtualna o wdrożone kontenery Docker

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>Aplikacja usługi kontenera uruchamiana za pomocą interfejsu wiersza polecenia Docker

Aby uruchomić aplikacji usługi kontenera przy użyciu interfejsu wiersza polecenia Docker, należy uruchomić docker-tworzą zapasowej polecenia. Tego polecenia używa docker-compose.yml pliku masz na poziomie rozwiązania, aby wdrożyć aplikację usługi kontenera. Rysunek 5-11 pokazuje wyniki podczas uruchamiania polecenia w katalogu głównym projektu, który zawiera plik docker-compose.yml.

![](./media/image15.png)

**Rysunek 5-11**. Przykład wyników podczas uruchamiania rozwiązania docker compose zapasowej polecenia

Po docker-tworzą zapasowej uruchamia polecenia, aplikacji i jej powiązane kontenery są wdrażane na hoście Docker, zgodnie z opisami w reprezentacji maszyny Wirtualnej w rysunek 5 – 10.

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>Uruchomiona i debugowanie aplikacji kontenera wielu z programem Visual Studio 

Nie można pobrać prostsze uruchamiania aplikacji usługi kontenera przy użyciu programu Visual Studio 2017 r. Nie można jedynie uruchomić aplikacji kontenera usługi, ale można debugować jego kontenerów bezpośrednio z programu Visual Studio przez ustawienie regularne punktów przerwania.

Jak wspomniano wcześniej, podczas każdego dodawania obsługi rozwiązania Docker do projektu w ramach rozwiązania, projektu jest skonfigurowany w pliku globalnego (poziom rozwiązania) docker-compose.yml, który można uruchomić ani debugować jednocześnie całego rozwiązania. Visual Studio będzie uruchomić jeden kontener dla każdego projektu, który ma włączoną obsługą rozwiązania Docker i wykonania wszystkich czynności wewnętrzny (dotnet opublikować, kompilacji docker itp.).

Należy koniecznie zwrócić uwagę, jak pokazano na rysunku 5-12, w programie Visual Studio 2017 rzeczy jest dodatkowe **Docker** polecenia dla akcji klucza F5. Ta opcja pozwala uruchomić ani debugować aplikacji kontenera aplikacji przez uruchomienie wszystkich kontenerów, które są zdefiniowane w plikach docker-compose.yml na poziomie rozwiązania. Możliwość debugowania kontenera wielu rozwiązań oznacza, że można ustawić kilka punktów przerwania, każdy punkt przerwania w innym projekcie (kontener), a podczas debugowania w programie Visual Studio zostanie zatrzymane w punktów przerwania zdefiniowany w różnych projektów i uruchomiona na różnych kontenerów.

![](./media/image16.png)

**Rysunek 5 – 12**. Uruchamianie aplikacji usługi kontenera w Visual Studio 2017 r.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Wdrażanie kontenera ASP.NET z hostem zdalnym Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Uwagi dotyczące testowania i wdrażania z orchestrators

Rozwiązania docker compose w górę i docker uruchomienie polecenia (lub systemem i debugowanie kontenerów w programie Visual Studio) są odpowiednie do testowania kontenery w środowisku projektowania. Jednak nie powinni używać tej metody, jeśli ma być przeznaczona dla klastrów Docker i orchestrators, takich jak Docker Swarm, Mesosphere DC/OS lub Kubernetes. Jeśli używasz klastra, takie jak [Docker Swarm tryb](https://docs.docker.com/engine/swarm/) (dostępne w CE Docker dla systemu Windows i Mac od wersji 1.12), należy wdrożyć i przetestować przy użyciu dodatkowych poleceń, takich jak [tworzenia usługi docker](https://docs.docker.com/engine/reference/commandline/service_create/) dla pojedynczy usługi. Jeśli wdrażana jest aplikacja składa się z kilku kontenery, użyj [rozwiązania docker compose pakietu](https://docs.docker.com/compose/reference/bundle/) i [docker wdrażanie myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) do wdrożenia aplikacji złożony jako *stosu*. Aby uzyskać więcej informacji, zobacz w blogu [wprowadzenie eksperymentalne rozproszonych aplikacji pakiety](https://blog.docker.com/2016/06/docker-app-bundle/) w dokumentacji programu Docker. w witrynie Docker.

Aby uzyskać [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) i [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) użyje inne wdrożenie poleceń i skryptów oraz.

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Testowanie aplikacji Docker za pomocą lokalnego hosta Docker

Ten krok będą się różnić w zależności od czynności aplikacji. W prostą aplikację .NET Core w sieci Web, który jest wdrożony jako jeden kontener lub usługi uzyskać dostęp do usługi przez otwarcie przeglądarki na hoście Docker i przechodząc do tej lokacji, jak pokazano w rysunek 5-13. (Jeśli konfiguracji w plik Dockerfile mapuje kontenera do portu na hoście, który jest inny niż 80, obejmuje host pocztowy w adresie URL).

![](./media/image18.png)

**Rysunek 5-13**. Przykład testowania aplikacji Docker lokalnie za pomocą localhost

Jeśli nie wskazuje localhost Docker adres IP hosta (domyślnie, gdy przy użyciu rozwiązania Docker CE, powinien), aby poruszać się z usługą, użyj adresu IP karty sieciowej tego komputera.

Należy pamiętać, że na przykład kontenerem omawiana tego adresu URL w przeglądarce korzysta z portu 80. Jednak wewnętrznie żądania nastąpi przekierowanie do portu 5000, ponieważ który był jak została wdrożona z docker, uruchom polecenie, zgodnie z objaśnieniem w poprzednim kroku.

Może także przetestować aplikacji przy użyciu programu curl z terminalu, jak pokazano w rysunek 5-14. W przypadku instalacji Docker w systemie Windows Docker IP hosta są zawsze domyślnie 10.0.75.1 Oprócz rzeczywisty adres IP komputera.

![](./media/image19.png)

**Rysunek 5-14**. Przykład testowania aplikacji Docker lokalnie przy użyciu programu curl

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Testowanie i debugowanie kontenerów wyposażonych w Visual Studio 2017 r.

Podczas uruchamiania i debugowanie kontenerów wyposażonych w Visual Studio 2017 r, można debugować aplikacji .NET w podobny sposób jak w przypadku braku kontenerów.

### <a name="testing-and-debugging-without-visual-studio"></a>Testowanie i debugowanie bez programu Visual Studio

Jeśli tworzysz podejście Edytor/CLI trudniej jest debugowanie kontenerów i można debugować generując śladów.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Debugowanie aplikacji w lokalnych kontenerze Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker. Tworzenie, debugowanie, wdrażanie aplikacji platformy ASP.NET Core przy użyciu rozwiązania Docker.** Wideo.
    [*https://channel9.msdn.com/events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Uproszczony przepływu pracy podczas opracowywania kontenery z programem Visual Studio

W rezultacie przepływu pracy przy użyciu programu Visual Studio jest znacznie prostsze niż w przypadku użycia metody Edytor/interfejsu wiersza polecenia. Większość czynności wymagane przez Docker powiązane plik Dockerfile i docker-compose.yml pliki są ukryte lub uproszczony przez program Visual Studio, jak pokazano w rysunek 5 – 15.

![](./media/image20.png)

**Rysunek 5 – 15**. Uproszczony przepływu pracy podczas opracowywania w programie Visual Studio

Ponadto należy wykonać krok 2 (Obsługa Docker dodawanie do projektów) tylko raz. W związku z tym przepływu pracy jest podobna do zadań programowania zwykle, gdy dla innych Programowanie przy użyciu platformy .NET. Musisz wiedzieć, co dzieje się w obszarze obejmuje (procesu tworzenia obrazu, jakie obrazy podstawowe używasz, wdrożenia kontenerów, itp.) i czasami się, że należy również edytować plik Dockerfile lub docker-compose.yml plik, aby dostosować zachowania. Jednak znacznie upraszcza większość zadań za pomocą programu Visual Studio, co możesz znacznie większą wydajność.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Steve Lasker. .NET — rozwój docker z programu Visual Studio 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T. Fritz. Umieść aplikacji .NET Core w kontenerze o nowe narzędzia Docker dla programu Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Za pomocą poleceń programu PowerShell w plik Dockerfile skonfigurować kontenery systemu Windows 

[Kontenery systemu Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) umożliwiają konwertowanie istniejących aplikacji systemu Windows na obrazy usługi Docker i wdrażać je z tego samego narzędzia jako rest ekosystemu Docker. Aby użyć kontenery systemu Windows, należy uruchomić polecenia programu PowerShell w plik Dockerfile, jak pokazano w poniższym przykładzie:

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

W takim przypadku wiemy przy użyciu podstawowy obraz systemu Windows Server Core (ustawienie FROM) i instalacji usług IIS za pomocą polecenia programu PowerShell (ustawienie URUCHAMIANIA). W podobny sposób poleceń programu PowerShell można użyć również do skonfigurowania dodatkowych składników, takich jak ASP.NET 4.x, .NET 4.6 lub innego oprogramowania systemu Windows. Na przykład następujące polecenie w plik Dockerfile konfiguruje ASP.NET 4.5:

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **ASPNET — docker/plik Dockerfile.** Przykład polecenia programu Powershell do uruchamiania z dockerfiles dołączenie funkcji systemu Windows.
    [*https://github.com/Microsoft/ASPNET-docker/blob/Master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (.. / net-core-single-containers-linux-windows-server-hosts/index.md)
