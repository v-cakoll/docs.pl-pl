---
title: Używanie poleceń programu Windows PowerShell w pliku DockerFile do konfigurowania kontenerów Windows (standardzie platformy Docker na podstawie)
description: Dowiedz się, jak podczas pracy z platformą Docker w kontenerach Windows przy użyciu programu PowerShell
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: d9c0bc28f62d44eb7471b99c63055ef43da12a69
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664708"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Używanie poleceń programu Windows PowerShell w pliku DockerFile do konfigurowania kontenerów Windows (standardzie platformy Docker na podstawie)

Za pomocą [kontenery Windows](/virtualization/windowscontainers/about/index), można przekonwertować istniejące aplikacje Windows do obrazów platformy Docker i wdrożyć je przy użyciu tych samych narzędzi, jak w pozostałych ekosystemie Docker.

Aby korzystać z kontenerów Windows, wystarczy do tworzenia poleceń programu Windows PowerShell w pliku DockerFile, jak pokazano w poniższym przykładzie:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

W tym przypadku używamy programu Windows PowerShell do zainstalowania obrazu podstawowego systemu Windows Server Core, a także usług IIS.

W podobny sposób, również wystarczą poleceń programu Windows PowerShell do skonfigurowania dodatkowych składników, takich jak tradycyjnych ASP.NET 4.x i .NET 4.6 lub innego oprogramowania Windows, jak pokazano poniżej:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Poprzednie](visual-studio-tools-for-docker.md)
>[dalej](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
