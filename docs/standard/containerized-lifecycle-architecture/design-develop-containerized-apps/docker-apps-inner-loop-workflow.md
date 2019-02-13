---
title: Przepływ pracy wewnętrznej pętli tworzenia aplikacji platformy Docker
description: Dowiedz się więcej "wewnętrzną pętlę" przepływu pracy dla opracowywania aplikacji platformy Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 03eb4662e55551678105fa9ef25b42cc05c132a5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219091"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Przepływ pracy wewnętrznej pętli tworzenia aplikacji platformy Docker

Przed wyzwoleniem zewnętrzna Pętla przepływu pracy, obejmujące cały DevOps cyklu, rozpoczyna na każdy Deweloper maszynie kodowania samej aplikacji, za pomocą swojego preferowanego języków lub platform i testowanie jej lokalnie (rysunek 4 – 14). Ale w każdym przypadku konieczne będzie bardzo ważna kwestia, niezależnie od tego, jaki język, struktury lub platform wybierz. W tym określonego przepływu pracy są zawsze tworzenia i testowania kontenerów platformy Docker, ale lokalnie.

![](./media/image18.png)

Rysunek 4 – 14: Kontekst wewnętrznej pętli tworzenia kodu

Kontener lub wystąpienia obrazu platformy Docker będzie zawierać tych składników:

-   Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux lub Windows)

-   Pliki dodawane przez dewelopera (na przykład pliki binarne aplikacji)

-   Konfiguracja (na przykład ustawienia środowiska i zależności)

-   Instrukcje dotyczące jakie procesy do uruchomione przez platformy Docker

Możesz skonfigurować przepływ pracy wewnętrznej pętli tworzenia kodu, który korzysta z platformy Docker jako proces (opisany w następnej sekcji). Weź pod uwagę początkowe kroki, aby skonfigurować środowisko nie jest uwzględniony, ponieważ trzeba to zrobić tylko raz.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker

Aplikacje składają się z własnych usług, a także dodatkowe biblioteki (zależności).

Rysunek 4 – 15 przedstawiono podstawowe kroki, które zazwyczaj trzeba przeprowadzić podczas kompilowania aplikacji platformy Docker, następuje szczegółowy opis każdego kroku.

![](./media/image19.png)

Rysunek 4 — 15: Ogólny przepływ pracy dla cyklu życia aplikacji kontenerowych nimi platformy Docker za pomocą interfejsu wiersza polecenia platformy Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1. Rozpocznij kodowanie w programie Visual Studio Code i utworzyć linię bazową początkową aplikacji/usługi

Sposób tworzenia aplikacji jest bardzo podobny sposób, co można zrobić bez platformy Docker. Różnica jest, że podczas tworzenia, są wdrażanie i testowanie aplikacji lub usług działających w kontenerach platformy Docker, umieszczone w środowisku lokalnym (np. maszyny Wirtualnej systemu Linux lub Windows).

**Konfigurowanie środowiska lokalnego**

Najnowsze wersje platformy Docker dla systemów Mac i Windows jest łatwiejsze niż kiedykolwiek do tworzenia aplikacji platformy Docker i konfiguracja jest prosta.

**Więcej informacji o** Aby uzyskać instrukcje na temat konfigurowania Docker for Windows, przejdź do [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).

Aby uzyskać instrukcje na temat konfigurowania platformy Docker dla komputerów Mac, przejdź do <https://docs.docker.com/docker-for-mac/>.

Ponadto należy Edytor kodu, aby faktycznie można opracować aplikację przy użyciu interfejsu wiersza polecenia platformy Docker.

