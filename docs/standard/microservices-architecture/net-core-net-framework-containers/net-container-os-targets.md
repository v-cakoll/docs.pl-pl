---
title: Jakiego systemu operacyjnego do docelowego z kontenerami .NET
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Jakiego systemu operacyjnego do docelowego z kontenerami .NET"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
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

-   Microsoft /**dotnet:2.0.0 — środowisko uruchomieniowe-Joasia**

        .NET Core 2.0 runtime-only on Linux

-   Microsoft /**dotnet:2.0.0 — środowisko uruchomieniowe-nanoserver-1709** 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   Microsoft /**aspnetcore:2.0**
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
[Poprzednie] (kontener framework wybór factors.md) [dalej] (oficjalne net-docker-images.md)
