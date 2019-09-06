---
title: Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | System operacyjny, który ma być przeznaczony dla kontenerów platformy .NET
ms.date: 01/07/2019
ms.openlocfilehash: 6f160aeba5257722490788271e6f89359342cc0d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296510"
---
# <a name="what-os-to-target-with-net-containers"></a>Jakiego systemu operacyjnego należy używać docelowo z kontenerami .NET

Mając na względy różnorodność systemów operacyjnych obsługiwanych przez platformę Docker i różnice między .NET Framework i .NET Core, należy wskazać określony system operacyjny i konkretne wersje w zależności od używanej platformy.

W przypadku systemu Windows można użyć systemu Windows Server Core lub Windows nano Server. Te wersje systemu Windows zapewniają różne cechy (IIS w systemie Windows Server Core oraz samodzielny serwer sieci Web, taki jak Kestrel na serwerze nano Server), który może być odpowiednio wymagany przez .NET Framework lub .NET Core.

W przypadku systemu Linux dostępne są wiele dystrybucje i są obsługiwane w oficjalnych obrazach platformy Docker .NET (na przykład Debian).

Na rysunku 3-1 można zobaczyć ewentualną wersję systemu operacyjnego w zależności od używanego programu .NET Framework.

![W przypadku wdrażania starszych aplikacji .NET Framework musisz mieć system Windows Server Core, który jest zgodny ze starszymi aplikacjami i usługami IIS, ma większy obraz. Podczas wdrażania aplikacji .NET Core można kierować do systemu Windows nano Server, który jest zoptymalizowany pod kątem chmury, używa Kestrel i jest mniejszy i uruchamiany szybciej. Możesz również wskazać system Linux, obsługujący Debian, Alpine i inne. Używa także Kestrel i jest mniejszy i uruchamiany szybciej.](./media/image1.png)

**Rysunek 3-1.** Systemy operacyjne przeznaczone do celów w zależności od wersji programu .NET Framework

Możesz również utworzyć własny obraz platformy Docker w przypadku, gdy chcesz użyć innego dystrybucji systemu Linux lub jeśli chcesz, aby obraz z wersjami nie został dostarczony przez firmę Microsoft. Można na przykład utworzyć obraz z ASP.NET Core uruchomionym na tradycyjnych .NET Framework i Windows Server Core, który jest scenariuszem nietypowym dla platformy Docker.

Po dodaniu nazwy obrazu do pliku pliku dockerfile można wybrać system operacyjny i wersję w zależności od użytego tagu, jak w następujących przykładach:

<table>
<thead>
<tr class="header">
<th>Obraz</th>
<th>Komentarze</th>
</tr>
</thead>
<tbody>
<tr>
<td>mcr.microsoft.com/dotnet/core/runtime:2.2</td>
<td>Architektura .NET Core 2,2: Obsługuje systemy Linux i Windows nano Server w zależności od hosta platformy Docker.</td>
</tr>
<tr class="odd">
<td>mcr.microsoft.com/dotnet/core/aspnet:2.2</td>
<td><p>Obsługa wieloarchitektur ASP.NET Core 2,2: Obsługuje systemy Linux i Windows nano Server w zależności od hosta platformy Docker.</p>
<p>Obraz aspnetcore ma kilka optymalizacji dla ASP.NET Core.</p></td>
</tr>
<tr class="even">
<td>mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</td>
<td>Środowisko uruchomieniowe programu .NET Core 2,2 — tylko w systemie Linux Alpine dystrybucji</td>
</tr>
<tr class="odd">
<td>mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</td>
<td>Środowisko uruchomieniowe programu .NET Core 2,2 — tylko w systemie Windows nano Server (system Windows Server w wersji 1803)</td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> [Poprzedni](container-framework-choice-factors.md)Następny
> [](official-net-docker-images.md)
