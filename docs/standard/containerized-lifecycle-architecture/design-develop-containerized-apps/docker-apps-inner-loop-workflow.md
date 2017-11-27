---
title: "Przepływ pracy pętli wewnętrzny programowanie aplikacji Docker"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 30c10b2407ab643e04eb44c00ddf4a89d369a025
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Przepływ pracy pętli wewnętrzny programowanie aplikacji Docker

Aby mogło nastąpić wyzwolenie przepływu pracy zewnętrznego pętli obejmujących całą DevOps cykl, zaczyna na każdy Deweloper maszyny, kodowania samej aplikacji, za pomocą jego preferowanych języków lub platform i testowanie go lokalnie (14 4 rysunek). Jednak w każdym przypadku należy bardzo ważnym, niezależnie od tego, jakie języka, framework i platform wybierz. W tym określonego przepływu pracy są zawsze programują i testują rozwiązania Docker kontenerów, ale lokalnie.

![](./media/image18.png)

Rysunek 4 — 14: wewnętrzny pętli programowanie kontekstu

Kontener lub wystąpienia obrazu Docker będzie zawierać następujące składniki:

-   Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux lub Windows)

-   Pliki dodane przez dewelopera (na przykład pliki binarne aplikacji)

-   Konfiguracja (na przykład ustawienia środowiska i zależności)

-   Instrukcje dotyczące przetwarza uruchamianie Docker

Można skonfigurować przepływ pracy programowanie pętli wewnętrzny, który wykorzystuje Docker jako proces (opisany w następnej sekcji). Uwzględniać początkowe kroki, aby skonfigurować środowisko nie jest uwzględnione, ponieważ musisz to zrobić tylko raz.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Tworzenie tylko jednej aplikacji w kontenerze Docker przy użyciu programu Visual Studio Code i interfejsu wiersza polecenia Docker

Aplikacje składają się z własnych usług oraz dodatkowych bibliotek (zależności).

Rysunek 4 – 15 przedstawiono podstawowe kroki, które zwykle trzeba przeprowadzić podczas kompilowania aplikacji Docker następuje szczegółowy opis każdego kroku.

![](./media/image19.png)

Rysunek 4 — 15: ogólny przepływ pracy cyklu życia aplikacji Docker konteneryzowanych za pomocą interfejsu wiersza polecenia Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1: Rozpoczęcie kodowania w programie Visual Studio Code i utworzyć odniesienia początkowej aplikacji/usługi

Sposób tworzenia aplikacji jest bardzo podobny sposób jak bez Docker. Różnica polega na tym że podczas tworzenia, wdrażania i testowania aplikacji lub usługi działające w kontenerach Docker umieszczone w środowisku lokalnym (na przykład maszyny Wirtualnej systemu Linux lub Windows).

**Konfigurowanie środowiska lokalnego**

Najnowsze wersje Docker dla systemów Mac i systemu Windows jest łatwiejsze niż kiedykolwiek do tworzenia aplikacji Docker i Instalator jest proste.

**Więcej informacji o** instrukcje dotyczące konfigurowania Docker dla systemu Windows, przejdź do [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).

Aby uzyskać instrukcje na temat konfigurowania Docker dla komputerów Mac, przejdź do <https://docs.docker.com/docker-for-mac/>.

Ponadto należy edytora kodu, dzięki czemu można faktycznie opracowywanie aplikacji przy użyciu interfejsu wiersza polecenia Docker.

