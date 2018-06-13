---
title: Wybieranie platformy obliczeń platformy Azure dla aplikacji kontenera
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Wybieranie platformy obliczeń platformy Azure dla aplikacji kontenera
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958243"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Wybieranie platformy obliczeń platformy Azure dla aplikacji kontenera

Jak można zauważyć po odczytaniu w poprzednich sekcjach, platforma Azure jest Otwórz chmury, które oferuje wiele wyborów. Można użyć najlepiej spełnia Twoje potrzeby, jednak również powierzchni pytania o jakie/technologii produktów należy używać konteneryzowanych aplikacji.

Jako *domyślnie* zalecenia, poniżej przedstawiono główne kryteria zalecane w tych wskazówkach:

  - **Jednej aplikacji wbudowanymi:** wybierz usługi aplikacji Azure
  - **N-warstwowa aplikacja:** wybierz orchestrators, takie jak usługi Kubernetes Azure (AKS), usługa sieci szkieletowej (CPP) lub usługi aplikacji, jeśli masz jedną lub kilka usług zaplecza
  - **Linux mikrousług:** wybierz AKS/Kubernetes
  - **Mikrousług systemu Windows:** wybierz sieci szkieletowej usług
  - **Funkcje niekorzystającą & procedury obsługi zdarzeń:** wybierz usługi Azure Functions
  - **Na dużą skalę partii:** wybierz partii zadań Azure

Jednak tego zalecenia należy zwrócić na powiększanie soli, jak wybór produktu będzie zależeć od potrzeb i właściwości określonej aplikacji. Nie wszystkie aplikacje są takie same, nawet wtedy, gdy początkowo może wyglądać podobnych typów.

Po dokładniejszej analizy potrzeb aplikacji zaznaczono produkt może być różne. Jednak jako punkt początkowy, warto mieć początkowej wskazówek, z którym rozpoczęcia ewaluacji i testowania na podstawie określonych priorytetu.

Następny rysunek można analizować bardziej globalnego podczas tabeli szczegółowe decyzji.

![](./media/image8.5.png)

Powiadomienie jak podstawowego systemu operacyjnego (w porównaniu z systemem Windows. Linux) można także współczynnik decyzji, niektóre orchestrators są bardziej dojrzałe Linux kontenerów i innych kontenerów systemu Windows. Na przykład kontenery Linux są bardzo dojrzałe w Kubernetes (AKS na platformie Azure) ale mniej dojrzałe w sieci szkieletowej usług. Z drugiej strony kontenery systemu Windows są bardziej dojrzałe w sieci szkieletowej usług (wydane w 2017 maja) i mniej dojrzałe w AKS.

Jednak różnic w dojrzałości system operacyjny będzie w przyszłości zanikania i wielu platform będą mieli porównywalne dojrzałości systemu operacyjnego i decyzja będzie leżą więcej informacji na temat Preferencje na podstawie konkretnych cech aplikacji może być konieczne lub oparte na każdej z platform ekosystemu przyczyny.


>[!div class="step-by-step"]
[Poprzednie](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[dalej](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
