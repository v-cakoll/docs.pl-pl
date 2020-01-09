---
title: 'Porady: implementowanie ICommandSource'
ms.date: 12/05/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ICommandSource interfaces [WPF], implementing
ms.assetid: 7452dd39-6e11-44bf-806a-31d87f3772ac
ms.openlocfilehash: 755377d25a2deb48aa9da86d4182075e30763530
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345095"
---
# <a name="how-to-implement-icommandsource"></a><span data-ttu-id="e4d6d-102">Porady: implementowanie ICommandSource</span><span class="sxs-lookup"><span data-stu-id="e4d6d-102">How to: Implement ICommandSource</span></span>

<span data-ttu-id="e4d6d-103">Ten przykład przedstawia sposób tworzenia źródła poleceń przez implementację <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-103">This example shows how to create a command source by implementing <xref:System.Windows.Input.ICommandSource>.</span></span> <span data-ttu-id="e4d6d-104">Źródło polecenia jest obiektem, który wie, jak wywołać polecenie.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-104">A command source is an object that knows how to invoke a command.</span></span> <span data-ttu-id="e4d6d-105">Interfejs <xref:System.Windows.Input.ICommandSource> uwidacznia trzy elementy członkowskie:</span><span class="sxs-lookup"><span data-stu-id="e4d6d-105">The <xref:System.Windows.Input.ICommandSource> interface exposes three members:</span></span>

- <span data-ttu-id="e4d6d-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: polecenie, które zostanie wywołane.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-106"><xref:System.Windows.Input.ICommandSource.Command%2A>: the command that will be invoked.</span></span>
- <span data-ttu-id="e4d6d-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: zdefiniowany przez użytkownika typ danych, który jest przesyłany ze źródła polecenia do metody, która obsługuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-107"><xref:System.Windows.Input.ICommandSource.CommandParameter%2A>: a user-defined data type which is passed from the command source to the method that handles the command.</span></span>
- <span data-ttu-id="e4d6d-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: obiekt, na którym jest wykonywane polecenie.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-108"><xref:System.Windows.Input.ICommandSource.CommandTarget%2A>: the object that the command is being executed on.</span></span>

<span data-ttu-id="e4d6d-109">W tym przykładzie tworzona jest Klasa, która dziedziczy po formancie <xref:System.Windows.Controls.Slider> i implementuje interfejs <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-109">In this example, a class is created that inherits from the <xref:System.Windows.Controls.Slider> control and implements the  <xref:System.Windows.Input.ICommandSource> interface.</span></span>
  
## <a name="example"></a><span data-ttu-id="e4d6d-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4d6d-110">Example</span></span>

<span data-ttu-id="e4d6d-111">WPF udostępnia wiele klas, które implementują <xref:System.Windows.Input.ICommandSource>, takie jak <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>i <xref:System.Windows.Documents.Hyperlink>.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-111">WPF provides a number of classes which implement <xref:System.Windows.Input.ICommandSource>, such as <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.MenuItem>, and <xref:System.Windows.Documents.Hyperlink>.</span></span> <span data-ttu-id="e4d6d-112">Źródło polecenia definiuje, jak wywołuje polecenie.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-112">A command source defines how it invokes a command.</span></span> <span data-ttu-id="e4d6d-113">Klasy te wywołują polecenie po kliknięciu i stają się źródłami poleceń, gdy ich Właściwość <xref:System.Windows.Input.ICommandSource.Command%2A> jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-113">These classes invoke a command when they're clicked and they only become a command source when their <xref:System.Windows.Input.ICommandSource.Command%2A> property is set.</span></span>

<span data-ttu-id="e4d6d-114">W tym przykładzie wywołasz polecenie, gdy suwak zostanie przeniesiony lub dokładniej, gdy właściwość <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-114">In this example, you'll invoke the command when the slider is moved, or more accurately, when the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property is changed.</span></span>

<span data-ttu-id="e4d6d-115">Poniżej znajduje się definicja klasy:</span><span class="sxs-lookup"><span data-stu-id="e4d6d-115">The following is the class definition:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourceclassdefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceClassDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourceclassdefinition)]

<span data-ttu-id="e4d6d-116">Następnym krokiem jest zaimplementowanie elementów członkowskich <xref:System.Windows.Input.ICommandSource>.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-116">The next step is to implement the <xref:System.Windows.Input.ICommandSource> members.</span></span> <span data-ttu-id="e4d6d-117">W tym przykładzie właściwości są implementowane jako obiekty <xref:System.Windows.DependencyProperty>.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-117">In this example, the properties are implemented as <xref:System.Windows.DependencyProperty> objects.</span></span> <span data-ttu-id="e4d6d-118">Dzięki temu właściwości mogą używać powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-118">This enables the properties to use data binding.</span></span> <span data-ttu-id="e4d6d-119">Aby uzyskać więcej informacji na temat klasy <xref:System.Windows.DependencyProperty>, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e4d6d-119">For more information about the <xref:System.Windows.DependencyProperty> class, see the [Dependency Properties Overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="e4d6d-120">Aby uzyskać więcej informacji na temat powiązania danych, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e4d6d-120">For more information about data binding, see the [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="e4d6d-121">Tutaj jest wyświetlana tylko Właściwość <xref:System.Windows.Input.ICommandSource.Command%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-121">Only the <xref:System.Windows.Input.ICommandSource.Command%2A> property is shown here.</span></span>
 
[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandpropertydefinition)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandPropertyDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandpropertydefinition)]  
  
