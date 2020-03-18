---
title: Projektowanie aplikacji kontenerowych i opartych na mikrousługach
description: Projektowanie aplikacji kontenerowych i opartych na mikrousługach jest nie małym wyczynem i nie należy lekceważyć. Poznaj podstawowe pojęcia w tym rozdziale.
ms.date: 09/20/2018
ms.openlocfilehash: aff30c907f1140b94dbcae330ed7cb633b0a744b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70295519"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Projektowanie aplikacji kontenerowych i opartych na mikrousługach

*Mikrousługi oferują ogromne korzyści, ale także podnieść ogromne nowe wyzwania. Wzorce architektury mikrousług są podstawowymi filarami podczas tworzenia aplikacji opartej na mikrousługach.*

Wcześniej w tym przewodniku, można dowiedzieć się podstawowe pojęcia dotyczące kontenerów i platformy Docker. To były minimalne informacje potrzebne do rozpoczęcia pracy z kontenerami. Mimo że nawet wtedy, gdy kontenery są enablers i doskonałe dopasowanie do mikrousług, nie są one obowiązkowe dla architektury mikrousług i wiele koncepcji architektonicznych w tej sekcji architektury można zastosować bez kontenerów, zbyt. Wytyczne te koncentrują się jednak na przecięciu obu ze względu na już wprowadzone znaczenie kontenerów.

Aplikacje dla przedsiębiorstw mogą być złożone i często składają się z wielu usług zamiast jednej aplikacji opartej na usługach. W takich przypadkach należy zrozumieć dodatkowe podejścia architektoniczne, takie jak mikrousług i niektórych wzorców projektowania opartego na domenie (DDD) oraz koncepcji aranżacji kontenera. Należy zauważyć, że w tym rozdziale opisano nie tylko mikrousług w kontenerach, ale wszelkie konteneryzowane aplikacji, jak również.

## <a name="container-design-principles"></a>Zasady projektowania kontenerów

W modelu kontenera wystąpienie obrazu kontenera reprezentuje pojedynczy proces. Definiując obraz kontenera jako granicę procesu, można utworzyć elementy pierwotne, które mogą służyć do skalowania procesu lub do partii.

Podczas projektowania obrazu kontenera w pliku Dockerfile zostanie wyświetlona definicja [ENTRYPOINT.](https://docs.docker.com/engine/reference/builder/#entrypoint) Definiuje proces, którego okres istnienia kontroluje okres istnienia kontenera. Po zakończeniu procesu kończy się cykl życia kontenera. Kontenery mogą reprezentować długotrwałe procesy, takie jak serwery sieci web, ale mogą również reprezentować procesy krótkotrwałe, takie jak zadania wsadowe, które wcześniej mogły zostać zaimplementowane jako usługi Azure [WebJobs.](https://github.com/Azure/azure-webjobs-sdk/wiki)

Jeśli proces nie powiedzie się, kontener kończy się, a koordynator przejmuje. Jeśli koordynator został skonfigurowany do przechowywania pięciu wystąpień uruchomionych i jeden kończy się niepowodzeniem, koordynator utworzy inne wystąpienie kontenera, aby zastąpić proces nie powiodło się. W zadaniu wsadowym proces jest uruchamiany z parametrami. Po zakończeniu procesu praca zostanie zakończona. Niniejsze wskazówki są drążenia w dół na koordynatorów, później.

Może się okazać scenariusz, w którym chcesz wiele procesów uruchomionych w jednym kontenerze. W tym scenariuszu, ponieważ może istnieć tylko jeden punkt wejścia na kontener, można uruchomić skrypt w kontenerze, który uruchamia tyle programów, zgodnie z potrzebami. Na przykład można użyć [supervisor](http://supervisord.org/) lub podobne narzędzie do dbania o uruchomienie wielu procesów wewnątrz jednego kontenera. Jednak mimo że można znaleźć architektury, które posiadają wiele procesów na kontener, takie podejście nie jest bardzo często.

>[!div class="step-by-step"]
>[Poprzedni](../net-core-net-framework-containers/official-net-docker-images.md)
>[następny](containerize-monolithic-applications.md)
