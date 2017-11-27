---
title: Tabeli decyzji. Platformy .NET Framework na potrzeby Docker
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Tabela decyzji, platformy .NET Framework na potrzeby Docker"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4889662c4d887bebd320389e3ced6aae1c93133b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabela decyzji: platformy .NET Framework na potrzeby Docker

Poniżej przedstawiono podsumowanie czy użyć kontenery .NET Framework lub .NET Core i systemu Windows lub Linux. Należy pamiętać, że dla systemu Linux kontenerów, potrzebujesz hostów Docker opartych na systemie Linux (maszyn wirtualnych i serwery) i kontenerów systemu Windows należy systemu Windows Server oparte hostów Docker (maszyn wirtualnych lub serwerach).

Istnieje kilka funkcji aplikacji, które mają wpływ na podstawie decyzji. Należy porównać znaczenie te funkcje podczas podejmowania decyzji.

> [!IMPORTANT]
> Programowanie maszyny zostaną uruchomione jeden host Docker, Linux lub Windows. Powiązane mikrousług, który ma zostać uruchamianie i testowanie razem w jednym z rozwiązań, wszystkie należy uruchomić na tę samą platformę kontenera.

* Wybór architektury aplikacji jest **Mikrousług kontenerów**.
    - Wybór implementacji .NET powinien być *.NET Core*.
    - Wybór platformy kontener może być albo *kontenery Linux* lub *kontenery Windows*.
* Wybór architektury aplikacji jest **wbudowanymi aplikacji**.
    - Wybór implementacji .NET mogą być *.NET Core* lub *.NET Framework*.
    - Jeśli wybrano *.NET Core*, wybór platformy kontenera mogą być *kontenery Linux* lub *kontenery Windows*.
    - Jeśli wybrano *.NET Framework*, wybór platformy kontenera musi być *kontenery Windows*.
* Aplikacja jest **nowych aplikacji na podstawie kontenera ("pole zielony")**.
    - Wybór implementacji .NET powinien być *.NET Core*.
    - Wybór platformy kontener może być albo *kontenery Linux* lub *kontenery Windows*.
* Aplikacja jest **Migrowanie starszych aplikacji ("pole brązowy") systemu Windows Server do kontenerów**
    - Wybór implementacji .NET jest *.NET Framework* oparte na framework zależności.
    - Wybór platformy kontenera musi być *kontenery Windows* z powodu zależności .NET Framework.
* Celem projektu aplikacji jest **najlepsze w klasie wydajności i skalowalności**.
    - Wybór implementacji .NET powinien być *.NET Core*.
    - Wybór platformy kontener może być albo *kontenery Linux* lub *kontenery Windows*.
* Zostały utworzone przy użyciu aplikacji **platformy ASP.NET Core**.
    - Wybór implementacji .NET powinien być *.NET Core*.
    - Można użyć *.NET Framework* wykonania, jeśli masz inne zależności struktury.
    - Jeśli wybrano *.NET Core*, wybór platformy kontenera mogą być *kontenery Linux* lub *kontenery Windows*.
    - Jeśli wybrano *.NET Framework*, wybór platformy kontenera musi być *kontenery Windows*.
* Zostały utworzone przy użyciu aplikacji **programu ASP.NET 4 (MVC 5, 2 interfejsu API sieci Web i formularzy sieci Web)**.
    - Wybór implementacji .NET jest *.NET Framework* oparte na framework zależności.
    - Wybór platformy kontenera musi być *kontenery Windows* z powodu zależności .NET Framework.
* Aplikacja używa **usług SignalR**.
    - Wybór implementacji .NET mogą być *.NET Framework*, lub *.NET Core 2.1 (po jej opublikowaniu) lub nowszym*.
    - Wybór platformy kontenera musi być *kontenery Windows* w przypadku wybrania implementacji SignalR dla programu .NET Framework.
    - Wybór platformy kontener może być kontenery systemu Linux lub kontenery systemu Windows w przypadku wybrania implementacji SignalR .NET Core 2.1 lub nowszy (po jej opublikowaniu).  
    - Gdy **usług SignalR** Uruchom na *.NET Core*, można użyć *Linux kontenerów lub kontenery systemu Windows*.
* Aplikacja używa **WCF, WF i innych starszych platform**.
    - Wybór implementacji .NET jest *.NET Framework*, lub *.NET Core (w plan w przyszłości)*.
    - Wybór platformy kontenera musi być *kontenery Windows* z powodu zależności .NET Framework.
* Aplikacja obejmuje **usług zużycie Azure**.
    - Wybór implementacji .NET jest *.NET Framework*, lub *.NET Core (usługi po pewnym czasie wszystkie Azure określi zestawy SDK klientów dla platformy .NET Core)*.
    - Wybór platformy kontenera musi być *kontenery Windows* Jeśli używasz interfejsów API klienta .NET Framework.
    - Jeśli używasz interfejsów API dostępnych dla klienta *.NET Core*, można również wybrać *Linux kontenery i kontenery Windows*.

>[!div class="step-by-step"]
[Poprzednie] (net-framework — kontener scenarios.md) [dalej] (net kontenera os-targets.md)
