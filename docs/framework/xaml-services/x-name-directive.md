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
ms.openlocfilehash: 7fcb7fe767e892109e48c5e56db26b5943b6ef13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xname-directive"></a>x:Name — dyrektywa
Identyfikuje elementy zdefiniowane XAML XAML namescope. XAML namescopes i ich modeli unikatowości mogą być stosowane do wystąpień obiektów, gdy platform zapewniają interfejsów API, lub zaimplementuj zachowania, które uzyskują dostęp do wykres obiektu utworzone XAML w czasie wykonywania.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Name="XAMLNameValue".../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Ciąg, który odpowiada ograniczeń [xamlname — gramatyka](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
  
## <a name="remarks"></a>Uwagi  
 Po `x:Name` jest stosowany do struktury firmy kopii model programowania, nazwy jest odpowiednikiem zmiennej, która zawiera odwołanie do obiektu lub wystąpienia zwrócony przez konstruktora.  
  
 Wartość `x:Name` użycie dyrektywy muszą być unikatowe w obrębie XAML namescope. Domyślnie gdy jest używana przez .NET Framework XAML Services API głównej namescope XAML elementu głównego XAML pojedynczego produkcji XAML nie jest zdefiniowany i obejmują elementy, które są zawarte w tym środowisku produkcyjnym XAML. Dodatkowe odrębny namescopes XAML, który może wystąpić w ramach pojedynczego produkcji XAML mogą zostać zdefiniowane przez platformy w celu rozwiązania określonych scenariuszy. Na platformie WPF, nowe namescopes XAML są na przykład zdefiniowany i utworzone przez dowolnego szablonu, który jest też definiowany w produkcji XAML. Aby uzyskać więcej informacji na temat namescopes XAML (ale zastosowanie w przypadku wielu pojęcia namescope XAML napisane dla WPF), zobacz [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Ogólnie rzecz biorąc `x:Name` nie powinny być stosowane w sytuacjach, które także używają `x:Key`. Implementacje XAML przez określonych platform istniejących wprowadziły pojęcia podstawienia między `x:Key` i `x:Name`, ale nie jest zalecanym rozwiązaniem. Usługi XAML .NET framework nie obsługuje takich pojęcia podstawienia podczas obsługi nazwy/kluczowych informacji takich jak <xref:System.Windows.Markup.INameScope> lub <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Zasady permittance z `x:Name` oraz wymuszania unikatowość nazwy potencjalnie są definiowane przez określonych platform implementującej. Jednak może być używany z usługami .NET Framework XAML, definicje framework XAML namescope unikatowości powinny być zgodne z definicją <xref:System.Windows.Markup.INameScope> informacji w tej dokumentacji i należy używać tych samych zasad dotyczące miejsca informacje są stosowane. Na przykład [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementacji dzieli różnych elementów kodu znaczników w oddzielne <xref:System.Windows.NameScope> zakresów, takich jak słowniki zasobów drzewa logicznego utworzonych przez poziomu strony XAML, szablonów i innych odroczone zawartości, a następnie wymusza XAML Unikatowość nazwy w każdej z tych namescopes XAML.  
  
 Dla niestandardowych typów, które używają zapisywania obiektów platformy .NET Framework XAML Services XAML, właściwość mapujący do `x:Name` na typ można ustanowić lub zmienione. Zdefiniuj to zachowanie odwołując nazwa właściwości do mapowania z <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> w kodzie definicji typu.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> jest to atrybut poziomu typu.  
  
 Usługi XAML Framework Using.NET, logikę zapasowy XAML namescope obsługi można zdefiniować w sposób niezależny od framework zaimplementowanie <xref:System.Windows.Markup.INameScope> interfejsu.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 W obszarze Konfiguracja standardowego kompilacji dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplikacji, która używa XAML klasy częściowe i związane z kodem, określony `x:Name` staje się nazwa pola, które jest tworzony w podstawowych kodu, gdy [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jest przetwarzany przez znacznik zadania kompilacji kompilacji i że pole zawiera odwołanie do obiektu. Domyślnie pole utworzone jest wewnętrzny. Dostępu do pola można zmienić, określając [x: fieldmodifier — atrybut](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md). W podsystemie WPF i Silverlight sekwencji jest definiuje kompilacji znaczników oraz nazwy pól w częściowej klasy, ale wartość jest początkowo pusta. Następnie wygenerowanego metodę o nazwie `InitializeComponent` jest wywołane z wnętrza konstruktora klasy. `InitializeComponent` składa się z `FindName` wywołuje przy użyciu `x:Name` wartości znajdujące się w części zdefiniowanych XAML klasy częściowej jako danych wejściowych ciągów. Wartości zwracane są następnie przypisywane do odwołania pola o nazwie podobnej do wypełnienia wartości pól z obiektami, które zostały utworzone z XAML podczas analizowania. Wykonywanie `InitializeComponent` umożliwiać odniesienia w czasie wykonywania obiektu wykresu przy użyciu `x:Name` / Nazwa pola bezpośrednio, zamiast czekać, aż do wywołania `FindName` jawnie w dowolnej chwili należy odwołanie do obiektu zdefiniowany w języku XAML.  
  
 Dla WPF aplikacji korzystającej z programu Microsoft Visual Basic elementów docelowych i obejmuje pliki XAML z `Page` Akcja kompilacji, właściwości oddzielne odwołania jest tworzony podczas kompilacji, który dodaje `WithEvents` — słowo kluczowe do wszystkich elementów, które mają `x:Name`, aby obsługiwać `Handles` składnię delegatów obsługi zdarzeń. Ta właściwość zawsze jest publiczny. Aby uzyskać więcej informacji, zobacz [Visual Basic i obsługi zdarzeń WPF](../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` jest używana przez procesor WPF XAML do rejestrowania nazwy do XAML namescope w czasie ładowania, nawet w przypadkach, gdy strona nie jest skompilowany znaczników przez akcje kompilacji (na przykład utracić XAML słownik zasobów). Jest jednym z powodów tego zachowania, ponieważ `x:Name` jest potencjalnie potrzebne <xref:System.Windows.Data.Binding.ElementName%2A> powiązania. Aby uzyskać więcej informacji, zobacz [omówienie powiązania danych](../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Jak wspomniano wcześniej, `x:Name` (lub `Name`) nie powinny być stosowane w sytuacjach, które także używają `x:Key`. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> Ma specjalnego zachowania Definiowanie się jako XAML namescope, ale przekazywania nie zaimplementowano lub wartości null dla <xref:System.Windows.Markup.INameScope> interfejsów API, aby wymusić to zachowanie. Jeśli wystąpi analizator WPF XAML `Name` lub `x:Name` w XAML zdefiniowane <xref:System.Windows.ResourceDictionary>, nazwa nie została dodana do dowolnego namescope XAML. Próby znalezienia tej nazwy z dowolnym namescope XAML i `FindName` metod nie zwróci prawidłowe wyniki.  
  
### <a name="xname-and-name"></a>x: nazwy i nazwy  
 Wiele scenariuszy, w aplikacji WPF można uniknąć jakimkolwiek użyciem `x:Name` atrybutu, ponieważ `Name` właściwości zależności jako określone w domyślnej przestrzeni nazw XAML kilka ważnych klas podstawowych takich jak <xref:System.Windows.FrameworkElement> i <xref:System.Windows.FrameworkContentElement> spełnia wymagania tego samego celu. Nadal istnieją pewne typowe scenariusze XAML i WPF gdzie kodu dostępu do elementu bez `Name` właściwości na poziomie framework jest ważne. Na przykład nie obsługują niektórych animacji i scenorysu klasy obsługi `Name` właściwości, ale często muszą odwoływać się w kodzie w celu kontrolowania animacji. Należy określić `x:Name` jako atrybut na osi czasu i transformacje, które są tworzone w języku XAML, jeśli zamierzasz później odwoływać je z kodu.  
  
 Jeśli <xref:System.Windows.FrameworkElement.Name%2A> jest dostępna jako właściwość klasy, <xref:System.Windows.FrameworkElement.Name%2A> i `x:Name` mogą być używane zamiennie jako atrybuty, ale spowoduje wyjątek analizy, jeśli określono oba w tym samym elemencie. XAML w przypadku kompilacji znaczników, wyjątek zostanie przeprowadzona w dniu kompilacji znaczników, w przeciwnym razie wystąpi na obciążenia.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> można ustawić za pomocą składni atrybutu XAML w kodu za pomocą <xref:System.Windows.DependencyObject.SetValue%2A>; należy jednak pamiętać ustawienie <xref:System.Windows.FrameworkElement.Name%2A> właściwości w kodzie nie tworzy odwołania pola przedstawiciela w XAML namescope w większości przypadków, w którym XAML jest już załadowane. Zamiast ustawiania <xref:System.Windows.FrameworkElement.Name%2A> w kodzie, użyj <xref:System.Windows.NameScope> metody z kodu przed namescope odpowiednie.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> można również ustawić za pomocą składni elementu właściwości z tekstu wewnętrznego, ale jest rzadko. Z kolei `x:Name` nie można ustawić w składni elementu właściwości XAML lub kodu za pomocą <xref:System.Windows.DependencyObject.SetValue%2A>; można tylko ustawić, przy użyciu składni atrybutu na obiektach, ponieważ jest on dyrektywy.  
  
## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użycia programu Silverlight  
 `x:Name` dla programu Silverlight jest udokumentowany oddzielnie. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka (platformy Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>  
 [Drzewa w WPF](../../../docs/framework/wpf/advanced/trees-in-wpf.md)
