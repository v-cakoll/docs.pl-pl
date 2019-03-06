---
title: Przejęcie wartości właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: 64cafbe2f6044c83600ef227608dee24b29e3943
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359887"
---
# <a name="property-value-inheritance"></a>Przejęcie wartości właściwości
Dziedziczenie wartości właściwości jest funkcją [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości systemu. Dziedziczenie wartości właściwości umożliwia elementy podrzędne w drzewie elementów, aby uzyskać wartość określonej właściwości z obiektu nadrzędnego elementom dziedziczenie tę wartość, jak go w dowolnym miejscu została ustawiona w najbliższym elemencie nadrzędnym. Element nadrzędny może także uzyskać wartość poprzez dziedziczenie wartości właściwości, więc system potencjalnie recurses aż do głównej strony. Dziedziczenie wartości właściwości nie jest to domyślne zachowanie systemu właściwości; Właściwość, należy ustanowić z ustawieniem określonego metadanych aby spowodować, że tę właściwość można zainicjować dziedziczenie wartości właściwości dla elementów podrzędnych.  
  

  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>Dziedziczenie wartości właściwości jest dziedziczenie zawierania  
 "Dziedziczenie" jako termin w tym miejscu nie jest dość identyczne z koncepcją dziedziczenia w kontekście typów i ogólne obiektowy programowania, w którym klasy pochodne dziedziczą definicje elementów członkowskich z ich klasami podstawowymi. Znaczenie dziedziczenia również jest aktywny w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: właściwości zdefiniowane w różnych klas bazowych są widoczne jako atrybuty dla pochodne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] klasy używane jako elementy, gdy dostępne jako elementy członkowskie dla kodu. Dziedziczenie wartości właściwości jest szczególnie o jak wartości właściwości może dziedziczyć z jednego elementu do innej na podstawie relacji nadrzędny podrzędny w drzewie elementów. Tego drzewa elementów jest najbardziej bezpośrednio widoczne podczas zagnieżdżania elementy wewnątrz innych elementów, jak zdefiniować aplikacje w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników. Drzewa obiektów można również utworzyć programowo przez dodawanie obiektów do wyznaczonej kolekcji innych obiektów, a dziedziczenie wartości właściwości działa tak samo w drzewie zakończone w czasie wykonywania.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Praktyczne zastosowania dziedziczenie wartości właściwości  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Zawierają kilka właściwości, które mają dziedziczenia właściwości włączone. Zazwyczaj scenariusz dla tych jest wymagają one właściwości w których jest właściwe, właściwość można ustawić tylko raz na każdej stronie, ale w przypadku tej właściwości jest również członkiem jednej z klas elementu podstawowego i dlatego będzie dostępne są także na większości elementów podrzędnych. Na przykład <xref:System.Windows.FrameworkElement.FlowDirection%2A> formantów właściwości kierunek, w którym przepływ zawartości powinien być prezentowane i rozmieszczone na stronie. Zazwyczaj chcesz koncepcji przepływu tekstu do obsłużenia spójnie w całej wszystkie elementy podrzędne. Kierunek przepływu były jakiegoś powodu Resetowanie w pewien poziom drzewa elementów przez użytkownika lub akcji środowiska, zazwyczaj należy resetować w całym. Gdy <xref:System.Windows.FrameworkElement.FlowDirection%2A> dziedziczą właściwości zostanie podjęta, tylko wartość muszą być Ustaw lub Wyzeruj raz, na poziomie drzewa elementu, który obejmuje na potrzeby prezentacji każdej strony w aplikacji. Nawet wartość początkową domyślną będzie dziedziczyć w ten sposób. Model dziedziczenia wartość właściwości nadal umożliwia poszczególne elementy zresetować wartość rzadkich przypadkach, gdy o różnych kierunki przepływu jest zamierzone.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Tworzenie niestandardowe właściwości dziedziczonych  
 Zmieniając właściwości niestandardowych metadanych, można również ustawić niestandardowe właściwości dziedziczonych. Należy jednak pamiętać, że wyznaczanie właściwość jako dziedziczne mają pewne zagadnienia związane z wydajnością. W przypadkach, w którym tej właściwości nie ma ustalonych wartości lokalnej lub wartości uzyskanej za pomocą stylów, szablonów i powiązania danych właściwości dziedziczonych udostępnia wartości właściwości przypisane do wszystkich elementów podrzędnych w drzewie logicznym.  
  
 Do tworzenia właściwości uczestniczą w dziedziczeniu wartości, Utwórz niestandardową dołączona właściwość, zgodnie z opisem w [rejestrowanie dołączonych właściwości](how-to-register-an-attached-property.md). Zarejestrowanie właściwości metadanych (<xref:System.Windows.FrameworkPropertyMetadata>) i wybierz opcję "Inherits" w ustawieniach Opcje w ramach tych metadanych. Również upewnij się, że właściwość ma wartość domyślną ustanowionych ponieważ teraz odziedziczą tę wartość. Mimo, że właściwość jest zarejestrowany, jak dołączone, również można utworzyć właściwości "opakowanie" dla dostępu pobierania/ustawiania na typ właściciela tak samo jak dla właściwości zależności "nie dołączony". Po wykonaniu tej czynności, można ustawić albo właściwości dziedziczonych przy użyciu otoki właściwość direct na typ właściciela lub typy pochodne lub ustawić przy użyciu składni dołączonej właściwości na dowolnym <xref:System.Windows.DependencyObject>.  
  
 Zachowuje się podobnie jak właściwości globalne; są dołączone właściwości Możesz sprawdzić wartość na dowolnym <xref:System.Windows.DependencyObject> i uzyskać prawidłowy wynik. Typowy scenariusz w przypadku dołączonych właściwości jest do ustawiania wartości właściwości dla elementów podrzędnych, a ten scenariusz jest bardziej skuteczne, jeśli w danym właściwość jest dołączona właściwość, która występuje zawsze niejawnie jako dołączoną właściwość dla każdego elementu (<xref:System.Windows.DependencyObject>) w drzewie.  
  
