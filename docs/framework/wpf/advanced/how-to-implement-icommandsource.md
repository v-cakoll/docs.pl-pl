---
title: 'Porady: implementowanie ICommandSource'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 6c18e0b77ec53d9bd3e7ce610f2940effe603c88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174696"
---
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="2880e-102">Porady: implementowanie ICommandSource</span><span class="sxs-lookup"><span data-stu-id="2880e-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="2880e-103">W tym przykładzie pokazano, jak <xref:System.Windows.Input.ICommandSource>utworzyć źródło poleceń przez zaimplementowanie .</span><span class="sxs-lookup"><span data-stu-id="2880e-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="2880e-104">Źródło polecenia jest obiektem, który wie, jak wywołać polecenie.</span><span class="sxs-lookup"><span data-stu-id="2880e-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="2880e-105">Interfejs <xref:System.Windows.Input.ICommandSource> udostępnia trzy elementy członkowskie:</span><span class="sxs-lookup"><span data-stu-id="2880e-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="2880e-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: polecenie, które zostanie wywołane.</span><span class="sxs-lookup"><span data-stu-id="2880e-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="2880e-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: typ danych zdefiniowany przez użytkownika, który jest przekazywany ze źródła polecenia do metody obsługującej polecenie.</span><span class="sxs-lookup"><span data-stu-id="2880e-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="2880e-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: obiekt, na który jest wykonywane polecenie.</span><span class="sxs-lookup"><span data-stu-id="2880e-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="2880e-109">W tym przykładzie jest tworzony klasy, <xref:System.Windows.Controls.Slider> która dziedziczy <xref:System.Windows.Input.ICommandSource> z formantu i implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="2880e-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="2880e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="2880e-110">Example</span></span>

<span data-ttu-id="2880e-111">WPF WPF udostępnia szereg <xref:System.Windows.Input.ICommandSource>klas, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.MenuItem>które <xref:System.Windows.Documents.Hyperlink>implementują , takich jak , i .</span><span class="sxs-lookup"><span data-stu-id="2880e-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="2880e-112">Źródło polecenia definiuje sposób wywoływania polecenia.</span><span class="sxs-lookup"><span data-stu-id="2880e-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="2880e-113">Te klasy wywołać polecenie po kliknięciu i stają się one <xref:System.Windows.Input.ICommandSource.Command%2A> tylko źródłem poleceń, gdy ich właściwość jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="2880e-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="2880e-114">W tym przykładzie wywołasz polecenie, gdy suwak zostanie przeniesiony lub dokładniej <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> po zmianie właściwości.</span><span class="sxs-lookup"><span data-stu-id="2880e-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="2880e-115">Poniżej przedstawiono definicję klasy:</span><span class="sxs-lookup"><span data-stu-id="2880e-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="2880e-116">Następnym krokiem jest <xref:System.Windows.Input.ICommandSource> zaimplementowanie elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="2880e-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="2880e-117">W tym przykładzie właściwości są <xref:System.Windows.DependencyProperty> implementowane jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="2880e-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="2880e-118">Dzięki temu właściwości do korzystania z powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="2880e-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="2880e-119">Aby uzyskać więcej <xref:System.Windows.DependencyProperty> informacji na temat klasy, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2880e-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="2880e-120">Aby uzyskać więcej informacji na temat powiązania danych, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2880e-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="2880e-121">W <xref:System.Windows.Input.ICommandSource.Command%2A> tym miejscu znajduje się tylko właściwość.</span><span class="sxs-lookup"><span data-stu-id="2880e-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="2880e-122">Poniżej znajduje <xref:System.Windows.DependencyProperty> się wywołanie zwrotne zmiany:</span><span class="sxs-lookup"><span data-stu-id="2880e-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="2880e-123">Następnym krokiem jest dodanie i usunięcie polecenia skojarzonego ze źródłem polecenia.</span><span class="sxs-lookup"><span data-stu-id="2880e-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="2880e-124">Właściwość <xref:System.Windows.Input.ICommandSource.Command%2A> nie może być po prostu zastąpione po dodaniu nowego polecenia, ponieważ programy obsługi zdarzeń skojarzone z poprzednim poleceniem, jeśli istnieje, muszą zostać usunięte najpierw.</span><span class="sxs-lookup"><span data-stu-id="2880e-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="2880e-125">Następnym krokiem jest utworzenie <xref:System.Windows.Input.ICommand.CanExecuteChanged> logiki dla programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="2880e-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="2880e-126">Zdarzenie <xref:System.Windows.Input.ICommand.CanExecuteChanged> powiadamia źródło polecenia, że zdolność polecenia do wykonania na bieżącym celu polecenia może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="2880e-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="2880e-127">Gdy źródło polecenia odbiera to zdarzenie, <xref:System.Windows.Input.ICommand.CanExecute%2A> zazwyczaj wywołuje metodę w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="2880e-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="2880e-128">Jeśli polecenie nie może wykonać na bieżącym celu polecenia, źródło polecenia zwykle wyłączy się.</span><span class="sxs-lookup"><span data-stu-id="2880e-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="2880e-129">Jeśli polecenie można wykonać na bieżącym celu polecenia, źródło polecenia zazwyczaj włącza się.</span><span class="sxs-lookup"><span data-stu-id="2880e-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="2880e-130">Ostatnim krokiem <xref:System.Windows.Input.ICommand.Execute%2A> jest metoda.</span><span class="sxs-lookup"><span data-stu-id="2880e-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="2880e-131">Jeśli polecenie jest <xref:System.Windows.Input.RoutedCommand>, <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> metoda jest wywoływana; <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> w przeciwnym razie metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2880e-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="2880e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2880e-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="2880e-133">Przegląd poleceń</span><span class="sxs-lookup"><span data-stu-id="2880e-133">Commanding Overview</span></span>](commanding-overview.md)
