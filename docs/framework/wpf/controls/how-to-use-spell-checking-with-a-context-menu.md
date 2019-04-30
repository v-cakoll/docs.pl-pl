---
title: 'Instrukcje: Używanie sprawdzania pisowni z menu kontekstowym'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
ms.openlocfilehash: 72b24c386eb99140c9c2729688994b81f92e1a6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699152"
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>Instrukcje: Używanie sprawdzania pisowni z menu kontekstowym
Domyślnie po włączeniu pisowni w formancie edycji, takie jak <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox>, Pobierz możliwości sprawdzania pisowni z menu kontekstowego. Na przykład, gdy użytkownicy kliknij prawym przyciskiem myszy wyrazu, otrzymują zestaw sugestie dotyczące pisowni lub opcję, aby **Ignoruj wszystkich**. Jednak aby zastąpić domyślne menu kontekstowe z menu kontekstowego, ta funkcja jest utracone i trzeba napisać kod, aby ponownie włączyć funkcję sprawdzania pisowni z menu kontekstowego. Poniższy przykład pokazuje, jak ją włączyć dla <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tworząca <xref:System.Windows.Controls.TextBox> z niektóre zdarzenia, które są używane do implementowania menu kontekstowego.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kod, który implementuje menu kontekstowego.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 Kod używany do wykonywania za pomocą <xref:System.Windows.Controls.RichTextBox> jest podobny. Główną różnicą jest parametr przekazany do `GetSpellingError` metody. Aby uzyskać <xref:System.Windows.Controls.TextBox>, indeks całkowitą położenia karetki do przekazania:  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 Aby uzyskać <xref:System.Windows.Controls.RichTextBox>, przekazać <xref:System.Windows.Documents.TextPointer> położeniu karetki, który określa:  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>Zobacz także

- [TextBox — omówienie](textbox-overview.md)
- [RichTextBox — omówienie](richtextbox-overview.md)
- [Włączanie sprawdzania pisowni w kontrolce edycji tekstu](how-to-enable-spell-checking-in-a-text-editing-control.md)
- [Używanie niestandardowego menu kontekstowego z kontrolką TextBox](how-to-use-a-custom-context-menu-with-a-textbox.md)
