---
title: Wprowadzenie do platformy Docker
description: Ten artykuł zawiera wprowadzenie i omówienie platformy Docker w kontekście aplikacji .NET Core.
ms.date: 03/20/2019
ms.custom: mvc
ms.openlocfilehash: eedfd1e7c1b361beb9d4f271e739657ef5e894a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157794"
---
# <a name="introduction-to-net-and-docker"></a>Wprowadzenie do platform .NET i Docker

Program .NET Core można łatwo uruchomić w kontenerze platformy Docker. Kontenery zapewniają lekki sposób izolowania aplikacji od reszty systemu hosta, udostępnianie tylko jądra i przy użyciu zasobów podanych do aplikacji. Jeśli nie znasz platformy Docker, zdecydowanie zaleca się przeczytanie [dokumentacji przeglądu platformy](https://docs.docker.com/engine/docker-overview/)Docker.

Aby uzyskać więcej informacji na temat instalowania platformy Docker, zobacz stronę pobierania aplikacji [Docker Desktop: Community Edition](https://www.docker.com/products/docker-desktop).

## <a name="docker-basics"></a>Podstawy platformy Docker

Istnieje kilka pojęć, które powinieneś znać. Klient platformy Docker ma identyfikator acli, który służy do zarządzania obrazami i kontenerami. Jak wcześniej wspomniano, należy trochę czasu, aby przeczytać dokumentację [omówienie platformy Docker.](https://docs.docker.com/engine/docker-overview/)

### <a name="images"></a>Obrazy

Obraz jest uporządkowaną kolekcją zmian systemu plików, które stanowią podstawę kontenera. Obraz nie ma stanu i jest tylko do odczytu. Dużo czasu obraz jest oparty na innym obrazie, ale z pewnym dostosowaniem. Na przykład podczas tworzenia nowego obrazu dla aplikacji, należy oprzeć go na istniejący obraz, który już zawiera .NET Core runtime.

Ponieważ kontenery są tworzone na podstawie obrazów, obrazy mają zestaw parametrów uruchamiania (takich jak początkowy plik wykonywalny), które są uruchamiane po uruchomieniu kontenera.

### <a name="containers"></a>Kontenery

Kontener jest instancją obrazu z dobytku. Podczas tworzenia obrazu można wdrożyć aplikację i zależności. Następnie można utworzyć wiele kontenerów, z których każdy jest odizolowany od siebie. Każde wystąpienie kontenera ma własny system plików, pamięć i interfejs sieciowy.

### <a name="registries"></a>Rejestry

Rejestry kontenerów są kolekcją repozytoriów obrazów. Obrazy można oprzeć na obrazie rejestru. Kontenery można tworzyć bezpośrednio z obrazu w rejestrze. [Relacja między kontenerami platformy Docker, obrazami i rejestrami](../../architecture/microservices/container-docker-introduction/docker-containers-images-registries.md) jest ważną koncepcją podczas [projektowania i tworzenia konteneryzowanych aplikacji lub mikrousług.](../../architecture/microservices/architect-microservice-container-applications/index.md) Takie podejście znacznie skraca czas między programowaniem a wdrażaniem.

Docker ma rejestr publiczny hostowany w [centrum docker Hub,](https://hub.docker.com/) którego można używać. [Obrazy pokrewne .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) są wyświetlane w centrum docker hub.

Rejestr kontenerów firmy Microsoft (MCR) jest oficjalnym źródłem obrazów kontenerów dostarczonych przez firmę Microsoft. McR jest zbudowany na usłudze Azure CDN, aby zapewnić obrazy replikowane globalnie. Jednak mcr nie ma publicznej witryny sieci Web, a podstawowym sposobem na poznanie obrazów kontenerów dostarczonych przez firmę Microsoft jest za pośrednictwem [stron Centrum docker firmy Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).

### <a name="dockerfile"></a>Plik dockerfile

**Plik Dockerfile** to plik definiujący zestaw instrukcji, który tworzy obraz. Każda instrukcja w **pliku Dockerfile** tworzy warstwę w obrazie. W przeważającej części podczas przebudowy obrazu tylko warstwy, które uległy zmianie, są przebudowywane. **Plik Dockerfile** może być dystrybuowany do innych osób i umożliwia im ponowne utworzenie nowego obrazu w taki sam sposób, w jaki został utworzony. Dzięki temu można rozpowszechniać *instrukcje dotyczące* tworzenia obrazu, głównym sposobem rozpowszechniania obrazu jest opublikowanie go w rejestrze.

## <a name="net-core-images"></a>Obrazy .NET Core

Oficjalne obrazy platformy Docker platformy .NET Core są publikowane w rejestrze kontenerów firmy Microsoft (MCR) i można je wykryć w [repozytorium Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Każde repozytorium zawiera obrazy dla różnych kombinacji .NET (SDK lub Runtime) i OS, których można użyć.

Firma Microsoft udostępnia obrazy dostosowane do określonych scenariuszy. Na przykład [repozytorium ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) zawiera obrazy, które są tworzone do uruchamiania ASP.NET aplikacji Core w środowisku produkcyjnym.

## <a name="azure-services"></a>Usługi platformy Azure

Różne usługi platformy Azure obsługują kontenery. Utwórz obraz platformy Docker dla aplikacji i wdrożyć go w jednej z następujących usług:

- [Usługa Azure Kubernetes (AKS)](https://azure.microsoft.com/services/kubernetes-service/)\
Skalowanie i organizowanie kontenerów systemu Linux przy użyciu kubernetes.

- [Usługa aplikacji platformy Azure](https://azure.microsoft.com/services/app-service/containers/)\
Wdrażanie aplikacji sieci Web lub interfejsów API przy użyciu kontenerów systemu Linux w środowisku PaaS.

- [Wystąpienia kontenera platformy Azure](https://azure.microsoft.com/services/container-instances/)\
Hostuj swój kontener w chmurze bez żadnych usług zarządzania wyższego poziomu.

- [Azure Batch](https://azure.microsoft.com/services/batch/)\
Uruchamianie powtarzających się zadań obliczeniowych przy użyciu kontenerów.

- [Sieć szkieletowa usług platformy Azure](https://azure.microsoft.com/services/service-fabric/)\
Podnoszenie, przesuwanie i modernizyzywanie aplikacji .NET do mikrousług przy użyciu kontenerów systemu Windows Server.

- [Rejestr kontenerów platformy Azure](https://azure.microsoft.com/services/container-registry/)\
Przechowywanie obrazów kontenerów i zarządzanie nimi we wszystkich typach wdrożeń platformy Azure.

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się, jak konteneryzować aplikację .NET Core.](build-container.md)
- [Dowiedz się, jak konteneryzować aplikację ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Wypróbuj samouczek Learn ASP.NET Core Microservice.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Dowiedz się więcej o narzędziach kontenerów w programie Visual Studio](/visualstudio/containers/overview)
