---
title: Tworzenie aplikacji Windows Forms z poziomu wiersza polecenia
titleSuffix: ''
description: Dowiedz się, jak wykonać podstawowe kroki w celu utworzenia i uruchomienia aplikacji Windows Forms z poziomu wiersza polecenia.
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: b63bf884b9fd03a0510c7f240f19d7a14196971a
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903457"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="c21a9-103">Instrukcje: Tworzenie aplikacji Windows Forms z poziomu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c21a9-103">How to: Create a Windows Forms application from the command line</span></span>

<span data-ttu-id="c21a9-104">W poniższych procedurach opisano podstawowe kroki, które należy wykonać w celu utworzenia i uruchomienia aplikacji Windows Forms z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c21a9-104">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="c21a9-105">Istnieją rozległe wsparcie dla tych procedur w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c21a9-105">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="c21a9-106">Zobacz również [Przewodnik: hosting formantu Windows Forms w WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="c21a9-106">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>
  
## <a name="procedure"></a><span data-ttu-id="c21a9-107">Procedura</span><span class="sxs-lookup"><span data-stu-id="c21a9-107">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="c21a9-108">Aby utworzyć formularz</span><span class="sxs-lookup"><span data-stu-id="c21a9-108">To create the form</span></span>  
  
1. <span data-ttu-id="c21a9-109">W pustym pliku kodu wpisz następujące `Imports` `using` instrukcje lub:</span><span class="sxs-lookup"><span data-stu-id="c21a9-109">In an empty code file, type the following `Imports` or `using` statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="c21a9-110">Zadeklaruj klasę o nazwie `Form1` , która dziedziczy z klasy form:</span><span class="sxs-lookup"><span data-stu-id="c21a9-110">Declare a class named `Form1` that inherits from the Form class:</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="c21a9-111">Utwórz konstruktora bez parametrów dla `Form1` .</span><span class="sxs-lookup"><span data-stu-id="c21a9-111">Create a parameterless constructor for `Form1`.</span></span>
  
     <span data-ttu-id="c21a9-112">Do konstruktora zostanie dodany kod w kolejnej procedurze.</span><span class="sxs-lookup"><span data-stu-id="c21a9-112">You will add more code to the constructor in a subsequent procedure.</span></span>
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="c21a9-113">Dodaj `Main` metodę do klasy.</span><span class="sxs-lookup"><span data-stu-id="c21a9-113">Add a `Main` method to the class.</span></span>
  
    1. <span data-ttu-id="c21a9-114">Zastosuj <xref:System.STAThreadAttribute> do metody języka C#, `Main` Aby określić, że aplikacja Windows Forms jest apartamentem jednowątkowym.</span><span class="sxs-lookup"><span data-stu-id="c21a9-114">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="c21a9-115">(Atrybut nie jest konieczny w Visual Basic, ponieważ aplikacje Windows Forms opracował z Visual Basic domyślnie korzystają z jednowątkowego modelu apartamentu).</span><span class="sxs-lookup"><span data-stu-id="c21a9-115">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="c21a9-116">Wywołaj <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> , aby zastosować style systemu operacyjnego do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c21a9-116">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="c21a9-117">Utwórz wystąpienie formularza i uruchom je.</span><span class="sxs-lookup"><span data-stu-id="c21a9-117">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="c21a9-118">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="c21a9-118">To compile and run the application</span></span>  
  
1. <span data-ttu-id="c21a9-119">W wierszu polecenia .NET Framework przejdź do katalogu, w którym została utworzona `Form1` Klasa.</span><span class="sxs-lookup"><span data-stu-id="c21a9-119">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="c21a9-120">Kompiluj formularz.</span><span class="sxs-lookup"><span data-stu-id="c21a9-120">Compile the form.</span></span>  
  
    - <span data-ttu-id="c21a9-121">Jeśli używasz języka C#, wpisz:`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="c21a9-121">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="c21a9-122">Jeśli używasz Visual Basic, wpisz:`vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="c21a9-122">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="c21a9-123">W wierszu polecenia wpisz:`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="c21a9-123">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="c21a9-124">Dodawanie kontrolki i obsługa zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c21a9-124">Adding a control and handling an event</span></span>

<span data-ttu-id="c21a9-125">Poprzednie kroki procedury pokazują, jak po prostu utworzyć podstawowy formularz systemu Windows, który kompiluje i uruchamia.</span><span class="sxs-lookup"><span data-stu-id="c21a9-125">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="c21a9-126">Kolejna procedura pokazuje, jak utworzyć i dodać kontrolkę do formularza i obsłużyć zdarzenie dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c21a9-126">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="c21a9-127">Aby uzyskać więcej informacji o kontrolkach, które można dodać do Windows Forms, zobacz [Windows Forms Controls](./controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="c21a9-127">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>
  
 <span data-ttu-id="c21a9-128">Oprócz zrozumienia sposobu tworzenia aplikacji Windows Forms, należy zrozumieć Programowanie oparte na zdarzeniach i sposób obsługi danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c21a9-128">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="c21a9-129">Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w Windows Forms](creating-event-handlers-in-windows-forms.md)i [Obsługa danych wejściowych użytkownika](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="c21a9-129">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="c21a9-130">Aby zadeklarować formant Button i obsłużyć jego zdarzenie kliknięcia</span><span class="sxs-lookup"><span data-stu-id="c21a9-130">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="c21a9-131">Zadeklaruj kontrolkę przycisku o nazwie `button1` .</span><span class="sxs-lookup"><span data-stu-id="c21a9-131">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="c21a9-132">W konstruktorze Utwórz przycisk i ustaw jego <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c21a9-132">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="c21a9-133">Dodaj przycisk do formularza.</span><span class="sxs-lookup"><span data-stu-id="c21a9-133">Add the button to the form.</span></span>  
  
     <span data-ttu-id="c21a9-134">Poniższy przykład kodu demonstruje, jak zadeklarować formant Button:</span><span class="sxs-lookup"><span data-stu-id="c21a9-134">The following code example demonstrates how to declare the button control:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="c21a9-135">Utwórz metodę, aby obsłużyć <xref:System.Windows.Forms.Control.Click> zdarzenie dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="c21a9-135">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="c21a9-136">W obsłudze zdarzeń kliknięcia, Wyświetl <xref:System.Windows.Forms.MessageBox> z komunikatem "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c21a9-136">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="c21a9-137">Poniższy przykład kodu demonstruje, jak obsłużyć zdarzenie kliknięcia kontrolki przycisku:</span><span class="sxs-lookup"><span data-stu-id="c21a9-137">The following code example demonstrates how to handle the button control's click event:</span></span>
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="c21a9-138">Skojarz <xref:System.Windows.Forms.Control.Click> zdarzenie z utworzoną metodą.</span><span class="sxs-lookup"><span data-stu-id="c21a9-138">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="c21a9-139">Poniższy przykład kodu demonstruje, jak skojarzyć zdarzenie z metodą.</span><span class="sxs-lookup"><span data-stu-id="c21a9-139">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="c21a9-140">Skompiluj i uruchom aplikację zgodnie z opisem w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="c21a9-140">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c21a9-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="c21a9-141">Example</span></span>  

<span data-ttu-id="c21a9-142">Poniższy przykład kodu jest kompletnym przykładem z poprzednich procedur:</span><span class="sxs-lookup"><span data-stu-id="c21a9-142">The following code example is the complete example from the previous procedures:</span></span>
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c21a9-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c21a9-143">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="c21a9-144">Zmienianie wyglądu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c21a9-144">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="c21a9-145">Rozszerzanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c21a9-145">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="c21a9-146">Wprowadzenie do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c21a9-146">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
