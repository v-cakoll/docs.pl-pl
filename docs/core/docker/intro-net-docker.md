---
title: "Wprowadzenie do usług .NET i Docker"
description: "Opis rozwiązania Docker i .NET Core"
keywords: .NET, .NET core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.openlocfilehash: 0164c36dcfb8a851dcb40d82265390795dc3d16c
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="introduction-to-net-and-docker"></a>Wprowadzenie do usług .NET i Docker

 Ten artykuł zawiera wprowadzenie oraz tło koncepcyjnej do pracy z platformą .NET na Docker. 

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker: Pakowanie aplikacji do wdrożenia i uruchomienia dowolnego miejsca

[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined) jest otwarta platforma, która umożliwia deweloperom i administratorom tworzenie [obrazów](https://docs.docker.com/glossary/?term=image), wysyłki i uruchomić aplikacje rozproszone w słabo izolowanym środowisku, nazywany [kontenera](https://www.docker.com/what-container). Takie podejście umożliwia zarządzanie cyklem życia aplikacji wydajne między programowanie, odpowiedzi na pytania i środowisk produkcyjnych.
 
[Platformy Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) używa [aparatem platformy Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) szybkie tworzenie i pakietu aplikacji jako [obrazy usługi Docker](https://docs.docker.com/glossary/?term=image) utworzone przy użyciu plików napisany w [plik Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) formatu, który następnie jest wdrażany i uruchamiany [warstwie kontenera](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Możesz utworzyć własne [warstwie obrazy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) jako dockerfiles lub użyj istniejące grupy z [rejestru](https://docs.docker.com/glossary/?term=registry), takiej jak [Centrum Docker](https://docs.docker.com/glossary/?term=Docker%20Hub).

[Relacji między Docker kontenerów, obrazy i rejestrów](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries) jest ważne pojęcia podczas [projektowania i tworzenia konteneryzowanych aplikacji lub mikrousług](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/). Takie podejście znacznie skraca czas między opracowywania i wdrażania.

### <a name="further-reading-and-watching"></a>Dalsze informacje (i obserwowanie)

* [Kontenery systemu Windows: tworzenie nowoczesnych aplikacji za pomocą formantu korporacyjnej.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Omówienie docker](https://docs.docker.com/engine/docker-overview/)
* [Plik Dockerfile kontenerów systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Najlepsze rozwiązania dotyczące pisania Dockerfiles](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [Obrazy usługi Docker Kompilowanie aplikacji .NET Core](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>Pobieranie obrazy usługi Docker .NET

Obrazy oficjalnego Docker .NET są utworzone i zoptymalizowane przez firmę Microsoft. Są one publicznie dostępne w repozytoria firmy Microsoft w Centrum Docker. Każdego repozytorium może zawierać wiele obrazów, w zależności od wersji platformy .NET, a także w wersjach systemu operacyjnego. Większość repozytoriów obrazu zapewniają szeroką gamę znakowanie ułatwiające wybranie zarówno wersji określonej platformy, jak i systemu operacyjnego (Linux distro lub wersji systemu Windows).

## <a name="scenario-based-guidance"></a>Wskazówki na podstawie scenariusza

Celem firmy Microsoft dla repozytoriów .NET jest szczegółowym i skupiają się repozytoriów, które reprezentują konkretnych sytuacji lub obciążenia.

`microsoft/aspnetcore` Obrazy są zoptymalizowane pod kątem aplikacji platformy ASP.NET Core w Docker, więc kontenery można uruchomić szybciej.

Obrazy platformy .NET Core (`microsoft/dotnet`) są przeznaczone dla aplikacji konsoli .NET Core w oparciu. Na przykład procesy partii zadań Webjob Azure i inne scenariusze konsoli, należy użyć zoptymalizowanych obrazów .NET Core.

Jest to najbardziej oczywisty poziome scenariusz przy użyciu aplikacji Docker i .NET do środowiska produkcyjnego i obsługiwania. Okaże się czy produkcji jest tylko jeden scenariusz i innych te są przydatne w równym stopniu. Te scenariusze nie są specyficzne dla platformy .NET, ale powinny być stosowane do większości platform developer.

* **Zainstaluj małym tarciu** — można wypróbować .NET bez instalacji lokalnej. Wystarczy pobrać obrazu Docker z platformą .NET w nim.

* **Tworzenie w kontenerze** — można utworzyć spójne środowisko, tworzenie środowisk projektowania i produkcji podobne (unikanie problemów, takich jak stan globalny na komputerach deweloperów). Visual Studio Tools for Docker umożliwiają nawet uruchomić kontener bezpośrednio z programu Visual Studio.

* **Testowanie w kontenerze** — możesz przetestować w kontenerze, zmniejszając błędy spowodowane środowiskami niepoprawnie skonfigurowany lub inne zmiany pozostawione od ostatniego testu.

* **Kompilacji w kontenerze** — można utworzyć kod w kontenerze uniknięcie poprawnie skonfigurować maszyny udostępnionego kompilacji w wielu środowiskach, ale zamiast tego Przenieś do "BYOC" (Przynieś własne kontenera) podejście.

* **Wdrożenie we wszystkich środowiskach** — może wdrożyć obraz za pomocą wszystkich środowisk. Takie podejście zmniejsza błędy z powodu różnic konfiguracji, zwykle zmiany zachowania obrazu za pomocą zewnętrznych (na przykład zmienne wprowadzony środowiska).

[Ogólne wskazówki](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance) dotyczących decydowania między .NET Core i .NET Framework dla rozwoju kontenera Docker.

### <a name="common-docker-development-scenarios"></a>Typowe scenariusze programowania Docker

#### <a name="net-core"></a>.NET Core

**Zasoby platformy .NET core**

 Wybierz spełniających scenariuszy zainteresowania przykłady .NET Core. Wszystkie przykładowe instrukcje przedstawiają sposób obrazy systemu Windows lub Linux Docker z hostów Windows, Linux lub macOS docelowe.

Przykłady użycia .NET Core 2.0. Używają Docker [kompilacji wieloetapowym](https://github.com/dotnet/announcements/issues/18) i [architektury wielu tagów](https://github.com/dotnet/announcements/issues/14) w razie potrzeby.

* [Obrazy platformy .NET core w DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [Dockerize aplikacji .NET Core](https://docs.docker.com/engine/examples/dotnetcore/)

* .NET Core Docker w przykładzie pokazano, jak [Użyj Docker w procesie tworzenia aplikacji platformy .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). Przykład współdziała z kontenerów zarówno systemu Linux i Windows.

* W tym przykładzie .NET Core Docker pokazuje wzorzec najlepsze praktyki dla [tworzenia obrazów Docker dla aplikacji .NET Core w środowisku produkcyjnym.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) Przykład współdziała z kontenerów zarówno systemu Linux i Windows.

* To [próbki .NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) przedstawiono najlepsze wzorzec rozwiązanie do tworzenia obrazów Docker [niezależne aplikacji .NET Core](https://docs.microsoft.com/dotnet/core/deploying/). Używany do najmniejszego kontenera produkcyjnego bez korzyści z [udostępnianie obrazy podstawowe między kontenery](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). Jednak można udostępnić niższych warstwach Docker.

#### <a name="arm32--raspberry-pi"></a>ARM32 / Pi malina

* [.NET core środowiska uruchomieniowego ARM32 kompilacje anonsu](https://github.com/dotnet/announcements/issues/29)

* [ARM32 / malina Pi .NET Core obrazy na DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 / Pi malinowe .NET Core Docker przykładów w witrynie GitHub](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [.NET framework obrazów na DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/) to repozytorium zawiera przykłady ilustrujące różne konfiguracje programu .NET Framework Docker. Obrazy te można użyć jako podstawa obrazów Docker.

**.NET framework 4.7**

[ [Dotnet — przykład struktury: 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) przedstawiono podstawowe "hello world" użycie [.NET Framework 4.7](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47). Przedstawiono sposób tworzenia i wdrożyć aplikację jednostki uzależnionej na [obrazu docker .NET Framework 4.7](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).

**.NET framework 4.6.2**

[Dotnet — przykład framework: 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) przedstawiono podstawowe "hello world" użycie [.NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462). Przedstawiono sposób tworzenia i wdrożyć aplikację jednostki uzależnionej na [obrazu docker .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).

**.NET framework 3.5**

 [Dotnet — przykład struktury: 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) przedstawiono podstawowe "hello world" użycie [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5). Przedstawiono sposób tworzenia i wdrażania projektu polegania na programie .NET Framework 3.5 w rozwiązaniu Docker.

#### <a name="aspnet-core"></a>Platformy ASP.NET Core

* [W tym przykładzie platformy ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) pokazuje wzorzec najlepszych rozwiązań tworzenia obrazy usługi Docker dla platformy ASP.NET Core aplikacji w środowisku produkcyjnym. Przykład współdziała z kontenerów zarówno systemu Linux i Windows.

* [Obrazy platformy ASP.NET Core w DockerHub](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [Obrazy platformy ASP.NET Core w witrynie GitHub](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>Struktura ASP.NET 

* [Struktura ASP.NET obrazów na DockerHub](https://hub.docker.com/r/microsoft/aspnet/)

* [Aplikacja formularzy sieci Web ASP.NET dla .NET Framework 4.6.2 próbki](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Obrazy systemu Windows Communication Framework (WCF) w DockerHub](https://hub.docker.com/r/microsoft/wcf/)

* [Obrazy systemu Windows Communication Framework (WCF) w witrynie GitHub](https://github.com/microsoft/iis-docker)

* [Za pomocą .NET Full Framework 4.6.2 przykłady Docker Windows Communication Framework (WCF)](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Obrazy Internet Information Server (IIS) w DockerHub](https://hub.docker.com/r/microsoft/iis/)

* [Obrazy Internet Information Server (IIS) w witrynie GitHub](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Interakcje z innych Microsoft stosu kontener obrazów

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Uruchamianie programu Microsoft SQL Server dla systemu Linux 2017 kontener obrazu z Docker Szybki Start](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server dla systemu Linux obrazów na DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Microsoft SQL Server dla systemu Windows kontenery obrazów na DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Microsoft SQL Server Express Edition obrazów systemu Windows kontenerów na DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Microsoft SQL Server Developer Edition obrazów systemu Windows kontenerów na DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Visual Studio Team Services (VSTS) agenta

* [Visual Studio Team Services (VSTS) agent obrazów na DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Visual Studio Team Services (VSTS) agent obrazów w witrynie GitHub](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Agent programu Operations Management Suite (OMS) w systemie Linux

* [Operations Management Suite (OMS) w systemie Linux agent Przegląd](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [Operations Management Suite (OMS) obrazów na DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/) 

* [Operations Management Suite (OMS) obrazów w witrynie GitHub](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Interfejs wiersza polecenia platformy Microsoft Azure (CLI)

* [Microsoft Azure interfejs wiersza polecenia (CLI) obrazów na DockerHub](https://hub.docker.com/r/microsoft/azure-cli/) 

* [Microsoft Azure interfejs wiersza polecenia (CLI) obrazów w witrynie GitHub](https://github.com/Microsoft/OMS-docker)

> [!Note]
> Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się już dziś](https://azure.microsoft.com/free/?b=16.48) bezpłatnej 30-dniowe konto i 200 USD interweniować środków Azure wypróbowanie dowolną kombinację usługami Azure.
>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Emulator rozwiązania Cosmos bazy danych Microsoft Azure (tylko kontenery systemu Windows)

* [Obrazy emulatora bazy danych programu Microsoft Azure rozwiązania Cosmos w DockerHub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Użyj emulatora usługi Azure rozwiązania Cosmos bazy danych dla lokalnych projektowania i testowania](https://docs.microsoft.com/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Eksploracja rozbudowany ekosystem programowanie Docker

Teraz, kiedy znasz o różnych obrazy usługi Docker i platformy Docker, następnym krokiem jest Eksploruj rozbudowany ekosystem Docker. Poniższe linki Pokaż jak narzędzia Microsoft uzupełniają programowanie kontenera.

* [Ze sobą przy użyciu platformy .NET i Docker](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) 
* [Projektowanie i tworzenie aplikacji na podstawie Mikrousługi i usługi kontenera platformy .NET](../standard/microservices-architecture/multi-container-microservice-net-applications)
* [Visual Studio Code Docker rozszerzenia](https://code.visualstudio.com/docs/languages/dockerfile) 
* [Dowiedz się, jak używać usługi Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/) 
* [Przykładowe uruchomić pobierania sieci szkieletowej usług](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Korzyści wynikające z kontenerów systemu Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index#video-overview)
* [Praca z narzędzia Docker programu Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Wdrażanie obrazów Docker z rejestru kontenera platformy Azure do wystąpień kontenera platformy Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Profilowanie kodu Visual Studio](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Wprowadzenie ręce na z programem Visual Studio for Mac, kontenery i niekorzystającą kodu w chmurze](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Pierwsze kroki z Docker i Visual Studio for Mac laboratorium](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Następne kroki

* [Poznaj podstawy korzystania z platformy Docker z programem .NET Core](../docker/docker-basics-dotnet-core.md)
* [Tworzenie obrazy usługi Docker .NET Core](../docker/building-net-docker-images)
