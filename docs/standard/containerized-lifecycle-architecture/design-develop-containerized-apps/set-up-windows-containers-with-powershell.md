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
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="8ba7b-104">Za pomocą poleceń programu Windows PowerShell w plik DockerFile skonfigurować kontenery systemu Windows (standardowa Docker w podstawie)</span><span class="sxs-lookup"><span data-stu-id="8ba7b-104">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="8ba7b-105">Z [kontenery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), można przekonwertować istniejących aplikacji systemu Windows, aby obrazy usługi Docker i wdrożyć je przy użyciu tego samego narzędzi jako rest ekosystemu Docker.</span><span class="sxs-lookup"><span data-stu-id="8ba7b-105">With [Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="8ba7b-106">Aby użyć kontenery systemu Windows, wystarczy do tworzenia poleceń programu Windows PowerShell w plik DockerFile, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8ba7b-106">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="8ba7b-107">W takim przypadku używamy środowiska Windows PowerShell do zainstalowania obrazu podstawowego systemu Windows Server Core, a także usług IIS.</span><span class="sxs-lookup"><span data-stu-id="8ba7b-107">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="8ba7b-108">W podobny sposób można umożliwia również poleceń programu Windows PowerShell Konfigurowanie dodatkowych składników, takich jak tradycyjnych ASP.NET 4.x i .NET 4.6 lub innego oprogramowania systemu Windows, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="8ba7b-108">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
<span data-ttu-id="8ba7b-109">[Poprzednie] (visual-studio narzędzia do docker.md) [dalej] (.. /docker-devops-Workflow/index.MD)</span><span class="sxs-lookup"><span data-stu-id="8ba7b-109">[Previous] (visual-studio-tools-for-docker.md) [Next] (../docker-devops-workflow/index.md)</span></span>
