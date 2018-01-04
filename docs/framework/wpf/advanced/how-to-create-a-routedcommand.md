---
title: 'Porady: tworzenie RoutedCommand'
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
helpviewer_keywords: RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 449b55d07aa0119ff23c8642ca83b0989f5b1d4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-routedcommand"></a><span data-ttu-id="1ded4-102">Porady: tworzenie RoutedCommand</span><span class="sxs-lookup"><span data-stu-id="1ded4-102">How to: Create a RoutedCommand</span></span>
<span data-ttu-id="1ded4-103">W tym przykładzie przedstawiono sposób tworzenia niestandardowego <xref:System.Windows.Input.RoutedCommand> i implementowania polecenia niestandardowych tworząc <xref:System.Windows.Input.ExecutedRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> i dołączać do <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="1ded4-103">This example shows how to create a custom <xref:System.Windows.Input.RoutedCommand> and how to implement the custom command by creating a <xref:System.Windows.Input.ExecutedRoutedEventHandler> and a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and attaching them to a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="1ded4-104">Aby uzyskać więcej informacji na wydawanie poleceń, zobacz [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1ded4-104">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ded4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ded4-105">Example</span></span>  
 <span data-ttu-id="1ded4-106">Pierwszym krokiem tworzenia <xref:System.Windows.Input.RoutedCommand> jest zdefiniowanie polecenia i uruchomieniu jej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ded4-106">The first step in creating a <xref:System.Windows.Input.RoutedCommand> is defining the command and instantiating it.</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 <span data-ttu-id="1ded4-107">Aby można było używać polecenia w aplikacji, można utworzyć procedury obsługi zdarzeń, które określają, jak działa polecenie</span><span class="sxs-lookup"><span data-stu-id="1ded4-107">In order to use the command in an application, event handlers which define what the command does must be created</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 <span data-ttu-id="1ded4-108">Następnie <xref:System.Windows.Input.CommandBinding> jest tworzony, który kojarzy polecenie z obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1ded4-108">Next, a  <xref:System.Windows.Input.CommandBinding> is created which associates the command with the event handlers.</span></span> <span data-ttu-id="1ded4-109"><xref:System.Windows.Input.CommandBinding> Jest tworzona na konkretny obiekt.</span><span class="sxs-lookup"><span data-stu-id="1ded4-109">The <xref:System.Windows.Input.CommandBinding> is created on a specific object.</span></span>  <span data-ttu-id="1ded4-110">Ten obiekt definiuje zakres <xref:System.Windows.Input.CommandBinding> w drzewie — element</span><span class="sxs-lookup"><span data-stu-id="1ded4-110">This object defines the scope of the <xref:System.Windows.Input.CommandBinding> in the element tree</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 <span data-ttu-id="1ded4-111">Ostatnim krokiem jest wywoływanie polecenia.</span><span class="sxs-lookup"><span data-stu-id="1ded4-111">The final step is invoking the command.</span></span>  <span data-ttu-id="1ded4-112">Jednym ze sposobów Wywołaj polecenie ma skojarzyć go z <xref:System.Windows.Input.ICommandSource>, takich jak <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="1ded4-112">One way to invoke a command is to associate it with a <xref:System.Windows.Input.ICommandSource>, such as a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 <span data-ttu-id="1ded4-113">Po kliknięciu przycisku <xref:System.Windows.Input.RoutedCommand.Execute%2A> metoda niestandardowa <xref:System.Windows.Input.RoutedCommand> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="1ded4-113">When the Button is clicked, the <xref:System.Windows.Input.RoutedCommand.Execute%2A> method on the custom <xref:System.Windows.Input.RoutedCommand> is called.</span></span>  <span data-ttu-id="1ded4-114"><xref:System.Windows.Input.RoutedCommand> Zgłasza <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> kierowane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1ded4-114">The <xref:System.Windows.Input.RoutedCommand> raises the <xref:System.Windows.Input.CommandManager.PreviewExecuted> and <xref:System.Windows.Input.CommandManager.Executed> routed events.</span></span>  <span data-ttu-id="1ded4-115">Te zdarzenia przechodzenia drzewa element wyszukiwanie <xref:System.Windows.Input.CommandBinding> dla tego konkretnego polecenia.</span><span class="sxs-lookup"><span data-stu-id="1ded4-115">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for this particular command.</span></span>  <span data-ttu-id="1ded4-116">Jeśli <xref:System.Windows.Input.CommandBinding> zostanie znaleziony, <xref:System.Windows.Input.ExecutedRoutedEventHandler> skojarzone z <xref:System.Windows.Input.CommandBinding> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="1ded4-116">If a <xref:System.Windows.Input.CommandBinding> is found, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> associated with <xref:System.Windows.Input.CommandBinding> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ded4-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ded4-117">See Also</span></span>  
 <xref:System.Windows.Input.RoutedCommand>  
 [<span data-ttu-id="1ded4-118">Przegląd poleceń</span><span class="sxs-lookup"><span data-stu-id="1ded4-118">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
