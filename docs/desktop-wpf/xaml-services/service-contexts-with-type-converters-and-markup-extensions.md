---
title: Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 59c4385eb4df8c622be6164cdb0a1a911c445ca8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071662"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Konteksty usług dostępne dla typów konwerterów i rozszerzeń znaczników
Autorzy typów, które obsługują typy konwertera i rozszerzenia znaczników, często muszą mieć informacje kontekstowe o tym, gdzie użycie znajduje się w znacznikach lub w otaczającej strukturze wykresu obiektów. Informacje mogą być potrzebne, aby podany obiekt został poprawnie skreślony lub aby można było nawiązywać odwołania do istniejących obiektów na wykresie obiektu. Korzystając z usług .NET XAML kontekst, który może być wymagany, jest narażony jako seria interfejsów usługi. Kod obsługi konwertera typu lub rozszerzenia znaczników może wysyłać zapytania do <xref:System.Xaml.XamlObjectWriter> usługi przy użyciu kontekstu dostawcy usług, który jest dostępny i przekazywany z lub powiązanych typów. Kontekst schematu XAML jest bezpośrednio dostępny za pośrednictwem jednej z takich usług. W tym temacie opisano sposób uzyskiwania dostępu do kontekstów usługi z implementacji konwertera wartości i wyświetla listę zazwyczaj dostępnych usług i ich ról.

## <a name="obtaining-services"></a>Uzyskiwanie usług

Jako realizator konwertera wartości często potrzebujesz dostępu do pewnego typu kontekstu, w którym stosuje się konwerter wartości. Kontekst ten może zawierać informacje, takie jak aktywny kontekst schematu XAML, dostęp do systemu mapowania typów, który zapewnia kontekst schematu XAML i moduł zapisujący obiekty XAML i tak dalej. Usługi dostępne dla rozszerzenia znaczników lub implementacji konwertera typu są przekazywane za pośrednictwem parametrów kontekstu, które są częścią podpisu każdej metody wirtualnej. W każdym przypadku <xref:System.IServiceProvider> zostały zaimplementowane w <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> kontekście i można wywołać, aby zażądać usługi.

## <a name="services-for-a-markup-extension"></a>Usługi rozszerzenia znaczników

<xref:System.Windows.Markup.MarkupExtension>ma tylko jedną <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>metodę wirtualną, . Parametr `serviceProvider` wejściowy jest jak usługi są przekazywane do implementacji, gdy rozszerzenie znaczników jest wywoływana przez procesor XAML. Poniższy pseudokod ilustruje, jak implementacja rozszerzenia <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>znaczników może wyszukiwać usługi w jego:

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

## <a name="services-for-a-type-converter"></a>Usługi dla konwertera typów

<xref:System.ComponentModel.TypeConverter>ma cztery metody wirtualne, które używają kontekstu usługi i które obsługują użycia XAML. Każda z tych metod `context` przekazuje parametr wejściowy. Ten parametr jest <xref:System.ComponentModel.ITypeDescriptorContext>typu , ale <xref:System.IServiceProvider>interfejs dziedziczy , <xref:System.IServiceProvider.GetService%2A> i dlatego istnieje metoda dostępna do wpisywanie implementacji konwertera.

Poniższy pseudokod ilustruje, jak implementacja konwertera typów dla użycia XAML może <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>wyszukiwać usługi w jednym z jego nadpisań, w tym przypadku:

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

## <a name="services-for-a-value-serializer"></a>Usługi dla serializatora wartości

W kontekście serializatora wartości należy użyć typu <xref:System.Windows.Markup.ValueSerializer> dostawcy <xref:System.Windows.Markup.IValueSerializerContext>usług, który jest specyficzny dla klasy. Kontekst ten jest przekazywany do <xref:System.Windows.Markup.ValueSerializer> zastąpienia czterech metod wirtualnych. Wywołanie <xref:System.IServiceProvider.GetService%2A> z kontekstu, aby uzyskać usługi.