Firma Microsoft udostępnia programu Visual Studio Code, czyli lekkiemu edytorowi kodu, która jest obsługiwana na komputerach Mac, Windows i Linux, oferuje funkcję IntelliSense za pomocą [Obsługa wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python i większość nowoczesnych języków), [debugowania](https://code.visualstudio.com/Docs/editor/debugging), [integracji z usługą Git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [Obsługa rozszerzeń](https://code.visualstudio.com/docs/extensions/overview). Ten edytor to doskonałe rozwiązanie dla deweloperów systemów Mac i Linux. W Windows możesz również można użyć pełnej aplikacji programu Visual Studio.

**Więcej informacji o** Aby uzyskać instrukcje na temat instalowania programu Visual Studio for Windows, Mac lub Linux, przejdź do <https://code.visualstudio.com/docs/setup/setup-overview/>.

Można pracować z interfejsem wiersza polecenia platformy Docker i pisanie kodu za pomocą dowolnego edytora kodu, ale jeśli używasz programu Visual Studio Code, jego sprawia, że ułatwiają tworzenie pliku Dockerfile i pliki docker-compose.yml w obszarze roboczym. Ponadto można uruchamiać zadania programu Visual Studio Code z poziomu środowiska IDE, które wyświetli monit o skrypty, które mogą działać rozwinięciem operacje, przy użyciu interfejsu wiersza polecenia Docker poniżej.

Visual Studio Code jest zapewniana przez rozszerzenie, należy zainstalować. Aby to zrobić, naciśnij klawisze Ctrl + Shift + P, wpisz **zainstalować ext**, a następnie uruchomić rozszerzenia: Zainstaluj rozszerzenie polecenie, aby wyświetlić listę rozszerzeń witryny Marketplace. Następnie wpisz **docker** do filtrowania wyników, a następnie wybierz plik Dockerfile i pliku platformy Docker Compose (yml) rozszerzenia pomocy technicznej, jak pokazano w rysunek 4 – 16.

![](./media/image20.png)

Rysunek 4 – 16: Instalowanie rozszerzenia platformy Docker w programie Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2. Tworzenie pliku DockerFile związane z istniejącego obrazu (zwykły system operacyjny lub środowiskach deweloperskich, takich jak .NET Core, Node.js i Ruby)

Potrzebny będzie plik DockerFile według obrazu niestandardowego do zbudowania i kontenera do wdrożenia, w związku z tym, jeśli aplikacja składa się z jednej usługi niestandardowych, konieczne będzie pojedynczego pliku DockerFile. Ale jeśli aplikacja składa się z wielu usług (tak jak w architekturze mikrousług), musisz mieć jeden plik Dockerfile na usługę.

Plik DockerFile znajduje się zwykle w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, tak że platforma Docker wie, jak skonfigurować i uruchomić tej aplikacji lub usługi. Można tworzyć z pliku DockerFile i dodać go do projektu, wraz z kodu (.NET Core, node.js itp.), lub, jeśli jesteś nowym użytkownikiem środowiska, spójrz na poniższe porady.

> [!TIP]
> Można użyć narzędzia wiersza polecenia o nazwie [yo docker](https://github.com/Microsoft/generator-docker), który szkielety mechanizmów pliki z projektu w języku, wybierz i dodaje wymagane pliki konfiguracji platformy Docker. Zasadniczo, aby ułatwić deweloperów rozpoczynających pracę, tworzy odpowiedni plik DockerFile, docker-compose.yml i inne skojarzone skrypty, aby skompilować i uruchomić kontenerów Docker. Tego generatora yeoman wyświetli monit o na kilka pytań, pytaniem hosta tworzenia wybranego języka i docelowy kontener.

![yo platformy docker](./media/image21.png)

Na przykład rysunek 4-17 pokazuje dwa zrzuty ekranu z terminali w Windows i na komputerze Mac, w obu przypadkach uruchamianie yo platformy docker, która spowoduje wygenerowanie przykładowych projektów kodu (obecnie platformy .NET Core, języka Golang i Node.js jako obsługiwanych języków) już skonfigurowany do pracy początku platformy Docker.

![](./media/image22.PNG)  ![](./media/image23.png)

Rysunek 4-17: yo platformy docker narzędzia polecenia w Windows (po lewej) i na komputerze Mac

Rysunek 4-18 stanowi przykład za pomocą yo platformy docker po utworzeniu istniejącego projektu platformy .NET Core w miejscu, aby być szkielet.

![](./media/image24.PNG)

Rysunek 4 — 18: yo platformy docker przy użyciu istniejącej platformy .NET Core projektu w miejscu

Z pliku DockerFile należy określić, jakie podstawowego obrazu platformy Docker, który ma być używany (np. przy użyciu "od microsoft/dotnet:1.0.0-core"). Zazwyczaj utworzysz obraz niestandardowy na podstawie podstawowy obraz, który można uzyskać z dowolnego oficjalne repozytorium na [rejestru usługi Docker Hub](https://hub.docker.com/) (takich jak [obrazu dla platformy .NET Core](https://hub.docker.com/r/microsoft/dotnet/) lub jeden [dla środowiska Node.js](https://hub.docker.com/_/node/)).

***Opcja A: Użyj istniejącego oficjalny obraz platformy Docker***

Za pomocą oficjalnego repozytorium stos języka z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowanie, testowanie i produkcja).

Poniżej przedstawiono przykładowy plik DockerFile dla kontenera platformy .NET Core:

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

W tym przypadku wykorzystywana jest wersja 1.0.1 oficjalny obraz platformy Docker programu ASP.NET Core dla systemu Linux o nazwie microsoft/aspnetcore:1.0.1. Aby uzyskać więcej informacji, zapoznaj się z [strony obrazu platformy Docker programu ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) i [strony obrazu platformy Docker programu .NET Core](https://hub.docker.com/r/microsoft/dotnet/). Możesz również mogą korzystać z innego obrazu porównywalne, np. węzeł: 4-onbuild dla środowiska Node.js i wiele innych wstępnie skonfigurowanych obrazów dla języków programowania, które są dostępne pod adresem [usługi Docker Hub](https://hub.docker.com/explore/).

W pliku DockerFile trzeba będzie również poinstruować platformy Docker do nasłuchiwania na portach TCP, która będzie używana w czasie wykonywania (np. port 80).

Istnieją inne wiersze konfiguracji, którą można dodać w pliku DockerFile w zależności od języka/platformy, którego używasz, dzięki czemu Docker wie, jak uruchomić aplikację. Na przykład, potrzebny jest wiersz punktu wejścia przy użyciu \["dotnet", "MyCustomMicroservice.dll"\] do uruchamiania aplikacji .NET Core, chociaż może mieć wiele wariantów w zależności od podejście do kompilowania i uruchamiania usługi. Jeśli używasz zestawu SDK i interfejsu wiersza polecenia platformy dotnet do kompilowania i uruchamiania aplikacji .NET może być nieco inne. Mierzenie to, że wiersz punktu wejścia, a także dodatkowe wiersze będą różnić w zależności od języka/platformy, na której możesz wybrać dla swojej aplikacji.

**Więcej informacji o** uzyskać informacji na temat Tworzenie obrazów platformy Docker dla aplikacji platformy .NET Core, przejdź do <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.

Aby dowiedzieć się więcej o tworzeniu własnych obrazów, przejdź do [ https://docs.docker.com/engine/\ samouczki/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).

**Repozytoria obrazu dla wielu platform**

W miarę koncentruje się kontenery Windows jednym repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows. Jest to nowa funkcja dostępna na platformie Docker, który umożliwia dostawcom obejmują wiele platform, takich jak za pomocą pojedynczego repozytorium na [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repozytorium, która jest dostępna w witrynie DockerHub rejestru. Jak funkcja nabierają życia, ściągając ten obraz z hosta Windows będzie pobierać wariant Windows, natomiast ściągania taką samą nazwę obrazu na hoście z systemem Linux każda będzie ściągać wariantów systemu Linux.

***Opcja B: Tworzenie obrazu podstawowego od podstaw***

Można utworzyć własny obraz podstawowy platformy Docker od podstaw, zgodnie z opisem w tym [artykułu](https://docs.docker.com/engine/userguide/eng-image/baseimages/) docker. Jest to scenariusz, który prawdopodobnie nie jest najlepszym rozwiązaniem dla Ciebie, jeśli po prostu rozpoczynasz korzystanie z platformy Docker, ale jeśli chcesz ustawić bity określonego obrazu podstawowego, możesz to zrobić.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3. Tworzenie niestandardowych obrazów platformy Docker osadzania usługi w nim

Dla każdej usługi niestandardowego, który składa się z aplikacji należy utworzyć obraz powiązane. Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, musisz pojedynczego obrazu.

> [!NOTE]
> Biorąc pod uwagę "zewnętrzna pętla DevOps przepływu pracy", obrazy zostanie utworzona przez zautomatyzowanego procesu kompilacji po każdym wypchnięciu kodu źródłowego do repozytorium Git (ciągła integracja), więc obrazy zostanie utworzony w tym środowisku globalnych z usługi Kod źródłowy.

Jednak zanim firma Microsoft uważa, przechodząc do tej trasy zewnętrzna pętla, musimy upewnić się, że aplikację platformy Docker faktycznie działa prawidłowo, aby nie mogą umieścić kod, który może nie działać poprawnie do systemu kontroli źródła (Git itp.).

W związku z tym Każdy deweloper musi najpierw celu cały proces wewnętrzny pętli do testowania lokalnie i kontynuować tworzenie, dopóki nie chcą wypchnąć pełne funkcji lub zmień wartość na system kontroli źródła.

Aby utworzyć obraz w środowisku lokalnym i za pomocą pliku DockerFile, można użyć polecenia kompilacji platformy docker, jak pokazano w rysunek 4-19 (możesz również uruchomić narzędzia docker compose — tworzenie aplikacji poprzez wiele kontenerów/usług).

![](./media/image25.png)

Rysunek 4 — 19: Uruchamianie kompilacji platformy docker

Opcjonalnie, zamiast bezpośredniego uruchamiania docker kompilacji z folderu projektu, można najpierw wygenerować folderu do wdrożenia z bibliotekami .NET potrzebne przy użyciu dotnet wykonywania polecenia publikowania, a następnie uruchom kompilacji platformy docker.

W tym przykładzie, spowoduje to utworzenie obrazu platformy Docker przy użyciu nazwy cesardl/netcore-webapi mikrousługi — docker: pierwszy (: najpierw jest tag, takich jak określonej wersji). Możesz wykonać ten krok dla każdego obrazu niestandardowego, potrzebne do utworzenia złożone aplikacji platformy Docker za pomocą wielu kontenerów.

Można znaleźć istniejących obrazów w lokalnym repozytorium (komputerze deweloperskim) przy użyciu platformy docker polecenie obrazów, jak pokazano w rysunek 4-20.

![](./media/image26.png)

Rysunek 4-20: Wyświetlanie istniejących obrazów przy użyciu obrazów platformy docker

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4. (Opcjonalnie) Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania złożone aplikacji platformy Docker z wieloma usługami

Za pomocą pliku docker-compose.yml można zdefiniować zestaw powiązanych usług, który można wdrożyć jako złożone aplikacji za pomocą poleceń wdrażania opisano w następnej sekcji krok.

Musisz utworzyć ten plik w głównego lub główny folder rozwiązania; w następującym pliku docker-compose.yml powinien mieć podobnej zawartości:

```yml
version: '2'
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

W tym konkretnym przypadku ten plik definiuje dwie usługi: Usługa sieci web (usługa niestandardowa) i usługa redis (usługa popularnej pamięci podręcznej). Każda usługa zostanie wdrożony jako kontener, dlatego musimy użyć konkretnego obrazu platformy Docker dla każdego. Dla tej usługi sieci web określonego obrazu należy wykonać następujące czynności:

-   Twórz z pliku DockerFile w bieżącym katalogu

-   Przekazuj narażonych port 80 w kontenerze na porcie 81 na komputerze hosta

-   Zainstaluj w katalogu projektu na hoście/Code w kontenerze, dzięki czemu można zmodyfikować kod bez konieczności ponownego kompilowania obrazu

-   Połączenia usługi sieci web z usługą redis Cache

Używa usługi redis [najnowszego obrazu publicznego redis](https://hub.docker.com/_/redis/) pobierane z rejestru usługi Docker Hub. [redis](https://redis.io/) to system bardzo popularnej pamięci podręcznej dla aplikacji po stronie serwera.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5. Kompilowanie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, wystarczy uruchomić go przez wdrożenie jej do hosta platformy Docker (maszyny Wirtualnej lub serwera fizycznego). Jednak jeśli Twoja aplikacja składa się z wielu usług, musisz *została utworzona*również. Teraz widzieć różne opcje.

***Opcja A: Uruchom jeden kontener lub usługi***

Obraz platformy Docker można uruchomić przy użyciu platformy docker, uruchom polecenie, jak pokazano poniżej:

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

Należy pamiętać, że dla tego konkretnego wdrożenia, firma Microsoft będzie można przekierowywanie żądania wysyłane do portu 80 na port wewnętrzny 5000. Teraz aplikacja nasłuchuje na porcie zewnętrznym 80 na poziomie hosta.

***Opcja B: Tworzenie i uruchamianie aplikacji wielu kontenerów***

W większości przypadków enterprise aplikację platformy Docker składać się z wielu usług. W takiej sytuacji polecenie można uruchomić narzędzia docker compose się (rysunek 4-21), w której zostanie użyty plik docker-compose.yml, które zostały utworzone wcześniej. Uruchomienie tego polecenia wdraża złożone aplikacji ze wszystkimi jego powiązane kontenerów.

![](./media/image27.png)

Rysunek 4 — 21: Wyniki polecenia "docker-compose up"

Po uruchomieniu docker-compose w górę, wdrażania aplikacji i jej powiązane kontenerów w hoście platformy Docker, jak pokazano w rysunek 4-22 w reprezentacji maszyny Wirtualnej.

![](./media/image28.png)

Rysunek 4-22: Maszyny Wirtualnej przy użyciu kontenerów Docker wdrożonych

Uwaga docker-compose się i platformy docker, uruchom może być wystarczający do testowania kontenerów w środowisku deweloperskim, ale użytkownik nie może on używać ich na wszystkich koordynatorów, takich jak Docker Swarm, Mesosphere DC/OS lub Kubernetes, jeśli są oczekiwane do pracy z klastrami platformy Docker Aby można było skalować w górę. Jeśli używasz klastra, takie jak [trybu Docker Swarm](https://docs.docker.com/engine/swarm/) (dostępne w Docker for Windows i Mac od wersji 1.12), należy wdrożyć i przetestować z dodatkowymi poleceniami, takie jak usługa docker utworzyć dla jednej usługi lub gdy wszystko Wdrażanie aplikacji składających się z kilku kontenerów, za pomocą platformy docker compose pakietu i wdrażana w rozwiązaniu docker myBundleFile, wdrażając złożone aplikacji jako stosu, zgodnie z opisem w artykule [pakiety aplikacji rozproszonych](https://blog.docker.com/2016/06/docker-app-bundle/) docker.

Dla [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) i [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) użyje wdrożenia różnych poleceń i skryptów, jak również.

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6. Testowanie aplikacji platformy Docker (lokalnie, w swojej lokalnej maszyny Wirtualnej dysku CD)

W tym kroku różnią się w zależności od tego, jakie działania aplikacji.

W bardzo prosty .NET Core internetowego interfejsu API "Hello World" wdrażane jako pojedynczy kontener lub usługi czy po prostu potrzebujesz dostępu do usługi, zapewniając portu TCP, określone w pliku DockerFile.

Jeśli host lokalny nie jest włączony, aby przejść do swojej usługi, należy znaleźć adres IP dla maszyny, za pomocą tego polecenia:

adresu ip maszyny platformy docker *nazwa usługi kontenera*

Na hoście platformy Docker Otwórz przeglądarkę i przejdź do tej lokacji; Twoja aplikacja/Usługa jest uruchomiona, powinien zostać wyświetlony, jak pokazano w rysunek 4-23.

![](./media/image29.png)

Rysunek 4-23: Testowanie aplikacji platformy Docker lokalnie przy użyciu localhost

Należy pamiętać, że korzysta ona z portu 80, ale wewnętrznie była nastąpi przekierowanie do portu 5000, ponieważ jest to, jak został wdrożony za pomocą platformy docker, uruchom, jak wyjaśniono wcześniej.

Można to sprawdzić, używając programu CURL z poziomu terminalu. W przypadku instalacji platformy Docker na Windows domyślny adres IP jest 10.0.75.1, jak pokazano w rysunek 4-24.

![](./media/image30.png)

Rysunek 4 – 24: Testowanie aplikacji platformy Docker lokalnie, używając programu CURL

**Debugowanie kontenera uruchomionego w platformy Docker**

Jeśli używasz środowiska Node.js i innych platform, takich jak kontenery platformy .NET Core, programu Visual Studio Code obsługuje debugowania platformy Docker.

Możesz również debugować platformy .NET Core kontenerów platformy Docker przy użyciu programu Visual Studio, zgodnie z opisem w następnej sekcji.

**Więcej informacji:** Aby dowiedzieć się więcej o debugowaniu w kontenerach platformy Docker w środowisku Node.js, przejdź do <https://blog.docker.com/2016/07/live-debugging-docker/> i [ https://blogs.msdn.microsoft.com/\ użytkownika\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-big-Debugging-Updates-Rich-Object-Hover-Conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).

>[!div class="step-by-step"]
>[Poprzednie](docker-apps-development-environment.md)
>[dalej](visual-studio-tools-for-docker.md)