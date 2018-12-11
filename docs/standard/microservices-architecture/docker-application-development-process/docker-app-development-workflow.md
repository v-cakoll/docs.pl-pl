---
title: Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/05/2018
ms.openlocfilehash: bc6b1796ed7b12a04affc521ac2efee515c48ae2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150553"
---
# <a name="development-workflow-for-docker-apps"></a>Przepływ pracy tworzenia oprogramowania dla aplikacji platformy Docker

Każdy deweloper maszyny, których Deweloper kody aplikacji przy użyciu preferowanego języka i sprawdza ją lokalnie rozpoczyna się cyklu tworzenia aplikacji. Niezależnie od tego, które języków i platformy, deweloper zdecyduje, w tym przepływie pracy dewelopera jest zawsze opracowywania i testowania kontenerów platformy Docker, ale sposób lokalnie.

Każdy kontener (wystąpienia obrazu platformy Docker) obejmuje następujące składniki:

- Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux, Windows Nano Server lub Windows Server Core).

- Pliki dodawane przez dewelopera (pliki binarne aplikacji itp.).

- Informacje o konfiguracji (ustawienia środowiska i zależności).

## <a name="workflow-for-developing-docker-container-based-applications"></a>Przepływ pracy na potrzeby tworzenia aplikacji opartych na kontenerach platformy Docker

W tej sekcji opisano *pętli wewnętrzny* przepływ pracy tworzenia oprogramowania dla aplikacji opartych na kontenerach platformy Docker. Przepływ pracy wewnętrznej pętli oznacza, że to nie biorąc pod uwagę szersze przepływ pracy DevOps i po prostu koncentruje się na rozwoju pracy na komputerze dewelopera. Początkowe kroki konfigurowania środowiska nie są dołączane, ponieważ te są wykonywane tylko raz.

Aplikacja składa się z własnych usług, a także dodatkowe biblioteki (zależności). Poniżej przedstawiono podstawowe kroki, które zwykle wykonać podczas kompilowania aplikacji platformy Docker, jak pokazano w rysunek 5-1.

![Instrukcje krok po kroku przepływu pracy tworzenia grafiki konteneryzowanych aplikacji platformy Docker](./media/image1.png)

**Rysunek 5-1.** Instrukcje krok po kroku przepływu pracy do tworzenia aplikacji kontenerowych nimi platformy Docker

W tym przewodniku opisano szczegółowo całego tego procesu i na każdym kroku głównych zostało wyjaśnione, skupiając się na środowisko Visual Studio.

