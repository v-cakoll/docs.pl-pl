---
title: "Przegląd Wiązanie deklaracji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 615b92d264b91ab5b267d5e79ab829b8afa489cd
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2018
---
# <a name="binding-declarations-overview"></a>Przegląd Wiązanie deklaracji
W tym temacie opisano różne sposoby, mogą zadeklarować powiązania.  
  
 
  
<a name="Prereq"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Przed przeczytaniem tego tematu, ważne jest, że znasz koncepcji i użycie rozszerzenia znaczników. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 W tym temacie nie opisano pojęcia dotyczące powiązania danych. Omówienie pojęć powiązania danych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
<a name="BindinginXAML"></a>   
## <a name="declaring-a-binding-in-xaml"></a>Deklarowanie powiązania w języku XAML  
 W tej sekcji omówiono sposób deklaruje powiązanie w języku XAML.  
  
<a name="MarkupExtensionSyntax"></a>   
### <a name="markup-extension-usage"></a>Użycie rozszerzenia znaczników  
 <xref:System.Windows.Data.Binding> to rozszerzenie znacznika. Gdy używasz rozszerzenia powiązania Aby zadeklarować powiązanie deklaracji składa się z serii klauzule po `Binding` — słowo kluczowe i oddzielonych przecinkami (,). Klauzule w deklaracji powiązanie mogą znajdować się w dowolnej kolejności i istnieje wiele możliwych kombinacji. Klauzule są *nazwa*=*wartość* pary where *nazwa* jest nazwą <xref:System.Windows.Data.Binding> właściwości i *wartość* jest wartość, która jest ustawienie dla właściwości.  
  
 Podczas tworzenia powiązania deklaracji ciągów w znaczniku, musi być dołączony do właściwości zależności określonego obiektu docelowego. Poniższy przykład przedstawia sposób powiązania <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> właściwości przy użyciu rozszerzenia powiązania, określając <xref:System.Windows.Data.Binding.Source%2A> i <xref:System.Windows.Data.Binding.Path%2A> właściwości.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]  
  
 Można określić większość właściwości <xref:System.Windows.Data.Binding> klasy w ten sposób. Aby uzyskać więcej informacji o rozszerzeniu powiązanie również podobnie jak w przypadku listę <xref:System.Windows.Data.Binding> Zobacz właściwości, których nie można ustawić przy użyciu rozszerzenia powiązania [powiązania — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) omówienie.  
  
