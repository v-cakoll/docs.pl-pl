---
title: Wprowadzenie do platform .NET i Docker
description: Omówienie platformy Docker i platformy .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.custom: mvc
ms.openlocfilehash: d578ec5a25dbb5de3c88386e212e68cf3b267749
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970646"
---
# <a name="introduction-to-net-and-docker"></a>Wprowadzenie do platform .NET i Docker

Ten artykuł zawiera wprowadzenie i pojęciach tła do pracy z platformą .NET na platformy Docker.

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Platformy docker: Pakowanie aplikacji, wdrażanie i uruchamianie w dowolnym miejscu

[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) to otwarta platforma, która umożliwia deweloperom i administratorom tworzenie [obrazów](https://docs.docker.com/glossary/?term=image), dostarczania i uruchamiania aplikacji rozproszonych w środowisku izolowanym luźno o nazwie [kontenera](https://www.docker.com/what-container). Takie podejście umożliwia zarządzanie cyklem życia aplikacji wydajne między środowiskiem deweloperskim, odpowiedzi na pytania i środowisk produkcyjnych.
 
[Platforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) używa [aparat platformy Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) umożliwiają szybkie tworzenie i pakowanie aplikacji jako [obrazów platformy Docker](https://docs.docker.com/glossary/?term=image) utworzone za pomocą pliki zapisane [pliku Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) formatu, który następnie jest wdrażany i uruchamiany [warstwie kontenerów](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Możesz utworzyć własne [obrazów z warstwami](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) jako pliki dockerfile lub może być istniejące z [rejestru](https://docs.docker.com/glossary/?term=registry), takiej jak [usługi Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).

[Relacji między kontenerami aparatu Docker, obrazy i rejestry](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) jest bardzo ważnym pojęciem podczas [projektowanie i tworzenie kontenerowych nimi aplikacji lub mikrousług](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). To podejście znacznie skraca czas między opracowywania i wdrażania.

### <a name="further-reading-and-watching"></a>Dalsze informacje (i obserwowanie)

* [Kontenery z systemem Windows: opracowywanie nowoczesnych aplikacji za pomocą kontroli korporacyjnej.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Przegląd platformy docker](https://docs.docker.com/engine/docker-overview/)
* [Plik Dockerfile kontenerów Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Najlepsze rozwiązania dotyczące zapisywania plików Dockerfile](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [Kompilowanie obrazów platformy Docker dla aplikacji platformy .NET Core](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>Pobieranie obrazów platformy Docker platformy .NET

Obrazy Docker w programie .NET oficjalne są tworzone i zoptymalizowane pod kątem przez firmę Microsoft. Są one publicznie dostępne w przypadku repozytoriów firmy Microsoft w usłudze Docker Hub. Każde repozytorium może zawierać wiele obrazów, w zależności od wersji platformy .NET i w wersjach systemu operacyjnego. Większość repozytoriów obraz zapewniają szeroką tagowania ułatwiające wybranie określonych wersję i systemu operacyjnego (dystrybucja systemu Linux lub Windows w wersji).

## <a name="scenario-based-guidance"></a>Wskazówki dotyczące scenariusza bazujące

Celem firmy Microsoft dla repozytoriów platformy .NET jest repozytoria szczegółową i skupionego projektu, reprezentujących konkretnego scenariusza lub obciążenia.

`microsoft/aspnetcore` Obrazy są zoptymalizowane pod kątem aplikacji platformy ASP.NET Core na platformy Docker, dzięki czemu szybciej zacząć kontenerów.

Obrazy platformy .NET Core (`microsoft/dotnet`) są przeznaczone dla aplikacji konsoli, oparte na module .NET Core. Na przykład procesy wsadowe, zadania Webjob platformy Azure i innych scenariuszy konsoli, należy użyć zoptymalizowane obrazy platformy .NET Core.

Jest to najbardziej oczywiste poziomy scenariusz korzystania z aplikacji platformy Docker i platformy .NET wdrożenia produkcyjnego i hostować. Okazuje się się, że produkcji jest tylko jeden scenariusz, a inne są równie przydatne. Te scenariusze nie są specyficzne dla platformy .NET, ale powinno dotyczyć większości platform programistycznych.

* **Bezproblemowe instalowanie** — .NET można wypróbować bez instalacji lokalnej. Wystarczy pobrać obraz platformy Docker przy użyciu platformy .NET w nim.

* **Programowanie w kontenerze** — możesz tworzyć w środowisku spójne wprowadzania środowisk deweloperskich i produkcyjnych podobne (unikanie problemy, takie jak stan globalny na komputerach deweloperów). Visual Studio Tools for Docker nawet umożliwia uruchamianie kontenera bezpośrednio z programu Visual Studio.

* **Testowanie w kontenerze** — możesz przetestować w kontenerze, zmniejszając błędy z powodu nieprawidłowo skonfigurowane środowiska lub innych zmian pozostawione z ostatniego testu.

* **Tworzenie w kontenerze** — możesz tworzyć kod w kontenerze, unikając konieczności poprawnie skonfigurować maszyny kompilacji udostępniony dla wielu środowisk, ale zamiast tego Przenieś do "BYOC" (bring własnego kontenera) podejście.

* **Wdrożenie we wszystkich środowiskach** — można wdrożyć obraz za pośrednictwem wszystkich środowisk. Takie podejście zmniejsza błędy z powodu różnic w konfiguracji, zwykle zmiany zachowania obrazu za pomocą konfiguracji zewnętrzne (na przykład, zmiennych środowiska wprowadzonego).

[Ogólne wskazówki dotyczące](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) dotyczących decydowania między programem.NET Core i .NET Framework do tworzenia kontenera platformy Docker.

### <a name="common-docker-development-scenarios"></a>Typowe scenariusze deweloperskie platformy Docker

#### <a name="net-core"></a>.NET Core

**Zasoby platformy .NET core**

 Pobierz przykłady platformy .NET Core, pasujące scenariuszy zainteresowania. Wszystkie instrukcje przykładowe przedstawiają sposób pod kątem obrazów Windows lub platformy Docker w systemie Linux z hostów Windows, Linux lub macOS.

Przykłady użycia platformy .NET Core 2.0. Korzystać z aparatu Docker [kompilacji wieloetapowych](https://github.com/dotnet/announcements/issues/18) i [architektury wielu tagów](https://github.com/dotnet/announcements/issues/14) zgodnie z wymaganiami.

* [Obrazy platformy .NET core w witrynie DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [Przekształcać aplikacji .NET Core](https://docs.docker.com/engine/examples/dotnetcore/)

* Docker w programie .NET Core w przykładzie pokazano, jak [korzystać z aparatu Docker w procesie tworzenia aplikacji platformy .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). Przykład współdziała z kontenerów systemów Linux i Windows.

* Docker w programie .NET Core w przykładzie pokazano wzorzec najlepsze praktyki dla [tworzenie obrazów platformy Docker dla aplikacji platformy .NET Core w środowisku produkcyjnym.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) Przykład współdziała z kontenerów systemów Linux i Windows.

* To [przykładowe Docker w programie .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) przedstawiono najlepsze praktyki wzorzec do tworzenia obrazów platformy Docker dla [niezależna aplikacji .NET Core](../deploying/index.md). Używany do najmniejszej kontenera produkcyjnych bez korzyści z [udostępnianie podstawowe obrazy między kontenerów](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). Jednak może być udostępniane niższych warstwach platformy Docker.

#### <a name="arm32--raspberry-pi"></a>ARM32 / Raspberry Pi

* [Ogłoszenie kompilacje ARM32 środowiska uruchomieniowego programu .NET core](https://github.com/dotnet/announcements/issues/29)

* [ARM32 / Raspberry Pi platformy .NET Core obrazy w witrynie DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 / urządzenia Raspberry Pi .NET Core Docker przykłady w witrynie GitHub](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [.NET framework obrazów w witrynie DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/)

To repozytorium zawiera przykłady, które pokazują różne konfiguracje Docker w programie .NET Framework. Obrazy te można użyć jako punktu wyjścia dla własnych obrazów platformy Docker.

**.NET framework 4.7**

[Dotnet-przykładowe framework: 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) pokazuje podstawowe "hello world" użycie [.NET Framework 4.7](../../framework/whats-new/index.md#v47). Przedstawia on sposób tworzenie i wdrażanie aplikacji, opierając się na [obrazu platformy docker programu .NET Framework 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile).

**.NET framework 4.6.2**

[Dotnet-przykładowe framework: 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) pokazuje podstawowe "hello world" użycie [platformy .NET Framework 4.6.2](../../framework/whats-new/index.md#v462). Przedstawia on sposób tworzenie i wdrażanie aplikacji, opierając się na [obrazu platformy docker platformy .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile).

**.NET framework 3.5**

 [Dotnet-przykładowe framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) pokazuje podstawowe "hello world" użycie [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile). Przedstawia on sposób tworzenia i wdrażania projektu polegania na programie .NET Framework 3.5 na platformie Docker.

#### <a name="aspnet-core"></a>ASP.NET Core

* [W tym przykładzie platformy Docker programu ASP.NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) przedstawiono najlepsze praktyki wzorzec do tworzenia obrazów platformy Docker dla platformy ASP.NET Core z aplikacji w środowisku produkcyjnym. Przykład współdziała z kontenerów systemów Linux i Windows.

* [Obrazy platformy ASP.NET Core w witrynie DockerHub](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [Obrazy platformy ASP.NET Core w usłudze GitHub](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>Środowiska ASP.NET Framework

* [Środowiska ASP.NET Framework obrazów w witrynie DockerHub](https://hub.docker.com/r/microsoft/aspnet/)

* [Aplikacja formularzy sieci Web ASP.NET, na przykład .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Obrazy Windows Communication Framework (WCF) w witrynie DockerHub](https://hub.docker.com/r/microsoft/wcf/)

* [Obrazy Windows Communication Framework (WCF) w witrynie GitHub](https://github.com/microsoft/wcf-docker)

* [Przykłady Docker Windows Communication Framework (WCF) przy użyciu platformy .NET Framework 4.6.2](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Obrazy Internet Information Server (IIS) w witrynie DockerHub](https://hub.docker.com/r/microsoft/iis/)

* [Obrazy Internet Information Server (IIS) w witrynie GitHub](https://github.com/microsoft/iis-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Oddziałują na inne obrazy kontenera stos Microsoft

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Uruchamianie programu Microsoft SQL Server dla obrazu kontenera systemu Linux 2017 z przewodnika Szybki Start platformy Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Program Microsoft SQL Server dla obrazów systemu Linux w witrynie DockerHub](https://hub.docker.com/r/microsoft/mssql-server-linux/)

* [Microsoft SQL Server Express Edition obrazy kontenerów Windows w witrynie DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Program Microsoft SQL Server Developer Edition obrazy kontenerów Windows w witrynie DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="azure-devops-services-agent"></a>Agent usługom DevOps platformy Azure

* [Obrazy agenta usługom DevOps platformy Azure w witrynie DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Obrazy agenta usługom DevOps platformy Azure w witrynie GitHub](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Agent programu Operations Management Suite (OMS) w systemie Linux

* [Omówienie agenta pakietu Operations Management Suite (OMS) w systemie Linux](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md)

* [Operations Management Suite (OMS) obrazów w witrynie DockerHub](https://hub.docker.com/r/microsoft/oms/)

* [Operations Management Suite (OMS) obrazów w witrynie GitHub](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Interfejs wiersza polecenia platformy Microsoft Azure (CLI)

* [Microsoft Azure interfejs wiersza polecenia (CLI) obrazów w witrynie DockerHub](https://hub.docker.com/r/microsoft/azure-cli/) 

* [Microsoft Azure interfejs wiersza polecenia (CLI) obrazów w witrynie GitHub](https://github.com/Azure/azure-cli#Docker)

> [!NOTE]
> Jeśli nie masz subskrypcji platformy Azure, [Zarejestruj się dzisiaj](https://azure.microsoft.com/free/?b=16.48) bezpłatne konto 30-dniowej i Odbierz 200 USD środków na korzystanie z platformy Azure możesz wypróbować dowolną kombinację usług platformy Azure.

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Emulator usługi Cosmos DB platformy Microsoft Azure (tylko Windows kontenery)

* [Obrazy emulatora usługi Microsoft Azure Cosmos DB w witrynie DockerHub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Korzystanie z emulatora usługi Azure Cosmos DB do lokalnego tworzenia i testowania](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Eksplorowanie bogaty ekosystem rozwoju platformy Docker

Skoro wiesz już o różnych obrazów platformy Docker i platformy Docker, następnym krokiem jest zapoznaj się z bogatego ekosystemu platformy Docker. Poniższe linki dowiesz się, jak narzędzia Microsoft uzupełniają programowania kontenerów.

* [Ze sobą przy użyciu platformy .NET i Docker](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [Projektowanie i opracowywanie aplikacji obsługującej wiele kontenerów i opartych na Mikrousługach .NET](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [Rozszerzenie programu Visual Studio Code Docker](https://code.visualstudio.com/docs/languages/dockerfile)
* [Dowiedz się, jak używać usługi Azure Service Fabric](/azure/service-fabric/index)
* [Usługa Service Fabric Getting uruchomić próbki](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Korzyści z kontenerów Windows](/virtualization/windowscontainers/about/index#video-overview)
* [Praca z narzędzia Docker programu Visual Studio](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* [Wdrażanie obrazów platformy Docker z rejestru kontenerów platformy Azure w usłudze Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Debugowanie za pomocą programu Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [Praktycznym doświadczeniu z programem Visual Studio dla komputerów Mac, kontenerów i kod bez użycia serwera w chmurze](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Wprowadzenie do platformy Docker i programu Visual Studio dla komputerów Mac laboratorium](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Następne kroki

* [Poznaj podstawy korzystania z platformy Docker z programem .NET Core](docker-basics-dotnet-core.md)
* [Tworzenie obrazów platformy Docker programu .NET Core](building-net-docker-images.md)
