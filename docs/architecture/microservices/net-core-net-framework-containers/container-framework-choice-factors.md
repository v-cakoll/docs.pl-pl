---
title: Tabela decyzji. .NET Framework do użycia przez platformę Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Tabela decyzji, .NET Frameworks do użycia dla platformy Docker
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296535"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabela decyzji: korzystanie z programu .NET Framework z platformą Docker

Poniższa tabela decyzji zawiera podsumowanie, czy należy używać .NET Framework, czy .NET Core. Należy pamiętać, że w przypadku kontenerów systemu Linux wymagane są hosty platformy Docker oparte na systemie Linux (maszyny wirtualne lub serwery), które są wymagane w przypadku kontenerów platformy Docker opartych na programie Windows Server (maszyn wirtualnych lub serwerach).

> [!IMPORTANT]
> Na maszynach deweloperskich zostanie uruchomiony jeden host platformy Docker (Linux lub Windows). Powiązane mikrousługi, które mają zostać uruchomione i przetestowane razem w jednym rozwiązaniu, będą musiały działać na tej samej platformie kontenerów.

<table>
<thead>
<tr class="header">
<th><strong>Typ architektury/aplikacji</strong></th>
<th><strong>Kontenery systemu Linux</strong></th>
<th><strong>Kontenery systemu Windows</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Mikrousługi na kontenerach</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Aplikacja monolityczna</td>
<td>.NET Core</td>
<td><p>.NET Framework</p>
<p>.NET Core</p></td>
</tr>
<tr class="odd">
<td>Najlepsza w klasie wydajność i skalowalność</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Migracja starszej wersji systemu Windows Server ("brązowy-Field") do kontenerów</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>Nowy projekt oparty na kontenerach ("zielony-pole")</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET Core (zalecane)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NETe 4 (MVC 5, Web API 2 i Web Forms)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>Usługi sygnalizujące</td>
<td>.NET Core 2,1 lub nowsza wersja</td>
<td><p>.NET Framework</p>
<p>.NET Core 2,1 lub nowsza wersja</p></td>
</tr>
<tr class="odd">
<td>WCF, WF i inne starsze platformy</td>
<td>WCF w programie .NET Core (tylko Biblioteka klienta WCF)</td>
<td><p>.NET Framework</p>
<p>WCF w programie .NET Core (tylko Biblioteka klienta WCF)</p></td>
</tr>
<tr class="even">
<td>Użycie usług platformy Azure</td>
<td><p>.NET Core</p>
<p>(ostatecznie wszystkie usługi platformy Azure będą dostarczać zestawy SDK klienta dla platformy .NET Core)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(ostatecznie wszystkie usługi platformy Azure będą dostarczać zestawy SDK klienta dla platformy .NET Core)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
>[Poprzedni](net-framework-container-scenarios.md)Następny
>[](net-container-os-targets.md)
