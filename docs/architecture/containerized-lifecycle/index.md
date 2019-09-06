---
title: Wprowadzenie do kontenerów i platformy Docker
description: Zapoznaj się z ogólnymi omówieniem głównych korzyści płynących z używania platformy Docker.
ms.date: 02/15/2019
ms.openlocfilehash: a03c67ed4fbc55c84e69fba5b7978863c8305e00
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295673"
---
# <a name="introduction-to-containers-and-docker"></a>Wprowadzenie do kontenerów i platformy Docker

*Kontenerach to podejście do tworzenia oprogramowania, w którym aplikacja lub usługa, jej zależności i jej konfiguracja (Abstrakcja jako pliki manifestu wdrożenia) są pakowane razem jako obraz kontenera. Następnie można przetestować aplikację kontenerową jako jednostkę i wdrożyć ją jako wystąpienie obrazu kontenera w systemie operacyjnym hosta (OS).*

Podobnie jak kontenery wysyłkowe umożliwiają transport towarów przez wysyłkę, szkolenie lub ciężarówkę niezależnie od ładunku, kontenery oprogramowania działają jako standardowa jednostka wdrażania oprogramowania, która może zawierać inny kod i zależności. Konteneryzowania oprogramowanie w ten sposób umożliwia deweloperom i specjalistom IT wdrażanie ich w różnych środowiskach z niewielkim modyfikacją lub bez niej.

Kontenery izolują również aplikacje od siebie w udostępnionym systemie operacyjnym. Aplikacje kontenerowe działają na hoście kontenera, który z kolei jest uruchamiany w systemie operacyjnym (Linux lub Windows). W związku z tym kontenery mają znacznie mniejsze rozmiary niż obrazy maszyn wirtualnych.

Każdy kontener może uruchamiać całą aplikację sieci Web lub usługę, jak pokazano na rysunku 1-1. W tym przykładzie Host platformy Docker jest hostem kontenera, a APP1, APP2, Svc1 i Svc2 są kontenerami aplikacjami lub usługami.

![Dwie aplikacje i dwie usługi działające w systemie operacyjnym w maszynie wirtualnej lub serwerze fizycznym](./media/image1.png)

**Rysunek 1-1**. Wiele kontenerów uruchomionych na hoście kontenera

Inną korzyścią, jaką można uzyskać od kontenerach, jest skalowalność. Możesz szybko skalować w poziomie, tworząc nowe kontenery dla krótkoterminowych zadań. Z punktu widzenia aplikacji Tworzenie wystąpienia obrazu (Tworzenie kontenera) jest podobne do tworzenia wystąpienia procesu, takiego jak usługa lub aplikacja sieci Web. Niemniej jednak w przypadku uruchamiania wielu wystąpień tego samego obrazu na wielu serwerach hosta, zazwyczaj każdy kontener (wystąpienie obrazu) można uruchomić na innym serwerze hosta lub maszynie wirtualnej w różnych domenach błędów.

W krótkim czasie kontenery oferują zalety izolacji, przenośności, elastyczności, skalowalności i kontroli całego przepływu pracy cyklu życia aplikacji. Najważniejsze korzyści to izolacja środowiska zapewniana między tworzeniem i Ops.

>[!div class="step-by-step"]
>[Next](what-is-docker.md)
