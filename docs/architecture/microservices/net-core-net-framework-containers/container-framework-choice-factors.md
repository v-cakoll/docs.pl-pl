---
title: Tabela decyzji. .NET Framework do użycia przez platformę Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Tabela decyzji, .NET Frameworks do użycia dla platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: 8ffe2b7bc0bee976d3a63b274994dbcc8aef0c61
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628322"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabela decyzji: korzystanie z programu .NET Framework z platformą Docker

Poniższa tabela decyzji zawiera podsumowanie, czy należy używać .NET Framework, czy .NET Core. Należy pamiętać, że w przypadku kontenerów systemu Linux wymagane są hosty platformy Docker oparte na systemie Linux (maszyny wirtualne lub serwery), które są wymagane w przypadku kontenerów platformy Docker opartych na programie Windows Server (maszyn wirtualnych lub serwerach).

> [!IMPORTANT]
> Na maszynach deweloperskich zostanie uruchomiony jeden host platformy Docker (Linux lub Windows). Powiązane mikrousługi, które mają zostać uruchomione i przetestowane razem w jednym rozwiązaniu, będą musiały działać na tej samej platformie kontenerów.

| Typ architektury/aplikacji | Kontenery systemu Linux | Kontenery systemu Windows |
|-------------------------|------------------|--------------------|
| Mikrousługi na kontenerach | .NET Core | .NET Core |
| Aplikacja monolityczna | .NET Core | .NET Framework <br/> .NET Core |
| Najlepsza w klasie wydajność i skalowalność | .NET Core | .NET Core |
| Migracja starszej wersji systemu Windows Server ("brązowy-Field") do kontenerów | -- | .NET Framework |
| Nowy projekt oparty na kontenerach ("zielony-pole") | .NET Core | .NET Core |
| ASP.NET Core | .NET Core | .NET Core (zalecane) <br/> .NET Framework |
| ASP.NETe 4 (MVC 5, Web API 2 i Web Forms) | -- | .NET Framework |
| Usługi sygnalizujące | .NET Core 2,1 lub nowsza wersja | .NET Framework <br/> .NET Core 2,1 lub nowsza wersja |
| WCF, WF i inne starsze platformy | WCF w programie .NET Core (tylko Biblioteka kliencka) | .NET Framework <br/> WCF w programie .NET Core (tylko Biblioteka kliencka) |
| Użycie usług platformy Azure | .NET Core <br/> (ostatecznie większość usług platformy Azure udostępnia zestawy SDK klienta dla platformy .NET Core) | .NET Framework <br/> .NET Core <br/> (ostatecznie większość usług platformy Azure udostępnia zestawy SDK klienta dla platformy .NET Core) |

>[!div class="step-by-step"]
>[Poprzednie](net-framework-container-scenarios.md)
>[dalej](net-container-os-targets.md)
