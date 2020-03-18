---
title: Wprowadzenie do kontenerów i platformy Docker
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Wprowadzenie do kontenerów i platformy Docker
ms.date: 08/31/2018
ms.openlocfilehash: 364cbc0ba8149be1873df628a1ca243f420e7d0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740069"
---
# <a name="introduction-to-containers-and-docker"></a>Wprowadzenie do kontenerów i platformy Docker

Konteneryzacja jest podejście do tworzenia oprogramowania, w którym aplikacji lub usługi, jego zależności i jego konfiguracji (abstrakcjonowane jako pliki manifestu wdrożenia) są pakowane razem jako obraz kontenera. Konteneryzowana aplikacja może być testowana jako jednostka i wdrażana jako wystąpienie obrazu kontenera w systemie operacyjnym hosta (OS).

Podobnie jak kontenery wysyłkowe umożliwiają transport towarów statkiem, pociągiem lub ciężarówką niezależnie od ładunku w środku, kontenery oprogramowania działają jako standardowa jednostka wdrażania oprogramowania, która może zawierać inny kod i zależności. Konteneryzowanie oprogramowania w ten sposób umożliwia programistom i specjalistom IT wdrażanie ich w różnych środowiskach z niewielkimi lub żadnymi modyfikacjami.

Kontenery również izolować aplikacje od siebie na wspólnym os. Konteneryzowane aplikacje działają na serwerze kontenera, który z kolei działa w systemie operacyjnym (Linux lub Windows). Kontenery mają zatem znacznie mniejszą powierzchnię niż obrazy maszyny wirtualnej (VM).

Każdy kontener można uruchomić całą aplikację sieci web lub usługi, jak pokazano na rysunku 2-1. W tym przykładzie host platformy Docker jest hostem kontenerów, a App1, App2, Svc 1 i Svc 2 są konteneryzowanymi aplikacjami lub usługami.

![Diagram przedstawiający cztery kontenery działające na maszynie wirtualnej lub serwerze.](./media/index/multiple-containers-single-host.png)

**Rysunek 2-1**. Wiele kontenerów działających na hoście kontenera

Inną zaletą konteneryzacji jest skalowalność. Można szybko skalować w sposób skalowany w sposób skalowany w sposób skalowany w sposób skalowany w sposób skalowany w sposób skalowany w sposób określony, tworząc nowe kontenery do zadań krótkoterminowych. Z punktu widzenia aplikacji tworzenie wystąpienia obrazu (tworzenie kontenera) jest podobne do tworzenia procesu, takiego jak usługa lub aplikacja sieci Web. Jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta zazwyczaj każdy kontener (wystąpienie obrazu) ma być uruchamiany na innym serwerze hosta lub maszynie wirtualnej w różnych domenach błędów.

Krótko mówiąc, kontenery oferują korzyści z izolacji, przenośności, elastyczności, skalowalności i kontroli w całym przepływie pracy cyklu życia aplikacji. Najważniejszą korzyścią jest izolacja środowiska między dev i ops.

>[!div class="step-by-step"]
>[Poprzedni](../index.md)
>[następny](docker-defined.md)
