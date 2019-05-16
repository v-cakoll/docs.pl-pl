---
title: Wprowadzenie do kontenerów i platformy Docker
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Wprowadzenie do kontenerów i platformy Docker
ms.date: 08/31/2018
ms.openlocfilehash: cb6244939f6ae89ba1dc824b55a21d1e010cef5e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644517"
---
# <a name="introduction-to-containers-and-docker"></a>Wprowadzenie do kontenerów i platformy Docker

Konteneryzacji to podejście do tworzenia oprogramowania, w którym aplikacji lub usługi, jego zależności i jego konfiguracji (wyodrębnione pliki manifestu wdrożenia) jednym pakiecie w postaci obrazu kontenera. Konteneryzowanej aplikacji można przetestować jako jednostka i wdrażane jako wystąpienia obrazu kontenera do hosta systemu operacyjnego (OS).

Po prostu dopuszcza wysyła kontenery transportu statku, szkolenie lub truck niezależnie od ładunku wewnątrz towarów, kontenery oprogramowania pełnić rolę pojedynczej jednostki standard wdrożenia oprogramowania, który może zawierać inny kod i zależności. Konteneryzowania oprogramowania w ten sposób umożliwia deweloperom i informatykom, ich wdrażania w środowiskach o niewielkich modyfikacji.

Kontenery także izolowania aplikacji od siebie nawzajem na udostępnionym systemu operacyjnego. Konteneryzowane aplikacje uruchamiane w systemie hosta kontenera, który z kolei jest uruchamiany w systemach operacyjnych (Linux lub Windows). Kontenery w związku z tym mają znacznie mniejszy wyświetlacz niż obrazy maszyn wirtualnych (VM).

Każdy kontener można uruchomić aplikacji całej sieci web lub usługi, jak pokazano w rysunek 2-1. W tym przykładzie hosta platformy Docker jest host kontenera i serwera App1, App2, Svc 1 i Svc 2 są konteneryzowanych aplikacji lub usług.

![Dwie aplikacje i dwie usługi działające w ramach systemu operacyjnego na maszynie Wirtualnej lub serwera fizycznego](./media/image1.png)

**Rysunek 2-1**. Wiele kontenerów, działające na hoście kontenera

Kolejną korzyścią wynikającą z konteneryzacji jest skalowalność. Można skalować w poziomie szybko tworząc nowe kontenery krótkoterminowych zadań. Z punktu widzenia aplikacji wystąpienia obrazu (utworzenie kontenera) jest podobne do tworzenia wystąpienia procesu, takich jak usługi lub aplikacji sieci web. Niezawodność jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta, zazwyczaj chcesz każdego kontenera (obraz wystąpienia), aby uruchomić na innym serwerze hosta lub maszyn wirtualnych w różnych domenach błędów.

Krótko mówiąc kontenery oferują korzyści z izolacji, przenośność, elastyczność, skalowalność i kontroli w całej aplikacji przepływu pracy cyklu życia. Najważniejsze korzyści to środowisko izolacji udostępniane między deweloperskim i operacjami.

>[!div class="step-by-step"]
>[Poprzednie](../index.md)
>[dalej](docker-defined.md)
