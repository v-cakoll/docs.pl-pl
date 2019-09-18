---
title: Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 0d4e274ad7b64820e74347908c08c7726e96bbe8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053844"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników
Autorzy typów, którzy obsługują konwerter typów i użycie rozszerzeń znaczników, muszą często mieć kontekstowe informacje o tym, gdzie użycie znajduje się w znaczniku lub w strukturze wykresu otaczających obiektów. Informacje mogą być konieczne w celu poprawnego wystąpienia podanego obiektu lub odwołania do istniejących obiektów na grafie obiektów. W przypadku korzystania z .NET Framework usług XAML kontekst, który może być wymagany, jest ujawniany jako seria interfejsów usługi. Kod obsługi konwertera typów lub rozszerzeń znaczników może wysyłać zapytania dotyczące usługi przy użyciu kontekstu dostawcy usług, który jest dostępny i jest przeszukiwany przez typy powiązane z <xref:System.Xaml.XamlObjectWriter> lub. Kontekst schematu XAML jest dostępny bezpośrednio za pomocą jednej takiej usługi. W tym temacie opisano sposób uzyskiwania dostępu do kontekstów usługi z implementacji konwertera wartości i są wyświetlane zazwyczaj dostępne usługi i ich role.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Uzyskiwanie usług  
 Jako implementujący konwerter wartości często potrzebny jest dostęp do pewnego typu kontekstu, w którym zastosowano konwerter wartości. Ten kontekst może obejmować takie informacje, jak kontekst aktywnego schematu XAML, dostęp do systemu mapowania typów, który udostępnia kontekst schematu XAML i składnik zapisywania obiektów XAML, i tak dalej. Usługi dostępne dla wdrożenia znacznika lub implementacji konwertera typów są przekazywane przez parametry kontekstu, które są częścią podpisu każdej metody wirtualnej. W każdym przypadku <xref:System.IServiceProvider> zaimplementowane w kontekście i mogą wywołać <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> żądanie usługi.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Usługi dla rozszerzenia znaczników  
 <xref:System.Windows.Markup.MarkupExtension>ma tylko jedną metodę wirtualną, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Parametr wejściowy `serviceProvider` to sposób, w jaki usługi są przekazywane do implementacji, gdy rozszerzenie znacznika jest wywoływane przez procesor XAML. Poniższy pseudokodzie ilustruje, jak implementacja rozszerzenia znaczników może wysyłać zapytania o usługi w swojej <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:  
  
