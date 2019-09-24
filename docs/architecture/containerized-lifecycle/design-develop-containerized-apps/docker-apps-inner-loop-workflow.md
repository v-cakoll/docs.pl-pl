---
title: Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker
description: Zapoznaj się z przepływem pracy "pętla wewnętrzna" na potrzeby opracowywania aplikacji platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 04e1b29e6a0cef89df05cc9124806c74a38b5249
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214351"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker

Przed wyzwoleniem przepływu pracy z pętlą zewnętrzną obejmującą cały cykl DevOps, wszystko to rozpocznie się na maszynie każdego dewelopera, kodowanie samej aplikacji przy użyciu preferowanych języków lub platform i przetestowanie go lokalnie (rysunek 4-21). Jednak w każdym przypadku będziesz mieć ważny, niezależnie od tego, jaki język, struktura lub platformy są wybrane. W tym konkretnym przepływie pracy są zawsze opracowywanie i testowanie kontenerów platformy Docker, ale lokalnie.

![Krok 1 — Code/Run/Debug](./media/image18.png)

**Rysunek 4-21**. Kontekst programowania pętli wewnętrznej

Kontener lub wystąpienie obrazu platformy Docker będzie zawierać następujące składniki:

- Wybór systemu operacyjnego (na przykład dystrybucja systemu Linux lub Windows)

- Pliki dodane przez dewelopera (na przykład pliki binarne aplikacji)

- Konfiguracja (na przykład ustawienia środowiska i zależności)

- Instrukcje dotyczące procesów uruchamianych przez platformę Docker

Można skonfigurować przepływ pracy programowania w pętli wewnętrznej, który wykorzystuje platformę Docker jako proces (opisany w następnej sekcji). Należy pamiętać, że wstępne kroki konfigurowania środowiska nie są uwzględniane, ponieważ wystarczy tylko raz.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu Visual Studio Code i interfejsu wiersza polecenia platformy Docker

Aplikacje składają się z własnych usług i dodatkowych bibliotek (zależności).

Na rysunku 4-22 przedstawiono podstawowe kroki, które zwykle trzeba wykonać podczas kompilowania aplikacji platformy Docker, a następnie szczegółowe opisy poszczególnych kroków.

![Przegląd przepływu pracy: Krok 1. kod, krok 2 — zapis wieloetapowe dockerfile, krok 3 — Tworzenie obrazów zdefiniowanych za pomocą wieloetapowe dockerfile, krok 4 — Definiowanie usług przy użyciu pliku platformy Docker, krok 5 — Uruchamianie kontenerów lub aplikacji składających się z kroku 6 — Testowanie aplikacji, krok 7 — wypychanie aby rozpocząć pętlę zewnętrzną (potoki ciągłej integracji/ciągłego wdrażania) lub Kontynuuj de veloping.](./media/image19.png)

**Rysunek 4-22**. Przepływ pracy wysokiego poziomu dla cyklu życia aplikacji kontenera platformy Docker przy użyciu interfejsu wiersza polecenia platformy Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1. Rozpocznij kodowanie w Visual Studio Code i Utwórz początkową aplikację/linię bazową usługi

Sposób tworzenia aplikacji jest podobny do sposobu, w jaki to zrobisz, bez dokowania. Różnica polega na tym, że podczas tworzenia i testowania aplikacji lub usług działających w kontenerach platformy Docker umieszczonych w środowisku lokalnym (na przykład w przypadku maszyn wirtualnych z systemem Linux lub Windows).

**Konfigurowanie środowiska lokalnego**

Najnowsze wersje platformy Docker dla komputerów Mac i systemu Windows ułatwiają tworzenie aplikacji platformy Docker, a instalacja jest prosta.

> [!TIP]
> Aby uzyskać instrukcje dotyczące konfigurowania Docker for Windows, przejdź do <https://docs.docker.com/docker-for-windows/>.
>
>Aby uzyskać instrukcje dotyczące konfigurowania platformy Docker dla komputerów Mac, <https://docs.docker.com/docker-for-mac/>przejdź do.

Ponadto potrzebny jest Edytor kodu, dzięki czemu można w rzeczywistości opracowywać aplikację przy użyciu interfejsu wiersza polecenia platformy Docker.

