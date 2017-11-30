---
title: "Wprowadzenie do kontenerów i Docker"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 4e79c4658492516e33efc0b33408e3d4220640f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-containers-and-docker"></a>Wprowadzenie do kontenerów i Docker

Przechowywanie w kontenerach jest podejście do rozwoju oprogramowania, w której aplikacja lub usługi, jego zależności i jego konfiguracji (pobieranej jako pliki manifestu wdrożenia) jednym pakiecie jako obraz kontenera. Następnie można przetestować aplikację konteneryzowanych jako jednostki i wdrożyć go jako kontener wystąpienie obrazu systemu operacyjnego hosta.

Tak samo jak w branży wysyłki używa standardowych kontenerów, aby przenieść towarów dostawy, pociągu lub ciężarówka, niezależnie od ładunku w tych kontenerach oprogramowania działają jako standardowa jednostka oprogramowania, które mogą zawierać różne kodu i zależności. Wprowadzenie do oprogramowania w kontenerach umożliwia dla deweloperów i specjalistów IT do wdrożenia tych kontenerach w środowiskach z żadnych modyfikacji.

Kontenery również izolowania aplikacji od siebie na udostępnionych systemu operacyjnego (systemu operacyjnego). Konteneryzowanych aplikacje działają hosta kontenera, który z kolei jest uruchamiany na system operacyjny (Linux lub Windows). W związku z tym kontenery zostały znacznie mniej miejsca niż obrazy maszyny wirtualnej (VM).

Każdego kontenera można uruchomić w całej aplikacji sieci web lub usługi, jak pokazano w rysunku 1-1.

![](./media/image1.png)

Rysunek 1-1: wiele kontenerów uruchomiona na hoście kontenera

W tym przykładzie Docker Host jest hostem kontenera, i aplikacji 1, 2 aplikacji Svc 1 i Svc 2 konteneryzowanych aplikacji lub usług.

Kolejna korzyść związana, który może pochodzić od przechowywanie w kontenerach jest skalowalność. Użytkownik może skalowalnego w poziomie szybko tworząc nowe kontenery krótkoterminowych zadań. Z punktu widzenia aplikacji *tworzenia wystąpienia obrazu* (utworzenie kontenera) jest podobny do tworzenia wystąpienia procesów, takich jak usługi lub aplikacji sieci web. Niezawodność jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta, zwykle ma każdego kontenera (wystąpienia obrazu) do uruchomienia na serwerze innego hosta lub maszyny Wirtualnej w domenach awarii innego.

Krótko mówiąc kontenery oferuje zalet izolacji, przenośność elastyczności, skalowalności i kontroli dla przepływu pracy cyklu życia całej aplikacji. Najważniejszą korzyścią jest izolacji udostępniane między deweloperów i Ops.


>[!div class="step-by-step"]
[Next] (co to docker.md)
