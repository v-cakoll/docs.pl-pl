---
title: "Domyślny kontekst schematu XAML i kontekst schematu WPF XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ee7c83868934f1a524bb0068ea5e749e6cbfab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Domyślny kontekst schematu XAML i kontekst schematu WPF XAML
Kontekst schematu XAML jest koncepcyjny jednostki, która kwalifikuje się jak produkcji XAML, który korzysta z określonego słownika XAML współdziała z obiektu zapisywania zachowanie, w tym sposób mapowania typu rozwiązuje, jak zestawy są załadowane, jak w przypadku niektórych składników zapisywania i odczytywania ustawienia są interpretowane. W tym temacie opisano funkcje usług .NET Framework XAML i kontekst schematu XAML skojarzoną domyślną, który jest oparta na systemie typów CLR. W tym temacie opisano kontekst schematu XAML, służący do WPF.  
  
## <a name="default-xaml-schema-context"></a>Domyślny kontekst schematu XAML  
 Usługi XAML .NET framework implementuje i używa domyślny kontekst schematu XAML. Domyślne zachowanie kontekst schematu XAML nie jest zawsze całości widoczny w interfejsie API <xref:System.Xaml.XamlSchemaContext> klasy. Jednak w wielu przypadkach wpływ kontekst schematu XAML domyślne zachowanie jest według za pośrednictwem wspólnego interfejsu API systemu typu XAML, takich jak <xref:System.Xaml.XamlMember> lub <xref:System.Xaml.XamlType>, lub za pośrednictwem narażone na czytników XAML i zapisywania XAML, które korzystają z interfejsów API domyślny kontekst schematu XAML.  
  
 Można utworzyć <xref:System.Xaml.XamlSchemaContext> która hermetyzuje domyślne zachowanie przez wywołanie metody <xref:System.Xaml.XamlSchemaContext> konstruktora. Spowoduje to utworzenie jawnie domyślny kontekst schematu XAML. Tej samej domyślny kontekst schematu XAML tworzona jest niejawnie, jeśli zainicjować czytnika XAML lub zapis XAML za pomocą interfejsów API, która nie jawnie <xref:System.Xaml.XamlSchemaContext> parametru wejściowego.  
  
 Domyślny kontekst schematu XAML zależy od odbicia CLR zachowanie mapowania typu. Dotyczy to również sprawdzając definiującej CLR <xref:System.Type>i pokrewnych <xref:System.Reflection.PropertyInfo> lub <xref:System.Reflection.MethodInfo>. Ponadto autorstwa CLR typów albo elementów członkowskich jest używany do Wypełnij szczegółowych informacji dla typu XAML lub informacji elementu członkowskiego XAML, które używa kopii typu środowiska CLR. Domyślny kontekst schematu XAML nie wymaga typu systemu rozszerzenia technik, takich jak `Invoker` wzorca, ponieważ niezbędne informacje są dostępne w systemie typów CLR.  
  
 Dla zestawu ładowania logiki domyślny kontekst schematu XAML zależy głównie wartości zestawu w mapowania przestrzeni nazw XAML. Ponadto <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> można wskazówki zestawu do załadowania dla scenariuszy, takich jak podczas ładowania typów wewnętrznych.  
  
