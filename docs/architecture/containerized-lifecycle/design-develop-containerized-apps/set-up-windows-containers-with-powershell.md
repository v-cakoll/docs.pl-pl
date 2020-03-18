---
title: Używanie poleceń programu Windows PowerShell w pliku DockerFile do konfigurowania kontenerów systemu Windows (opartych na standardzie platformy Docker)
description: Dowiedz się, jak używać programu PowerShell podczas pracy z platformą Docker w kontenerach systemu Windows
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295705"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Używanie poleceń programu Windows PowerShell w pliku DockerFile do konfigurowania kontenerów systemu Windows (opartych na standardzie platformy Docker)

Kontenery [systemu Windows](/virtualization/windowscontainers/about/index)można konwertować istniejące aplikacje systemu Windows na obrazy platformy Docker i wdrażać je za pomocą tych samych narzędzi, co pozostałe urządzenia do każdowe.

Aby korzystać z kontenerów systemu Windows, wystarczy napisać polecenia programu Windows PowerShell w pliku DockerFile, jak pokazano w poniższym przykładzie:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

W takim przypadku używamy programu Windows PowerShell do zainstalowania obrazu podstawowego systemu Windows Server Core oraz usług IIS.

W podobny sposób można również użyć poleceń programu Windows PowerShell do skonfigurowania dodatkowych składników, takich jak tradycyjne ASP.NET 4.x i .NET 4.6 lub innego oprogramowania Windows, jak pokazano tutaj:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Poprzedni](visual-studio-tools-for-docker.md)
>[następny](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
