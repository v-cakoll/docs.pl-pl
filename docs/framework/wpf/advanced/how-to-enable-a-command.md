---
title: "Jak włączyć polecenie"
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
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b27f8544a44a252eb1a1afd6e096f303360c14e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-a-command"></a><span data-ttu-id="b2363-102">Jak włączyć polecenie</span><span class="sxs-lookup"><span data-stu-id="b2363-102">How to: Enable a Command</span></span>
<span data-ttu-id="b2363-103">W poniższym przykładzie pokazano sposób użycia droższe w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2363-103">The following example demonstrates how to use commanding in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  <span data-ttu-id="b2363-104">W przykładzie przedstawiono sposób skojarzyć <xref:System.Windows.Input.RoutedCommand> do <xref:System.Windows.Controls.Button>, Utwórz <xref:System.Windows.Input.CommandBinding>i tworzenie obsługi zdarzeń, które implementują <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="b2363-104">The example shows how to associate a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Button>, create a <xref:System.Windows.Input.CommandBinding>, and create the event handlers which implement the <xref:System.Windows.Input.RoutedCommand>.</span></span>  <span data-ttu-id="b2363-105">Aby uzyskać więcej informacji na wydawanie poleceń, zobacz [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b2363-105">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2363-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2363-106">Example</span></span>  
 <span data-ttu-id="b2363-107">W pierwszej sekcji kodu tworzy [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], który składa się z <xref:System.Windows.Controls.Button> i <xref:System.Windows.Controls.StackPanel>i tworzy <xref:System.Windows.Input.CommandBinding> który kojarzy programy obsługi poleceń z <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="b2363-107">The first section of code creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], which consists of a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.StackPanel>, and creates a <xref:System.Windows.Input.CommandBinding> that associates the command handlers with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="b2363-108"><xref:System.Windows.Input.ICommandSource.Command%2A> Właściwość <xref:System.Windows.Controls.Button> jest skojarzony z <xref:System.Windows.Input.ApplicationCommands.Close%2A> polecenia.</span><span class="sxs-lookup"><span data-stu-id="b2363-108">The <xref:System.Windows.Input.ICommandSource.Command%2A> property of the <xref:System.Windows.Controls.Button> is associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="b2363-109"><xref:System.Windows.Input.CommandBinding> Jest dodawany do <xref:System.Windows.Input.CommandBindingCollection> głównego <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="b2363-109">The <xref:System.Windows.Input.CommandBinding> is added to the <xref:System.Windows.Input.CommandBindingCollection> of the root <xref:System.Windows.Window>.</span></span> <span data-ttu-id="b2363-110"><xref:System.Windows.Input.CommandBinding.Executed> i <xref:System.Windows.Input.CommandBinding.CanExecute> procedury obsługi zdarzeń są dołączone do tego powiązania i skojarzone z <xref:System.Windows.Input.ApplicationCommands.Close%2A> polecenia.</span><span class="sxs-lookup"><span data-stu-id="b2363-110">The <xref:System.Windows.Input.CommandBinding.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers are attached to this binding and associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="b2363-111">Bez <xref:System.Windows.Input.CommandBinding> nie logiki polecenia, tylko mechanizm Wywołaj polecenie nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="b2363-111">Without the <xref:System.Windows.Input.CommandBinding> there is no command logic, only a mechanism to invoke the command.</span></span>  <span data-ttu-id="b2363-112">Gdy <xref:System.Windows.Controls.Button> zostanie kliknięty <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> jest wywoływane na elemencie docelowym polecenia, a następnie <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span><span class="sxs-lookup"><span data-stu-id="b2363-112">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> is raised on the command target followed by the <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span></span>  <span data-ttu-id="b2363-113">Te zdarzenia przechodzenia drzewa element wyszukiwanie <xref:System.Windows.Input.CommandBinding> dla tego konkretnego polecenia.</span><span class="sxs-lookup"><span data-stu-id="b2363-113">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for that particular command.</span></span>  <span data-ttu-id="b2363-114">Warto zauważyć, że ponieważ <xref:System.Windows.RoutedEvent> tunelu i bąbelków w drzewie element, należy zachować ostrożność w przypadku gdy <xref:System.Windows.Input.CommandBinding> jest umieszczany.</span><span class="sxs-lookup"><span data-stu-id="b2363-114">It is worth noting that because <xref:System.Windows.RoutedEvent> tunnel and bubble through the element tree, care must be taken in where the <xref:System.Windows.Input.CommandBinding> is put.</span></span>   <span data-ttu-id="b2363-115">Jeśli <xref:System.Windows.Input.CommandBinding> znajduje się na element równorzędny element docelowy polecenia lub innego węzła, który nie jest na trasie o <xref:System.Windows.RoutedEvent>, <xref:System.Windows.Input.CommandBinding> nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="b2363-115">If the <xref:System.Windows.Input.CommandBinding> is on a sibling of the command target or another node that is not on the route of the <xref:System.Windows.RoutedEvent>, the <xref:System.Windows.Input.CommandBinding> will not be accessed.</span></span>  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 <span data-ttu-id="b2363-116">W następnej sekcji kod implementuje <xref:System.Windows.Input.CommandManager.Executed> i <xref:System.Windows.Input.CommandBinding.CanExecute> procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b2363-116">The next section of code implements the <xref:System.Windows.Input.CommandManager.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers.</span></span>  
  
 <span data-ttu-id="b2363-117"><xref:System.Windows.Input.CommandManager.Executed> Obsługi wywołuje metodę Zamknij otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="b2363-117">The <xref:System.Windows.Input.CommandManager.Executed> handler calls a method to close the open file.</span></span>  <span data-ttu-id="b2363-118"><xref:System.Windows.Input.CommandBinding.CanExecute> Obsługi wywołuje metodę, aby określić, czy plik jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b2363-118">The <xref:System.Windows.Input.CommandBinding.CanExecute> handler calls a method to determine whether a file is open.</span></span>  <span data-ttu-id="b2363-119">Jeśli plik jest otwarty, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> ustawiono `true`; w przeciwnym razie wartość jest równa `false`.</span><span class="sxs-lookup"><span data-stu-id="b2363-119">If a file is open, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> is set to `true`; otherwise, it is set to `false`.</span></span>  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a><span data-ttu-id="b2363-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2363-120">See Also</span></span>  
 [<span data-ttu-id="b2363-121">Przegląd poleceń</span><span class="sxs-lookup"><span data-stu-id="b2363-121">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
