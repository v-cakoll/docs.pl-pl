---
title: Tworzenie aplikacji Windows Forms z wiersza polecenia
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181989"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="46f31-102">Jak: Tworzenie aplikacji Windows Forms z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="46f31-102">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="46f31-103">W poniższych procedurach opisano podstawowe kroki, które należy wykonać, aby utworzyć i uruchomić aplikację Windows Forms z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="46f31-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="46f31-104">Istnieje obszerna obsługa tych procedur w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46f31-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="46f31-105">Zobacz też [Przewodnik: Hostowanie formantu formularzy systemu Windows w programie WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="46f31-105">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="46f31-106">Procedura</span><span class="sxs-lookup"><span data-stu-id="46f31-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="46f31-107">Aby utworzyć formularz</span><span class="sxs-lookup"><span data-stu-id="46f31-107">To create the form</span></span>  
  
1. <span data-ttu-id="46f31-108">W pustym pliku kodu `Imports` wpisz `using` następujące lub instrukcje:</span><span class="sxs-lookup"><span data-stu-id="46f31-108">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="46f31-109">Deklaruj klasę o nazwie, `Form1` która dziedziczy z klasy Form:</span><span class="sxs-lookup"><span data-stu-id="46f31-109">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="46f31-110">Utwórz konstruktor `Form1`bez parametrów dla .</span><span class="sxs-lookup"><span data-stu-id="46f31-110">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="46f31-111">Do konstruktora dodasz więcej kodu w kolejnej procedurze.</span><span class="sxs-lookup"><span data-stu-id="46f31-111">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="46f31-112">Dodaj `Main` metodę do klasy.</span><span class="sxs-lookup"><span data-stu-id="46f31-112">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="46f31-113">Zastosuj <xref:System.STAThreadAttribute> do C# `Main` metoda, aby określić aplikacji Windows Forms jest jednowątkowy apartament.</span><span class="sxs-lookup"><span data-stu-id="46f31-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="46f31-114">(Atrybut nie jest konieczne w języku Visual Basic, ponieważ windows formularze aplikacje opracowane za pomocą języka Visual Basic używać jednowątkowego modelu mieszkania domyślnie.)</span><span class="sxs-lookup"><span data-stu-id="46f31-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="46f31-115">Wywołanie, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> aby zastosować style systemu operacyjnego do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46f31-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="46f31-116">Utwórz wystąpienie formularza i uruchom je.</span><span class="sxs-lookup"><span data-stu-id="46f31-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="46f31-117">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="46f31-117">To compile and run the application</span></span>  
  
1. <span data-ttu-id="46f31-118">W wierszu polecenia .NET Framework przejdź do `Form1` katalogu utworzonego klasy.</span><span class="sxs-lookup"><span data-stu-id="46f31-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="46f31-119">Skompiluj formularz.</span><span class="sxs-lookup"><span data-stu-id="46f31-119">Compile the form.</span></span>  
  
    - <span data-ttu-id="46f31-120">Jeśli używasz języka C#, wpisz:`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="46f31-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="46f31-121">Jeśli używasz języka Visual Basic, wpisz:`vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="46f31-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="46f31-122">W wierszu polecenia wpisz:`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="46f31-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="46f31-123">Dodawanie formantu i obsługa zdarzenia</span><span class="sxs-lookup"><span data-stu-id="46f31-123">Adding a control and handling an event</span></span>

<span data-ttu-id="46f31-124">W poprzednich krokach procedury pokazano, jak po prostu utworzyć podstawowy formularz systemu Windows, który kompiluje i uruchamia.</span><span class="sxs-lookup"><span data-stu-id="46f31-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="46f31-125">Następna procedura pokaże, jak utworzyć i dodać formant do formularza i obsługi zdarzenia dla formantu.</span><span class="sxs-lookup"><span data-stu-id="46f31-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="46f31-126">Aby uzyskać więcej informacji na temat formantów, które można dodać do formularzy systemu Windows, zobacz [Formanty formularzy systemu Windows](./controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="46f31-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="46f31-127">Oprócz zrozumienia sposobu tworzenia aplikacji Windows Forms, należy zrozumieć programowania opartego na zdarzeniach i jak obsługiwać dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="46f31-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="46f31-128">Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](creating-event-handlers-in-windows-forms.md)i obsługa danych [wejściowych użytkownika](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="46f31-128">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="46f31-129">Aby zadeklarować kontrolkę przycisku i obsłużyć jego zdarzenie kliknięcia</span><span class="sxs-lookup"><span data-stu-id="46f31-129">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="46f31-130">Deklarowanie formantu przycisku o nazwie `button1`.</span><span class="sxs-lookup"><span data-stu-id="46f31-130">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="46f31-131">W konstruktorze utwórz przycisk <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Text%2A> ustaw jego , i właściwości.</span><span class="sxs-lookup"><span data-stu-id="46f31-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="46f31-132">Dodaj przycisk do formularza.</span><span class="sxs-lookup"><span data-stu-id="46f31-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="46f31-133">Poniższy przykład kodu pokazuje, jak zadeklarować formant przycisku:</span><span class="sxs-lookup"><span data-stu-id="46f31-133">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="46f31-134">Utwórz metodę obsługi <xref:System.Windows.Forms.Control.Click> zdarzenia dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="46f31-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="46f31-135">W programie obsługi zdarzeń <xref:System.Windows.Forms.MessageBox> click wyświetl komunikat "Hello World".</span><span class="sxs-lookup"><span data-stu-id="46f31-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="46f31-136">Poniższy przykład kodu pokazuje, jak obsługiwać zdarzenie kliknięcia formantu przycisku:</span><span class="sxs-lookup"><span data-stu-id="46f31-136">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="46f31-137">Skojarz <xref:System.Windows.Forms.Control.Click> zdarzenie z utworzoną metodą.</span><span class="sxs-lookup"><span data-stu-id="46f31-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="46f31-138">Poniższy przykład kodu pokazuje, jak skojarzyć zdarzenie z metodą.</span><span class="sxs-lookup"><span data-stu-id="46f31-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="46f31-139">Skompiluj i uruchom aplikację zgodnie z opisem w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="46f31-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46f31-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="46f31-140">Example</span></span>  

<span data-ttu-id="46f31-141">Poniższy przykład kodu jest kompletnym przykładem z poprzednich procedur:</span><span class="sxs-lookup"><span data-stu-id="46f31-141">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="46f31-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46f31-142">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="46f31-143">Zmienianie wyglądu formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46f31-143">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="46f31-144">Rozszerzanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46f31-144">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="46f31-145">Wprowadzenie do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="46f31-145">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
