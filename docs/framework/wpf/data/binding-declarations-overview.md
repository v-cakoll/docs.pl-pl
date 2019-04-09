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
ms.openlocfilehash: c0fcbc8054272356c39ba7925041ecef05a0322c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165272"
---
# <a name="binding-declarations-overview"></a>Przegląd Wiązanie deklaracji
W tym temacie omówiono różne sposoby, można zadeklarować powiązania.  

<a name="Prereq"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Przed odczytaniem w tym temacie, należy się zapoznać się z pojęciem i użycie rozszerzenia znaczników. Aby uzyskać więcej informacji na temat rozszerzenia znaczników, zobacz [rozszerzenia znacznikowania i WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).  
  
 W tym temacie nie opisano pojęcia dotyczące powiązania danych. Omówienie koncepcji powiązań danych, zobacz [Data Binding Overview](data-binding-overview.md).  
  
<a name="BindinginXAML"></a>   
## <a name="declaring-a-binding-in-xaml"></a>Deklarowanie powiązania w XAML  
 W tej sekcji omówiono sposób deklarowania powiązania w XAML.  
  
<a name="MarkupExtensionSyntax"></a>   
### <a name="markup-extension-usage"></a>Użycie rozszerzenia znaczników  
 <xref:System.Windows.Data.Binding> jest rozszerzeniem znacznika. Podczas deklarowania powiązania za pomocą rozszerzenia powiązanie deklaracji składa się z szeregu następujące klauzule `Binding` — słowo kluczowe i oddzielone przecinkami (,). Klauzule w deklaracji powiązania mogą znajdować się w dowolnej kolejności, i istnieje wiele możliwych kombinacji. Klauzule są *nazwa*=*wartość* par gdzie *nazwa* nazywa się <xref:System.Windows.Data.Binding> właściwości i *wartość* jest wartość, która jest ustawienie dla właściwości.  
  
 Podczas tworzenia powiązania deklaracji ciągów w znaczniku, musi być dołączony do konkretnej zależności własności obiektu docelowego. Poniższy przykład pokazuje jak powiązać <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> właściwości przy użyciu rozszerzenia powiązania, określając <xref:System.Windows.Data.Binding.Source%2A> i <xref:System.Windows.Data.Binding.Path%2A> właściwości.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]  
  
 Można określić większość właściwości <xref:System.Windows.Data.Binding> klasy w ten sposób. Aby uzyskać więcej informacji o rozszerzeniu powiązania, jak również jak w przypadku listy <xref:System.Windows.Data.Binding> Zobacz właściwości, których nie można ustawić przy użyciu rozszerzenia powiązania [Binding Markup Extension](../advanced/binding-markup-extension.md) Przegląd.  
  
