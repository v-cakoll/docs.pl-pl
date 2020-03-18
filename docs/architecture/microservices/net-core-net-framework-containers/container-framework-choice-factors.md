---
title: Tabela decyzji. Platformy .NET do użycia dla platformy Docker
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Tabela decyzji, platformy .NET do użycia dla platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: 8ffe2b7bc0bee976d3a63b274994dbcc8aef0c61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628322"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabela decyzji: korzystanie z programu .NET Framework z platformą Docker

W poniższej tabeli decyzji podsumowano, czy używać programu .NET Framework lub .NET Core. Należy pamiętać, że w przypadku kontenerów systemu Linux potrzebne są hosty platformy Docker oparte na systemie Linux (maszyny wirtualne lub serwery) i że w przypadku kontenerów systemu Windows potrzebujesz hostów platformy Docker opartych na systemie Windows Server (maszyn wirtualnych lub serwerów).

> [!IMPORTANT]
> Maszyny deweloperów będą uruchamiać jeden host platformy Docker, linux lub windows. Powiązane mikrousługi, które chcesz uruchomić i przetestować razem w jednym rozwiązaniu, wszystkie będą musiały działać na tej samej platformie kontenera.

| Architektura / typ aplikacji | Kontenery systemu Linux | Kontenery systemu Windows |
|-------------------------|------------------|--------------------|
| Mikrousługi w kontenerach | .NET Core | .NET Core |
| Aplikacja monolityczna | .NET Core | .NET Framework <br/> .NET Core |
| Najlepsza w swojej klasie wydajność i skalowalność | .NET Core | .NET Core |
| Starsza aplikacja systemu Windows Server ("pole brązowe") migracja do kontenerów | -- | .NET Framework |
| Nowy rozwój oparty na kontenerach ("zielone pole") | .NET Core | .NET Core |
| ASP.NET Core | .NET Core | .NET Core (zalecane) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, Web API 2 i formularze sieci Web) | -- | .NET Framework |
| Usługi SignalR | .NET Core 2.1 lub nowsza wersja | .NET Framework <br/> .NET Core 2.1 lub nowsza wersja |
| WCF, WF i inne starsze struktury | WCF w .NET Core (tylko biblioteka klienta) | .NET Framework <br/> WCF w .NET Core (tylko biblioteka klienta) |
| Zużycie usług platformy Azure | .NET Core <br/> (Po pewnym czasie większość usług platformy Azure zapewni zestawy SDK klienta dla .NET Core) | .NET Framework <br/> .NET Core <br/> (Po pewnym czasie większość usług platformy Azure zapewni zestawy SDK klienta dla .NET Core) |

>[!div class="step-by-step"]
>[Poprzedni](net-framework-container-scenarios.md)
>[następny](net-container-os-targets.md)
