---
title: Wprowadzenie do kontenerów i platformy Docker
description: Uzyskaj ogólny przegląd głównych korzyści z używania platformy Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: aa3ead1cb184e23dd091822368e62f580ed73ee5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785628"
---
# <a name="introduction-to-containers-and-docker"></a>Wprowadzenie do kontenerów i platformy Docker

*Konteneryzacji to podejście do tworzenia oprogramowania, w którym aplikacji lub usługi, jego zależności i jego konfiguracji (wyodrębnione pliki manifestu wdrożenia) jednym pakiecie w postaci obrazu kontenera. Możesz następnie testowanie konteneryzowanych aplikacji jako jednostki i wdrożyć go jako wystąpienia obrazu kontenera do hosta systemu operacyjnego (OS).*

Po prostu dopuszcza wysyła kontenery transportu statku, szkolenie lub truck niezależnie od ładunku wewnątrz towarów, kontenery oprogramowania pełnić rolę pojedynczej jednostki standard wdrożenia oprogramowania, który może zawierać inny kod i zależności. Konteneryzowania oprogramowania w ten sposób umożliwia deweloperom i informatykom, ich wdrażania w środowiskach o niewielkich modyfikacji.

Kontenery także izolowania aplikacji od siebie nawzajem na udostępnionym systemu operacyjnego. Konteneryzowane aplikacje uruchamiane w systemie hosta kontenera, który z kolei jest uruchamiany w systemach operacyjnych (Linux lub Windows). Kontenery w związku z tym mają znacznie mniejszy wyświetlacz niż obrazy maszyn wirtualnych (VM).

Każdy kontener można uruchomić aplikacji całej sieci web lub usługi, jak pokazano w rysunku 1-1. W tym przykładzie hosta platformy Docker jest host kontenera i serwera App1, App2, Svc1 i Svc2 są konteneryzowanych aplikacji lub usług.

![Dwie aplikacje i dwie usługi działające w ramach systemu operacyjnego na maszynie Wirtualnej lub serwera fizycznego](./media/image1.png)

**Rysunek 1-1**. Wiele kontenerów, działające na hoście kontenera

Kolejną korzyścią, które może pochodzić z konteneryzacji jest skalowalność. Można skalować w poziomie szybko tworząc nowe kontenery krótkoterminowych zadań. Z punktu widzenia aplikacji wystąpienia obrazu (utworzenie kontenera) jest podobne do tworzenia wystąpienia procesu, takich jak usługi lub aplikacji sieci web. Niezawodność jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta, zazwyczaj chcesz każdego kontenera (obraz wystąpienia), aby uruchomić na innym serwerze hosta lub maszyn wirtualnych w różnych domenach błędów.

Krótko mówiąc kontenery oferują korzyści z izolacji, przenośność, elastyczność, skalowalność i kontroli w całej aplikacji przepływu pracy cyklu życia. Najważniejsze korzyści to środowisko izolacji, udostępniane między deweloperskim i operacjami.

>[!div class="step-by-step"]
>[Next](what-is-docker.md)
