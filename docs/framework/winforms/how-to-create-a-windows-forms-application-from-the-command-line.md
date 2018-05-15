---
title: 'Porady: tworzenie aplikacji formularzy systemu Windows z wiersza polecenia'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe7c1eddd67e678e7086d948efb854a6b4b52f6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="505ba-102">Porady: tworzenie aplikacji formularzy systemu Windows z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="505ba-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="505ba-103">W poniższych procedurach opisano podstawowe kroki, które należy wykonać w celu tworzenia i uruchamiania aplikacji Windows Forms z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="505ba-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="505ba-104">Brak kompleksową obsługę tych procedur w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="505ba-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="505ba-105">Zobacz też [wskazówki: Tworzenie prostego formularza systemu Windows](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span><span class="sxs-lookup"><span data-stu-id="505ba-105">Also see [Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="505ba-106">Procedura</span><span class="sxs-lookup"><span data-stu-id="505ba-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="505ba-107">Aby utworzyć formularz</span><span class="sxs-lookup"><span data-stu-id="505ba-107">To create the form</span></span>  
  
1.  <span data-ttu-id="505ba-108">W pliku kodu pusta wpisz następujące importu lub przy użyciu instrukcji:</span><span class="sxs-lookup"><span data-stu-id="505ba-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="505ba-109">Deklarowanie klasy o nazwie `Form1` dziedziczącego z klasy formularza.</span><span class="sxs-lookup"><span data-stu-id="505ba-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  <span data-ttu-id="505ba-110">Tworzenie domyślnego konstruktora dla `Form1`.</span><span class="sxs-lookup"><span data-stu-id="505ba-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="505ba-111">Więcej kodu zostaną dodane do konstruktora w następnej procedurze.</span><span class="sxs-lookup"><span data-stu-id="505ba-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="505ba-112">Dodaj `Main` metodę do klasy.</span><span class="sxs-lookup"><span data-stu-id="505ba-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="505ba-113">Zastosuj <xref:System.STAThreadAttribute> do języka C# `Main` metodę, aby określić aplikacji formularzy systemu Windows jest jednowątkowego apartamentu.</span><span class="sxs-lookup"><span data-stu-id="505ba-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="505ba-114">(Nie jest potrzebny atrybut w języku Visual Basic, ponieważ w aplikacjach formularzy systemu Windows opracowana z użyciem języka Visual Basic modelu jednowątkowego apartamentu domyślnie.)</span><span class="sxs-lookup"><span data-stu-id="505ba-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2.  <span data-ttu-id="505ba-115">Wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> zastosować style systemu operacyjnego do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="505ba-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3.  <span data-ttu-id="505ba-116">Utwórz wystąpienie formularza i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="505ba-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="505ba-117">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="505ba-117">To compile and run the application</span></span>  
  
1.  <span data-ttu-id="505ba-118">W wierszu polecenia środowiska .NET Framework, przejdź do katalogu utworzonego `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="505ba-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2.  <span data-ttu-id="505ba-119">Kompiluj formularza.</span><span class="sxs-lookup"><span data-stu-id="505ba-119">Compile the form.</span></span>  
  
    -   <span data-ttu-id="505ba-120">Jeśli używasz języka C#, wpisz: `csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="505ba-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="505ba-121">Jeśli używasz programu Visual Basic, wpisz: `vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="505ba-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3.  <span data-ttu-id="505ba-122">W wierszu polecenia wpisz: `Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="505ba-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="505ba-123">Dodawanie formantu i obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="505ba-123">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="505ba-124">Poprzednie kroki procedury przedstawionej tylko tworzenie podstawowych formularza systemu Windows, który kompiluje i uruchamia.</span><span class="sxs-lookup"><span data-stu-id="505ba-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="505ba-125">Następnej procedury opisano, jak utworzyć i dodać kontrolkę w formularzu i obsługi zdarzeń dla formantu.</span><span class="sxs-lookup"><span data-stu-id="505ba-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="505ba-126">Aby uzyskać więcej informacji dotyczących formantów, można dodać do formularzy systemu Windows, zobacz [formantów formularzy systemu Windows](../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="505ba-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](../../../docs/framework/winforms/controls/index.md).</span></span>  
  
 <span data-ttu-id="505ba-127">Oprócz opis sposobu tworzenia aplikacji formularzy systemu Windows, należy pamiętać programowania opartego na zdarzeniach i sposób obsługi danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="505ba-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="505ba-128">Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach systemu Windows](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), i [obsługi danych wejściowych użytkownika](../../../docs/framework/winforms/controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="505ba-128">For more information, see [Creating Event Handlers in Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), and [Handling User Input](../../../docs/framework/winforms/controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="505ba-129">Aby zadeklarować formantu przycisku i obsługiwać jego Zdarzenie kliknięcia</span><span class="sxs-lookup"><span data-stu-id="505ba-129">To declare a button control and handle its click event</span></span>  
  
1.  <span data-ttu-id="505ba-130">Deklarowanie kontrolkę przycisku o nazwie `button1`.</span><span class="sxs-lookup"><span data-stu-id="505ba-130">Declare a button control named `button1`.</span></span>  
  
2.  <span data-ttu-id="505ba-131">W konstruktorze, utworzyć przycisku i ustawić jej <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="505ba-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3.  <span data-ttu-id="505ba-132">Dodawanie przycisku do formularza.</span><span class="sxs-lookup"><span data-stu-id="505ba-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="505ba-133">Poniższy przykład kodu pokazuje, jak można zadeklarować formantu przycisku.</span><span class="sxs-lookup"><span data-stu-id="505ba-133">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="505ba-134">Tworzenie metody, aby obsłużyć <xref:System.Windows.Forms.Control.Click> zdarzenia dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="505ba-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5.  <span data-ttu-id="505ba-135">W obsłudze zdarzeń, kliknij przycisk Wyświetl <xref:System.Windows.Forms.MessageBox> z komunikatem "Hello World".</span><span class="sxs-lookup"><span data-stu-id="505ba-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="505ba-136">Poniższy przykład kodu pokazuje sposób obsługi przycisku Zdarzenie kliknięcia formantu.</span><span class="sxs-lookup"><span data-stu-id="505ba-136">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <span data-ttu-id="505ba-137">Skojarz <xref:System.Windows.Forms.Control.Click> zdarzeń przy użyciu metody tworzenia.</span><span class="sxs-lookup"><span data-stu-id="505ba-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="505ba-138">Poniższy przykład kodu pokazuje, jak skojarzone zdarzenie z metodą.</span><span class="sxs-lookup"><span data-stu-id="505ba-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  <span data-ttu-id="505ba-139">Kompilowanie i uruchamianie aplikacji, zgodnie z opisem w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="505ba-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="505ba-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="505ba-140">Example</span></span>  
 <span data-ttu-id="505ba-141">Poniższy przykład kodu jest pełny przykład z poprzedniej procedury.</span><span class="sxs-lookup"><span data-stu-id="505ba-141">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="505ba-142">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="505ba-142">Compiling the Code</span></span>  
  
-   <span data-ttu-id="505ba-143">Aby skompilować kod, postępuj zgodnie z instrukcjami procedury postępowania opisujących sposób skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="505ba-143">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="505ba-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="505ba-144">See Also</span></span>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [<span data-ttu-id="505ba-145">Zmienianie wyglądu formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="505ba-145">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [<span data-ttu-id="505ba-146">Rozszerzanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="505ba-146">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 [<span data-ttu-id="505ba-147">Wprowadzenie do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="505ba-147">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
