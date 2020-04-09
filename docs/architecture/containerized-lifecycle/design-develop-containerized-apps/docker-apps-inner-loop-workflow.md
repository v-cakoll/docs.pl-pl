---
title: Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker
description: Dowiedz się, przepływ pracy "pętla wewnętrzna" do tworzenia aplikacji platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 615cfd08f46609c4e100ea3e72b541fe2c1ae62a
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989015"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker

Przed wyzwoleniem przepływu pracy pętli zewnętrznej obejmującej cały cykl DevOps wszystko zaczyna się na komputerze każdego dewelopera, kodowanie samej aplikacji, przy użyciu preferowanych języków lub platform i testowanie go lokalnie (Rysunek 4-21). Ale w każdym przypadku będziesz miał ważny punkt wspólny, bez względu na język, ramy lub platformy, które wybierzesz. W tym określonym przepływie pracy zawsze tworzysz i testujesz kontenery platformy Docker, ale lokalnie.

![Diagram przedstawiający koncepcję środowiska deweloperskiego pętli wewnętrznej.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**Rysunek 4-21**. Kontekst rozwoju pętli wewnętrznej

Kontener lub wystąpienie obrazu platformy Docker będzie zawierać następujące składniki:

- Wybór systemu operacyjnego (na przykład dystrybucja Linuksa lub Windows)

- Pliki dodane przez dewelopera (na przykład pliki binarne aplikacji)

- Konfiguracja (na przykład ustawienia środowiska i zależności)

- Instrukcje dotyczące procesów uruchamianych przez platformę Docker

Można skonfigurować przepływ pracy tworzenia pętli wewnętrznej, który wykorzystuje docker jako proces (opisane w następnej sekcji). Należy wziąć pod uwagę, że początkowe kroki konfigurowania środowiska nie są uwzględniane, ponieważ wystarczy to zrobić tylko raz.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu kodu programu Visual Studio i interfejsu wiersza polecenia platformy Docker

Aplikacje są wykonane z własnych usług oraz dodatkowych bibliotek (zależności).

Rysunek 4-22 przedstawia podstawowe kroki, które zwykle należy wykonać podczas tworzenia aplikacji platformy Docker, a następnie szczegółowe opisy każdego kroku.

![Diagram przedstawiający siedem kroków, które należy wykonać do utworzenia aplikacji konteneryzowanej.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**Rysunek 4-22**. Przepływ pracy wysokiego poziomu dla cyklu życia konteneryzowanych aplikacji platformy Docker przy użyciu interfejsu wiersza polecenia platformy Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1: Rozpocznij kodowanie w programie Visual Studio Code i utwórz początkową linię bazową aplikacji/usługi

Sposób tworzenia aplikacji jest podobny do sposobu, w jaki to zrobić bez platformy Docker. Różnica polega na tym, że podczas tworzenia wdrażasz i testujesz aplikację lub usługi uruchomione w kontenerach platformy Docker umieszczonych w środowisku lokalnym (takim jak maszyna wirtualna z systemem Linux lub system Windows).

**Konfigurowanie środowiska lokalnego**

Dzięki najnowszym wersjom platformy Docker dla komputerów Mac i Windows tworzenie aplikacji platformy Docker jest łatwiejsze niż kiedykolwiek, a konfiguracja jest prosta.

> [!TIP]
> Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-windows/>Docker dla systemu Windows, przejdź do pliku .
>
>Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-mac/>Docker dla komputerów Mac, przejdź do pliku .

Ponadto potrzebny jest edytor kodu, dzięki czemu można faktycznie tworzyć aplikacji podczas korzystania z interfejsu wiersza polecenia platformy Docker.

Firma Microsoft udostępnia program Visual Studio Code, który jest lekkim edytorem kodu obsługiwanym w [systemach](https://code.visualstudio.com/docs/languages/overview) Windows, Linux i macOS, i zapewnia intellisense obsługę wielu języków (JavaScript, .NET, Go, Java, Ruby, Python i większość nowoczesnych języków), [debugowanie,](https://code.visualstudio.com/Docs/editor/debugging) [integrację z obsługą Git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [rozszerzenia .](https://code.visualstudio.com/docs/extensions/overview) Ten edytor doskonale pasuje do programistów macOS i Linux. W systemie Windows można również używać programu Visual Studio.

> [!TIP]
> Aby uzyskać instrukcje dotyczące instalowania programu Visual Studio Code <https://code.visualstudio.com/docs/setup/setup-overview/>dla systemów Windows, Linux lub macOS, przejdź do pliku .
>
> Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-mac/>Docker dla komputerów Mac, przejdź do pliku .

Można pracować z docker CLI i napisać kod przy użyciu dowolnego edytora kodu, ale `Dockerfile` przy `docker-compose.yml` użyciu programu Visual Studio Code z rozszerzeniem platformy Docker ułatwia tworzenie i pliki w obszarze roboczym. Można również uruchamiać zadania i skrypty z ide kodu programu Visual Studio do wykonywania poleceń platformy Docker przy użyciu interfejsu wiersza polecenia platformy Docker pod spodem.

Rozszerzenie platformy Docker dla programu VS Code zawiera następujące funkcje:

- Automatyczne `Dockerfile` `docker-compose.yml` generowanie plików i ich generowanie

- Wskazówki dotyczące wyróżniania i `docker-compose.yml` `Dockerfile` aktywowania składni dla plików i plików

- IntelliSense (uzupełnienia) `Dockerfile` `docker-compose.yml` dla i plików

- Linting (błędy i ostrzeżenia) dla `Dockerfile` plików

- Integracja z paletą poleceń (F1) dla najpopularniejszych poleceń platformy Docker

- Integracja z Eksploratorem do zarządzania obrazami i kontenerami

- Wdrażanie obrazów z rejestrów kontenerów usługi DockerHub i azure do usługi Azure App Service

Aby zainstalować rozszerzenie platformy Docker, naciśnij klawisze `ext install`Ctrl+Shift+P, wpisz polecenie Zainstaluj rozszerzenie, aby wyświetlić listę rozszerzeń portalu Marketplace. Następnie wpisz **dok.** aby filtrować wyniki, a następnie wybierz rozszerzenie Docker Support, jak pokazano na rysunku 4-23.

![Widok rozszerzenia platformy Docker dla programu VS Code.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Rysunek 4-23**. Instalowanie rozszerzenia platformy Docker w programie Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2: Tworzenie pliku dockerfile powiązanego z istniejącym obrazem (zwykły system operacyjny lub środowiska deweloperów, takie jak .NET Core, Node.js i Ruby)

Musisz na obraz `DockerFile` niestandardowy do zbudowannia i na kontener do wdrożenia. Jeśli aplikacja składa się z jednej usługi niestandardowej, `DockerFile`potrzebujesz jednej . Ale jeśli aplikacja składa się z wielu usług (jak w architekturze `Dockerfile` mikrousług), trzeba będzie jeden na usługę.

Jest `DockerFile` często umieszczany w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, dzięki czemu program Docker wie, jak skonfigurować i uruchomić tę aplikację lub usługę. Możesz utworzyć `DockerFile` i dodać go do projektu wraz z kodem (node.js, .NET Core itp.) lub, jeśli jesteś nowy w środowisku, zapoznaj się z następującą poradą.

> [!TIP]
> Rozszerzenie platformy Docker służy do prowadzenia `Dockerfile` podczas `docker-compose.yml` korzystania z plików i plików związanych z kontenerów platformy Docker. Ostatecznie prawdopodobnie napiszesz tego rodzaju pliki bez tego narzędzia, ale użycie rozszerzenia Platformy Docker jest dobrym punktem wyjścia, który przyspieszy krzywą uczenia się.

Na rysunku 4-24 można zobaczyć, jak plik docker-compose jest dodawany przy użyciu rozszerzenia platformy Docker dla kodu VS.

![Widok konsoli rozszerzenia platformy Docker dla programu VS Code.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Rysunek 4-24**. Pliki docker dodane za pomocą **polecenia Dodaj pliki platformy Docker do obszaru roboczego**

Podczas dodawania pliku dockerfile należy określić, jaki bazowy obraz `FROM mcr.microsoft.com/dotnet/core/aspnet`platformy Docker będzie używany (np. przy użyciu ). Zwykle tworzysz obraz niestandardowy na obrazie podstawowym, który można uzyskać z dowolnego oficjalnego repozytorium w [rejestrze Docker Hub](https://hub.docker.com/) (np. [obraz dla .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) lub obraz dla [node.js).](https://hub.docker.com/_/node/)

***Używanie istniejącego oficjalnego obrazu platformy Docker***

Korzystanie z oficjalnego repozytorium stosu języka z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym rozwoju, testowania i produkcji).

Poniżej przedstawiono przykładowy plik DockerFile dla kontenera .NET Core:

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

W tym przypadku obraz jest oparty na wersji 2.2 oficjalnego obrazu Core Docker ASP.NET (multi-arch `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`dla Linuksa i Windowsa), zgodnie z linią . (Aby uzyskać więcej informacji na ten temat, zobacz [stronę ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) i stronę [.NET Core Docker Image).](https://hub.docker.com/_/microsoft-dotnet-core/)

W pliku DockerFile można również poinstruować program Docker, aby nasłuchiwać portu TCP, który będzie używany w czasie wykonywania (na przykład port 80).

Można określić dodatkowe ustawienia konfiguracji w Dockerfile, w zależności od języka i struktury, którego używasz. Na przykład `ENTRYPOINT` wiersz `["dotnet", "MySingleContainerWebApp.dll"]` z informuje Docker, aby uruchomić aplikację .NET Core. Jeśli używasz SDK i .NET Core`dotnet CLI`CLI ( ) do tworzenia i uruchamiania aplikacji .NET, to ustawienie będzie inne. Kluczowym punktem jest to, że linia ENTRYPOINT i inne ustawienia zależą od języka i platformy, którą wybierzesz dla aplikacji.

> [!TIP]
> Aby uzyskać więcej informacji na temat tworzenia obrazów <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>platformy Docker dla aplikacji .NET Core, przejdź do pliku .
>
> Aby dowiedzieć się więcej o <https://docs.docker.com/engine/tutorials/dockerimages/>tworzeniu własnych obrazów, przejdź do .

**Korzystanie z repozytoriów obrazów wielokołowych**

Pojedyncza nazwa obrazu w repozytorium może zawierać warianty platformy, takie jak obraz systemu Linux i obraz systemu Windows. Ta funkcja umożliwia dostawcom, takim jak Microsoft (twórcom obrazów podstawowych), tworzenie jednego repozytorium obejmującego wiele platform (czyli Linuksa i Windowsa). Na przykład repozytorium [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostępne w rejestrze Docker Hub zapewnia obsługę systemów Linux i Windows Nano Server przy użyciu tej samej nazwy obrazu.

Ciągnięcie obrazu [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hosta systemu Windows ściąga wariant systemu Windows, podczas gdy ciągnięcie tej samej nazwy obrazu z hosta Linuksa ściąga wariant Linuksa.

***Tworzenie obrazu bazowego od podstaw***

Można utworzyć własny obraz bazowy platformy Docker od podstaw, jak wyjaśniono w tym [artykule](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z platformy Docker. Ten scenariusz prawdopodobnie nie jest najlepszy dla Ciebie, jeśli dopiero zaczynasz z platformą Docker, ale jeśli chcesz ustawić określone bity własnego obrazu podstawowego, możesz to zrobić.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3: Tworzenie niestandardowych obrazów platformy Docker osadzających w niej usługę

Dla każdej usługi niestandardowej, która obejmuje aplikację, musisz utworzyć powiązany obraz. Jeśli aplikacja składa się z jednej usługi lub aplikacji internetowej, potrzebujesz tylko jednego obrazu.

> [!NOTE]
> Biorąc pod uwagę "przepływ pracy DevOps w pętli zewnętrznej", obrazy zostaną utworzone przez zautomatyzowany proces kompilacji za każdym razem, gdy wypchniesz kod źródłowy do repozytorium Git (ciągła integracja), więc obrazy zostaną utworzone w tym środowisku globalnym z kodu źródłowego.
>
> Zanim jednak rozważymy przejście do tej trasy w pętli zewnętrznej, musimy upewnić się, że aplikacja platformy Docker działa poprawnie, aby nie wypychać kodu, który może nie działać poprawnie w systemie kontroli źródła (Git itp.).
>
> W związku z tym każdy deweloper najpierw musi wykonać cały proces pętli wewnętrznej, aby przetestować lokalnie i kontynuować rozwój, dopóki nie chce wypchnąć pełną funkcję lub zmiany do systemu kontroli źródła.

Aby utworzyć obraz w środowisku lokalnym i przy użyciu DockerFile, można użyć polecenia kompilacji platformy docker, jak `docker-compose up --build` pokazano na rysunku 4-25 (można również uruchomić dla aplikacji składanych przez kilka kontenerów/usług).

![Zrzut ekranu przedstawiający dane wyjściowe konsoli polecenia kompilacji platformy docker.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Rysunek 4-25**. Uruchamianie kompilacji platformy docker

Opcjonalnie zamiast uruchamiać bezpośrednio `docker build` z folderu projektu, najpierw można wygenerować folder z możliwością `dotnet publish` wdrożenia z `docker build`bibliotekami .NET potrzebnymi za pomocą polecenia uruchom, a następnie uruchomić program .

W tym przykładzie tworzy obraz `cesardl/netcore-webapi-microservice-docker:first` `:first` platformy Docker o nazwie ( jest tagiem, jak określona wersja). Można wykonać ten krok dla każdego obrazu niestandardowego, który należy utworzyć dla złożonej aplikacji platformy Docker z kilkoma kontenerami.

Istniejące obrazy można znaleźć w lokalnym repozytorium (komputerze deweloperskim) za pomocą polecenia obrazy platformy docker, jak pokazano na rysunku 4-26.

![Wyjście konsoli z obrazów dokowane polecenia, pokazując istniejące obrazy.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Rysunek 4-26**. Wyświetlanie istniejących obrazów przy użyciu obrazów dokowych

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4: Zdefiniuj swoje usługi w docker-compose.yml podczas tworzenia złożonej aplikacji platformy Docker z wieloma usługami

Za `docker-compose.yml` pomocą pliku można zdefiniować zestaw powiązanych usług, które mają być wdrożone jako złożona aplikacja z poleceniami wdrażania wyjaśnionymi w następnej sekcji kroku.

Utwórz ten plik w głównym lub głównym folderze rozwiązania; powinien mieć zawartość podobną do `docker-compose.yml` tej pokazanej w tym pliku:

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

W tym konkretnym przypadku ten plik definiuje dwie usługi: usługę sieci web (usługę niestandardową) i usługę redis (popularną usługę pamięci podręcznej). Każda usługa zostanie wdrożona jako kontener, więc musimy użyć konkretnego obrazu platformy Docker dla każdego. W przypadku tej konkretnej usługi sieci web obraz będzie musiał wykonać następujące czynności:

- Kompilacja z pliku DockerFile w bieżącym katalogu

- Prześlij odsłonięty port 80 na kontenerze do portu 81 na komputerze-hoście

- Zamontuj katalog projektu na hoście, aby /code w kontenerze, umożliwiając modyfikowanie kodu bez konieczności przebudowyowania obrazu

- Łączenie usługi sieci web z usługą redis

Usługa redis używa [najnowszego publicznego obrazu redis](https://hub.docker.com/_/redis/) pobranego z rejestru usługi Docker Hub. [redis](https://redis.io/) to popularny system pamięci podręcznej dla aplikacji po stronie serwera.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5: Tworzenie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, wystarczy go uruchomić, wdrażając go na hoście platformy Docker Host (VM lub serwer fizyczny). Jeśli jednak aplikacja składa się z wielu usług, musisz *ją skomponować.* Zobaczmy różne opcje.

***Opcja A: Uruchamianie pojedynczego kontenera lub usługi***

Obraz platformy Docker można uruchomić za pomocą polecenia uruchom docker, jak pokazano poniżej:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

W przypadku tego konkretnego wdrożenia będziemy przekierowywać żądania wysyłane do portu 80 do portu wewnętrznego 5000. Teraz aplikacja nasłuchuje na zewnętrznym porcie 80 na poziomie hosta.

***Opcja B: Komponowanie i uruchamianie aplikacji z wieloma kontenerami***

W większości scenariuszy przedsiębiorstw aplikacja platformy Docker będzie składać się z wielu usług. W takich przypadkach można `docker-compose up` uruchomić polecenie (Rysunek 4-27), które będzie używać pliku docker-compose.yml, który mógł zostać utworzony wcześniej. Uruchomienie tego polecenia wdraża złożoną aplikację ze wszystkimi powiązanymi kontenerami.

![Wyjście konsoli z polecenia docker-compose up.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Rysunek 4-27**. Wyniki uruchamiania polecenia "docker-compose up"

Po uruchomieniu `docker-compose up`można wdrożyć aplikację i jej powiązanych kontenerów do hosta platformy Docker, jak pokazano na rysunku 4-28, w reprezentacji maszyny Wirtualnej.

![Maszyna wirtualna z aplikacjami z wieloma kontenerami.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Rysunek 4-28**. Maszyna wirtualna z wdrożonymi kontenerami platformy Docker

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6: Przetestuj aplikację platformy Docker (lokalnie, w lokalnej maszynie wirtualnej cd)

Ten krok będzie się różnić w zależności od tego, co robi aplikacja.

W prostym interfejsie API sieci Web .NET Core "Hello World" wdrożonym jako pojedynczy kontener lub usługa wystarczy uzyskać dostęp do usługi, udostępniając port TCP określony w pliku DockerFile.

Jeśli localhost nie jest włączony, aby przejść do usługi, znajdź adres IP komputera za pomocą tego polecenia:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Na hoście platformy Docker otwórz przeglądarkę i przejdź do tej witryny; powinien zostać wyświetlony aplikacji/usługi uruchomione, jak pokazano na rysunku 4-29.

![Widok przeglądarki odpowiedzi z localhost/API/values.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Rysunek 4-29**. Testowanie aplikacji platformy Docker lokalnie przy użyciu localhost

Należy pamiętać, że używa portu 80, ale wewnętrznie jest przekierowywany do portu 5000, `docker run`ponieważ tak został wdrożony z , jak wyjaśniono wcześniej.

Można to sprawdzić za pomocą CURL z terminala. W instalacji platformy Docker w systemie Windows domyślny adres IP to 10.0.75.1, jak pokazano na rysunku 4-30.

![Wyjście konsoli z http://10.0.75.1/API/values coraz z curl](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Rysunek 4-30**. Testowanie aplikacji platformy Docker lokalnie przy użyciu CURL

**Debugowanie kontenera uruchomionego w programie Docker**

Visual Studio Code obsługuje debugowanie platformy Docker, jeśli używasz Node.js i innych platform, takich jak kontenery .NET Core.

Można również debugować .NET Core lub .NET Framework kontenerów w programie Docker podczas korzystania z programu Visual Studio dla systemu Windows lub Mac, zgodnie z opisem w następnej sekcji.

> [!TIP]
> Aby dowiedzieć się więcej o debugowaniu kontenerów platformy Docker node.js, zobacz <https://blog.docker.com/2016/07/live-debugging-docker/> i <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.

>[!div class="step-by-step"]
>[Poprzedni](docker-apps-development-environment.md)
>[następny](visual-studio-tools-for-docker.md)