<span data-ttu-id="e4d6d-122">Poniżej znajduje się <xref:System.Windows.DependencyProperty> zmiany wywołania zwrotnego:</span><span class="sxs-lookup"><span data-stu-id="e4d6d-122">The following is the <xref:System.Windows.DependencyProperty> change callback:</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcecommandchanged)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceCommandChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcecommandchanged)]

<span data-ttu-id="e4d6d-123">Następnym krokiem jest dodanie i usunięcie polecenia, które jest skojarzone ze źródłem polecenia.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-123">The next step is to add and remove the command which is associated with the command source.</span></span> <span data-ttu-id="e4d6d-124">Właściwość <xref:System.Windows.Input.ICommandSource.Command%2A> nie może zostać po prostu zastąpiona po dodaniu nowego polecenia, ponieważ programy obsługi zdarzeń skojarzone z poprzednim poleceniem, jeśli istnieje, należy najpierw usunąć.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-124">The <xref:System.Windows.Input.ICommandSource.Command%2A> property cannot simply be overwritten when a new command is added, because the event handlers associated with the previous command, if there was one, must be removed first.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandsourcehookunhookcommands)]
[!code-vb[ImplementICommandSource#ImplementICommandSourceHookUnHookCommands](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandsourcehookunhookcommands)]

<span data-ttu-id="e4d6d-125">Następnym krokiem jest utworzenie logiki dla programu obsługi <xref:System.Windows.Input.ICommand.CanExecuteChanged>.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-125">The next step is to create logic for the <xref:System.Windows.Input.ICommand.CanExecuteChanged> handler.</span></span>

<span data-ttu-id="e4d6d-126">Zdarzenie <xref:System.Windows.Input.ICommand.CanExecuteChanged> powiadamia źródło polecenia, że możliwość wykonania polecenia w bieżącym obiekcie docelowym polecenia mogła ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-126">The <xref:System.Windows.Input.ICommand.CanExecuteChanged> event notifies the command source that the ability of the command to execute on the current command target may have changed.</span></span> <span data-ttu-id="e4d6d-127">Gdy źródło polecenia odbiera to zdarzenie, zazwyczaj wywołuje metodę <xref:System.Windows.Input.ICommand.CanExecute%2A> przy użyciu polecenia.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-127">When a command source receives this event, it typically calls the <xref:System.Windows.Input.ICommand.CanExecute%2A> method on the command.</span></span> <span data-ttu-id="e4d6d-128">Jeśli polecenie nie może zostać wykonane na bieżącym obiekcie docelowym polecenia, źródło polecenia spowoduje zwykle wyłączenie samego siebie.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-128">If the command cannot execute on the current command target, the command source will typically disable itself.</span></span> <span data-ttu-id="e4d6d-129">Jeśli polecenie można wykonać na bieżącym obiekcie docelowym polecenia, źródło polecenia będzie zazwyczaj umożliwiało samodzielne.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-129">If the command can execute on the current command target, the command source will typically enable itself.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandcanexecutechanged)]
[!code-vb[ImplementICommandSource#ImplementICommandCanExecuteChanged](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandcanexecutechanged)]

<span data-ttu-id="e4d6d-130">Ostatnim krokiem jest metoda <xref:System.Windows.Input.ICommand.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-130">The last step is the <xref:System.Windows.Input.ICommand.Execute%2A> method.</span></span> <span data-ttu-id="e4d6d-131">Jeśli polecenie jest <xref:System.Windows.Input.RoutedCommand>, Metoda <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> jest wywoływana; w przeciwnym razie wywoływana jest metoda <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4d6d-131">If the command is a <xref:System.Windows.Input.RoutedCommand>, the <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> method is called; otherwise, the <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.ICommand.Execute%2A> method is called.</span></span>

[!code-csharp[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/ImplementICommandSource/CSharp/CommandSlider.cs#implementicommandexecute)]
[!code-vb[ImplementICommandSource#ImplementICommandExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImplementICommandSource/visualbasic/commandslider.vb#implementicommandexecute)]

## <a name="see-also"></a><span data-ttu-id="e4d6d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4d6d-132">See also</span></span>

- <xref:System.Windows.Input.ICommandSource>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="e4d6d-133">Przegląd poleceń</span><span class="sxs-lookup"><span data-stu-id="e4d6d-133">Commanding Overview</span></span>](commanding-overview.md)
