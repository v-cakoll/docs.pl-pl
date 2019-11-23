---
title: Używanie poleceń programu Windows PowerShell w pliku dockerfile do konfigurowania kontenerów systemu Windows (opartych na platformie Docker standard)
description: Dowiedz się, jak używać programu PowerShell podczas pracy z platformą Docker w kontenerach systemu Windows
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295705"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="c8658-103">Używanie poleceń programu Windows PowerShell w pliku dockerfile do konfigurowania kontenerów systemu Windows (opartych na platformie Docker standard)</span><span class="sxs-lookup"><span data-stu-id="c8658-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="c8658-104">[Kontenery systemu Windows](/virtualization/windowscontainers/about/index)umożliwiają konwertowanie istniejących aplikacji systemu Windows na obrazy platformy Docker i wdrażanie ich przy użyciu tych samych narzędzi, co w przypadku reszty ekosystemu platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="c8658-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="c8658-105">Aby korzystać z kontenerów systemu Windows, wystarczy napisać polecenia programu Windows PowerShell w pliku dockerfile, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c8658-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="c8658-106">W takim przypadku korzystamy z programu Windows PowerShell, aby zainstalować podstawowy obraz systemu Windows Server Core oraz usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="c8658-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="c8658-107">W podobny sposób można również użyć poleceń programu Windows PowerShell, aby skonfigurować dodatkowe składniki, takie jak tradycyjne ASP.NET 4. x i .NET 4,6 lub inne oprogramowanie systemu Windows, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="c8658-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="c8658-108">[Poprzedni](visual-studio-tools-for-docker.md)
>[Następny](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="c8658-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
