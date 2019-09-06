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
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Używanie poleceń programu Windows PowerShell w pliku dockerfile do konfigurowania kontenerów systemu Windows (opartych na platformie Docker standard)

[Kontenery systemu Windows](/virtualization/windowscontainers/about/index)umożliwiają konwertowanie istniejących aplikacji systemu Windows na obrazy platformy Docker i wdrażanie ich przy użyciu tych samych narzędzi, co w przypadku reszty ekosystemu platformy Docker.

Aby korzystać z kontenerów systemu Windows, wystarczy napisać polecenia programu Windows PowerShell w pliku dockerfile, jak pokazano w następującym przykładzie:

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

W takim przypadku korzystamy z programu Windows PowerShell, aby zainstalować podstawowy obraz systemu Windows Server Core oraz usługi IIS.

W podobny sposób można również użyć poleceń programu Windows PowerShell, aby skonfigurować dodatkowe składniki, takie jak tradycyjne ASP.NET 4. x i .NET 4,6 lub inne oprogramowanie systemu Windows, jak pokazano poniżej:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Poprzedni](visual-studio-tools-for-docker.md)Następny
>[](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
