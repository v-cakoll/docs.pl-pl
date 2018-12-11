---
title: Wprowadzenie do kontenerów i platformy Docker
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: c2a6b9802bbb995939d33c5c40ef9c1afa1620e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148824"
---
# <a name="introduction-to-containers-and-docker"></a>Wprowadzenie do kontenerów i platformy Docker

Konteneryzacji to podejście do tworzenia oprogramowania, w którym aplikacji lub usługi, jego zależności i jego konfiguracji (wyodrębnione pliki manifestu wdrożenia) jednym pakiecie w postaci obrazu kontenera. Możesz następnie testowanie konteneryzowanych aplikacji jako jednostki i wdrożyć go jako wystąpienia obrazu kontenera do systemu operacyjnego hosta.

Tak samo, jak branży wysyłki używa standardowych kontenerów, aby przenieść towarów przez statku, szkolenie lub truck niezależnie od ładunku wewnątrz nich kontenery oprogramowania pełnić rolę pojedynczej jednostki standard oprogramowania, który może zawierać inny kod i zależności. Wprowadzenie do oprogramowania do kontenerów umożliwia deweloperom i informatykom, wdrażanie tych kontenerów w środowiskach o niewielkich modyfikacji.

Kontenery także izolowania aplikacji od siebie nawzajem na udostępnionym systemu operacyjnego (OS). Uruchamianie konteneryzowanych aplikacji na hoście kontenera, który z kolei jest uruchamiany w systemach operacyjnych (Linux lub Windows). Dlatego kontenery mają znacznie mniejszy wyświetlacz niż obrazy maszyn wirtualnych (VM).

Każdy kontener można uruchomić w całej aplikacji sieci web lub usługi, jak pokazano w rysunku 1-1.

![](./media/image1.png)

Rysunek 1-1: Wiele kontenerów, działające na hoście kontenera

W tym przykładzie hosta platformy Docker jest host kontenera, a aplikacja 1, 2 aplikacji, Svc 1 i Svc 2 są konteneryzowanych aplikacji lub usług.

Kolejną korzyścią, które może pochodzić z konteneryzacji jest skalowalność. Użytkownik może skalowalnego w poziomie szybko tworząc nowe kontenery krótkoterminowych zadań. Z punktu widzenia aplikacji *wystąpienia obrazu* (utworzenie kontenera) jest podobne do tworzenia wystąpienia procesu, takich jak usługi lub aplikacji sieci web. Niezawodność jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta, zazwyczaj chcesz każdego kontenera (obraz wystąpienia), aby uruchomić na innym serwerze hosta lub maszyn wirtualnych w różnych domenach błędów.

Krótko mówiąc kontenery oferują korzyści z izolacji, przenośność, elastyczność, skalowalność i kontroli w całej aplikacji przepływu pracy cyklu życia. Najważniejszą korzyścią jest izolacja świadczona między deweloperskim i operacjami.

>[!div class="step-by-step"]
>[Next](what-is-docker.md)