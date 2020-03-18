---
title: Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Do czego cel systemu operacyjnego za pomocą kontenerów .NET
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501863"
---
# <a name="what-os-to-target-with-net-containers"></a>Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET

Biorąc pod uwagę różnorodność systemów operacyjnych obsługiwanych przez platformę Docker i różnice między .NET Framework i .NET Core, należy kierować określone systemy operacyjne i konkretne wersje w zależności od struktury, której używasz.

W przypadku systemu Windows można używać systemu Windows Server Core lub Systemu Windows Nano Server. Te wersje systemu Windows zapewniają różne cechy (usługi IIS w systemie Windows Server Core w porównaniu z samoobsługowym serwerem sieci Web, takim jak Kestrel w nano serwerze), które mogą być potrzebne odpowiednio przez program .NET Framework lub .NET Core.

W przypadku Linuksa wiele dystrybucji jest dostępnych i obsługiwanych w oficjalnych obrazach dockera .NET (takich jak Debian).

Na rysunku 3-1 można zobaczyć możliwą wersję systemu operacyjnego w zależności od używanej struktury .NET.

![Diagram przedstawiający, którego systemu operacyjnego użyć z kontenerami .NET.](./media/net-container-os-targets/targeting-operating-systems.png)

**Rysunek 3-1.** Systemy operacyjne do docelowego w zależności od wersji platformy .NET

Podczas wdrażania starszych aplikacji .NET Framework musisz kierować system Windows Server Core, zgodny ze starszymi aplikacjami i usługami IIS, ale ma większy obraz. Podczas wdrażania aplikacji .NET Core można kierować na system Windows Nano Server, który jest zoptymalizowany pod kątem chmury, używa kestrelu i jest mniejszy i uruchamia się szybciej. Możesz również kierować reklamy na Linuksa, wspierając Debiana, Alpine i inne. Używa również Kestrel, jest mniejszy i zaczyna się szybciej.

Można również utworzyć własny obraz platformy Docker w przypadkach, gdy chcesz użyć innej dystrybucji systemu Linux lub gdzie chcesz obraz z wersjami nie dostarczonymi przez firmę Microsoft. Na przykład można utworzyć obraz z ASP.NET Core uruchomiony na tradycyjnych .NET Framework i Windows Server Core, który jest nie tak typowy scenariusz dla platformy Docker.

> [!IMPORTANT]
> Podczas korzystania z obrazów windows server core może się okazać, że brakuje niektórych bibliotek DLL w porównaniu z pełnymi obrazami systemu Windows. Możesz rozwiązać ten problem, tworząc niestandardowy obraz Server Core, dodając brakujące pliki w czasie kompilacji obrazu, jak wspomniano w tym [komentarzu GitHub](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).

Po dodaniu nazwy obrazu do pliku Dockerfile można wybrać system operacyjny i wersję w zależności od używanego tagu, jak w poniższych przykładach:

| Image (Obraz) | Komentarze |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:3.1 | .NET Core 3.1 multi-architecture: Obsługuje Linux i Windows Nano Server w zależności od hosta platformy Docker. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1 | ASP.NET core 3.1 multi-architecture: Obsługuje Linux i Windows Nano Server w zależności od hosta platformy Docker. <br/> Obraz aspnetcore ma kilka optymalizacji dla ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim | .NET Core 3.1 tylko w dystrybucji Debiana |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809 | Tylko środowisko uruchomieniowe programu .NET Core 3.1 w systemie Windows Nano Server (wersja 1809 systemu Windows Server) |

## <a name="additional-resources"></a>Zasoby dodatkowe

- **BitmapDecoder kończy się niepowodzeniem z powodu braku pliku WindowsCodecsExt.dll (problem z githubem)**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Poprzedni](container-framework-choice-factors.md)
> [następny](official-net-docker-images.md)
