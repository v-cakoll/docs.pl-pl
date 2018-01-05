---
title: "Przejęcie wartości właściwości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eac3e03cfc0ca8bbb6f61f1bc6663c67fd6303f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="property-value-inheritance"></a>Przejęcie wartości właściwości
Dziedziczenie wartość właściwości jest funkcją [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości systemu. Dziedziczenie wartości właściwości umożliwia elementy podrzędne w drzewie elementów, aby uzyskać wartość określonej właściwości z nadrzędnego elementom dziedziczenie tej wartości, ponieważ został ustawiony dowolne miejsce w najbliższym elemencie nadrzędnym. Element nadrzędny może również uzyskać wartość poprzez dziedziczenie wartości właściwości, więc system potencjalnie recurses aż do strony głównej. Dziedziczenie wartość właściwości nie jest domyślne zachowanie systemu właściwość; Właściwość należy ustanowić przy użyciu ustawienia określonego metadanych aby spowodować tej właściwości do zainicjowania dziedziczenie wartości właściwości w elementach podrzędnych.  
  

  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>Dziedziczenie wartość właściwości jest zawierania dziedziczenia  
 "Dziedziczenia" jako terminu w tym miejscu nie jest dość identyczne z koncepcją dziedziczenia w kontekście typów i ogólne zorientowane obiektowo programowania, w którym klas pochodnych dziedziczą definicji elementu członkowskiego z ich klasami podstawowymi. Dziedziczenie znaczenia również jest aktywny w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: właściwości zdefiniowane w różnych klas podstawowych są widoczne jako atrybuty dla pochodnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] klas, gdy używane jako elementy i udostępniany jako elementy członkowskie dla kodu. Dziedziczenie wartość właściwości jest szczególnie o jak wartości właściwości może dziedziczyć z jednego elementu na inny, na podstawie relacji nadrzędny podrzędny w obrębie drzewa elementów. Tree elementów jest najbardziej bezpośrednio widoczne podczas zagnieżdżania elementy wewnątrz innych elementów, jak zdefiniować aplikacje w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników. Drzewa obiektów można również tworzyć programowo przez dodawanie obiektów do wyznaczonych kolekcji innych obiektów, a wartość dziedziczenia działa tak samo w drzewie zakończono w czasie wykonywania.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>Zastosowania praktyczne dziedziczenia wartość właściwości  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] Obejmują kilka właściwości, które mają włączone dziedziczenie właściwości. Zazwyczaj scenariusz tych jest wymagają one właściwości, gdzie jest odpowiednie, że dla właściwości można ustawić tylko raz na każdej stronie, ale w przypadku tej właściwości jest również członkiem jednej z klas base element i w związku z tym będzie istnieć na większości elementów podrzędnych. Na przykład <xref:System.Windows.FrameworkElement.FlowDirection%2A> kierunek, w którym przepływ zawartość formantów właściwości powinny być prezentowane i rozmieszczone na stronie. Zwykle ma koncepcji przepływu tekstu do obsługi spójne w całym wszystkie elementy podrzędne. Gdyby kierunek przepływu jakiegoś powodu Resetowanie w pewnego poziomu drzewa elementu przez użytkownika lub środowiska akcji, zazwyczaj należy zresetować w całej. Gdy <xref:System.Windows.FrameworkElement.FlowDirection%2A> dotyczące dziedziczą właściwości, wartość tylko należy ustawić lub zresetować raz na poziomie drzewa element, który obejmuje potrzeby prezentacji dla każdej strony w aplikacji. Nawet wartością domyślną początkowej będzie dziedziczyć w ten sposób. Model dziedziczenia wartość właściwości umożliwia nadal poszczególne elementy zresetować wartość w rzadkich przypadkach, gdzie kombinacji kierunki przepływu jest zamierzone.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>Tworzenie niestandardowych właściwości dziedziczonych  
 Zmieniając metadanych właściwości niestandardowej, można również ustawić własne niestandardowe właściwości dziedziczonych. Należy jednak pamiętać, wyznaczenie właściwości dziedziczonych jako że pewne zagadnienia dotyczące wydajności. W przypadkach, w których tej właściwości nie ma ustalonych wartości lokalnej lub wartość uzyskiwaną style, szablonów i powiązania danych właściwości dziedziczonych zapewnia jej wartości właściwości przypisane do wszystkich elementów podrzędnych w drzewie logicznym.  
  
 Do tworzenia właściwości uczestniczyć w dziedziczeniu wartości, należy utworzyć niestandardowego dołączona właściwość, zgodnie z opisem w [zarejestrować dołączonych właściwości](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md). Zarejestruj właściwości metadanych (<xref:System.Windows.FrameworkPropertyMetadata>) i określ opcję "Inherits" w ustawieniach Opcje w ramach tych metadanych. Upewnij się również czy właściwość ma wartość domyślna nawiązane, ponieważ teraz odziedziczą tę wartość. Mimo że właściwość jest zarejestrowany, jak dołączyć, może również chcesz utworzyć właściwości "otoki" dla dostępu pobierania/ustawiania na typ właściciela tak samo, jak dla właściwości zależności "nie dołączony". Po wykonaniu tej czynności, właściwość dziedziczona albo można ustawić przy użyciu otoki właściwość direct na typ właściciela lub typy pochodne lub można ją ustawić za pomocą składni właściwości dołączonych na dowolnym <xref:System.Windows.DependencyObject>.  
  
 Dołączone właściwości jest podobny do globalnych właściwości; Możesz sprawdzić wartość na dowolnym <xref:System.Windows.DependencyObject> i uzyskać prawidłowy wynik. Typowy scenariusz w przypadku dołączonych właściwości jest można ustawić wartości właściwości dla elementów podrzędnych, a w tym scenariuszu jest bardziej skuteczne, jeśli właściwość zagrożona jest dołączona właściwość, która jest zawsze domyślnie dostępne jako dołączona właściwość na każdym elemencie (<xref:System.Windows.DependencyObject>) w drzewie.  
  
