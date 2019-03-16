---
title: Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 04d1a8b1c6f05537f12c3df79fda007332621264
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58049459"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników
Autorzy typów, które obsługują typów konwerterów i znaczników rozszerzenie użycia często muszą mieć informacje kontekstowe o którym użycia znajduje się w znaczniku lub w otaczających struktura grafu obiektów. Informacje mogą być wymagane, aby poprawnie konkretyzacji udostępnionego obiektu lub tak, aby odwołania do obiektu w istniejących obiektach na grafie obiektu jest możliwe. Korzystając z usług programu .NET Framework XAML, kontekst, który może być wymagane jest udostępniany jako serię interfejsy usługi. Odpytuje typu konwertera lub języka znaczników, rozszerzenie kod pomocy technicznej dla usługi za pomocą kontekstu dostawcy usług, który jest dostępny i przekazanych z <xref:System.Xaml.XamlObjectWriter> lub typów pokrewnych. Kontekst schematu XAML jest bezpośrednio dostępny za pośrednictwem jednej takiej usługi. W tym temacie opisano, jak uzyskać dostęp do konteksty usług z implementacji konwertera wartości i wyświetla zazwyczaj dostępnych usług i ich ról.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Uzyskiwanie usługi  
 Jako implementującego konwerter wartości często trzeba dostępu do określonego typu kontekstu, w którym zastosowano konwertera wartości. Ten kontekst może zawierać informacje, takie jak active kontekst schematu XAML, dostęp do system mapowania typu, który kontekst schematu XAML i modułu zapisywania obiektu XAML zapewniają i tak dalej. Dostępne usługi dla implementacji konwertera rozszerzenia lub typu znaczników są przekazywane za pośrednictwem parametrów kontekstu, które są częścią podpis poszczególnych metod wirtualnych. W każdym przypadku masz <xref:System.IServiceProvider> zaimplementowane w kontekście, a może wywołać <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> żądania usługi.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Usługi rozszerzenia znaczników  
 <xref:System.Windows.Markup.MarkupExtension> ma tylko jedną metodę wirtualną, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Dane wejściowe `serviceProvider` parametr jest jak usług są przekazywane do implementacji, gdy rozszerzenie znaczników jest wywoływana przez procesor XAML. Poniższym pseudokodzie ilustruje, jak Implementacja rozszerzenia znaczników może zapytanie dla usług w jej <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:  
  
```  
public override object ProvideValue(IServiceProvider serviceProvider)  
{  
...  
    // Get the IXamlTypeResolver from the service provider  
    if (serviceProvider == null)  
    {  
        throw new ArgumentNullException("serviceProvider");  
    }  
    IXamlTypeResolver xamlTypeResolver = serviceProvider.GetService(typeof(IXamlTypeResolver)) as IXamlTypeResolver;  
    if (xamlTypeResolver == null)  
   {  
        throw new ArgumentException("IXamlTypeResolver"));  
    }  
...  
}  
```  
  
<a name="services_for_a_type_converter"></a>   
## <a name="services-for-a-type-converter"></a>Usługi konwertera typów  
 <xref:System.ComponentModel.TypeConverter> ma cztery metody wirtualne, które korzystają z kontekstu usługi, co umożliwia obsługę użycia XAML. Każda z tych metod przekazuje dane wejściowe `context` parametru. Ten parametr jest typu <xref:System.ComponentModel.ITypeDescriptorContext>, ale ten interfejs dziedziczy <xref:System.IServiceProvider>i dlatego istnieje <xref:System.IServiceProvider.GetService%2A> metody dostępne dla implementacji konwertera typów.  
  
 Poniższym pseudokodzie ilustruje, jak implementacja konwerter typu dla XAML użycia może być zapytanie dla usług w jednej z jej zastąpienia, w tym przypadku <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:  
  
```  
public override object ConvertFrom(ITypeDescriptorContext typeDescriptorContext,  
  CultureInfo cultureInfo,  
  object source)  
{  
    IRootObjectProvider rootProvider = typeDescriptorContext.GetService(typeof(IRootObjectProvider)) as IRootObjectProvider;  
    if (rootProvider != null && source is String)  
    {  
        //return something, else ...  
    }  
    throw GetConvertFromException(source);  
}  
```  
  
