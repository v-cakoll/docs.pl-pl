---
title: Domyślny kontekst schematu XAML i kontekst schematu WPF XAML
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 1312541321e74668e6527c6c54e712342fbb3a17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124699"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Domyślny kontekst schematu XAML i kontekst schematu WPF XAML
Kontekst schematu XAML jest koncepcyjnymi encji, który kwalifikuje się, jak produkcji XAML, który korzysta z określonego słownika XAML współdziała z obiektu zapisywania zachowania, w tym sposób mapowania typów rozwiązuje, jak zespoły są ładowane, jak w przypadku niektórych czytników i składników zapisywania ustawienia są interpretowane. W tym temacie opisano funkcje usług .NET Framework XAML i kontekst schematu XAML skojarzoną domyślną, który jest oparty na systemie typu CLR. W tym temacie opisano kontekst schematu XAML, który służy do WPF.  
  
## <a name="default-xaml-schema-context"></a>Domyślny kontekst schematu XAML  
 .NET framework XAML Services implementuje i używa domyślny kontekst schematu XAML. Domyślne zachowanie kontekst schematu XAML nie jest zawsze w pełni widoczne w interfejsie API <xref:System.Xaml.XamlSchemaContext> klasy. Jednak w wielu przypadkach zachowanie, które ma wpływ na domyślny kontekst schematu XAML jest możliwość obserwowania za pośrednictwem wspólny interfejs API w systemu typu XAML, takich jak członkowie <xref:System.Xaml.XamlMember> lub <xref:System.Xaml.XamlType>, lub za pośrednictwem interfejsów API ujawnianych w XAML czytników i składników zapisywania z XAML, które korzystają z domyślny kontekst schematu XAML.  
  
 Możesz utworzyć <xref:System.Xaml.XamlSchemaContext> która hermetyzuje domyślnego zachowania wywołując <xref:System.Xaml.XamlSchemaContext> konstruktora. Spowoduje to jawne utworzenie domyślny kontekst schematu XAML. Ten sam domyślny kontekst schematu XAML jest tworzony niejawnie, jeśli zainicjować czytnika XAML lub zapis XAML przy użyciu interfejsów API, która nie jawnie <xref:System.Xaml.XamlSchemaContext> parametr wejściowy.  
  
 Domyślny kontekst schematu XAML opiera się na odbicia środowiska CLR dla swojego zachowania mapowania typu. Dotyczy to również badanie definiujące CLR <xref:System.Type>i pokrewnych <xref:System.Reflection.PropertyInfo> lub <xref:System.Reflection.MethodInfo>. Ponadto autorstwa CLR dotyczącymi typów lub elementów członkowskich jest używana w celu Wypełnij szczegóły dla typu XAML lub XAML elementu członkowskiego informacje, których używa kopii typu środowiska CLR. Domyślny kontekst schematu XAML nie wymaga typu systemu rozszerzenia technik, takich jak `Invoker` wzorca, ponieważ niezbędne informacje są dostępne z systemu typu CLR.  
  
 Dla zestawu ładowania logiki domyślny kontekst schematu XAML zależy przede wszystkim żadnych wartości zestawu w mapowania przestrzeni nazw XAML. Ponadto <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> można podpowiedzi zestawu do załadowania dla scenariuszy, takich jak ładowanie typów wewnętrznych.  
  