```csharp  
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
## <a name="services-for-a-type-converter"></a>Usługi dla konwertera typów  
 <xref:System.ComponentModel.TypeConverter>Program ma cztery metody wirtualne korzystające z kontekstu usługi i obsługujące użycie języka XAML. Każda z tych metod przekazuje parametr wejściowy `context` . Ten parametr jest typu <xref:System.ComponentModel.ITypeDescriptorContext>, ale ten interfejs dziedziczy <xref:System.IServiceProvider>i w <xref:System.IServiceProvider.GetService%2A> związku z tym ma metodę dostępną dla implementacji konwertera typów.  
  
 Poniższy pseudokodzie ilustruje, jak implementacja konwertera typów dla użycia XAML może wykonywać zapytania dotyczące usług w jednym z jego zastąpień, w <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>tym przypadku:  
  
```csharp  
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
## <a name="services-for-a-value-serializer"></a>Usługi dla serializatora wartości  
 W przypadku kontekstu serializatora wartości należy użyć typu dostawcy usługi, który jest specyficzny <xref:System.Windows.Markup.ValueSerializer> dla klasy <xref:System.Windows.Markup.IValueSerializerContext>,. Ten kontekst jest przesyłany do zastąpień <xref:System.Windows.Markup.ValueSerializer> czterech metod wirtualnych. Wywołaj <xref:System.IServiceProvider.GetService%2A> z kontekstu, aby uzyskać usługi.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>Korzystanie z kontekstów dostawcy usług XAML  
 Dostawca usług do <xref:System.IServiceProvider.GetService%2A> uzyskiwania dostępu do usług XAML dostępnych dla rozszerzeń znaczników lub konwerterów typów jest implementowany jako Klasa wewnętrzna, z narażeniem tylko za pomocą interfejsu i sposobu przekazywania go do odpowiedniego kontekstu. Za każdym razem, gdy operacja przetwarzania XAML w domyślnych .NET Framework implementacjach usługi XAML ścieżki ładowania lub ścieżki zapisu wywołuje odpowiednie rozszerzenie znaczników lub metody konwertera typów, które wymagają kontekstu usługi, ten obiekt wewnętrzny jest przekazaniem. W zależności od sytuacji kontekst usługi systemowej zawiera `MarkupExtensionContext` albo lub `TextSyntaxContext`, ale te, które są określone w obu tych klasach, są wewnętrzne. Interakcje z tymi klasami są ograniczone do wysyłania do nich usług za pośrednictwem <xref:System.IServiceProvider.GetService%2A>programu.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>Dostępne usługi z .NET Framework kontekstu usługi XAML  
 .NET Framework usługi XAML definiują usługi dla rozszerzeń znaczników, konwerterów typów, serializatorów wartości i potencjalnie innych zastosowań. W poniższych sekcjach opisano każdą z tych usług i przedstawiono wskazówki dotyczące sposobu używania usługi w implementacji.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Dokumentacja referencyjna**:<xref:System.IServiceProvider>  
  
 **Istotne dla:** Podstawowa operacja infrastruktury opartej na usłudze w .NET Framework, aby można było wywoływać <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Dokumentacja referencyjna**:<xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Pochodzi od <xref:System.IServiceProvider>. Ta klasa reprezentuje kontekst w standardowych <xref:System.ComponentModel.TypeConverter> sygnaturach; <xref:System.ComponentModel.TypeConverter> jest klasą, która istniała od .NET Framework 1,0. Jest to wstępnie aktualna wartość XAML i <xref:System.ComponentModel.TypeConverter> scenariusz języka XAML dla konwersji typu String-Value. W kontekście .NET Framework usług XAML metody <xref:System.ComponentModel.TypeConverter> są implementowane jawnie. Zachowanie jawnej implementacji wskazuje, że <xref:System.ComponentModel.ITypeDescriptorContext> interfejs API nie jest istotny dla systemów typu XAML lub do odczytu lub zapisu obiektów z XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A> `null` i <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> generalnie zwracają z .NET Framework kontekstowych usług XAML.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Dokumentacja referencyjna**:<xref:System.Windows.Markup.IValueSerializerContext>  
  
 Pochodzi z <xref:System.ComponentModel.ITypeDescriptorContext> i również polega na jawnych implementacjach, aby pominąć fałszywe konsekwencje dotyczące systemu typów XAML. Obsługuje metody pomocnika wyszukiwania statycznego <xref:System.Windows.Markup.ValueSerializer>w.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Dokumentacja referencyjna**:<xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Zdefiniowane przez:** <xref:System.Windows.Markup> przestrzeń nazw, zestaw system. XAML  
  
 **Istotne dla:** Scenariusze Załaduj ścieżkę i interakcje z kontekstem schematu XAML  
  
 **Interfejs API usługi:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 Może mieć wpływ na mapowanie typu XAML-to-CLR, które są niezbędne, gdy moduł zapisujący XAML konstruuje obiekt CLR w grafie obiektu. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>przetwarza potencjalnie kwalifikowany prefiks ciągu, który odnosi się do nazwy typu XAML (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) i zwraca CLR. <xref:System.Type> Rozwiązywanie typów jest zwykle silnie zależne od kontekstu schematu XAML. Tylko kontekst schematu XAML jest świadomy zagadnień, takich jak zestawy, które są ładowane, i które z tych zestawów mogą lub powinny być dostępne do rozpoznawania typów.  
  
