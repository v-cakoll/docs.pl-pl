---
title: Jakie aplikacje natywne chmury?
description: Modernizacji istniejących aplikacji .NET z kontenerami chmury Azure i systemu Windows | Jakie aplikacje natywne chmury?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 0e880689001ece2b770811cfbe3fea43aa425b32
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958237"
---
# <a name="what-about-cloud-native-applications"></a>Jakie aplikacje natywne chmury?

Mimo że [Native chmury](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplikacje nie podlegają głównym celem niniejszego przewodnika warto wiedzę na temat tego poziomu dojrzałości modernizacji i odróżnienia go od aplikacji zoptymalizowanych pod kątem chmury.

Rysunek 4-3 umieszcza aplikacje natywne chmury poziomu dojrzałości modernizacji aplikacji:

![Pozycjonowanie aplikacje natywne chmury](./media/image3.png)

> **Rysunek 4-3.** Pozycjonowanie aplikacje natywne chmury

Poziomu dojrzałości modernizacji Native chmury zwykle wymaga nowych programowanie inwestycji. Przenoszenie poziom natywne chmury zwykle niezależnie wynikają z potrzeb biznesowych do modernizacji jak możliwość znacząco zwiększyć skalę w dużych aplikacji przez utworzenie autonomicznego podsystemów (mikrousług), które można wdrożyć i skalowania aplikacji w innych obszarach aplikacji podczas obniżenia kosztów w długich elastyczność ewolucji termin i zwiększyć części tych aplikacji autonomicznej, które zapewniają znaczny konkurować zalety. 

Główne kolumn [Native chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikacje są oparte na mikrousług architektura metod, które można rozwijać, elastyczność i skalować do ograniczenia, które mogą być trudne w architekturze wbudowanymi wdrożyć do jednej lokalnej lub w środowisku chmury.

Rysunek 4-4 zawiera charakterystykę modelu chmury Native.  

> ![Właściwości chmury natywne są Mikrousług, kontenery odporności chmury, orchestrators i serverles](./media/image4.png)
>
> **Rysunek 4-4.** Właściwości chmury natywne

Ponadto aplikacje podstawowe nowoczesnych witryn sieci web i aplikacje natywne chmury można rozszerzyć przez dodanie innych usług, takich jak analizy sztucznego (AI), usługa machine learning (ML) i IoT. Można użyć dowolnego z tych usług do jednej z metod zoptymalizowanych pod kątem chmury można rozszerzyć.

Główną różnicą w aplikacjach na poziomie chmury natywne jest architektury aplikacji. [Chmura native](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplikacje są, zgodnie z definicją w aplikacji, które są oparte na mikrousług. Aplikacje natywne chmury wymagają specjalnych architektury, technologii i platform, w porównaniu do aplikacji sieci web wbudowanymi lub tradycyjny N-poziomowej aplikacji.

## <a name="cloud-native-applications-details"></a>Szczegóły aplikacje natywne chmury

[Chmura Native](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) jest bardziej zaawansowanych lub dojrzałe stanu dla dużych i kluczowych aplikacji. Aplikacje natywne chmury zwykle wymagają architektury i projektu, które powstały od początku zamiast modernizacji istniejących aplikacji. Najważniejsza różnica między aplikacją chmury natywne i aplikacji sieci web zoptymalizowanych pod kątem chmury prostsze jest zalecenie, aby używać mikrousług architektury w podejściu native chmury. Aplikacje zoptymalizowanych pod kątem chmury można także aplikacje wbudowanymi sieci web lub aplikacji wielowarstwowych.

[Aplikacji współczynnik dwunastu](https://12factor.net/) (kolekcja wzorców, które są ściśle związane ze podejścia mikrousług) jest traktowana jako wymagania dotyczące [native chmury](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) architekturach aplikacji.

[Foundation natywnego obliczeniowych w chmurze (CNCF)](https://www.cncf.io/) jest podstawowy promotor zasad native chmury. Firma Microsoft [członkiem CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Dla definicji próbki oraz więcej informacji na temat aplikacji natywnych chmury, zobacz artykuł Gartner [projektowania i zaprojektować aplikacje natywne chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Dokładne wskazówki firmy Microsoft dotyczące sposobu wdrażania aplikacji natywnych chmury, zobacz [mikrousług .NET: Architektura konteneryzowanych aplikacji .NET](https://aka.ms/microservicesebook).

Najważniejszym czynnikiem wziąć pod uwagę, czy migrować do pełnego zastosowania [native chmury](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) model jest, że należy rearchitect do architektura mikrousług. Wymaga to wyraźnie znaczącą inwestycję w rozwoju ze względu na duże proces refaktoryzacji. Ta opcja jest zazwyczaj wybrany dla kluczowych aplikacji wymagających nowe poziomy skalowalność i elastyczność długoterminowej. Jednak można pomyśleć kierunku native chmury przez dodanie mikrousług dla kilku nowych scenariuszy, a ostatecznie Refaktoryzuj aplikacji pełni jako mikrousług. Jest to przyrostowe metody, która jest najlepszym rozwiązaniem w przypadku niektórych scenariuszy.

## <a name="what-about-microservices"></a>Co mikrousług? 

Ważne jest zrozumienie mikrousług oraz ich współdziałaniu, gdy rozważane jest chmury natywne aplikacje dla swojej organizacji.

Architektura mikrousług jest zaawansowane metody, która służy do aplikacji, które są tworzone od początku lub rozwijać istniejące aplikacje kierunku aplikacje natywne chmury. Można uruchomić, dodając kilka mikrousług do istniejących aplikacji, aby dowiedzieć się o nowych wzorcami mikrousług. Jednak wyraźnie, musisz architektów i kod, szczególnie w przypadku tego typu architektura.

Jednak mikrousług nie są wymagane dla każdej nowej lub nowoczesnych aplikacji. Mikrousług nie są "magic bullet", a nie są jednej, najlepszym sposobem tworzenia każdej aplikacji. Jak i kiedy korzystać mikrousług zależy od typu aplikacji, która jest potrzebne do tworzenia.

Architektura mikrousług staje się to preferowane rozwiązanie dla rozproszonych i dużych lub złożonych aplikacji krytycznym, które są oparte na wiele niezależnych podsystemów w formie autonomicznej usługi. W architektura mikrousług aplikacji jest utworzony jako zbiór usług, które można niezależnie rozwinięte, przetestowane, wersji, wdrożyć i skalowania. Może to obejmować wszystkie powiązane, autonomicznej bazy danych na mikrousługi.

Aby uzyskać szczegółowy widok architektury mikrousług, które można wdrożyć przy użyciu platformy .NET Core, zobacz e-book do pobrania plików PDF [mikrousług .NET: Architektura konteneryzowanych aplikacji .NET](https://aka.ms/microservicesebook). Przewodnik jest również dostępna [online](../../microservices-architecture/index.md).

Ale nawet w scenariuszach, w których mikrousług oferują zaawansowane możliwości niezależne od wdrożenia, granice silne podsystemu i różnorodności technologii-też wiązać wiele wyzwania. Wyzwania dotyczące projektowanie aplikacji rozproszonych, takich jak modeli danych pofragmentowanych i niezależny; uzyskanie odporność komunikacji między mikrousług; potrzebę spójność ostateczna; i złożoność działania. Mikrousług wprowadzenie wyższy poziom złożoności w porównaniu do tradycyjnego wbudowanymi aplikacjami.

Ze względu na złożoność architektury mikrousług tylko konkretnych scenariuszy i niektórych typów aplikacji są odpowiednie dla aplikacji opartych na mikrousługi. Obejmują one dużych i złożonych aplikacji, które mają wiele rozwijającymi podsystemy. W takich przypadkach warto pomyśleć bardziej złożonych architektura oprogramowania, zwiększyć elastyczność długoterminowej i bardziej efektywną obsługę aplikacji. Ale dla mniej złożonymi scenariuszami, mogą być lepiej kontynuować podejście wbudowanymi aplikacji lub zbliża się do N-warstwowa prostsze.

Jako ostatecznego Uwaga, nawet ryzyko jest powtarzających się o to pojęcie nie powinien wyglądać za pomocą mikrousług w aplikacji jako "kwoty ujęte lub nic wcale." Można rozszerzać i rozwijać istniejące aplikacje wbudowanymi, dodając nowe, małe scenariusze oparte na mikrousług. Nie trzeba zacząć od początku, aby rozpocząć pracę z podejścia architektura mikrousług. W rzeczywistości zaleca się, że rozwijać z używania istniejącej aplikacji wbudowanymi lub N-warstwowa przez dodanie nowych scenariuszy. Po pewnym czasie można podzielić aplikacji w autonomicznej części lub mikrousług. Możesz przystąpić do zmieniających się wbudowanymi aplikacji w kierunku mikrousług krok po kroku.

W każdym przypadku reszty we wskazówkach tych obecny skupiono się większość wszystkich na "nie mikrousług aplikacji opartych na" ponieważ w tych wskazówkach jest skierowany głównie modernizacji istniejących aplikacji, które zwykle mają wbudowanymi lub N-warstwowa architektury.


>[!div class="step-by-step"]
[Poprzednie](microsoft-technologies-in-cloud-optimized-applications.md)
[dalej](deploy-existing-net-apps-as-windows-containers.md)
