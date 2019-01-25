---
title: 'Instrukcje: Wykryj kiedy tekst w TextBox uległ zmianie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 23bf0a88b3dc16491fbd520683385c65a58a7f6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696558"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="e25a0-102">Instrukcje: Wykryj kiedy tekst w TextBox uległ zmianie</span><span class="sxs-lookup"><span data-stu-id="e25a0-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="e25a0-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenia w celu wykonania metody zawsze wtedy, gdy tekst w <xref:System.Windows.Controls.TextBox> kontrolki została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="e25a0-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="e25a0-104">W klasie CodeBehind dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawierający <xref:System.Windows.Controls.TextBox> formant, który chcesz monitorować zmiany, Wstaw metodę do wywołania, gdy <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> generowane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="e25a0-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="e25a0-105">Ta metoda musi mieć podpisu, który jest zgodny, co jest oczekiwane przez <xref:System.Windows.Controls.TextChangedEventHandler> delegować.</span><span class="sxs-lookup"><span data-stu-id="e25a0-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="e25a0-106">Program obsługi zdarzeń jest wywoływana zawsze wtedy, gdy zawartość <xref:System.Windows.Controls.TextBox> kontrolki są zmieniane przez użytkownika lub programowo.</span><span class="sxs-lookup"><span data-stu-id="e25a0-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="e25a0-107">**Uwaga:** To zdarzenie jest uruchamiany, gdy <xref:System.Windows.Controls.TextBox> formant zostanie utworzony i wstępnie wypełniane przy użyciu tekstu.</span><span class="sxs-lookup"><span data-stu-id="e25a0-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e25a0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="e25a0-108">Example</span></span>  
 <span data-ttu-id="e25a0-109">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definiująca swoje <xref:System.Windows.Controls.TextBox> sterowania, określ <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atrybutu z wartością, która jest zgodna z nazwą metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e25a0-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="e25a0-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="e25a0-110">Example</span></span>  
 <span data-ttu-id="e25a0-111">W klasie CodeBehind dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawierający <xref:System.Windows.Controls.TextBox> formant, który chcesz monitorować zmiany, Wstaw metodę do wywołania, gdy <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> generowane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="e25a0-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="e25a0-112">Ta metoda musi mieć podpisu, który jest zgodny, co jest oczekiwane przez <xref:System.Windows.Controls.TextChangedEventHandler> delegować.</span><span class="sxs-lookup"><span data-stu-id="e25a0-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="e25a0-113">Program obsługi zdarzeń jest wywoływana zawsze wtedy, gdy zawartość <xref:System.Windows.Controls.TextBox> kontrolki są zmieniane przez użytkownika lub programowo.</span><span class="sxs-lookup"><span data-stu-id="e25a0-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="e25a0-114">**Uwaga:** To zdarzenie jest uruchamiany, gdy <xref:System.Windows.Controls.TextBox> formant zostanie utworzony i wstępnie wypełniane przy użyciu tekstu.</span><span class="sxs-lookup"><span data-stu-id="e25a0-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="e25a0-115">Komentarze</span><span class="sxs-lookup"><span data-stu-id="e25a0-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e25a0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e25a0-116">See also</span></span>
- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="e25a0-117">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="e25a0-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="e25a0-118">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="e25a0-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
