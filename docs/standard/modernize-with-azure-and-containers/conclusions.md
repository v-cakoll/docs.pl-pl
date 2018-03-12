---
title: Wnioski
description: "Modernizacji istniejących aplikacji .NET z chmury Azure i kontenery systemu Windows | wnioski"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9ab627793ac45510aba6ce76fdb87834b02e55f8
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
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