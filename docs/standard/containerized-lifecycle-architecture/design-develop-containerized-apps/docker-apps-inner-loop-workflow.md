---
title: Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker
description: Dowiedz się więcej "wewnętrzną pętlę" przepływu pracy dla opracowywania aplikacji platformy Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 36fcf5769376375854c2a2631e26e8b136df0de6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050569"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Przepływ pracy wewnętrznej pętli tworzenia kodu dla aplikacji platformy Docker

Przed wyzwoleniem zewnętrzna Pętla przepływu pracy, obejmujące cały DevOps cyklu, rozpoczyna na każdy Deweloper maszynie kodowania samej aplikacji, za pomocą swojego preferowanego języków lub platform i testowanie jej lokalnie (rysunek 4-21). Jednak w każdym przypadku, będziesz mieć to ważny punkt, niezależnie od tego, jaki język, struktury lub platform wybierz. W tym określonego przepływu pracy zawsze tworzenia i testowania kontenerów platformy Docker, ale lokalnie.

![Krok 1 — Kod/uruchomienia/debugowania](./media/image18.png)

**Rysunek 4-21**. Kontekst wewnętrznej pętli tworzenia kodu

Kontener lub wystąpienia obrazu platformy Docker będzie zawierać tych składników:

-   Wybór systemu operacyjnego (na przykład dystrybucji systemu Linux lub Windows)

- Pliki dodawane przez dewelopera (na przykład pliki binarne aplikacji)

-   Konfiguracja (na przykład ustawienia środowiska i zależności)

- Instrukcje dotyczące jakie procesy do uruchomione przez platformy Docker

Możesz skonfigurować przepływ pracy wewnętrznej pętli tworzenia kodu, który korzysta z platformy Docker jako proces (opisany w następnej sekcji). Należy wziąć pod uwagę początkowe kroki konfigurowania środowiska nie są dołączane, ponieważ należy ją wykonać jeden raz.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Tworzenie pojedynczej aplikacji w kontenerze platformy Docker przy użyciu programu Visual Studio Code i interfejsu wiersza polecenia platformy Docker

Aplikacje składają się z własnych usług, a także dodatkowe biblioteki (zależności).

Rysunek 4-22 przedstawiono podstawowe kroki, które zazwyczaj trzeba przeprowadzić podczas kompilowania aplikacji platformy Docker, następuje szczegółowy opis każdego kroku.

![Omówienie przepływu pracy: Krok 1 — kodu, krok 2 — zapis plików Dockerfile, krok 3 — Tworzenie obrazów zdefiniowane przy użyciu plików Dockerfile, krok 4 — zdefiniowanie usług przy użyciu pliku docker-compose, krok 5 — uruchom kontenery lub złożone aplikacje, krok 6 — aplikacje testowe, krok 7 — Wypychanie do rozpoczęcia zewnętrzna pętla (potoki ciągłej integracji/ciągłego wdrażania) lub kontynuować de veloping.](./media/image19.png)

**Rysunek 4-22**. Ogólny przepływ pracy dla cyklu życia aplikacji kontenerowych nimi platformy Docker za pomocą interfejsu wiersza polecenia platformy Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Krok 1. Rozpocznij kodowanie w programie Visual Studio Code i utworzyć linię bazową początkową aplikacji/usługi

Sposób tworzenia aplikacji jest podobny sposób, co można zrobić bez platformy Docker. Różnica jest, że podczas tworzenia, jesteś wdrażania i testowania aplikacji lub usług działających w kontenerach platformy Docker, umieszczone w środowisku lokalnym (np. maszyny Wirtualnej systemu Linux lub Windows).

**Konfigurowanie środowiska lokalnego**

Najnowsze wersje platformy Docker dla systemów Mac i Windows jest łatwiejsze niż kiedykolwiek do tworzenia aplikacji platformy Docker i konfiguracja jest prosta.

> [! INFORMACJE O]
>
> Aby uzyskać instrukcje na temat konfigurowania Docker for Windows, przejdź do <https://docs.docker.com/docker-for-windows/>.
>
>Aby uzyskać instrukcje na temat konfigurowania platformy Docker dla komputerów Mac, przejdź do <https://docs.docker.com/docker-for-mac/>.

Ponadto należy Edytor kodu, aby faktycznie można opracować aplikację przy użyciu interfejsu wiersza polecenia platformy Docker.

