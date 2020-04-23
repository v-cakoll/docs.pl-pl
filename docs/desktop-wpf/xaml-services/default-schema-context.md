---
title: Domyślny kontekst schematu XAML i kontekst schematu WPF XAML
ms.date: 03/30/2017
ms.assetid: 04e06a15-09b3-4210-9bdf-9a64c2eccb83
ms.openlocfilehash: 2e92372de61230a98a02282cc28fc3f479cd94eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071865"
---
# <a name="default-xaml-schema-context-and-wpf-xaml-schema-context"></a>Domyślny kontekst schematu XAML i kontekst schematu WPF XAML
Kontekst schematu XAML jest jednostką koncepcyjną, która kwalifikuje sposób, w jaki produkcja XAML, która używa określonego słownictwa XAML, współdziała z zachowaniem zapisu obiektu, w tym jak mapowanie typów jest rozpoznawane, jak zestawy są ładowane, jak interpretowane są określone ustawienia czytnika i modułu zapisującego. W tym temacie opisano funkcje usług .NET XAML i skojarzony domyślny kontekst schematu XAML, który jest oparty na systemie typu CLR. W tym temacie opisano również kontekst schematu XAML, który jest używany dla WPF.

## <a name="default-xaml-schema-context"></a>Domyślny kontekst schematu XAML

Usługi .NET XAML — implementuje i używa domyślnego kontekstu schematu XAML. Domyślne zachowanie kontekstu schematu XAML nie zawsze jest <xref:System.Xaml.XamlSchemaContext> w pełni widoczne w interfejsie API klasy. Jednak w wielu przypadkach zachowanie, na które wpływa domyślny kontekst schematu XAML, jest obserwowalne za pośrednictwem wspólnego interfejsu API systemu typu XAML, takiego jak członkowie <xref:System.Xaml.XamlMember> lub <xref:System.Xaml.XamlType>, lub za pośrednictwem interfejsów API udostępnianych na czytnikach XAML i modułach zapisu XAML, które używają domyślnego kontekstu schematu XAML.

Można <xref:System.Xaml.XamlSchemaContext> utworzyć, który hermetyzuje domyślne <xref:System.Xaml.XamlSchemaContext> zachowanie, wywołując konstruktora. Spowoduje to jawne utworzenie domyślnego kontekstu schematu XAML. Ten sam domyślny kontekst schematu XAML jest tworzony niejawnie, jeśli zainicjować czytnik XAML lub moduł <xref:System.Xaml.XamlSchemaContext> zapisujący XAML przy użyciu interfejsów API, które jawnie nie przyjmują parametru wejściowego.

Domyślny kontekst schematu XAML opiera się na odbicie CLR dla jego zachowanie mapowania typu. Obejmuje to badanie definiującego <xref:System.Type>CLR <xref:System.Reflection.PropertyInfo> <xref:System.Reflection.MethodInfo>i pokrewne lub . Ponadto atrybucja CLR na typy lub elementy członkowskie jest używana w celu wypełnienia specyfiki dla typu XAML lub XAML informacje o członkowi, który używa typu kopii CLR. Domyślny kontekst schematu XAML nie wymaga technik rozszerzenia `Invoker` systemu typu, takich jak wzorzec, ponieważ niezbędne informacje są dostępne z systemu typu CLR.

W przypadku logiki ładowania zestawu domyślny kontekst schematu XAML opiera się głównie na wartościach zestawu podanych w mapowaniach przestrzeni nazw XAML. Ponadto <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A> można podpowiadać zestawu do załadowania, dla scenariuszy, takich jak ładowanie typów wewnętrznych.

## <a name="wpf-xaml-schema-context"></a>Kontekst schematu XAML WPF

Kontekst schematu WPF XAML jest opisany w tym temacie, ponieważ implementacja WPF stanowi interesującą ilustrację rodzajów funkcji, które można wprowadzić, implementując kontekst schematu XAML innych niż domyślny. Ponadto koncepcja kontekstu schematu XAML nie jest omówiona bardzo dużo w dokumentacji WPF, która dotyczy WPF XAML; zachowanie, które włącza kontekst schematu XAML może być w pełni zrozumiałe tylko wtedy, gdy jest zintegrowane z omówienia, jak działa domyślny kontekst schematu XAML. Kontekst schematu WPF XAML implementuje następujące zachowanie.

