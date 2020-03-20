---
title: Metadane zależności właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 3d84510fce69e81929cbe9b6088e12aaf3409769
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186369"
---
# <a name="dependency-property-metadata"></a>Metadane zależności właściwości
System [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości zawiera system raportowania metadanych, który wykracza poza to, co można zgłaszać o właściwości za pomocą odbicia lub ogólne właściwości środowiska wykonawczego języka wspólnego (CLR). Metadane właściwości zależności mogą być również przypisywane jednoznacznie przez klasę definiującą właściwość zależności, można zmienić, gdy właściwość zależności zostanie dodana do innej klasy i może być specjalnie zastąpiona przez wszystkie klasy pochodne, które dziedziczą właściwość zależności z definiowanej klasy podstawowej.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że rozumiesz właściwości zależności z perspektywy konsumenta istniejących właściwości zależności w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klasach i przeczytałeś przegląd właściwości [zależności.](dependency-properties-overview.md) Aby postępować zgodnie z przykładami w tym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] temacie, należy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również zrozumieć i wiedzieć, jak pisać aplikacje.  
  
<a name="dp_metadata_contents"></a>
## <a name="how-dependency-property-metadata-is-used"></a>Jak używane są metadane właściwości zależności  
 Metadane właściwości zależności istnieje jako obiekt, który można zbadać do zbadania właściwości właściwości zależności. Te metadane są również często dostępne przez system właściwości, ponieważ przetwarza dowolną właściwość danej zależności. Obiekt metadanych właściwości zależności może zawierać następujące typy informacji:  
  
- Wartość domyślna właściwości zależności, jeśli nie można określić żadnej innej wartości dla właściwości zależności według wartości lokalnej, stylu, dziedziczenia itp. Aby uzyskać szczegółowe omówienie sposobu, w jaki wartości domyślne uczestniczą w priorytecie używanym przez system właściwości podczas przypisywania wartości właściwości zależności, zobacz [Pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).  
  
- Odwołania do implementacji wywołania zwrotnego, które wpływają na zachowania przymusu lub powiadomienia o zmianie na podstawie typu właściciela. Należy zauważyć, że te wywołania zwrotne są często definiowane z poziomem dostępu niepublicznego, więc uzyskanie rzeczywistych odwołań z metadanych nie jest zwykle możliwe, chyba że odwołania znajdują się w dozwolonym zakresie dostępu. Aby uzyskać więcej informacji na temat wywołania zwrotnych właściwości zależności, zobacz [Wywołania zwrotności właściwości zależności i sprawdzanie poprawności](dependency-property-callbacks-and-validation.md).  
  
- Jeśli właściwość zależności, o której mowa, jest uważana za właściwość na poziomie struktury WPF, metadane mogą zawierać właściwości zależności na poziomie struktury WPF, które zgłaszają informacje i stan dla usług, takich jak poziom struktury WPF logika dziedziczenia aparatu układu i właściwości. Aby uzyskać więcej informacji na temat tego aspektu metadanych właściwości zależności, zobacz [Metadane właściwości framework .](framework-property-metadata.md)  
  
<a name="APIs"></a>
## <a name="metadata-apis"></a>Interfejsy API metadanych  
 Typ, który zgłasza większość informacji o metadanych <xref:System.Windows.PropertyMetadata> używanych przez system właściwości jest klasą. Wystąpienia metadanych są opcjonalnie określone, gdy właściwości zależności są zarejestrowane w systemie właściwości i mogą być określone ponownie dla dodatkowych typów, które dodają się jako właściciele lub zastępują metadane, które dziedziczą z zależności klasy podstawowej definicji właściwości. (W przypadkach, gdy rejestracja właściwości nie <xref:System.Windows.PropertyMetadata> określa metadanych, domyślnie tworzone są wartości domyślne dla tej klasy). Zarejestrowane metadane <xref:System.Windows.PropertyMetadata> są zwracane, <xref:System.Windows.DependencyProperty.GetMetadata%2A> jak po wywołaniu różnych przeciążeń, <xref:System.Windows.DependencyObject> które otrzymują metadane z właściwości zależności w wystąpieniu.  
  
 Klasa <xref:System.Windows.PropertyMetadata> jest następnie pochodną, aby zapewnić bardziej szczegółowe metadane dla podziałów architektonicznych, takich jak klasy na poziomie struktury WPF. <xref:System.Windows.UIPropertyMetadata>dodaje raportowanie <xref:System.Windows.FrameworkPropertyMetadata> animacji i zapewnia właściwości na poziomie struktury WPF wymienione w poprzedniej sekcji. Gdy właściwości zależności są zarejestrowane, mogą <xref:System.Windows.PropertyMetadata> być rejestrowane przy użyciu tych klas pochodnych. Po zbadaniu metadanych <xref:System.Windows.PropertyMetadata> typ podstawowy może potencjalnie zostać rzutowany do klas pochodnych, dzięki czemu można zbadać bardziej szczegółowe właściwości.  
  