> [!NOTE]
>  Mimo że dziedziczenie wartości właściwości może pojawić się działać w przypadku właściwości zależności nie dołączony, zachowanie dziedziczenia właściwości nie dołączony do określonych granic elementu w drzewie w czasie wykonywania jest niezdefiniowane. Zawsze używaj <xref:System.Windows.DependencyProperty.RegisterAttached%2A> można zarejestrować właściwości, w którym można określić <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> w metadanych.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Dziedziczenie wartości właściwości w granicach drzewa  
 Dziedziczenie właściwości polega na przechodzić przez drzewo elementów. To drzewo stanowi często zbliżony do drzewa logicznego. Jednak zawsze, gdy dołączysz obiektem poziomu core WPF w znaczniku, który definiuje obrębu drzewa, takie jak <xref:System.Windows.Media.Brush>, utworzono nieciągły drzewo logiczne. Wartość true drzewo logiczne nie obejmuje koncepcyjnie za pośrednictwem <xref:System.Windows.Media.Brush>, ponieważ drzewo logiczne jest pojęciem poziomie struktury WPF. Widać to odzwierciedlone w wynikach, korzystając z metody <xref:System.Windows.LogicalTreeHelper>. Jednak dziedziczenie wartości właściwości można wypełnić tę lukę w drzewie logicznym i nadal można przekazać wartości odziedziczone przez, tak długo, jak właściwości dziedziczonych został zarejestrowany jako dołączoną właściwość i nie zamierzonego granic blokowanie dziedziczenia (takie jak <xref:System.Windows.Controls.Frame>) zostanie osiągnięty.  
  
## <a name="see-also"></a>Zobacz także
- [Metadane zależności właściwości](dependency-property-metadata.md)
- [Przegląd właściwości dołączonych](attached-properties-overview.md)
- [Następstwo wartości właściwości zależności](dependency-property-value-precedence.md)
