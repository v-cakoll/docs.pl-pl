---
title: Przegląd Topologia nawigacji
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 08f6342095706e5ffe9479f5236457d21474152a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174202"
---
# <a name="navigation-topologies-overview"></a>Przegląd Topologia nawigacji
<a name="introduction"></a>Ten przegląd zawiera wprowadzenie do topologii nawigacji w WPF. Następnie omówione są trzy typowe topologie nawigacji z próbkami.  
  
> [!NOTE]
> Przed przeczytaniem tego tematu, należy zapoznać się z pojęciem nawigacji strukturalnej w WPF przy użyciu funkcji strony. Aby uzyskać więcej informacji na temat obu tych tematów, zobacz [Omówienie nawigacji strukturalnej](structured-navigation-overview.md).  
  
 Ten temat zawiera następujące sekcje:  
  
- [Topologie nawigacji](#Navigation_Topologies)  
  
- [Ustrukturyzowane topologie nawigacji](#Structured_Navigation_Topologies)  
  
- [Nawigacja po stałej topologii liniowej](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [Nawigacja dynamiczna nad stałą topologią hierarchiczną](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [Nawigacja po topologii generowanej dynamicznie](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a>Topologie nawigacji  
 W WPF WPF nawigacja<xref:System.Windows.Controls.Page>zazwyczaj składa się<xref:System.Windows.Documents.Hyperlink>ze stron ( ) z hiperłączami ( ), które nawigują do innych stron po kliknięciu. Strony, do których nawigowane są identyfikowane za pomocą jednolitych identyfikatorów zasobów (URI) (patrz [Uri pakietów w WPF).](pack-uris-in-wpf.md) Rozważmy następujący prosty przykład, który pokazuje strony, hiperłącza i jednolite identyfikatory zasobów (URI):  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Strony te są rozmieszczone w *topologii nawigacji,* której struktura zależy od sposobu nawigacji między stronami. Ta szczególna topologia nawigacji jest odpowiednia w prostych scenariuszach, chociaż nawigacja może wymagać bardziej złożonych topologii, z których niektóre można zdefiniować tylko wtedy, gdy aplikacja jest uruchomiona.  
  
 W tym temacie omówiono trzy typowe topologie nawigacji: *liniowy stały,* *stały hierarchiczny*i *generowany dynamicznie.* Każda topologia nawigacji jest pokazana za [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocą próbki, która ma podobny ten, który jest pokazany na poniższym rysunku:  
  
 ![Strony zadań z elementami danych i przyciskami nawigacyjnymi.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a>Ustrukturyzowane topologie nawigacji  
 Istnieją dwa szerokie rodzaje topologii nawigacji:  
  
- **Stała topologia:** zdefiniowana w czasie kompilacji i nie zmienia się w czasie wykonywania. Poprawione topologie są przydatne do nawigacji po stałej sekwencji stron w kolejności liniowej lub hierarchicznej.  
  
- **Topologia dynamiczna:** zdefiniowana w czasie wykonywania na podstawie danych wejściowych zebranych od użytkownika, aplikacji lub systemu. Dynamiczne topologie są przydatne, gdy strony mogą poruszać się w różnych sekwencjach.  
  
 Chociaż istnieje możliwość tworzenia topologii nawigacji przy użyciu stron, przykłady używają funkcji strony, ponieważ zapewniają dodatkową obsługę, która upraszcza obsługę przekazywania i zwracania danych za pośrednictwem stron topologii.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a>Nawigacja po stałej topologii liniowej  
 Stała topologia liniowa jest analogiczna do struktury kreatora, który ma jedną lub więcej stron kreatora, które są nawigowane w stałej kolejności. Na poniższej ilustracji przedstawiono strukturę wysokiego poziomu i przepływ kreatora o stałej topologii liniowej:  
  
 ![Diagram przedstawiający stałą topologię liniową.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 Typowe zachowania podczas nawigacji po stałej topologii liniowej są następujące:  
  
- Przechodzenie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.PageFunction%601>-less) nie jest wymagana, ponieważ strona wywołująca może wywołać pierwszą stronę kreatora bezpośrednio. Za pomocą strony uruchamiania, jednak można uprościć inicjowania kreatora, szczególnie jeśli inicjowanie jest złożone.  
  
- Użytkownicy mogą nawigować między stronami za pomocą przycisków Wstecz i Dalej (lub hiperłączy).  
  
- Użytkownicy mogą nawigować między stronami za pomocą arkusza.  
  
- Użytkownicy mogą anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
- Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
- Jeśli kreator zostanie anulowany, kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.  
  
- Jeśli użytkownik zaakceptuje kreatora, kreator zwraca odpowiedni wynik i zwraca zebrane dane.  
  
- Po zakończeniu pracy kreatora (zaakceptowaniu lub anulowaniu) strony, w skład których wchodzi kreator, zostaną usunięte z dziennika. Dzięki temu każde wystąpienie kreatora jest izolowane, co pozwala uniknąć potencjalnych anomalii danych lub stanu.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Nawigacja dynamiczna nad stałą topologią hierarchiczną  
 W niektórych aplikacjach strony umożliwiają nawigację do dwóch lub więcej innych stron, jak pokazano na poniższym rysunku:
  
 ![Diagram przedstawiający stronę, która może przejść do wielu stron.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Ta struktura jest znana jako stała hierarchiczna topologia, a sekwencja, w której hierarchia jest przechodzenia jest często określana w czasie wykonywania przez aplikację lub użytkownika. W czasie wykonywania każda strona w hierarchii, która umożliwia nawigację do dwóch lub więcej innych stron, zbiera dane wymagane do określenia, do której strony chcesz przejść. Na poniższym rysunku przedstawiono jedną z kilku możliwych sekwencji nawigacji na podstawie poprzedniego rysunku:  
  
 ![Diagram, który pokazuje możliwą sekwencję nawigacji.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 Mimo że sekwencja, w której są nawigowane strony w stałej strukturze hierarchicznej, jest określana w czasie wykonywania, środowisko użytkownika jest takie samo jak środowisko użytkownika dla stałej topologii liniowej:  
  
- Przechodzenie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.PageFunction%601>-less) nie jest wymagana, ponieważ strona wywołująca może wywołać pierwszą stronę kreatora bezpośrednio. Za pomocą strony uruchamiania, jednak można uprościć inicjowania kreatora, szczególnie jeśli inicjowanie jest złożone.  
  
- Użytkownicy mogą nawigować między stronami za pomocą przycisków Wstecz i Dalej (lub hiperłączy).  
  
- Użytkownicy mogą nawigować między stronami za pomocą arkusza.  
  
- Użytkownicy mogą zmienić sekwencję nawigacji, jeśli nawigują z powrotem po dzienniku.  
  
- Użytkownicy mogą anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
- Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
- Jeśli kreator zostanie anulowany, kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.  
  
- Jeśli użytkownik zaakceptuje kreatora, kreator zwraca odpowiedni wynik i zwraca zebrane dane.  
  
- Po zakończeniu pracy kreatora (zaakceptowaniu lub anulowaniu) strony, w skład których wchodzi kreator, zostaną usunięte z dziennika. Dzięki temu każde wystąpienie kreatora jest izolowane, co pozwala uniknąć potencjalnych anomalii danych lub stanu.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a>Nawigacja po topologii generowanej dynamicznie  
 W niektórych aplikacjach sekwencja, w której nawigowane są dwie lub więcej stron, może być określona tylko w czasie wykonywania, czy przez użytkownika, aplikacji lub danych zewnętrznych. Na poniższym rysunku przedstawiono zestaw stron z nieokreśloną sekwencją nawigacji:  
  
 ![Zestaw stron z nieokreśloną sekwencją nawigacji.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 Następny rysunek ilustruje sekwencję nawigacji, która została wybrana przez użytkownika w czasie wykonywania:  
  
 ![Diagram przedstawiający sekwencję nawigacji wybraną w czasie wykonywania.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 Sekwencja nawigacji jest znana jako dynamicznie generowana topologia. Dla użytkownika, podobnie jak w przypadku innych topologii nawigacji, środowisko użytkownika jest takie samo, jak w przypadku poprzednich topologii:  
  
- Przechodzenie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Navigation.PageFunction%601>-less) nie jest wymagana, ponieważ strona wywołująca może wywołać pierwszą stronę kreatora bezpośrednio. Za pomocą strony uruchamiania, jednak można uprościć inicjowania kreatora, szczególnie jeśli inicjowanie jest złożone.  
  
- Użytkownicy mogą nawigować między stronami za pomocą przycisków Wstecz i Dalej (lub hiperłączy).  
  
- Użytkownicy mogą nawigować między stronami za pomocą arkusza.  
  
- Użytkownicy mogą anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
- Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
- Jeśli kreator zostanie anulowany, kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.  
  
- Jeśli użytkownik zaakceptuje kreatora, kreator zwraca odpowiedni wynik i zwraca zebrane dane.  
  
- Po zakończeniu pracy kreatora (zaakceptowaniu lub anulowaniu) strony, w skład których wchodzi kreator, zostaną usunięte z dziennika. Dzięki temu każde wystąpienie kreatora jest izolowane, co pozwala uniknąć potencjalnych anomalii danych lub stanu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Przegląd Strukturyzowana nawigacja](structured-navigation-overview.md)
