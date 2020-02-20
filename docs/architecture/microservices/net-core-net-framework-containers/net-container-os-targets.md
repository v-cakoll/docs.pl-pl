---
title: Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | System operacyjny, który ma być przeznaczony dla kontenerów platformy .NET
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501863"
---
# <a name="what-os-to-target-with-net-containers"></a>Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET

Mając na względy różnorodność systemów operacyjnych obsługiwanych przez platformę Docker i różnice między .NET Framework i .NET Core, należy wskazać określony system operacyjny i konkretne wersje w zależności od używanej platformy.

W przypadku systemu Windows można użyć systemu Windows Server Core lub Windows nano Server. Te wersje systemu Windows zapewniają różne cechy (IIS w systemie Windows Server Core oraz samodzielny serwer sieci Web, taki jak Kestrel na serwerze nano Server), który może być odpowiednio wymagany przez .NET Framework lub .NET Core.

W przypadku systemu Linux dostępne są wiele dystrybucje i są obsługiwane w oficjalnych obrazach platformy Docker .NET (na przykład Debian).

Na rysunku 3-1 można zobaczyć ewentualną wersję systemu operacyjnego w zależności od używanego programu .NET Framework.

![Diagram przedstawiający, z których systemu operacyjnego korzystać z kontenerów platformy .NET.](./media/net-container-os-targets/targeting-operating-systems.png)

**Rysunek 3-1.** Systemy operacyjne przeznaczone do celów w zależności od wersji programu .NET Framework

W przypadku wdrażania starszych aplikacji .NET Framework należy określić system Windows Server Core, który jest zgodny ze starszymi aplikacjami i usługami IIS, ale ma większy obraz. Podczas wdrażania aplikacji .NET Core można kierować do systemu Windows nano Server, który jest zoptymalizowany pod kątem chmury, używa Kestrel i jest mniejszy i uruchamiany szybciej. Możesz również wskazać system Linux, obsługujący Debian, Alpine i inne. Program używa również Kestrel, jest mniejszy i uruchamia się szybciej.

Możesz również utworzyć własny obraz platformy Docker w przypadku, gdy chcesz użyć innego dystrybucji systemu Linux lub jeśli chcesz, aby obraz z wersjami nie został dostarczony przez firmę Microsoft. Można na przykład utworzyć obraz z ASP.NET Core uruchomionym na tradycyjnych .NET Framework i Windows Server Core, który jest scenariuszem nietypowym dla platformy Docker.

> [!IMPORTANT]
> W przypadku korzystania z obrazów systemu Windows Server Core może się zdarzyć, że brakuje niektórych bibliotek DLL w porównaniu z pełnymi obrazami systemu Windows. Aby rozwiązać ten problem, można utworzyć niestandardowy obraz serwera podstawowego, dodając brakujące pliki w czasie kompilacji obrazu, jak wspomniano w [komentarzu](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)w serwisie GitHub.

Po dodaniu nazwy obrazu do pliku pliku dockerfile można wybrać system operacyjny i wersję w zależności od użytego tagu, jak w następujących przykładach:

| Image (Obraz) | Komentarze |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:3.1 | Architektura .NET Core 3,1 — Obsługa systemu Linux i Windows nano Server w zależności od hosta platformy Docker. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1 | Wieloarchitektura ASP.NET Core 3,1: obsługuje systemy Linux i Windows nano Server w zależności od hosta platformy Docker. <br/> Obraz aspnetcore ma kilka optymalizacji dla ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim | Środowisko uruchomieniowe programu .NET Core 3,1 — tylko w systemie Linux Debian dystrybucji |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809 | Środowisko uruchomieniowe programu .NET Core 3,1 — tylko w systemie Windows nano Server (system Windows Server w wersji 1809) |

## <a name="additional-resources"></a>Dodatkowe zasoby

- **BitmapDecoder nie powiodła się z powodu braku pliku WindowsCodecsExt. dll (problem z usługą GitHub)**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Poprzednie](container-framework-choice-factors.md)
> [dalej](official-net-docker-images.md)