> [!NOTE]
> Właściwości właściwości, które mogą <xref:System.Windows.FrameworkPropertyMetadata> być określone w są czasami określane w tej dokumentacji jako "flagi". Podczas tworzenia nowych wystąpień metadanych do użycia w rejestracji właściwości zależności lub zastąpienia metadanych, należy <xref:System.Windows.FrameworkPropertyMetadataOptions> określić te wartości przy użyciu flagwise wyliczenia, a następnie podać ewentualnie łączone wartości wyliczenia do <xref:System.Windows.FrameworkPropertyMetadata> konstruktora. Jednak po skonstruowaniu te cechy opcji <xref:System.Windows.FrameworkPropertyMetadata> są widoczne w ramach jako szereg właściwości logicznych, a nie konstruująca wartość wyliczenia. Właściwości logiczne umożliwiają sprawdzanie każdego warunkowego, zamiast wymagać zastosowania maski do wartości wyliczenia flagowego, aby uzyskać interesujące informacje. Konstruktor używa łączone <xref:System.Windows.FrameworkPropertyMetadataOptions> w celu zachowania długości podpisu konstruktora uzasadnione, natomiast rzeczywiste skonstruowane metadane udostępnia właściwości dyskretne, aby kwerendy metadane bardziej intuicyjne.  
  