## <a name="wpf-xaml-schema-context"></a>Kontekst schematu WPF XAML  
 Kontekst schematu WPF XAML jest opisany w tym temacie, ponieważ implementacja WPF udostępnia ilustrację interesujące rodzaje funkcje, które mogą zostać wprowadzone zaimplementowanie z systemem innym niż domyślny kontekst schematu XAML. Ponadto koncepcji kontekst schematu XAML nie omówiono znacznie w dokumentacji programu WPF, którego dotyczy WPF XAML; kontekst schematu XAML umożliwia zachowanie tylko może być całkowicie zrozumiały zintegrowany z omówieniem działania domyślny kontekst schematu XAML. Kontekst schematu WPF XAML wykonuje następujące działania.  
  
 **Zastępuje wyszukiwania:** WPF ma kilka modeli zawartości określonych dla XAML w przypadku, gdy nie ma właściwości zawartości XAML, które funkcji bez konieczności <xref:System.Windows.Markup.ContentPropertyAttribute> przypisane. <xref:System.Xaml.XamlType.LookupContentProperty%2A>zastąpienia WPF implementuje tego zachowania.  
  
 **Odroczenie wyrażeń WPF:** WPF funkcji kilka klas wyrażenie, które mają być odroczone wartość, dopóki nie będzie dostępne kontekstu środowiska uruchomieniowego. Rozszerzenia szablonu jest również zachowania w czasie wykonywania, która zależy od opóźnienia technik.  
  
 **Wpisz systemu wyszukiwania optymalizacje:** WPF zawiera szeroką gamę XAML słownictwa oraz obiekt modelu, w tym definicji elementu członkowskiego klasy podstawowej, które dziedziczą dosłownie setki klas zdefiniowanych WPF. Ponadto WPF sam jest rozmieszczenie do kilku zestawów. WPF optymalizuje jego wyszukiwania typów przy użyciu tabel odnośników i innych technik. Zapewnia to wydajność przez domyślny kontekst schematu XAML i jego wyszukiwania typów CLR na podstawie. W przypadkach, których typy nie istnieją w tabeli odnośników zachowanie używa techniki kontekst schematu XAML, które są podobne do domyślny kontekst schematu XAML.  
  
 **Rozszerzenie XamlType i XamlMember:** WPF rozszerza pojęcia dotyczące właściwości zależności właściwości i zdarzenia rozsyłane pojęć zdarzeń związanych z. Nadanie tych pojęć lepszą widoczność operacje przetwarzania XAML, rozszerza WPF <xref:System.Xaml.XamlType> i <xref:System.Xaml.XamlMember>i dodaje wewnętrzny właściwości, które raport właściwości zależności i kierowania właściwości zdarzenia.  
  
### <a name="accessing-the-wpf-xaml-schema-context"></a>Uzyskiwanie dostępu do kontekst schematu WPF XAML  
 Jeśli używasz techniki XAML, które są oparte na WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> lub <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>, kontekst schematu WPF XAML jest już używany w tych implementacji składnika zapisywania języka XAML i czytnika XAML.  
  
 Jeśli używane są inne czytnik XAML lub implementacje składnika zapisywania języka XAML, które nie Inicjuj kontekst schematu WPF XAML, można rozpocząć pracę WPF XAML kontekst schematu z <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>. Można następnie użyć tej wartości jako inicjowania dla innych korzystające z interfejsu API <xref:System.Xaml.XamlSchemaContext>. Na przykład można wywołać <xref:System.Xaml.XamlXmlReader.%23ctor%2A> inicjowania i Przekaż kontekst schematu WPF XAML. Można także użyć kontekst schematu WPF XAML dla operacji system typu XAML. Może to być inicjowanie konstrukcji <xref:System.Xaml.XamlType> lub <xref:System.Xaml.XamlMember>, lub wywoływania <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.  
  
 Należy pamiętać, że jeśli dostęp do niektórych aspektów WPF XAML czysty perspektywy strumienia węzłów XAML, niektóre funkcje framework WPF mogą nie mieć działał jeszcze. Na przykład szablony formantów WPF nie są jeszcze stosowane. W związku z tym jeśli dostęp do właściwości, która w czasie wykonywania mogą być wypełniane przy użyciu drzewa wizualnego pełnych może zobaczyć tylko wartość właściwości, która odwołuje się do szablonu. Kontekst usługi dostępne w celu rozszerzenia znaczników WPF może nie być również dokładne, jeśli z sytuacji z systemem innym niż środowisko uruchomieniowe i może spowodować wystąpienie wyjątków podczas próby zapisu wykresu obiektów.  
  