## <a name="using-the-xaml-service-provider-contexts"></a>Korzystanie z kontekstów dostawcy usług XAML

Dostawca usług <xref:System.IServiceProvider.GetService%2A> dostępu do usług XAML dostępnych dla rozszerzeń znaczników lub konwerterów typów jest implementowany jako klasa wewnętrzna, z ekspozycją tylko za pośrednictwem interfejsu i sposobem przekazywania go do odpowiedniego kontekstu. Za każdym razem, gdy operacja przetwarzania XAML w domyślnych implementacjach usług .NET XAML ścieżki ładowania lub ścieżki zapisywania wywołuje odpowiednie rozszerzenia znaczników lub metody konwertera typu, które wymagają kontekstu usługi, ten obiekt wewnętrzny jest przekazywany. W zależności od okoliczności kontekst usługi `MarkupExtensionContext` systemowej zapewnia albo lub `TextSyntaxContext`, ale specyfika obu tych klas są wewnętrzne. Twoja interakcja z tymi klasami jest <xref:System.IServiceProvider.GetService%2A>ograniczona do żądania od nich usług, poprzez .

## <a name="available-services-from-the-net-xaml-service-context"></a>Dostępne usługi z kontekstu usługi .NET XAML

Usługi NET XAML definiują usługi dla rozszerzeń znaczników, konwerterów typów, serializatorów wartości i potencjalnie innych użycia. W poniższych sekcjach opisano każdą z tych usług i zawierają wskazówki dotyczące sposobu, w jaki usługa może być używana w implementacji.

### <a name="iserviceprovider"></a>Iserviceprovider

**Dokumentacja referencyjna:**<xref:System.IServiceProvider>

**Istotne dla:** Podstawowe działanie infrastruktury opartej na usługach w .NET, dzięki czemu można wywołać <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.

### <a name="itypedescriptorcontext"></a>Itypedescriptorcontext

**Dokumentacja referencyjna:**<xref:System.ComponentModel.ITypeDescriptorContext>

Pochodzi z <xref:System.IServiceProvider>. Ta klasa reprezentuje kontekst <xref:System.ComponentModel.TypeConverter> w standardowych podpisów; <xref:System.ComponentModel.TypeConverter> jest klasą, która istnieje od platformy .NET Framework 1.0. Poprzedza XAML i scenariusz XAML <xref:System.ComponentModel.TypeConverter> dla konwersji typu wartości ciągu. W kontekście usług .NET XAML metody <xref:System.ComponentModel.TypeConverter> są implementowane jawnie. Jawne zachowanie implementacji wskazuje wywołującym, <xref:System.ComponentModel.ITypeDescriptorContext> że interfejs API nie jest odpowiedni dla systemów typu XAML lub do odczytu lub zapisu obiektów z XAML. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>i <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> zazwyczaj `null` zwraca z kontekstów usług .NET XAML.

### <a name="ivalueserializercontext"></a>Ivalueserializercontext

**Dokumentacja referencyjna:**<xref:System.Windows.Markup.IValueSerializerContext>

Pochodzi z <xref:System.ComponentModel.ITypeDescriptorContext> i również opiera się na jawne implementacje do tłumienia fałszywych implikacje dotyczące systemu typu XAML. Obsługuje metody pomocnicze wyszukiwania statycznego na <xref:System.Windows.Markup.ValueSerializer>programie .

### <a name="ixamltyperesolver"></a>Ixamltyperesolver

**Dokumentacja referencyjna:**<xref:System.Windows.Markup.IXamlTypeResolver>

**Zdefiniowane przez:** <xref:System.Windows.Markup> obszar nazw, zespół System.Xaml  

**Istotne dla:** Ładowanie scenariuszy ścieżek i interakcji z kontekstem schematu XAML

**Interfejs API usługi:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>

