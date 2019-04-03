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
ms.openlocfilehash: 3e5cca90861ccdeaff904a34c6f484cfdd32c975
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819596"
---
# <a name="navigation-topologies-overview"></a>Przegląd Topologia nawigacji
<a name="introduction"></a> W tym omówieniu przedstawiono wprowadzenie do topologii nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Następnie opisano trzy popularne topologie nawigacji, z przykładami.  
  
> [!NOTE]
>  Przed odczytaniem w tym temacie, należy zapoznać się z pojęciem strukturyzowana Nawigacja w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] za pomocą funkcji strony. Aby uzyskać więcej informacji na temat obu tych tematów, zobacz [ze strukturą Przegląd Nawigacja](structured-navigation-overview.md).  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Topologie nawigacji](#Navigation_Topologies)  
  
-   [Topologie strukturyzowana Nawigacja](#Structured_Navigation_Topologies)  
  
-   [Nawigacja za pośrednictwem stały liniowa topologia](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [Dynamicznej nawigacji nad stały hierarchiczna topologia](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [Nawigacja w dynamicznie generowanym topologii](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Topologie nawigacji  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], nawigacji zwykle składa się z stron (<xref:System.Windows.Controls.Page>) za pomocą hiperlinków (<xref:System.Windows.Documents.Hyperlink>), przejdź do innych stron, po kliknięciu. Stron, które są przejście, są identyfikowane przez [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (zobacz [pakiet URI w WPF](pack-uris-in-wpf.md)). Należy wziąć pod uwagę następujące prosty przykład pokazujący hiperłącza, strony i [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Te strony są rozmieszczane w *topologia nawigacji* której strukturę zależy od sposobu można nawigować między stronami. Ta topologia nawigacji w szczególności jest odpowiedni w przypadku prostych scenariuszy, chociaż nawigacji mogą wymagać bardziej złożonych topologii, niektóre z nich mogą być definiowane tylko gdy aplikacja jest uruchomiona.  
  
 W tym temacie opisano trzy popularne topologie nawigacji: *stała liniowa*, *stała hierarchiczna*, i *dynamicznie generowanym*. Każda topologia nawigacji przedstawiono przykład, który ma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jak te, które przedstawiono na poniższej ilustracji:  
  
 ![Strony zadania przy użyciu elementów danych i przycisków nawigacji.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Topologie strukturyzowana Nawigacja  
 Istnieją dwa ogólne typy topologie nawigacji:  
  
-   **Stała topologia**: zdefiniowany w czasie kompilacji i nie zmienia się w czasie wykonywania. Naprawiono topologii są przydatne do nawigacji za pomocą stałych sekwencji stron w kolejności liniowy lub hierarchiczny.  
  
-   **Dynamiczne topologii**: zdefiniowany w czasie wykonywania, w oparciu o dane wejściowe, które są zbierane od użytkownika, aplikacji lub systemu. Dynamiczne topologii są przydatne, gdy strony można nawigować w różnych sekwencji.  
  
 Chociaż istnieje możliwość utworzenia topologie nawigacji za pomocą stron, przykłady funkcji strony należy użyć w sytuacji, ponieważ zapewniają dodatkową pomoc, która upraszcza obsługę przekazywanie i zwracanie danych na stronach topologii.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Nawigacja za pośrednictwem stały liniowa topologia  
 Naprawiono liniowa topologia jest analogiczne do struktury kreatora, który ma co najmniej jednej strony kreatora, które są przejście w stałej kolejności. Na poniższej ilustracji przedstawiono ogólną strukturę i przepływ kreatora bez stały liniowa topologia:  
  
 ![Diagram, który pokazuje stały liniowa topologia.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 Następujące typowe zachowania do nawigowania w stałym liniowa topologia:  
  
-   Przechodząc ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]— mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagane, ponieważ wywołujący strony można bezpośrednio wywoływać pierwszej stronie kreatora. Przy użyciu strony uruchamiania, jednak można uprościć inicjowanie kreatora, szczególnie w przypadku, gdy inicjalizacja jest złożony.  
  
-   Użytkownicy mogą przejść między stronami, korzystając z tyłu i do przodu przycisków (lub hiperłącza).  
  
-   Użytkownicy mogą przejść między stronami przy użyciu arkusza.  
  
-   Użytkownikom można anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
-   Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
-   Jeśli Kreator zostanie anulowane, Kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.  
  
-   Jeśli użytkownik zaakceptuje kreatora, Kreator zwraca odpowiedni wynik i zwraca dane zebrane.  
  
-   Po ukończeniu pracy kreatora (zaakceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika. Dzięki temu każde wystąpienie Kreatora izolowane, zapobiegając potencjalnych danych lub nieprawidłowości stanu.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Dynamicznej nawigacji nad stały hierarchiczna topologia  
 W niektórych aplikacjach strony umożliwiają przechodzenie do co najmniej dwóch innych stron, jak pokazano na poniższej ilustracji: 
  
 ![Diagram przedstawiający strona, która można przejść do wielu stron.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Ta struktura jest znany jako stały topologii hierarchicznej i sekwencji, w którym hierarchii, o ile jest często określana w czasie wykonywania przez użytkownika lub aplikacji. W czasie wykonywania każda strona w hierarchii, która umożliwia przechodzenie do co najmniej dwóch innych stron zbiera dane wymagane do określenia, które strony dla przejścia. Na poniższym rysunku przedstawiono jeden z kilku sekwencji nawigacji możliwe oparte na poprzedniej ilustracji:  
  
 ![Diagram przedstawiający sekwencję nawigacji to możliwe.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 Mimo że sekwencji, w którym są przejście stron w strukturze hierarchicznej stałej jest określana w czasie wykonywania, środowisko użytkownika jest taki sam jak środowiska użytkownika dla stałych liniowa topologia:  
  
-   Przechodząc ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]— mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagane, ponieważ wywołujący strony można bezpośrednio wywoływać pierwszej stronie kreatora. Przy użyciu strony uruchamiania, jednak można uprościć inicjowanie kreatora, szczególnie w przypadku, gdy inicjalizacja jest złożony.  
  
-   Użytkownicy mogą przejść między stronami, korzystając z tyłu i do przodu przycisków (lub hiperłącza).  
  
-   Użytkownicy mogą przejść między stronami przy użyciu arkusza.  
  
-   Użytkownicy mogą zmienić sekwencję nawigacji, jeśli ich poruszanie się wstecz arkusza.  
  
-   Użytkownikom można anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
-   Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
-   Jeśli Kreator zostanie anulowane, Kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.  
  
-   Jeśli użytkownik zaakceptuje kreatora, Kreator zwraca odpowiedni wynik i zwraca dane zebrane.  
  
-   Po ukończeniu pracy kreatora (zaakceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika. Dzięki temu każde wystąpienie Kreatora izolowane, zapobiegając potencjalnych danych lub nieprawidłowości stanu.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Nawigacja w dynamicznie generowanym topologii  
 W niektórych aplikacjach sekwencji, w którym są przejście, dwóch lub więcej stron można tylko można określić w czasie wykonywania przez użytkownika, aplikacji lub danych zewnętrznych. Na poniższym rysunku przedstawiono zestaw stron z sekwencją nieokreślonej nawigacji:  
  
 ![Zestaw stron z sekwencją nieokreślonej nawigacji.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 Następny rysunek przedstawia sekwencję nawigacji, który został wybrany przez użytkownika w czasie wykonywania:  
  
 ![Diagram przedstawiający sekwencję nawigacji wybranej w czasie wykonywania.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 Sekwencję nawigacji jest określany jako dynamicznie generowanym topologii. Dla użytkownika jako przy użyciu innych topologie nawigacji środowisko użytkownika jest taka sama jak w przypadku poprzedniego topologii:  
  
-   Przechodząc ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]— mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagane, ponieważ wywołujący strony można bezpośrednio wywoływać pierwszej stronie kreatora. Przy użyciu strony uruchamiania, jednak można uprościć inicjowanie kreatora, szczególnie w przypadku, gdy inicjalizacja jest złożony.  
  
-   Użytkownicy mogą przejść między stronami, korzystając z tyłu i do przodu przycisków (lub hiperłącza).  
  
-   Użytkownicy mogą przejść między stronami przy użyciu arkusza.  
  
-   Użytkownikom można anulować kreatora z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
-   Użytkownicy mogą zaakceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
-   Jeśli Kreator zostanie anulowane, Kreator zwraca odpowiedni wynik i nie zwraca żadnych danych.  
  
-   Jeśli użytkownik zaakceptuje kreatora, Kreator zwraca odpowiedni wynik i zwraca dane zebrane.  
  
-   Po ukończeniu pracy kreatora (zaakceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika. Dzięki temu każde wystąpienie Kreatora izolowane, zapobiegając potencjalnych danych lub nieprawidłowości stanu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Strukturyzowana nawigacja — omówienie](structured-navigation-overview.md)