**Zastąpienia odnośne:** WPF WPF ma kilka modeli zawartości dla XAML, gdzie istnieją <xref:System.Windows.Markup.ContentPropertyAttribute> właściwości zawartości XAML, które działają bez przypisane. <xref:System.Xaml.XamlType.LookupContentProperty%2A>overrides dla WPF implementuje to zachowanie.

**Odroczenie dla wyrażeń WPF:** WPF WPF zawiera kilka klas wyrażeń, które odraczają wartość, dopóki kontekst środowiska uruchomieniowego nie będzie dostępny. Ponadto rozszerzenie szablonu jest zachowanie środowiska uruchomieniowego, który opiera się na technik odroczenia.

**Wpisz optymalizacje wyszukiwania systemu:** WPF WPF ma obszerne słownictwo XAML i model obiektów, w tym definicji elementów członkowskich klasy podstawowej, które dziedziczą dosłownie setki klas zdefiniowanych w WPF. Ponadto sam WPF jest rozłożony na kilka zestawów. WPF WPF optymalizuje jego wyszukiwania typu za pomocą tabel odnośników i innych technik. Zapewnia to poprawę wydajności w stosunku do domyślnego kontekstu schematu XAML i jego wyszukiwania typu opartego na programie CLR. W przypadkach, gdy typy nie istnieją w tabeli odnośnictwa, zachowanie używa technik kontekstu schematu XAML, które są podobne do domyślnego kontekstu schematu XAML.

**Rozszerzenie XamlType i XamlMember:** WPF WPF rozszerza pojęcia właściwości z właściwości zależności i koncepcji zdarzeń z kierowanych zdarzeń. Aby nadać tym pojęciom lepszą widoczność <xref:System.Xaml.XamlType> dla <xref:System.Xaml.XamlMember>operacji przetwarzania XAML, WPF rozszerza i , i dodaje właściwości wewnętrzne, które raport właściwości zależności i routowanej właściwości zdarzeń.

### <a name="accessing-the-wpf-xaml-schema-context"></a>Uzyskiwanie dostępu do kontekstu schematu XAML WPF

Jeśli używasz technik XAML, które są <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> oparte <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>na WPF lub kontekst schematu WPF XAML jest już używany w tych czytników XAML i xaml modułu zapisującego implementacje.

Jeśli używasz innych implementacji czytnika XAML lub modułu zapisującego XAML, które nie są inicjalizowania z kontekstem schematu WPF XAML, możesz uzyskać działający kontekst schematu WPF XAML z <xref:System.Windows.Markup.XamlReader.GetWpfSchemaContext%2A?displayProperty=nameWithType>. Następnie można użyć tej wartości jako inicjowania dla innych interfejsów <xref:System.Xaml.XamlSchemaContext>API, które używają . Na przykład można <xref:System.Xaml.XamlXmlReader.%23ctor%2A> wywołać inicjalizacji i przekazać kontekst schematu WPF XAML. Lub można użyć kontekstu schematu WPF XAML dla operacji systemu typu XAML. Może to obejmować inicjowanie konstrukcji <xref:System.Xaml.XamlType> lub <xref:System.Xaml.XamlMember>, lub wywołanie <xref:System.Xaml.XamlSchemaContext.GetXamlType%2A?displayProperty=nameWithType>.

Należy zauważyć, że jeśli dostęp do niektórych aspektów WPF XAML z czystego xaml perspektywy strumienia węzła, niektóre możliwości struktury WPF może nie działał jeszcze. Na przykład szablony WPF dla formantów nie są jeszcze stosowane. W związku z tym, jeśli dostęp do właściwości, która w czasie wykonywania może być wypełniona pełnym drzewem wizualnym, może być widoczna tylko wartość właściwości, która odwołuje się do szablonu. Kontekst usługi przewidziane dla WPF rozszerzeń znaczników może również nie być dokładne, jeśli są dostarczane z sytuacji nie-runtime i może spowodować wyjątki podczas próby zapisania wykresu obiektu.

## <a name="xaml-and-assembly-loading"></a>Ładowanie XAML i złożenia

