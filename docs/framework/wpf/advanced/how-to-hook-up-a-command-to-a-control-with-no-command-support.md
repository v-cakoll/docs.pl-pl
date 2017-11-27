---
title: "Jak podpiąć polecenie do formantu bez użycia obsługi poleceń"
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
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f38a6f900ee2b253708da4b63bdc2f474fa3ab1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a><span data-ttu-id="49cd7-102">Jak podpiąć polecenie do formantu bez użycia obsługi poleceń</span><span class="sxs-lookup"><span data-stu-id="49cd7-102">How to: Hook Up a Command to a Control with No Command Support</span></span>
<span data-ttu-id="49cd7-103">Poniższy przykład przedstawia sposób Podłączanie <xref:System.Windows.Input.RoutedCommand> do <xref:System.Windows.Controls.Control> którego nie ma wbudowaną obsługą dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="49cd7-103">The following example shows how to hook up a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Control> which does not have built in support for the command.</span></span>  <span data-ttu-id="49cd7-104">Dla kompletnego przykładu, który przechwytuje się poleceń do wielu źródeł, zobacz [utworzyć niestandardowe próbę RoutedCommand](http://go.microsoft.com/fwlink/?LinkID=159980) próbki.</span><span class="sxs-lookup"><span data-stu-id="49cd7-104">For a complete sample which hooks up commands to multiple sources, see the [Create a Custom RoutedCommand Sample](http://go.microsoft.com/fwlink/?LinkID=159980) sample.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49cd7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="49cd7-105">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="49cd7-106">udostępnia bibliotekę używanych poleceń, które programistom wystąpić regularnie.</span><span class="sxs-lookup"><span data-stu-id="49cd7-106"> provides a library of common commands which application programmers encounter regularly.</span></span>  <span data-ttu-id="49cd7-107">Klasy, które obejmują biblioteki polecenia są: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, i <xref:System.Windows.Documents.EditingCommands>.</span><span class="sxs-lookup"><span data-stu-id="49cd7-107">The classes which comprise the command library are: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, and <xref:System.Windows.Documents.EditingCommands>.</span></span>  
  
 <span data-ttu-id="49cd7-108">Statycznych <xref:System.Windows.Input.RoutedCommand> obiektów, które składają się następujące klasy nie zostanie podana logiki polecenia.</span><span class="sxs-lookup"><span data-stu-id="49cd7-108">The static <xref:System.Windows.Input.RoutedCommand> objects which make up these classes do not supply command logic.</span></span>  <span data-ttu-id="49cd7-109">Logika dla polecenia jest skojarzony z polecenie z <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="49cd7-109">The logic for the command is associated with the command with a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="49cd7-110">Wiele formantów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utworzone w obsłudze niektórych poleceń w bibliotece polecenia.</span><span class="sxs-lookup"><span data-stu-id="49cd7-110">Many controls in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] have built in support for some of the commands in the command library.</span></span>  <span data-ttu-id="49cd7-111"><xref:System.Windows.Controls.TextBox>, na przykład obsługuje wiele poleceń edycji aplikacji, takich jak <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, i <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.</span><span class="sxs-lookup"><span data-stu-id="49cd7-111"><xref:System.Windows.Controls.TextBox>, for example, supports many of the application edit commands such as <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, and <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.</span></span>  <span data-ttu-id="49cd7-112">Deweloper aplikacji nie trzeba wykonywać żadnych czynności specjalne do pobrania tych poleceń, aby pracować z tych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="49cd7-112">The application developer does not have to do anything special to get these commands to work with these controls.</span></span>  <span data-ttu-id="49cd7-113">Jeśli <xref:System.Windows.Controls.TextBox> jest element docelowy polecenia po wykonaniu polecenia obsłuży przy użyciu polecenia <xref:System.Windows.Input.CommandBinding> wbudowane w formancie.</span><span class="sxs-lookup"><span data-stu-id="49cd7-113">If the <xref:System.Windows.Controls.TextBox> is the command target when the command is executed, it will handle the command using the <xref:System.Windows.Input.CommandBinding> that is built into the control.</span></span>  
  
 <span data-ttu-id="49cd7-114">Poniżej pokazano, jak używać <xref:System.Windows.Controls.Button> jako źródło polecenia <xref:System.Windows.Input.ApplicationCommands.Open%2A> polecenia.</span><span class="sxs-lookup"><span data-stu-id="49cd7-114">The following shows how to use a <xref:System.Windows.Controls.Button> as the command source for the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  <span data-ttu-id="49cd7-115">A <xref:System.Windows.Input.CommandBinding> utworzeniu tego określonego stowarzyszonych <xref:System.Windows.Input.CanExecuteRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> z <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="49cd7-115">A <xref:System.Windows.Input.CommandBinding> is created that associates the specified <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="49cd7-116">Po pierwsze utworzono źródło polecenia.</span><span class="sxs-lookup"><span data-stu-id="49cd7-116">First, the command source is created.</span></span>  <span data-ttu-id="49cd7-117">A <xref:System.Windows.Controls.Button> jest używany jako źródło polecenia.</span><span class="sxs-lookup"><span data-stu-id="49cd7-117">A <xref:System.Windows.Controls.Button> is used as the command source.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 <span data-ttu-id="49cd7-118">Następnie <xref:System.Windows.Input.ExecutedRoutedEventHandler> i <xref:System.Windows.Input.CanExecuteRoutedEventHandler> są tworzone.</span><span class="sxs-lookup"><span data-stu-id="49cd7-118">Next, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> are created.</span></span>  <span data-ttu-id="49cd7-119"><xref:System.Windows.Input.ExecutedRoutedEventHandler> Po prostu otwiera <xref:System.Windows.MessageBox> oznaczającego wykonania polecenia.</span><span class="sxs-lookup"><span data-stu-id="49cd7-119">The <xref:System.Windows.Input.ExecutedRoutedEventHandler> simply opens a <xref:System.Windows.MessageBox> to signify that the command executed.</span></span>  <span data-ttu-id="49cd7-120"><xref:System.Windows.Input.CanExecuteRoutedEventHandler> Ustawia <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="49cd7-120">The <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sets the <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> property to `true`.</span></span>  <span data-ttu-id="49cd7-121">Zwykle, może wykonać obsługi przeprowadza się sprawdza bardziej niezawodne, jeśli wykonanie polecenia na aktualnym elemencie docelowym polecenia.</span><span class="sxs-lookup"><span data-stu-id="49cd7-121">Normally, the can execute handler would perform more robust checks to see if the command could execute on the current command target.</span></span>  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 <span data-ttu-id="49cd7-122">Na koniec <xref:System.Windows.Input.CommandBinding> jest tworzony w katalogu głównym <xref:System.Windows.Window> aplikacji, które kojarzy obsługi kierowane zdarzenia do <xref:System.Windows.Input.ApplicationCommands.Open%2A> polecenia.</span><span class="sxs-lookup"><span data-stu-id="49cd7-122">Finally, a <xref:System.Windows.Input.CommandBinding> is created on the root <xref:System.Windows.Window> of the application that associates the routed events handlers to the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a><span data-ttu-id="49cd7-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49cd7-123">See Also</span></span>  
 [<span data-ttu-id="49cd7-124">Sterująca — omówienie</span><span class="sxs-lookup"><span data-stu-id="49cd7-124">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [<span data-ttu-id="49cd7-125">Podłączanie polecenia dla formantu o obsługę poleceń</span><span class="sxs-lookup"><span data-stu-id="49cd7-125">Hook Up a Command to a Control with Command Support</span></span>](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
