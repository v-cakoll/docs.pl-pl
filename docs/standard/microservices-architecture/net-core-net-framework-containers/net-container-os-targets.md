---
title: Jakiego systemu operacyjnego do docelowego z kontenerami .NET
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Jakiego systemu operacyjnego do docelowego z kontenerami .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 53b279a3325ae0fb662cd91a6f7f454b765196ff
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251015"
---
# <a name="what-os-to-target-with-net-containers"></a>Jakiego systemu operacyjnego do docelowego z kontenerami .NET

Biorąc pod uwagę różnorodność systemów operacyjnych obsługiwanych przez Docker i różnice między .NET Framework i .NET Core, docelowych określonego systemu operacyjnego i określonych wersji zależnie od używanego. 

W systemie Windows można użyć systemu Windows Server Core lub serwerze Nano systemu Windows. Te wersje systemu Windows zawierają różne charakterystyki (usługi IIS w systemie Windows Server Core a serwerem sieci web hostowania samoobsługowego, takich jak Kestrel Nano Server), które mogą być wymagane odpowiednio przez .NET Framework lub .NET Core. 

Dla systemu Linux wiele dystrybucjach są dostępne i obsługiwane w oficjalnego obrazy usługi .NET Docker (na przykład Debian).

W rysunku 3-1 spowoduje możliwe wersji systemu operacyjnego, w zależności od używane w programie .NET framework.

![](./media/image1.png)

**Rysunek 3-1.** Systemy operacyjne, na docelowy w zależności od wersji programu .NET framework

Można też utworzyć własny obraz Docker w przypadkach, której chcesz użyć innego distro Linux lub miejscu obrazu z wersji nie jest obsługiwane przez firmę Microsoft. Na przykład może utworzyć obrazu z platformy ASP.NET Core systemem tradycyjne .NET Framework i Server Core systemu Windows, czyli scenariusza nie tak typowe dla platformy Docker.

Nazwa obrazu należy dodać do pliku plik Dockerfile, można wybrać system operacyjny i wersję, w zależności od tag, którego używasz, na przykład:

-   Microsoft /**dotnet:2.1 — środowisko uruchomieniowe**

        .NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.

-   Microsoft /**dotnet:2.1 — aspnetcore — środowisko uruchomieniowe**
    
        ASP.NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 

-   Microsoft /**dotnet:2.1 — aspnetcore — środowisko uruchomieniowe-alpine** 

        .NET Core 2.1 runtime-only on Linux Alpine distro

-   Microsoft /**dotnet:2.1 — aspnetcore — środowisko uruchomieniowe-nanoserver-1803** 

        .NET Core 2.1 runtime-only on Windows Nano Server (Windows Server version 1803)




>[!div class="step-by-step"]
[Poprzednie] (kontener framework wybór factors.md) [dalej] (oficjalne net-docker-images.md)
