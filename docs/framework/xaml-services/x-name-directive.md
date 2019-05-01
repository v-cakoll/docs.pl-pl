---
title: x:Name — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- x:Name
- xName
- Name
helpviewer_keywords:
- x:Name attribute [XAML Services]
- XAML [XAML Services], x:Name attribute
- Name attribute in XAML [XAML Services]
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
ms.openlocfilehash: d25c8500250411083e9fb6b33b3f743e5cd103c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796529"
---
# <a name="xname-directive"></a>x:Name — dyrektywa
Jednoznacznie identyfikuje elementy zdefiniowane XAML XAML namescope. Zakresy nazw XAML i ich modeli unikatowości mogą być stosowane do wystąpień obiektów platform zapewniają interfejsy API lub zaimplementować zachowania uzyskujących dostęp do wykresu obiektu utworzone XAML w czasie wykonywania.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Ciąg, który jest zgodny z ograniczeniami [xamlname — gramatyka](xamlname-grammar.md).|  
  
## <a name="remarks"></a>Uwagi  
 Po `x:Name` jest stosowany do struktury firmy kopii modelu programowania, nazwa jest odpowiednikiem zmiennej, która zawiera odwołanie do obiektu lub wystąpienie zwrócone przez konstruktora.  
  
 Wartość `x:Name` użycie dyrektywy muszą być unikatowe w obrębie XAML namescope. Domyślnie gdy jest używana przez .NET Framework XAML usług API głównej namescope XAML jest zdefiniowana na element główny XAML pojedynczego procesu produkcji XAML i obejmuje elementy, które są zawarte w tym środowisku produkcyjnym XAML. Dodatkowe dyskretnych zakresy nazw XAML, które mogą wystąpić w ramach pojedynczego procesu produkcji XAML mogą być definiowane przez środowisk dla określonych scenariuszy. W środowisku WPF nowe zakresy nazw XAML są na przykład zdefiniowane i utworzony przez dowolny szablon, który jest też definiowany w produkcji XAML. Aby uzyskać więcej informacji na temat zakresy nazw XAML (ale odpowiednie dla wielu koncepcji namescope XAML napisane dla WPF), zobacz [zakresy WPF XAML nazw](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Ogólnie rzecz biorąc `x:Name` nie powinny być stosowane w sytuacjach, które także używają `x:Key`. Implementacje XAML przez określone z istniejącymi strukturami wprowadza pojęcia podstawienia między `x:Key` i `x:Name`, ale nie jest zalecanym rozwiązaniem. .NET framework XAML Services nie obsługuje takie pojęcia podstawienia podczas obsługi informacji klucza/nazwy, takie jak <xref:System.Windows.Markup.INameScope> lub <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Zasady permittance z `x:Name` a także Sprawiedliwości unikatowość nazwy potencjalnie są definiowane przez określonych środowisk wykonawczych. Jednak może być używany z usługami programu .NET Framework XAML, definicje framework XAML namescope unikatowości powinny być zgodne z definicją <xref:System.Windows.Markup.INameScope> informacje przedstawione w tej dokumentacji i należy używać tych samych zasad dotyczące miejsca informacje są stosowane. Na przykład [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementacji różnych elementów kodu znaczników są podzielone na oddzielne <xref:System.Windows.NameScope> zakresów adresów, takich jak słowniki zasobów drzewo logiczne utworzone przez poziomu strony XAML, szablonów i inne odroczone zawartości, a następnie wymusza XAML Unikatowość nazwy w ramach każdej z tych zakresy nazw XAML.  
  
 Dla niestandardowych typów używających składników zapisywania obiektu .NET Framework XAML Services XAML właściwość mapujący do `x:Name` na typ można ustanowić lub zmienione. Definiowanie zachowania, odwołując się do nazwy właściwości do mapowania z <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> w kodzie definicji typu.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> jest to atrybut poziomu typu.  
  
 Using.NET Framework XAML usług, logiki zapasowy obsługi namescope XAML można zdefiniować w sposób niezależny od framework implementując <xref:System.Windows.Markup.INameScope> interfejsu.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użytkowania WPF  
 W obszarze Konfiguracja standardową kompilacją [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplikacji, która używa XAML, klasy częściowe i związane z kodem, określony `x:Name` staje się nazwę pola, który jest tworzony w źródłowym kodu, gdy [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jest przetwarzany przez znacznik Zadanie kompilacji w kompilacji, a to pole zawiera odwołanie do obiektu. Domyślnie pole utworzony jest wewnętrzny. Dostęp do pola można zmienić, określając [x: fieldmodifier — atrybut](x-fieldmodifier-directive.md). W programie WPF i Silverlight sekwencji jest definiuje kompilacji znaczników i nazwy pola w częściowej klasy, ale wartość jest początkowo pusta. Następnie wygenerowanej metody o nazwie `InitializeComponent` jest wywoływana z w ramach konstruktora klasy. `InitializeComponent` składa się z `FindName` wywołań przy użyciu wszystkich `x:Name` wartości, które istnieją w zdefiniowanych XAML części klasy częściowej jako dane wejściowe ciągów. Wartości zwracane są przypisywany do odwołania podobnie nazwanego pola do wypełnienia wartości pól z obiektami, które zostały utworzone przy użyciu XAML podczas analizowania. Wykonanie `InitializeComponent` umożliwiać odwołania w czasie wykonywania obiektu programu graph przy użyciu `x:Name` / Nazwa pola bezpośrednio, zamiast wywoływać `FindName` jawnie w dowolnej chwili należy odwołanie do obiektu zdefiniowany XAML.  
  
 Dla WPF jest przeznaczony dla aplikacji, która używa programu Microsoft Visual Basic i obejmuje pliki XAML z `Page` akcji kompilacji, właściwości oddzielne odwołania jest tworzony podczas kompilacji, który dodaje `WithEvents` — słowo kluczowe do wszystkich elementów, które mają `x:Name`, które obsługują `Handles` składnia delegatów obsługi zdarzeń. Ta właściwość zawsze jest publiczny. Aby uzyskać więcej informacji, zobacz [Visual Basic i obsługa zdarzeń WPF](../wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` jest używany przez procesor WPF XAML można zarejestrować nazwę do XAML namescope w czasie ładowania, nawet w przypadku przypadków, gdy strona nie jest kompilowana do znaczników przez akcje kompilacji (na przykład luźne XAML słownika zasobów). Jest jednym z powodów to zachowanie, ponieważ `x:Name` potencjalnie jest wymagany w przypadku <xref:System.Windows.Data.Binding.ElementName%2A> powiązania. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](../wpf/data/data-binding-overview.md).  
  
 Jak wspomniano wcześniej, `x:Name` (lub `Name`) nie należy stosować w sytuacjach, które także używają `x:Key`. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> Ma specjalne zachowanie Definiowanie sama jako XAML namescope, ale zwracając nie zaimplementowano lub wartości null dla <xref:System.Windows.Markup.INameScope> interfejsów API jako sposób wymuszania to zachowanie. Jeśli WPF XAML analizator składni napotka `Name` lub `x:Name` w XAML zdefiniowane <xref:System.Windows.ResourceDictionary>, nazwa nie jest dodawana do wszelkich namescope XAML. Próby znalezienia tej nazwy z dowolnego namescope XAML i `FindName` metody nie będzie zwracał prawidłowe wyniki.  
  
### <a name="xname-and-name"></a>x: Name i nazwa  
 Wiele scenariuszy aplikacji WPF można uniknąć jakiekolwiek wykorzystanie `x:Name` atrybutu, ponieważ `Name` właściwość zależności jako określone w domyślnej przestrzeni nazw XAML dla kilku ważnych klas bazowych takich jak <xref:System.Windows.FrameworkElement> i <xref:System.Windows.FrameworkContentElement> spełnia wymagania tego samego celu. Nadal istnieją pewne typowe scenariusze XAML i WPF gdzie kodu dostępu do elementu bez `Name` właściwości na poziomie framework jest ważne. Na przykład, nie obsługują niektórych animacji i scenorysu klasy obsługi `Name` właściwości, ale często muszą się odwoływać w kodzie w celu kontrolowania animacji. Należy określić `x:Name` jako atrybut na osi czasu i przekształceń, które są tworzone w XAML, jeśli zamierzasz później odwołać je z poziomu kodu.  
  
 Jeśli <xref:System.Windows.FrameworkElement.Name%2A> jest dostępna jako właściwość w klasie, <xref:System.Windows.FrameworkElement.Name%2A> i `x:Name` mogą być używane zamiennie jako atrybuty, ale spowoduje wyjątek analizy, jeśli są określone oba w tym samym elemencie. Jeśli XAML jest skompilowany kod znaczników, wyjątek wystąpi w kompilacji znaczników, przeciwnym razie wystąpi przy ładowaniu.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> można ustawić przy użyciu składni atrybutu XAML i kodu za pomocą <xref:System.Windows.DependencyObject.SetValue%2A>; należy jednak pamiętać, to ustawienie <xref:System.Windows.FrameworkElement.Name%2A> właściwości w kodzie nie tworzy odwołanie do pola reprezentatywny w ramach XAML namescope w większości przypadków, w którym XAML jest już załadowane. Zamiast ustawieniem <xref:System.Windows.FrameworkElement.Name%2A> w kodzie, należy użyć <xref:System.Windows.NameScope> metody z kodu względem odpowiednich namescope.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> można również ustawić za pomocą składni elementu właściwości, za pomocą tekst wewnętrzny, ale jest rzadko. Z kolei `x:Name` nie można ustawić w składni elementu właściwości XAML lub kodu za pomocą <xref:System.Windows.DependencyObject.SetValue%2A>; tylko można ustawić, za pomocą składni atrybutów obiektów, ponieważ jest on dyrektywy.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użytkowania Silverlight  
 `x:Name` dla programu Silverlight jest opisane osobno. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Drzewa w WPF](../wpf/advanced/trees-in-wpf.md)
