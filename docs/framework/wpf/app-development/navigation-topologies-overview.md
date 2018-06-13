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
ms.openlocfilehash: 8976ba7973e4f53022846b98c47d5613fd6ba158
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557553"
---
# <a name="navigation-topologies-overview"></a>Przegląd Topologia nawigacji
<a name="introduction"></a> Ten przegląd zawiera wprowadzenie do topologii nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Następnie omówiono trzy popularne topologie nawigacji, z próbek.  
  
> [!NOTE]
>  Przed przeczytaniem tego tematu, należy zapoznać się z pojęciem strukturze nawigacji w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] przy użyciu funkcji strony. Aby uzyskać więcej informacji na obu tych tematów, zobacz [strukturalnych omówienie nawigacji](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md).  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Topologie nawigacji](#Navigation_Topologies)  
  
-   [Topologie strukturze nawigacji](#Structured_Navigation_Topologies)  
  
-   [Nawigacji za pośrednictwem stałym topologii liniowy](#Navigation_over_a_Fixed_Linear_Topology)  
  
-   [Dynamiczne nawigacji w topologii hierarchicznej stałej](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
-   [Nawigacji na dynamicznie generowanym topologii](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Topologie nawigacji  
 W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], nawigacji zazwyczaj składa się z stron (<xref:System.Windows.Controls.Page>) na hiperłącza (<xref:System.Windows.Documents.Hyperlink>) który przejdź do innych stron, po kliknięciu. Strony, które są przejście są identyfikowane przez [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] (zobacz [identyfikatorów URI pakietu na platformie WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)). Należy wziąć pod uwagę następujące prosty przykład pokazujący stron, hiperłącza, i [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]:  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Te strony są rozmieszczone w *topologii nawigacji* której strukturę zależy od sposobu można przechodzić między stronami. Ta topologia określonego nawigacji jest odpowiednie w scenariuszach prostego, ale nawigacji może wymagać bardziej złożonej topologii, niektóre z nich można zdefiniować tylko gdy aplikacja jest uruchomiona.  
  
 W tym temacie omówiono trzy popularne topologie nawigacji: *stałej liniowej*, *stałej hierarchiczna*, i *dynamicznie generowanym*. Każdej topologii nawigacji przedstawiono próbkę, który ma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , takich jak to przedstawiono na poniższej ilustracji:  
  
 ![Zadanie stron z elementami danych](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure6.png "NavigationTopologyFigure6")  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Topologie strukturze nawigacji  
 Istnieją dwa ogólne typy topologii nawigacji:  
  
-   **Stałe topologii**: zdefiniowany w czasie kompilacji i nie zmienia się w czasie wykonywania. Stały topologii są przydatne w przypadku nawigację stałym sekwencji stron w kolejności liniowego lub hierarchicznej.  
  
-   **Dynamiczne topologii**: zdefiniowany w czasie wykonywania w oparciu o dane wejściowe, zbierane od użytkownika, aplikacji lub systemu. Topologie dynamiczne są przydatne, gdy strony może zostać przesłane w różnych sekwencji.  
  
 Chociaż można utworzyć za pomocą stron topologie nawigacji, przykłady używać funkcji strony, ponieważ zapewniają dodatkową pomoc, który upraszcza obsługę przekazywanie i zwracający dane na stronach topologii.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Nawigacji za pośrednictwem stałym topologii liniowy  
 Stałe topologii liniowego jest odpowiednikiem struktury kreatora, który ma co najmniej jeden stronach kreatora, które są przejście w stałej kolejności. Na poniższej ilustracji przedstawiono wysokiego poziomu struktury i przepływu kreatora przy stałym topologii liniowej.  
  
 ![Diagram topologii nawigacji](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure1.png "NavigationTopologyFigure1")  
  
 Następujące typowe zachowania do nawigowania za pośrednictwem stałym topologii liniowej:  
  
-   Przejście ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ wywołujący strony można wywołać bezpośrednio pierwszej stronie kreatora. Przy użyciu strony uruchamiania, jednak może uprościć Kreatora inicjowania, zwłaszcza w wypadku inicjowania jest złożony.  
  
-   Użytkownicy mogą przechodzić między stronami przy użyciu Wstecz i do przodu przycisków (lub hiperłącza).  
  
-   Użytkownicy mogą przechodzić między stronami przy użyciu arkusza.  
  
-   Użytkownicy mogą anulować pracę z kreatorem z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
-   Użytkownicy mogą akceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
-   Kreator zostało anulowane, Kreator zwraca wynik w odpowiednich i nie zwraca żadnych danych.  
  
-   Jeśli użytkownik akceptuje kreatora, Kreator zwraca wynik w odpowiednich i zwraca dane zebrane.  
  
-   Po ukończeniu pracy kreatora (akceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika. Dzięki temu każde wystąpienie Kreatora samodzielnie, zapobiegając potencjalnych danych lub nieprawidłowości stanu.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Dynamiczne nawigacji w topologii hierarchicznej stałej  
 W niektórych aplikacjach strony umożliwiają nawigacji do dwóch lub więcej innych stron, jak pokazano na poniższej ilustracji.  
  
 ![Strona, która może przejść do wielu stron](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure2.png "NavigationTopologyFigure2")  
  
 Ta struktura jest określane jako stały topologii hierarchicznej i sekwencji, w którym przecina w hierarchii jest często określana w czasie wykonywania przez użytkownika lub aplikacji. W czasie wykonywania każdej strony w hierarchii, które umożliwia nawigacji do dwóch lub więcej stron zbiera dane wymagane do określenia, aby przejść do strony. Poniższa ilustracja przedstawia jedną z kilku sekwencji nawigacji możliwe oparte na powyższej ilustracji.  
  
 ![Diagram topologii nawigacji](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure3.png "NavigationTopologyFigure3")  
  
 Mimo że sekwencji, w którym są przejście stron w strukturze hierarchicznej stałej jest określana w czasie wykonywania, środowisko użytkownika jest taka sama jak czynności użytkownika dla stałej topologii liniowej:  
  
-   Przejście ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ wywołujący strony można wywołać bezpośrednio pierwszej stronie kreatora. Przy użyciu strony uruchamiania, jednak może uprościć Kreatora inicjowania, zwłaszcza w wypadku inicjowania jest złożony.  
  
-   Użytkownicy mogą przechodzić między stronami przy użyciu Wstecz i do przodu przycisków (lub hiperłącza).  
  
-   Użytkownicy mogą przechodzić między stronami przy użyciu arkusza.  
  
-   Użytkownicy mogą zmieniać kolejności nawigacji, jeśli nawigowania wstecz dziennika.  
  
-   Użytkownicy mogą anulować pracę z kreatorem z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
-   Użytkownicy mogą akceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
-   Kreator zostało anulowane, Kreator zwraca wynik w odpowiednich i nie zwraca żadnych danych.  
  
-   Jeśli użytkownik akceptuje kreatora, Kreator zwraca wynik w odpowiednich i zwraca dane zebrane.  
  
-   Po ukończeniu pracy kreatora (akceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika. Dzięki temu każde wystąpienie Kreatora samodzielnie, zapobiegając potencjalnych danych lub nieprawidłowości stanu.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Nawigacji na dynamicznie generowanym topologii  
 W niektórych aplikacjach sekwencji, w którym są przejście dwóch lub więcej stron tylko można określić w czasie wykonywania przez użytkownika, aplikacji lub danych zewnętrznych. Na poniższym rysunku przedstawiono zestaw stron z sekwencją nieokreślonej nawigacji.  
  
 ![Diagram topologii nawigacji](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure4.png "NavigationTopologyFigure4")  
  
 Następny rysunek przedstawia sekwencji nawigacji, który został wybrany przez użytkownika w czasie wykonywania.  
  
 ![Diagram nawigacji](../../../../docs/framework/wpf/app-development/media/navigationtopologyfigure5.png "NavigationTopologyFigure5")  
  
 Sekwencja nawigacji jest określany jako dynamicznie generowanym topologii. Dla użytkownika jako w innych topologiach nawigacji środowisko użytkownika jest taki sam jak dla poprzedniego topologie jest:  
  
-   Przejście ze strony wywołania do strony uruchamiania, która inicjuje kreatora i przechodzi do pierwszej strony kreatora. Strona uruchamiania ( [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-mniej <xref:System.Windows.Navigation.PageFunction%601>) nie jest wymagana, ponieważ wywołujący strony można wywołać bezpośrednio pierwszej stronie kreatora. Przy użyciu strony uruchamiania, jednak może uprościć Kreatora inicjowania, zwłaszcza w wypadku inicjowania jest złożony.  
  
-   Użytkownicy mogą przechodzić między stronami przy użyciu Wstecz i do przodu przycisków (lub hiperłącza).  
  
-   Użytkownicy mogą przechodzić między stronami przy użyciu arkusza.  
  
-   Użytkownicy mogą anulować pracę z kreatorem z dowolnej strony kreatora, naciskając przycisk Anuluj.  
  
-   Użytkownicy mogą akceptować kreatora na ostatniej stronie kreatora, naciskając przycisk Zakończ.  
  
-   Kreator zostało anulowane, Kreator zwraca wynik w odpowiednich i nie zwraca żadnych danych.  
  
-   Jeśli użytkownik akceptuje kreatora, Kreator zwraca wynik w odpowiednich i zwraca dane zebrane.  
  
-   Po ukończeniu pracy kreatora (akceptowane lub anulowane), stron, które obejmuje kreatora są usuwane z dziennika. Dzięki temu każde wystąpienie Kreatora samodzielnie, zapobiegając potencjalnych danych lub nieprawidłowości stanu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Strukturyzowana nawigacja — omówienie](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)
