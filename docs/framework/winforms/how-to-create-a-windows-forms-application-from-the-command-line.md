---
title: 'Porady: tworzenie aplikacji formularzy systemu Windows z wiersza polecenia'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22acab6ea3912488ae1382ffb42ca5383a7311af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="d858e-102">Porady: tworzenie aplikacji formularzy systemu Windows z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="d858e-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="d858e-103">W poniższych procedurach opisano podstawowe kroki, które należy wykonać w celu tworzenia i uruchamiania aplikacji Windows Forms z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d858e-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="d858e-104">Brak kompleksową obsługę tych procedur w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d858e-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="d858e-105">Zobacz też [wskazówki: Tworzenie prostego formularza systemu Windows](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span><span class="sxs-lookup"><span data-stu-id="d858e-105">Also see [Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d858e-106">Procedura</span><span class="sxs-lookup"><span data-stu-id="d858e-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="d858e-107">Aby utworzyć formularz</span><span class="sxs-lookup"><span data-stu-id="d858e-107">To create the form</span></span>  
  
1.  <span data-ttu-id="d858e-108">W pliku kodu pusta wpisz następujące importu lub przy użyciu instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d858e-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="d858e-109">Deklarowanie klasy o nazwie `Form1` dziedziczącego z klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="d858e-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  <span data-ttu-id="d858e-110">Tworzenie domyślnego konstruktora dla `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d858e-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="d858e-111">Więcej kodu zostaną dodane do konstruktora w następnej procedurze.</span><span class="sxs-lookup"><span data-stu-id="d858e-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="d858e-112">Dodaj `Main` metodę do klasy.</span><span class="sxs-lookup"><span data-stu-id="d858e-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="d858e-113">Zastosuj <xref:System.STAThreadAttribute> do `Main` metodę, aby określić aplikacji formularzy systemu Windows jest pojedynczy komórek wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="d858e-113">Apply the <xref:System.STAThreadAttribute> to the `Main` method to specify your Windows Forms application is a single threaded apartment.</span></span>  
  
    2.  <span data-ttu-id="d858e-114">Wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> umożliwiają wygląd systemu Windows XP, do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d858e-114">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to give a Windows XP appearance to your application.</span></span>  
  
    3.  <span data-ttu-id="d858e-115">Utwórz wystąpienie formularza i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="d858e-115">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="d858e-116">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="d858e-116">To compile and run the application</span></span>  
  
1.  <span data-ttu-id="d858e-117">W wierszu polecenia środowiska .NET Framework, przejdź do katalogu utworzonego `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="d858e-117">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2.  <span data-ttu-id="d858e-118">Kompiluj formularza.</span><span class="sxs-lookup"><span data-stu-id="d858e-118">Compile the form.</span></span>  
  
    -   <span data-ttu-id="d858e-119">Jeśli używasz języka C#, wpisz:`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="d858e-119">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="d858e-120">Jeśli używasz programu Visual Basic, wpisz:`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span><span class="sxs-lookup"><span data-stu-id="d858e-120">If you are using Visual Basic, type: `vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span></span>  
  
3.  <span data-ttu-id="d858e-121">W wierszu polecenia wpisz:`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="d858e-121">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="d858e-122">Dodawanie formantu i obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="d858e-122">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="d858e-123">Poprzednie kroki procedury przedstawionej tylko tworzenie podstawowych formularza systemu Windows, który kompiluje i uruchamia.</span><span class="sxs-lookup"><span data-stu-id="d858e-123">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="d858e-124">Następnej procedury opisano, jak utworzyć i dodać kontrolkę w formularzu i obsługi zdarzeń dla formantu.</span><span class="sxs-lookup"><span data-stu-id="d858e-124">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="d858e-125">Aby uzyskać więcej informacji dotyczących formantów, można dodać do formularzy systemu Windows, zobacz [formantów formularzy systemu Windows](../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="d858e-125">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](../../../docs/framework/winforms/controls/index.md).</span></span>  
  
 <span data-ttu-id="d858e-126">Oprócz opis sposobu tworzenia aplikacji formularzy systemu Windows, należy pamiętać programowania opartego na zdarzeniach i sposób obsługi danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d858e-126">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="d858e-127">Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach systemu Windows](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), i [obsługi danych wejściowych użytkownika](../../../docs/framework/winforms/controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="d858e-127">For more information, see [Creating Event Handlers in Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), and [Handling User Input](../../../docs/framework/winforms/controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="d858e-128">Aby zadeklarować formantu przycisku i obsługiwać jego Zdarzenie kliknięcia</span><span class="sxs-lookup"><span data-stu-id="d858e-128">To declare a button control and handle its click event</span></span>  
  
1.  <span data-ttu-id="d858e-129">Deklarowanie kontrolkę przycisku o nazwie `button1`.</span><span class="sxs-lookup"><span data-stu-id="d858e-129">Declare a button control named `button1`.</span></span>  
  
2.  <span data-ttu-id="d858e-130">W konstruktorze, utworzyć przycisku i ustawić jej <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d858e-130">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3.  <span data-ttu-id="d858e-131">Dodawanie przycisku do formularza.</span><span class="sxs-lookup"><span data-stu-id="d858e-131">Add the button to the form.</span></span>  
  
     <span data-ttu-id="d858e-132">Poniższy przykład kodu pokazuje, jak można zadeklarować formantu przycisku.</span><span class="sxs-lookup"><span data-stu-id="d858e-132">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="d858e-133">Tworzenie metody, aby obsłużyć <xref:System.Windows.Forms.Control.Click> zdarzenia dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="d858e-133">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5.  <span data-ttu-id="d858e-134">W obsłudze zdarzeń, kliknij przycisk Wyświetl <xref:System.Windows.Forms.MessageBox> z komunikatem "Hello World".</span><span class="sxs-lookup"><span data-stu-id="d858e-134">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="d858e-135">Poniższy przykład kodu pokazuje sposób obsługi przycisku Zdarzenie kliknięcia formantu.</span><span class="sxs-lookup"><span data-stu-id="d858e-135">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <span data-ttu-id="d858e-136">Skojarz <xref:System.Windows.Forms.Control.Click> zdarzeń przy użyciu metody tworzenia.</span><span class="sxs-lookup"><span data-stu-id="d858e-136">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="d858e-137">Poniższy przykład kodu pokazuje, jak skojarzone zdarzenie z metodą.</span><span class="sxs-lookup"><span data-stu-id="d858e-137">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  <span data-ttu-id="d858e-138">Kompilowanie i uruchamianie aplikacji, zgodnie z opisem w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="d858e-138">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d858e-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="d858e-139">Example</span></span>  
 <span data-ttu-id="d858e-140">Poniższy przykład kodu jest pełny przykład z poprzedniej procedury.</span><span class="sxs-lookup"><span data-stu-id="d858e-140">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d858e-141">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d858e-141">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d858e-142">Aby skompilować kod, postępuj zgodnie z instrukcjami procedury postępowania opisujących sposób skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="d858e-142">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d858e-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d858e-143">See Also</span></span>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [<span data-ttu-id="d858e-144">Zmienianie wyglądu formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d858e-144">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [<span data-ttu-id="d858e-145">Rozszerzanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d858e-145">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 [<span data-ttu-id="d858e-146">Wprowadzenie do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d858e-146">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
