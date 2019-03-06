---
title: 'Instrukcje: Użyj niestandardowego menu kontekstowego za pomocą TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: 805f5205a91f9b3da0c48c987f1f49f1d81892b7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358603"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a><span data-ttu-id="7e0f6-102">Instrukcje: Użyj niestandardowego menu kontekstowego za pomocą TextBox</span><span class="sxs-lookup"><span data-stu-id="7e0f6-102">How to: Use a Custom Context Menu with a TextBox</span></span>
<span data-ttu-id="7e0f6-103">W tym przykładzie pokazano, jak definiować ani implementować menu kontekstowego proste dla <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7e0f6-103">This example shows how to define and implement a simple custom context menu for a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e0f6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e0f6-104">Example</span></span>  
 <span data-ttu-id="7e0f6-105">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie zdefiniowano <xref:System.Windows.Controls.TextBox> formant, który zawiera menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="7e0f6-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example defines a <xref:System.Windows.Controls.TextBox> control that includes a custom context menu.</span></span>  
  
 <span data-ttu-id="7e0f6-106">Menu kontekstowe jest definiowana za pomocą <xref:System.Windows.Controls.ContextMenu> elementu.</span><span class="sxs-lookup"><span data-stu-id="7e0f6-106">The context menu is defined using a <xref:System.Windows.Controls.ContextMenu> element.</span></span>  <span data-ttu-id="7e0f6-107">Menu kontekstowe, sama składa się z szeregu <xref:System.Windows.Controls.MenuItem> elementy i <xref:System.Windows.Controls.Separator> elementów.</span><span class="sxs-lookup"><span data-stu-id="7e0f6-107">The context menu itself consists of a series of <xref:System.Windows.Controls.MenuItem> elements and <xref:System.Windows.Controls.Separator> elements.</span></span>  <span data-ttu-id="7e0f6-108">Każdy <xref:System.Windows.Controls.MenuItem> element definiuje polecenie w menu kontekstowym; <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> atrybut definiuje wyświetlany tekst dla polecenia menu i <xref:System.Windows.Controls.MenuItem.Click> atrybut określa metodę programu obsługi dla każdego elementu menu.</span><span class="sxs-lookup"><span data-stu-id="7e0f6-108">Each <xref:System.Windows.Controls.MenuItem> element defines a command in the context menu; the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> attribute defines the display text for the menu command, and the <xref:System.Windows.Controls.MenuItem.Click> attribute specifies a handler method for each menu item.</span></span>  <span data-ttu-id="7e0f6-109"><xref:System.Windows.Controls.Separator> Elementu powoduje po prostu oddzielający wiersza do renderowania między elementami menu poprzednie i kolejne.</span><span class="sxs-lookup"><span data-stu-id="7e0f6-109">The <xref:System.Windows.Controls.Separator> element simply causes a separating line to be rendered between the previous and subsequent menu items.</span></span>  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a><span data-ttu-id="7e0f6-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e0f6-110">Example</span></span>  
 <span data-ttu-id="7e0f6-111">Poniższy przykład pokazuje kod implementacji dla poprzedniego definicji menu kontekstowe, a także kod, który włącza i wyłącza menu kontekstowe.</span><span class="sxs-lookup"><span data-stu-id="7e0f6-111">The following example shows the implementation code for the preceding context menu definition, as well as the code that enables and disables the context menu.</span></span>  <span data-ttu-id="7e0f6-112"><xref:System.Windows.Controls.ContextMenu.Opened> Zdarzeń służy do dynamiczne Włączanie lub wyłączanie niektórych poleceń w zależności od bieżącego stanu <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="7e0f6-112">The <xref:System.Windows.Controls.ContextMenu.Opened> event is used to dynamically enable or disable certain commands depending on the current state of the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="7e0f6-113">Aby przywrócić ustawienia domyślne menu kontekstowe, użyj <xref:System.Windows.DependencyObject.ClearValue%2A> metodę, aby wyczyścić wartości <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7e0f6-113">To restore the default context menu, use the <xref:System.Windows.DependencyObject.ClearValue%2A> method to clear the value of the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property.</span></span>  <span data-ttu-id="7e0f6-114">Aby całkowicie wyłączyć menu kontekstowe, ustaw <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwość odwołanie o wartości null (`Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7e0f6-114">To disable the context menu altogether, set the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property to a null reference (`Nothing` in Visual Basic).</span></span>  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a><span data-ttu-id="7e0f6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e0f6-115">See also</span></span>
- [<span data-ttu-id="7e0f6-116">Używanie sprawdzania pisowni z menu kontekstowym</span><span class="sxs-lookup"><span data-stu-id="7e0f6-116">Use Spell Checking with a Context Menu</span></span>](how-to-use-spell-checking-with-a-context-menu.md)
- [<span data-ttu-id="7e0f6-117">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="7e0f6-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="7e0f6-118">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="7e0f6-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