## <a name="xaml-and-assembly-loading"></a>XAML i ładowania zestawu  
 Ładowania dla języka XAML i .NET Framework XAML Services zestawu integruje się z pojęcie zdefiniowane CLR <xref:System.AppDomain>. Kontekst schematu XAML interpretuje jak ładowanie zestawów albo znaleźć typów w czasie wykonywania lub projektu, oparte na korzystanie z <xref:System.AppDomain> i innych czynników. Logika różni się nieco w zależności od tego, czy XAML jest luźno XAML dla czytnika XAML, jest XAML skompilowany do biblioteki DLL przez `XamlBuildTask`, lub BAML wygenerowane przez jego WPF `PresentationBuildTask`.  
  
 Kontekst schematu WPF XAML integruje się z modelem aplikacji WPF, który z kolei używa <xref:System.AppDomain> i innych czynników, które są szczegóły implementacji WPF.  
  
#### <a name="xaml-reader-input-loose-xaml"></a>Dane wejściowe czytnika XAML (utracić XAML)  
  
1.  Kontekst schematu XAML iteruje <xref:System.AppDomain> aplikacji wyszukiwanie już załadowany zestaw, który dopasowuje wszystkie aspekty nazwę, zaczynając od najbardziej ostatnio załadowanego zestawu. Jeśli zostanie znaleziony dopasowanie, ten zestaw jest używany do rozpoznawania.  
  
2.  W przeciwnym razie wartość jednego z poniższych oparte na CLR <xref:System.Reflection.Assembly> interfejsu API są używane do załadowania zestawu:  
  
    -   Jeśli nazwa kwalifikowana jest w mapowaniu, wywołanie <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> w kwalifikowanej nazwie.  
  
    -   Jeśli w poprzednim kroku nie powiedzie się, użyj krótka nazwa (i token klucza publicznego Jeśli istnieje) do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
    -   Jeśli nazwa jest niekwalifikowane w mapowaniu, wywołanie <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
#### <a name="xamlbuildtask"></a>XamlBuildTask  
 `XamlBuildTask`Służy do [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)] i [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)].  
  
 Należy pamiętać, że za pomocą odwołań do zestawów `XamlBuildTask` są zawsze w pełni kwalifikowana.  
  
1.  Wywołanie <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> w kwalifikowanej nazwie.  
  
2.  Jeśli w poprzednim kroku nie powiedzie się, użyj krótka nazwa (i token klucza publicznego Jeśli istnieje) do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)  
 Istnieją dwa aspekty ładowania zestawu dla BAML: podczas ładowania początkowego zestawu, który zawiera BAML jako składnik, a ładowanie zestawów zapasowego typu dla wszystkich typów odwołuje się do produkcji BAML.  
  
##### <a name="assembly-load-for-initial-markup"></a>Ładowanie zestawu dla znacznika początkowego:  
 Odwołanie do zestawu do załadowania znaczników z jest zawsze niekwalifikowane.  
  
1.  Kontekst schematu WPF XAML iteruje <xref:System.AppDomain> aplikacji WPF, wyszukiwanie już załadowany zestaw, który dopasowuje wszystkie aspekty nazwę, zaczynając od najbardziej ostatnio załadowanego zestawu. Jeśli zostanie znaleziony dopasowanie, ten zestaw jest używany do rozpoznawania.  
  
2.  Jeśli w poprzednim kroku nie powiedzie się, użyj krótka nazwa (i token klucza publicznego Jeśli istnieje) do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
##### <a name="assembly-references-by-baml-types"></a>Odwołania do zestawów przez typy BAML:  
 Odwołania do zestawów dla typów używanych w środowisku produkcyjnym BAML są zawsze FQDN jako dane wyjściowe zadania kompilacji.  
  
1.  Kontekst schematu WPF XAML iteruje <xref:System.AppDomain> aplikacji WPF, wyszukiwanie już załadowany zestaw, który dopasowuje wszystkie aspekty nazwę, zaczynając od najbardziej ostatnio załadowanego zestawu. Jeśli zostanie znaleziony dopasowanie, ten zestaw jest używany do rozpoznawania.  
  
2.  W przeciwnym razie wartość jednej z następujących metod jest używana do załadowania zestawu:  
  
    -   Wywołanie <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> w kwalifikowanej nazwie.  
  
    -   Krótka nazwa + publicznego tokenu kombinacja były zgodne z zestawem BAML został załadowany z, należy użyć tego zestawu.  
  
    -   Użyj krótką nazwę + token klucza publicznego do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie struktur i koncepcji strumienia węzłów XAML](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
