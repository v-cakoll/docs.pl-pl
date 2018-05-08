---
title: Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: b68f00724ecd3a3edc64ee1e3dd7d97bffa20a62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników
Autorzy typów, które obsługuje użycia typu konwertera i znaczników rozszerzenia często musi mieć informacje kontekstowe o którym użycia znajduje się w znaczniku lub w otaczającej strukturę wykresu obiektów. Informacje mogą być wymagane, aby udostępnionego obiektu zostanie uruchomiony prawidłowo lub, aby można było wprowadzić odwołania do obiektów w istniejących obiektach w grafie obiektu. Korzystając z usług .NET Framework XAML, kontekstu, które mogą być wymagane jest ujawniona jako serię interfejsów usług. Typ konwertera lub znacznik rozszerzenia obsługi kodu mogą wykonywać kwerendę o usługi przy użyciu kontekstu dostawcy usług, który jest dostępny i przekazany za pośrednictwem z <xref:System.Xaml.XamlObjectWriter> lub powiązane typy. Kontekst schematu XAML jest bezpośrednio dostępny za pośrednictwem jednej takiej usługi. W tym temacie opisano, jak uzyskać dostęp do usługi kontekstów z implementacji konwertera wartości i wyświetla zwykle dostępnych usług i ich role.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Uzyskiwanie usług  
 Jako implementujący konwerter wartości często muszą dostępu do niektórych typów kontekstu, w którym zastosowano konwerter wartości. Tego kontekstu może obejmują informacje takie jak active kontekst schematu XAML, dostęp do wybranego typu mapowania systemu kontekst schematu XAML i moduł zapisywania obiektów XAML Podaj i tak dalej. Dostępność usług dla implementacji konwertera znaczników, jak rozszerzenie lub typ są przekazywane za pośrednictwem parametrów kontekstu, które są częścią podpis każdej metody wirtualnej. W każdym przypadku należy <xref:System.IServiceProvider> zaimplementowana w tym kontekście i można wywołać <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> na żądanie usługi.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Usługi rozszerzenia znaczników  
 <xref:System.Windows.Markup.MarkupExtension> tylko jedna metoda wirtualna, ma <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Dane wejściowe `serviceProvider` parametr jest jak usług są przekazywane do implementacji, gdy rozszerzenie znaczników jest wywoływana przez procesor XAML. Następujące pseudocode przedstawiono, jak Implementacja rozszerzenia znaczników może wysyłać zapytania dotyczące usług w jej <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:  
  
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
 <xref:System.ComponentModel.TypeConverter> ma cztery metody wirtualne używający kontekstu usługi i użycia XAML, który obsługuje. Każda z tych metod przekazuje dane wejściowe `context` parametru. Ten parametr jest typu <xref:System.ComponentModel.ITypeDescriptorContext>, ale ten interfejs dziedziczy <xref:System.IServiceProvider>i dlatego istnieje <xref:System.IServiceProvider.GetService%2A> dostępnej na typ konwertera implementacji metody.  
  
 Następujące pseudocode przedstawiono, jak implementacja konwerter typu dla XAML użycia może wysyłać zapytania dotyczące usług w jednym z jego zastąpienia w takim przypadku <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:  
  
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
 Dla wartości kontekst serializatora, możesz użyć typ dostawcy usług, które są specyficzne dla <xref:System.Windows.Markup.ValueSerializer> klasy <xref:System.Windows.Markup.IValueSerializerContext>. Ten kontekst jest przekazywana do zastąpienia cztery <xref:System.Windows.Markup.ValueSerializer> metodach wirtualnych. Wywołanie <xref:System.IServiceProvider.GetService%2A> z kontekstu uzyskanie usług.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>Przy użyciu konteksty dostawcy usług XAML  
 Dostawcy usług dla <xref:System.IServiceProvider.GetService%2A> dostęp do usług XAML dostępne dla konwerterów rozszerzenia lub typ znaczników jest zaimplementowany jako Wewnętrzna klasa, z narażenia tylko za pośrednictwem interfejsu oraz sposób przekazywania do odpowiedniego kontekstu. Zawsze, gdy operacja przetwarzania XAML w domyślnej implementacji usług .NET Framework XAML załadować ścieżki lub ścieżkę zapisu wywołuje znaczników odpowiednie rozszerzenie lub typu konwertera metody, które wymagają kontekstu usługi, jest przekazywany obiekt wewnętrzny. W zależności od okoliczności, w kontekście usługi systemu zawiera albo `MarkupExtensionContext` lub `TextSyntaxContext`, ale specyfice obu tych klas są wewnętrzne. Interakcję z tych klas jest ograniczone do żądania usług z nimi za pośrednictwem <xref:System.IServiceProvider.GetService%2A>.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>Usługi dostępne w kontekście usługi .NET Framework XAML  
 Usługi XAML .NET framework definiuje usługi rozszerzenia znaczników, typy konwerterów wartości serializatorów i potencjalnie inne użycia. W poniższych sekcjach opisano każdy z tych usług i zapewnianie wskazówek w zakresie jak usługa może być używana w implementacji.  
  
