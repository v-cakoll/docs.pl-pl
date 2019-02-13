---
title: Używanie poleceń programu Windows PowerShell w pliku DockerFile do konfigurowania kontenerów Windows (standardzie platformy Docker na podstawie)
description: Dowiedz się, jak podczas pracy z platformą Docker w kontenerach Windows przy użyciu programu PowerShell
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: df9e98e3f963b6492e1008455251b61a8cb6e771
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219974"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Używanie poleceń programu Windows PowerShell w pliku DockerFile do konfigurowania kontenerów Windows (standardzie platformy Docker na podstawie)

Za pomocą [kontenery Windows](/virtualization/windowscontainers/about/index), można przekonwertować istniejące aplikacje Windows do obrazów platformy Docker i wdrożyć je przy użyciu tych samych narzędzi, jak w pozostałych ekosystemie Docker.

Aby korzystać z kontenerów Windows, wystarczy do tworzenia poleceń programu Windows PowerShell w pliku DockerFile, jak pokazano w poniższym przykładzie:

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

W tym przypadku używamy programu Windows PowerShell do zainstalowania obrazu podstawowego systemu Windows Server Core, a także usług IIS.

W podobny sposób, również wystarczą poleceń programu Windows PowerShell do skonfigurowania dodatkowych składników, takich jak tradycyjnych ASP.NET 4.x i .NET 4.6 lub innego oprogramowania Windows, jak pokazano poniżej:

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Poprzednie](visual-studio-tools-for-docker.md)
>[dalej](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
