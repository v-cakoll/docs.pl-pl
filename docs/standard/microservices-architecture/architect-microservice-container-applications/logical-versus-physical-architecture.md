---
title: Architektura logiczna i fizycznej architektury
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Architektura logiczna i fizycznej architektury"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b08a5b8fb8f9df8a9a0a821fa85f1f6a94fce2d3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a>Architektura logiczna i fizycznej architektury

Jest przydatne w tym momencie do zatrzymywania i omówienia różnicy między Architektura logiczna i architektura fizycznych, jak dotyczy to projekt aplikacji opartych na mikrousługi.

Aby rozpocząć, tworzenie mikrousług nie korzystają z żadnych określonych technologii. Na przykład kontenery Docker nie są wymagane, aby można było utworzyć architektura mikrousługi. Mikrousług tych można również uruchomić jako zwykły procesów. Mikrousług to architektura logiczna.

Ponadto, nawet wtedy, gdy mikrousługi fizycznie implementacji jako pojedynczą usługę, proces lub kontenera (sake na prostotę jest podejście przyjęte w pierwotnej wersji [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), to parzystość platformy mikrousługi biznesowe i usługa fizycznego lub kontenera nie jest zawsze wymagane we wszystkich przypadkach podczas kompilowania dużych i złożonych aplikacji, składa się z wielu dziesiątek, a nawet setki usług.

Jest to, gdy ma różnicy między architektury logicznej i fizycznej architektury aplikacji. Architektura logiczna i logiczne granice systemu nie zawsze mapują jeden do jednego z architekturą fizycznej lub wdrożenia. Może się zdarzyć, ale często nie.

Mimo że może zidentyfikowano niektórych mikrousług biznesowych lub ograniczonych kontekstów, oznacza to, że najlepszym sposobem wykonania jest zawsze przez utworzenie jednego usługi (np. interfejsu API sieci Web programu ASP.NET) lub jeden kontener Docker dla każdego mikrousługi biznesowych. Posiadanie reguły każdego mikrousługi firm informujący o tym, realizowane przy użyciu jednej usługi lub kontener rezygnujesz.

W związku z tym mikrousługi biznesowych lub ograniczonych kontekstu jest architektura logiczna, która może mieć odpowiedniki (lub nie) z architekturą fizycznych. Istotne jest czy mikrousługi biznesowych lub ograniczonych kontekstu musi być autonomiczne, zezwalając kod stanu niezależnie określonej wersji, wdrożyć i skalowania.

Jak pokazano na rysunku 4-8, mikrousługi firm katalogu może składać się z kilku usług lub procesów. Mogą to być wiele usług interfejsu API sieci Web ASP.NET lub dowolny inny rodzaj usług przy użyciu protokołu HTTP lub innych protokołów. Co ważniejsze usługi można udostępnić te same dane, tak długo, jak te usługi są spójne względem tej samej domenie biznesowych.

![](./media/image8.png)

**Rysunek 4-8**. Mikrousługi biznesowe z kilku usług fizycznych

Usług w przykładzie udostępnianie tego samego modelu danych, ponieważ te same dane co usługa wyszukiwania jest przeznaczony dla usługi interfejsu API sieci Web. Dlatego w fizycznych implementacji mikrousługi biznesowych, jest dzielona tej funkcji, można skalować każdej z tych usług wewnętrznego w górę lub w dół zgodnie z potrzebami. Może być usługi interfejsu API sieci Web zwykle wymaga więcej wystąpień usługi wyszukiwania, lub na odwrót.)

Krótko mówiąc architektura logiczna mikrousług nie zawsze musi pokrywa się z architekturą fizycznego wdrożenia. W tym przewodniku zawsze, gdy firma Microsoft wspomina mikrousługi, możemy oznacza firmy lub mikrousługi logiczne, które można mapować do co najmniej jednej usługi. W większości przypadków będzie to jednej usługi, ale może być więcej.


>[!div class="step-by-step"]
[Poprzednie] (dane suwerenności na microservice.md) [dalej] (distributed-data-management.md)