<a name="services_for_a_value_serializer"></a>   
## <a name="services-for-a-value-serializer"></a>Usługi dla serializatora wartość  
 Dla wartości serializator kontekstowe, użyj typ dostawcy usług, które są specyficzne dla <xref:System.Windows.Markup.ValueSerializer> klasy <xref:System.Windows.Markup.IValueSerializerContext>. Ten kontekst jest przekazywany do zastąpienia cztery <xref:System.Windows.Markup.ValueSerializer> metod wirtualnych. Wywołaj <xref:System.IServiceProvider.GetService%2A> z kontekstu, aby uzyskać usług.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>Za pomocą konteksty dostawcy usług w XAML  
 Dostawcy usług dla <xref:System.IServiceProvider.GetService%2A> dostęp do usług XAML można konwertery rozszerzenia lub typu znaczników jest implementowany jako Wewnętrzna klasa, z ujawnienia wyłącznie za pośrednictwem interfejsu i jak jest przekazywany do odpowiedniego kontekstu. Zawsze, gdy operacja przetwarzania XAML w domyślnej implementacji .NET Framework XAML Services załadować ścieżki lub ścieżka zapisu wywołuje znaczników odpowiednie rozszerzenie lub typu konwertera metody, które wymagają kontekst usługi, ten obiekt wewnętrzny jest przekazywany. W zależności od okoliczności, w kontekście usługi systemu zawiera jedną `MarkupExtensionContext` lub `TextSyntaxContext`, ale szczegółowe informacje na temat obu tych klas są wewnętrzne. Interakcji z tych klas jest ograniczona do żądania usług z nich, przy użyciu <xref:System.IServiceProvider.GetService%2A>.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>Dostępne usługi w kontekście usługi .NET Framework XAML  
 .NET framework XAML Services definiuje usługi rozszerzenia znaczników, konwerterów typów, wartości serializatory i potencjalnie inne zastosowania. W poniższych sekcjach opisano każdą z tych usług i zapewniają wskazówki dotyczące sposobu usługi mogą być używane w celu wykonania.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Dokumentację referencyjną**: <xref:System.IServiceProvider>  
  
 **Odpowiednie do:** Podstawowe operacji opartych na usługach infrastruktury w programie .NET Framework, dzięki czemu można wywołać <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Dokumentację referencyjną**: <xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Pochodzi od klasy <xref:System.IServiceProvider>. Ta klasa reprezentuje kontekst w standardzie <xref:System.ComponentModel.TypeConverter> podpisów. <xref:System.ComponentModel.TypeConverter> to klasa, która istniała od .NET Framework 1.0. Jest on starszy od XAML i XAML <xref:System.ComponentModel.TypeConverter> scenariusz konwersja typu wartości ciągu. W kontekście usług programu .NET Framework XAML metody <xref:System.ComponentModel.TypeConverter> są implementowane w sposób jawny. Jawna implementacja zachowanie wskazuje dotyczące obiektów wywołujących, <xref:System.ComponentModel.ITypeDescriptorContext> interfejsu API nie jest ważna, systemów typu XAML lub do odczytu lub zapisu obiektów z XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, i <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> zazwyczaj zwraca `null` z usług programu .NET Framework XAML kontekstów.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Dokumentację referencyjną**: <xref:System.Windows.Markup.IValueSerializerContext>  
  
 Pochodzi od klasy <xref:System.ComponentModel.ITypeDescriptorContext> i również opiera się na jawne implementacje do pomijania skutki fałszywe informacje o systemie typu XAML. Obsługuje wyszukiwanie statyczne metody pomocnicze na <xref:System.Windows.Markup.ValueSerializer>.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Dokumentację referencyjną**: <xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Zdefiniowane przez:** <xref:System.Windows.Markup> przestrzeni nazw System.Xaml zestawu  
  
 **Odpowiednie do:** Scenariusze ścieżki obciążenia oraz interakcję z kontekst schematu XAML  
  
 **Interfejs API usługi:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 Może mieć wpływ na XAML do CLR mapowania typów, które są niezbędne, gdy Edytor XAML konstruuje obiekt CLR wykresu obiektu. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> przetwarza ciąg potencjalnie kwalifikowana prefiks odnosi się do nazwy typu XAML (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>), a następnie zwraca CLR <xref:System.Type>. Rozpoznawanie typów jest zazwyczaj znacznej mierze zależy od kontekst schematu XAML. Kontekst schematu XAML jest pamiętać o kwestiach, takich jak zestawy, które są ładowane i które te zestawy lub powinni mieć dostęp do rozpoznawania typu.  
  
