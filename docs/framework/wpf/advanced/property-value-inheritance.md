---
title: Przejęcie wartości właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: eb757d039437d9954a2b648c5f758dffa3fee3d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958359"
---
# <a name="property-value-inheritance"></a>Przejęcie wartości właściwości
Dziedziczenie wartości właściwości jest funkcją [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systemu właściwości. Dziedziczenie wartości właściwości umożliwia elementy potomne w drzewie elementów, aby uzyskać wartość określonej właściwości z elementów nadrzędnych, dziedziczących tę wartość, tak jak została ustawiona w dowolnym miejscu w najbliższym elemencie nadrzędnym. Element nadrzędny może również otrzymać jego wartość za pomocą dziedziczenia wartości właściwości, więc system może odnosił się cały sposób do katalogu głównego strony. Dziedziczenie wartości właściwości nie jest domyślnym zachowaniem systemu. Właściwość musi być ustanowiona z określonym ustawieniem metadanych, aby spowodować, że ta właściwość będzie inicjować dziedziczenie wartości właściwości w elementach podrzędnych.  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>Dziedziczenie wartości właściwości jest dziedziczeniem zawierania  
 "Dziedziczenie" jako termin nie jest zupełnie takie samo jak dziedziczenie w kontekście typów i ogólne programowanie zorientowane obiektowo, gdzie klasy pochodne dziedziczą definicje elementów członkowskich z ich klas podstawowych. To znaczenie dziedziczenia jest również aktywne w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: właściwości zdefiniowane w różnych klasach bazowych są udostępniane jako atrybuty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] klas pochodnych, gdy są używane jako elementy i udostępniane jako elementy członkowskie dla kodu. Dziedziczenie wartości właściwości jest szczególnie związane ze sposobem, w jaki wartości właściwości mogą dziedziczyć z jednego elementu do drugiego na podstawie relacji nadrzędny-podrzędny w drzewie elementów. To drzewo elementów jest najbardziej widoczne bezpośrednio podczas zagnieżdżania elementów wewnątrz innych elementów w miarę definiowania aplikacji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczniku. Drzewa obiektów mogą być również tworzone programowo przez dodanie obiektów do Wyznaczeni kolekcji innych obiektów, a dziedziczenie wartości właściwości działa w taki sam sposób w gotowym drzewie w czasie wykonywania.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Praktyczne zastosowania dziedziczenia wartości właściwości  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Interfejsy API zawierają kilka właściwości, dla których włączono dziedziczenie właściwości. Typowym scenariuszem jest to, że obejmują one właściwość, gdzie jest to odpowiednie, że właściwość jest ustawiana tylko raz na stronę, ale gdzie ta właściwość jest również elementem członkowskim jednej z klas elementu podstawowego i dlatego również istnieje w większości elementów podrzędnych. Na przykład <xref:System.Windows.FrameworkElement.FlowDirection%2A> Właściwość kontroluje, która kierunek przepływu zawartości powinna być wyświetlana i uporządkowana na stronie. Zazwyczaj pojęcie przepływu tekstu ma być obsługiwane spójnie we wszystkich elementach podrzędnych. Jeśli kierunek przepływu został z jakiegoś powodu resetowany na pewnym poziomie drzewa elementów przez akcję użytkownika lub środowiska, powinien on być zazwyczaj resetowany w programie. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Gdy właściwość jest wprowadzana do dziedziczenia, wartość musi być ustawiana lub resetowana tylko raz na poziomie w drzewie elementów, która obejmuje potrzeby prezentacji każdej strony w aplikacji. Nawet początkowa wartość domyślna będzie dziedziczyć w ten sposób. Model dziedziczenia wartości właściwości nadal umożliwia indywidualnym elementom resetowanie wartości dla rzadkich przypadków, w których zamierzone są różne kierunki przepływu.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Dziedziczenie właściwości niestandardowej  
 Zmieniając metadane właściwości niestandardowej, można także zapewnić dziedziczenie własnych właściwości niestandardowych. Należy jednak zauważyć, że wyznaczenie właściwości jako dziedziczenia ma pewne zagadnienia dotyczące wydajności. W przypadkach, gdy ta właściwość nie ma ustalonej wartości lokalnej ani wartości uzyskanej za pomocą stylów, szablonów lub powiązania danych, dziedziczona Właściwość zapewnia przypisane wartości właściwości do wszystkich elementów podrzędnych w drzewie logicznym.  
  
 Aby Właściwość brała udział w dziedziczeniu wartości, Utwórz niestandardową Właściwość dołączoną, zgodnie z opisem w temacie [Rejestrowanie dołączonej właściwości](how-to-register-an-attached-property.md). Zarejestruj właściwość z metadanymi (<xref:System.Windows.FrameworkPropertyMetadata>) i określ opcję "Inherits" w ustawieniach opcji w ramach tych metadanych. Upewnij się również, że właściwość ma ustaloną wartość domyślną, ponieważ ta wartość będzie teraz dziedziczyć. Mimo że zarejestrowano właściwość jako dołączoną, można również utworzyć właściwość "otoka" dla dostępu get/set w typie właściciela, tak jak dla właściwości zależności "niedołączone". Po wykonaniu tej czynności można ustawić właściwość dziedziczenia przy użyciu bezpośredniej otoki właściwości na typ właściciela lub typy pochodne lub można ją ustawić przy użyciu składni dołączonej właściwości na dowolnym <xref:System.Windows.DependencyObject>.  
  
 Dołączone właściwości są koncepcyjnie podobne do właściwości globalnych; Możesz sprawdzić, czy wartość <xref:System.Windows.DependencyObject> jest prawidłowa i uzyskać prawidłowy wynik. Typowym scenariuszem dla dołączonych właściwości jest ustawienie wartości właściwości w elementach podrzędnych i ten scenariusz jest bardziej efektywny, jeśli właściwość w pytaniu jest dołączoną właściwością, która jest zawsze niejawnie obecna jako dołączona właściwość dla każdego elementu (<xref:System.Windows.DependencyObject>) w drzewie.  
  
