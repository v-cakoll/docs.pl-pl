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
ms.openlocfilehash: b62432d64393f4fb749af2e25c42e2e0161de219
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950746"
---
# <a name="navigation-topologies-overview"></a>Przegląd Topologia nawigacji
<a name="introduction"></a>To omówienie zawiera wprowadzenie do topologii nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie. Trzy popularne topologie nawigacji wraz z przykładami zostały omówione w dalszej części.  
  
> [!NOTE]
> Przed przeczytaniem tego tematu należy zapoznać się z koncepcją nawigacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] strukturalnej przy użyciu funkcji strony. Aby uzyskać więcej informacji na temat obu tych tematów, zobacz [Omówienie nawigacji strukturalnej](structured-navigation-overview.md).  
  
 Ten temat zawiera następujące sekcje:  
  
- [Topologie nawigacji](#Navigation_Topologies)  
  
- [Topologie nawigacji strukturalnej](#Structured_Navigation_Topologies)  
  
- [Nawigowanie po stałej topologii liniowej](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [Dynamiczna Nawigacja w ramach stałej topologii hierarchicznej](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [Nawigacja w ramach dynamicznie generowanej topologii](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Topologie nawigacji  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie Nawigacja zwykle składa się ze<xref:System.Windows.Controls.Page>stron () za<xref:System.Windows.Documents.Hyperlink>pomocą hiperlinków (), które przeprowadzą do innych stron po kliknięciu. Strony, do których prowadzi przechodzenie, są [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] identyfikowane przez (zobacz [identyfikatory URI pakietu w WPF](pack-uris-in-wpf.md)). Rozważmy następujący prosty przykład pokazujący strony, hiperłącza i [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Te strony są rozmieszczone w *topologii nawigacyjnej* , której struktura jest określana w sposób, w jaki można przechodzić między stronami. Ta topologia nawigacji jest odpowiednia w prostych scenariuszach, chociaż Nawigacja może wymagać bardziej złożonych topologii, a niektóre z nich można zdefiniować tylko wtedy, gdy aplikacja jest uruchomiona.  
  
 W tym temacie opisano trzy popularne topologie nawigacji: *stałe liniowe*, *stałe*, hierarchiczne i *dynamicznie generowane*. Każda topologia nawigacji jest przedstawiona przy użyciu przykładu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , który ma taki sam sposób jak ten, który jest przedstawiony na poniższym rysunku:  
  
 ![Strony zadań z elementami danych i przyciskami nawigacji.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Topologie nawigacji strukturalnej  
 Istnieją dwa popularne typy topologii nawigacyjnej:  
  
- **Stała topologia**: zdefiniowana w czasie kompilacji i nie zmienia się w czasie wykonywania. Stałe topologie są przydatne do nawigacji przez stałą sekwencję stron w kolejności liniowej lub hierarchicznej.  
  
- **Topologia dynamiczna**: zdefiniowana w czasie wykonywania na podstawie danych wejściowych zbieranych od użytkownika, aplikacji lub systemu. Topologie dynamiczne są przydatne, gdy strony można nawigować w różnych sekwencjach.  
  
 Chociaż istnieje możliwość tworzenia topologii nawigacji przy użyciu stron, przykłady używają funkcji strony, ponieważ zapewniają dodatkową pomoc techniczną, która upraszcza obsługę przekazywania i zwracania danych za pośrednictwem stron topologii.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Nawigowanie po stałej topologii liniowej  
 Stała topologia liniowa jest analogiczna do struktury kreatora, która zawiera co najmniej jedną stronę kreatora, która jest używana w ustalonej kolejności. Na poniższej ilustracji przedstawiono strukturę i przepływ kreatora ze stałą topologią liniową:  
  
 ![Diagram przedstawiający stałą topologię liniową.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 Typowe zachowania w przypadku nawigowania po ustalonej topologii liniowej obejmują następujące elementy:  
  
- Nawigowanie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ strona wywołująca może bezpośrednio wywołać pierwszą stronę kreatora. Za pomocą strony uruchamiania można jednak uprościć inicjowanie kreatora, szczególnie jeśli Inicjalizacja jest złożona.  
  
- Użytkownicy mogą przechodzić między stronami przy użyciu przycisków Wstecz i dalej (lub hiperlinków).  
  
- Użytkownicy mogą przechodzić między stronami przy użyciu dziennika.  
  
- Użytkownicy mogą anulować pracę kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
- Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
- Jeśli Kreator zostanie anulowany, Kreator zwróci odpowiedni wynik i nie zwróci żadnych danych.  
  
- Jeśli użytkownik zaakceptuje kreatora, Kreator zwróci odpowiedni wynik i zwróci zebrane dane.  
  
- Po zakończeniu pracy kreatora (zaakceptowane lub anulowane) strony, które składają się Kreator, są usuwane z dziennika. Pozwala to na odizolowanie każdego wystąpienia kreatora, co pozwala uniknąć potencjalnych różnic danych lub stanu.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Dynamiczna Nawigacja w ramach stałej topologii hierarchicznej  
 W niektórych aplikacjach strony umożliwiają nawigację do dwóch lub więcej stron, jak pokazano na poniższym rysunku: 
  
 ![Diagram pokazujący stronę, która może przechodzić do wielu stron.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Ta struktura jest znana jako stała hierarchiczna topologia, a sekwencja, w której przechodzą hierarchie, jest często określana w czasie wykonywania przez aplikację lub użytkownika. W czasie wykonywania każda Strona w hierarchii, która umożliwia nawigowanie do dwóch lub więcej stron, zbiera dane wymagane do określenia, do której strony należy przejść. Na poniższej ilustracji przedstawiono jedną z kilku możliwych sekwencji nawigacji na podstawie poprzedniej ilustracji:  
  
 ![Diagram, który pokazuje możliwe sekwencję nawigacji.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 Mimo że przechodzenie między stronami w stałej strukturze hierarchicznej jest określane w czasie wykonywania, środowisko użytkownika jest takie samo jak środowisko użytkownika dla stałej topologii liniowej:  
  
- Nawigowanie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ strona wywołująca może bezpośrednio wywołać pierwszą stronę kreatora. Za pomocą strony uruchamiania można jednak uprościć inicjowanie kreatora, szczególnie jeśli Inicjalizacja jest złożona.  
  
- Użytkownicy mogą przechodzić między stronami przy użyciu przycisków Wstecz i dalej (lub hiperlinków).  
  
- Użytkownicy mogą przechodzić między stronami przy użyciu dziennika.  
  
- Użytkownicy mogą zmienić sekwencję nawigacji, jeśli nawigują ponownie w dzienniku.  
  
- Użytkownicy mogą anulować pracę kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
- Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
- Jeśli Kreator zostanie anulowany, Kreator zwróci odpowiedni wynik i nie zwróci żadnych danych.  
  
- Jeśli użytkownik zaakceptuje kreatora, Kreator zwróci odpowiedni wynik i zwróci zebrane dane.  
  
- Po zakończeniu pracy kreatora (zaakceptowane lub anulowane) strony, które składają się Kreator, są usuwane z dziennika. Pozwala to na odizolowanie każdego wystąpienia kreatora, co pozwala uniknąć potencjalnych różnic danych lub stanu.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Nawigacja w ramach dynamicznie generowanej topologii  
 W niektórych aplikacjach sekwencja, w której są przechodź dwie lub więcej stron, można określić tylko w czasie wykonywania, niezależnie od tego, czy użytkownik, aplikacja lub dane zewnętrzne. Na poniższej ilustracji przedstawiono zestaw stron z nieokreśloną sekwencją nawigacji:  
  
 ![Zestaw stron z nieokreśloną sekwencją nawigacji.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 Następny rysunek ilustruje sekwencję nawigacji, która została wybrana przez użytkownika w czasie wykonywania:  
  
 ![Diagram pokazujący sekwencję nawigacji wybraną w czasie wykonywania.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 Sekwencja nawigacji jest znana jako topologia generowana dynamicznie. Dla użytkownika, podobnie jak w przypadku innych topologii nawigacyjnej, środowisko użytkownika jest takie samo, jak w przypadku poprzednich topologii:  
  
- Nawigowanie ze strony wywołującej do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ strona wywołująca może bezpośrednio wywołać pierwszą stronę kreatora. Za pomocą strony uruchamiania można jednak uprościć inicjowanie kreatora, szczególnie jeśli Inicjalizacja jest złożona.  
  
- Użytkownicy mogą przechodzić między stronami przy użyciu przycisków Wstecz i dalej (lub hiperlinków).  
  
- Użytkownicy mogą przechodzić między stronami przy użyciu dziennika.  
  
- Użytkownicy mogą anulować pracę kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
- Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
- Jeśli Kreator zostanie anulowany, Kreator zwróci odpowiedni wynik i nie zwróci żadnych danych.  
  
- Jeśli użytkownik zaakceptuje kreatora, Kreator zwróci odpowiedni wynik i zwróci zebrane dane.  
  
- Po zakończeniu pracy kreatora (zaakceptowane lub anulowane) strony, które składają się Kreator, są usuwane z dziennika. Pozwala to na odizolowanie każdego wystąpienia kreatora, co pozwala uniknąć potencjalnych różnic danych lub stanu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Strukturyzowana nawigacja — omówienie](structured-navigation-overview.md)