Firma Microsoft udostępnia Visual Studio Code, czyli edytorze niewielki kod, który jest obsługiwany w Mac, Windows i Linux i udostępnia IntelliSense z [obsługi wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, przejdź, Java, Ruby, Python i większość Nowoczesne języki), [debugowania](https://code.visualstudio.com/Docs/editor/debugging), [integracji z usługą Git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [Obsługa rozszerzeń](https://code.visualstudio.com/docs/extensions/overview). Ten edytor jest doskonałym dopasowania dla deweloperów komputerów Mac i Linux. W systemie Windows również służy pełnej aplikacji Visual Studio.

**Więcej informacji o** instrukcje dotyczące instalowania programu Visual Studio dla systemu Windows, Mac lub Linux, przejdź do [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).

Możesz pracować z interfejsu wiersza polecenia Docker i wpisz swój kod, za pomocą dowolnego edytora kodu, ale jeśli używasz programu Visual Studio Code pozwala ułatwiają tworzenie plik Dockerfile i pliki docker-compose.yml w obszarze roboczym. Ponadto można uruchamiać zadania programu Visual Studio Code z IDE, która wyświetli monit o skrypty, które mogą być uruchomione rozwinięciem operacji za pomocą interfejsu wiersza polecenia Docker poniżej.

Visual Studio Code są udostępniane przez rozszerzenie, należy zainstalować. Aby to zrobić, naciśnij kombinację klawiszy Ctrl + Shift + P, wpisz **zainstalować ext**, a następnie uruchom rozszerzenia: polecenia instalowania rozszerzenia można wyświetlić listy rozszerzeń witryny Marketplace. Następnie wpisz **docker** Aby filtrować wyniki, a następnie wybierz plik Dockerfile i Docker Compose pliku (yml) rozszerzenia obsługi, jak pokazano w rysunek 4-16.

![](./media/image20.png)

Rysunek 4 – 16: Instalowanie rozszerzenia Docker w kodzie programu Visual Studio

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2: Tworzenie plik DockerFile związane z istniejącego obrazu (zwykły system operacyjny lub deweloperów środowiskach, takich jak .NET Core, Node.js i Ruby)

Konieczne będzie plik DockerFile dla poszczególnych niestandardowy obraz ma zostać utworzony i kontener do wdrożenia, w związku z tym, jeśli aplikacja składa się z jednej usługi niestandardowe, konieczne będzie pojedynczy plik DockerFile. Jednak jeśli aplikacja składa się z wielu usług (jak architektura mikrousług), będziesz potrzebować co plik Dockerfile dla danej usługi.

Plik DockerFile zazwyczaj znajduje się w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, tak że Docker wie, jak skonfigurować i uruchomić tej aplikacji lub usługi. Można tworzyć z plik DockerFile i dodaj go do projektu wraz z kodu (node.js, .NET Core itp.), lub jeśli dopiero zaczynasz do środowiska, Przyjrzyjmy się następujące porady.

> [!TIP]
> Można użyć narzędzia wiersza polecenia o nazwie [yo docker](https://github.com/Microsoft/generator-docker), który rusztowania pliki z projektu w języku, wybierz i dodaje wymagane pliki konfiguracji Docker. Zasadniczo, aby pomóc deweloperom wprowadzenie, tworzy odpowiedni plik DockerFile, docker-compose.yml i inne skojarzone skrypty, aby skompilować i uruchomić kontenerów Docker. Tego generatora narzędzia yeoman wyświetli monit o na kilka pytań, prosząc programowanie wybranego hosta kontenera języka i docelowego.

![yo docker](./media/image21.png)

Na przykład rysunek 4-17 zawiera dwa zrzuty ekranu z terminali systemu Windows i na komputerze Mac, w obu przypadkach systemem yo docker, co spowoduje, że przykładowy kod projektów (obecnie .NET Core Golang i Node.js jako obsługiwanych języków) już skonfigurowana do pracy w w górnej części Docker.

![](./media/image22.PNG)  ![](./media/image23.png)

Rysunek 4 — 17: yo docker narzędzia polecenia w systemie Windows (lewych) i na komputerze Mac

Rysunek 4-18 stanowi przykład przy użyciu yo docker po miejscowej można szkieletu istniejącego projektu platformy .NET Core.

![](./media/image24.PNG)

Rysunek 4 — 18: yo docker z istniejących .NET Core projektu w miejscu

Z plik DockerFile możesz określić podstawową obrazów Docker należy używać (np. przy użyciu "od microsoft/dotnet:1.0.0-core"). Zazwyczaj utworzysz niestandardowego obrazu na podstawowy obraz, który można uzyskać z dowolnego oficjalnego repozytorium pod adresem [rejestru Centrum Docker](https://hub.docker.com/) (takich jak [obrazu dla platformy .NET Core](https://hub.docker.com/r/microsoft/dotnet/) lub [dla środowiska Node.js](https://hub.docker.com/_/node/)).

***Opcja A: użycie istniejącego obrazu platformy Docker urzędowego***

Użycie oficjalnego repozytorium stosu języka z numerem wersji gwarantuje, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowania, testowania i produkcji).

Poniżej przedstawiono przykładowy plik DockerFile kontenera .NET Core.

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

W takim przypadku go używa wersji 1.0.1 oficjalnego obrazu platformy ASP.NET Core Docker Linux o nazwie microsoft/aspnetcore:1.0.1. Aby uzyskać szczegółowe informacje, zapoznaj się [strony platformy ASP.NET Core Docker obrazu](https://hub.docker.com/r/microsoft/aspnetcore/) i [strona .NET Core Docker obrazu](https://hub.docker.com/r/microsoft/dotnet/). Możesz również może używać innego obrazu można porównywać pod względem, takich jak węzła: 4-onbuild dla środowiska Node.js lub wielu innych obrazów wstępnie skonfigurowane dla języków programowania, które są dostępne pod adresem [Centrum Docker](https://hub.docker.com/explore/).

W plik DockerFile należy także poinstruować Docker do nasłuchiwania na portach TCP, która będzie używana w czasie wykonywania (np. port 80).

Istnieją inne wiersze konfiguracji, które można dodać w plik DockerFile w zależności od języka/framework, którego używasz, więc Docker potrafi uruchomić aplikację. Na przykład, potrzebny jest wiersz punktu wejścia z \["dotnet", "MyCustomMicroservice.dll"\] do uruchamiania aplikacji .NET Core, chociaż może mieć wiele wariantów w zależności od rozwiązania do tworzenia i uruchamiania usługi. Jeśli używasz zestawu SDK i interfejsu wiersza polecenia platformy dotnet tworzenie i uruchamianie aplikacji .NET, może być nieco inne. Mierzenie jest, że ENTRYPOINT wiersza oraz dodatkowe wiersze będą różne w zależności od języka/platformy wybrane dla aplikacji.

**Więcej informacji o** dla informacji o tworzeniu obrazy usługi Docker dla aplikacji .NET Core, przejdź do <https://docs.microsoft.com/dotnet/articles/core/docker/building-net-docker-images>.

Aby dowiedzieć się więcej na temat tworzenia własnych obrazów, przejdź do [https://docs.docker.com/engine/ \samouczki/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).

**Repozytoria obrazu dla wielu platform**

Jak kontenery Windows staną się bardziej powszechnie, jednym repozytorium mogą zawierać wariantów platform, takich jak obraz systemu Linux i Windows. Jest to nowa funkcja dostępna w Docker, który umożliwia dostawcom obejmują wiele platform, takich jak za pomocą jednego repozytorium [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repozytorium, która jest dostępna w DockerHub rejestru. Jak funkcja zawiera aktywności, ściąganie tego obrazu na hoście systemu Windows będzie pobierać wariant systemu Windows, natomiast ściąganie taką samą nazwę obrazu z hosta systemu Linux będzie pobierać wariant systemu Linux.

***Opcja B: tworzenia obrazu podstawowego od podstaw***

Można utworzyć własny obraz podstawowy Docker od początku, zgodnie z objaśnieniem w tym [artykułu](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Docker. Ten scenariusz, który prawdopodobnie nie jest najważniejsze dla Ciebie, jeśli jest uruchamiany tylko z rozwiązaniem Docker z jest, ale jeśli chcesz ustawić określone bity obrazu podstawowego, możesz to zrobić.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3: Tworzenie niestandardowe obrazy usługi Docker osadzanie w nim usługi

Dla każdej usługi niestandardowych, który składa się z aplikacji musisz utworzyć obraz pokrewne. Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, musisz tylko jeden obraz.

> [!NOTE]
> Biorąc pod uwagę "zewnętrzne pętli DevOps przepływu pracy", obrazy zostaną utworzone przez proces kompilacji automatycznych zawsze, gdy wypychanie kodu źródłowego do repozytorium Git (ciągłej integracji), obrazów, które zostaną utworzone w tym globalnych środowisku z sieci Kod źródłowy.

Jednak zanim możemy należy wziąć pod uwagę będzie tego trasy zewnętrzne pętli, musimy upewnij się, że aplikacja Docker faktycznie działa prawidłowo, aby ich nie umieścić kod, który może nie działać poprawnie do systemu kontroli źródła (Git, itp.).

W związku z tym Każdy deweloper musi najpierw celu cały proces wewnętrzny pętli do testowania lokalnie i kontynuować tworzenie dopóki mają push pełną funkcji lub zmiany z systemu kontroli źródła.

Do utworzenia obrazu w środowisku lokalnym i za pomocą plik DockerFile, służy polecenie kompilacji docker, jak pokazano w rysunek 4-19 (można także uruchomić rozwiązania docker compose — tworzenie aplikacji składane przez kilka kontenery/usługi).

![](./media/image25.png)

Rysunek 4 — 19: uruchomioną kompilację docker

Opcjonalnie, zamiast bezpośredniego uruchamiania docker kompilacji z folderu projektu, najpierw można wygenerować folderu do wdrożenia z bibliotekami .NET potrzebne przy użyciu wykonywania dotnet publikowania polecenia, a następnie uruchom kompilacji docker.

W tym przykładzie, spowoduje to utworzenie obrazu Docker z nazwy cesardl/netcore-webapi mikrousługi-docker: pierwszy (: najpierw jest znacznik, podobnie jak w określonej wersji). Można wykonać ten krok dla każdego niestandardowego obrazu potrzebnych do tworzenia aplikacji Docker składać się z kilku kontenerów.

Można znaleźć istniejących obrazów w lokalnym repozytorium (komputerze deweloperskim) przy użyciu rozwiązania docker polecenia obrazów, zgodnie z opisami w rysunek 4-20.

![](./media/image26.png)

Rysunek 4-20: wyświetlanie istniejących obrazów za pomocą obrazy usługi docker

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4: Definiowanie (opcjonalnie) usług w rozwiązaniu docker-compose.yml podczas kompilowania aplikacji przez Docker składać się z wieloma usługami

Plik docker-compose.yml można zdefiniować zestawu usług wdrażanych jako aplikacja składa z poleceń wdrażania szczegółowo w następnej sekcji krok.

Musisz utworzyć ten plik w sieci głównym lub głównego folderu rozwiązania; powinien mieć zawartość podobny do następującego pliku docker-compose.yml:

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

W tym przypadku plik definiuje dwie usługi: Usługa sieci web (usługa niestandardowych) i usługę redis (usługa popularnych pamięci podręcznej). Każdej usługi zostanie wdrożony jako kontener, więc musimy używane dla każdego konkretnego obrazu Docker. Dla tej usługi sieci web określonego obrazu należy wykonać następujące czynności:

-   Konstruuj z plik DockerFile w bieżącym katalogu

-   Przekazuj dostępnego portu 80 kontenera do portu 81 na komputerze hosta

-   Katalogu projektu instalacji na hoście /code w kontenerze, dzięki czemu można zmodyfikować kod bez konieczności odbudować obrazu

-   Łączenie z usługą redis usługi sieci web

Używane przez usługę redis [najnowsze obrazu publicznego redis](https://hub.docker.com/_/redis/) pobierane z rejestru Centrum Docker. [redis](http://redis.io/) to system bardzo popularny pamięci podręcznej dla aplikacji po stronie serwera.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5: Tworzenie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, wystarczy uruchomić go przez wdrożenie jej (maszyny Wirtualnej lub serwerze fizycznym) hosta Docker. Jednak jeśli aplikacja składa się z wielu usług, musisz *została utworzona*, zbyt. Zobaczmy różne opcje.

***Opcja A: uruchom jeden kontener lub usługi***

Obraz Docker można uruchomić przy użyciu rozwiązania docker, uruchom polecenie, jak pokazano poniżej:

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

Należy pamiętać, że dla tego konkretnego wdrożenia, firma Microsoft będzie można Przekierowywanie żądań wysyłane do portu 80 do wewnętrznego portu 5000. Teraz aplikacja nasłuchuje na porcie zewnętrznym 80 na poziomie hosta.

***Opcja B: tworzenia i uruchamiania aplikacji kontenera wielu***

W większości przypadków przedsiębiorstwa aplikacji Docker składać się z wielu usług. W tych przypadkach można uruchomić polecenie rozwiązania docker compose górę (rysunek 4-21), którego użyje plik docker-compose.yml, które zostały utworzone wcześniej. Uruchomienie tego polecenia wdraża składa aplikacji ze wszystkimi jego powiązanych kontenerów.

![](./media/image27.png)

Rysunek 4 — 21: Wyniki uruchomienia polecenia "docker tworzą się"

Po uruchomieniu programu docker-tworzą w górę, wdrażania aplikacji i jej powiązane kontenerów do hosta Docker, zgodnie z opisami 4 rysunek-22, w reprezentacji maszyny Wirtualnej.

![](./media/image28.png)

Rysunek 4 — 22: maszyna wirtualna o wdrożone kontenery Docker

Uwaga docker tworzą się i docker Uruchom może być wystarczająca do testowania kontenerów w środowisku projektowania, ale nie można na przykład je na wszystkich jeśli są oczekiwane do pracy z klastrami Docker i orchestrators, takich jak Docker Swarm, Mesosphere DC/OS lub Kubernetes Aby można było skalowanie w górę. Jeśli używasz klastra, takie jak [Docker Swarm tryb](https://docs.docker.com/engine/swarm/) (dostępne w Docker dla systemu Windows i Mac od wersji 1.12), należy do wdrożenia i przetestowania przy użyciu dodatkowych poleceń, takich jak usługa docker utworzyć dla jednej usługi lub podczas pracy Wdrażanie aplikacji składający się z kilku kontenerów, przy użyciu rozwiązania docker compose pakietu i docker wdrażanie myBundleFile, wdrażając składa aplikacji jako stosu, zgodnie z opisem w artykule [pakiety aplikacji rozproszonych](https://blog.docker.com/2016/06/docker-app-bundle/) z Docker.

Aby uzyskać [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) i [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) użyje inne wdrożenie poleceń i skryptów, jak również.

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6: Przetestować aplikację Docker (lokalnie, w sieci lokalnej maszyny Wirtualnej CD)

Ten krok będą się różnić w zależności od czynności aplikacji.

W bardzo proste .NET Core interfejsu API sieci Web "Hello World" wdrożony jako jeden kontener lub usługi czy wystarczy uzyskać dostęp do usługi, zapewniając określonym w plik DockerFile porcie TCP.

Jeśli host lokalny nie jest włączony, przejdź do usługi, znaleźć adres IP dla komputera, za pomocą tego polecenia:

ip komputera docker *your nazwa kontenera*

Na hoście Docker Otwórz przeglądarkę i przejdź do tej lokacji; powinny pojawić się aplikacji/usługi uruchomione, jak pokazano w rysunek 4-23.

![](./media/image29.png)

Rysunek 4 — 23: testowanie aplikacji Docker lokalnie za pomocą localhost

Należy pamiętać, że używa portu 80, ale wewnętrznie został nastąpi przekierowanie do portu 5000, ponieważ jest to, jak została wdrożona z docker uruchomić, zgodnie z opisem.

Można to sprawdzić za pomocą CURL z terminala. W instalacji Docker w systemie Windows domyślny adres IP jest 10.0.75.1, jak pokazano w rysunek 4 do 24.

![](./media/image30.png)

Rysunek 4 – 24: testowanie aplikacji Docker lokalnie, przy użyciu programu CURL

**Debugowanie kontenera systemem Docker**

Visual Studio Code obsługuje Docker debugowania, jeśli używasz środowiska Node.js i innych platform, takich jak kontenery .NET Core.

Możesz również debugować kontenerów .NET Core w Docker przy użyciu programu Visual Studio, zgodnie z opisem w następnej sekcji.

**Aby dowiedzieć się więcej:** Aby dowiedzieć się więcej na temat debugowania kontenery Node.js Docker, <https://blog.docker.com/2016/07/live-debugging-docker/> i [https://blogs.msdn.microsoft.com/ \ użytkownika\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).


>[!div class="step-by-step"]
[Poprzednie] (docker aplikacje development-environment.md) [dalej] (visual-studio narzędzia do docker.md)
