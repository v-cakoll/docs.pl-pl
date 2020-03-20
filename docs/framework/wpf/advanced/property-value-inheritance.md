---
title: Przejęcie wartości właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: b63f307d9edffd14315d383d8e06419fa141aee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187195"
---
# <a name="property-value-inheritance"></a>Przejęcie wartości właściwości
Dziedziczenie wartości właściwości jest [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcją systemu właściwości. Dziedziczenie wartości właściwości umożliwia elementy podrzędne w drzewie elementów, aby uzyskać wartość określonej właściwości z elementów nadrzędnych, dziedzicząc tę wartość, jak została ustawiona w dowolnym miejscu w najbliższym elemencie nadrzędnym. Element nadrzędny może również uzyskać jego wartość poprzez dziedziczenie wartości właściwości, więc system potencjalnie powtarza się aż do katalogu głównego strony. Dziedziczenie wartości właściwości nie jest domyślnym zachowaniem systemu właściwości; właściwość musi zostać ustanowiona z ustawieniem określonych metadanych, aby spowodować, że właściwość inicjuje dziedziczenie wartości właściwości na elementach podrzędnych.  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>
## <a name="property-value-inheritance-is-containment-inheritance"></a>Dziedziczenie wartości właściwości jest dziedziczeniem hermetyzacji  
 "Dziedziczenie" jako termin w tym miejscu nie jest zupełnie taka sama koncepcja jak dziedziczenie w kontekście typów i programowania ogólnego obiektowego, gdzie pochodne klasy dziedziczą definicje elementów członkowskich z ich klas podstawowych. To znaczenie dziedziczenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]jest również aktywne w : właściwości zdefiniowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w różnych klasach podstawowych są widoczne jako atrybuty dla klas pochodnych, gdy są używane jako elementy i są udostępniane jako elementy członkowskie dla kodu. Dziedziczenie wartości właściwości jest szczególnie o tym, jak wartości właściwości można dziedziczyć z jednego elementu do drugiego na podstawie relacji nadrzędny podrzędny w drzewie elementów. To drzewo elementów jest najbardziej bezpośrednio widoczne podczas zagnieżdżania elementów wewnątrz innych elementów podczas definiowania aplikacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znacznikach. Drzewa obiektów można również tworzyć programowo, dodając obiekty do wyznaczonych kolekcji innych obiektów, a dziedziczenie wartości właściwości działa w ten sam sposób w gotowym drzewie w czasie wykonywania.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>
## <a name="practical-applications-of-property-value-inheritance"></a>Praktyczne zastosowania dziedziczenia wartości majątku  
 Interfejsy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API zawierają kilka właściwości, które mają włączone dziedziczenie właściwości. Zazwyczaj scenariusz dla nich jest, że obejmują one właściwości, gdzie jest właściwe, że właściwość można ustawić tylko raz na stronie, ale gdzie ta właściwość jest również członkiem jednej z klas podstawowych elementów i w związku z tym również istnieje na większości elementów podrzędnych. Na przykład <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość określa, w którym kierunku przepływa zawartość powinna być przedstawiona i ułożona na stronie. Zazwyczaj chcesz, aby koncepcja przepływu tekstu była obsługiwana spójnie we wszystkich elementach podrzędnych. Jeśli kierunek przepływu były z jakiegoś powodu zresetować w pewnym poziomie drzewa elementów przez użytkownika lub działania środowiska, zazwyczaj należy zresetować w całym. Gdy <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość jest do dziedziczenia, wartość musi być ustawiona lub zresetowana tylko raz na poziomie w drzewie elementów, który obejmuje potrzeby prezentacji każdej strony w aplikacji. Nawet początkowa wartość domyślna odziedziczy w ten sposób. Model dziedziczenia wartości właściwości nadal umożliwia poszczególnych elementów, aby zresetować wartość dla rzadkich przypadkach, gdy o kombinacji kierunków przepływu jest zamierzone.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>