## <a name="wpf-xaml-schema-context"></a>Kontekst schematu WPF XAML  
 Kontekst schematu WPF XAML jest opisany w tym temacie, ponieważ implementacji WPF stanowi ilustrację interesujące rodzajów funkcje, które mogą zostać wprowadzone przez zaimplementowanie innego niż domyślny kontekst schematu XAML. Ponadto koncepcji kontekst schematu XAML nie omówiono znacznie w dokumentacji programu WPF, odnoszący się do WPF XAML; zachowanie, które umożliwia kontekst schematu XAML może składać się całkowicie zrozumiały, jeśli zintegrowane z dyskusję na temat sposobu działania domyślny kontekst schematu XAML. Kontekst schematu WPF XAML implementuje następujące zachowanie.  
  
 **Zastępuje wyszukiwania:** WPF ma kilka modeli zawartości dla XAML w przypadku, gdy ma właściwości zawartości XAML, które działają bez konieczności <xref:System.Windows.Markup.ContentPropertyAttribute> opartego na atrybutach. <xref:System.Xaml.XamlType.LookupContentProperty%2A> zastąpienia WPF zaimplementować to zachowanie.  
  
 **Odroczenie WPF wyrażeń:** WPF zawiera kilka klas wyrażenie, które Odrocz wartość, dopóki dostępny jest kontekst środowiska uruchomieniowego. Ponadto rozszerzenie szablonu jest zachowanie środowiska uruchomieniowego, która zależy od opóźnienia technik.  
  
 **Typ optymalizacji wyszukiwania systemu:** WPF ma rozbudowane XAML słownictwa oraz obiekt modelu, w tym definicje elementów członkowskich klasy podstawowej, które dziedziczą dosłownie setki klasy zdefiniowane WPF. Ponadto WPF, sama jest rozłożona się między kilka zestawów. WPF optymalizuje jego wyszukiwanie typu przy użyciu tabel odnośników i innych technik. Zapewnia to poprawa wydajności przez domyślny kontekst schematu XAML i jego wyszukiwanie na podstawie CLR typu. W przypadkach, w których typów nie istnieją w tabeli odnośników zachowanie używa technik kontekst schematu XAML, które są podobne do domyślny kontekst schematu XAML.  
  
 **Rozszerzenie XamlType i XamlMember:** WPF rozszerza pojęcia właściwości przy użyciu właściwości zależności i pojęcia zdarzenia ze zdarzeniami trasowanymi. Nadanie tych pojęć większą wzajemną widoczność operacji przetwarzania XAML, rozszerza WPF <xref:System.Xaml.XamlType> i <xref:System.Xaml.XamlMember>i dodaje wewnętrzny właściwości, które zgłosić właściwości zależności i kierowane właściwości zdarzenia.  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>Uzyskiwanie dostępu do kontekst schematu WPF XAML  
 Jeśli używasz technik XAML, które są oparte na WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> lub <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>, kontekst schematu WPF XAML jest już używana na tych implementacji modułu zapisującego XAML i czytnika XAML.  
  
 Jeśli używasz innych czytnik XAML lub implementacji modułu zapisującego XAML, które nie Inicjuj kontekst schematu WPF XAML można rozpocząć pracę WPF XAML kontekst schematu z <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>. Tej wartości można następnie użyć jako inicjowania innego interfejsu API, używanego przez <xref:System.Xaml.XamlSchemaContext>. Na przykład, można wywołać <xref:System.Xaml.XamlXmlReader.%23ctor%2A> do inicjowania i Przekaż kontekst schematu WPF XAML. Można także użyć kontekst schematu WPF XAML dla operacji systemie typu XAML. Może to obejmować inicjowanie konstrukcji <xref:System.Xaml.XamlType> lub <xref:System.Xaml.XamlMember>, lub podczas wywoływania <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.  
  
 Należy pamiętać, że jeśli uzyskujesz dostęp do niektórych aspektów XAML w WPF z czystego perspektyw strumienia węzłów XAML, niektóre funkcje framework WPF może nie mieć działał jeszcze. Na przykład szablony kontrolek WPF nie są jeszcze stosowane. Dlatego jeśli uzyskujesz dostęp do właściwości, która może zostać wypełniony pełne wizualne drzewo w czasie wykonywania, może być widoczne tylko wartości właściwości, który odwołuje się do szablonu. Kontekst usługi przewidziane WPF — rozszerzenia znaczników może także być dokładne, jeśli podany z sytuacji bez środowiska uruchomieniowego i może spowodować wyjątki, podczas próby zapisu wykresu obiektu.  
  
