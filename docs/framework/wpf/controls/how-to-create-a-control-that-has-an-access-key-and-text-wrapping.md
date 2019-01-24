---
title: 'Instrukcje: Utwórz formant z kluczem dostępu i zwijaniem tekstu'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: 12410e2abd1031f7ac42bdaab4b8e09a6b8b6006
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649586"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>Instrukcje: Utwórz formant z kluczem dostępu i zwijaniem tekstu
W tym przykładzie pokazano, jak utworzyć formant, który ma klucz dostępu i obsługuje zawijania tekstu. W przykładzie użyto <xref:System.Windows.Controls.Label> kontroli w celu zilustrowania koncepcji te.  
  
## <a name="example"></a>Przykład  
 **Dodaj zawijania tekstu do etykiety**  
  
 <xref:System.Windows.Controls.Label> Kontrolka nie obsługuje operacji zawijania tekstu. Jeśli potrzebujesz etykiety, która otacza w wielu wierszach, można zagnieżdżać inny element, który obsługuje tekst opakowywanie i umieść element w etykiecie. Poniższy przykład pokazuje, jak używać <xref:System.Windows.Controls.TextBlock> się etykietę, która otacza kilka wierszy tekstu.  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **Dodaj klucz dostępu i zwijaniem tekstu do etykiety**  
  
 Jeśli potrzebujesz <xref:System.Windows.Controls.Label> zawierający klawisza dostępu (Mnemonik), należy użyć <xref:System.Windows.Controls.AccessText> element, który znajduje się wewnątrz <xref:System.Windows.Controls.Label>.  
  
 Określa, takich jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, i <xref:System.Windows.Controls.GroupBox> mają domyślne szablony kontrolek. Te szablony zawierają <xref:System.Windows.Controls.ContentPresenter>. Jedna z właściwości, które mogą być ustawione na <xref:System.Windows.Controls.ContentPresenter> jest <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", którego można użyć do określenia klucza dostępu dla formantu.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.Label> który ma klucz dostępu i obsługuje zawijania tekstu. Aby włączyć zawijania tekstu, przykład ustawia <xref:System.Windows.Controls.AccessText.TextWrapping%2A> właściwości i używa podkreślenia znaków do określenia klucza dostępu. (Znak, który następuje bezpośrednio po znaku podkreślenia jest klucz dostępu).  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Ustaw właściwość Target etykiety](https://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
