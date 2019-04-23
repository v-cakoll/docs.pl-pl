---
title: Wprowadzenie do platformy Docker
description: Ten artykuł zawiera omówienie i wprowadzenie do platformy Docker w kontekście aplikacji .NET Core.
ms.date: 03/20/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: acf1307c241d9462278bc0fce5cf59fdde0750a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480732"
---
# <a name="introduction-to-net-and-docker"></a>Wprowadzenie do platform .NET i Docker

.NET core może łatwo Uruchamiaj w kontenerze platformy Docker. Kontenery umożliwiają uproszczone do izolowania aplikacji od reszty systemu hosta, udostępnianie tylko jądra i korzystanie z zasobów do aplikacji. Jeśli jesteś zaznajomiony z platformy Docker, zalecane jest przeczytanie platformy Docker [Przegląd dokumentacji](https://docs.docker.com/engine/docker-overview/).

Aby uzyskać więcej informacji o tym, jak zainstalować platformę Docker, zobacz stronę pobierania pakietu [pulpitu platformy Docker: Wersja Community](https://www.docker.com/products/docker-desktop).

## <a name="docker-basics"></a>Podstawy platformy docker

Istnieje kilka koncepcji, w których należy zapoznać się z. Klient platformy Docker ma program interfejs wiersza polecenia, który umożliwia zarządzanie obrazami i kontenerów. Jak wcześniej wspomniano, powinien trwać do przeczytania przez czytelników [Docker — omówienie](https://docs.docker.com/engine/docker-overview/) dokumentacji. 

### <a name="images"></a>Obrazy

Obraz jest uporządkowany zbiór zmian systemu plików, które stanowią podstawę kontenera. Obraz, który nie ma stanu i jest tylko do odczytu. Dużo czasu obrazu opiera się na inny obraz, ale niektóre dostosowania. Na przykład po utworzeniu nowego obrazu aplikacji będzie będzie oparty na istniejący obraz, która już zawiera środowisko uruchomieniowe platformy .NET Core.

Ponieważ kontenery są tworzone na podstawie obrazów, obrazy mają zestaw parametrów wykonywania (na przykład początkowy plik wykonywalny), które są uruchamiane podczas uruchamiania kontenera.

### <a name="containers"></a>Kontenery

Kontener jest możliwy do uruchomienia wystąpienia obrazu. Podczas tworzenia obrazu, możesz wdrożyć aplikację i zależności. Następnie można wdrożyć wiele kontenerów, każdy odizolowane od siebie nawzajem. Każde wystąpienie kontenera ma swój własny system plików, pamięci i interfejs sieciowy.

### <a name="registries"></a>rejestry

Rejestry kontenerów to zbiór repozytoriów obrazu. Obrazy można oprzeć na obrazie rejestru. Możesz tworzyć kontenery bezpośrednio z obrazu w rejestrze. [Relacji między kontenerami aparatu Docker, obrazy i rejestry](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) jest bardzo ważnym pojęciem podczas [projektowanie i tworzenie kontenerowych nimi aplikacji lub mikrousług](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). To podejście znacznie skraca czas między opracowywania i wdrażania.

Docker ma rejestru publicznego hostowanych na [usługi Docker Hub](https://hub.docker.com/) , można użyć. [Obrazy powiązane z platformy .NET core](https://hub.docker.com/_/microsoft-dotnet-core/) znajduje się w usłudze Docker Hub. 

Rejestr kontenerów firmy Microsoft (MCR) jest oficjalnym źródłem obrazów kontenerów firmy Microsoft. MCR jest oparta na usługi Azure CDN zapewnienie replikowany globalnie obrazów. Jednak MCR nie publiczną witrynę sieci Web i podstawowym sposobem, aby dowiedzieć się więcej informacji o obrazach kontenera dostarczonych przez firmę Microsoft za pośrednictwem [stron usługi Docker Hub Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).

### <a name="dockerfile"></a>Dockerfile

A **pliku Dockerfile** jest plikiem, który definiuje zestaw instrukcji, która tworzy obraz. Każdej instrukcji w **pliku Dockerfile** tworzy warstwę na obrazie. W większości przypadków podczas ponownego kompilowania obrazu odbudować są tylko warstwy, które uległy zmianie. **Pliku Dockerfile** mogą być dystrybuowane do innych osób i można je odtworzyć, aby utworzyć nowy obraz w taki sam sposób został utworzony. A dzięki temu można rozpowszechniać *instrukcje* na sposób tworzenia obrazu, główny sposób dystrybucji obrazu jest opublikowanie jej do rejestru.

## <a name="net-core-images"></a>Obrazy platformy .NET core

Oficjalne obrazy Docker w programie .NET Core są publikowane do rejestru kontenerów firmy Microsoft (MCR) i są wykrywalni na [repozytorium usługi Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/). Każdego repozytorium zawiera obrazy dla różnych kombinacji .NET (zestaw SDK lub środowisko uruchomieniowe) i systemu operacyjnego, którego można używać. 

Firma Microsoft udostępnia obrazy, które są dostosowane do określonych scenariuszy. Na przykład [repozytorium platformy ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy, które są kompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.

## <a name="azure-services"></a>Usługi platformy Azure

Różne usługi platformy Azure obsługują kontenery. Tworzenie obrazu platformy Docker dla aplikacji i wdrożyć go na jeden z następujących usług:

* [Usługa Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/)\
Skalowanie i organizowanie kontenerów systemu Linux przy użyciu platformy Kubernetes.

* [Azure App Service](https://azure.microsoft.com/services/app-service/containers/)\
Wdrażanie aplikacji sieci web lub interfejsów API przy użyciu kontenerów systemu Linux w środowisku PaaS.

* [Usługa Azure Container Instances](https://azure.microsoft.com/services/container-instances/)\
Hosta kontenera w chmurze bez żadnych wyższego poziomu usługi zarządzania.

* [Azure Batch](https://azure.microsoft.com/services/batch/)\
Uruchamiaj powtarzalne zadania obliczeniowe przy użyciu kontenerów.

* [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)\
Przenoszenie, shift i modernizowanie aplikacji .NET do mikrousług przy użyciu kontenerów systemu Windows Server

* [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)\
Store i Zarządzaj obrazami kontenerów we wszystkich typach wdrożeń platformy Azure.

## <a name="next-steps"></a>Następne kroki

* [Dowiedz się, jak konteneryzowanie aplikacji .NET Core.](build-docker-netcore-container.md)
* [Wypróbuj samouczek Dowiedz się, ASP.NET Core Mikrousług.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
