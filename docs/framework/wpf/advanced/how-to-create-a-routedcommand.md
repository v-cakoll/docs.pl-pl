---
title: 'Instrukcje: Tworzenie RoutedCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: 4119a762bd0db63108d08a9db9367e367adb6b58
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372090"
---
# <a name="how-to-create-a-routedcommand"></a><span data-ttu-id="ef251-102">Instrukcje: Tworzenie RoutedCommand</span><span class="sxs-lookup"><span data-stu-id="ef251-102">How to: Create a RoutedCommand</span></span>
<span data-ttu-id="ef251-103">W tym przykładzie pokazano, jak utworzyć niestandardową <xref:System.Windows.Input.RoutedCommand> i jak implementować polecenia niestandardowego przez utworzenie <xref:System.Windows.Input.ExecutedRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> i dołączania ich do <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="ef251-103">This example shows how to create a custom <xref:System.Windows.Input.RoutedCommand> and how to implement the custom command by creating a <xref:System.Windows.Input.ExecutedRoutedEventHandler> and a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and attaching them to a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="ef251-104">Aby uzyskać więcej informacji na temat polecenia, zobacz [polecenia Przegląd](commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ef251-104">For more information on commanding, see the [Commanding Overview](commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef251-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef251-105">Example</span></span>  
 <span data-ttu-id="ef251-106">Pierwszym krokiem w tworzeniu <xref:System.Windows.Input.RoutedCommand> jest definiowanie polecenia i tworzenia jego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ef251-106">The first step in creating a <xref:System.Windows.Input.RoutedCommand> is defining the command and instantiating it.</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 <span data-ttu-id="ef251-107">Aby można było używać polecenia w aplikacji, można utworzyć procedury obsługi zdarzeń, które definiują, polecenie powoduje</span><span class="sxs-lookup"><span data-stu-id="ef251-107">In order to use the command in an application, event handlers which define what the command does must be created</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 <span data-ttu-id="ef251-108">Następnie <xref:System.Windows.Input.CommandBinding> jest tworzony, który kojarzy polecenie z programami obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ef251-108">Next, a  <xref:System.Windows.Input.CommandBinding> is created which associates the command with the event handlers.</span></span> <span data-ttu-id="ef251-109"><xref:System.Windows.Input.CommandBinding> Jest tworzona w określonym obiektem.</span><span class="sxs-lookup"><span data-stu-id="ef251-109">The <xref:System.Windows.Input.CommandBinding> is created on a specific object.</span></span>  <span data-ttu-id="ef251-110">Ten obiekt definiuje zakres <xref:System.Windows.Input.CommandBinding> w drzewie elementów</span><span class="sxs-lookup"><span data-stu-id="ef251-110">This object defines the scope of the <xref:System.Windows.Input.CommandBinding> in the element tree</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 <span data-ttu-id="ef251-111">Ostatnim krokiem jest wywoływanie polecenia.</span><span class="sxs-lookup"><span data-stu-id="ef251-111">The final step is invoking the command.</span></span>  <span data-ttu-id="ef251-112">Jednym ze sposobów, aby wywołać polecenie jest skojarz ją z <xref:System.Windows.Input.ICommandSource>, takich jak <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="ef251-112">One way to invoke a command is to associate it with a <xref:System.Windows.Input.ICommandSource>, such as a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 <span data-ttu-id="ef251-113">Po kliknięciu przycisku <xref:System.Windows.Input.RoutedCommand.Execute%2A> metody na niestandardowej <xref:System.Windows.Input.RoutedCommand> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ef251-113">When the Button is clicked, the <xref:System.Windows.Input.RoutedCommand.Execute%2A> method on the custom <xref:System.Windows.Input.RoutedCommand> is called.</span></span>  <span data-ttu-id="ef251-114"><xref:System.Windows.Input.RoutedCommand> Zgłasza <xref:System.Windows.Input.CommandManager.PreviewExecuted> i <xref:System.Windows.Input.CommandManager.Executed> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ef251-114">The <xref:System.Windows.Input.RoutedCommand> raises the <xref:System.Windows.Input.CommandManager.PreviewExecuted> and <xref:System.Windows.Input.CommandManager.Executed> routed events.</span></span>  <span data-ttu-id="ef251-115">Te zdarzenia przechodzić przez drzewo elementów, wyszukiwanie <xref:System.Windows.Input.CommandBinding> dla tego określonego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ef251-115">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for this particular command.</span></span>  <span data-ttu-id="ef251-116">Jeśli <xref:System.Windows.Input.CommandBinding> zostanie znaleziony, <xref:System.Windows.Input.ExecutedRoutedEventHandler> skojarzony <xref:System.Windows.Input.CommandBinding> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ef251-116">If a <xref:System.Windows.Input.CommandBinding> is found, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> associated with <xref:System.Windows.Input.CommandBinding> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef251-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef251-117">See also</span></span>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="ef251-118">Przegląd poleceń</span><span class="sxs-lookup"><span data-stu-id="ef251-118">Commanding Overview</span></span>](commanding-overview.md)
