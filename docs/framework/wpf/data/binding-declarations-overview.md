---
title: Przegląd Wiązanie deklaracji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
ms.openlocfilehash: 8fea61c463928ee69ef5dd0dfbf107f89c5384ff
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544468"
---
# <a name="binding-declarations-overview"></a>Przegląd Wiązanie deklaracji

W tym temacie omówiono różne sposoby deklarowania powiązania.

<a name="Prereq"></a>

## <a name="prerequisites"></a>Wymagania wstępne

Przed przeczytaniem tego tematu ważne jest zapoznanie się z koncepcją i użyciem rozszerzeń znaczników. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i XAML WPF](../advanced/markup-extensions-and-wpf-xaml.md).

Ten temat nie obejmuje koncepcji powiązań danych. Aby zapoznać się z pojęciami dotyczącymi powiązań danych, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a>Deklarowanie powiązania w języku XAML

W tej sekcji omówiono sposób deklarowania powiązania w języku XAML.

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a>Użycie rozszerzenia znaczników

<xref:System.Windows.Data.Binding> to rozszerzenie znaczników. W przypadku użycia rozszerzenia powiązania do deklarowania powiązania, deklaracja składa się z serii klauzul po słowie kluczowym `Binding` i oddzielone przecinkami (,). Klauzule w deklaracji wiązania mogą znajdować się w dowolnej kolejności i istnieje wiele możliwych kombinacji. Klauzule są *nazwami*=par *wartości* , gdzie *name* jest nazwą właściwości <xref:System.Windows.Data.Binding>, a *wartość* jest wartością ustawianą dla właściwości.

Podczas tworzenia ciągów deklaracji powiązań w znaczniku, muszą one być dołączone do określonej właściwości zależności obiektu docelowego. Poniższy przykład pokazuje, jak powiązać Właściwość <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> przy użyciu rozszerzenia Binding, określając właściwości <xref:System.Windows.Data.Binding.Source%2A> i <xref:System.Windows.Data.Binding.Path%2A>.

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

W ten sposób można określić większość właściwości klasy <xref:System.Windows.Data.Binding>. Aby uzyskać więcej informacji o rozszerzeniu powiązania oraz o liście <xref:System.Windows.Data.Binding> właściwości, których nie można ustawić za pomocą rozszerzenia powiązania, zobacz Omówienie [rozszerzenia znaczników powiązań](../advanced/binding-markup-extension.md) .

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a>Składnia elementu obiektu

Składnia elementu obiektu jest alternatywą dla tworzenia deklaracji powiązania. W większości przypadków nie ma szczególnej korzyści, aby użyć rozszerzenia znacznika lub składni elementu obiektu. Jednak w przypadku, gdy rozszerzenie znaczników nie obsługuje Twojego scenariusza, na przykład gdy wartość właściwości jest typu innego niż ciąg, dla którego nie istnieje żadna konwersja typu, należy użyć składni elementu obiektu.

Poniżej znajduje się przykład składni elementu obiektu i użycie rozszerzenia znacznika:

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

Przykład wiąże <xref:System.Windows.Controls.TextBlock.Foreground%2A> Właściwość przez deklarację powiązania przy użyciu składni rozszerzenia. Deklaracja powiązania dla właściwości <xref:System.Windows.Controls.TextBlock.Text%2A> używa składni elementu obiektu.

Aby uzyskać więcej informacji na temat różnych warunków, zobacz [Szczegóły składni języka XAML](../advanced/xaml-syntax-in-detail.md).

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a>Powiązanie i Priorytetbinding

<xref:System.Windows.Data.MultiBinding> i <xref:System.Windows.Data.PriorityBinding> nie obsługują składni rozszerzenia XAML. W związku z tym należy użyć składni elementu obiektu, Jeśli deklarujesz <xref:System.Windows.Data.MultiBinding> lub <xref:System.Windows.Data.PriorityBinding> w języku XAML.

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a>Tworzenie powiązania w kodzie

Innym sposobem określenia powiązania jest ustawienie właściwości bezpośrednio w obiekcie <xref:System.Windows.Data.Binding> w kodzie. Poniższy przykład pokazuje, jak utworzyć obiekt <xref:System.Windows.Data.Binding> i określić właściwości w kodzie.  W tym przykładzie `TheConverter` jest obiektem, który implementuje interfejs <xref:System.Windows.Data.IValueConverter>.

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

Jeśli powiązanie obiektu jest <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> można wywołać metodę `SetBinding` bezpośrednio dla obiektu, zamiast korzystać z <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>. Aby zapoznać się z przykładem, zobacz [Tworzenie powiązania w kodzie](how-to-create-a-binding-in-code.md).

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a>Składnia ścieżki powiązania

Użyj właściwości <xref:System.Windows.Data.Binding.Path%2A>, aby określić wartość źródłową, z którą chcesz powiązać:

- W najprostszym przypadku wartość właściwości <xref:System.Windows.Data.Binding.Path%2A> jest nazwą właściwości obiektu źródłowego, który ma być używany dla powiązania, np. `Path=PropertyName`.

- Podwłaściwości właściwości można określić za pomocą podobnej składni, która jest w C#. Na przykład klauzula `Path=ShoppingCart.Order` ustawia powiązanie z podwłaściwością `Order` obiektu lub właściwości `ShoppingCart`.

