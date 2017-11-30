---
title: "Za pomocą poleceń programu Windows PowerShell w plik DockerFile skonfigurować kontenery systemu Windows (standardowa Docker w podstawie)"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: f7e92b0f1c749e2c00e3afc4ffcfc2fc88d7628f
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2017
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
