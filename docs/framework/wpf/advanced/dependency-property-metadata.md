---
title: Metadane zależności właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 800bf80e5ba3e697c122bcf4b1bc0f302357d087
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401628"
---
# <a name="dependency-property-metadata"></a>Metadane zależności właściwości
System [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości zawiera system raportowania metadanych, który wykracza poza to, co może być raportowane przez właściwość za pomocą odbicia lub ogólnych charakterystyk środowiska uruchomieniowego języka wspólnego (CLR). Metadane dla właściwości zależności można również przypisać jednoznacznie przez klasę, która definiuje właściwość zależności, można zmienić, gdy właściwość zależności jest dodawana do innej klasy i może być przesłonięta przez wszystkie klasy pochodne, które dziedziczą Właściwość zależności od definicji klasy podstawowej.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że właściwości zależności są rozpoznawane w perspektywie odbiorcy istniejących [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości zależności w klasach i odczytywane są [Przegląd właściwości zależności](dependency-properties-overview.md). Aby postępować zgodnie z przykładami w tym temacie, należy również zrozumieć [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i wiedzieć, jak pisać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje.  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>Jak są używane metadane właściwości zależności  
 Metadane właściwości zależności istnieją jako obiekt, do którego można zbadać właściwości zależności. Te metadane są również często dostępne przez system właściwości podczas przetwarzania danej właściwości zależności. Obiekt metadanych dla właściwości zależności może zawierać następujące typy informacji:  
  
- Wartość domyślna właściwości zależności, jeśli nie można określić żadnej innej wartości dla właściwości zależności przez wartość lokalną, styl, dziedziczenie itp. Szczegółowe omówienie sposobu, w jaki wartości domyślne uczestniczą w pierwszeństwie używanym przez system właściwości podczas przypisywania wartości właściwości zależności, można znaleźć w temacie [pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).  
  
- Odwołania do implementacji wywołania zwrotnego, które wpływają na działanie przymusu lub zmiany powiadomienia dla typu dla właściciela. Należy zauważyć, że te wywołania zwrotne są często zdefiniowane z niepublicznym poziomem dostępu, więc uzyskanie faktycznych odwołań z metadanych jest ogólnie niemożliwe, chyba że odwołania znajdują się w dozwolonym zakresie dostępu. Aby uzyskać więcej informacji na temat wywołania zwrotnego właściwości zależności, zobacz [wywołania zwrotne właściwości zależności i walidacja](dependency-property-callbacks-and-validation.md).  
  
- Jeśli właściwość zależności jest uznawana za właściwość na poziomie platformy WPF, metadane mogą zawierać charakterystykę właściwości zależności poziomu platformy WPF, która raportuje informacje i stan usług, takich jak platforma WPF Framework-Level mechanizm układu i logika dziedziczenia właściwości. Aby uzyskać więcej informacji na temat tego aspektu metadanych właściwości zależności, zobacz [metadane właściwości platformy](framework-property-metadata.md).  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>Interfejsy API metadanych  
 Typ, który raportuje większość informacji metadanych używanych przez system właściwości, jest <xref:System.Windows.PropertyMetadata> klasą. Wystąpienia metadanych są opcjonalnie określane, gdy właściwości zależności są zarejestrowane w systemie właściwości i można je określić ponownie dla dodatkowych typów, które dodają siebie jako właściciele lub przesłaniają metadane, które dziedziczą z zależności klasy podstawowej Definicja właściwości. (W przypadku, gdy rejestracja właściwości nie określa metadanych, <xref:System.Windows.PropertyMetadata> zostanie utworzona wartość domyślna z wartościami domyślnymi dla tej klasy). Zarejestrowane metadane są zwracane <xref:System.Windows.PropertyMetadata> po wywołaniu różnych <xref:System.Windows.DependencyProperty.GetMetadata%2A> przeciążeń, które pobierają metadane z właściwości zależności w <xref:System.Windows.DependencyObject> wystąpieniu.  
  
 Następnie <xref:System.Windows.PropertyMetadata> Klasa pochodzi od, aby zapewnić bardziej szczegółowe metadane dla przegród architektury, takich jak klasy na poziomie WPF Framework. <xref:System.Windows.UIPropertyMetadata>dodaje raportowanie animacji i <xref:System.Windows.FrameworkPropertyMetadata> udostępnia właściwości na poziomie platformy WPF wymienione w poprzedniej sekcji. Po zarejestrowaniu właściwości zależności można je zarejestrować w tych <xref:System.Windows.PropertyMetadata> klasach pochodnych. Po zbadaniu metadanych typ podstawowy <xref:System.Windows.PropertyMetadata> może być potencjalnie rzutowany na klasy pochodne, aby można było sprawdzić bardziej szczegółowe właściwości.  
  
> [!NOTE]
>  Cechy właściwości, które można określić w programie <xref:System.Windows.FrameworkPropertyMetadata> , są czasami określane jako "flags" w tej dokumentacji. Podczas tworzenia nowych wystąpień metadanych do użycia w rejestracjach właściwości zależności lub zastąpień metadanych należy określić te wartości przy użyciu wyliczenia <xref:System.Windows.FrameworkPropertyMetadataOptions> flagwise, a następnie podać możliwe połączone wartości wyliczenia do <xref:System.Windows.FrameworkPropertyMetadata> Konstruktor. Jednak po skonstruowaniu te właściwości opcji są ujawniane w ramach <xref:System.Windows.FrameworkPropertyMetadata> jako seria właściwości logicznych, a nie od konstruowania wartości wyliczenia. Właściwości logiczne umożliwiają sprawdzanie każdego warunku, a nie wymaganie zastosowania maski do wartości wyliczenia flagwise w celu uzyskania interesujących Cię informacji. Konstruktor używa połączonej <xref:System.Windows.FrameworkPropertyMetadataOptions> wartości, aby zachować rozsądną długość podpisu konstruktora, natomiast rzeczywiste skonstruowane metadane uwidaczniają dyskretne właściwości, aby wykonywać zapytania o metadane bardziej intuicyjne.  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Kiedy należy przesłonić metadane, kiedy należy utworzyć klasę  
 System [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości ma ustalone możliwości zmiany niektórych właściwości zależności bez konieczności ich całkowitego zaimplementowania. W tym celu należy utworzyć inne wystąpienie metadanych właściwości dla właściwości zależności, która istnieje w określonym typie. Należy zauważyć, że większość istniejących właściwości zależności nie są właściwościami wirtualnymi, więc dokładnie mówiąc "ponowne implementowanie" przy użyciu dziedziczonych klas może zostać wykonane tylko przez zapełnienie istniejącego elementu członkowskiego.  
  
 Jeśli scenariusz, który próbujesz włączyć dla właściwości zależności typu, nie może zostać osiągnięty poprzez modyfikację cech istniejących właściwości zależności, może to być konieczne do utworzenia klasy pochodnej, a następnie zadeklarować niestandardową właściwość zależności w klasie pochodnej. Niestandardowa właściwość zależności zachowuje się identycznie z właściwościami zależności zdefiniowanymi przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsy API. Aby uzyskać więcej informacji na temat niestandardowych właściwości zależności, zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md).  
  
 Jedną z istotnych cech właściwości zależności, której nie można przesłonić, jest jej typ wartości. Jeśli dziedziczysz właściwość zależności, która ma przybliżone zachowanie, które jest wymagane, ale potrzebujesz innego typu dla niego, musisz zaimplementować niestandardową właściwość zależności i ewentualnie połączyć właściwości przy użyciu konwersji typów lub innych Implementacja klasy niestandardowej. Ponadto nie można zastąpić istniejącej <xref:System.Windows.ValidateValueCallback>, ponieważ to wywołanie zwrotne istnieje w samym polu rejestracji, a nie w jego metadanych.  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>Scenariusze zmieniania istniejących metadanych  
 Jeśli pracujesz z metadanymi istniejącej właściwości zależności, jeden typowy scenariusz zmiany metadanych właściwości zależności ma na celu zmianę wartości domyślnej. Zmiana lub dodanie wywołań zwrotnych systemu właściwości jest bardziej zaawansowanym scenariuszem. Można to zrobić, jeśli implementacja klasy pochodnej ma różne relacje między właściwościami zależności. Jednym z tych zdarzeń jest model programowania obsługujący zarówno kod, jak i użycie deklaracyjne, ponieważ właściwości muszą być ustawione w dowolnej kolejności. W związku z tym wszystkie właściwości zależne muszą być ustawione na wartość just-in-Time bez kontekstu i nie mogą polegać na Poznaniu kolejności ustawień, takich jak można znaleźć w konstruktorze. Aby uzyskać więcej informacji na temat tego aspektu systemu właściwości, zobacz [wywołania zwrotne właściwości zależności i walidacja](dependency-property-callbacks-and-validation.md). Należy zauważyć, że wywołania zwrotne walidacji nie są częścią metadanych; są one częścią identyfikatora właściwości zależności. W związku z tym nie można zmienić walidacji wywołania zwrotnego przez zastąpienie metadanych.  
  
 W niektórych przypadkach może być również konieczne zmodyfikowanie opcji metadanych właściwości na poziomie platformy WPF we właściwościach istniejących zależności. Te opcje komunikują się z określonymi znanymi warunkami dotyczącymi właściwości na poziomie platformy WPF z innymi procesami na poziomie platformy WPF, takimi jak system układu.  Ustawienie opcji jest zazwyczaj wykonywane tylko podczas rejestrowania nowej właściwości zależności, ale istnieje również możliwość zmiany metadanych właściwości na poziomie platformy WPF w <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> ramach wywołania lub. <xref:System.Windows.DependencyProperty.AddOwner%2A> Aby uzyskać informacje o określonych wartościach i więcej informacji, zobacz [Framework właściwości metadanych](framework-property-metadata.md). Aby uzyskać więcej informacji dotyczących sposobu ustawiania tych opcji dla nowo zarejestrowanej właściwości zależności, zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md).  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>Zastępowanie metadanych  
 Celem przesłaniania metadanych jest przede wszystkim, że istnieje możliwość zmiany różnych zachowań pochodnych metadanych, które są stosowane do właściwości zależności, która istnieje w danym typie. Przyczyny tego są wyjaśnione bardziej szczegółowo w sekcji [metadanych](#dp_metadata_contents) . Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz [przesłanianie metadanych dla właściwości zależności](how-to-override-metadata-for-a-dependency-property.md).  
  
 Metadane właściwości można podać dla właściwości zależności podczas wywołania rejestracji (<xref:System.Windows.DependencyProperty.Register%2A>). Jednak w wielu przypadkach może być konieczne dostarczenie metadanych specyficznych dla typu dla klasy, gdy dziedziczy ona tę właściwość zależności. Można to zrobić, wywołując <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metodę.  Na przykład z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsów API <xref:System.Windows.FrameworkElement> Klasa jest <xref:System.Windows.UIElement.Focusable%2A> typem, który najpierw rejestruje właściwość zależności. Ale Klasa przesłania metadane dla właściwości zależności, aby zapewnić własną początkową wartość domyślną, zmieniając ją z `false` na `true`i w przeciwnym razie ponownie używa oryginalnej <xref:System.Windows.UIElement.Focusable%2A> implementacji. <xref:System.Windows.Controls.Control>  
  
 Podczas zastępowania metadanych różne charakterystyki metadanych są scalone lub zastępowane.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>jest scalony. Jeśli dodasz nowe <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, to wywołanie zwrotne zostanie zapisane w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w przesłonięciu, <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> wartość jest podwyższana jako odwołanie z najbliższego elementu nadrzędnego, który określono w metadanych.  
  
- Rzeczywiste zachowanie systemu właściwości dla <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> to, że implementacje dla wszystkich właścicieli metadanych w hierarchii są zachowywane i dodawane do tabeli, z kolejnością wykonywania przez system właściwości, że wywołania zwrotne najbardziej pochodnej klasy są wywoływane jako pierwsze.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>jest zastępowany. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.DefaultValue%2A> w przesłonięciu, <xref:System.Windows.PropertyMetadata.DefaultValue%2A> wartość pochodzi z najbliższego elementu nadrzędnego, który został określony w metadanych.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementacje zostały zastąpione. Jeśli dodasz nowe <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, to wywołanie zwrotne zostanie zapisane w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w przesłonięciu, <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> wartość jest podwyższana jako odwołanie z najbliższego elementu nadrzędnego, który określono w metadanych.  
  
- Zachowanie systemu właściwości polega na tym, że <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> tylko w metadanych bezpośrednich jest wywoływana. Żadne odwołania do innych <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementacji w hierarchii nie są zachowywane.  
  
 To zachowanie jest implementowane <xref:System.Windows.PropertyMetadata.Merge%2A>przez program i można je zastąpić w pochodnych klasach metadanych.  
  
#### <a name="overriding-attached-property-metadata"></a>Zastępowanie metadanych dołączonej właściwości  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]programie dołączone właściwości są implementowane jako właściwości zależności. Oznacza to, że mają także metadane właściwości, które poszczególne klasy mogą przesłonić. Zagadnienia dotyczące określania dołączonej właściwości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programie mają zwykle <xref:System.Windows.DependencyObject> ustawioną właściwość dołączoną. W związku z <xref:System.Windows.DependencyObject> tym każda klasa pochodna może zastąpić metadane dla każdej dołączonej właściwości, ponieważ może być ustawiona w wystąpieniu klasy. Można przesłonić wartości domyślne, wywołania zwrotne lub właściwości raportowania charakterystyki poziomu platformy WPF. Jeśli dołączona właściwość jest ustawiona w wystąpieniu klasy, stosowane są te charakterystyki metadanych właściwości zastępujące. Na przykład można przesłonić wartość domyślną, w taki sposób, aby wartość zastąpienia była raportowana jako wartość właściwości dołączonej w wystąpieniach klasy, za każdym razem, gdy właściwość nie jest ustawiona w inny sposób.  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> Właściwość nie jest istotna dla dołączonych właściwości.  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Dodawanie klasy jako właściciela istniejącej właściwości zależności  
 Klasa może dodać siebie jako właściciela właściwości zależności, która została już zarejestrowana przy użyciu <xref:System.Windows.DependencyProperty.AddOwner%2A> metody. Dzięki temu Klasa może używać właściwości zależności, która została pierwotnie zarejestrowana dla innego typu. Dodanie klasy zazwyczaj nie jest klasą pochodną typu, który najpierw zarejestrował właściwość dependency jako Owner. Efektywnie dzięki temu Klasa i jej klasy pochodne do "dziedziczą" implementację właściwości zależności bez oryginalnej klasy Owner i dodawanej klasy są w tej samej rzeczywistej hierarchii klas. Dodatkowo, Dodawanie klasy (i wszystkie klasy pochodne również) może zapewnić metadane specyficzne dla typu dla właściwości oryginalnej zależności.  
  
 Jak również dodać siebie jako właściciela poprzez metody narzędziowe systemu właściwości, Dodaj klasę należy zadeklarować dodatkowe publiczne elementy członkowskie na siebie w celu udostępnienia właściwości zależności] pełny uczestnik systemu właściwości z narażeniem na kod i adiustację . Klasa, która dodaje istniejącą właściwość zależności, ma takie same obowiązki, jak w przypadku uwidaczniania modelu obiektów dla tej właściwości zależności, jako Klasa, która definiuje nową właściwość zależności niestandardowej. Pierwszy taki członek do ujawnienia jest polem identyfikatora właściwości zależności. To pole powinno być `public static readonly` polem typu <xref:System.Windows.DependencyProperty>, które jest przypisane do zwracanej wartości <xref:System.Windows.DependencyProperty.AddOwner%2A> wywołania. Drugi element członkowski do zdefiniowania to właściwość otoka środowiska uruchomieniowego języka wspólnego (CLR). Otoka ułatwia manipulowanie właściwością zależności w kodzie (pozwala uniknąć wywołań do <xref:System.Windows.DependencyObject.SetValue%2A> każdego czasu i może to wywołać tylko raz w samej otoki). Otoka jest implementowana identycznie, jak zostanie zaimplementowana, Jeśli zarejestrowano niestandardową właściwość zależności. Aby uzyskać więcej informacji na temat implementowania właściwości zależności, zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md) i [Dodaj typ właściciela dla właściwości zależności](how-to-add-an-owner-type-for-a-dependency-property.md).  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner i dołączone właściwości  
 Można wywołać <xref:System.Windows.DependencyProperty.AddOwner%2A> właściwość zależności, która jest zdefiniowana jako dołączona właściwość przez klasę Owner. Ogólnie przyczyną jest uwidocznienie wcześniej dołączonej właściwości jako niedołączonej właściwości zależności. Następnie <xref:System.Windows.DependencyProperty.AddOwner%2A> zobaczysz wartość zwracaną `public static readonly` jako pole do użycia jako identyfikator właściwości zależności i zdefiniujesz odpowiednie właściwości "otoki", aby Właściwość pojawiła się w tabeli Members i obsługiwała dołączoną Właściwość Użycie w klasie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Metadane właściwości struktury](framework-property-metadata.md)