- Aby powiązać z dołączoną właściwością, Umieść nawiasy wokół dołączonej właściwości. Na przykład, aby powiązać z dołączoną właściwością <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, składnia jest `Path=(DockPanel.Dock)`.

- Indeksatory właściwości można określić w nawiasach kwadratowych po nazwie właściwości, w której zastosowano indeksator. Na przykład klauzula `Path=ShoppingCart[0]` ustawia powiązanie z indeksem, który odnosi się do tego, jak wewnętrzna indeksowanie właściwości obsługuje ciąg literału "0". Obsługiwane są również indeksatory zagnieżdżone.

- Indeksatory i podwłaściwości mogą być mieszane w klauzuli `Path`; na przykład `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`

- Wewnątrz indeksatorów można mieć wiele parametrów indeksatora oddzielonych przecinkami (,). Typ każdego parametru można określić za pomocą nawiasów. Można na przykład mieć `Path="[(sys:Int32)42,(sys:Int32)24]"`, gdzie `sys` jest mapowany do przestrzeni nazw `System`.

- Gdy źródłem jest widok kolekcji, bieżący element można określić za pomocą ukośnika (/). Na przykład klauzula `Path=/` ustawia powiązanie z bieżącym elementem w widoku. Gdy źródłem jest kolekcja, ta składnia określa bieżący element domyślnego widoku kolekcji.

- Nazwy właściwości i ukośniki można łączyć z właściwościami przechodzenia, które są kolekcjami. Na przykład `Path=/Offices/ManagerName` określa bieżący element kolekcji źródłowej, która zawiera właściwość `Offices`, która jest również kolekcją. Jego bieżący element jest obiektem, który zawiera właściwość `ManagerName`.

- Opcjonalnie można użyć ścieżki kropki (.) w celu utworzenia powiązania z bieżącym źródłem. Na przykład `Text="{Binding}"` jest równoznaczne z `Text="{Binding Path=.}"`.

### <a name="escaping-mechanism"></a>Mechanizm ucieczki

- Wewnątrz indeksatorów ([]), znak karetki (^) wyprowadza następny znak.

- Jeśli ustawisz <xref:System.Windows.Data.Binding.Path%2A> w języku XAML, musisz również wyjść (przy użyciu jednostek XML) określonych znaków, które są specjalne dla definicji języka XML:

  - Użyj `&amp;` do ucieczki znaku "&".

  - Użyj `&gt;` do ucieczki znacznika końcowego ">".

- Ponadto w przypadku opisania całego powiązania w atrybucie przy użyciu składni rozszerzenia znaczników należy wyjść z (przy użyciu ukośnika odwrotnego \\), które są specyficzne dla analizatora rozszerzeń znaczników [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

  - Ukośnik odwrotny (\\) jest samym znakiem ucieczki.

  - Znak równości (=) oddziela nazwę właściwości od wartości właściwości.

  - Przecinek (,) oddziela właściwości.

  - Prawy nawias klamrowy (}) jest końcem rozszerzenia znacznika.

<a name="Default"></a>

## <a name="default-behaviors"></a>Zachowania domyślne

Zachowanie domyślne jest następujące, jeśli nie zostanie określone w deklaracji.

- Tworzony jest domyślny konwerter, który próbuje wykonać konwersję typu między wartością źródłową powiązania a wartością docelową powiązania. Jeśli konwersja nie zostanie wykonana, domyślny konwerter zwraca `null`.

- Jeśli nie ustawisz <xref:System.Windows.Data.Binding.ConverterCulture%2A>, aparat powiązań używa właściwości `Language` obiektu docelowego powiązania. W języku XAML domyślnie jest to "en-US" lub dziedziczy wartość z elementu głównego (lub dowolnego elementu) strony, jeśli został on jawnie ustawiony.

- Tak długo, jak powiązanie ma już kontekst danych (na przykład Dziedziczony kontekst danych pochodzący z elementu nadrzędnego), a wszelkie elementy lub kolekcje zwracane przez ten kontekst są odpowiednie do powiązania bez konieczności dalszej modyfikacji ścieżki, deklaracja powiązania może nie mieć żadnych klauzul w ogóle: `{Binding}` jest to częstość określenia powiązania dla stylów danych, gdzie powiązanie działa na kolekcji. Aby uzyskać więcej informacji, zobacz sekcję "całe obiekty używane jako źródło powiązań" w [omówieniu źródeł powiązań](binding-sources-overview.md).

- Domyślne <xref:System.Windows.Data.Binding.Mode%2A> różnią się między jednokierunkowe i dwukierunkowe w zależności od właściwości zależności, która jest powiązana. Można zawsze zadeklarować tryb powiązania jawnie, aby upewnić się, że powiązanie ma odpowiednie zachowanie. Ogólnie rzecz biorąc, edytowane przez użytkownika właściwości kontrolki, takie jak <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, domyślnie do powiązań dwukierunkowych, a większość innych właściwości domyślnie do powiązań jednokierunkowych.

- Wartość domyślna <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> różni się między <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> i <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> w zależności od powiązanej właściwości zależności. Wartość domyślna dla większości właściwości zależności jest <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, podczas gdy właściwość <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ma wartość domyślną <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.

## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
- [Powiązanie danych](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath, składnia XAML](../advanced/propertypath-xaml-syntax.md)
