---
title: Jak użyć sprawdzania pisowni z menu kontekstowym
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 966e3adbcb57c30a55d606f6d6b8b51523ee30ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553770"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>Jak użyć sprawdzania pisowni z menu kontekstowym
Domyślnie po włączeniu sprawdzania w formancie edycji pisowni, takich jak <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox>, Pobierz sprawdzanie pisowni wybory w menu kontekstowym. Na przykład po użytkowników prawym przyciskiem myszy wyrazu otrzymują zestaw sugestie dotyczące pisowni lub opcję **Ignoruj wszystkie**. Jednak aby zastąpić domyślne menu kontekstowe z własnych menu kontekstowe niestandardowych, te funkcje zostaną utracone i trzeba napisać kod, aby ponownie włączyć funkcję Sprawdzanie pisowni w menu kontekstowym. Poniższy przykład pokazuje, jak je włączyć na <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tworzącą <xref:System.Windows.Controls.TextBox> z niektórych zdarzeń, które są używane do implementowania menu kontekstowego.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia kod, który implementuje menu kontekstowego.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 Kod używany w przypadku tej z <xref:System.Windows.Controls.RichTextBox> przypomina. Główną różnicą jest parametr przekazany do `GetSpellingError` metody. Aby uzyskać <xref:System.Windows.Controls.TextBox>, Przekaż indeks całkowitą położenia karetki:  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 Aby uzyskać <xref:System.Windows.Controls.RichTextBox>, Przekaż <xref:System.Windows.Documents.TextPointer> położenia karetki, który określa:  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>Zobacz też  
 [TextBox — omówienie](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Włączanie sprawdzania pisowni w kontrolce edycji tekstu](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [Używanie niestandardowego menu kontekstowego z kontrolką TextBox](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)
