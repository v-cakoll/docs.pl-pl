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
ms.openlocfilehash: 9f812a49a3217a563be1bd7f1d999b641c28463d
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071452"
---
# <a name="xname-directive"></a>x:Name — dyrektywa

Jednoznacznie identyfikuje elementy zdefiniowane przez XAML w oskopie nazw XAML. Namescopes XAML i ich modele unikatowości mogą być stosowane do obiektów wystąpienia, gdy struktury zapewniają interfejsy API lub implementują zachowania, które uzyskują dostęp do wykresu obiektów utworzonych przez XAML w czasie wykonywania.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|`XAMLNameValue`|Ciąg zgodny z ograniczeniami [gramatyki XamlName](xamlname-grammar.md).|

## <a name="remarks"></a>Uwagi

Po `x:Name` zastosowaniu do modelu programowania kopii struktury, nazwa jest odpowiednikiem zmiennej, która posiada odwołanie do obiektu lub wystąpienie zwrócone przez konstruktora.

Wartość użycia `x:Name` dyrektywy musi być unikatowa w ramach zakresu nazw XAML. Domyślnie, gdy jest używany przez interfejs API usług XAML platformy .NET, podstawowy kod nazw XAML jest zdefiniowany w elemencie głównym XAML pojedynczej produkcji XAML i obejmuje elementy zawarte w tej produkcji XAML. Dodatkowe dyskretne namescopes XAML, które mogą wystąpić w ramach jednej produkcji XAML mogą być zdefiniowane przez struktury do rozwiązania określonych scenariuszy. Na przykład w WPF nowe identyfikatory XAML są definiowane i tworzone przez dowolny szablon, który jest również zdefiniowany w tej produkcji XAML. Aby uzyskać więcej informacji na temat nazw XAML (napisanych dla WPF, ale istotnych dla wielu pojęć xaml namescope), zobacz [WPF XAML Namescopes](../../framework/wpf/advanced/wpf-xaml-namescopes.md).

Ogólnie rzecz `x:Name` biorąc, nie powinny być `x:Key`stosowane w sytuacjach, które również używają . Implementacje XAML przez konkretne istniejące struktury wprowadziły pojęcia podstawiania między `x:Key` i `x:Name`, ale nie jest to zalecana praktyka. Usługi .NET XAML nie obsługują takich pojęć podstawienia <xref:System.Windows.Markup.INameScope> <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>podczas obsługi informacji o nazwie/kluczu, takich jak lub .