## <a name="xaml-and-assembly-loading"></a>XAML i ładowanie zestawu  
 Ładowanie XAML i .NET Framework XAML usługi zestawu integruje się z zdefiniowane CLR koncepcji <xref:System.AppDomain>. Kontekst schematu XAML interpretuje jak ładować zestawy lub znaleźć typów w czasie wykonywania lub czasie projektowania, oparte na korzystanie z <xref:System.AppDomain> i inne czynniki. Logika różni się nieco w zależności od tego, czy XAML jest luźno XAML dla czytnika XAML, jest XAML kompilowana do biblioteki DLL przez `XamlBuildTask`, lub BAML generowany przez firmy WPF `PresentationBuildTask`.  
  
 Kontekst schematu WPF XAML integruje się z modelem aplikacji WPF, który z kolei używa <xref:System.AppDomain> i innych czynników, które są szczegóły implementacji WPF.  
  
#### <a name="xaml-reader-input-loose-xaml"></a>Dane wejściowe czytnika XAML (luźne XAML)  
  
1.  Kontekst schematu XAML, który wykonuje iterację przez <xref:System.AppDomain> aplikacji wyszukiwanie już załadowany zestaw, który dopasowuje wszystkie aspekty nazwę, począwszy od najbardziej niedawno załadowany zestaw. Jeśli zostanie znalezione dopasowanie, ten zestaw jest używany do rozpoznawania.  
  
2.  W przeciwnym razie jedną z następujących technik oparte na CLR <xref:System.Reflection.Assembly> interfejsu API są używane do załadowania zestawu:  
  
    -   Jeśli nazwa kwalifikuje się do mapowania, wywołaj <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> kwalifikowanej nazwy.  
  
    -   Jeśli w poprzednim kroku nie powiedzie się, użyj krótkiej nazwy (i token klucza publicznego Jeśli jest obecna) do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
    -   Jeśli nazwa jest niekwalifikowana w mapowaniu, wywołaj <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask` jest używany dla usług Windows Communication Foundation (WCF) i Windows Workflow Foundation.  
  
 Należy zauważyć, że zestaw, który odwołuje się za pośrednictwem `XamlBuildTask` są zawsze w pełni kwalifikowana.  
  
1.  Wywołaj <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> kwalifikowanej nazwy.  
  
2.  Jeśli w poprzednim kroku nie powiedzie się, użyj krótkiej nazwy (i token klucza publicznego Jeśli jest obecna) do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 Istnieją dwa aspekty ładowania zestawu dla BAML: podczas ładowania początkowego zestawu, który zawiera BAML jako składnik, a ładowanie zestawów zapasowy typ dla wszystkich typów, które odwołuje się produkcji BAML.  
  
##### <a name="assembly-load-for-initial-markup"></a>Ładowanie zestawu dla początkowej znaczników:  
 Odwołanie do zestawu do załadowania znaczników z jest zawsze niekwalifikowane.  
  
1.  Kontekst schematu WPF XAML, który wykonuje iterację przez <xref:System.AppDomain> aplikacji WPF, wyszukiwanie już załadowany zestaw, który dopasowuje wszystkie aspekty nazwę, począwszy od najbardziej niedawno załadowany zestaw. Jeśli zostanie znalezione dopasowanie, ten zestaw jest używany do rozpoznawania.  
  
2.  Jeśli w poprzednim kroku nie powiedzie się, użyj krótkiej nazwy (i token klucza publicznego Jeśli jest obecna) do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
##### <a name="assembly-references-by-baml-types"></a>Odwołania do zestawu według typów BAML:  
 Odwołania do zestawów dla typów używanych w środowisku produkcyjnym BAML są zawsze w pełni kwalifikowaną jako dane wyjściowe z zadania kompilacji.  
  
1.  Kontekst schematu WPF XAML, który wykonuje iterację przez <xref:System.AppDomain> aplikacji WPF, wyszukiwanie już załadowany zestaw, który dopasowuje wszystkie aspekty nazwę, począwszy od najbardziej niedawno załadowany zestaw. Jeśli zostanie znalezione dopasowanie, ten zestaw jest używany do rozpoznawania.  
  
2.  W przeciwnym razie jest jedną z następujących technik służy do załadowania zestawu:  
  
    -   Wywołaj <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> kwalifikowanej nazwy.  
  
    -   Krótka nazwa + publicznego tokenu kombinacja były zgodne z zestawem, który BAML został załadowany z, należy użyć tego zestawu.  
  
    -   Użyj krótkiej nazwy i token klucza publicznego do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- [Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML](understanding-xaml-node-stream-structures-and-concepts.md)
