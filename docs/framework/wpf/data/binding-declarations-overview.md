---
title: Przegląd Wiązanie deklaracji
description: Dowiedz się, jak zadeklarować powiązanie w języku XAML na potrzeby tworzenia aplikacji w Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 8d4943de0cacb5fe0b5a0c37a5a68f15243ad528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619640"
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

<xref:System.Windows.Data.Binding>jest rozszerzeniem znaczników. W przypadku użycia rozszerzenia powiązania do deklarowania powiązania, deklaracja składa się z serii klauzul po `Binding` słowie kluczowym i oddzielonych przecinkami (,). Klauzule w deklaracji wiązania mogą znajdować się w dowolnej kolejności i istnieje wiele możliwych kombinacji. Klauzule są *Name* = parami*wartości* nazw, gdzie *name* jest nazwą <xref:System.Windows.Data.Binding> właściwości, a *wartość* jest wartością ustawianą dla właściwości.

Podczas tworzenia ciągów deklaracji powiązań w znaczniku, muszą one być dołączone do określonej właściwości zależności obiektu docelowego. Poniższy przykład pokazuje, jak powiązać <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> Właściwość przy użyciu rozszerzenia powiązania, określając <xref:System.Windows.Data.Binding.Source%2A> <xref:System.Windows.Data.Binding.Path%2A> właściwości i.

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

W ten sposób można określić większość właściwości <xref:System.Windows.Data.Binding> klasy. Aby uzyskać więcej informacji o rozszerzeniu powiązania oraz o liście <xref:System.Windows.Data.Binding> właściwości, których nie można ustawić za pomocą rozszerzenia powiązania, zobacz Omówienie [rozszerzenia znaczników powiązań](../advanced/binding-markup-extension.md) .

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a>Składnia elementu obiektu

Składnia elementu obiektu jest alternatywą dla tworzenia deklaracji powiązania. W większości przypadków nie ma szczególnej korzyści, aby użyć rozszerzenia znacznika lub składni elementu obiektu. Jednak w przypadku, gdy rozszerzenie znaczników nie obsługuje Twojego scenariusza, na przykład gdy wartość właściwości jest typu innego niż ciąg, dla którego nie istnieje żadna konwersja typu, należy użyć składni elementu obiektu.

Poniżej znajduje się przykład składni elementu obiektu i użycie rozszerzenia znacznika:

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

Przykład wiąże <xref:System.Windows.Controls.TextBlock.Foreground%2A> Właściwość przez zadeklarowanie powiązania przy użyciu składni rozszerzenia. Deklaracja powiązania dla <xref:System.Windows.Controls.TextBlock.Text%2A> właściwości używa składni elementu obiektu.

Aby uzyskać więcej informacji na temat różnych warunków, zobacz [Szczegóły składni języka XAML](../advanced/xaml-syntax-in-detail.md).

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a>Powiązanie i Priorytetbinding

<xref:System.Windows.Data.MultiBinding>i <xref:System.Windows.Data.PriorityBinding> nie obsługują składni rozszerzenia XAML. W związku z tym należy użyć składni elementu obiektu, Jeśli deklarujesz <xref:System.Windows.Data.MultiBinding> lub <xref:System.Windows.Data.PriorityBinding> w języku XAML.

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a>Tworzenie powiązania w kodzie

Innym sposobem określenia powiązania jest ustawienie właściwości bezpośrednio dla <xref:System.Windows.Data.Binding> obiektu w kodzie. Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Data.Binding> obiekt i określić właściwości w kodzie.  W tym przykładzie `TheConverter` jest obiektem, który implementuje <xref:System.Windows.Data.IValueConverter> interfejs.

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

Jeśli powiązanie obiektu jest <xref:System.Windows.FrameworkElement> lub można <xref:System.Windows.FrameworkContentElement> wywołać `SetBinding` metodę dla obiektu bezpośrednio zamiast przy użyciu <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> . Aby zapoznać się z przykładem, zobacz [Tworzenie powiązania w kodzie](how-to-create-a-binding-in-code.md).

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a>Składnia ścieżki powiązania

Użyj <xref:System.Windows.Data.Binding.Path%2A> właściwości, aby określić wartość źródłową, z którą chcesz powiązać:

- W najprostszym przypadku <xref:System.Windows.Data.Binding.Path%2A> wartość właściwości jest nazwą właściwości obiektu źródłowego, który ma być używany dla powiązania, na przykład `Path=PropertyName` .

- Podwłaściwości właściwości można określić za pomocą podobnej składni, która jest w języku C#. Na przykład klauzula `Path=ShoppingCart.Order` ustawia powiązanie z podwłaściwością `Order` obiektu lub właściwości `ShoppingCart` .

- Aby powiązać z dołączoną właściwością, Umieść nawiasy wokół dołączonej właściwości. Na przykład, aby powiązać z dołączoną właściwością <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> , składnia ma wartość `Path=(DockPanel.Dock)` .

