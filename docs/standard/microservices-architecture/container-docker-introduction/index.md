---
title: Wprowadzenie do kontenerów i Docker
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Wprowadzenie do kontenerów i Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c1f78a8904270123188367a01bddbcac3f7f1b7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-containers-and-docker"></a>Wprowadzenie do kontenerów i Docker

Przechowywanie w kontenerach jest podejście do rozwoju oprogramowania, w której aplikacja lub usługi, jego zależności i jego konfiguracji (pobieranej jako pliki manifestu wdrożenia) jednym pakiecie jako obraz kontenera. Konteneryzowanych aplikacji można przetestować jako jednostki i wdrażać jako kontener wystąpienie obrazu systemu operacyjnego hosta (systemu operacyjnego).

Tak samo, jak kontenery wysyłki umożliwiają transportu dostawy, pociągu lub ciężarówka niezależnie od ładunku wewnątrz towarów, kontenery oprogramowania działają jako standardowa jednostka oprogramowania, które mogą zawierać różne kodu i zależności. Containerizing oprogramowania w ten sposób umożliwia deweloperom i informatykom je wdrożyć w środowiskach z żadnych modyfikacji.

Kontenery również izolowania aplikacji od siebie na udostępnionych systemu operacyjnego. Konteneryzowanych aplikacje są uruchamiane na górze kontenera hosta, który z kolei jest uruchamiany na system operacyjny (Linux lub Windows). Kontenery więc znacznie mniej miejsca niż obrazy maszyny wirtualnej (VM).

Każdego kontenera można uruchomić aplikacji sieci web całego lub usługi, jak pokazano w rysunku 2-1. W tym przykładzie Docker host jest hostem kontenera, i App1, App2 Svc 1 i Svc 2 konteneryzowanych aplikacji lub usług.

![](./media/image1.png)

**Rysunek 2-1**. Wiele kontenerów uruchomiona na hoście kontenera

Inną zaletą przechowywanie w kontenerach jest skalowalność. Możesz skalować w poziomie szybko tworząc nowe kontenery krótkoterminowych zadań. Z punktu widzenia aplikacji tworzenie wystąpień obrazu (utworzenie kontenera) jest podobny do tworzenia wystąpienia procesów, takich jak usługi lub aplikacji sieci web. Niezawodność jednak po uruchomieniu wielu wystąpień tego samego obrazu na wielu serwerach hosta, zwykle ma każdego kontenera (wystąpienia obrazu) do uruchomienia na serwerze innego hosta lub maszyny Wirtualnej w domenach awarii innego.

Krótko mówiąc kontenery oferuje zalet izolacji, przenośność elastyczności, skalowalności i kontroli dla przepływu pracy z cyklem życia całej aplikacji. Najważniejszą korzyścią jest izolacji udostępniane między deweloperów i Ops.


>[!div class="step-by-step"]
[Poprzednie] (.. / index.md) [dalej] (docker defined.md)
