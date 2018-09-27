---
title: Tabela decyzji. .NET Framework na potrzeby platformy Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Tabela decyzji, .NET Framework na potrzeby platformy Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 74b3749077fdb375f84ddacd98221aa4afcf2f67
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47401241"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabela decyzji: .NET Framework na potrzeby platformy Docker

W poniższej tabeli decyzji podsumowano, czy ma być używany program .NET Framework lub .NET Core. Należy pamiętać, że dla kontenerów systemu Linux, należy opartych na systemie Linux hostów platformy Docker (maszyn wirtualnych lub serwerach) i dla kontenerów Windows należy systemu Windows Server na podstawie hostów platformy Docker (maszyn wirtualnych lub serwerach).

> [!IMPORTANT]
> Rozwoju maszyny zostaną uruchomione jeden host platformy Docker, Linux lub Windows. Wszystkie powiązane mikrousług, który chcesz uruchomić i przetestować ze sobą w jednym rozwiązaniu będzie musiał ją uruchomić na tę samą platformę kontenerów.

<table>
<thead>
<tr class="header">
<th><strong>Architektura / typ aplikacji</strong></th>
<th><strong>Kontenery systemu Linux</strong></th>
<th><strong>Kontenery Windows</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Mikrousług w kontenerach</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Monolityczną aplikację</td>
<td>.NET Core</td>
<td><p>.NET Framework</p>
<p>.NET Core</p></td>
</tr>
<tr class="odd">
<td>Najlepsze w swojej klasie, wydajności i skalowalności</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Migrowanie starszych aplikacji ("pole brown") systemu Windows Server do kontenerów</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>Nowych wdrożeń opartych na kontenerach ("pole zielony")</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET core (zalecane)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NET 4 (MVC 5, Web API 2 i formularzy sieci Web)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>Usługi SignalR</td>
<td>.NET core 2.1 lub nowszej wersji</td>
<td><p>.NET Framework</p>
<p>.NET core 2.1 lub nowszej wersji</p></td>
</tr>
<tr class="odd">
<td>Usługi WCF, WF i innych platform starszej wersji</td>
<td>Usługi WCF w programie .NET Core (tylko Biblioteka klienta WCF)</td>
<td><p>.NET Framework</p>
<p>Usługi WCF w programie .NET Core (tylko Biblioteka klienta WCF)</p></td>
</tr>
<tr class="even">
<td>Użycie usług platformy Azure</td>
<td><p>.NET Core</p>
<p>(po pewnym czasie wszystkich usług platformy Azure zapewni client SDK dla platformy .NET Core)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(po pewnym czasie wszystkich usług platformy Azure zapewni client SDK dla platformy .NET Core)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
[Poprzednie](net-framework-container-scenarios.md)
[dalej](net-container-os-targets.md)
