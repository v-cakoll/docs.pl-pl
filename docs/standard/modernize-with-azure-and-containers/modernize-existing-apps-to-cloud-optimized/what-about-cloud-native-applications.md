---
title: Jak wygląda aplikacjom natywnym dla chmury?
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów w chmurze platformy Azure i Windows | Jak wygląda aplikacjom natywnym dla chmury?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: b84eb50c0d425447e3f78f1473608c27254523a7
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746419"
---
# <a name="what-about-cloud-native-applications"></a>Jak wygląda aplikacjom natywnym dla chmury?

Mimo że [natywnych dla chmury](https://azure.microsoft.com/overview/cloudnative/) aplikacje nie są głównym celem tego przewodnika, warto rozumieć ten poziom dojrzałości modernizacji i odróżnienia go od aplikacjami optymalizowanymi pod kątem chmury.

Rysunek 4-3 umieszcza natywnych aplikacji w chmurze w poziomie dojrzałości modernizacja aplikacji:

![Pozycjonowanie aplikacjom natywnym dla chmury](./media/image3.png)

> **Rysunek 4-3.** Pozycjonowanie aplikacjom natywnym dla chmury

Poziom dojrzałości modernizacji natywnych dla chmury zwykle wymagają nowych inwestycji rozwoju. Przejście do poziomu natywnych dla chmury zwykle wynikają potrzeba biznesowa w celu zmodernizowania możliwie najlepiej znacząco zwiększyć skalę w dużych aplikacji, tworząc podsystemy autonomicznego (mikrousług), które mogą być wdrażane i skalowania aplikacji niezależnie z innych obszarów aplikacji, obniżając jednocześnie koszty w długi czas trwania umowy i zwiększenia ewolucji elastyczności części tych aplikacji autonomicznych, które zapewniają znaczących konkurować korzyści. 

Głównych filarów aplikacji natywnych dla chmury są oparte na metody dotyczące architektury mikrousług, które ewoluują wraz z elastyczności i skalowanie do ograniczenia, które mogą być trudny do osiągnięcia w monolityczne architektury wdrożone w środowisku lokalnym lub w chmurze środowisko.

Rysunek 4-4 przedstawiono charakterystykę modelu natywnych dla chmury.  

> ![Cechy natywnych dla chmury są Mikrousług, kontenerów, odporne na błędy dla chmury i koordynatorów serverles](./media/image4.png)
>
> **Rysunek 4-4.** Właściwości natywnych dla chmury

Ponadto podstawowe nowoczesne aplikacje sieci web i aplikacji natywnych dla chmury można rozszerzyć przez dodanie innych usług, takich jak sztucznej inteligencji (AI), usługi machine learning (ML) i IoT. Można użyć dowolnej z tych usług do rozszerzenia jedną z możliwych podejść zoptymalizowane pod kątem chmury.

Jest główną różnicą w aplikacjach na poziomie natywnych dla chmury w ramach architektury aplikacji. Aplikacje natywne w chmurze są zgodnie z definicją, aplikacje, które są oparte na mikrousługach. Aplikacji natywnych dla chmury wymagają specjalnych architektury, technologii i platform, w porównaniu do monolityczną aplikację lub tradycyjny N-warstwowej.

## <a name="cloud-native-applications-details"></a>Szczegóły aplikacji natywnych dla chmury

Natywnych dla chmury jest bardziej zaawansowane lub dojrzała stanu dla aplikacji z dużymi i o kluczowym znaczeniu. Aplikacje natywne w chmurze zwykle wymagają architektury i projektowania, które są tworzone od podstaw, a nie przez modernizowanie istniejących aplikacji. Główną różnicą między aplikacji natywnych dla chmury i prostsze zoptymalizowane pod kątem chmury aplikacji sieci web to zalecenie, aby używać architektur mikrousług w podejściu natywnych dla chmury. Zoptymalizowane pod kątem chmury aplikacji może być również w aplikacji monolitycznej sieci web lub aplikacji N-warstwowych.

[Aplikacji 12-Factor](https://12factor.net/) (zbiór wzorców, które są ściśle związane ze podejścia mikrousług) jest traktowana jako wymagana dla architektury aplikacji natywnych dla chmury.

[Foundation natywnych obliczeń w chmurze (CNCF)](https://www.cncf.io/) jest podstawowym promoter zasad natywnych dla chmury. Firma Microsoft jest [członkiem CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Przykładowa definicja i więcej informacji na temat właściwości aplikacji natywnych dla chmury, zobacz artykuł firmy Gartner [architektury i projektowania aplikacji natywnych dla chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Dokładne wskazówki od firmy Microsoft o sposobie wdrażania aplikacji natywnych dla chmury, zobacz [mikrousługi .NET: Architektura konteneryzowanych aplikacji .NET](https://aka.ms/microservicesebook).

Najistotniejszym czynnikiem wziąć pod uwagę, czy migrować pełnej aplikacji natywnych dla chmury modelu jest, użytkownik musi Przekształcanie do opartych na mikrousługach architektury. Wymaga to wyraźnie znaczących inwestycji związanych z programowania ze względu na duże proces refaktoryzacji. Zazwyczaj zostanie wybrana ta opcja dla aplikacji o kluczowym znaczeniu, które wymagają nowych poziomów skalowalność i elastyczność długoterminowe. Jednak można rozpocząć przenoszenie kierunku natywnych dla chmury, dodając mikrousług dla kilku nowych scenariuszy i ostatecznie refaktoryzacji aplikacji pełni jako mikrousług. To podejście przyrostowe jest najlepszym rozwiązaniem w przypadku niektórych scenariuszy.

## <a name="what-about-microservices"></a>Jak wygląda mikrousług? 

Ważne jest zrozumienie mikrousług i sposobie ich działania, gdy rozważasz aplikacjom natywnym dla chmury w organizacji.

Architektura mikrousług jest zaawansowane metody, która służy do aplikacji, które są tworzone od podstaw lub ewolucji istniejących aplikacji do aplikacji natywnych dla chmury. Można uruchomić, dodając kilka mikrousług do istniejących aplikacji, aby dowiedzieć się o nowych paradygmatów mikrousług. Ale wyraźnie widać, należy do architektury i kodu, szczególnie w przypadku tego typu podejście.

Mikrousługi są obowiązkowe dla każdej nowej lub nowoczesnych aplikacji. Mikrousługi nie są "magic bullet" i nie są one pojedynczy, najlepszym sposobem tworzenia każdej aplikacji. Jak i kiedy używasz mikrousług zależy od typu aplikacji, które są potrzebne do utworzenia.

Architektura mikrousług staje się preferowane podejście do rozproszonego i dużych lub złożonych aplikacji o krytycznym znaczeniu, które opierają się na wiele niezależnych podsystemów w formie autonomicznej usług. W przypadku opartych na mikrousługach architektury aplikacji została stworzona jako zbiór usług, które mogą być niezależne rozwinięte, przetestowane, poddany kontroli wersji, wdrażanie i skalowanie. Może to obejmować wszystkie powiązane autonomicznej bazy danych na mikrousługach.

Aby uzyskać szczegółowy widok architektury mikrousług, które można wdrożyć przy użyciu platformy .NET Core, zobacz do pobrania plików PDF książkę elektroniczną [mikrousługi .NET: Architektura konteneryzowanych aplikacji .NET](https://aka.ms/microservicesebook). Przewodnik, dostępna jest także [online](../../microservices-architecture/index.md).

Ale nawet w scenariuszach, w których mikrousług oferują zaawansowane możliwości niezależne od wdrożenia, podsystem silnych granic i różnorodność technologii-one też wiązać się z wielu nowe wyzwania. Wyzwania odnoszą się do rozwoju aplikacji rozproszonych, takich jak modele danych pofragmentowanych i niezależne; osiągnięcie odporne na błędy komunikacji między mikrousługami; potrzebę spójność ostateczną; i złożoność operacyjną. Mikrousługi wprowadzają wyższego poziomu złożoności w porównaniu do tradycyjnych monolitycznych aplikacji.

Ze względu na złożoność architektury mikrousług są odpowiednie dla aplikacji opartych na mikrousługach tylko konkretnych scenariuszy i niektórych typów aplikacji. Obejmują one dużych i złożonych aplikacji, które mają wiele ewoluują podsystemów. W takich przypadkach warto zainwestować w bardziej złożone architektury oprogramowania, większą elastyczność długoterminowego i bardziej efektywną obsługę aplikacji. Ale w przypadku mniej złożonych scenariuszy może być lepiej kontynuować za pomocą podejścia monolitycznego aplikacji lub zbliża się prostsze N-warstwowej.

Jako ostatecznego notatki, nawet ryzyko zwrócenia powtarzających się o to pojęcie i nie powinien przyjrzymy się przy użyciu mikrousług w swoich aplikacjach jako "całości opartą or nothing wcale." Można też rozszerzyć i ewolucji istniejących aplikacji monolitycznej, dodając nowe, małe scenariusze oparte na mikrousługach. Nie trzeba zacząć od podstaw, aby rozpocząć pracę z podejścia architektury mikrousług. W rzeczywistości zaleca się, że rozwijać się używać istniejącej aplikacji monolitycznych lub N-warstwowej, dodając nowe scenariusze. Po pewnym czasie można podzielić ją do autonomicznego składników lub mikrousług. Aby rozpocząć, ewoluują aplikacji monolitycznych w kierunku mikrousług krok po kroku.

W każdym przypadku pozostałej części tej wskazówki obecne koncentruje się większość wszystkich na "Brak opartych na mikrousługach aplikacji", ponieważ te wskazówki głównie przeznaczone dla modernizacji istniejących aplikacji, mających monolityczne lub N-warstwowej architektury.

>[!div class="step-by-step"]
>[Poprzednie](microsoft-technologies-in-cloud-optimized-applications.md)
>[dalej](deploy-existing-net-apps-as-windows-containers.md)
