---
title: Za pomocą poleceń programu Windows PowerShell w plik DockerFile skonfigurować kontenery systemu Windows (standardowa Docker w podstawie)
description: Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: 48af11117ec8eb0034d9557a332b89d3418d4b31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567861"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Za pomocą poleceń programu Windows PowerShell w plik DockerFile skonfigurować kontenery systemu Windows (standardowa Docker w podstawie)

Z [kontenery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), można przekonwertować istniejących aplikacji systemu Windows, aby obrazy usługi Docker i wdrożyć je przy użyciu tego samego narzędzi jako rest ekosystemu Docker.

Aby użyć kontenery systemu Windows, wystarczy do tworzenia poleceń programu Windows PowerShell w plik DockerFile, jak pokazano w poniższym przykładzie:

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

W takim przypadku używamy środowiska Windows PowerShell do zainstalowania obrazu podstawowego systemu Windows Server Core, a także usług IIS.

W podobny sposób można umożliwia również poleceń programu Windows PowerShell Konfigurowanie dodatkowych składników, takich jak tradycyjnych ASP.NET 4.x i .NET 4.6 lub innego oprogramowania systemu Windows, jak pokazano poniżej:

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
[Poprzednie] (visual-studio narzędzia do docker.md) [dalej] (.. /docker-devops-Workflow/index.MD)
