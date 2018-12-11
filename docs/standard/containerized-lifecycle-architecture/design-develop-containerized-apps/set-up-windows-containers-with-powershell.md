---
title: Używanie poleceń programu Windows PowerShell w pliku DockerFile do konfigurowania kontenerów Windows (standardzie platformy Docker na podstawie)
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: 5e85beea0efbee6a2b6594e3a49d705505a36e1c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149396"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="460ea-103">Używanie poleceń programu Windows PowerShell w pliku DockerFile do konfigurowania kontenerów Windows (standardzie platformy Docker na podstawie)</span><span class="sxs-lookup"><span data-stu-id="460ea-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="460ea-104">Za pomocą [kontenery Windows](/virtualization/windowscontainers/about/index), można przekonwertować istniejące aplikacje Windows do obrazów platformy Docker i wdrożyć je przy użyciu tych samych narzędzi, jak w pozostałych ekosystemie Docker.</span><span class="sxs-lookup"><span data-stu-id="460ea-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="460ea-105">Aby korzystać z kontenerów Windows, wystarczy do tworzenia poleceń programu Windows PowerShell w pliku DockerFile, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="460ea-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="460ea-106">W tym przypadku używamy programu Windows PowerShell do zainstalowania obrazu podstawowego systemu Windows Server Core, a także usług IIS.</span><span class="sxs-lookup"><span data-stu-id="460ea-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="460ea-107">W podobny sposób, również wystarczą poleceń programu Windows PowerShell do skonfigurowania dodatkowych składników, takich jak tradycyjnych ASP.NET 4.x i .NET 4.6 lub innego oprogramowania Windows, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="460ea-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="460ea-108">[Poprzednie](visual-studio-tools-for-docker.md)
>[dalej](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="460ea-108">[Previous](visual-studio-tools-for-docker.md)
[Next](../docker-devops-workflow/index.md)</span></span>