Zasady `x:Name` zezwalania, jak również wymuszanie unikatowości nazwy są potencjalnie definiowane przez określone ramy wdrażania. Jednak aby być użytecznym z usługami .NET XAML, definicje frameworkowe unikatowości nazw <xref:System.Windows.Markup.INameScope> XAML powinny być zgodne z definicją informacji w tej dokumentacji i powinny używać tych samych reguł dotyczących miejsca, w którym informacje są stosowane. Na przykład [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementacja dzieli różne elementy <xref:System.Windows.NameScope> znaczników na oddzielne zakresy, takie jak słowniki zasobów, drzewo logiczne utworzone przez xaml na poziomie strony, szablony i inną odroczoną zawartość, a następnie wymusza unikatowość nazwy XAML w ramach każdego z tych nazw XAML.

W przypadku typów niestandardowych korzystających z modułów zapisu obiektów `x:Name` XAML usług .NET XAML można ustanowić lub zmienić właściwość mapową typu. Definiujesz to zachowanie, odwołując się do <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> nazwy właściwości do mapy z kodem definicji typu.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>jest atrybutem na poziomie typu.

Using.NET usług XAML logikę tworzenia kopii zapasowych dla obsługi nazw XAML można zdefiniować <xref:System.Windows.Markup.INameScope> w sposób neutralny dla struktury, implementując interfejs.

## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF

W standardowej konfiguracji [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kompilacji dla aplikacji, która używa XAML, klasy `x:Name` częściowe i związane z kodem, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] określony staje się nazwą pola, które jest tworzone w kodzie źródłowym, gdy jest przetwarzany przez zadanie kompilacji znaczników, a to pole posiada odwołanie do obiektu. Domyślnie utworzone pole jest wewnętrzne. Dostęp do pól można zmienić, określając [atrybut x:FieldModifier](xfieldmodifier-directive.md). W WPF I Silverlight sekwencji jest, że kompilacja znaczników definiuje i nazwy pola w klasie częściowej, ale wartość jest początkowo pusta. Następnie wygenerowana metoda `InitializeComponent` o nazwie jest wywoływana z wewnątrz konstruktora klasy. `InitializeComponent`składa `FindName` się z wywołań przy użyciu każdej z `x:Name` wartości, które istnieją w części klasy częściowej zdefiniowanej przez XAML jako ciągi wejściowe. Zwracane wartości są następnie przypisywane do odwołania do pola o podobnej nazwie, aby wypełnić wartości pól obiektami utworzonymi na podstawie analizy XAML. Wykonanie `InitializeComponent` umożliwia odwoływanie się do wykresu obiektu `x:Name` czasu wykonywania przy użyciu /field `FindName` name bezpośrednio, zamiast wywoływać jawnie w dowolnym momencie potrzebne odwołanie do obiektu zdefiniowanego przez XAML.

Dla aplikacji WPF, która używa obiektów docelowych języka Microsoft `Page` Visual Basic i zawiera pliki XAML `WithEvents` z akcji kompilacji, `x:Name`oddzielna `Handles` właściwość odwołania jest tworzony podczas kompilacji, która dodaje słowo kluczowe do wszystkich elementów, które mają , do obsługi składni dla delegatów obsługi zdarzeń. Ta właściwość jest zawsze publiczna. Aby uzyskać więcej informacji, zobacz [Visual Basic i Obsługa zdarzeń WPF](../../framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).

`x:Name`jest używany przez procesor WPF XAML do rejestrowania nazwy w xaml namescope w czasie ładowania, nawet w przypadkach, gdy strona nie jest znaczników kompilowane przez akcje kompilacji (na przykład luźne XAML słownika zasobów). Jedną z przyczyn tego `x:Name` zachowania jest, <xref:System.Windows.Data.Binding.ElementName%2A> ponieważ jest potencjalnie potrzebne do wiązania. Aby uzyskać szczegółowe informacje, zobacz [Omówienie powiązania danych](../data/data-binding-overview.md).

Jak wspomniano wcześniej, `x:Name` (lub) `Name`nie powinny być stosowane `x:Key`w sytuacjach, które również używają . Ma [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.ResourceDictionary> specjalne zachowanie definiowania się jako xaml namescope, ale zwracanie <xref:System.Windows.Markup.INameScope> nie implementowane lub null wartości dla interfejsów API jako sposób wymuszania tego zachowania. Jeśli parser WPF XAML `Name` `x:Name` napotka lub w <xref:System.Windows.ResourceDictionary>xaml zdefiniowane , nazwa nie jest dodawany do żadnych nazw XAML. Próba znalezienia tej nazwy z dowolnego kodu `FindName` nazw XAML i metody nie zwróci prawidłowe wyniki.

### <a name="xname-and-name"></a>x:Nazwa i nazwa

Wiele scenariuszy aplikacji WPF można `x:Name` uniknąć użycia atrybutu, ponieważ właściwość `Name` zależności, jak określono w domyślnej przestrzeni <xref:System.Windows.FrameworkElement> nazw <xref:System.Windows.FrameworkContentElement> XAML dla kilku ważnych klas podstawowych, takich jak i spełnia ten sam cel. Nadal istnieją niektóre typowe scenariusze XAML i WPF, `Name` gdzie dostęp do kodu do elementu bez właściwości na poziomie struktury jest ważne. Na przykład niektóre klasy obsługi animacji i `Name` scenorysu nie obsługują właściwości, ale często muszą być odwoływane w kodzie, aby kontrolować animację. Należy określić `x:Name` jako atrybut na osiach czasu i przekształcenia, które są tworzone w XAML, jeśli zamierzasz odwoływać się do nich z kodu później.

Jeśli <xref:System.Windows.FrameworkElement.Name%2A> jest dostępny jako właściwość <xref:System.Windows.FrameworkElement.Name%2A> `x:Name` w klasie i może być używany zamiennie jako atrybuty, ale wyjątek analizy spowoduje, jeśli oba są określone w tym samym elemencie. Jeśli XAML jest znaczników skompilowany, wyjątek wystąpi na kompilacji znaczników, w przeciwnym razie występuje na obciążenie.

<xref:System.Windows.FrameworkElement.Name%2A>można ustawić przy użyciu składni atrybutu XAML, a w kodzie przy użyciu <xref:System.Windows.DependencyObject.SetValue%2A>; należy jednak zauważyć, że ustawienie <xref:System.Windows.FrameworkElement.Name%2A> właściwości w kodzie nie tworzy reprezentatywne odwołanie do pola w obszarze nazw XAML w większości przypadków, gdy kod XAML jest już załadowany. Zamiast próbować ustawić <xref:System.Windows.FrameworkElement.Name%2A> w kodzie, <xref:System.Windows.NameScope> użyj metod z kodu, względem odpowiedniego namescope.

<xref:System.Windows.FrameworkElement.Name%2A>można również ustawić przy użyciu składni elementu właściwości z tekstem wewnętrznym, ale jest to rzadkością. Natomiast `x:Name` nie można ustawić w składni elementu właściwości XAML <xref:System.Windows.DependencyObject.SetValue%2A>ani w kodzie przy użyciu ; można go ustawić tylko przy użyciu składni atrybutów na obiektach, ponieważ jest to dyrektywa.

## <a name="silverlight-usage-notes"></a>Uwagi dotyczące użycia programu Silverlight

`x:Name`dla programu Silverlight jest dokumentowany oddzielnie. Aby uzyskać więcej informacji, zobacz [obszar nazw XAML (x:) Funkcje językowe (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=nameWithType>
- [Drzewa w WPF](../../framework/wpf/advanced/trees-in-wpf.md)