<a name="override_or_subclass"></a>
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>Kiedy zastąpić metadane, kiedy wyprowadzić klasę  
 System [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości ustanowił możliwości zmiany niektórych cech właściwości zależności bez konieczności ich całkowicie ponownie zaimplementowane. Jest to realizowane przez konstruowanie innego wystąpienia metadanych właściwości dla właściwości zależności, ponieważ istnieje ona dla określonego typu. Należy zauważyć, że większość istniejących właściwości zależności nie są właściwości wirtualne, więc ściśle mówiąc "re-implementing" je na dziedziczone klasy można osiągnąć tylko przez cieniowanie istniejącego elementu członkowskiego.  
  
 Jeśli scenariusz, który próbujesz włączyć dla właściwości zależności na typie, nie może zostać zrealizowany przez modyfikację właściwości istniejących właściwości zależności, może być konieczne utworzenie klasy pochodnej, a następnie zadeklarowanie właściwości zależności niestandardowej na klasie pochodnej. Właściwość zależności niestandardowej zachowuje się identycznie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości zależności zdefiniowanych przez interfejsy API. Aby uzyskać więcej informacji na temat niestandardowych właściwości zależności, zobacz [Właściwości zależności niestandardowej](custom-dependency-properties.md).  
  
 Jedną z godnych uwagi cech właściwości zależności, której nie można zastąpić, jest jej typ wartości. Jeśli dziedziczysz właściwość zależności, która ma przybliżone zachowanie, które potrzebujesz, ale potrzebujesz innego typu dla niego, trzeba będzie zaimplementować właściwość zależności niestandardowej i być może połączyć właściwości za pomocą konwersji typu lub innych implementacji na niestandardowej klasie. Ponadto nie można zastąpić <xref:System.Windows.ValidateValueCallback>istniejącego , ponieważ to wywołanie zwrotne istnieje w samym polu rejestracji, a nie w jego metadanych.  
  
<a name="scenarios"></a>
## <a name="scenarios-for-changing-existing-metadata"></a>Scenariusze zmiany istniejących metadanych  
 Jeśli pracujesz z metadanymi istniejącej właściwości zależności, jednym z typowych scenariuszy zmiany metadanych właściwości zależności jest zmiana wartości domyślnej. Zmiana lub dodanie wywołań zwrotnych systemu właściwości jest bardziej zaawansowany scenariusz. Można to zrobić, jeśli implementacja klasy pochodnej ma różne wzajemne powiązania między właściwości zależności. Jednym z warunków posiadania modelu programowania, który obsługuje zarówno kod i deklaratywne użycie jest, że właściwości muszą włączyć jest ustawiona w dowolnej kolejności. W związku z tym wszelkie właściwości zależne muszą być ustawione just-in-time bez kontekstu i nie można polegać na znajomości kolejności ustawień, takich jak mogą być znalezione w konstruktorze. Aby uzyskać więcej informacji na temat tego aspektu systemu właściwości, zobacz [Wywołania zwrotności właściwości zależności i sprawdzanie poprawności](dependency-property-callbacks-and-validation.md). Należy zauważyć, że wywołania zwrotne sprawdzania poprawności nie są częścią metadanych; są one częścią identyfikatora właściwości zależności. W związku z tym wywołania zwrotne sprawdzania poprawności nie można zmienić przez zastąpienie metadanych.  
  
 W niektórych przypadkach można również zmienić opcje metadanych właściwości na poziomie struktury WPF na istniejące właściwości zależności. Te opcje komunikują niektóre znane warunki dotyczące właściwości na poziomie struktury WPF do innych procesów na poziomie struktury WPF, takich jak system układu.  Ustawienie opcji jest zazwyczaj wykonywane tylko podczas rejestrowania nowej właściwości zależności, ale jest również możliwe, aby zmienić <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> <xref:System.Windows.DependencyProperty.AddOwner%2A> metadane właściwości na poziomie struktury WPF w ramach lub wywołania. Aby uzyskać określone wartości do użycia i więcej informacji, zobacz [Metadane właściwości framework .](framework-property-metadata.md) Aby uzyskać więcej informacji, które są istotne dla sposobu ustawienia tych opcji dla nowo zarejestrowanej właściwości zależności, zobacz [Właściwości zależności niestandardowej](custom-dependency-properties.md).  
  
<a name="dp_override_metadata"></a>
### <a name="overriding-metadata"></a>Zastępowanie metadanych  
 Celem zastępowania metadanych jest przede wszystkim, dzięki czemu masz możliwość zmiany różnych zachowań pochodnych metadanych, które są stosowane do właściwości zależności, ponieważ istnieje na typ. Przyczyny tego są wyjaśnione bardziej szczegółowo w sekcji [Metadane.](#dp_metadata_contents) Aby uzyskać więcej informacji, w tym niektóre przykłady kodu, zobacz [Zastępowanie metadanych właściwości zależności](how-to-override-metadata-for-a-dependency-property.md).  
  
 Metadane właściwości mogą być dostarczane dla właściwości<xref:System.Windows.DependencyProperty.Register%2A>zależności podczas wywołania rejestracji ( ). Jednak w wielu przypadkach można podać metadane specyficzne dla typu dla klasy, gdy dziedziczy tę właściwość zależności. Można to zrobić, <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> wywołując metodę.  Na przykład z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsów API <xref:System.Windows.FrameworkElement> klasa jest typem, <xref:System.Windows.UIElement.Focusable%2A> który najpierw rejestruje właściwość zależności. Ale <xref:System.Windows.Controls.Control> klasa zastępuje metadane dla właściwości zależności, aby zapewnić własną początkową `true`wartość domyślną, zmieniając <xref:System.Windows.UIElement.Focusable%2A> ją z `false` , i w przeciwnym razie ponownie używa oryginalnej implementacji.  
  
 Po zastąpieniu metadanych, różne właściwości metadanych są scalane lub zastępowane.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>zostanie scalona. Jeśli dodasz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>nowy , że wywołanie zwrotne jest przechowywany w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> w zastąpienia, wartość <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> jest promowana jako odwołanie od najbliższego elementa nadrzędnego, który określił go w metadanych.  
  
- Rzeczywiste zachowanie systemu <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> właściwości jest, że implementacje dla wszystkich właścicieli metadanych w hierarchii są zachowywane i dodawane do tabeli, z kolejnością wykonania przez system właściwości jest to, że najczęściej pochodne wywołania zwrotne klasy są wywoływane jako pierwsze.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>zostanie zastąpiony. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.DefaultValue%2A> w zastąpienia, wartość pochodzi <xref:System.Windows.PropertyMetadata.DefaultValue%2A> od najbliższego elementa nadrzędnego, który określił go w metadanych.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementacje. Jeśli dodasz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>nowy , że wywołanie zwrotne jest przechowywany w metadanych. Jeśli nie określisz <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> w zastąpienia, wartość <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> jest promowana jako odwołanie od najbliższego elementa nadrzędnego, który określił go w metadanych.  
  
- Zachowanie systemu właściwości jest <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> wywoływane tylko w bezpośrednich metadanych. Nie są zachowywane żadne odwołania do innych <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementacji w hierarchii.  
  
 To zachowanie jest <xref:System.Windows.PropertyMetadata.Merge%2A>implementowane przez programie i może zostać zastąpione przez klasy metadanych pochodnych.  
  
#### <a name="overriding-attached-property-metadata"></a>Zastępowanie dołączonych metadanych właściwości  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dołączone właściwości są implementowane jako właściwości zależności. Oznacza to, że mają one również metadane właściwości, które poszczególne klasy można zastąpić. Zagadnienia dotyczące zakresu dołączonej właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w są <xref:System.Windows.DependencyObject> zazwyczaj, że każdy może mieć dołączone właściwości ustawione na nich. W związku <xref:System.Windows.DependencyObject> z tym każda klasa pochodna może zastąpić metadane dla każdej dołączonej właściwości, ponieważ może być ustawiona na wystąpienie klasy. Można zastąpić wartości domyślne, wywołania zwrotne lub właściwości raportowania charakterystycznych na poziomie struktury WPF. Jeśli dołączona właściwość jest ustawiona na wystąpienie klasy, te właściwości zastępowania właściwości właściwości mają zastosowanie. Na przykład można zastąpić wartość domyślną, tak aby wartość zastąpienia jest raportowana jako wartość dołączonej właściwości w wystąpieniach klasy, gdy właściwość nie jest ustawiona w inny sposób.  
  
> [!NOTE]
> Właściwość <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> nie jest odpowiednia dla dołączonych właściwości.  
  
<a name="dp_add_owner"></a>
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>Dodawanie klasy jako właściciela istniejącej właściwości zależności  
 Klasa może dodać się jako właściciel właściwości zależności, która została już <xref:System.Windows.DependencyProperty.AddOwner%2A> zarejestrowana, przy użyciu metody. Dzięki temu klasa do korzystania z właściwości zależności, który został pierwotnie zarejestrowany dla innego typu. Klasa dodawania zazwyczaj nie jest klasą pochodną typu, która jako pierwsza zarejestrowała tę właściwość zależności jako właściciela. Skutecznie to pozwala klasy i jej klas pochodnych do "dziedziczenia" implementacji właściwości zależności bez oryginalnej klasy właściciela i dodawanie klasy jest w tej samej hierarchii klasy true. Ponadto dodawanie klasy (i wszystkie klasy pochodne, jak również) można następnie podać metadane specyficzne dla typu dla oryginalnej właściwości zależności.  
  
 Oprócz dodawania się jako właściciel za pośrednictwem metod narzędziowych systemu właściwości, klasa dodawania powinna deklarować dodatkowe elementy członkowskie publiczne na siebie, aby właściwość zależności] była pełnoprawnym uczestnikiem systemu właściwości z ekspozycją zarówno na kod, jak i znaczniki . Klasa, która dodaje istniejącą właściwość zależności ma takie same obowiązki, o ile uwidacznianie modelu obiektu dla tej właściwości zależności, podobnie jak klasa, która definiuje nową właściwość zależności niestandardowej. Pierwszym takim elementem członkowskim do udostępnienia jest pole identyfikatora właściwości zależności. To pole powinno `public static readonly` być <xref:System.Windows.DependencyProperty>polem typu, które jest przypisane do wartości zwracanej <xref:System.Windows.DependencyProperty.AddOwner%2A> wywołania. Drugi element członkowski do zdefiniowania jest właściwość "otoka" wspólnego środowiska wykonawczego języka (CLR). Otoka sprawia, że znacznie bardziej wygodne do manipulowania właściwości zależności <xref:System.Windows.DependencyObject.SetValue%2A> w kodzie (można uniknąć wywołań za każdym razem i można dokonać tego wywołania tylko raz w otoce samej). Otoka jest implementowana identycznie jak to będzie implementowane, jeśli zostały zarejestrowane właściwości zależności niestandardowej. Aby uzyskać więcej informacji na temat implementowania właściwości zależności, zobacz [Właściwości zależności niestandardowej](custom-dependency-properties.md) i [Dodaj typ właściciela dla właściwości zależności](how-to-add-an-owner-type-for-a-dependency-property.md).  
  
#### <a name="addowner-and-attached-properties"></a>Właściwości addowner i dołączone  
 Można wywołać <xref:System.Windows.DependencyProperty.AddOwner%2A> właściwość zależności, która jest zdefiniowana jako dołączone właściwości przez klasę właściciela. Ogólnie rzecz biorąc, powodem tego jest udostępnić wcześniej dołączone właściwości jako właściwości zależności nie dołączone. Następnie udostępni wartość <xref:System.Windows.DependencyProperty.AddOwner%2A> zwracaną `public static readonly` jako pole do użycia jako identyfikator właściwości zależności i zdefiniujesz odpowiednie właściwości "otoki", tak aby właściwość pojawiała się w tabeli członków i obsługuje użycie właściwości niezałączone w klasie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Metadane właściwości struktury](framework-property-metadata.md)
