---
title: "Jak wykryć kiedy tekst w TextBox uległ zmianie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92fc8995ab75cc25bac3bb21b1646052822c3721
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="fd83f-102">Jak wykryć kiedy tekst w TextBox uległ zmianie</span><span class="sxs-lookup"><span data-stu-id="fd83f-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="fd83f-103">W tym przykładzie pokazano sposób użycia <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> zdarzenia w celu wykonania metody zawsze, gdy tekst w <xref:System.Windows.Controls.TextBox> kontrolki została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="fd83f-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="fd83f-104">W klasie CodeBehind dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawierający <xref:System.Windows.Controls.TextBox> formant, który chcesz monitorować zmian, Wstaw metodę do wywołania po każdej zmianie <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> generowane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="fd83f-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="fd83f-105">Ta metoda musi mieć podpisie, który odpowiada, co jest oczekiwane przez <xref:System.Windows.Controls.TextChangedEventHandler> delegowanie.</span><span class="sxs-lookup"><span data-stu-id="fd83f-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="fd83f-106">Program obsługi zdarzeń jest wywoływana przy każdym zawartość <xref:System.Windows.Controls.TextBox> formantu są zmieniane przez użytkownika lub programowo.</span><span class="sxs-lookup"><span data-stu-id="fd83f-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="fd83f-107">**Uwaga:** to zdarzenie uruchamiane w przypadku <xref:System.Windows.Controls.TextBox> formantu zostanie utworzona i wstępnie wypełniane przy użyciu tekstu.</span><span class="sxs-lookup"><span data-stu-id="fd83f-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd83f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd83f-108">Example</span></span>  
 <span data-ttu-id="fd83f-109">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definiuje Twojej <xref:System.Windows.Controls.TextBox> kontrolować, określ <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atrybut o wartości, która jest zgodna z nazwą metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fd83f-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="fd83f-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd83f-110">Example</span></span>  
 <span data-ttu-id="fd83f-111">W klasie CodeBehind dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawierający <xref:System.Windows.Controls.TextBox> formant, który chcesz monitorować zmian, Wstaw metodę do wywołania po każdej zmianie <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> generowane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="fd83f-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="fd83f-112">Ta metoda musi mieć podpisie, który odpowiada, co jest oczekiwane przez <xref:System.Windows.Controls.TextChangedEventHandler> delegowanie.</span><span class="sxs-lookup"><span data-stu-id="fd83f-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="fd83f-113">Program obsługi zdarzeń jest wywoływana przy każdym zawartość <xref:System.Windows.Controls.TextBox> formantu są zmieniane przez użytkownika lub programowo.</span><span class="sxs-lookup"><span data-stu-id="fd83f-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="fd83f-114">**Uwaga:** to zdarzenie uruchamiane w przypadku <xref:System.Windows.Controls.TextBox> formantu zostanie utworzona i wstępnie wypełniane przy użyciu tekstu.</span><span class="sxs-lookup"><span data-stu-id="fd83f-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="fd83f-115">Komentarze</span><span class="sxs-lookup"><span data-stu-id="fd83f-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd83f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd83f-116">See Also</span></span>  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [<span data-ttu-id="fd83f-117">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="fd83f-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="fd83f-118">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="fd83f-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