> [!NOTE]
>  Chociaż dziedziczenie wartości właściwości mogą być wyświetlane dla właściwości zależności nie dołączony, zachowanie dziedziczenia właściwości nie dołączony do określonych granic elementu w drzewie w czasie wykonywania jest niezdefiniowana. Zawsze używaj <xref:System.Windows.DependencyProperty.RegisterAttached%2A> można zarejestrować właściwości, w którym można określić <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> w metadanych.  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>Dziedziczenie właściwości między granicami drzewa  
 Dziedziczenie właściwości polega na przechodzenie drzewa elementów. Tego drzewa często jest zbliżony do drzewa logicznego. Jednak po każdej zmianie zawiera obiektem poziomu core WPF kod znaczników, który definiuje element drzewa, takich jak <xref:System.Windows.Media.Brush>, utworzono nieciągłego drzewa logicznego. Wartość true, drzewa logicznego nie rozszerza koncepcyjnie za pośrednictwem <xref:System.Windows.Media.Brush>, ponieważ drzewa logicznego to pojęcie poziomie struktury WPF. Widać to odzwierciedlone w wynikach, korzystając z metody <xref:System.Windows.LogicalTreeHelper>. Jednak dziedziczenie wartość właściwości może mostkować luki w drzewie logicznym, można nadal dziedziczonej wartości przekazywane za pośrednictwem, tak długo, jak właściwości dziedziczonych została zarejestrowana jako dołączona właściwość i nie zamierzonego granic blokowanie dziedziczenia (takie jak <xref:System.Windows.Controls.Frame>) napotkano.  
  
## <a name="see-also"></a>Zobacz też  
 [Metadane zależności właściwości](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Przegląd właściwości dołączonych](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [Następstwo wartości właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)