### <a name="iuricontext"></a>IUriContext  
 **Dokumentacja referencyjna**:<xref:System.Windows.Markup.IUriContext>  
  
 **Zdefiniowane przez:** <xref:System.Windows.Markup> przestrzeń nazw, zestaw system. XAML  
  
 **Istotne dla:** Załaduj ścieżkę i Zapisz obsługę ścieżki wartości elementów członkowskich, które są `x:Uri` identyfikatorami URI lub wartościami.  
  
 **Interfejs API usługi:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Ta usługa zgłasza globalnie dostępny katalog główny URI (jeśli istnieje). Główny identyfikator URI może służyć do rozpoznawania względnych identyfikatorów URI do bezwzględnych identyfikatorów URI lub odwrotnie. Ten scenariusz dotyczy głównie usług aplikacji, które są udostępniane przez określoną strukturę, lub możliwości często używanej klasy elementu głównego w strukturze. Podstawowy identyfikator URI można ustalić jako ustawienia czytnika XAML, które następnie są przekazywane do modułu zapisywania obiektów XAML i raportowane przez tę usługę.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Dokumentacja referencyjna**:<xref:System.Xaml.IAmbientProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeń nazw, zestaw system. XAML  
  
 **Istotne dla:** Załaduj obsługę ścieżki i przeszukiwanie typów lub optymalizacje.  
  
 **Interfejsy API usługi:** <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 inne.  
  
 Koncepcja Ambience w języku XAML jest techniką do oznaczania określonego elementu członkowskiego typu jako otoczenia. Alternatywnie, typ może być otaczający, aby wszystkie wartości właściwości, które przechowują wystąpienie typu, powinny być uznawane za właściwości otoczenia. Rozszerzenia znaczników lub konwertery typów, które znajdują się w strumieniu węzła XAML i są elementami podrzędnymi na grafie obiektów, mogą uzyskać dostęp do właściwości otoczenia lub wystąpienia typu w czasie ładowania; mogą też korzystać z wiedzy o strukturze otoczenia w czasie zapisywania. Może to mieć wpływ na stopień kwalifikacji, który jest wymagany do rozpoznawania typów dla innych usług, takich jak <xref:System.Windows.Markup.IXamlTypeResolver> dla `x:Type`lub. Zobacz też <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Dokumentacja referencyjna**:<xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeń nazw, zestaw system. XAML  
  
 **Istotne dla:** Załaduj ścieżkę i wszystkie operacje, które muszą rozpoznać typ XAML, do typu zapasowego.  
  
 **Interfejs API usługi:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Kontekst schematu XAML jest niezbędny do opóźniania operacji ładowania, ponieważ ten sam kontekst schematu musi działać na odroczonym obszarze w celu zintegrowania odroczonej zawartości. Aby uzyskać więcej informacji na temat roli kontekstu schematu XAML, zobacz [usługi XAML](index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Dokumentacja referencyjna**:<xref:System.Xaml.IRootObjectProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeń nazw, zestaw system. XAML  
  
 **Istotne dla:** Ścieżka ładowania.  
  
 **Interfejs API usługi:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 Usługa ma zastosowanie do usług aplikacji, które są udostępniane przez określoną strukturę lub przez funkcje często używanej klasy elementu głównego w strukturze. Jeden z scenariuszy uzyskiwania obiektu głównego jest łączący związany z kodem i okablowanie zdarzeń. Na przykład implementacja `x:Class` WPF jest używana do kompilowania znaczników i okablowania dowolnego atrybutu programu obsługi zdarzeń, który znajduje się w innym miejscu znacznika XAML. Punkt połączenia znaczników i zdefiniowanej w kodzie klas częściowych do kompilowania znaczników znajduje się w elemencie głównym.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Dokumentacja referencyjna**:<xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeń nazw, zestaw system. XAML  
  
 **Istotne dla:** Ścieżka ładowania, Zapisz ścieżkę.  
  
 **Interfejs API usługi:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> dla ścieżki<xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> ładowania dla ścieżki zapisu.  
  
 <xref:System.Xaml.IXamlNamespaceResolver>to usługa, która może zwracać identyfikator przestrzeni nazw XAML/identyfikator URI na podstawie jego prefiksu zamapowanego w źródłowym znaczniku XAML.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Dokumentacja referencyjna**:<xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Zdefiniowane przez:** <xref:System.Windows.Markup> przestrzeń nazw, zestaw system. XAML  
  
 **Istotne dla:** Załaduj ścieżkę i Zapisz ścieżkę.  
  
 **Interfejsy API usługi:** <xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  
  
 <xref:System.Windows.Markup.IProvideValueTarget>Włącza konwerter typów lub rozszerzenie znaczników w celu uzyskania kontekstu, w którym działa w czasie ładowania. Implementacje mogą używać tego kontekstu, aby unieważnić użycie. Na przykład, WPF ma logikę wewnątrz niektórych rozszerzeń znaczników, takich jak <xref:System.Windows.DynamicResourceExtension>. Logika sprawdza, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> aby upewnić się, że rozszerzenie jest używane tylko do ustawiania właściwości zależności (lub krótką listę innych właściwości niezależności).  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Dokumentacja referencyjna**:<xref:System.Xaml.IXamlNameResolver>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeń nazw, zestaw system. XAML  
  
 **Istotne dla:** Ścieżka do definicji grafu obiektów, rozpoznawanie obiektów zidentyfikowanych przez `x:Name`, `x:Reference`lub technik specyficznych dla platformy.  
  
 **Interfejsy API usługi:** <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; inne interfejsy API dla bardziej zaawansowanych scenariuszy, takich jak postępowanie z odwołaniami do przodu.  
  
 Implementacja usług .NET Framework XAML jest `x:Reference` obsługiwana przez tę usługę. Określone struktury lub narzędzia, które obsługują platformę, korzystają z tej `x:Name` usługi w celu obsługi<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> lub równoważnej obsługi właściwości (atrybutd).  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Dokumentacja referencyjna**:<xref:System.Xaml.IDestinationTypeProvider>  
  
 **Zdefiniowane przez:** <xref:System.Xaml> przestrzeń nazw, zestaw system. XAML  
  
 **Istotne dla:** Rozpoznanie ścieżki dotyczącej pośrednich informacji o typie CLR.  
  
 **Interfejs API usługi:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Rozszerzenia znaczników dla przeglądu XAML](markup-extensions-for-xaml-overview.md)
- [Typy konwerterów dla XAML — omówienie](type-converters-for-xaml-overview.md)
