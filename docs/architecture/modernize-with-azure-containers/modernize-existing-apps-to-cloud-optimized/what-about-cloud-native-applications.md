---
title: A może natywne aplikacje w chmurze?
description: Modernizacja istniejących aplikacji .NET za pomocą kontenerów usługi Azure Cloud i Windows | Co z aplikacjami natywnym dla chmury?
ms.date: 04/28/2018
ms.openlocfilehash: d2a7f89e347d75ddbdae84c8eb57e32447b83297
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543550"
---
# <a name="what-about-cloud-native-applications"></a>A może natywne aplikacje w chmurze?

Chociaż aplikacje [natywne dla chmury](https://azure.microsoft.com/overview/cloudnative/) nie są głównym celem tego przewodnika, warto zrozumieć ten poziom dojrzałości modernizacji i odróżnić go od aplikacji zoptymalizowanych pod kątem chmury.

Rysunek 4-3 umieszcza aplikacje natywne dla chmury na poziomach dojrzałości modernizacji aplikacji:

![Diagram przedstawiający sposób pozycjonowanie aplikacji natywnych dla chmury.](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**Rysunek 4-3.** Pozycjonowanie aplikacji natywnych dla chmury

Poziom dojrzałości modernizacji natywnej chmury zwykle wymaga nowych inwestycji rozwojowych. Przejście do poziomu natywnego w chmurze jest zazwyczaj sterowane przez potrzebę firmy do modernizacji aplikacji w jak największym stopniu, aby drastycznie poprawić skalę w dużych aplikacjach, tworząc autonomiczne podsystemy (mikrousługi), które mogą być wdrażane i skalowane niezależnie z innych obszarów aplikacji przy jednoczesnym obniżeniu kosztów w dłuższej perspektywie i zwiększeniu elastyczności ewolucji części tych autonomicznych aplikacji, które zapewniają znaczne korzyści konkurencji.

Główne filary aplikacji natywnych dla chmury są oparte na podejściach architektury mikrousług, które mogą ewoluować z elastycznością i skalowaniem do limitów, które byłyby trudne do osiągnięcia w architekturze monolitycznej, wdrożonej w środowisku lokalnym lub w chmurze Środowiska.

Rysunek 4-4 przedstawia główne cechy modelu natywnego dla chmury.

![Diagram zawierający listę głównych cech natywnych dla chmury.](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**Rysunek 4-4.** Właściwości natywne dla chmury

Ponadto można rozszerzyć podstawowe nowoczesne aplikacje internetowe i aplikacje natywne dla chmury, dodając inne usługi, takie jak sztuczna inteligencja (AI), uczenie maszynowe (ML) i IoT. Można użyć dowolnej z tych usług, aby rozszerzyć dowolną z możliwych metod zoptymalizowanych pod kątem chmury.

Podstawowa różnica w aplikacjach na poziomie cloud-native jest w architekturze aplikacji. Aplikacje natywne dla chmury są z definicji aplikacjami opartymi na mikrousługach. Aplikacje natywne dla chmury wymagają specjalnych architektur, technologii i platform w porównaniu z monolityczną aplikacją internetową lub tradycyjną aplikacją N-Warstwową.

## <a name="cloud-native-applications-details"></a>Szczegóły aplikacji natywnych dla chmury

Cloud-Native to bardziej zaawansowany lub dojrzały stan dla dużych i krytycznych aplikacji. Aplikacje natywne dla chmury zwykle wymagają architektury i projektowania, które są tworzone od podstaw, a nie przez modernizację istniejących aplikacji. Kluczową różnicą między aplikacją natywną dla chmury a prostszą aplikacją sieci web zoptymalizowaną pod kątem chmury jest zalecenie używania architektur mikrousług w podejściu natywnym dla chmury. Aplikacje zoptymalizowane pod kątem chmury mogą być również monolitycznymi aplikacjami internetowymi lub aplikacjami N-Warstwowymi.

[Aplikacja dwunastoczynnikowa](https://12factor.net/) (kolekcja wzorców, które są ściśle związane z podejściami mikrousług) jest również uważana za wymaganie dla architektur aplikacji natywnych dla chmury.

[Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) jest głównym promotorem zasad natywnych dla chmury. Firma Microsoft jest [członkiem CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Szczegółowe wskazówki dotyczące projektowania i tworzenia aplikacji natywnych dla chmury można uzyskać w następujących bezpłatnych książkach elektronicznych:

* [Projektowanie aplikacji .NET dla platformy Azure natywnej dla chmury](../../cloud-native/introduction.md)
* [.NET Microservices: Architektura konteneryzowanych aplikacji .NET](../../microservices/index.md).

Najważniejszym czynnikiem, który należy wziąć pod uwagę podczas migracji pełnej aplikacji do modelu natywnego w chmurze, jest konieczność ponownego architekta do architektury opartej na mikrousługach. Jest to oczywiście wymagało znacznych inwestycji w rozwój ze względu na duży proces refaktoryzacji. Ta opcja jest zwykle wybierana dla aplikacji o znaczeniu krytycznym, które wymagają nowych poziomów skalowalności i długoterminowej elastyczności. Ale można rozpocząć przechodzenie w kierunku natywnych dla chmury, dodając mikrousług dla zaledwie kilku nowych scenariuszy i ostatecznie refaktoryzacji aplikacji w pełni jako mikrousług. Jest to podejście przyrostowe, które jest najlepszym rozwiązaniem dla niektórych scenariuszy.

## <a name="what-about-microservices"></a>Co z mikrousługami?

Opis mikrousług i ich działania jest ważne, gdy rozważasz aplikacji natywnych dla chmury dla organizacji.

Architektura mikrousług jest zaawansowane podejście, które można użyć dla aplikacji, które są tworzone od podstaw lub gdy rozwijać istniejące aplikacje w kierunku aplikacji natywnych dla chmury. Można rozpocząć od dodania kilku mikrousług do istniejących aplikacji, aby dowiedzieć się więcej o nowych paradygmatów mikrousług. Ale oczywiście, trzeba architekta i kodu, zwłaszcza dla tego typu podejścia architektonicznego.

Jednak mikrousługi nie są obowiązkowe dla każdej nowej lub nowoczesnej aplikacji. Mikrousługi nie są "magic bullet" i nie są one jednym, najlepszym sposobem tworzenia każdej aplikacji. Jak i kiedy używasz mikrousług zależy od typu aplikacji, które należy utworzyć.

Architektura mikrousług staje się preferowanym podejściem dla rozproszonych i dużych lub złożonych aplikacji o znaczeniu krytycznym, które są oparte na wielu niezależnych podsystemach w postaci usług autonomicznych. W architekturze opartej na mikrousługach aplikacja jest tworzona jako zbiór usług, które mogą być niezależnie opracowane, przetestowane, wersjonowane, wdrożone i skalowane. Może to obejmować wszelkie powiązane, autonomicznej bazy danych na mikrousługi.

Aby uzyskać szczegółowe spojrzenie na architekturę mikrousług, którą można zaimplementować przy użyciu programu .NET Core, zobacz do pobrania mikrousługi pdf [e-book .NET: Architektura dla konteneryzowanych aplikacji .NET](https://aka.ms/microservicesebook). Przewodnik jest również dostępny [online](../../microservices/index.md).

Ale nawet w scenariuszach, w których mikrousługi oferują zaawansowane możliwości niezależne wdrażanie, silne granice podsystemu i różnorodność technologii, ale również podnieść wiele nowych wyzwań. Wyzwania są związane z rozwojem aplikacji rozproszonych, takich jak rozdrobnione i niezależne modele danych; osiągnięcie odpornej komunikacji między mikrousługami; potrzebę ostatecznej spójności; i złożoności operacyjnej. Mikrousługi wprowadzają wyższy poziom złożoności w porównaniu do tradycyjnych aplikacji monolitycznych.

Ze względu na złożoność architektury mikrousług tylko określone scenariusze i niektóre typy aplikacji są odpowiednie dla aplikacji opartych na mikrousługach. Należą do nich duże i złożone aplikacje, które mają wiele, ewoluujących podsystemów. W takich przypadkach warto zainwestować w bardziej złożoną architekturę oprogramowania, aby zwiększyć długoterminową elastyczność i bardziej wydajną konserwację aplikacji. Jednak w przypadku mniej złożonych scenariuszy może być lepiej kontynuować z monolitycznego podejścia aplikacji lub prostsze podejścia N-Tier.

W ostatniej uwadze, nawet na ryzyko powtarzania się o tej koncepcji, nie należy patrzeć na przy użyciu mikrousług w aplikacjach jako "all-in lub nic w ogóle." Można rozszerzyć i rozwijać istniejące aplikacje monolityczne, dodając nowe, małe scenariusze oparte na mikrousługach. Nie trzeba zaczynać od zera, aby rozpocząć pracę z podejściem architektury mikrousług. W rzeczywistości zaleca się ewoluować od korzystania z istniejącej aplikacji monolityczne lub N-warstwowych przez dodanie nowych scenariuszy. Po pewnym czasie można podzielić aplikację na składniki autonomiczne lub mikrousług. Można rozpocząć ewoluowanie aplikacji monolitycznych w kierunku mikrousług, krok po kroku.

W każdym razie reszta niniejszych wskazówek koncentruje się przede wszystkim na "nie ma aplikacji opartych na mikrousługach", ponieważ te wskazówki są przeznaczone głównie do modernizacji istniejących aplikacji, które zwykle mają architektury monolityczne lub N-Tier.

> [!div class="step-by-step"]
> [Poprzedni](microsoft-technologies-in-cloud-optimized-applications.md)
> [następny](deploy-existing-net-apps-as-windows-containers.md)