Firma Microsoft udostępnia Visual Studio Code, który jest lekkim edytorem kodu obsługiwanym w systemach Mac, Windows i Linux oraz udostępnia technologię IntelliSense z [obsługą wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, go, Java, Ruby, Python i większość nowoczesnych języków). [ Debugowanie](https://code.visualstudio.com/Docs/editor/debugging), [integracja z](https://code.visualstudio.com/Docs/editor/versioncontrol) [obsługą git i rozszerzeniami](https://code.visualstudio.com/docs/extensions/overview). Ten Edytor jest doskonałym rozwiązaniem dla deweloperów systemów Mac i Linux. W systemie Windows można również użyć pełnej aplikacji programu Visual Studio.

> [!TIP]
> Aby uzyskać instrukcje dotyczące instalowania Visual Studio Code dla systemu Windows, Mac lub Linux, przejdź <https://code.visualstudio.com/docs/setup/setup-overview/>do.
>
> Aby uzyskać instrukcje dotyczące konfigurowania platformy Docker dla komputerów Mac, <https://docs.docker.com/docker-for-mac/>przejdź do.

Możesz współpracować z interfejsem wiersza polecenia platformy Docker i pisać kod przy użyciu dowolnego edytora kodu, ale używanie Visual Studio Code z rozszerzeniem Docker ułatwia tworzenie i `Dockerfile` `docker-compose.yml` opracowywanie plików w obszarze roboczym. Możesz również uruchamiać zadania i skrypty z Visual Studio Code IDE, aby wykonywać polecenia platformy Docker przy użyciu interfejsu wiersza polecenia platformy Docker poniżej.

Rozszerzenie Docker dla VS Code zapewnia następujące funkcje:

- Automatyczne `Dockerfile` i`docker-compose.yml` generowanie plików

- Podświetlanie składni i wskazówki dotyczące kursora `docker-compose.yml` dla `Dockerfile` i plików

- Technologia IntelliSense (uzupełnianie) `Dockerfile` dla `docker-compose.yml` plików i

- Zaznaczanie błędów (błędy i ostrzeżenia) dla `Dockerfile` plików

- Paleta poleceń (F1) dla najpopularniejszych poleceń platformy Docker

- Integracja Eksploratora do zarządzania obrazami i kontenerami

- Wdróż obrazy z DockerHub i rejestrów kontenerów platformy Azure, aby Azure App Service

Aby zainstalować rozszerzenie platformy Docker, naciśnij kombinację klawiszy Ctrl + Shift + `ext install`P, wpisz polecenie, a następnie uruchom rozszerzenie install, aby wyświetlić listę rozszerzeń portalu Marketplace. Następnie wpisz **Docker** , aby przefiltrować wyniki, a następnie wybierz rozszerzenie obsługa platformy Docker, jak przedstawiono na rysunku 4-23.

![Widok rozszerzenia Docker dla VS Code.](./media/image20.png)

**Rysunek 4-23**. Instalowanie rozszerzenia platformy Docker w Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2. Tworzenie pliku dockerfile związanych z istniejącym obrazem (zwykłym systemem operacyjnym lub środowiskami deweloperskimi, takimi jak .NET Core, Node. js i Ruby)

Musisz `DockerFile` utworzyć obraz niestandardowy do skompilowania i na kontener, który ma zostać wdrożony. Jeśli Twoja aplikacja składa się z pojedynczej usługi niestandardowej, będziesz potrzebować jednego `DockerFile`z nich. Jeśli jednak aplikacja składa się z wielu usług (podobnie jak w przypadku architektury mikrousług), będzie potrzebna jedna `Dockerfile` na usługę.

`DockerFile` Jest to zwykle umieszczane w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, dzięki czemu platforma Docker wie, jak skonfigurować i uruchomić tę aplikację lub usługę. Możesz utworzyć `DockerFile` i dodać go do projektu wraz z kodem (Node. js, .NET Core itp.) lub, jeśli jesteś nowym środowiskiem, zapoznaj się z poniższą wskazówką.

> [!TIP]
> Możesz użyć rozszerzenia Docker, aby poprowadzić Cię podczas korzystania `Dockerfile` z `docker-compose.yml` plików i związanych z kontenerami platformy Docker. Na koniec prawdopodobnie napiszesz te rodzaje plików bez tego narzędzia, ale przy użyciu rozszerzenia Docker jest dobrym punktem wyjścia, który przyspiesza uczenie się.

Na rysunku 4-24 można zobaczyć, jak zostanie dodany plik do redagowania platformy Docker przy użyciu rozszerzenia Docker dla VS Code.

![Widok konsoli rozszerzenia platformy Docker dla VS Code.](./media/image24.png)

**Rysunek 4-24**. Pliki platformy Docker dodane za pomocą **polecenia Dodaj pliki platformy Docker do obszaru roboczego**

Po dodaniu pliku dockerfile należy określić, który podstawowy obraz platformy Docker będzie używany (na przykład za pomocą `FROM mcr.microsoft.com/dotnet/core/aspnet`programu). Zwykle utworzysz niestandardowy obraz na podstawie obrazu podstawowego, który można uzyskać z dowolnego oficjalnego repozytorium w [rejestrze usługi Docker Hub](https://hub.docker.com/) (na przykład [obrazu dla platformy .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) lub [dla środowiska Node. js](https://hub.docker.com/_/node/)).

***Użyj istniejącego oficjalnego obrazu platformy Docker***

Korzystanie z oficjalnego repozytorium stosu języka z numerem wersji zapewnia, że te same funkcje językowe są dostępne na wszystkich komputerach (w tym na etapie projektowania, testowania i produkcji).

Poniżej znajduje się przykład pliku dockerfile dla kontenera .NET Core:

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

W tym przypadku obraz jest oparty na wersji 2,2 ASP.NET Core oficjalnego obrazu platformy Docker (wiele rozwiązań dla systemów Linux i Windows), zgodnie z wierszem `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`. (Aby uzyskać więcej informacji na temat tego tematu, zobacz stronę [ASP.NET Core Docker](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) i stronę [obrazu platformy Docker programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) ).

W pliku dockerfile można także nakazać platformie Docker nasłuchiwanie portu TCP, który będzie używany w czasie wykonywania (na przykład port 80).

Możesz określić dodatkowe ustawienia konfiguracji w pliku dockerfile, w zależności od używanego języka i platformy. Na przykład `ENTRYPOINT` wiersz z `["dotnet", "MySingleContainerWebApp.dll"]` poleceniem instruuje platformę Docker, aby uruchomić aplikację .NET Core. Jeśli używasz zestawu SDK i interfejs wiersza polecenia platformy .NET Core (`dotnet CLI`) do kompilowania i uruchamiania aplikacji .NET, to ustawienie będzie inne. Kluczowym punktem jest to, że wiersz punktu wejścia i inne ustawienia zależą od języka i platformy wybranej dla aplikacji.

> [!TIP]
> Aby uzyskać więcej informacji na temat tworzenia obrazów platformy Docker dla aplikacji platformy .NET <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>Core, przejdź do.
>
> Aby dowiedzieć się więcej na temat tworzenia własnych obrazów, <https://docs.docker.com/engine/tutorials/dockerimages/>przejdź do.

**Używanie repozytoriów obrazów wieloskładnikowych**

Nazwa pojedynczego obrazu w repozytorium może zawierać warianty platformy, takie jak obraz systemu Linux i obraz Windows. Ta funkcja umożliwia dostawcom, takim jak firma Microsoft (twórcy obrazów podstawowych), tworzenie jednego repozytorium w celu pokrycia wielu platform (to jest Linux i Windows). Na przykład repozytorium [dotnet/rdzeń/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostępne w rejestrze usługi Docker Hub zapewnia obsługę systemu Linux i Windows nano Server przy użyciu tej samej nazwy obrazu.

Ściąganie obrazu [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hosta z systemem Windows powoduje pobranie wariantu systemu Windows, podczas gdy ściąganie tej samej nazwy obrazu z hosta z systemem Linux jest ściągane.

***Tworzenie obrazu podstawowego od podstaw***

Możesz utworzyć własny obraz podstawowy platformy Docker od podstaw, jak wyjaśniono w tym [artykule](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z platformy Docker. Ten scenariusz prawdopodobnie nie jest najlepszym rozwiązaniem, jeśli właśnie zaczynasz pracę z platformą Docker, ale jeśli chcesz ustawić określone bity obrazu podstawowego, możesz to zrobić.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3. Tworzenie niestandardowych obrazów platformy Docker osadzania w niej usługi

Dla każdej usługi niestandardowej, która składa się z aplikacji, konieczne będzie utworzenie powiązanego obrazu. Jeśli aplikacja składa się z pojedynczej usługi lub aplikacji sieci Web, będzie potrzebny tylko jeden obraz.

> [!NOTE]
> Podczas wzięcia pod uwagę "przepływu pracy DevOps pętla zewnętrzna" obrazy zostaną utworzone przez zautomatyzowany proces kompilacji po każdym wypchnięciu kodu źródłowego do repozytorium git (ciągłej integracji), dzięki czemu obrazy zostaną utworzone w tym środowisku globalnym z kod źródłowy.
>
> Jednak przed rozważeniem przechodzenia do tej trasy z pętlą zewnętrzną musimy upewnić się, że aplikacja platformy Docker rzeczywiście działa prawidłowo, aby nie wypchnięcia kodu, który może nie działać prawidłowo w systemie kontroli źródła (git itp.).
>
> W związku z tym każdy Deweloper musi najpierw wykonać cały proces pętli wewnętrznej, aby przetestować lokalnie i kontynuować programowanie do momentu, gdy chcą wypchnąć kompletną funkcję lub zmienić system kontroli źródła.

Aby utworzyć obraz w środowisku lokalnym i przy użyciu pliku dockerfile, można użyć polecenia Docker Build, jak pokazano na rysunku 4-25 (można również uruchamiać `docker-compose up --build` aplikacje składające się z kilku kontenerów/usług).

![Dane wyjściowe konsoli dla kompilacji Docker-Zredaguj, pokazujące postęp pobierania obrazów.](./media/image25.png)

**Rysunek 4-25**. Uruchamianie kompilacji platformy Docker

Opcjonalnie, zamiast bezpośrednio `docker build` z poziomu folderu projektu, można najpierw wygenerować folder do wdrożenia z bibliotekami platformy .NET wymaganymi przy użyciu polecenia Uruchom `dotnet publish` , a następnie uruchomić `docker build`polecenie.

W tym przykładzie tworzony jest obraz platformy Docker o `cesardl/netcore-webapi-microservice-docker:first` nazwie`:first` (jest to tag, taki jak określona wersja). Ten krok można wykonać dla każdego niestandardowego obrazu, który trzeba utworzyć dla złożonej aplikacji platformy Docker z kilkoma kontenerami.

Istniejące obrazy można znaleźć w lokalnym repozytorium (na komputerze deweloperskim) przy użyciu polecenia Docker images, jak pokazano na rysunku 4-26.

![Dane wyjściowe konsoli z obrazów platformy Docker, pokazujące istniejące obrazy.](./media/image26.png)

**Rysunek 4-26**. Wyświetlanie istniejących obrazów przy użyciu obrazów platformy Docker

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4. Zdefiniuj usługi w Docker-Compose. yml podczas tworzenia złożonej aplikacji platformy Docker z wieloma usługami

Przy użyciu `docker-compose.yml` pliku można zdefiniować zestaw powiązanych usług, które mają zostać wdrożone jako aplikacja składająca się z poleceniami wdrażania wyjaśnionymi w następnym kroku.

Utwórz ten plik w folderze głównym lub głównym rozwiązania. powinna zawierać zawartość podobną do pokazanej w `docker-compose.yml` tym pliku:

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

W tym konkretnym przypadku ten plik definiuje dwie usługi: usługi sieci Web (usługi niestandardowej) i usługi Redis (popularne usługi pamięci podręcznej). Każda usługa zostanie wdrożona jako kontener, dlatego musimy użyć konkretnego obrazu platformy Docker dla każdego z nich. W przypadku tej konkretnej usługi sieci Web obraz będzie musiał wykonać następujące czynności:

- Kompiluj z pliku dockerfile w bieżącym katalogu

- Przekazuj uwidoczniony port 80 w kontenerze do portu 81 na komputerze hosta

- Zainstaluj katalog projektu na hoście do/Code w kontenerze, dzięki czemu można modyfikować kod bez konieczności ponownego kompilowania obrazu.

- Łączenie usługi sieci Web z usługą Redis

Usługa Redis używa [najnowszego publicznego obrazu Redis](https://hub.docker.com/_/redis/) pobranego z rejestru usługi Docker Hub. [Redis](https://redis.io/) to popularny system pamięci podręcznej dla aplikacji po stronie serwera.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5. Kompilowanie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, wystarczy ją uruchomić, wdrażając ją na hoście platformy Docker (maszynie wirtualnej lub serwerze fizycznym). Jeśli jednak aplikacja składa się z wielu usług, musisz *ją utworzyć*. Zobaczmy różne opcje.

***Opcja A: Uruchamianie pojedynczego kontenera lub usługi***

Obraz platformy Docker można uruchomić przy użyciu polecenia Docker Run, jak pokazano poniżej:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

W przypadku tego konkretnego wdrożenia będziemy przekierowywać żądania wysyłane do portu 80 do wewnętrznego portu 5000. Teraz aplikacja nasłuchuje na porcie zewnętrznym 80 na poziomie hosta.

***Opcja B: Tworzenie i uruchamianie aplikacji z wieloma kontenerami***

W większości scenariuszy przedsiębiorstwa aplikacja platformy Docker będzie składać się z wielu usług. W takich przypadkach można uruchomić `docker-compose up` polecenie (rysunek 4-27), które będzie korzystać z pliku Docker-Compose. yml, który został wcześniej utworzony. Uruchomienie tego polecenia powoduje wdrożenie aplikacji składającej ze wszystkimi powiązanymi kontenerami.

![Dane wyjściowe konsoli z platformy Docker — tworzenie.](./media/image27.png)

**Rysunek 4-27**. Wyniki uruchamiania polecenia "Docker-Zredaguj do"

Po uruchomieniu `docker-compose up`programu aplikacja i powiązane z nim kontenery są wdrażane na hoście platformy Docker, jak pokazano na rysunku 4-28 w reprezentacji maszyny wirtualnej.

![Maszyna wirtualna z uruchomioną funkcją wielokontenera aplikacji.](./media/image28.png)

**Rysunek 4-28**. Maszyna wirtualna z wdrożonymi kontenerami platformy Docker

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6. Testowanie aplikacji platformy Docker (lokalnie, na lokalnej maszynie wirtualnej z płytą CD)

Ten krok będzie się różnić w zależności od tego, co aplikacja działa.

W prostym interfejsie API sieci Web platformy .NET Core "Hello world" wdrożonym jako pojedynczy kontener lub usługa, wystarczy uzyskać dostęp do usługi, podając port TCP określony w pliku dockerfile.

Jeśli localhost nie jest włączona, aby przejść do usługi, Znajdź adres IP dla maszyny za pomocą tego polecenia:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Na hoście platformy Docker Otwórz przeglądarkę i przejdź do tej witryny. powinna zostać wyświetlona aplikacja/usługa, jak pokazano na rysunku 4-29.

![Widok przeglądarki odpowiedzi z localhost/API/Values.](./media/image29.png)

**Rysunek 4-29**. Testowanie aplikacji platformy Docker lokalnie przy użyciu hosta lokalnego

Należy zauważyć, że korzysta on z portu 80, ale wewnętrznie jest przekierowywany do portu 5000, ponieważ został on wdrożony w programie `docker run`, jak wyjaśniono wcześniej.

Można to przetestować przy użyciu ZWINIĘCIEa z terminalu. W przypadku instalacji platformy Docker w systemie Windows domyślny adres IP to 10.0.75.1, jak przedstawiono na rysunku 4-30.

![Dane wyjściowe konsoli od pobrania http://10.0.75.1/API/values z](./media/image30.png)

**Rysunek 4-30**. Lokalne testowanie aplikacji platformy Docker przy użyciu programu ZWINIĘCIE

**Debugowanie kontenera działającego na platformie Docker**

Visual Studio Code obsługuje debugowanie platformy Docker, jeśli używasz środowiska Node. js i innych platform, takich jak kontenery .NET Core.

Można również debugować kontenery .NET Core lub .NET Framework w programie Docker podczas korzystania z programu Visual Studio dla systemu Windows lub Mac, zgodnie z opisem w następnej sekcji.

> [! ZAWARTYCH
>
> Aby dowiedzieć się więcej na temat debugowania kontenerów platformy Docker Node <https://blog.docker.com/2016/07/live-debugging-docker/> . <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>js, przejdź do i.

>[!div class="step-by-step"]
>[Poprzedni](docker-apps-development-environment.md)
>[Następny](visual-studio-tools-for-docker.md)