### <a name="iuricontext"></a>IUriContext  
 **Dokumentację referencyjną**: <xref:System.Windows.Markup.IUriContext>  
  
 **Zdefiniowane przez:** <xref:System.Windows.Markup> przestrzeni nazw System.Xaml zestawu  
  
 **Odpowiednie do:** Ładowanie ścieżki i Zapisz ścieżkę obsługi wartości elementów członkowskich, które są identyfikatory URI lub `x:Uri` wartości.  
  
 **Interfejs API usługi:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Ta usługa raporty dostępnie głównego identyfikatora URI, jeśli istnieje. Głównego identyfikatora URI może służyć do rozwiązania względne identyfikatory URI, URI na bezwzględny lub odwrotnie. Ten scenariusz jest głównie dotyczą usługi aplikacji, które są dostępne w określonej struktury lub możliwości klasy elementu głównego często używanych w ramach. Podstawowy identyfikator URI może zostać nawiązana ustawienie do odczytu XAML, który jest następnie przekazywane do modułu zapisywania obiektu XAML i zgłoszone przez tę usługę.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Dokumentację referencyjną**: <xref:System.Xaml.IAmbientProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw System.Xaml zestawu  
  
 **Odpowiednie do:** Załaduj optymalizacji lub odroczenia ścieżki obsługi i typu wyszukiwania.  
  
 **Interfejsy API usługi:**<xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 innych użytkowników.  
  
 Koncepcja otoczenie w XAML jest techniką do oznaczania konkretnego składowej typu jako otoczenia. Alternatywnie typu mogą być otoczenia wartości wszystkich właściwości, zawierających wystąpienie tego typu należy rozważyć właściwości otoczenia. Rozszerzenia znaczników lub konwerterów typów, które są dalej w tym samym strumień węzłów XAML i które są elementy podrzędne na grafie obiektu można uzyskiwać dostęp do właściwości otoczenia lub wystąpienie typu w czasie ładowania; lub mogą używać informacji na temat struktury otoczenia na oszczędzić czas. Może to wpłynąć na stopień kwalifikacji, które są potrzebne do Rozwiązywanie typy dla innych usług, takich jak <xref:System.Windows.Markup.IXamlTypeResolver> lub `x:Type`. Zobacz też <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Dokumentację referencyjną**: <xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw System.Xaml zestawu  
  
 **Odpowiednie do:** Ścieżka obciążenia i każdej operacji, która musi zostać rozpoznany typ XAML typ zapasowy.  
  
 **Interfejs API usługi:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Kontekst schematu XAML jest niezbędne dla wszystkich operacji ładowania Ustąp, ponieważ ten sam kontekst schematu musi działać na obszarze odroczonego integrowana odroczonej zawartości. Aby uzyskać więcej informacji na temat roli kontekst schematu XAML, zobacz [XAML Services](index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Dokumentację referencyjną**: <xref:System.Xaml.IRootObjectProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw System.Xaml zestawu  
  
 **Odpowiednie do:** Ścieżka obciążenia.  
  
 **Interfejs API usługi:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 Usługa jest odpowiednie do usług aplikacji, które są udostępniane przez określonej struktury lub możliwości klasy elementu głównego często używanych w ramach. Jeden scenariusz do uzyskiwania obiektu głównego jest połączenie związane z kodem i okablowania zdarzeń. Na przykład implementacji WPF okna `x:Class` jest używany dla kompilacji znaczników i okablowania dowolny atrybut procedury obsługi zdarzeń, która znajduje się w dowolnym miejscu, w znaczniku XAML. Punkt połączenia z kodu znaczników i związane z kodem zdefiniowane klas częściowych, do kompilacji znaczników jest w elemencie głównym.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Dokumentację referencyjną**: <xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw System.Xaml zestawu  
  
 **Odpowiednie do:** Ścieżka obciążenia ścieżka zapisu.  
  
 **Interfejs API usługi:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> dla ścieżki obciążenia <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> dla ścieżka zapisu.  
  
 <xref:System.Xaml.IXamlNamespaceResolver> jest to usługa, która może zwracać identyfikatora przestrzeni nazw XAML / identyfikator URI na podstawie jego prefiksu mapowane w znaczniku XAML źródłowy.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Dokumentację referencyjną**: <xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Zdefiniowane przez:** <xref:System.Windows.Markup> przestrzeni nazw System.Xaml zestawu  
  
 **Odpowiednie do:** Załaduj ścieżki i Zapisz ścieżkę.  
  
 **Interfejsy API usługi:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  
  
 <xref:System.Windows.Markup.IProvideValueTarget> Włącza rozszerzenia typu konwertera lub języka znaczników, można uzyskać kontekst dotyczący gdy działa w czasie ładowania. Implementacje przy użyciu tego kontekstu do unieważnienia użycia. Na przykład WPF ma logiki wewnątrz niektóre z jego rozszerzenia znaczników takich jak <xref:System.Windows.DynamicResourceExtension>. Testy logiczne <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> aby upewnić się, że rozszerzenie jest używana tylko do ustawiania właściwości zależności (lub krótką listę innych właściwości bez zależności).  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Dokumentację referencyjną**: <xref:System.Xaml.IXamlNameResolver>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw System.Xaml zestawu  
  
 **Odpowiednie do:** Ładowanie definicji wykresu obiektu ścieżki, rozpoznawanie obiektów identyfikowane przez `x:Name`, `x:Reference`, lub techniki określonej platformy.  
  
 **Interfejsy API usługi:**<xref:System.Xaml.IXamlNameResolver.Resolve%2A>; inne interfejsy API dla bardziej zaawansowanych scenariuszy, takich jak zajmowanie się odwołania w przód.  
  
 Implementacja programu .NET Framework XAML Services `x:Reference` obsługi opiera się na tę usługę. Określonych platform lub narzędzia, które obsługuje struktury, należy używać tej usługi dla `x:Name` obsługi lub równoważny (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> opartego na atrybutach) obsługi właściwości.  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Dokumentację referencyjną**: <xref:System.Xaml.IDestinationTypeProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw System.Xaml zestawu  
  
 **Odpowiednie do:** Załaduj rozpoznawania ścieżek pośrednich informacji o typie CLR.  
  
 **Interfejs API usługi:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Rozszerzenia znaczników dla przeglądu XAML](markup-extensions-for-xaml-overview.md)
- [Typy konwerterów dla XAML — omówienie](type-converters-for-xaml-overview.md)
