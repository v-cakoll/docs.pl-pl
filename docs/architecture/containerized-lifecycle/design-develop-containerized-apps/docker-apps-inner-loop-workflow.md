---
title: Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker
description: Dowiedz się o przepływie pracy "pętli wewnętrznej" dla tworzenia aplikacji platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 3d2fc889d22dbf02acccfbf9231ad98fca224cff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936811"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker

Przed wyzwolenia przepływu pracy pętli zewnętrznej obejmujących cały cykl DevOps, wszystko zaczyna się na komputerze każdego dewelopera, kodowanie samej aplikacji, przy użyciu preferowanych języków lub platform i testowanie go lokalnie (Rysunek 4-21). Ale w każdym przypadku będziesz mieć ważny wspólny punkt, bez względu na język, ramy lub wybrane platformy. W tym określonym przepływie pracy zawsze tworzysz i testujesz kontenery platformy Docker, ale lokalnie.

![Diagram przedstawiający pojęcie środowiska dewelopera pętli wewnętrznej.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**Rysunek 4-21**. Kontekst rozwoju pętli wewnętrznej

Kontener lub wystąpienie obrazu platformy Docker będzie zawierać następujące składniki:

- Wybór systemu operacyjnego (na przykład dystrybucja Systemu Linux lub Windows)

- Pliki dodane przez dewelopera (na przykład pliki binarne aplikacji)

- Konfiguracja (na przykład ustawienia środowiska i zależności)

- Instrukcje dotyczące procesów uruchamianych przez platformę Docker

Można skonfigurować przepływ pracy tworzenia pętli wewnętrznej, który wykorzystuje platformę Docker jako proces (opisany w następnej sekcji). Należy wziąć pod uwagę, że początkowe kroki, aby skonfigurować środowisko nie są uwzględniane, ponieważ wystarczy zrobić to tylko raz.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu kodu programu Visual Studio i funkcji cli platformy Docker

Aplikacje są składane z własnych usług oraz dodatkowych bibliotek (zależności).

Rysunek 4-22 przedstawia podstawowe kroki, które zwykle należy wykonać podczas tworzenia aplikacji platformy Docker, a następnie szczegółowe opisy każdego kroku.

![Diagram przedstawiający siedem kroków potrzebnych do utworzenia aplikacji konteneryzowanej.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**Rysunek 4-22**. Wysokopoziomowy przepływ pracy dla cyklu życia dla aplikacji konteneryzowanych platformy Docker przy użyciu interfejsu cli platformy Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1: Rozpocznij kodowanie w kodzie programu Visual Studio i utwórz początkową linię bazową aplikacji/usługi

Sposób tworzenia aplikacji jest podobny do sposobu, w jaki to zrobić bez platformy Docker. Różnica polega na tym, że podczas opracowywania wdrażasz i testujesz aplikację lub usługi uruchomione w kontenerach platformy Docker umieszczonych w środowisku lokalnym (takich jak maszyna wirtualna systemu Linux lub windows).

**Konfigurowanie lokalnego środowiska**

Dzięki najnowszym wersjom platformy Docker dla komputerów Mac i systemu Windows tworzenie aplikacji Docker jest łatwiejsze niż kiedykolwiek, a konfiguracja jest prosta.

> [!TIP]
> Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-windows/>Docker dla systemu Windows, przejdź do strony .
>
>Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-mac/>Docker dla komputerów Mac, przejdź do strony .

Ponadto musisz edytor kodu, dzięki czemu można faktycznie rozwijać aplikację przy użyciu interfejsów cli platformy Docker.

Firma Microsoft udostępnia program Visual Studio Code, który jest lekkim edytorem kodu obsługiwanym w systemach Windows, Linux i macOS, i zapewnia programowi IntelliSense [obsługę wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python i najnowocześniejsze języki), [debugowanie,](https://code.visualstudio.com/Docs/editor/debugging) [integrację z obsługą git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [rozszerzeń.](https://code.visualstudio.com/docs/extensions/overview) Ten edytor jest doskonałym rozwiązaniem dla programistów macOS i Linux. W systemie Windows można również użyć programu Visual Studio.

> [!TIP]
> Aby uzyskać instrukcje dotyczące instalowania kodu programu Visual Studio dla <https://code.visualstudio.com/docs/setup/setup-overview/>systemu Windows, Systemu Linux lub systemu macOS, przejdź do strony .
>
> Aby uzyskać instrukcje dotyczące konfigurowania platformy <https://docs.docker.com/docker-for-mac/>Docker dla komputerów Mac, przejdź do strony .

Można pracować z platformą Docker CLI i napisać kod przy użyciu dowolnego edytora kodu, `Dockerfile` `docker-compose.yml` ale za pomocą kodu programu Visual Studio z rozszerzeniem platformy Docker ułatwia tworzenie i pliki w obszarze roboczym. Można również uruchamiać zadania i skrypty z IDE kodu programu Visual Studio do wykonywania poleceń platformy Docker przy użyciu polecenia wiersza polecenia platformy Docker poniżej.

Rozszerzenie platformy Docker dla kodu VS zawiera następujące funkcje:

- Automatyczne `Dockerfile` `docker-compose.yml` i generowanie plików

- Opisy wyróżniania i `docker-compose.yml` aktywowania składni i `Dockerfile` aktywowanie

- IntelliSense (uzupełnienia) `Dockerfile` dla `docker-compose.yml` i plików

- Linting (błędy i ostrzeżenia) dla `Dockerfile` plików

- Integracja z paletą poleceń (F1) dla najpopularniejszych poleceń platformy Docker

- Integracja eksploratora do zarządzania obrazami i kontenerami

- Wdrażanie obrazów z usługi DockerHub i usługi Azure Container Registries w usłudze Azure App Service

Aby zainstalować rozszerzenie platformy Docker, naciśnij `ext install`klawisze Ctrl+Shift+P, wpisz , a następnie uruchom polecenie Zainstaluj rozszerzenie, aby wyświetlić listę rozszerzeń marketplace. Następnie wpisz **docker,** aby filtrować wyniki, a następnie wybierz rozszerzenie docker Support, jak przedstawiono na rysunku 4-23.

![Widok rozszerzenia platformy Docker dla kodu VS.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Rysunek 4-23**. Instalowanie rozszerzenia platformy Docker w kodzie programu Visual Studio

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2: Tworzenie pliku DockerFile powiązanego z istniejącym obrazem (zwykły system operacyjny lub środowiska deweloperów, takie jak .NET Core, Node.js i Ruby)

Do skonstruowania `DockerFile` i wdrożenia należy wykonać obraz niestandardowy. Jeśli aplikacja składa się z jednej usługi niestandardowej, `DockerFile`potrzebujesz jednej usługi. Ale jeśli aplikacja składa się z wielu usług (jak w architekturze mikrousług), trzeba jeden `Dockerfile` na usługę.

Jest `DockerFile` często umieszczany w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, dzięki czemu platforma Docker wie, jak skonfigurować i uruchomić tę aplikację lub usługę. Możesz utworzyć `DockerFile` i dodać go do projektu wraz z kodem (node.js, .NET Core itp.) lub, jeśli jesteś nowy w środowisku, spójrz na następującą końcówkę.

> [!TIP]
> Rozszerzenie platformy Docker służy do prowadzenia `Dockerfile` `docker-compose.yml` użytkownika podczas korzystania z plików związanych z kontenerami platformy Docker. W końcu prawdopodobnie napiszesz tego rodzaju pliki bez tego narzędzia, ale użycie rozszerzenia Docker jest dobrym punktem wyjścia, który przyspieszy krzywą uczenia się.

Na rysunku 4-24 można zobaczyć, jak plik docker-compose jest dodawany przy użyciu rozszerzenia platformy Docker dla kodu VS.

![Widok konsoli rozszerzenia platformy Docker dla kodu VS.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Rysunek 4-24**. Pliki docker dodane przy użyciu **polecenia Dodaj pliki docker do obszaru roboczego**

Po dodaniu pliku DockerFile należy określić, jakiego podstawowego obrazu `FROM mcr.microsoft.com/dotnet/core/aspnet`platformy Docker będziesz używać (np. przy użyciu). Zazwyczaj tworzysz obraz niestandardowy na obrazie podstawowym uzyskanym z dowolnego oficjalnego repozytorium w [rejestrze docker hub](https://hub.docker.com/) (na przykład [obraz dla programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) lub obraz dla [node.js).](https://hub.docker.com/_/node/)

***Używanie istniejącego oficjalnego obrazu platformy Docker***

Korzystanie z oficjalnego repozytorium stosu językowego z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym rozwoju, testowania i produkcji).

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

W tym przypadku obraz jest oparty na wersji 2.2 oficjalnego ASP.NET Core Docker (multi-arch `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`dla Linuksa i Windows), zgodnie z linią . (Aby uzyskać więcej informacji na ten temat, zobacz ASP.NET core [docker image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) strony i [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) strony).

W pliku DockerFile można również poinstruować platformę Docker, aby nasłuchiwać portu TCP, który będzie używany w czasie wykonywania (na przykład port 80).

Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz. Na przykład `ENTRYPOINT` wiersz `["dotnet", "MySingleContainerWebApp.dll"]` z mówi docker do uruchomienia aplikacji .NET Core. Jeśli używasz sdk i .NET Core CLI`dotnet CLI`( ) do tworzenia i uruchamiania aplikacji .NET, to ustawienie będzie inna. Kluczową kwestią jest to, że linia ENTRYPOINT i inne ustawienia zależą od języka i platformy wybranej dla aplikacji.

> [!TIP]
> Aby uzyskać więcej informacji na temat tworzenia obrazów <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>platformy Docker dla aplikacji .NET Core, przejdź do .
>
> Aby dowiedzieć się więcej o tworzeniu <https://docs.docker.com/engine/tutorials/dockerimages/>własnych obrazów, przejdź do .

**Korzystanie z repozytoriów obrazów wielołukowych**

Nazwa pojedynczego obrazu w reppo może zawierać warianty platformy, takie jak obraz systemu Linux i obraz systemu Windows. Ta funkcja umożliwia dostawcom takim jak Microsoft (twórcy obrazów bazowych) tworzenie pojedynczego reponu na wiele platform (czyli Linux i Windows). Na przykład repozytorium [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostępne w rejestrze docker Hub zapewnia obsługę systemów Linux i Windows Nano Server przy użyciu tej samej nazwy obrazu.

Wyciąganie obrazu [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hosta systemu Windows pobiera wariant systemu Windows, podczas gdy pobieranie tej samej nazwy obrazu z hosta Linux ściąga wariant Linuksa.

***Tworzenie obrazu bazowego od podstaw***

Można utworzyć własny obraz podstawowy platformy Docker od podstaw, jak wyjaśniono w tym [artykule](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z platformy Docker. Ten scenariusz prawdopodobnie nie jest najlepszy dla Ciebie, jeśli dopiero zaczynasz z platformą Docker, ale jeśli chcesz ustawić określone bity własnego obrazu podstawowego, możesz to zrobić.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3: Tworzenie niestandardowych obrazów platformy Docker osadzania usługi w nim

Dla każdej usługi niestandardowej, która składa się z aplikacji, należy utworzyć powiązany obraz. Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci Web, potrzebujesz tylko jednego obrazu.

> [!NOTE]
> Biorąc pod uwagę "przepływ pracy DevOps w pętli zewnętrznej", obrazy będą tworzone przez zautomatyzowany proces kompilacji za każdym razem, gdy wypchniesz kod źródłowy do repozytorium Git (Ciągła integracja), dzięki czemu obrazy zostaną utworzone w tym środowisku globalnym z kodu źródłowego.
>
> Ale zanim rozważymy przejście do tej trasy pętli zewnętrznej, musimy upewnić się, że aplikacja Docker faktycznie działa poprawnie, tak aby nie wypychać kodu, który może nie działać poprawnie do systemu kontroli źródła (Git, itp.).
>
> W związku z tym każdy deweloper najpierw musi wykonać cały proces pętli wewnętrznej, aby przetestować lokalnie i kontynuować rozwój, dopóki nie będzie chciał wypchnąć pełną funkcję lub zmienić system kontroli źródła.

Aby utworzyć obraz w środowisku lokalnym i za pomocą DockerFile, można użyć polecenia kompilacji platformy docker, jak pokazano na rysunku 4-25 (można również uruchomić `docker-compose up --build` dla aplikacji złożonych przez kilka kontenerów/usług).

![Zrzut ekranu przedstawiający dane wyjściowe konsoli polecenia kompilacji platformy docker.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Rysunek 4-25**. Uruchamianie kompilacji platformy docker

Opcjonalnie zamiast bezpośrednio `docker build` uruchamiać z folderu projektu, można najpierw wygenerować folder wdrażalny z `dotnet publish` bibliotekami .NET potrzebnymi przy użyciu polecenia uruchom, a następnie uruchomić `docker build`.

W tym przykładzie tworzy obraz `cesardl/netcore-webapi-microservice-docker:first` platformy Docker o nazwie (jest`:first` tagiem, jak określona wersja). Można wykonać ten krok dla każdego niestandardowego obrazu, który należy utworzyć dla skomponowanej aplikacji platformy Docker z kilku kontenerów.

Istniejące obrazy można znaleźć w lokalnym repozytorium (komputerze deweloperskim) za pomocą polecenia obrazy dokowane, jak pokazano na rysunku 4-26.

![Wyjście konsoli z obrazów dokatki poleceń, pokazujące istniejące obrazy.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Rysunek 4-26**. Wyświetlanie istniejących obrazów przy użyciu obrazów dokowane

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4: Definiowanie usług w pliku docker-compose.yml podczas tworzenia skomponowanej aplikacji platformy Docker z wieloma usługami

Za `docker-compose.yml` pomocą pliku można zdefiniować zestaw powiązanych usług, które mają zostać wdrożone jako złożona aplikacja z poleceniami wdrażania wyjaśnionymi w sekcji następny krok.

Utwórz ten plik w głównym lub głównym folderze rozwiązania; powinien mieć treści podobne do `docker-compose.yml` tych pokazanych w tym pliku:

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

W tym konkretnym przypadku ten plik definiuje dwie usługi: usługę sieci web (usługa niestandardowa) i usługę redis (popularną usługę pamięci podręcznej). Każda usługa zostanie wdrożona jako kontener, więc musimy użyć konkretnego obrazu platformy Docker dla każdego. W przypadku tej konkretnej usługi sieci Web obraz będzie musiał wykonać następujące czynności:

- Tworzenie z pliku DockerFile w bieżącym katalogu

- Prześlij odsłonięty port 80 na kontenerze do portu 81 na maszynie hosta

- Zamontuj katalog projektu na hoście do /code w kontenerze, umożliwiając modyfikowanie kodu bez konieczności odbudowywania obrazu

- Połącz usługę sieci web z usługą redis

Usługa redis używa [najnowszego publicznego obrazu redis](https://hub.docker.com/_/redis/) pobieranego z rejestru docker hub. [redis](https://redis.io/) to popularny system pamięci podręcznej dla aplikacji po stronie serwera.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5: Tworzenie i uruchamianie aplikacji Platformy Docker

Jeśli aplikacja ma tylko jeden kontener, wystarczy uruchomić go, wdrażając go na hoście platformy Docker (maszynie wirtualnej lub serwerze fizycznym). Jeśli jednak aplikacja składa się z wielu usług, należy *ją również skomponować.* Zobaczmy różne opcje.

***Opcja A: Uruchamianie pojedynczego kontenera lub usługi***

Obraz platformy Docker można uruchomić za pomocą polecenia docker run, jak pokazano poniżej:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

W przypadku tego konkretnego wdrożenia będziemy przekierowywać żądania wysłane do portu 80 do portu wewnętrznego 5000. Teraz aplikacja nasłuchuje na zewnętrznym porcie 80 na poziomie hosta.

***Opcja B: Tworzenie i uruchamianie aplikacji z wieloma kontenerami***

W większości scenariuszy przedsiębiorstwa aplikacja platformy Docker będzie składać się z wielu usług. W takich przypadkach można `docker-compose up` uruchomić polecenie (Rysunek 4-27), które będzie używać pliku docker-compose.yml, który został utworzony wcześniej. Uruchomienie tego polecenia wdraża skomponowaną aplikację ze wszystkimi powiązanymi kontenerami.

![Dane wyjściowe konsoli z polecenia docker-compose up.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Rysunek 4-27**. Wyniki uruchamiania polecenia "docker-compose up"

Po uruchomieniu `docker-compose up`należy wdrożyć aplikację i powiązane z nią kontenery w hoście platformy Docker, jak pokazano na rysunku 4-28, w reprezentacji maszyny Wirtualnej.

![Maszyna wirtualna z aplikacjami wielokontenerowymi.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Rysunek 4-28**. Maszyna wirtualna z wdrożonymi kontenerami platformy Docker

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6: Przetestuj aplikację platformy Docker (lokalnie, w lokalnej maszynie wirtualnej CD)

Ten krok będzie się różnić w zależności od tego, co aplikacja robi.

W prostym interfejsie API sieci Web programu .NET Core "Hello World" wdrożonym jako pojedynczy kontener lub usługa wystarczy uzyskać dostęp do usługi, udostępniając port TCP określony w pliku DockerFile.

Jeśli host lokalny nie jest włączony, aby przejść do usługi, znajdź adres IP komputera za pomocą tego polecenia:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Na hoście platformy Docker otwórz przeglądarkę i przejdź do tej witryny; powinna zostać wyświetlona uruchomiona aplikacja/usługa, jak pokazano na rysunku 4-29.

![Widok przeglądarki odpowiedzi z localhost/API/wartości.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Rysunek 4-29**. Testowanie aplikacji platformy Docker lokalnie przy użyciu localhost

Należy pamiętać, że używa portu 80, ale wewnętrznie jest przekierowywany do portu 5000, `docker run`ponieważ tak został wdrożony z , jak wyjaśniono wcześniej.

Można to sprawdzić za pomocą CURL z terminala. W instalacji platformy Docker w systemie Windows domyślnyadres IP to 10.0.75.1, jak przedstawiono na rysunku 4-30.

![Wyjście konsoli z http://10.0.75.1/API/values uzyskania z curl](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Rysunek 4-30**. Testowanie aplikacji Platformy Docker lokalnie przy użyciu curl

**Debugowanie kontenera działającego na platformie Docker**

Visual Studio Code obsługuje debugowanie platformy Docker, jeśli używasz Node.js i innych platform, takich jak kontenery .NET Core.

Można również debugować kontenery .NET Core lub .NET Framework w platformie Docker podczas korzystania z programu Visual Studio dla systemu Windows lub Mac, zgodnie z opisem w następnej sekcji.

> [!TIP]
> Aby dowiedzieć się więcej na temat debugowania kontenerów platformy Docker węzła js, zobacz <https://blog.docker.com/2016/07/live-debugging-docker/> i <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.

>[!div class="step-by-step"]
>[Poprzedni](docker-apps-development-environment.md)
>[następny](visual-studio-tools-for-docker.md)
