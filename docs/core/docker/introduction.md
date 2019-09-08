---
title: Wprowadzenie do platformy Docker
description: Ten artykuł zawiera wprowadzenie i Omówienie platformy Docker w kontekście aplikacji .NET Core.
ms.date: 03/20/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: 5da71215e3b539f10993677d23d89e2b8a49cb39
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799372"
---
# <a name="introduction-to-net-and-docker"></a>Wprowadzenie do platform .NET i Docker

Program .NET Core może być łatwo uruchamiany w kontenerze platformy Docker. Kontenery zapewniają lekki sposób izolowania aplikacji od pozostałej części systemu hosta, udostępniania tylko jądra i używania zasobów podanych dla aplikacji. Jeśli nie znasz platformy Docker, zdecydowanie zalecamy zapoznanie się z [dokumentacją z omówieniem](https://docs.docker.com/engine/docker-overview/)usługi Docker.

Aby uzyskać więcej informacji na temat instalowania platformy Docker, zobacz stronę pobierania dla [programu Docker Desktop: Wersja](https://www.docker.com/products/docker-desktop)Community.

## <a name="docker-basics"></a>Podstawy platformy Docker

Istnieje kilka koncepcji, z którymi należy się zapoznać. Klient platformy Docker ma program interfejsu wiersza polecenia służący do zarządzania obrazami i kontenerami. Jak wspomniano wcześniej, należy zapoznać się z dokumentacją dotyczącą [omówienia platformy Docker](https://docs.docker.com/engine/docker-overview/) . 

### <a name="images"></a>Obrazy

Obraz to uporządkowana kolekcja zmian systemu plików, która stanowi podstawę kontenera. Obraz nie ma stanu i jest tylko do odczytu. Znacznie czas, gdy obraz jest oparty na innym obrazie, ale z pewnym dostosowaniem. Na przykład podczas tworzenia nowego obrazu dla aplikacji można oprzeć go na istniejącym obrazie, który zawiera już środowisko uruchomieniowe platformy .NET Core.

Ponieważ kontenery są tworzone na podstawie obrazów, obrazy mają zestaw parametrów uruchomieniowych (takich jak uruchamianie pliku wykonywalnego), które są uruchamiane podczas uruchamiania kontenera.

### <a name="containers"></a>Kontenery

Kontener jest wystąpieniem możliwy do uruchomienia obrazu. Podczas kompilowania obrazu należy wdrożyć swoją aplikację i zależności. Następnie można utworzyć wystąpienie wielu kontenerów, każdy odizolowany od siebie nawzajem. Każde wystąpienie kontenera ma własny interfejs systemu plików, pamięci i interfejsu sieciowego.

### <a name="registries"></a>Wołuje

Rejestry kontenerów to kolekcja repozytoriów obrazów. Obrazy można oprzeć na obrazie rejestru. Kontenery można tworzyć bezpośrednio z obrazu w rejestrze. [Relacja między kontenerami platformy Docker, obrazami i rejestrami](../../architecture/microservices/container-docker-introduction/docker-containers-images-registries.md) jest ważnym pojęciem podczas [tworzenia i kompilowania kontenerów aplikacji lub mikrousług](../../architecture/microservices/architect-microservice-container-applications/index.md). Takie podejście znacznie skraca czas między programowaniem i wdrażaniem.

Platforma Docker ma publiczny rejestr hostowany w [centrum Docker](https://hub.docker.com/) , którego można użyć. [Obrazy powiązane z programem .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) są wymienione w centrum platformy Docker. 

Microsoft Container Registry (MCR) jest oficjalnym źródłem obrazów kontenerów dostarczonych przez firmę Microsoft. MCR jest oparta na Azure CDN, aby zapewnić globalnie zreplikowane obrazy. MCR nie ma jednak publicznej witryny sieci Web i głównym sposobem uczenia się obrazów kontenerów dostarczonych przez firmę Microsoft odbywa się za pomocą [stron centrum platformy Docker firmy Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).

### <a name="dockerfile"></a>Pliku dockerfile

**Pliku dockerfile** to plik, który definiuje zestaw instrukcji, które tworzą obraz. Każda instrukcja w **pliku dockerfile** tworzy warstwę w obrazie. W większości przypadków po odbudowaniu obrazu są przebudowywane tylko te warstwy, które uległy zmianie. **Pliku dockerfile** może być dystrybuowany do innych i umożliwia ich ponowne utworzenie w celu utworzenia nowego obrazu w taki sam sposób, w jaki został utworzony. Chociaż pozwala to na dystrybucję *instrukcji* dotyczących sposobu tworzenia obrazu, głównym sposobem dystrybuowania obrazu jest opublikowanie go w rejestrze.

## <a name="net-core-images"></a>Obrazy .NET Core

Oficjalne obrazy .NET Core Docker są publikowane w Container Registry firmy Microsoft (MCR) i można je odnajdywać w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Każde repozytorium zawiera obrazy różnych kombinacji platformy .NET (zestawu SDK lub środowiska uruchomieniowego) i systemu operacyjnego, których można użyć. 

Firma Microsoft udostępnia obrazy dostosowane do konkretnych scenariuszy. Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy skompilowane do uruchamiania aplikacji ASP.NET Core w środowisku produkcyjnym.

## <a name="azure-services"></a>Usługi platformy Azure

Różne kontenery obsługują usługi platformy Azure. Tworzysz obraz platformy Docker dla aplikacji i Wdróż go w jednej z następujących usług:

* [Usługa Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/)\
Skaluj i Organizuj kontenery systemu Linux przy użyciu Kubernetes.

* [Azure App Service](https://azure.microsoft.com/services/app-service/containers/)\
Wdrażaj aplikacje sieci Web lub interfejsy API przy użyciu kontenerów systemu Linux w środowisku PaaS.

* [Azure Container Instances](https://azure.microsoft.com/services/container-instances/)\
Hostowanie kontenera w chmurze bez żadnych usług zarządzania wyższego poziomu.

* [Azure Batch](https://azure.microsoft.com/services/batch/)\
Uruchamiaj powtarzające się zadania obliczeniowe przy użyciu kontenerów.

* [Service Fabric platformy Azure](https://azure.microsoft.com/services/service-fabric/)\
Podnieś, Przenieś i unowocześnienie aplikacji .NET do mikrousług przy użyciu kontenerów systemu Windows Server

* [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)\
Przechowuj obrazy kontenerów i zarządzaj nimi we wszystkich typach wdrożeń platformy Azure.

## <a name="next-steps"></a>Następne kroki

* [Dowiedz się, jak konteneryzowanie aplikację .NET Core.](build-docker-netcore-container.md)
* [Dowiedz się, jak konteneryzowanie aplikację ASP.NET Coreową.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
* [Wypróbuj samouczek uczenia się ASP.NET Core mikrousług.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [Informacje o narzędziach kontenera w programie Visual Studio](/visualstudio/containers/overview)