### <a name="iserviceprovider"></a>Dostawca IServiceProvider  
 **Odwołanie dokumentacji**: <xref:System.IServiceProvider>  
  
 **Dotyczy:** podstawowych operacji opartych na usługach infrastruktury w programie .NET Framework, dzięki czemu można wywołać <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Odwołanie dokumentacji**: <xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Pochodną <xref:System.IServiceProvider>. Ta klasa reprezentuje kontekst w standardzie <xref:System.ComponentModel.TypeConverter> podpisów. <xref:System.ComponentModel.TypeConverter> jest klasa, która była dostępna już .NET Framework 1.0. Go poprzedza XAML i XAML <xref:System.ComponentModel.TypeConverter> scenariusza konwersja typu wartości ciągu. W kontekście usług .NET Framework XAML, metody <xref:System.ComponentModel.TypeConverter> są jawnie implementowane. Wskazuje zachowanie jawnej implementacji dotyczące obiektów wywołujących który <xref:System.ComponentModel.ITypeDescriptorContext> interfejsu API nie jest ważna, systemów typu XAML lub odczytywania lub zapisywania obiektów z pliku XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, i <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> zwykle zwraca `null` z konteksty usług .NET Framework XAML.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Odwołanie dokumentacji**: <xref:System.Windows.Markup.IValueSerializerContext>  
  
 Pochodną <xref:System.ComponentModel.ITypeDescriptorContext> i również jest oparta na jawne implementacje do pomijania false skutki o system typów języka XAML. Obsługuje wyszukiwania statycznej metody pomocnicze na <xref:System.Windows.Markup.ValueSerializer>.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Odwołanie dokumentacji**: <xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Zdefiniowane przez:** <xref:System.Windows.Markup> przestrzeni nazw, zestawu System.Xaml    
  
 **Dotyczy:** scenariuszy ścieżki obciążenia i interakcji z kontekst schematu XAML  
  
 **Usługi interfejsu API:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 Może mieć wpływ mapowania typu XAML do środowiska CLR, które są niezbędne, gdy moduł zapisujący XAML konstrukcji obiektu CLR na wykresie obiektu. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> przetwarza ciąg potencjalnie kwalifikowana prefiks, który odpowiada nazwie typu XAML (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) i zwraca CLR <xref:System.Type>. Rozpoznawania typów zależy zwykle znacznie kontekst schematu XAML. Kontekst schematu XAML jest pamiętać o kwestiach, takie jak zestawy, które zostały załadowane i które z tych zestawów można lub powinni mieć dostęp do rozpoznawania typu.  
  
