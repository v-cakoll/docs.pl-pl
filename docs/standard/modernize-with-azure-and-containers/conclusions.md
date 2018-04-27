---
title: Wnioski
description: Modernizacji istniejących aplikacji .NET z chmury Azure i kontenery systemu Windows | wnioski
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5048e6abee83267c42389381e1e7f83b43ab94ac
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="conclusions"></a>Wnioski

- Rozwiązania oparte na kontenera ostatecznie zapewniają korzyści oszczędności kosztów. Kontenery są rozwiązanie problemów z wdrażaniem, ponieważ będą oni mogli usunąć tarcie spowodowane przez Brak zależności w środowiskach produkcyjnych. Przez usunięcie tych problemów, jego znacznie poprawia operacji tworzenia/testowania, DevOps i produkcji.

- Kontener Docker staje się coraz standardowe jednostki wdrożenia żadnych usług ani aplikacji serwerowych.

- W środowiskach produkcyjnych należy użyć orchestrator (na przykład sieci szkieletowej usług lub Kubernetes) umożliwia obsługę aplikacji dla komputerów z systemem Windows kontenery skalowalnych.

- Maszyny wirtualne platformy Azure obsługującym kontenery to szybki i łatwy sposób utworzyć małych środowiska i testowania w chmurze.

- Azure wystąpienia bazy danych SQL zarządzane zaleca się domyślnie podczas migrowania relacyjnych baz danych z istniejących aplikacji na platformie Azure.

- Visual Studio 2017 i Image2Docker są podstawowe narzędzia uruchamiania modernizacji istniejących aplikacji .NET z kontenerami systemu Windows przez przyspieszania pobierania uruchomiono naukę.

- Podczas umieszczania konteneryzowanych aplikacji w środowisku produkcyjnym zawsze będzie utworzyć lub przyjmuje kultury DevOps i narzędzia do opracowywania oprogramowania dla potoków CI/CD, takich jak Visual Studio Team Services lub Wpięć.

- Microsoft Azure udostępnia środowisko najbardziej co zwiększy do modernizacji istniejących aplikacji .NET Framework z kontenery systemu Windows, infrastruktury w chmurze i usługami typu PaaS.

>[!div class="step-by-step"]
[Poprzednie](walkthroughs-technical-get-started-overview.md)