---
title: "Projektowanie i tworzenie wielu kontenera i Mikrousługi na podstawie aplikacji .NET"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Projektowanie i tworzenie wielu kontenera i Mikrousługi na podstawie aplikacji .NET"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 46d2859fa3b739b1a2a8b1502d4e418fab204648
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Projektowanie i tworzenie aplikacji na podstawie Mikrousługi i usługi kontenera platformy .NET

*Opracowywanie aplikacji konteneryzowanych mikrousługi oznacza, że są tworzenia wielu kontenera aplikacji. Jednak aplikacji kontenera usługi mogą być również prostsze — na przykład trójwarstwowa aplikacja — i nie może zostać utworzony przy użyciu architektury mikrousługi.*

Wcześniej możemy wywoływane pytanie "Jest Docker niezbędne podczas kompilowania architektury mikrousługi?" Odpowiedź brzmi wyczyść nie. Docker jest czynnik i oferuje istotne korzyści, ale kontenery i Docker nie są wymagane twardych dla mikrousług. Na przykład można utworzyć aplikacji sieci mikrousług z lub bez Docker podczas korzystania z sieci szkieletowej usług Azure, obsługujący mikrousług uruchomione jako procesy prostego lub kontenery Docker.

Jednak jeśli wiesz, jak projektowanie i tworzenie aplikacji na podstawie mikrousług, opartą na Docker kontenerów, można do projektowania i opracowywania innych, łatwiejsze modelu aplikacji. Na przykład może projektowania aplikacji trójwarstwowej wymagającego podejście wielu kontenera. Z tego powodu i architektury mikrousługi są ważne trendu w świecie kontenera, w tej sekcji koncentruje się na implementacji architektury mikrousługi, za pomocą kontenerów Docker.


>[!div class="step-by-step"]
[Poprzednie] (.. /containerize-NET-Framework-Applications/index.MD) [dalej] (ruch design.md mikrousługi aplikacji)