Korzystając z podejście do tworzenia edytora/CLI (na przykład programu Visual Studio Code oraz interfejsu wiersza polecenia platformy Docker w systemie macOS lub Windows), musisz wiedzieć każdego kroku, zazwyczaj bardziej szczegółowo niż Jeśli używasz programu Visual Studio. Aby uzyskać więcej informacji na temat pracy w środowisku interfejsu wiersza polecenia, zobacz książki elektronicznej [cykl życia aplikacji kontenerowych nimi platformy Docker z Platforms i narzędzi Microsoft](https://aka.ms/dockerlifecycleebook/).

Podczas korzystania z programu Visual Studio, wiele z tych kroków są obsługiwane dla Ciebie, co znacznie zwiększa wydajność pracy. Jest to szczególnie istotne w przypadku, gdy są przy użyciu programu Visual Studio 2017 i ustawianie elementów docelowych wielokontenerowych aplikacji. Na przykład w tylko jednym kliknięciem, program Visual Studio dodaje *pliku Dockerfile* i *docker-compose.yml* plików do swoich projektów za pomocą konfiguracji dla aplikacji. Po uruchomieniu aplikacji w programie Visual Studio tworzy obraz platformy Docker i uruchamia aplikację obsługującą wiele kontenerów bezpośrednio na platformie Docker. Umożliwia ona nawet jednocześnie debugowanie kilka kontenerów. Te funkcje zwiększania szybkiego rozwoju.

Do wytycznych, który następuje po Wyjaśnijmy, co dzieje się "dzieje się w tle" za pomocą platformy Docker.

![Krok 1 — kod aplikacji grafiki](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Krok 1. Rozpocznij kodowanie i tworzenie początkowej aplikacja lub usługa linii bazowej

Tworzenie aplikacji platformy Docker to podobnie, jak opracować aplikację bez platformy Docker. Różnica jest, że podczas tworzenia dla platformy Docker, są wdrażanie i testowanie aplikacji lub usług działających w kontenerach platformy Docker w środowisku lokalnym. Kontener może być kontenera systemu Linux lub kontenerów Windows.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Konfigurowanie środowiska lokalnego z programem Visual Studio

Aby rozpocząć, upewnij się, że masz [Docker Community Edition (CE)](https://www.docker.com/community-edition) dla Windows zainstalowany zgodnie z opisem w poniższych instrukcjach:

[Wprowadzenie do platformy Docker CE dla Windows](https://docs.docker.com/docker-for-windows/)

Ponadto konieczne Visual Studio 2017 z **programowanie dla wielu platform .NET Core** obciążenia zainstalowany, jak pokazano w rysunek 5-2.

![](./media/image3.png)

**Rysunek 5-2**. Wybieranie **.NET Core i Docker** obciążenie podczas instalacji programu Visual Studio 2017

Możesz rozpocząć kodowanie swoją aplikację w zwykły .NET (zwykle w .NET Core, jeśli planowane jest korzystanie z kontenerów), nawet przed włączeniem platformy Docker w aplikacji i wdrażanie i testowanie na platformie Docker. Jednak zaleca się uruchamiania nad platformy Docker tak szybko, jak to możliwe, ponieważ się rzeczywistego środowiska i wszelkie problemy, które mogą być wykrywane tak szybko, jak to możliwe. To zaleca się, ponieważ dzięki programowi Visual Studio tak łatwe do pracy z rozwiązaniem Docker, że niemal pozornie przezroczyste — najlepszy przykład podczas debugowania aplikacji obsługującej wiele kontenerów za pomocą programu Visual Studio.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Wprowadzenie do platformy Docker CE dla Windows**

   [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

- **Visual Studio 2017**

   [*https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![Krok 2 — grafika zapisu plików Dockerfile](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Krok 2. Tworzenie pliku Dockerfile związane z istniejącego obrazu podstawowego platformy .NET

Potrzebujesz pliku Dockerfile dla niestandardowego obrazu, z którą chcesz skompilować; należy również plik Dockerfile dla każdego kontenera do wdrożenia, czy wdrożyć automatycznie z programu Visual Studio lub ręcznie przy użyciu interfejsu wiersza polecenia platformy Docker (docker, uruchom i docker-compose poleceń). Jeśli aplikacja zawiera pojedynczą usługę niestandardowych, konieczne będzie pojedynczego pliku Dockerfile. Jeśli aplikacja zawiera wiele usług (tak jak w architekturze mikrousług), należy jeden plik Dockerfile dla każdej usługi.

Plik Dockerfile znajduje się w folderze głównym aplikacji lub usługi. Zawiera polecenia, określające sposób konfigurowania i uruchamiania aplikacji lub usługi w kontenerze platformy Docker. Można ręcznie utworzyć plik Dockerfile w kodzie i dodać go do projektu, wraz z zależności .NET.

Program Visual Studio Tools for Docker to zadanie wymaga tylko kilku kliknięć myszą. Po utworzeniu nowego projektu w programie Visual Studio 2017 jest dostępna opcja o nazwie **włączyć obsługę platformy Docker**, jak pokazano w rysunek 5-3.

![Włączanie obsługi platformy Docker, podczas tworzenia nowego projektu w programie Visual Studio 2017](./media/image5.png)

**Rysunek 5-3**. Włączanie obsługi platformy Docker, podczas tworzenia nowego projektu w programie Visual Studio 2017

Można również włączyć obsługę platformy Docker w istniejącym projekcie aplikacji sieci web platformy .NET Core, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie **Dodaj** > **obsługę platformy Docker** , jak pokazano na rysunku 5-4.

![Dodaj opcję menu pomocy technicznej platformy Docker w programie Visual Studio](./media/add-docker-support.png)

**Rysunek 5-4**. Włączanie obsługi platformy Docker w istniejącym projekcie programu Visual Studio 2017

Ta akcja spowoduje dodanie *pliku Dockerfile* do projektu za pomocą wymaganej konfiguracji i jest dostępny tylko dla projektów aplikacji sieci web platformy .NET Core.

Aby dodać *docker-compose.yml* plików dla całego rozwiązania, kliknij prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierz **Dodaj**  >   **Obsługa Orkiestratora kontenerów**, jak pokazano na rysunku 5-5.

![Dodaj opcję menu pomocy technicznej koordynatora kontenerów w programie Visual Studio](./media/add-container-orchestrator-support.png)

**Rysunek 5-5**. Dodawanie obsługi orkiestratora kontenerów do istniejącego projektu w programie Visual Studio 2017.

W poniższych sekcjach opisano informacje, które przechodzi do każdego z tych plików. Program Visual Studio można wykonać to zadanie dla Ciebie, ale warto zrozumieć, co jest umieszczane w pliku Dockerfile.

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>Opcja A: Tworzenie projektu przy użyciu istniejących oficjalnego obrazu Docker w programie .NET

Zazwyczaj Tworzenie niestandardowego obrazu kontenera na podstawie obrazu podstawowego można uzyskać z oficjalnego repozytorium na [usługi Docker Hub](https://hub.docker.com/) rejestru. To jest dokładnie co się dzieje w tle po włączeniu obsługi platformy Docker w programie Visual Studio. Plik Dockerfile używa istniejący obraz aspnetcore.

Wcześniej opisano firma Microsoft, które obrazów platformy Docker i repozytoriów, można użyć w zależności od framework i systemu operacyjnego zostały wybrane. Na przykład, jeśli chcesz użyć programu ASP.NET Core (Linux lub Windows), obrazu do wykorzystania jest microsoft / aspnetcore:2.0. W związku z tym wystarczy określić, jakie podstawowego obrazu platformy Docker, który będzie używany dla kontenera. Można to zrobić, dodając firmy microsoft / aspnetcore:2.0 do Twojego pliku Dockerfile. Jest to wykonywane automatycznie przez program Visual Studio, ale w przypadku zaktualizowania wersji zaktualizuj tę wartość.

Oficjalna repozytorium obrazów platformy .NET z usługi Docker Hub przy użyciu numeru wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowanie, testowanie i produkcja).

Poniższy kod przedstawia przykładowy plik Dockerfile dla kontenera platformy ASP.NET Core.

```Dockerfile
FROM microsoft/aspnetcore:2.0

ARG source

WORKDIR /app

EXPOSE 80

COPY ${source:-obj/Docker/publish} .

ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

W tym przypadku kontener zależy od wersji 2.0 oficjalny obraz platformy Docker programu ASP.NET Core (wielu arch dla systemów Linux i Windows). Jest to ustawienie `FROM microsoft/aspnetcore:2.0`. (Aby uzyskać więcej informacji na temat tego obrazu podstawowego zobacz [obrazu platformy Docker programu ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) strony i [obrazu platformy Docker programu .NET Core](https://hub.docker.com/r/microsoft/dotnet/) strony.) W pliku Dockerfile trzeba będzie również poinstruować platformy Docker do nasłuchiwania na porcie TCP, używane w czasie wykonywania (w tym przypadku port 80, zgodnie z konfiguracją z ustawieniem UDOSTĘPNIAJĄ).

Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz. Na przykład wiersz punktu wejścia z \["dotnet", "MySingleContainerWebApp.dll"\] platformy docker, aby uruchomić aplikację .NET Core. Jeśli używasz zestawu SDK i .NET Core interfejsu wiersza polecenia (interfejsu wiersza polecenia platformy dotnet) aby skompilować i uruchomić aplikację .NET, to ustawienie będzie inny. Mierzenie to, że wiersz punktu wejścia i inne ustawienia będą różnić w zależności od języka i platformy, wybrany dla aplikacji.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Tworzenie obrazów platformy Docker dla aplikacji .NET Core**

   [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

- **Tworzenie własnego obrazu**. W oficjalnej dokumentacji platformy Docker.

   [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>Przy użyciu repozytoriów wielu architektury obrazu

Jednym repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows obraz. Ta funkcja umożliwia dostawców, takich jak Microsoft (obraz podstawowy dla twórców) do utworzenia pojedynczego repozytorium na pokrycie wiele platform (dotyczy to systemów Linux i Windows). Na przykład [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repozytorium, które są dostępne w rejestrze usługi Docker Hub zapewnia obsługę dla systemów Linux i Windows Nano Server przy użyciu tej samej nazwy repozytorium.

Jeśli określony tag, przeznaczonych dla platformy, która jest jawne, takich jak w następujących przypadkach:

- **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux

- **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

Jednak i to jest nowy od połowy 2017 r. w przypadku określenia taką samą nazwę obrazu, nawet w przypadku tego samego tagu, nowe obrazy wielu architektury (na przykład obraz aspnetcore obsługuje wielu arch) będą używać wersji systemu Linux lub Windows, w zależności od hosta platformy Docker systemu operacyjnego, który jest wdrażany , jak pokazano w poniższym przykładzie:

- **microsoft/aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

Dzięki temu podczas ściągnąć obraz z hosta Windows go każda będzie ściągać wariant Windows i ściągania taką samą nazwę obrazu na hoście z systemem Linux każda będzie ściągać wariantów systemu Linux.

### <a name="option-b-creating-your-base-image-from-scratch"></a>Opcja B: Tworzenie obrazu podstawowego od podstaw

Można utworzyć własny obraz podstawowy platformy Docker, od podstaw. W tym scenariuszu nie jest zalecane w przypadku osobą, która jest uruchamiana przy użyciu rozwiązania Docker, ale jeśli chcesz ustawić bity określonego obrazu podstawowego, możesz to zrobić.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Wielu architektury obrazów platformy .NET Core**.

   https://github.com/dotnet/announcements/issues/14

- **Tworzenie obrazu podstawowego**. Oficjalna dokumentacja platformy Docker.

   [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![Krok 3 — Tworzenie obrazów grafiki](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Krok 3. Tworzenie niestandardowych obrazów platformy Docker i osadzanie aplikacji lub usługi w nich

Dla każdej usługi w aplikacji należy utworzyć obraz powiązane. Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, wystarczy pojedynczego obrazu.

Obrazy platformy Docker są tworzone automatycznie dla Ciebie w programie Visual Studio. Poniższe kroki są tylko potrzebne dla przepływu pracy edytorze/interfejsu wiersza polecenia i wyjaśnione w celu uściślenia, o co się stanie, poniżej.

Jako deweloper musisz opracowywać i testować lokalnie, przed wypchnięciem ukończonych funkcji lub zmień wartość na system kontroli źródła (na przykład w usłudze GitHub). Oznacza to, że trzeba tworzenie obrazów platformy Docker i wdrażanie kontenerów do lokalnego hosta platformy Docker (Windows lub maszyny Wirtualnej systemu Linux) i uruchamianie, testowanie i debugowanie względem tych kontenerów lokalnego.

Aby utworzyć niestandardowy obraz w środowisku lokalnym przy użyciu interfejsu wiersza polecenia platformy Docker i z pliku Dockerfile, można użyć polecenia kompilacji platformy docker, tak jak rysunek 5-5.

![Tworzenie niestandardowego obrazu platformy Docker](./media/image8.png)

**Rysunek 5-5**. Tworzenie niestandardowego obrazu platformy Docker

Opcjonalnie zamiast bezpośredniego uruchamiania kompilacji platformy docker z folderu projektu, możesz najpierw wygenerować folderem do wdrożenia przy użyciu wymaganych bibliotek .NET i pliki binarne, uruchamiając polecenia dotnet publikowania, a następnie użyj polecenia kompilacji platformy docker.

Spowoduje to utworzenie obrazu platformy Docker o nazwie **cesardl/netcore-webapi mikrousługi — docker: pierwszy**. W tym przypadku: pierwszy to znacznik reprezentujący określonej wersji. Za Powtórz ten krok dla każdego obrazu niestandardowego, potrzebne do tworzenia aplikacji platformy Docker złożone.

Jeśli aplikacja składa się z wielu kontenerów (czyli jest aplikację obsługującą wiele kontenerów), można również użyć narzędzia docker compose się — polecenie kompilacji, aby skompilować wszystkie obrazy powiązane z jednym poleceniem, posługując się metadanymi ujawnione w powiązane pliki docker-compose.yml.

Można znaleźć istniejących obrazów w repozytorium lokalnym za pomocą platformy docker polecenie obrazów, jak pokazano w rysunek 5 – 6.

![Wyświetlanie istniejących obrazów za pomocą polecenia obrazów platformy docker](./media/image9.png)

**Rysunek 5 – 6.** Wyświetlanie istniejących obrazów za pomocą polecenia obrazów platformy docker

### <a name="creating-docker-images-with-visual-studio"></a>Tworzenie obrazów platformy Docker za pomocą programu Visual Studio

Podczas tworzenia projektu z obsługą platformy Docker przy użyciu programu Visual Studio, nie są jawnie tworzone obrazu. Zamiast tego obrazu zostanie utworzony po naciśnięciu klawisza **F5** do uruchamiania dockerized aplikacji lub usługi. Ten krok jest automatycznie w programie Visual Studio i nie będziesz widzieć praca, ale jest ważne, że wiesz, co się dzieje na dole.

![Krok 4 — Definiowanie usług grafiki](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Krok 4. Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania aplikacji platformy Docker z wieloma kontenerami

[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) pliku pozwala zdefiniować zestaw powiązanych usług, który można wdrożyć jako złożone aplikacji za pomocą poleceń wdrażania.

Aby użyć pliku docker-compose.yml, musisz utworzyć głównego pliku lub folderu głównego rozwiązania z zawartością, podobnie jak w poniższym przykładzie:

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

Ten plik docker-compose.yml jest nieco uproszczona i scalone. Zawiera on statyczne dane konfiguracji dla każdego kontenera (na przykład nazwa obrazu niestandardowego), która zawsze ma to zastosowanie, a także informacje o konfiguracji, które mogą być zależne od środowiska wdrażania, takie jak parametry połączenia. W kolejnych sekcjach dowiesz się, jak można podzielić na wiele konfiguracji platformy docker-compose.yml docker-compose plików i zastąpienie wartości w zależności od typu środowiska i wykonywanie (debugowanie lub wydanie).

Przykład pliku docker-compose.yml definiuje czterema usługami: webmvc usługi (aplikacja sieci web), dwa mikrousługi (catalog.api i ordering.api) i jeden źródłowy kontener danych, sql.data, oparte na programie SQL Server dla uruchomionego jako kontener systemu Linux. Każda usługa jest wdrażana jako kontener, dzięki czemu obraz platformy Docker jest wymagana dla każdego.

Plik docker-compose.yml określa nie tylko jakie kontenery są używane, ale ich indywidualnie konfiguracji. Na przykład webmvc definicja kontenera w plik yml:

- Używa wstępnie skompilowanych eshop / sieci web: latest obrazu. Jednakże można także skonfigurować obraz, który ma zostać utworzony jako część narzędzia docker compose wykonywania bez dodatkowej konfiguracji oparte na kompilację: sekcji w pliku docker-compose.

- Inicjuje dwóch zmiennych środowiskowych (adres URL katalogu i OrderingUrl).

- Przekazuje narażonych port 80 w kontenerze na zewnętrzny port 80 na maszynie hosta.

- Linki w aplikacji sieci web do wykazu i kolejność usłudze zależy od\_ustawienia. Powoduje to, że usługa poczekaj, aż te usługi są uruchomione.

Firma Microsoft będzie ponownie plik docker-compose.yml w dalszej części tego tematu, gdy opisujemy sposób implementacji aplikacji obsługującej wiele kontenerów i mikrousług.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Praca z docker-compose.yml w programie Visual Studio 2017

Podczas dodawania obsługi orkiestratora kontenerów do projektu aplikacji sieci web, jak pokazano w rysunek 5 – 7, program Visual Studio dodaje sekcję service (projekt) do rozwiązania, który zawiera plik docker-compose.yml. Jest to prosty sposób rozpocząć tworzenie rozwiązania wielu kontenerów.

![Dodaj element menu pomocy technicznej koordynatora kontenerów w programie Visual Studio](./media/add-container-orchestrator-support.png)

**Rysunek 5 – 7**. Dodanie obsługi platformy Docker w programie Visual Studio 2017, klikając prawym przyciskiem myszy projekt ASP.NET Core

Dodawanie obsługi orkiestratora kontenerów dodaje plik Dockerfile do projektu (jeśli jeszcze nie istnieje). Dodaje także informacje o konfiguracji do pliku docker-compose.yml globalnego na poziomie rozwiązania. Zobaczysz nowy węzeł projektu ( *docker compose.dcproj* pliku projektu) w **Eksploratora rozwiązań** zawierający plik docker-compose.yml, jak pokazano w rysunek 5 – 8.

![docker-compose węzła w Eksploratorze rozwiązań](./media/docker-compose-files.png)

**Rysunek 5 – 8**. **Narzędzia docker compose** węzła drzewa dodane w Eksploratorze rozwiązań 2017 r. w usłudze Visual Studio

Następnie można otworzyć pliku docker-compose.yml i zaktualizować je z dodatkowymi funkcjami.

Można wdrożyć aplikację obsługującą wiele kontenerów za pomocą pliku docker-compose.yml pojedynczego za pomocą `docker-compose up` polecenia.

![Krok 5 — uruchom aplikację grafiki](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Krok 5. Kompilowanie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, możesz uruchomić go przez wdrożenie jej do hosta platformy Docker (maszyny Wirtualnej lub serwera fizycznego). Jednak jeśli aplikacja zawiera wiele usług, możesz go wdrożyć jako złożone aplikacji, za pomocą jednego polecenia interfejsu wiersza polecenia (docker-compose się), lub za pomocą programu Visual Studio, które korzystają z tego polecenia w sposób niewidoczny. Przyjrzyjmy się różne opcje.

### <a name="option-a-run-a-single-container-app"></a>Opcja A: Uruchamianie aplikacji jednego kontenera

#### <a name="docker-cli"></a>Interfejs CLI platformy docker

Można uruchomić kontener platformy Docker za pomocą platformy docker, uruchom polecenie, tak jak rysunek 5-9:

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![Uruchamianie kontenera platformy Docker za pomocą platformy docker, uruchom polecenie](./media/image13.png)

**Rysunek 5-9**. Uruchamianie kontenera platformy Docker za pomocą platformy docker, uruchom polecenie

W takim przypadku polecenie wiąże wewnętrznego portu 5000 kontenera do portu 80 maszyny hosta. Oznacza to, że host jest nasłuchuje na porcie 80 i przekazywania do portu 5000 kontenera.

#### <a name="visual-studio"></a>Visual Studio

Jeśli jeszcze nie została dodana obsługa orkiestratora kontenerów, można również uruchomić aplikację jeden kontener w programie Visual Studio, naciskając klawisz **F5**. Kontener działa lokalnie przy użyciu platformy docker, uruchom.

### <a name="option-b-run-a-multi-container-app"></a>Opcja B: Uruchom aplikację obsługującą wiele kontenerów

W większości przypadków enterprise aplikację platformy Docker będzie składać się z wielu usług, co oznacza, że należy uruchomić aplikację obsługującą wiele kontenerów, jak pokazano na rysunku 5-10.

![Grafika przedstawiająca maszyny Wirtualnej za pomocą kontenerów Docker wdrożonych](./media/image14.png)

**Rysunek 5 – 10**. Maszyny Wirtualnej przy użyciu kontenerów Docker wdrożonych

#### <a name="docker-cli"></a>Interfejs CLI platformy docker

Aby uruchomić aplikację obsługującą wiele kontenerów za pomocą interfejsu wiersza polecenia platformy Docker, możesz uruchomić platformy docker-compose się polecenia. Tego polecenia używa docker-compose.yml pliku masz na poziomie rozwiązania, aby wdrożyć aplikację obsługującą wiele kontenerów. Rysunek 5 – 11 przedstawia wyniki przy uruchamianiu polecenia z katalogu głównego projektu, który zawiera plik docker-compose.yml.

![Przykład powoduje podczas uruchamiania narzędzia docker compose się polecenia](./media/image15.png)

**Rysunek 5 – 11**. Przykład powoduje podczas uruchamiania narzędzia docker compose się polecenia

Po platformy docker-compose się polecenia uruchomienia, aplikacji i jej powiązane kontenery są wdrażane w sieci hosta platformy Docker.

#### <a name="visual-studio"></a>Visual Studio

Korzystanie z aplikacji obsługującej wiele kontenerów, w programie Visual Studio 2017 jest proste. Nie tylko możesz uruchomić aplikację obsługującą wiele kontenerów, ale możesz debugować swoje kontenery bezpośrednio z programu Visual Studio przez ustawienie regularne punkty przerwania.

Jak wspomniano wcześniej, podczas dodawania każdego kolejnego obsługi orkiestratora kontenerów do projektu w ramach rozwiązania, projektu jest skonfigurowany w pliku globalnego docker-compose.yml (poziomie rozwiązania), który umożliwia uruchamiania lub debugowania całego rozwiązania tylko raz. Program Visual Studio uruchomi jeden kontener dla każdego projektu, który ma włączoną obsługę rozwiązań platformy Docker i wykonaj wszystkie kroki wewnętrznego dla Ciebie (dotnet publikowania, docker kompilacji itd.).

Istotną kwestią jest, jak pokazano na rysunku 5-12, w programie Visual Studio 2017 dodatkowego **Docker** polecenie, aby uzyskać **F5** klucza akcji. Ta opcja pozwala uruchomić lub debugować aplikację obsługującą wiele kontenerów przez uruchomienie wszystkich kontenerów, które są zdefiniowane w plikach docker-compose.yml na poziomie rozwiązania. Możliwość debugowania rozwiązań do obsługi wielu kontenerów oznacza, że można ustawić kilka punktów przerwania, w każdym punkcie przerwania, które znajdują się w innym projekcie (kontenera), a podczas debugowania w programie Visual Studio przestanie w punktach przerwania, zdefiniowane w różnych projektach i uruchomiona na różnych kontenerów.

![Uruchamianie aplikacji obsługującej wiele kontenerów w programie Visual Studio 2017](./media/image16.png)

**Rysunek 5 – 12**. Uruchamianie aplikacji obsługującej wiele kontenerów w programie Visual Studio 2017

### <a name="additional-resources"></a>Dodatkowe zasoby

-  **Wdrażanie kontenera platformy ASP.NET ha zdalnym hoście platformy Docker**

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Uwaga dotycząca testowanie i wdrażanie przy użyciu koordynatorów

Narzędzia docker compose się i platformy docker, Uruchom polecenia (lub uruchamianie i debugowanie kontenerów w programie Visual Studio) są odpowiednie do testowania kontenerów w środowisku programistycznym. Ale nie powinni używać tej metody, jeśli są przeznaczone dla klastrów platformy Docker i koordynatorów, takich jak Docker Swarm, Mesosphere DC/OS lub Kubernetes. Jeśli używasz klastra, takie jak [trybu Docker Swarm](https://docs.docker.com/engine/swarm/) (dostępne w Docker CE dla Windows i Mac od wersji 1.12), należy wdrożyć i przetestować przy użyciu dodatkowych poleceń, takich jak [tworzenia usługi docker](https://docs.docker.com/engine/reference/commandline/service_create/) dla jednej usługi. Jeśli wdrażasz aplikację składa się z kilku kontenerów, możesz użyć [pakietu Narzędzia docker compose](https://docs.docker.com/compose/reference/bundle/) i [myBundleFile wdrażana w rozwiązaniu docker](https://docs.docker.com/engine/reference/commandline/deploy/) wdrożyć złożone aplikację jako *stosu*. Aby uzyskać więcej informacji, zobacz wpis w blogu [Przedstawiamy eksperymentalne rozproszonych aplikacji pakiety](https://blog.docker.com/2016/06/docker-app-bundle/) w dokumentacji platformy Docker. w witrynie platformy Docker.

Dla [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) i [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/) użyje wdrożenia różnych poleceń i skryptów w także.

![Krok 6 grafiki](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Krok 6. Testowanie aplikacji platformy Docker za pomocą lokalnego hosta platformy Docker

W tym kroku różnią się w zależności od tego, co robi aplikacji. W prostej aplikacji sieci Web platformy .NET Core, który jest wdrażany jako jeden kontener lub usługi uzyskać dostęp do usługi, otwierając przeglądarki na hoście platformy Docker i przechodząc do tej lokacji, jak pokazano w rysunek 5-13. (Jeśli konfiguracji w pliku Dockerfile kontenera jest mapowany na port na hoście, który jest inna niż 80, obejmuje port hosta w adresie URL).

![Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu localhost](./media/image18.png)

**Rysunek 5-13**. Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu localhost

Adres IP hosta w przypadku platformy Docker nie wskazuje localhost (domyślnie, gdy za pomocą platformy Docker CE, powinien), aby przejść do usługi, użyj adresu IP karty sieciowej komputera.

Ten adres URL w przeglądarce na przykład kontenerem omawiana korzysta z portu 80. Jednak wewnętrznie żądania nastąpi przekierowanie do portu 5000, ponieważ było jak miała być wdrożona przy użyciu rozwiązania docker, uruchom polecenie, zgodnie z opisem w poprzednim kroku.

Możesz również przetestować aplikację przy użyciu programu curl w terminalu, jak pokazano w rysunek 5-14. W przypadku instalacji platformy Docker na Windows domyślny adres IP hosta platformy Docker jest zawsze 10.0.75.1 Oprócz rzeczywistego adresu IP tego komputera.

![Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu programu curl](./media/image19.png)

**Rysunek 5-14**. Przykład testowanie aplikacji platformy Docker lokalnie przy użyciu programu curl

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Testowanie i debugowanie kontenerów przy użyciu programu Visual Studio 2017

Gdy uruchamianie i debugowanie kontenerów za pomocą programu Visual Studio 2017, tak jak w przypadku braku pojemników można debugować aplikację platformy .NET w taki sam sposób.

### <a name="testing-and-debugging-without-visual-studio"></a>Testowanie i debugowanie bez programu Visual Studio

Jeśli tworzysz przy użyciu podejścia edytora/CLI debugowanie kontenerów jest trudniejsze, i chcesz debugować, generując ślady.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Debugowanie aplikacji w lokalnym kontenerze Docker**

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- **Steve Lasker. Kompilowanie, debugowanie, wdrażanie aplikacji platformy ASP.NET Core przy użyciu platformy Docker.** Film wideo.

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Uproszczone przepływu pracy podczas tworzenia kontenerów przy użyciu programu Visual Studio

Skutecznie przepływ pracy przy użyciu programu Visual Studio jest znacznie prostsze niż w przypadku użycia podejście edytora/interfejsu wiersza polecenia. Większość czynności wymagane przez platformę Docker związane z pliku Dockerfile i pliki docker-compose.yml są ukryte lub uproszczone przez program Visual Studio, jak pokazano w rysunek 5 – 15.

![Uproszczone przepływu pracy podczas tworzenia w programie Visual Studio](./media/image20.png)

**Rysunek 5 – 15**. Uproszczone przepływu pracy podczas tworzenia w programie Visual Studio

Ponadto należy wykonać tylko raz w kroku 2 (Dodawanie obsługę platformy Docker do swoich projektów). W związku z tym przepływ pracy jest podobne do zadań rozwoju zwykle, gdy przy użyciu platformy .NET do tworzenia innych aplikacji. Musisz wiedzieć, co się dzieje dzieje się w tle (procesu tworzenia obrazu, jakie obrazy podstawowe, którego używasz, wdrażanie kontenerów, itp.) i czasami również należy edytować plik Dockerfile lub docker-compose.yml dostosowywania zachowania. Jednak większość pracy jest znacznie uproszczone przy użyciu programu Visual Studio, co możesz o wiele bardziej produktywne.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Steve Lasker. Programowanie na platformie .NET platformy docker przy użyciu programu Visual Studio 2017**

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

- **Jeffrey T. Fritz. Umieszczanie aplikacji platformy .NET Core w kontenerze za pomocą nowych narzędzi platformy Docker dla programu Visual Studio**

   [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Używanie poleceń programu PowerShell w pliku Dockerfile do konfigurowania kontenerów Windows

[Kontenery Windows](/virtualization/windowscontainers/about/) umożliwiają konwertowanie istniejących aplikacji Windows obrazów platformy Docker i wdrożyć je przy użyciu tych samych narzędzi, jak w pozostałych ekosystemie Docker. Aby użyć kontenery Windows, możesz uruchomić poleceń programu PowerShell w pliku Dockerfile, jak pokazano w poniższym przykładzie:

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

- **aspnet-docker/Dockerfile.** Przykładowe polecenia programu Powershell do uruchamiania z plików dockerfile w celu uwzględnienia funkcji Windows.

   [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](../multi-container-microservice-net-applications/index.md)