- Indeksatory właściwości można określić w nawiasach kwadratowych po nazwie właściwości, w której zastosowano indeksator. Na przykład klauzula `Path=ShoppingCart[0]` ustawia powiązanie z indeksem, który odnosi się do tego, jak wewnętrzna indeksowanie właściwości obsługuje ciąg literału "0". Obsługiwane są również indeksatory zagnieżdżone.

- Indeksatory i podwłaściwości mogą być mieszane w `Path` klauzuli, na przykład`Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`

- Wewnątrz indeksatorów można mieć wiele parametrów indeksatora oddzielonych przecinkami (,). Typ każdego parametru można określić za pomocą nawiasów. Na przykład możesz mieć `Path="[(sys:Int32)42,(sys:Int32)24]"` , gdzie `sys` jest mapowany do `System` przestrzeni nazw.

- Gdy źródłem jest widok kolekcji, bieżący element można określić za pomocą ukośnika (/). Na przykład klauzula `Path=/` ustawia powiązanie z bieżącym elementem w widoku. Gdy źródłem jest kolekcja, ta składnia określa bieżący element domyślnego widoku kolekcji.

- Nazwy właściwości i ukośniki można łączyć z właściwościami przechodzenia, które są kolekcjami. Na przykład `Path=/Offices/ManagerName` określa bieżący element kolekcji źródłowej, który zawiera `Offices` Właściwość, która jest również kolekcją. Jego bieżący element jest obiektem, który zawiera `ManagerName` Właściwość.

- Opcjonalnie można użyć ścieżki kropki (.) w celu utworzenia powiązania z bieżącym źródłem. Na przykład `Text="{Binding}"` jest równoważne `Text="{Binding Path=.}"` .

### <a name="escaping-mechanism"></a>Mechanizm ucieczki

- Wewnątrz indeksatorów ([]), znak karetki (^) wyprowadza następny znak.

- Jeśli ustawisz <xref:System.Windows.Data.Binding.Path%2A> w języku XAML, musisz również wyjść (przy użyciu jednostek XML) określonych znaków, które są specjalne dla definicji języka XML:

  - Użyj `&amp;` do ucieczki znaku "&".

  - Użyj `&gt;` do ucieczki znacznika końcowego ">".

- Ponadto w przypadku opisania całego powiązania w atrybucie przy użyciu składni rozszerzenia znaczników należy wyjść z (przy użyciu ukośnika odwrotnego \\ ), które są specyficzne dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] analizatora rozszerzeń znaczników:

  - Ukośnik odwrotny ( \\ ) jest samym znakiem ucieczki.

  - Znak równości (=) oddziela nazwę właściwości od wartości właściwości.

  - Przecinek (,) oddziela właściwości.

  - Prawy nawias klamrowy (}) jest końcem rozszerzenia znacznika.

<a name="Default"></a>

## <a name="default-behaviors"></a>Zachowania domyślne

Zachowanie domyślne jest następujące, jeśli nie zostanie określone w deklaracji.

- Tworzony jest domyślny konwerter, który próbuje wykonać konwersję typu między wartością źródłową powiązania a wartością docelową powiązania. Jeśli nie można wykonać konwersji, domyślny konwerter zwraca wartość `null` .

- Jeśli nie zostanie ustawiona <xref:System.Windows.Data.Binding.ConverterCulture%2A> , aparat powiązania używa `Language` właściwości obiektu docelowego powiązania. W języku XAML domyślnie jest to "en-US" lub dziedziczy wartość z elementu głównego (lub dowolnego elementu) strony, jeśli został on jawnie ustawiony.

- Tak długo, jak powiązanie ma już kontekst danych (na przykład Dziedziczony kontekst danych pochodzący z elementu nadrzędnego), a wszelkie elementy lub kolekcje zwracane przez ten kontekst są odpowiednie do powiązania bez konieczności dalszej modyfikacji ścieżki, deklaracja powiązania może nie zawierać klauzul w ogóle: `{Binding}` jest to często sposób, w jaki powiązanie jest określone dla stylów danych, gdzie powiązanie działa na kolekcji. Aby uzyskać więcej informacji, zobacz sekcję "całe obiekty używane jako źródło powiązań" w [omówieniu źródeł powiązań](binding-sources-overview.md).

- Wartość domyślna <xref:System.Windows.Data.Binding.Mode%2A> zmienia się między jednokierunkowe i dwukierunkowe w zależności od właściwości zależności, która jest powiązana. Można zawsze zadeklarować tryb powiązania jawnie, aby upewnić się, że powiązanie ma odpowiednie zachowanie. Ogólnie rzecz biorąc, edytowalne właściwości kontrolki, takie jak <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType> , domyślnie do powiązań dwukierunkowych, a większość innych właściwości domyślnie to powiązania jednokierunkowe.

- Wartość domyślna <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> różni się między <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> i <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> w zależności od powiązanej właściwości zależności. Wartością domyślną dla większości właściwości zależności jest <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> , podczas gdy <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> Właściwość ma wartość domyślną <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> .

## <a name="see-also"></a>Zobacz także

- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
- [Powiązanie danych](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath — Składnia XAML](../advanced/propertypath-xaml-syntax.md)