Firma Microsoft udostępnia programu Visual Studio Code, czyli lekkiemu edytorowi kodu, która jest obsługiwana na komputerach Mac, Windows i Linux, oferuje funkcję IntelliSense za pomocą [Obsługa wielu języków](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python i większość nowoczesnych języków), [debugowania](https://code.visualstudio.com/Docs/editor/debugging), [integracji z usługą Git](https://code.visualstudio.com/Docs/editor/versioncontrol) i [Obsługa rozszerzeń](https://code.visualstudio.com/docs/extensions/overview). Ten edytor to doskonałe rozwiązanie dla deweloperów systemów Mac i Linux. W Windows możesz również można użyć pełnej aplikacji programu Visual Studio.

> [! INFORMACJE O]
>
> Aby uzyskać instrukcje na temat instalowania programu Visual Studio Code dla Windows, Mac lub Linux, przejdź do <https://code.visualstudio.com/docs/setup/setup-overview/>.
>
> Aby uzyskać instrukcje na temat konfigurowania platformy Docker dla komputerów Mac, przejdź do <https://docs.docker.com/docker-for-mac/>.

Można pracować z interfejsem wiersza polecenia platformy Docker i pisanie kodu za pomocą dowolnego edytora kodu, ale z rozszerzeniem platformy Docker przy użyciu programu Visual Studio Code to łatwe do autora `Dockerfile` i `docker-compose.yml` plików w obszarze roboczym. Zadania i skrypty można również uruchomić z programu Visual Studio IDE kod do wykonywania poleceń platformy Docker przy użyciu interfejsu wiersza polecenia Docker poniżej.

Rozszerzenia platformy Docker dla programu VS Code oferuje następujące funkcje:

- Automatyczne `Dockerfile` i `docker-compose.yml` Generowanie pliku

- Wyróżnianie i aktywuje porady dotyczące składni dla `docker-compose.yml` i `Dockerfile` plików

- Funkcja IntelliSense (uzupełnianie) dla `Dockerfile` i `docker-compose.yml` plików

- Zaznaczanie błędów (błędy i ostrzeżenia) dla `Dockerfile` plików

- Polecenie integracji palety (F1) dla najczęściej używanych poleceń platformy Docker

- Integracja z Eksploratorem zarządzania obrazami i kontenery

- Wdrażanie obrazów z witryny DockerHub i rejestry kontenerów platformy Azure w usłudze Azure App Service

Aby zainstalować rozszerzenia platformy Docker, naciśnij klawisze Ctrl + Shift + P, wpisz `ext install`, a następnie uruchom polecenie Zainstaluj rozszerzenie, aby wyświetlić listę rozszerzeń witryny Marketplace. Następnie wpisz **docker** do filtrowania wyników, a następnie wybierz rozszerzenie obsługi programu Docker, jak pokazano w rysunek 4-23.

![Wyświetl rozszerzenia platformy Docker dla programu VS Code.](./media/image20.png)

**Rysunek 4-23**. Instalowanie rozszerzenia platformy Docker w programie Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Krok 2. Tworzenie pliku DockerFile związane z istniejącego obrazu (zwykły system operacyjny lub środowiskach deweloperskich, takich jak .NET Core, Node.js i Ruby)

Będziesz potrzebować `DockerFile` według obrazu niestandardowego do zbudowania i kontenera do wdrożenia. Jeśli aplikacja składa się z jednej usługi niestandardowe, należy jeden `DockerFile`. Ale jeśli aplikacja składa się z wielu usług (tak jak w architekturze mikrousług), trzeba będzie je utworzyć `Dockerfile` na usługę.

`DockerFile` Często znajduje się w folderze głównym aplikacji lub usługi i zawiera wymagane polecenia, tak że platforma Docker wie, jak skonfigurować i uruchomić tej aplikacji lub usługi. Można utworzyć usługi `DockerFile` i dodaj go do swojego projektu, wraz z kodu (node.js, .NET Core, itp.), lub, jeśli jesteś nowym użytkownikiem środowiska, spójrz na poniższe porady.

> [!TIP]
>
> Można użyć rozszerzenia platformy Docker, przeprowadzenie Cię w przypadku korzystania z `Dockerfile` i `docker-compose.yml` pliki związane z programem kontenerów Docker. Po pewnym czasie prawdopodobnie napiszesz te rodzaje plików bez tego narzędzia, ale przy użyciu rozszerzenia platformy Docker jest dobry punkt wyjścia przyspieszy swoje nauki.

W rysunek 4 – 24, możesz zobaczyć jak docker-compose plik zostanie dodany przy użyciu rozszerzenia platformy Docker dla programu VS Code.

![Widok konsoli rozszerzenia platformy Docker dla programu VS Code.](./media/image24.png)

**Rysunek 4-24**. Pliki docker dodać za pomocą **plików Dodaj Docker do polecenia obszaru roboczego**

Po dodaniu pliku DockerFile, określ jaki podstawowego obrazu platformy Docker, należy używać (takimi jak wymaganie użycia `FROM mcr.microsoft.com/dotnet/core/aspnet`). Zazwyczaj utworzysz obraz niestandardowy na podstawie obrazu podstawowego, który można pobrać z dowolnego oficjalne repozytorium na [rejestru usługi Docker Hub](https://hub.docker.com/) (takich jak [obrazu dla platformy .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) lub [dla środowiska Node.js](https://hub.docker.com/_/node/)).

***Użyj istniejącego oficjalny obraz platformy Docker***

Za pomocą oficjalnego repozytorium stos języka z numerem wersji zapewnia, że te same funkcje języka są dostępne na wszystkich komputerach (w tym programowanie, testowanie i produkcja).

Poniżej przedstawiono przykładowy plik DockerFile dla kontenera platformy .NET Core:

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.1
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

W tym przypadku obraz, który jest oparty na oficjalny obraz platformy Docker programu ASP.NET Core (wielu arch dla systemów Linux i Windows) dla każdego wiersza w wersji 2.1 `FROM mcr.microsoft.com/dotnet/core/aspnet:2.1`. (Aby uzyskać więcej informacji na ten temat, zobacz [obrazu platformy Docker programu ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) strony i [obrazu platformy Docker programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) strony).

W pliku DockerFile można również poinstruować platformy Docker do nasłuchiwania na portach TCP, którego będziesz używać w czasie wykonywania (np. port 80).

Można określić dodatkowe ustawienia konfiguracji w pliku Dockerfile, w zależności od języka i struktury, którego używasz. Na przykład `ENTRYPOINT` linia z `["dotnet", "MySingleContainerWebApp.dll"]` platformy docker, aby uruchomić aplikację .NET Core. Jeśli używasz zestawu SDK oraz interfejsu wiersza polecenia platformy .NET Core (`dotnet CLI`) aby skompilować i uruchomić aplikację .NET, to ustawienie będzie inny. Kluczowym punktem tutaj jest, że wiersz punktu wejścia i inne ustawienia zależą od języka i platformy, wybrany dla aplikacji.

> [! INFORMACJE O]
>
> Aby uzyskać więcej informacji na temat Tworzenie obrazów platformy Docker dla aplikacji platformy .NET Core, przejdź do <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.
>
> Aby dowiedzieć się więcej o tworzeniu własnych obrazów, przejdź do <https://docs.docker.com/engine/tutorials/dockerimages/>.

**Użyj wielu architektury obrazu repozytoriów**

Nazwa pojedynczego obrazu w repozytorium może zawierać warianty platformy, takich jak obraz systemu Linux i Windows obraz. Ta funkcja umożliwia dostawców, takich jak Microsoft (obraz podstawowy dla twórców) do utworzenia pojedynczego repozytorium na pokrycie wiele platform (oznacza to, Linux i Windows). Na przykład [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repozytorium, które są dostępne w rejestrze usługi Docker Hub zapewnia obsługę dla systemów Linux i Windows Nano Server, korzystając z taką samą nazwę obrazu.

Ściąganie [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) obrazu z hosta Windows pobiera wariant Windows, natomiast ściągania taką samą nazwę obrazu na hoście z systemem Linux ściąga wariantów systemu Linux.

***Tworzenie obrazu podstawowego od podstaw***

Można utworzyć własny obraz podstawowy platformy Docker od podstaw, zgodnie z opisem w tym [artykułu](https://docs.docker.com/engine/userguide/eng-image/baseimages/) docker. Ten scenariusz jest prawdopodobnie nie najlepiej dla Ciebie, jeśli dopiero zaczynasz przy użyciu rozwiązania Docker, ale jeśli chcesz ustawić bity określonego obrazu podstawowego, możesz to zrobić.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Krok 3. Tworzenie niestandardowych obrazów platformy Docker osadzania usługi w nim

Dla każdej usługi niestandardowego, który składa się z aplikacji należy utworzyć obraz powiązane. Jeśli aplikacja składa się z jednej usługi lub aplikacji sieci web, musisz pojedynczego obrazu.

> [!NOTE]
>
> Biorąc pod uwagę "zewnętrzna pętla DevOps przepływu pracy", obrazy zostanie utworzona przez zautomatyzowanego procesu kompilacji po każdym wypchnięciu kodu źródłowego do repozytorium Git (ciągła integracja), więc obrazy zostanie utworzony w tym środowisku globalnych z usługi Kod źródłowy.
>
> Jednak zanim firma Microsoft uważa, przechodząc do tej trasy zewnętrzna pętla, musimy upewnić się, że aplikację platformy Docker faktycznie działa prawidłowo, aby nie mogą umieścić kod, który może nie działać poprawnie do systemu kontroli źródła (Git itp.).
>
> W związku z tym Każdy deweloper musi najpierw celu cały proces wewnętrzny pętli do testowania lokalnie i kontynuować tworzenie, dopóki nie chcą wypchnąć pełne funkcji lub zmień wartość na system kontroli źródła.

Aby utworzyć obraz w środowisku lokalnym i za pomocą pliku DockerFile, można użyć polecenia kompilacji platformy docker, jak pokazano w rysunek 4-25 (możesz także uruchomić `docker-compose up --build` aplikacji poprzez wiele kontenerów/usług).

![Dane wyjściowe konsoli kompilacji docker-compose pokazywanie obrazów pobieranie w toku.](./media/image25.png)

**Rysunek 4-25**. Uruchamianie kompilacji platformy docker

Opcjonalnie, zamiast bezpośredniego uruchamiania `docker build` z folderu projektu, najpierw można wygenerować folderu do wdrożenia z bibliotekami .NET potrzebne przy użyciu opcji Uruchom `dotnet publish` polecenia, a następnie uruchom `docker build`.

W tym przykładzie tworzy obraz platformy Docker o nazwie `cesardl/netcore-webapi-microservice-docker:first` (`:first` jest tag, takich jak określonej wersji). Możesz wykonać ten krok dla każdego obrazu niestandardowego, potrzebne do utworzenia złożone aplikacji platformy Docker za pomocą wielu kontenerów.

Można znaleźć istniejących obrazów w lokalnym repozytorium (komputerze deweloperskim) przy użyciu platformy docker polecenie obrazów, jak pokazano w rysunek 4-26.

![Dane wyjściowe z polecenia obrazów platformy docker, wyświetlanie istniejących obrazów z konsoli.](./media/image26.png)

**Rysunek 4-26**. Wyświetlanie istniejących obrazów przy użyciu obrazów platformy docker

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Krok 4. Zdefiniuj swoje usługi w docker-compose.yml, podczas kompilowania złożone aplikacji platformy Docker z wieloma usługami

Za pomocą `docker-compose.yml` pliku, można zdefiniować zestaw powiązanych usług, który można wdrożyć jako złożone aplikacji za pomocą poleceń wdrażania opisano w następnej sekcji krok.

Tworzenie tego pliku w głównego lub główny folder rozwiązania; powinien być podobny do przedstawionego w tym zawartości `docker-compose.yml` pliku:

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

W tym konkretnym przypadku ten plik definiuje dwie usługi: Usługa sieci web (usługa niestandardowa) i usługa redis (usługa popularnej pamięci podręcznej). Każda usługa zostanie wdrożony jako kontener, dlatego musimy użyć konkretnego obrazu platformy Docker dla każdego. Dla tej usługi sieci web określonego obrazu należy wykonać następujące czynności:

- Twórz z pliku DockerFile w bieżącym katalogu

- Przekazuj narażonych port 80 w kontenerze na porcie 81 na komputerze hosta

- Zainstaluj w katalogu projektu na hoście/Code w kontenerze, dzięki czemu można zmodyfikować kod bez konieczności ponownego kompilowania obrazu

- Połączenia usługi sieci web z usługą redis Cache

Używa usługi redis [najnowszego obrazu publicznego redis](https://hub.docker.com/_/redis/) pobierane z rejestru usługi Docker Hub. [redis](https://redis.io/) to system popularnej pamięci podręcznej dla aplikacji po stronie serwera.

### <a name="step-5-build-and-run-your-docker-app"></a>Krok 5. Kompilowanie i uruchamianie aplikacji platformy Docker

Jeśli aplikacja ma tylko jeden kontener, wystarczy uruchomić go przez wdrożenie jej do hosta platformy Docker (maszyny Wirtualnej lub serwera fizycznego). Jednak jeśli Twoja aplikacja składa się z wielu usług, musisz *została utworzona*również. Teraz widzieć różne opcje.

***Opcja A: Uruchom jeden kontener lub usługi***

Obraz platformy Docker można uruchomić przy użyciu platformy docker, uruchom polecenie, jak pokazano poniżej:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Dla tego konkretnego wdrożenia firma Microsoft będzie można Przekierowywanie żądań wysyłanych do portu 80 na port wewnętrzny 5000. Teraz aplikacja nasłuchuje na porcie zewnętrznym 80 na poziomie hosta.

***Opcja B: Tworzenie i uruchamianie aplikacji wielu kontenerów***

W większości przypadków enterprise aplikację platformy Docker składać się z wielu usług. W takich przypadkach można uruchomić `docker-compose up` polecenia (rysunek 4-27), który będzie używany plik docker-compose.yml, które zostały utworzone wcześniej. Uruchomienie tego polecenia wdraża złożone aplikacji ze wszystkimi jego powiązane kontenerów.

![Dane wyjściowe z konsoli narzędzia docker compose się polecenia.](./media/image27.png)

**Rysunek 4-27**. Wyniki polecenia "docker-compose up"

Po uruchomieniu `docker-compose up`, wdrażania aplikacji i jej powiązane kontenerów w hoście platformy Docker, jak pokazano w rysunek 4-28 w reprezentacji maszyny Wirtualnej.

![Maszyny Wirtualnej z systemem wielokontenerowych aplikacji.](./media/image28.png)

**Rysunek 4-28**. Maszyny Wirtualnej przy użyciu kontenerów Docker wdrożonych

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Krok 6. Testowanie aplikacji platformy Docker (lokalnie, w swojej lokalnej maszyny Wirtualnej dysku CD)

W tym kroku różnią się w zależności od tego, jakie działania aplikacji.

W prostych platformy .NET Core interfejsu API sieci Web "Hello World" wdrażane jako pojedynczy kontener lub usługi czy wystarczy dostęp do usługi, zapewniając portu TCP, określone w pliku DockerFile.

Jeśli host lokalny nie jest włączony, aby przejść do swojej usługi, należy znaleźć adres IP dla maszyny, za pomocą tego polecenia:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Na hoście platformy Docker Otwórz przeglądarkę i przejdź do tej lokacji; Twoja aplikacja/Usługa jest uruchomiona, powinien zostać wyświetlony, jak pokazano w rysunek 4-29.

![Widok w przeglądarce odpowiedź z localhost/API/wartości.](./media/image29.png)

**Rysunek 4-29**. Testowanie aplikacji platformy Docker lokalnie przy użyciu localhost

Pamiętaj, że jest ona przy użyciu portu 80, ale wewnętrznie jest nastąpi przekierowanie do portu 5000, ponieważ jest to, jak została ona wdrożona na `docker run`, jak wyjaśniono wcześniej.

Można to sprawdzić, używając programu CURL z poziomu terminalu. W przypadku instalacji platformy Docker na Windows domyślny adres IP jest 10.0.75.1, jak pokazano w rysunek 4-30.

![Pobieranie danych wyjściowych konsoli http://10.0.75.1/API/values za pomocą programu curl](./media/image30.png)

**Rysunek 4-30**. Testowanie aplikacji platformy Docker lokalnie, używając programu CURL

**Debugowanie kontenera uruchomionego w platformy Docker**

Jeśli używasz środowiska Node.js i innych platform, takich jak kontenery platformy .NET Core, programu Visual Studio Code obsługuje debugowania platformy Docker.

Możesz również debugować platformy .NET Core lub .NET Framework w kontenerach na platformie Docker podczas korzystania z programu Visual Studio for Windows lub Mac, zgodnie z opisem w następnej sekcji.

> [! INFORMACJE O]
>
> Aby dowiedzieć się więcej o debugowaniu w kontenerach platformy Docker w środowisku Node.js, przejdź do <https://blog.docker.com/2016/07/live-debugging-docker/> i <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.

>[!div class="step-by-step"]
>[Poprzednie](docker-apps-development-environment.md)
>[dalej](visual-studio-tools-for-docker.md)