<a name="ObjectElementSyntax"></a>   
### <a name="object-element-syntax"></a>Składnia elementu obiektu  
 Składnia elementu obiektu stanowi alternatywę dla tworzenia deklaracji powiązania. W większości przypadków nie ma żadnych danego zaletą używania rozszerzenie znaczników lub składni elementu obiektu. Jednak w przypadku których rozszerzenia znaczników nie obsługuje scenariusza, np. gdy wartość właściwości typu-ciąg dla typu nie istnieje konwersja, należy użyć składni elementu obiekt.  
  
 Poniżej przedstawiono przykład składni elementu obiektu i użycie rozszerzenia znaczników:  
  
 [!code-xaml[BindConversionMarkup#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 Przykład wiąże <xref:System.Windows.Controls.TextBlock.Foreground%2A> właściwości przez zadeklarowanie przy użyciu składni rozszerzenia powiązania. Deklaracja powiązania <xref:System.Windows.Controls.TextBlock.Text%2A> właściwość używa składni elementu obiekt.  
  
 Aby uzyskać więcej informacji o różnych warunków, zobacz [szczegółów w składni języka XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="MBandPB"></a>   
### <a name="multibinding-and-prioritybinding"></a>MultiBinding i PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> i <xref:System.Windows.Data.PriorityBinding> nie obsługują składni rozszerzenia języka XAML. W związku z tym należy użyć składni elementu obiektu, jeśli są deklarowanie <xref:System.Windows.Data.MultiBinding> lub <xref:System.Windows.Data.PriorityBinding> w języku XAML.  
  
<a name="BindinginCode"></a>   
## <a name="creating-a-binding-in-code"></a>Tworzenie powiązania w kodzie  
 Innym sposobem Określanie powiązania jest można ustawić właściwości bezpośrednio na <xref:System.Windows.Data.Binding> obiektu w kodzie. Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Data.Binding> obiektu i określić właściwości w kodzie.  W tym przykładzie `TheConverter` jest obiekt, który implementuje <xref:System.Windows.Data.IValueConverter> interfejsu.  
  
 [!code-csharp[BindConversion#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
  
 Jeśli obiekt jest powiązanie jest <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> można wywołać `SetBinding` metody dla obiekt bezpośrednio zamiast <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>. Na przykład zobacz [Utwórz powiązanie w kodzie](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md).  
  
<a name="Path_Syntax"></a>   
## <a name="binding-path-syntax"></a>Składnia ścieżki powiązania  
 Użyj <xref:System.Windows.Data.Binding.Path%2A> właściwości w celu określenia wartości źródła Aby powiązać:  
  
-   Ogólnie rzecz biorąc <xref:System.Windows.Data.Binding.Path%2A> wartość właściwości jest nazwa właściwości obiektu źródłowego do użycia dla powiązania, takich jak `Path=PropertyName`.  
  
-   Można określić właściwości podrzędne właściwości składniowym podobne jak w [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]. Na przykład klauzuli `Path=ShoppingCart.Order` ustawia powiązanie podwłaściwości `Order` obiektu lub właściwości `ShoppingCart`.  
  
-   Aby powiązać dołączona właściwość, umieść nawiasy dołączona właściwość. Na przykład, aby powiązać dołączona właściwość <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, składnia jest `Path=(DockPanel.Dock)`.  
  
-   Indeksatory właściwości można określić w nawiasach kwadratowych po nazwie właściwości, w których stosowane jest indeksatora. Na przykład klauzuli `Path=ShoppingCart[0]` ustawia powiązanie do indeksu, który odpowiada jak z właściwości wewnętrznego indeksowania obsługuje literału ciągu "0". Indeksatory zagnieżdżone są również obsługiwane.  
  
-   Indeksatory i właściwości mogą być wymieszane `Path` klauzuli, np. `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   Wewnątrz indeksatory może mieć wiele parametrów indeksatora rozdzielonych przecinkami (,). Można określić typ każdego parametru w nawiasach. Na przykład można mieć `Path="[(sys:Int32)42,(sys:Int32)24]"`, gdzie `sys` jest mapowany na `System` przestrzeni nazw.  
  
-   Jeśli źródło jest widokiem kolekcji, z ukośnikiem (/) można określić bieżącego elementu. Na przykład klauzuli `Path=/` ustawia powiązanie do bieżącego elementu w widoku. Gdy źródło jest kolekcją, ta składnia określa bieżący element domyślny widok kolekcji.  
  
-   Nazwy właściwości i ukośniki można łączyć przechodzenia przez właściwości, które są kolekcjami. Na przykład `Path=/Offices/ManagerName` Określa bieżący element kolekcji źródłowej, który zawiera `Offices` właściwość, która również jest kolekcją. Jego bieżący element jest obiekt, który zawiera `ManagerName` właściwości.  
  
-   Opcjonalnie ścieżka kropki (.) można powiązać z bieżącego źródła. Na przykład `Text="{Binding}"` jest odpowiednikiem `Text="{Binding Path=.}"`.  
  
### <a name="escaping-mechanism"></a>Anulowanie mechanizmu  
  
-   Wewnątrz indeksatorów ([]) znaki daszek (^) specjalne następny znak.  
  
-   Jeśli ustawisz <xref:System.Windows.Data.Binding.Path%2A> w języku XAML, należy również wprowadzić (przy użyciu jednostek XML) niektóre znaki specjalne do definicji języka XML:  
  
    -   Użyj `&` Aby anulować znak "&".  
  
    -   Użyj `>` ucieczki tag końcowy ">".  
  
-   Ponadto opisano cały powiązania w atrybucie przy użyciu składni rozszerzenia znaczników, należy wprowadzić (przy użyciu ukośnik odwrotny \\) znaki specjalne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] analizator kodu znaczników rozszerzenia:  
  
    -   Ukośnik odwrotny (\\) jest sam znak ucieczki.  
  
    -   Znak równości (=) oddziela nazwę właściwości od wartości właściwości.  
  
    -   Właściwości oddziela przecinka (,).  
  
    -   Prawy nawias klamrowy (}) jest zakończeniu rozszerzenia znacznika.  
  
<a name="Default"></a>   
## <a name="default-behaviors"></a>Domyślne zachowania  
 Domyślnym zachowaniem jest następująca Jeśli nie zostanie określony w deklaracji.  
  
-   Konwerter domyślny jest tworzony, który próbuje przeprowadzić konwersji typu wartości źródła powiązanie z wartością docelową powiązania. Jeśli nie można dokonać konwersji, zwraca konwerter domyślne `null`.  
  
-   Jeśli nie ustawisz <xref:System.Windows.Data.Binding.ConverterCulture%2A>, aparat wiązania używa `Language` właściwości powiązania obiektu docelowego. W języku XAML to wartością domyślną "en US" lub dziedziczy wartości z elementem głównym (lub dowolnego elementu) strony, jeśli został jawnie zdefiniowany.  
  
-   Tak długo, jak powiązania ma już kontekstu danych (na przykład dziedziczone kontekstu danych przesyłanych przez element nadrzędny) i niezależnie od elementu lub kolekcji zwracanych przez tego kontekstu jest odpowiednia dla powiązania bez konieczności dalszej modyfikacji ścieżki, Powiązanie deklaracja może nie mieć żadnych klauzul w: `{Binding}` często jest to sposób określono powiązania style danych, której powiązanie wykonuje działania na kolekcję. Aby uzyskać więcej informacji, zobacz sekcję "Całego obiekty używane jako powiązania źródła" w [powiązanie Przegląd źródeł](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
-   Wartość domyślna <xref:System.Windows.Data.Binding.Mode%2A> różnie w przypadku jednokierunkowych i dwukierunkowych w zależności od właściwości zależności, jest powiązane. Zawsze można zadeklarować tryb wiązania jawnie, aby upewnić się, że Twoje powiązanie ma zachowanie. W właściwości formantu ogólne, można edytować użytkownika takich jak <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, domyślnie dwukierunkowego powiązania, podczas gdy inne właściwości domyślnie powiązania jednokierunkowe.  
  
-   Wartość domyślna <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> wartości są różne <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> i <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> w zależności od tego, jak również właściwości zależności powiązane. Wartość domyślna dla większości właściwości zależności to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, podczas gdy <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> właściwość ma wartość domyślną równą <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [PropertyPath, składnia XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)