Ładowanie zestawu dla usług XAML i .NET XAML integruje się z koncepcją zdefiniowaną przez CLR <xref:System.AppDomain>. Kontekst schematu XAML interpretuje sposób ładowania zestawów lub znajdowania typów w czasie wykonywania <xref:System.AppDomain> lub czasie projektowania, na podstawie użycia i innych czynników. Logika jest nieco inna w zależności od tego, czy XAML jest luźny XAML dla `XamlBuildTask`czytnika XAML, jest XAML skompilowany do biblioteki DLL przez , czy jest BAML generowane przez `PresentationBuildTask`WPF.

Kontekst schematu XAML dla WPF integruje się z modelem <xref:System.AppDomain> aplikacji WPF, który z kolei używa, a także innych czynników, które są szczegóły implementacji WPF.

#### <a name="xaml-reader-input-loose-xaml"></a>Wejście czytnika XAML (luźny kod XAML)

01. Kontekst schematu XAML iteruje <xref:System.AppDomain> za pośrednictwem aplikacji, szukając już załadowanego zestawu, który pasuje do wszystkich aspektów nazwy, począwszy od ostatnio załadowanego zestawu. Jeśli zostanie znaleziony dopasowanie, ten zestaw jest używany do rozpoznawania.

02. W przeciwnym razie do załadowania zestawu <xref:System.Reflection.Assembly> używana jest jedna z następujących technik opartych na interfejsie API CLR:

    - Jeśli nazwa jest kwalifikowana w <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> mapowaniu, wywołanie nazwy kwalifikowanej.

    - Jeśli poprzedni krok nie powiedzie się, użyj krótkiej nazwy <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>(i tokenu klucza publicznego, jeśli jest obecny), aby wywołać .

    - Jeśli nazwa nie ma kwalifikacji w <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>mapowaniu, zadzwoń .

#### <a name="xamlbuildtask"></a>XamlBuildTask

`XamlBuildTask`jest używany dla Windows Communication Foundation (WCF) i Windows Workflow Foundation.

Należy zauważyć, że `XamlBuildTask` odwołania do zestawu za pośrednictwem są zawsze w pełni kwalifikowane.

1. Zadzwoń <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> po kwalifikowaną nazwę.

2. Jeśli poprzedni krok nie powiedzie się, użyj krótkiej nazwy <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>(i tokenu klucza publicznego, jeśli jest obecny), aby wywołać .

#### <a name="baml-presentationbuildtask"></a>BAML (PresentationBuildTask)

Istnieją dwa aspekty ładowania zestawu dla BAML: ładowanie początkowego zestawu, który zawiera BAML jako składnik, i ładowanie zestawów podkładowych typu dla wszystkich typów, do których odwołuje się produkcja BAML.

##### <a name="assembly-load-for-initial-markup"></a>Obciążenie złożenia dla znaczników początkowych:

Odwołanie do zestawu, aby załadować znaczników z jest zawsze bez zastrzeżeń.

1. Kontekst schematu WPF XAML iteruje za pośrednictwem <xref:System.AppDomain> aplikacji WPF, szukając już załadowanego zestawu, który pasuje do wszystkich aspektów nazwy, począwszy od ostatnio załadowanego zestawu. Jeśli zostanie znaleziony dopasowanie, ten zestaw jest używany do rozpoznawania.

2. Jeśli poprzedni krok nie powiedzie się, użyj krótkiej nazwy <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>(i tokenu klucza publicznego, jeśli jest obecny), aby wywołać .

##### <a name="assembly-references-by-baml-types"></a>Odwołania do zestawu według typów BAML:

Odwołania do zestawu dla typów używanych w produkcji BAML są zawsze w pełni kwalifikowane, jako dane wyjściowe zadania kompilacji.

01. Kontekst schematu WPF XAML iteruje za pośrednictwem <xref:System.AppDomain> aplikacji WPF, szukając już załadowanego zestawu, który pasuje do wszystkich aspektów nazwy, począwszy od ostatnio załadowanego zestawu. Jeśli zostanie znaleziony dopasowanie, ten zestaw jest używany do rozpoznawania.

02. W przeciwnym razie do załadowania złożenia jest używana jedna z następujących technik:

    - Zadzwoń <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> po kwalifikowaną nazwę.
  
    - Jeśli kombinacja tokenu klucza krótkiego + klucz publiczny jest zgodna z zestawem, z którego został załadowany BAML, użyj tego zestawu.

    - Użyj krótkiej nazwy + <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>tokenu klucza publicznego, aby wywołać .

## <a name="see-also"></a>Zobacz też

- [Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML](understanding-xaml-node-stream-structures-and-concepts.md)