## <a name="making-a-custom-property-inheritable"></a>Dziedziczenie właściwości niestandardowej  
 Zmieniając metadane właściwości niestandardowej, można również tworzyć własne właściwości niestandardowe dziedziczne. Należy jednak zauważyć, że wyznaczanie właściwości jako dziedziczne ma pewne zagadnienia dotyczące wydajności. W przypadkach, gdy ta właściwość nie ma ustalonej wartości lokalnej lub wartości uzyskanej za pomocą stylów, szablonów lub powiązania danych, dziedziczna właściwość udostępnia przypisane wartości właściwości do wszystkich elementów podrzędnych w drzewie logicznym.  
  
 Aby właściwość uczestniczyła w dziedziczeniu wartości, utwórz niestandardową dołączoną właściwość, zgodnie z opisem w [polu Zarejestruj dołączoną właściwość](how-to-register-an-attached-property.md). Zarejestruj właściwość z<xref:System.Windows.FrameworkPropertyMetadata>metadanymi ( ) i określ opcję "Dziedziczy" w ustawieniach opcji w ramach tych metadanych. Upewnij się również, że właściwość ma ustaloną wartość domyślną, ponieważ ta wartość będzie teraz dziedziczyć. Mimo że właściwość została zarejestrowana jako dołączona, można również utworzyć "otokę" właściwości dla dostępu get/set dla typu właściciela, tak jak w przypadku właściwości zależności "bez związku". Po wykonaniu tej funkcji można ustawić przy użyciu otoki właściwości bezpośredniej typu właściciela lub typów pochodnych lub można ją ustawić przy <xref:System.Windows.DependencyObject>użyciu dołączonej składni właściwości w dowolnym pliku .  
  
 Dołączone właściwości są koncepcyjnie podobne do właściwości globalnych; można sprawdzić wartość na <xref:System.Windows.DependencyObject> dowolnym i uzyskać prawidłowy wynik. Typowy scenariusz dla dołączonych właściwości jest ustawienie wartości właściwości na elementy podrzędne, a ten scenariusz jest bardziej skuteczne, jeśli właściwość, o<xref:System.Windows.DependencyObject>których mowa jest dołączone właściwość, która jest zawsze niejawnie obecny jako dołączone właściwości na każdy element ( ) w drzewie.  
  
> [!NOTE]
> Chociaż dziedziczenie wartości właściwości może wydawać się działać dla właściwości zależności bez konieczności, zachowanie dziedziczenia dla właściwości niezwiązanych z niektórymi elementami w drzewie czasu wykonywania jest niezdefiniowane. Zawsze <xref:System.Windows.DependencyProperty.RegisterAttached%2A> służy do rejestrowania <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> właściwości, gdzie można określić w metadanych.  
  
<a name="InheritanceContext"></a>
## <a name="inheriting-property-values-across-tree-boundaries"></a>Dziedziczenie wartości właściwości przez granice drzewa  
 Dziedziczenie właściwości działa przez przechodzenie przez drzewo elementów. To drzewo jest często równoległe do drzewa logicznego. Jednak za każdym razem, gdy w znacznikach znajduje się obiekt na poziomie rdzenia WPF, który definiuje drzewo elementów, takie jak <xref:System.Windows.Media.Brush>, utworzono nieciągłe drzewo logiczne. Prawdziwe drzewo logiczne nie koncepcyjnie rozciąga się za pośrednictwem <xref:System.Windows.Media.Brush>, ponieważ drzewo logiczne jest pojęciem na poziomie struktury WPF. Widać to odzwierciedlenie w wynikach podczas <xref:System.Windows.LogicalTreeHelper>korzystania z metod . Jednak dziedziczenie wartości właściwości może wypełnić tę lukę w drzewie logicznym <xref:System.Windows.Controls.Frame>i nadal może przekazywać dziedziczone wartości, o ile dziedziczna właściwość została zarejestrowana jako przyłączona właściwość i nie zostanie napotkana celowa granica blokowania dziedziczenia (np.  
  
## <a name="see-also"></a>Zobacz też

- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Przegląd właściwości dołączonych](attached-properties-overview.md)
- [Następstwo zależności wartości właściwości](dependency-property-value-precedence.md)