Może mieć wpływ na mapowanie typu XAML-TO-CLR, które jest niezbędne, gdy moduł zapisujący XAML konstruuje obiekt CLR na wykresie obiektu. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>przetwarza potencjalnie kwalifikowany ciąg prefiksu, który odpowiada<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>nazwie typu XAML ( ) i zwraca clr <xref:System.Type>. Rozpoznawanie typów jest zazwyczaj w dużym stopniu zależne od kontekstu schematu XAML. Tylko kontekst schematu XAML jest świadomy zagadnień, takich jak które zestawy są ładowane i które z tych zestawów mogą lub powinny być dostępne dla rozpoznawania typów.

### <a name="iuricontext"></a>Iuricontext

**Dokumentacja referencyjna:**<xref:System.Windows.Markup.IUriContext>

**Zdefiniowane przez:** <xref:System.Windows.Markup> obszar nazw, zespół System.Xaml  

**Istotne dla:** Załaduj ścieżkę i zapisz obsługę `x:Uri` ścieżek wartości elementów członkowskich, które są identyfikatorami URI lub wartościami.

**Interfejs API usługi:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>

Ta usługa raportuje globalnie dostępny katalog główny identyfikatora URI, jeśli istnieje. Katalog główny identyfikatora URI może służyć do rozpoznawania względnych identyfikatorów URI do bezwzględnych identyfikatorów URI lub odwrotnie. Ten scenariusz jest głównie istotne dla usług aplikacji, które są udostępniane przez określonej struktury lub możliwości często używane klasy elementu głównego w ramach. Podstawowy identyfikator URI można ustanowić jako ustawienie czytnika XAML, które jest następnie przekazywane do modułu zapisującego obiektów XAML i zgłaszane przez tę usługę.

### <a name="iambientprovider"></a>Iambientprovider

**Dokumentacja referencyjna:**<xref:System.Xaml.IAmbientProvider>

**Zdefiniowane przez:** <xref:System.Xaml> obszar nazw, zespół System.Xaml  

**Istotne dla:** Ładowanie obsługi ścieżki i odnośności wyszukiwania typu lub optymalizacji.

**Interfejsy API usługi:**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, trzy inne.

Koncepcja atmosfery w XAML jest techniką oznaczania określonego członka typu jako otoczenia. Alternatywnie typ może być otoczenia, tak aby wszystkie wartości właściwości, które posiadają wystąpienie typu powinny być traktowane właściwości otoczenia. Rozszerzenia znaczników lub konwertery typów, które znajdują się dalej wzdłuż strumienia węzła XAML i które są elementami podrzędnymi na wykresie obiektów, mogą uzyskiwać dostęp do właściwości otoczenia lub wystąpienia typu w czasie ładowania; lub mogą korzystać z wiedzy o strukturze otoczenia w zaoszczędzeniu czasu. Może to mieć wpływ na stopień kwalifikacji, który jest potrzebny <xref:System.Windows.Markup.IXamlTypeResolver> do `x:Type`rozwiązania typów dla innych usług, takich jak dla lub dla . Zobacz też <xref:System.Xaml.AmbientPropertyValue>.

### <a name="ixamlschemacontextprovider"></a>Ixamlschemacontextprovider

**Dokumentacja referencyjna:**<xref:System.Xaml.IXamlSchemaContextProvider>

**Zdefiniowane przez:** <xref:System.Xaml> obszar nazw, zespół System.Xaml  

**Istotne dla:** Załaduj ścieżkę i dowolną operację, która musi rozwiązać typ XAML do typu zapasowego.

**Interfejs API usługi:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>

Kontekst schematu XAML jest niezbędny dla wszystkich operacji odroczenia obciążenia, ponieważ ten sam kontekst schematu musi działać na obszarze odroczonym w celu zintegrowania odroczonej zawartości. Aby uzyskać więcej informacji na temat roli kontekstu schematu XAML, zobacz [Usługi XAML](../../../api/index.md).

### <a name="irootobjectprovider"></a>Irootobjectprovider

**Dokumentacja referencyjna:**<xref:System.Xaml.IRootObjectProvider>

