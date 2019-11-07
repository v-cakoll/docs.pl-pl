---
title: Wprowadzenie do kontenerów i platformy Docker
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Wprowadzenie do kontenerów i platformy Docker
ms.date: 08/31/2018
ms.openlocfilehash: 364cbc0ba8149be1873df628a1ca243f420e7d0b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740069"
---
# <a name="introduction-to-containers-and-docker"></a>Wprowadzenie do kontenerów i platformy Docker

Kontenerach to podejście do tworzenia oprogramowania, w którym aplikacja lub usługa, jej zależności i jej konfiguracja (Abstrakcja jako pliki manifestu wdrożenia) są pakowane razem jako obraz kontenera. Aplikacja kontenera może być testowana jako jednostka i wdrożona jako wystąpienie obrazu kontenera w systemie operacyjnym hosta (OS).

Podobnie jak kontenery wysyłkowe umożliwiają transport towarów przez wysyłkę, szkolenie lub ciężarówkę niezależnie od ładunku, kontenery oprogramowania działają jako standardowa jednostka wdrażania oprogramowania, która może zawierać inny kod i zależności. Konteneryzowania oprogramowanie w ten sposób umożliwia deweloperom i specjalistom IT wdrażanie ich w różnych środowiskach z niewielkim modyfikacją lub bez niej.

Kontenery izolują również aplikacje od siebie w udostępnionym systemie operacyjnym. Aplikacje kontenerowe działają na hoście kontenera, który z kolei jest uruchamiany w systemie operacyjnym (Linux lub Windows). Z tego względu kontenery mają znacznie mniejsze rozmiary niż obrazy maszyn wirtualnych.

Każdy kontener może uruchamiać całą aplikację sieci Web lub usługę, jak pokazano na rysunku 2-1. W tym przykładzie Host platformy Docker jest hostem kontenerów, a APP1, APP2, SVC 1 i SVC 2 są kontenerami aplikacjami lub usługami.

![Diagram przedstawiający cztery kontenery działające na maszynie wirtualnej lub serwerze.](./media/index/multiple-containers-single-host.png)

**Rysunek 2-1**. Wiele kontenerów uruchomionych na hoście kontenera

Kolejną zaletą kontenerach jest skalowalność. Możesz szybko skalować w poziomie, tworząc nowe kontenery dla krótkoterminowych zadań. Z punktu widzenia aplikacji Tworzenie wystąpienia obrazu (Tworzenie kontenera) jest podobne do tworzenia wystąpienia procesu, takiego jak usługa lub aplikacja sieci Web. Niemniej jednak w przypadku uruchamiania wielu wystąpień tego samego obrazu na wielu serwerach hosta, zazwyczaj każdy kontener (wystąpienie obrazu) można uruchomić na innym serwerze hosta lub maszynie wirtualnej w różnych domenach błędów.

W krótkim czasie kontenery oferują zalety izolacji, przenośności, elastyczności, skalowalności i kontroli całego przepływu pracy cyklu życia aplikacji. Najważniejsze korzyści to izolacja środowiska udostępniana między tworzeniem i Ops.

>[!div class="step-by-step"]
>[Poprzedni](../index.md)
>[dalej](docker-defined.md)