### <a name="iuricontext"></a>IUriContext  
 **Odwołanie dokumentacji**: <xref:System.Windows.Markup.IUriContext>  
  
 **Zdefiniowane przez:** <xref:System.Windows.Markup> przestrzeni nazw, zestawu System.Xaml    
  
 **Dotyczy:** załadować ścieżki i Zapisz ścieżkę Obsługa wartości elementów członkowskich, które są identyfikatorami URI lub `x:Uri` wartości.  
  
 **Usługi interfejsu API:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Tej usługi Raporty dostępnego globalnie głównego identyfikatora URI, jeśli istnieje. Główne URI mogą być używane do rozpoznawania względne identyfikatory URI na bezwzględny identyfikator URI lub na odwrót. Ten scenariusz jest głównie dotyczące usług aplikacji, które są dostępne w szczególności framework lub możliwości element klasy głównym często używanych w ramach. Podstawowy identyfikator URI, można ustanowić ustawienie do odczytu XAML, który następnie jest przekazywana do zapisywania obiektów języka XAML i zgłoszone przez tę usługę.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Odwołanie dokumentacji**: <xref:System.Xaml.IAmbientProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw, zestawu System.Xaml    
  
 **Dotyczy:** załadować optymalizacji lub odroczenia wyszukiwania i obsługi typu ścieżki.  
  
 **Interfejsy API usługi:**<xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 innych użytkowników.    
  
 Koncepcja otoczenie w języku XAML jest technika oznaczenie określonego elementu członkowskiego typu jako otoczenia. Alternatywnie typu może być otoczenia tak, aby wszystkie wartości właściwości zawierających wystąpienie tego typu należy traktować jako właściwości otoczenia. Rozszerzenia znaczników lub konwertery typu, które są dalej w tej samej strumień węzłów XAML i elementy podrzędne na wykresie obiektu, które są dostęp do właściwości otaczających lub wystąpienie typu w czasie ładowania. mogą też użyć informacji na temat struktury otoczenia na czas zapisywania. Może to mieć wpływ na stopień kwalifikacji potrzebnego do rozpoznania typy dla innych usług, takich jak dla <xref:System.Windows.Markup.IXamlTypeResolver> lub `x:Type`. Zobacz też <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Odwołanie dokumentacji**: <xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw, zestawu System.Xaml    
  
 **Dotyczy:** ścieżka obciążenia i żadnej operacji, która musi zostać rozpoznany typu XAML zapasowego typu.  
  
 **Usługi interfejsu API:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Kontekst schematu XAML jest niezbędne dla wszystkich operacji obciążenia Ustąp, ponieważ kontekst tego samego schematu musi działać w obszarze odroczonego integrowana odroczonego zawartości. Aby uzyskać więcej informacji na temat roli kontekst schematu XAML, zobacz [usługi XAML](../../../docs/framework/xaml-services/index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Odwołanie dokumentacji**: <xref:System.Xaml.IRootObjectProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw, zestawu System.Xaml    
  
 **Dotyczy:** ścieżka obciążenia.  
  
 **Usługi interfejsu API:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 Usługa jest istotne dla usług aplikacji, które są udostępniane przez konkretnego framework lub możliwości element klasy głównym często używanych w ramach. Jeden scenariusz uzyskiwania obiekt główny łączy CodeBehind i okablowania zdarzeń. Na przykład WPF wykonania `x:Class` jest używany dla kompilacji znaczników i okablowania dowolny atrybut obsługi zdarzeń, która znajduje się w innych pozycji w kodzie XAML. Punkt połączenia znaczników i kodu powiązanego zdefiniowanych klas częściowych do kompilacji znaczników jest w elemencie głównym.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Odwołanie dokumentacji**: <xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw, zestawu System.Xaml    
  
 **Dotyczy:** ścieżka obciążenia, ścieżkę zapisu.  
  
 **Usługi interfejsu API:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> dla ścieżki obciążenia <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> dla ścieżkę zapisu.  
  
 <xref:System.Xaml.IXamlNamespaceResolver> to usługa, która może zwracać identyfikator przestrzeni nazw XAML / identyfikator URI na podstawie prefiksu jego mapowane w źródłowym znaczników XAML.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Odwołanie dokumentacji**: <xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Zdefiniowane przez:** <xref:System.Windows.Markup> przestrzeni nazw, zestawu System.Xaml    
  
 **Dotyczy:** załadować ścieżki i Zapisz ścieżkę.  
  
 **Interfejsy API usługi:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.    
  
 <xref:System.Windows.Markup.IProvideValueTarget> Umożliwia rozszerzenie typu konwertera lub znacznik uzyskać kontekstu, o której działa w czasie ładowania. Implementacje może użyć tego kontekstu unieważnić użytkowania. Na przykład WPF ma logiki wewnątrz niektóre z jego rozszerzenia znaczników takich jak <xref:System.Windows.DynamicResourceExtension>. Testy logiczne <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> aby upewnić się, że rozszerzenie jest używana tylko do ustawiania właściwości zależności (lub krótką listę innych właściwości zależności nie).  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Odwołanie dokumentacji**: <xref:System.Xaml.IXamlNameResolver>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw, zestawu System.Xaml    
  
 **Dotyczy:** obciążenia ścieżki obiektu wykresu definicji, rozpoznawania obiektów identyfikowane przez `x:Name`, `x:Reference`, lub określonej struktury.  
  
 **Interfejsy API usługi:**<xref:System.Xaml.IXamlNameResolver.Resolve%2A>; innych interfejsów API dla bardziej zaawansowanych scenariuszy, takich jak zajmowanie się odwołania w przód.    
  
 Implementacja usług .NET Framework XAML `x:Reference` Obsługa zależy od tej usługi. Określonych platform lub narzędzia obsługujące platformę korzystają z tej usługi `x:Name` obsługi lub równoważnej (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> przypisanych) Obsługa właściwości.  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Odwołanie dokumentacji**: <xref:System.Xaml.IDestinationTypeProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeni nazw, zestawu System.Xaml    
  
 **Dotyczy:** załadować Ścieżka rozpoznawania pośrednie informacji o typie CLR.  
  
 **Usługi interfejsu API:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Markup.MarkupExtension>  
 <xref:System.Xaml.XamlObjectWriter>  
 [Rozszerzenia znaczników dla przeglądu XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)  
 [Typy konwerterów dla XAML — omówienie](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)
