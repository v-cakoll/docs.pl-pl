---
title: A może natywne aplikacje w chmurze?
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Co z aplikacjami natywnymi w chmurze?
ms.date: 04/28/2018
ms.openlocfilehash: cf4c3b24a4eeb62ed84a5fccb294b675d38fcc36
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2019
ms.locfileid: "72318437"
---
# <a name="what-about-cloud-native-applications"></a>A może natywne aplikacje w chmurze?

Chociaż aplikacje [natywne w chmurze](https://azure.microsoft.com/overview/cloudnative/) nie są głównym celem tego przewodnika, warto zrozumieć ten poziom dojrzałości, aby odróżnić go od aplikacji zoptymalizowanych pod kątem chmury.

Rysunek 4-3. rozmieszczenie aplikacji natywnych w chmurze w ramach poziomów dojrzałości dla modernizacji aplikacji:

![Diagram przedstawiający sposób pozycjonowania aplikacji natywnych w chmurze.](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**Rysunek 4-3.** Pozycjonowanie aplikacji natywnych w chmurze

Poziom dojrzałości w chmurze, który ma zwykle nowe inwestycje rozwojowe. Przechodzenie do poziomu natywnego chmury zwykle jest zależne od potrzeb firmy, aby przeprowadzić modernizację aplikacji tak, aby znacznie zwiększyć skalę w dużych aplikacjach przez tworzenie autonomicznych podsystemów (mikrousług), które można wdrażać i skalować niezależnie z innych obszarów aplikacji przy jednoczesnym obniżeniu kosztów w długim okresie i zwiększenia elastyczności rozwoju tych części aplikacji autonomicznej, które zapewniają znaczące korzyści z konkurowania.

Główne filary natywnych aplikacji w chmurze opierają się na architekturze mikrousług, które mogą rozwijać elastyczność i skalować do ograniczeń, które byłyby trudne do osiągnięcia w postaci monolitycznej architektury wdrożonej w środowisku lokalnym lub w chmurze naturalne.

Rysunek 4-4 przedstawia główne właściwości modelu natywnego w chmurze.

![Diagram zawierający listę głównych cech natywnych w chmurze.](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**Rysunek 4-4.** Charakterystyki natywne w chmurze

Ponadto można rozciągnąć podstawowe nowoczesne aplikacje sieci Web i natywne aplikacje w chmurze, dodając inne usługi, takie jak sztuczna inteligencja (AI), uczenie maszynowe (ML) i IoT. Możesz użyć dowolnej z tych usług, aby zwiększyć dowolne możliwe podejścia zoptymalizowane pod kątem chmury.

Podstawowa różnica w aplikacjach na poziomie natywnym w chmurze znajduje się w architekturze aplikacji. Aplikacje natywne w chmurze są według definicji aplikacji opartych na mikrousługach. Aplikacje natywne w chmurze wymagają specjalnej architektury, technologii i platform w porównaniu do monolitycznej aplikacji sieci Web lub tradycyjnej aplikacji N-warstwowej.

## <a name="cloud-native-applications-details"></a>Szczegóły aplikacji natywnych w chmurze

Chmura w chmurze to bardziej zaawansowany lub dojrzały stan dla aplikacji o dużym znaczeniu i o newralgicznych działaniach. Aplikacje natywne w chmurze wymagają zwykle architektury i projektu, które są tworzone od podstaw zamiast modernizacji istniejących aplikacji. Kluczową różnicą między aplikacją natywną w chmurze a uproszczoną aplikacją sieci Web zoptymalizowaną pod kątem chmury jest zalecenie do korzystania z architektur mikrousług w ramach podejścia natywnego w chmurze. Aplikacje zoptymalizowane pod kątem chmury mogą być również litymi aplikacjami sieci Web lub aplikacjami N-warstwowymi.

[Aplikacja 12-składnikowa](https://12factor.net/) (kolekcja wzorców ściśle powiązanych z podejściem mikrousług) jest również uważana za wymagania dotyczące architektur aplikacji natywnych w chmurze.

[Natywna platforma obliczeniowa w chmurze (CNCF)](https://www.cncf.io/) to podstawowy stymulator zasad natywnych w chmurze. Firma Microsoft jest [członkiem CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Aby zapoznać się z przykładową definicją i uzyskać więcej informacji na temat cech aplikacji natywnych w chmurze, zobacz artykuł [dotyczący tworzenia i projektowania aplikacji natywnych dla chmury](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Aby uzyskać szczegółowe wskazówki od firmy Microsoft dotyczące implementowania aplikacji natywnej w chmurze, zobacz [.NET mikrousługi: architektura dla kontenerów aplikacji .NET](https://aka.ms/microservicesebook).

Najważniejszym czynnikiem, które należy wziąć pod uwagę w przypadku migrowania pełnej aplikacji do modelu natywnego w chmurze, jest konieczność przeprowadzenia ponownej architektury na architekturę opartą na mikrousługach. To wyraźnie wymaga znaczących inwestycji w rozwój z powodu dużego procesu refaktoryzacji. Ta opcja jest zwykle wybierana dla aplikacji o krytycznym znaczeniu, które wymagają nowych poziomów skalowalności i długoterminowej elastyczności. Można jednak zacząć poruszać się w chmurze, dodając mikrousługi dla zaledwie kilku nowych scenariuszy, a ostatecznie refaktoryzację aplikacji w pełni jako mikrousługi. Jest to przyrostowe podejście, które jest najlepszą opcją dla niektórych scenariuszy.

## <a name="what-about-microservices"></a>Co z mikrousługami?

Informacje o mikrousługach i sposobie ich działania są ważne w przypadku rozważania aplikacji natywnych dla Twojej organizacji.

Architektura mikrousług jest zaawansowanym podejściem, którego można używać w przypadku aplikacji tworzonych od podstaw lub podczas rozwijania istniejących aplikacji do aplikacji natywnych w chmurze. Aby dowiedzieć się więcej o nowych odmianach mikrousług, możesz zacząć od dodania kilku mikrousług do istniejących aplikacji. Ale jasno, należy zaprojektować i kod, szczególnie w przypadku tego typu podejścia do architektury.

Jednak mikrousługi nie są obowiązkowe dla żadnej nowej lub nowoczesnej aplikacji. Mikrousługi nie są "magicznym punktorem" i nie są pojedynczym, najlepszym sposobem tworzenia każdej aplikacji. Jak i kiedy używać mikrousług, zależy od typu aplikacji, którą należy skompilować.

Architektura mikrousług jest preferowanym podejściem dla rozproszonych i dużych lub złożonych aplikacji o znaczeniu strategicznym, które są oparte na wielu niezależnych podsystemach w formie usług autonomicznych. W architekturze opartej na mikrousługach aplikacja jest zbudowana jako kolekcja usług, które mogą być osobno opracowane, przetestowane, w wersji, wdrożone i skalowane. Może to obejmować wszystkie powiązane, autonomiczną bazę danych na mikrousługi.

Aby zapoznać się z szczegółowym opisem architektury mikrousług, którą można zaimplementować przy użyciu platformy .NET Core, zobacz artykuł z możliwością pobierania w formacie PDF-książka [dla aplikacji platformy .NET](https://aka.ms/microservicesebook). Przewodnik jest również dostępny w [trybie online](../../microservices/index.md).

Jednak nawet w scenariuszach, w których mikrousługi oferują zaawansowane funkcje, niezależne wdrożenie, ścisłe granice podsystemu i różnorodność technologii — powodują także wiele nowych wyzwań. Wyzwania dotyczą tworzenia aplikacji rozproszonych, takich jak pofragmentowane i niezależne modele danych; osiągnięcie odpornej komunikacji między mikrousługami; konieczność zapewnienia spójności ostatecznej; i złożoność operacyjna. Mikrousługi wprowadzają wyższy poziom złożoności w porównaniu z tradycyjnymi aplikacjami monolitycznymi.

Ze względu na złożoność architektury mikrousług, w przypadku aplikacji opartych na mikrousługach odpowiednie są tylko określone scenariusze i niektóre typy aplikacji. Obejmują one duże i złożone aplikacje, które mają wiele różnych podsystemów. W takich przypadkach warto zainwestować w bardziej złożoną architekturę oprogramowania, co zwiększa elastyczność i wydajniejszą konserwację aplikacji. Jednak w przypadku mniej złożonych scenariuszy lepszym rozwiązaniem może być podwyższenie poziomu aplikacji lub prostsze podejście N-warstwowe.

W ostatecznej uwadze, nawet w przypadku ryzyka powtarzania tego pojęcia, nie należy używać mikrousług w aplikacjach jako "All-in lub Nothing". Możesz rozwijać i rozwijać istniejące aplikacje monolityczne, dodając nowe, małe scenariusze oparte na mikrousługach. Nie musisz zaczynać od podstaw, aby rozpocząć pracę z podejściem do architektury mikrousług. W rzeczywistości zalecamy, aby rozwijać z używania istniejącej aplikacji monolitycznej lub N-warstwowej przez dodanie nowych scenariuszy. Na koniec możesz podzielić aplikację na autonomiczne składniki lub mikrousługi. Możesz zacząć rozwijającać się aplikacje monolityczne w kierunku mikrousług, krok po kroku.

W każdym przypadku pozostała część niniejszych wskazówek koncentruje się na większości wszystkich "aplikacji opartych na mikrousługach", ponieważ te wskazówki odnoszą się głównie do modernizacji istniejących aplikacji, które zwykle mają warstwy monolityczne lub N-warstwowe.

> [!div class="step-by-step"]
> [Poprzedni](microsoft-technologies-in-cloud-optimized-applications.md)
> [dalej](deploy-existing-net-apps-as-windows-containers.md)
