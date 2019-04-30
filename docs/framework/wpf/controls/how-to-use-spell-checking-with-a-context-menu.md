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
# <a name="how-to-use-spell-checking-with-a-context-menu"></a><span data-ttu-id="6490f-102">Instrukcje: Używanie sprawdzania pisowni z menu kontekstowym</span><span class="sxs-lookup"><span data-stu-id="6490f-102">How to: Use Spell Checking with a Context Menu</span></span>
<span data-ttu-id="6490f-103">Domyślnie po włączeniu pisowni w formancie edycji, takie jak <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox>, Pobierz możliwości sprawdzania pisowni z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="6490f-103">By default, when you enable spell checking in an editing control like <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>, you get spell-checking choices in the context menu.</span></span> <span data-ttu-id="6490f-104">Na przykład, gdy użytkownicy kliknij prawym przyciskiem myszy wyrazu, otrzymują zestaw sugestie dotyczące pisowni lub opcję, aby **Ignoruj wszystkich**.</span><span class="sxs-lookup"><span data-stu-id="6490f-104">For example, when users right-click a misspelled word, they get a set of spelling suggestions or the option to **Ignore All**.</span></span> <span data-ttu-id="6490f-105">Jednak aby zastąpić domyślne menu kontekstowe z menu kontekstowego, ta funkcja jest utracone i trzeba napisać kod, aby ponownie włączyć funkcję sprawdzania pisowni z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="6490f-105">However, when you override the default context menu with your own custom context menu, this functionality is lost, and you need to write code to reenable the spell-checking feature in the context menu.</span></span> <span data-ttu-id="6490f-106">Poniższy przykład pokazuje, jak ją włączyć dla <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6490f-106">The following example shows how to enable this on a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6490f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6490f-107">Example</span></span>  
 <span data-ttu-id="6490f-108">W poniższym przykładzie przedstawiono [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tworząca <xref:System.Windows.Controls.TextBox> z niektóre zdarzenia, które są używane do implementowania menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="6490f-108">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that creates a <xref:System.Windows.Controls.TextBox> with some events that are used to implement the context menu.</span></span>  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="6490f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="6490f-109">Example</span></span>  
 <span data-ttu-id="6490f-110">Poniższy przykład pokazuje kod, który implementuje menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="6490f-110">The following example shows the code that implements the context menu.</span></span>  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 <span data-ttu-id="6490f-111">Kod używany do wykonywania za pomocą <xref:System.Windows.Controls.RichTextBox> jest podobny.</span><span class="sxs-lookup"><span data-stu-id="6490f-111">The code used for doing this with a <xref:System.Windows.Controls.RichTextBox> is similar.</span></span> <span data-ttu-id="6490f-112">Główną różnicą jest parametr przekazany do `GetSpellingError` metody.</span><span class="sxs-lookup"><span data-stu-id="6490f-112">The main difference is in the parameter passed to the `GetSpellingError` method.</span></span> <span data-ttu-id="6490f-113">Aby uzyskać <xref:System.Windows.Controls.TextBox>, indeks całkowitą położenia karetki do przekazania:</span><span class="sxs-lookup"><span data-stu-id="6490f-113">For a <xref:System.Windows.Controls.TextBox>, pass the integer index of the caret position:</span></span>  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <span data-ttu-id="6490f-114">Aby uzyskać <xref:System.Windows.Controls.RichTextBox>, przekazać <xref:System.Windows.Documents.TextPointer> położeniu karetki, który określa:</span><span class="sxs-lookup"><span data-stu-id="6490f-114">For a <xref:System.Windows.Controls.RichTextBox>, pass the <xref:System.Windows.Documents.TextPointer> that specifies the caret position:</span></span>  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a><span data-ttu-id="6490f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6490f-115">See also</span></span>

- [<span data-ttu-id="6490f-116">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="6490f-116">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="6490f-117">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="6490f-117">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="6490f-118">Włączanie sprawdzania pisowni w kontrolce edycji tekstu</span><span class="sxs-lookup"><span data-stu-id="6490f-118">Enable Spell Checking in a Text Editing Control</span></span>](how-to-enable-spell-checking-in-a-text-editing-control.md)
- [<span data-ttu-id="6490f-119">Używanie niestandardowego menu kontekstowego z kontrolką TextBox</span><span class="sxs-lookup"><span data-stu-id="6490f-119">Use a Custom Context Menu with a TextBox</span></span>](how-to-use-a-custom-context-menu-with-a-textbox.md)