<a name="ObjectElementSyntax"></a>   
### <a name="object-element-syntax"></a>Składnia elementu obiektu  
 Składnia elementu obiektu jest alternatywą dla tworzenia deklaracji powiązania. W większości przypadków jest szczególnie korzystne w za pośrednictwem rozszerzenia adiustacji lub składnia elementu obiektu. Jednak w przypadkach, których rozszerzenie znaczników nie obsługuje danego scenariusza, na przykład, gdy wartość właściwości jest typu niebędących ciągami, dla którego nie istnieje konwersja, należy użyć składni obiektów.  
  
 Oto przykład składnia elementu obiektu i użycie rozszerzenia znaczników:  
  
 [!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 Przykład wiąże <xref:System.Windows.Controls.TextBlock.Foreground%2A> właściwości przez zadeklarowanie powiązania za pomocą składni rozszerzenia. Powiązanie deklaracji pod kątem <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość jest używana składnia elementu obiektu.  
  
 Aby uzyskać więcej informacji na temat różnych warunków, zobacz [składnia XAML w szczegółów](../advanced/xaml-syntax-in-detail.md).  
  
<a name="MBandPB"></a>   
### <a name="multibinding-and-prioritybinding"></a>MultiBinding i PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> i <xref:System.Windows.Data.PriorityBinding> nie obsługują składni rozszerzenia XAML. W związku z tym, należy użyć składni elementu obiektu, jeśli użytkownik deklaruje <xref:System.Windows.Data.MultiBinding> lub <xref:System.Windows.Data.PriorityBinding> w XAML.  
  
<a name="BindinginCode"></a>   
## <a name="creating-a-binding-in-code"></a>Tworzenie powiązania w kodzie  
 Innym sposobem określenia powiązania jest do ustawiania właściwości bezpośrednio na <xref:System.Windows.Data.Binding> obiektu w kodzie. Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Data.Binding> obiektu, a następnie określ właściwości w kodzie.  W tym przykładzie `TheConverter` jest obiektem, który implementuje <xref:System.Windows.Data.IValueConverter> interfejsu.  
  
 [!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
  
 Jeśli obiekt, w której dokonywane jest wiązanie jest <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> może wywołać `SetBinding` metody na obiekcie bezpośrednio zamiast przy użyciu <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>. Aby uzyskać przykład, zobacz [Utwórz powiązanie w kodzie](how-to-create-a-binding-in-code.md).  
  
<a name="Path_Syntax"></a>   
## <a name="binding-path-syntax"></a>Składnia ścieżki wiązania  
 Użyj <xref:System.Windows.Data.Binding.Path%2A> właściwości w celu określenia wartość źródła Aby powiązać:  
  
-   W najprostszym przypadku <xref:System.Windows.Data.Binding.Path%2A> wartość właściwości jest nazwą właściwości obiektu źródłowego na potrzeby powiązania, takich jak `Path=PropertyName`.  
  
-   Można określić właściwości podrzędnych właściwości według podobnej składni podobnie jak w C#. Na przykład, klauzula `Path=ShoppingCart.Order` ustawia powiązanie podwłaściwości `Order` obiektu lub właściwości `ShoppingCart`.  
  
-   Aby powiązać z dołączoną właściwość, umieść nawiasy wokół dołączona właściwość. Na przykład, aby powiązać dołączonych właściwości <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, składnia jest `Path=(DockPanel.Dock)`.  
  
-   Indeksatory właściwości może być określona wewnątrz nawiasów kwadratowych po nazwie właściwości, której stosowana jest indeksator. Na przykład, klauzula `Path=ShoppingCart[0]` ustawia powiązanie indeks, który odpowiada jak Twoja własność wewnętrznego indeksowania obsługuje ciągiem literału "0". Indeksatory zagnieżdżone są również obsługiwane.  
  
-   Indeksatory i właściwości podrzędnych, które mogą być mieszane `Path` klauzuli; na przykład `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   Wewnątrz indeksatory może mieć wiele parametrów indeksatora rozdzielonych przecinkami (,). Można określić typ każdego parametru za pomocą nawiasów. Na przykład można mieć `Path="[(sys:Int32)42,(sys:Int32)24]"`, gdzie `sys` jest mapowany na `System` przestrzeni nazw.  
  
-   Jeśli źródło jest widok kolekcji, można określić bieżącego elementu z ukośnika (/). Na przykład, klauzula `Path=/` ustawia powiązanie z aktualnym elementem w widoku. Gdy źródłem jest kolekcją, ta składnia określa, że bieżący element domyślny widok kolekcji.  
  
-   Nazwy właściwości i ukośniki można łączyć na przechodzenie przez właściwości, które są kolekcjami. Na przykład `Path=/Offices/ManagerName` Określa bieżący element z kolekcji źródłowej, która zawiera `Offices` właściwość, która również jest kolekcją. Jego bieżący element jest obiektem, który zawiera `ManagerName` właściwości.  
  
-   Opcjonalnie ścieżka kropki (.) można powiązać z bieżącego źródła. Na przykład `Text="{Binding}"` jest odpowiednikiem `Text="{Binding Path=.}"`.  
  
### <a name="escaping-mechanism"></a>Mechanizm ucieczki  
  
-   Wewnątrz indeksatorów ([]) znak daszka (^) specjalne następny znak.  
  
-   Jeśli ustawisz <xref:System.Windows.Data.Binding.Path%2A> w XAML, należy również jako znak ucieczki dla (przy użyciu jednostki XML) niektórych znaków, które są specjalne do definicji języka XML:  
  
    -   Użyj `&` jako znak ucieczki dla znaku "&".  
  
    -   Użyj `>` jako znak ucieczki dla tagu końcowego ">".  
  
-   Ponadto, jeśli możesz opisać całe powiązania w atrybucie za pomocą składni rozszerzenia znaczników, należy jako znak ucieczki dla (przy użyciu ukośnik odwrotny \\) znaki, które są charakterystyczne dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] analizatora składni rozszerzenia znaczników:  
  
    -   Ukośnik odwrotny (\\) jest sam znak ucieczki.  
  
    -   Znak równości (=) oddziela nazwy właściwości od wartości właściwości.  
  
    -   Przecinek (,) oddziela właściwości.  
  
    -   Prawy nawias klamrowy (}) jest końcem rozszerzeniem znacznika.  
  
<a name="Default"></a>   
## <a name="default-behaviors"></a>Zachowania domyślne  
 Domyślne zachowanie jest następujący, jeśli nie określono w deklaracji.  
  
-   Konwerter domyślny jest tworzony, który próbuje przeprowadzić konwersję typu wartości źródło powiązania z powiązania wartości docelowej. Jeśli konwersja nie została wykonana, zwraca konwerter domyślne `null`.  
  
-   Jeśli nie ustawisz <xref:System.Windows.Data.Binding.ConverterCulture%2A>, korzysta z aparatu powiązania `Language` właściwości powiązania obiektu docelowego. W XAML to wartością domyślną jest "en US" lub dziedziczy wartości elementu głównego (lub dowolnego elementu), strony, jeśli został jawnie zdefiniowany.  
  
-   Tak długo, jak wiązanie ma już kontekstu danych (na przykład dziedziczone kontekstu danych pochodzących z elementu nadrzędnego) i niezależnie od element lub kolekcję, w zwracanym przez ten kontekst jest odpowiednia dla powiązania bez dalszych modyfikacji ścieżki, Powiązanie deklaracji może mieć wcale nie klauzule: `{Binding}` Często jest to sposób, w jaki określono wiązania danych style, której powiązanie podejmuje działania dotyczące kolekcji. Aby uzyskać więcej informacji, zobacz sekcję "Całe obiekty używane jako powiązania źródło" w [Przegląd wiązanie źródeł](binding-sources-overview.md).  
  
-   Wartość domyślna <xref:System.Windows.Data.Binding.Mode%2A> waha się między jednokierunkową i dwukierunkową, w zależności od właściwości zależności, który jest powiązany. Zawsze możesz zadeklarować tryb powiązania jawnie, aby upewnić się, że Twoje powiązanie żądane zachowanie. We właściwościach formantu ogólne, można edytować użytkownika takie jak <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, domyślnie powiązania dwukierunkowe, natomiast inne właściwości domyślnie powiązania jednokierunkowe.  
  
-   Wartość domyślna <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości waha się między <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> i <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> zależności od tego, jak również właściwość zależności powiązane. Jest wartością domyślną dla większości właściwości zależności <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, podczas gdy <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> właściwość ma wartość domyślną <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd Wiązanie danych](data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
- [Powiązanie danych](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath — Składnia XAML](../advanced/propertypath-xaml-syntax.md)
