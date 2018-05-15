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
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="7c741-103">Za pomocą poleceń programu Windows PowerShell w plik DockerFile skonfigurować kontenery systemu Windows (standardowa Docker w podstawie)</span><span class="sxs-lookup"><span data-stu-id="7c741-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="7c741-104">Z [kontenery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), można przekonwertować istniejących aplikacji systemu Windows, aby obrazy usługi Docker i wdrożyć je przy użyciu tego samego narzędzi jako rest ekosystemu Docker.</span><span class="sxs-lookup"><span data-stu-id="7c741-104">With [Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="7c741-105">Aby użyć kontenery systemu Windows, wystarczy do tworzenia poleceń programu Windows PowerShell w plik DockerFile, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7c741-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="7c741-106">W takim przypadku używamy środowiska Windows PowerShell do zainstalowania obrazu podstawowego systemu Windows Server Core, a także usług IIS.</span><span class="sxs-lookup"><span data-stu-id="7c741-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="7c741-107">W podobny sposób można umożliwia również poleceń programu Windows PowerShell Konfigurowanie dodatkowych składników, takich jak tradycyjnych ASP.NET 4.x i .NET 4.6 lub innego oprogramowania systemu Windows, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="7c741-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
<span data-ttu-id="7c741-108">[Poprzednie] (visual-studio narzędzia do docker.md) [dalej] (.. /docker-devops-Workflow/index.MD)</span><span class="sxs-lookup"><span data-stu-id="7c741-108">[Previous] (visual-studio-tools-for-docker.md) [Next] (../docker-devops-workflow/index.md)</span></span>