> [!NOTE]
> Chociaż dziedziczenie wartości właściwości może wydawać się niedołączone właściwości zależności, zachowanie dziedziczenia dla niedołączonej właściwości przy użyciu określonych granic elementów w drzewie wykonawczym jest niezdefiniowane. Zawsze używaj <xref:System.Windows.DependencyProperty.RegisterAttached%2A> do rejestrowania właściwości, które są <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> określone w metadanych.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Dziedziczenie wartości właściwości w granicach drzewa  
 Dziedziczenie właściwości działa przez przechodzenie drzewa elementów. To drzewo jest często równoległe do drzewa logicznego. Jednak po dołączeniu obiektu poziomu WPF w znaczniku, który definiuje drzewo elementu, takie jak <xref:System.Windows.Media.Brush>, utworzono nieciągłe Drzewo logiczne. Rzeczywiste Drzewo logiczne nie jest koncepcyjnie zwiększane za pomocą <xref:System.Windows.Media.Brush>, ponieważ Drzewo logiczne jest koncepcją na poziomie platformy WPF. Zobaczysz to odzwierciedlone w wynikach w przypadku korzystania z metod <xref:System.Windows.LogicalTreeHelper>. Jednak dziedziczenie wartości właściwości może być mostkiem tej przerwy w drzewie logicznym i nadal można przekazać dziedziczone wartości przez, tak długo, jak Właściwość dziedziczenia została zarejestrowana jako dołączona właściwość i nie ma celowo zablokowanego <xref:System.Windows.Controls.Frame>dziedziczenia.).  
  
## <a name="see-also"></a>Zobacz także

- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Przegląd właściwości dołączonych](attached-properties-overview.md)
- [Następstwo wartości właściwości zależności](dependency-property-value-precedence.md)
