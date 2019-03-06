---
title: Jakiego systemu operacyjnego docelowo z kontenerami .NET
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Jakiego systemu operacyjnego docelowo z kontenerami .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 9e1d07e48d88376efb5fbdbdadc999c8dcd5082d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374911"
---
# <a name="what-os-to-target-with-net-containers"></a>Jakiego systemu operacyjnego docelowo z kontenerami .NET

Biorąc pod uwagę różnorodność systemów operacyjnych obsługiwanych przez firmy Docker i różnice między .NET Framework i .NET Core, powinien dotyczyć określonego systemu operacyjnego i określonych wersji, w zależności od tego, w ramach, którego używasz.

Dla Windows można użyć systemu Windows Server Core lub Windows Nano Server. Te wersje Windows zawierają różne charakterystyki (usługi IIS w systemie Windows Server Core i server samodzielnie hostowanej sieci web, takich jak Kestrel w systemie Nano Server), które mogą być wymagane przez program .NET Framework lub .NET Core, odpowiednio.

W przypadku systemu Linux dystrybucje wielu są dostępne i jest obsługiwany w oficjalne obrazy Docker w programie .NET (na przykład Debian).

W rysunek 3-1 można zobaczyć możliwe wersji systemu operacyjnego, w zależności od programu .NET framework używane.

![Podczas wdrażania starszych aplikacji .NET Framework ma pod kątem systemu Windows Server Core, zgodne ze starszych aplikacji i usług IIS, ma większy obraz. W przypadku wdrażania aplikacji .NET Core, można wskazać Windows Nano Server, który jest zoptymalizowany pod kątem chmury, używa Kestrel i jest mniejszy i rozpoczyna się szybciej. Można również przeznaczać systemu Linux, Debian Alpine i innych pomocniczych. Również używa Kestrel jest mniejszy i rozpoczyna się szybciej.](./media/image1.png)

**Rysunek 3-1.** Systemy operacyjne pod kątem w zależności od wersji programu .NET framework

Można również utworzyć obraz platformy Docker w przypadkach, gdzie chcesz użyć innego dystrybucja systemu Linux lub którego obraz z wersjami, które nie są obsługiwane przez firmę Microsoft. Na przykład utworzyć obraz przy użyciu platformy ASP.NET Core uruchomionych na tradycyjnych .NET Framework i systemie Windows Server Core, która jest nie tak typowe platformy Docker.

Po dodaniu nazwy obrazu do pliku Dockerfile, można wybrać system operacyjny i wersję, w zależności od tag, którego używasz, jak w następujących przykładach:

<table>
<thead>
<tr class="header">
<th>Obraz</th>
<th>Komentarze</th>
</tr>
</thead>
<tbody>
<tr>
<td>Microsoft / dotnet:2.2 — środowisko uruchomieniowe</td>
<td>Architektura wielu platformy .NET core 2.2: Obsługa systemu Linux i Windows Nano Server, w zależności od hosta platformy Docker.</td>
</tr>
<tr class="odd">
<td>Microsoft / dotnet:2.2-aspnetcore-środowiska uruchomieniowego</td>
<td><p>Architektura wielu platformy ASP.NET Core 2.2: Obsługa systemu Linux i Windows Nano Server, w zależności od hosta platformy Docker.</p>
<p>Obraz aspnetcore ma kilka optymalizacji dla platformy ASP.NET Core.</p></td>
</tr>
<tr class="even">
<td>Microsoft / dotnet:2.2-aspnetcore-runtime-alpine</td>
<td>.NET core 2.2 tylko do środowiska uruchomieniowego na Alpine dystrybucja systemu Linux</td>
</tr>
<tr class="odd">
<td>Microsoft / dotnet:2.2-aspnetcore-runtime-nanoserver-1803</td>
<td>.NET core 2.2 tylko do środowiska uruchomieniowego na serwerze Windows Nano Server (Windows Server w wersji 1803)</td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> [Poprzednie](container-framework-choice-factors.md)
> [dalej](official-net-docker-images.md)