**Zdefiniowane przez:** <xref:System.Xaml> obszar nazw, zespół System.Xaml  

**Istotne dla:** Ścieżka ładowania.

**Interfejs API usługi:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>

Usługa jest istotne dla usług aplikacji, które są udostępniane przez określonej struktury lub możliwości często używane klasy elementu głównego w ramach. Jednym ze scenariuszy uzyskiwania obiektu głównego jest połączenie okablowania kodu i zdarzenia. Na przykład implementacja WPF jest używana do kompilacji znaczników `x:Class` i okablowania dowolnego atrybutu obsługi zdarzeń, który znajduje się w dowolnym innym miejscu w znacznikach XAML. Punkt połączenia znaczników i kodzależne zdefiniowane klasy częściowe dla kompilacji znaczników znajduje się w elemencie głównym.

### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver

**Dokumentacja referencyjna:**<xref:System.Xaml.IXamlNamespaceResolver>

**Zdefiniowane przez:** <xref:System.Xaml> obszar nazw, zespół System.Xaml  

**Istotne dla:** Załaduj ścieżkę, zapisz ścieżkę.

**Interfejs API usługi:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> dla ścieżki ładowania, dla ścieżki zapisywania.

<xref:System.Xaml.IXamlNamespaceResolver>jest usługą, która może zwracać identyfikator obszaru nazw XAML / identyfikator URI na podstawie jego prefiksu mapowane w źródłowych znaczników XAML.

### <a name="iprovidevaluetarget"></a>Iprovidevaluetarget

**Dokumentacja referencyjna:**<xref:System.Windows.Markup.IProvideValueTarget>

**Zdefiniowane przez:** <xref:System.Windows.Markup> obszar nazw, zespół System.Xaml  

**Istotne dla:** Załaduj ścieżkę i zapisz ścieżkę.

**Interfejsy API usługi:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  

<xref:System.Windows.Markup.IProvideValueTarget>umożliwia konwerter typu lub rozszerzenie znaczników, aby uzyskać kontekst o tym, gdzie działa w czasie ładowania. Implementacje mogą używać tego kontekstu, aby unieważnić użycie. Na przykład WPF WPF ma logikę wewnątrz <xref:System.Windows.DynamicResourceExtension>niektórych jego rozszerzeń znaczników, takich jak . Logika <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> sprawdza, aby upewnić się, że rozszerzenie jest używane tylko do ustawiania właściwości zależności (lub krótką listę innych właściwości nie zależności).

### <a name="ixamlnameresolver"></a>Ixamlnameresolver

**Dokumentacja referencyjna:**<xref:System.Xaml.IXamlNameResolver>

**Zdefiniowane przez:** <xref:System.Xaml> obszar nazw, zespół System.Xaml  

**Istotne dla:** Załaduj definicję wykresu obiektu `x:Name` `x:Reference`ścieżki, rozpoznawanie obiektów identyfikowanych przez techniki specyficzne dla struktury lub.

**Interfejsy API usługi:**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; inne interfejsy API dla bardziej zaawansowanych scenariuszy, takich jak radzenie sobie z odwołaniami do przodu.

Implementacja `x:Reference` obsługi usług .NET XAML services zależy od tej usługi. Określone struktury lub narzędzia, które obsługują `x:Name` platformę używać<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> tej usługi do obsługi lub równoważne (przypisane) obsługi właściwości.

### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider

**Dokumentacja referencyjna:**<xref:System.Xaml.IDestinationTypeProvider>

**Zdefiniowane przez:** <xref:System.Xaml> obszar nazw, zespół System.Xaml  

**Istotne dla:** Załaduj rozdzielczość ścieżki pośrednich informacji o typie CLR.

**Interfejs API usługi:**<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>

Aby uzyskać więcej informacji, zobacz <xref:System.Xaml.IDestinationTypeProvider>.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [Rozszerzenia znaczników dla przeglądu XAML](markup-extensions-overview.md)
- [Typy konwerterów dla XAML — Omówienie](type-converters-overview.md)
