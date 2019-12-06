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
ms.openlocfilehash: d17d977384962980839fbe2b2c0a4708412d403d
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837223"
---
# <a name="xname-directive"></a>x:Name — dyrektywa
Jednoznacznie identyfikuje elementy zdefiniowane w języku XAML w namescope języka XAML. Zakresy nazw WPF języka XAML i ich unikalne modele można stosować do obiektów skonkretyzowanych, gdy struktury zapewniają interfejsy API lub implementują zachowania, które uzyskują dostęp do grafu obiektów utworzonych w języku XAML w czasie wykonywania.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Ciąg, który jest zgodny z ograniczeniami [gramatyki XamlName](xamlname-grammar.md).|  
  
## <a name="remarks"></a>Uwagi  
 Po zastosowaniu `x:Name` do modelu programowania zapasowego platformy, nazwa jest równoważna zmiennej, która zawiera odwołanie do obiektu lub wystąpienie zwrócone przez konstruktora.  
  
 Wartość użycia dyrektywy `x:Name` musi być unikatowa w obrębie namescope języka XAML. Domyślnie, gdy jest używany przez .NET Framework interfejsu API usług XAML, podstawowy namescope XAML jest zdefiniowany w elemencie głównym XAML pojedynczej produkcji XAML i obejmuje elementy, które są zawarte w tej produkcji XAML. Dodatkowe dyskretne Zakresy nazw WPF języka XAML, które mogą wystąpić w ramach jednej produkcji XAML, mogą być definiowane przez platformy w celu rozwiązania określonych scenariuszy. Na przykład w WPF nowe zakresy nazw WPF języka XAML są definiowane i tworzone przez każdy szablon, który jest również zdefiniowany w tej produkcji XAML. Aby uzyskać więcej informacji na temat języka XAML Zakresy nazw WPF (na przykład w przypadku wielu koncepcji namescope języka XAML), zobacz [WPF XAML Zakresy nazw WPF](../wpf/advanced/wpf-xaml-namescopes.md).  
  
 Ogólnie rzecz biorąc `x:Name` nie należy stosować w sytuacjach, w których również używane są `x:Key`. Implementacje języka XAML według określonych istniejących platform wprowadziły koncepcje podstawienia między `x:Key` i `x:Name`, ale nie jest to zalecane rozwiązanie. .NET Framework usługi XAML nie obsługują takich koncepcji podstawienia podczas obsługi informacji o nazwach/kluczach, takich jak <xref:System.Windows.Markup.INameScope> lub <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Reguły zezwalania na `x:Name`, a także wymuszanie unikatowości nazwy są potencjalnie zdefiniowane przez określone struktury implementacji. Jednak, aby można było korzystać z usług .NET Framework XAML, definicje struktury języka XAML namescope muszą być zgodne z definicją <xref:System.Windows.Markup.INameScope> informacji w tej dokumentacji i powinny używać tych samych zasad, w których są stosowane informacje. Na przykład implementacja [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] dzieli różne elementy znaczników na oddzielne zakresy <xref:System.Windows.NameScope>, takie jak słowniki zasobów, Drzewo logiczne utworzone przez kod XAML, szablony i inną odroczoną zawartość, a następnie Wymusza unikatowość nazw XAML w ramach każdego z tych Zakresy nazw WPF języka XAML.  
  
 W przypadku typów niestandardowych, które używają .NET Framework modułów zapisujących obiektów XAML usług XAML, właściwość, która mapuje do `x:Name` na typie, może zostać ustanowiona lub zmieniona. Należy zdefiniować to zachowanie, odwołując się do nazwy właściwości, która ma być mapowana na <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> w kodzie definicji typu.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> jest atrybutem na poziomie typu.  
  
 Using.NET Framework XAML Services, logika zapasowa dla obsługi namescope języka XAML można zdefiniować w sposób neutralny w strukturze, implementując interfejs <xref:System.Windows.Markup.INameScope>.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 W ramach standardowej konfiguracji kompilacji dla aplikacji [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], która używa języka XAML, klas częściowych i kodu, określony `x:Name` jest nazwą pola, które jest tworzone w źródłowym kodzie, gdy [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jest przetwarzany przez zadanie kompilacji kompilacji znaczników, a to pole zawiera odwołanie do obiektu. Domyślnie utworzone pole jest polem wewnętrznym. Można zmienić dostęp do pola, określając [atrybut x:FieldModifier —](x-fieldmodifier-directive.md). W WPF i Silverlight, sekwencja polega na tym, że kompilacja adiustacji definiuje i nazwać pole w klasie częściowej, ale wartość jest początkowo pusta. Następnie wygenerowana Metoda o nazwie `InitializeComponent` jest wywoływana z poziomu konstruktora klasy. `InitializeComponent` składa się z `FindName` wywołań przy użyciu każdej wartości `x:Name`, która istnieje w części klasy częściowej zdefiniowanej w kodzie XAML jako ciągów wejściowych. Wartości zwracane są następnie przypisywane do odwołania do pola o podobnej nazwie, aby wypełnić wartości pola obiektami, które zostały utworzone na podstawie analizy XAML. Wykonanie `InitializeComponent` może odwoływać się do grafu obiektu czasu wykonywania przy użyciu nazwy `x:Name`/pola bezpośrednio, a nie do wywołania `FindName` jawnie zawsze, gdy potrzebujesz odwołania do obiektu zdefiniowanego w języku XAML.  
  
 W przypadku aplikacji WPF, która używa obiektów docelowych Visual Basic firmy Microsoft i zawiera pliki XAML z akcją kompilacji `Page`, zostanie utworzona oddzielna Właściwość odwołania podczas kompilacji, która dodaje słowo kluczowe `WithEvents` do wszystkich elementów, które mają `x:Name`, do obsługi składni `Handles` dla delegatów obsługi zdarzeń. Ta właściwość jest zawsze publiczna. Aby uzyskać więcej informacji, zobacz [Visual Basic i obsługa zdarzeń WPF](../wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` jest używany przez procesor WPF XAML w celu zarejestrowania nazwy w namescope języka XAML w czasie ładowania, nawet w przypadku przypadków, gdy strona nie jest skompilowana do oznaczenia przez akcje kompilacji (na przykład luźny kod XAML słownika zasobów). Jedną z przyczyn tego problemu jest to, że `x:Name` może być wymagana do <xref:System.Windows.Data.Binding.ElementName%2A> powiązania. Aby uzyskać szczegółowe informacje, zobacz temat [powiązanie danych — omówienie](../../desktop-wpf/data/data-binding-overview.md).  
  
 Jak wspomniano wcześniej, `x:Name` (lub `Name`) nie należy stosować w sytuacjach, w których także używane są `x:Key`. <xref:System.Windows.ResourceDictionary> [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ma specjalne zachowanie w zakresie definiowania siebie jako namescope języka XAML, ale zwracają wartości nie zaimplementowane lub null dla interfejsów API <xref:System.Windows.Markup.INameScope> jako sposób wymuszenia tego zachowania. Jeśli analizator XAML WPF napotka `Name` lub `x:Name` w <xref:System.Windows.ResourceDictionary>zdefiniowanym przez kod XAML, nazwa nie zostanie dodana do żadnych namescope języka XAML. Podjęto próbę znalezienia tej nazwy z dowolnych namescope języka XAML, a metody `FindName` nie będą zwracać prawidłowych wyników.  
  
### <a name="xname-and-name"></a>x:Name i nazwa  
 Wiele scenariuszy aplikacji WPF może uniknąć użycia atrybutu `x:Name`, ponieważ właściwość zależności `Name` określona w domyślnej przestrzeni nazw XAML dla kilku ważnych klas bazowych, takich jak <xref:System.Windows.FrameworkElement> i <xref:System.Windows.FrameworkContentElement>, spełnia to samo przeznaczenie. Nadal istnieją pewne typowe scenariusze języka XAML i WPF, w przypadku których kod dostępu do elementu bez właściwości `Name` na poziomie struktury jest ważny. Na przykład niektóre klasy obsługi animacji i scenorysu nie obsługują właściwości `Name`, ale często muszą być przywoływane w kodzie w celu kontrolowania animacji. Należy określić `x:Name` jako atrybut na osiach czasu i transformacje, które są tworzone w języku XAML, jeśli zamierzasz odwoływać je od kodu później.  
  
 Jeśli <xref:System.Windows.FrameworkElement.Name%2A> jest dostępny jako właściwość w klasie, <xref:System.Windows.FrameworkElement.Name%2A> i `x:Name` mogą być używane zamiennie jako atrybuty, ale wyjątek analizy spowoduje, że oba te elementy zostaną określone w tym samym elemencie. Jeśli XAML ma skompilowane znaczniki, wyjątek wystąpi podczas kompilowania znaczników, w przeciwnym razie następuje po załadowaniu.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> można ustawić przy użyciu składni atrybutu XAML i kodu przy użyciu <xref:System.Windows.DependencyObject.SetValue%2A>; należy jednak pamiętać, że ustawienie właściwości <xref:System.Windows.FrameworkElement.Name%2A> w kodzie nie powoduje utworzenia odwołania do pola reprezentatywnego w obrębie namescope języka XAML w większości sytuacji, gdy kod XAML jest już załadowany. Zamiast próbować ustawić <xref:System.Windows.FrameworkElement.Name%2A> w kodzie, należy użyć metody <xref:System.Windows.NameScope> z kodu, w odniesieniu do odpowiedniego namescope.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> można również ustawić przy użyciu składni elementu właściwości z tekstem wewnętrznym, ale jest to nietypowe. Z kolei nie można ustawić `x:Name` w składni elementu właściwości XAML ani w kodzie używającym <xref:System.Windows.DependencyObject.SetValue%2A>; można ją ustawić tylko przy użyciu składni atrybutów dla obiektów, ponieważ jest to dyrektywa.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użytkowania Silverlight  
 `x:Name` dla Silverlight jest opisane osobno. Aby uzyskać więcej informacji, zobacz [przestrzeń nazw XAML (x:) Funkcje języka (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Drzewa w WPF](../wpf/advanced/trees-in-wpf.md)
