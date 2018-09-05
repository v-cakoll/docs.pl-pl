---
title: 'Porady: bezpieczne wątkowo wywołania formantów formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: f2716db441380138e6058ec45d9ae9c07f0e21a7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534490"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="63a31-102">Porady: bezpieczne wątkowo wywołania formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="63a31-102">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>

<span data-ttu-id="63a31-103">Jeśli używasz wielowątkowości w celu poprawy wydajności aplikacji Windows Forms, należy się upewnić upewnij wywołania kontrolek w sposób wątkowo.</span><span class="sxs-lookup"><span data-stu-id="63a31-103">If you use multithreading to improve the performance of your Windows Forms applications, you must make sure that you make calls to your controls in a thread-safe way.</span></span>

<span data-ttu-id="63a31-104">Dostęp do kontrolek formularzy Windows Forms nie jest założenia bezpieczne dla wątków.</span><span class="sxs-lookup"><span data-stu-id="63a31-104">Access to Windows Forms controls is not inherently thread safe.</span></span> <span data-ttu-id="63a31-105">Jeśli masz dwa lub więcej wątków manipulowania stanem formantu, jest możliwość wymuszenia kontrolki w niespójnym stanie.</span><span class="sxs-lookup"><span data-stu-id="63a31-105">If you have two or more threads manipulating the state of a control, it is possible to force the control into an inconsistent state.</span></span> <span data-ttu-id="63a31-106">Inne błędy związane z wątku są dostępne, takich jak wyścigu i zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="63a31-106">Other thread-related bugs are possible, such as race conditions and deadlocks.</span></span> <span data-ttu-id="63a31-107">Należy się upewnić, że dostęp do formantów jest wykonywane w sposób wątkowo.</span><span class="sxs-lookup"><span data-stu-id="63a31-107">It is important to make sure that access to your controls is performed in a thread-safe way.</span></span>

<span data-ttu-id="63a31-108">Nie jest bezpieczne wywołanie formantu z wątku innego niż ten, który utworzył już formant bez użycia <xref:System.Windows.Forms.Control.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="63a31-108">It is unsafe to call a control from a thread other than the one that created the control without using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span> <span data-ttu-id="63a31-109">Oto przykład wywołania, który nie jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="63a31-109">The following is an example of a call that is not thread safe.</span></span>

```csharp
// This event handler creates a thread that calls a
// Windows Forms control in an unsafe way.
private void setTextUnsafeBtn_Click(
    object sender,
    EventArgs e)
{
    this.demoThread =
        new Thread(new ThreadStart(this.ThreadProcUnsafe));

    this.demoThread.Start();
}

// This method is executed on the worker thread and makes
// an unsafe call on the TextBox control.
private void ThreadProcUnsafe()
{
    this.textBox1.Text = "This text was set unsafely.";
}
```

```vb
' This event handler creates a thread that calls a
' Windows Forms control in an unsafe way.
 Private Sub setTextUnsafeBtn_Click( _
 ByVal sender As Object, _
 ByVal e As EventArgs) Handles setTextUnsafeBtn.Click

     Me.demoThread = New Thread( _
     New ThreadStart(AddressOf Me.ThreadProcUnsafe))

     Me.demoThread.Start()
 End Sub

' This method is executed on the worker thread and makes
' an unsafe call on the TextBox control.
Private Sub ThreadProcUnsafe()
   Me.textBox1.Text = "This text was set unsafely."
End Sub
```

```cpp
// This event handler creates a thread that calls a
    // Windows Forms control in an unsafe way.
private:
    void setTextUnsafeBtn_Click(Object^ sender, EventArgs^ e)
    {
        this->demoThread =
            gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcUnsafe));

        this->demoThread->Start();
    }

    // This method is executed on the worker thread and makes
    // an unsafe call on the TextBox control.
private:
    void ThreadProcUnsafe()
    {
        this->textBox1->Text = "This text was set unsafely.";
    }
```

<span data-ttu-id="63a31-110">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Pomaga wykrywać, gdy uzyskują dostęp do formantów w taki sposób, który nie jest bezpieczny dla wątków.</span><span class="sxs-lookup"><span data-stu-id="63a31-110">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] helps you detect when you are accessing your controls in a manner that is not thread safe.</span></span> <span data-ttu-id="63a31-111">Gdy aplikacja jest uruchamiana w debugerze i wątku innych niż ten, który utworzony formant próbuje wywołać, że kontrolki, debuger zgłasza <xref:System.InvalidOperationException> się komunikatem "kontrolki *nazwa kontrolki* dostępne z Wątek innego niż wątek, który został utworzony na".</span><span class="sxs-lookup"><span data-stu-id="63a31-111">When you are running your application in the debugger, and a thread other than the one which created a control tries to call that control, the debugger raises an <xref:System.InvalidOperationException> with the message, "Control *control name* accessed from a thread other than the thread it was created on."</span></span>

<span data-ttu-id="63a31-112">Ten wyjątek występuje niezawodnie podczas debugowania, a w pewnych okolicznościach, w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="63a31-112">This exception occurs reliably during debugging and, under some circumstances, at run time.</span></span> <span data-ttu-id="63a31-113">Można napotkać tego wyjątku podczas debugowania aplikacji, które powstała z jednego z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] przed [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63a31-113">You might see this exception when you debug applications that you wrote with the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] prior to the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="63a31-114">Zdecydowanie zaleca się rozwiązać ten problem, gdy zostanie wyświetlony, ale można ją wyłączyć, ustawiając <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="63a31-114">You are strongly advised to fix this problem when you see it, but you can disable it by setting the <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> property to `false`.</span></span> <span data-ttu-id="63a31-115">Powoduje to, że kontrolki do uruchomienia, takie jak aplikacja może działać w Visual Studio .NET 2003 i [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63a31-115">This causes your control to run like it would run under Visual Studio .NET 2003 and the [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="63a31-116">Jeśli używasz kontrolki ActiveX na formularzu, może pojawić się między wątkami <xref:System.InvalidOperationException> podczas uruchamiania w debugerze.</span><span class="sxs-lookup"><span data-stu-id="63a31-116">If you are using ActiveX controls on a form, you may receive the cross-thread <xref:System.InvalidOperationException> when you run under the debugger.</span></span> <span data-ttu-id="63a31-117">W takiej sytuacji nie obsługuje formant ActiveX wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="63a31-117">When this occurs, the ActiveX control does not support multithreading.</span></span> <span data-ttu-id="63a31-118">Aby uzyskać więcej informacji o używaniu kontrolki ActiveX z formularzami Windows Forms, zobacz [Windows Forms i niezarządzane aplikacje](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md).</span><span class="sxs-lookup"><span data-stu-id="63a31-118">For more information about using ActiveX controls with Windows Forms, see [Windows Forms and Unmanaged Applications](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md).</span></span>

## <a name="making-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="63a31-119">Bezpieczna wątkowo wywołania do Windows formantów formularzy</span><span class="sxs-lookup"><span data-stu-id="63a31-119">Making Thread-Safe Calls to Windows Forms Controls</span></span>

### <a name="to-make-a-thread-safe-call-to-a-windows-forms-control"></a><span data-ttu-id="63a31-120">Aby wywołać wątków do formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="63a31-120">To make a thread-safe call to a Windows Forms control</span></span>

1.  <span data-ttu-id="63a31-121">Zapytanie formantu <xref:System.Windows.Forms.Control.InvokeRequired%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="63a31-121">Query the control's <xref:System.Windows.Forms.Control.InvokeRequired%2A> property.</span></span>

2.  <span data-ttu-id="63a31-122">Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `true`, wywołaj <xref:System.Windows.Forms.Control.Invoke%2A> z delegatem, który sprawia, że to rzeczywiste wywołanie do formantu.</span><span class="sxs-lookup"><span data-stu-id="63a31-122">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, call <xref:System.Windows.Forms.Control.Invoke%2A> with a delegate that makes the actual call to the control.</span></span>

3.  <span data-ttu-id="63a31-123">Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `false`, bezpośrednio wywoływać formantu.</span><span class="sxs-lookup"><span data-stu-id="63a31-123">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `false`, call the control directly.</span></span>

<span data-ttu-id="63a31-124">W poniższym przykładzie kodu, wywołanie wątkowo jest zaimplementowana w `ThreadProcSafe` metody, która jest wykonywana przez wątek w tle.</span><span class="sxs-lookup"><span data-stu-id="63a31-124">In the following code example, a thread-safe call is implemented in the `ThreadProcSafe` method, which is executed by the background thread.</span></span> <span data-ttu-id="63a31-125">Jeśli <xref:System.Windows.Forms.TextBox> kontrolki <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `true`, `ThreadProcSafe` metoda tworzy wystąpienie `StringArgReturningVoidDelegate` i przekazuje, do formularza <xref:System.Windows.Forms.Control.Invoke%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="63a31-125">If the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, the `ThreadProcSafe` method creates an instance of `StringArgReturningVoidDelegate` and passes that to the form's <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span> <span data-ttu-id="63a31-126">Powoduje to, że `SetText` metoda do wywołania na wątek, który utworzył <xref:System.Windows.Forms.TextBox> kontrolki w tym kontekście wątku <xref:System.Windows.Forms.Control.Text%2A> zostaje ustalona bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="63a31-126">This causes the `SetText` method to be called on the thread that created the <xref:System.Windows.Forms.TextBox> control, and in this thread context the <xref:System.Windows.Forms.Control.Text%2A> property is set directly.</span></span>

```csharp
// This event handler creates a thread that calls a
// Windows Forms control in a thread-safe way.
private void setTextSafeBtn_Click(
    object sender,
    EventArgs e)
{
    this.demoThread =
        new Thread(new ThreadStart(this.ThreadProcSafe));

    this.demoThread.Start();
}

// This method is executed on the worker thread and makes
// a thread-safe call on the TextBox control.
private void ThreadProcSafe()
{
    this.SetText("This text was set safely.");
}
```

```vb
' This event handler creates a thread that calls a
' Windows Forms control in a thread-safe way.
 Private Sub setTextSafeBtn_Click( _
 ByVal sender As Object, _
 ByVal e As EventArgs) Handles setTextSafeBtn.Click

     Me.demoThread = New Thread( _
     New ThreadStart(AddressOf Me.ThreadProcSafe))

     Me.demoThread.Start()
 End Sub

' This method is executed on the worker thread and makes
' a thread-safe call on the TextBox control.
Private Sub ThreadProcSafe()
   Me.SetText("This text was set safely.")
 End Sub
```

```cpp
// This event handler creates a thread that calls a
    // Windows Forms control in a thread-safe way.
private:
    void setTextSafeBtn_Click(Object^ sender, EventArgs^ e)
    {
        this->demoThread =
            gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcSafe));

        this->demoThread->Start();
    }

    // This method is executed on the worker thread and makes
    // a thread-safe call on the TextBox control.
private:
    void ThreadProcSafe()
    {
        this->SetText("This text was set safely.");
    }
```

```csharp
// This delegate enables asynchronous calls for setting
// the text property on a TextBox control.
delegate void StringArgReturningVoidDelegate(string text);
```

```vb
' This delegate enables asynchronous calls for setting
' the text property on a TextBox control.
Delegate Sub StringArgReturningVoidDelegate([text] As String)
```

```cpp
// This delegate enables asynchronous calls for setting
// the text property on a TextBox control.
delegate void StringArgReturningVoidDelegate(String^ text);
```

```csharp
// This method demonstrates a pattern for making thread-safe
// calls on a Windows Forms control.
//
// If the calling thread is different from the thread that
// created the TextBox control, this method creates a
// StringArgReturningVoidDelegate and calls itself asynchronously using the
// Invoke method.
//
// If the calling thread is the same as the thread that created
// the TextBox control, the Text property is set directly.

private void SetText(string text)
{
    // InvokeRequired required compares the thread ID of the
    // calling thread to the thread ID of the creating thread.
    // If these threads are different, it returns true.
    if (this.textBox1.InvokeRequired)
    {
        StringArgReturningVoidDelegate d = new StringArgReturningVoidDelegate(SetText);
        this.Invoke(d, new object[] { text });
    }
    else
    {
        this.textBox1.Text = text;
    }
}
```

```vb
' This method demonstrates a pattern for making thread-safe
' calls on a Windows Forms control.
'
' If the calling thread is different from the thread that
' created the TextBox control, this method creates a
' StringArgReturningVoidDelegate and calls itself asynchronously using the
' Invoke method.
'
' If the calling thread is the same as the thread that created
 ' the TextBox control, the Text property is set directly.

 Private Sub SetText(ByVal [text] As String)

     ' InvokeRequired required compares the thread ID of the
     ' calling thread to the thread ID of the creating thread.
     ' If these threads are different, it returns true.
     If Me.textBox1.InvokeRequired Then
         Dim d As New StringArgReturningVoidDelegate(AddressOf SetText)
         Me.Invoke(d, New Object() {[text]})
     Else
         Me.textBox1.Text = [text]
     End If
 End Sub
```

```cpp
// This method demonstrates a pattern for making thread-safe
    // calls on a Windows Forms control.
    //
    // If the calling thread is different from the thread that
    // created the TextBox control, this method creates a
    // StringArgReturningVoidDelegate and calls itself asynchronously using the
    // Invoke method.
    //
    // If the calling thread is the same as the thread that created
    // the TextBox control, the Text property is set directly.

private:
    void SetText(String^ text)
    {
        // InvokeRequired required compares the thread ID of the
        // calling thread to the thread ID of the creating thread.
        // If these threads are different, it returns true.
        if (this->textBox1->InvokeRequired)
        {
            StringArgReturningVoidDelegate^ d =
                gcnew StringArgReturningVoidDelegate(this, &Form1::SetText);
            this->Invoke(d, gcnew array<Object^> { text });
        }
        else
        {
            this->textBox1->Text = text;
        }
    }
```

## <a name="making-thread-safe-calls-by-using-backgroundworker"></a><span data-ttu-id="63a31-127">Wykonywanie wywołań wątków przy użyciu BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="63a31-127">Making Thread-Safe Calls by using BackgroundWorker</span></span>
 <span data-ttu-id="63a31-128">Preferowany sposób implementacji wielowątkowości w aplikacji jest użycie <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="63a31-128">The preferred way to implement multithreading in your application is to use the <xref:System.ComponentModel.BackgroundWorker> component.</span></span> <span data-ttu-id="63a31-129"><xref:System.ComponentModel.BackgroundWorker> Składnik używa modelu sterowanego dla wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="63a31-129">The <xref:System.ComponentModel.BackgroundWorker> component uses an event-driven model for multithreading.</span></span> <span data-ttu-id="63a31-130">Jest uruchamiane w wątku w tle usługi <xref:System.ComponentModel.BackgroundWorker.DoWork> program obsługi zdarzeń i wątku, który tworzy przebiegów formantów swoje <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="63a31-130">The background thread runs your <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler, and the thread that creates your controls runs your <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handlers.</span></span> <span data-ttu-id="63a31-131">Możesz wywołać formantów z Twojej <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="63a31-131">You can call your controls from your <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handlers.</span></span>

#### <a name="to-make-thread-safe-calls-by-using-backgroundworker"></a><span data-ttu-id="63a31-132">Aby utworzyć wątkowo wywołania przy użyciu BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="63a31-132">To make thread-safe calls by using BackgroundWorker</span></span>

1.  <span data-ttu-id="63a31-133">Tworzenie metody, które wykonają tę pracę, który chcesz zrobić w wątku w tle.</span><span class="sxs-lookup"><span data-stu-id="63a31-133">Create a method to do the work that you want done in the background thread.</span></span> <span data-ttu-id="63a31-134">Nie wywołuj formantów utworzonych przez wątek główny w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="63a31-134">Do not call controls created by the main thread in this method.</span></span>

2.  <span data-ttu-id="63a31-135">Utwórz metodę, aby zgłosić wyników pracę w tle po jej zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="63a31-135">Create a method to report the results of your background work after it finishes.</span></span> <span data-ttu-id="63a31-136">Możesz wywołać formantów utworzonych przez wątek główny w przypadku tej metody.</span><span class="sxs-lookup"><span data-stu-id="63a31-136">You can call controls created by the main thread in this method.</span></span>

3.  <span data-ttu-id="63a31-137">BIND — metoda utworzonego w kroku 1, aby <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń wystąpienie <xref:System.ComponentModel.BackgroundWorker>i bind, metoda utworzony w kroku 2 tego samego wystąpienia <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="63a31-137">Bind the method created in step 1 to the <xref:System.ComponentModel.BackgroundWorker.DoWork> event of an instance of <xref:System.ComponentModel.BackgroundWorker>, and bind the method created in step 2 to the same instance’s <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>

4.  <span data-ttu-id="63a31-138">Aby uruchomić wątku w tle, należy wywołać <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody <xref:System.ComponentModel.BackgroundWorker> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="63a31-138">To start the background thread, call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of the <xref:System.ComponentModel.BackgroundWorker> instance.</span></span>

<span data-ttu-id="63a31-139">W poniższym przykładzie kodu <xref:System.ComponentModel.BackgroundWorker.DoWork> korzysta z programu obsługi zdarzeń <xref:System.Threading.Thread.Sleep%2A> do symulacji pracy, która zajmuje trochę czasu.</span><span class="sxs-lookup"><span data-stu-id="63a31-139">In the following code example, the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler uses <xref:System.Threading.Thread.Sleep%2A> to simulate work that takes some time.</span></span> <span data-ttu-id="63a31-140">Nie wywołuje formularza <xref:System.Windows.Forms.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="63a31-140">It does not call the form’s <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="63a31-141"><xref:System.Windows.Forms.TextBox> Kontrolki <xref:System.Windows.Forms.Control.Text%2A> właściwość jest ustawiona, bezpośrednio w <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="63a31-141">The <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.Text%2A> property is set directly in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

```csharp
// This BackgroundWorker is used to demonstrate the
// preferred way of performing asynchronous operations.
private BackgroundWorker backgroundWorker1;
```

```vb
' This BackgroundWorker is used to demonstrate the
' preferred way of performing asynchronous operations.
Private WithEvents backgroundWorker1 As BackgroundWorker
```

```cpp
// This BackgroundWorker is used to demonstrate the
    // preferred way of performing asynchronous operations.
private:
    BackgroundWorker^ backgroundWorker1;
```

```csharp
// This event handler starts the form's
// BackgroundWorker by calling RunWorkerAsync.
//
// The Text property of the TextBox control is set
// when the BackgroundWorker raises the RunWorkerCompleted
// event.
private void setTextBackgroundWorkerBtn_Click(
    object sender,
    EventArgs e)
{
    this.backgroundWorker1.RunWorkerAsync();
}

// This event handler sets the Text property of the TextBox
// control. It is called on the thread that created the
// TextBox control, so the call is thread-safe.
//
// BackgroundWorker is the preferred way to perform asynchronous
// operations.

private void backgroundWorker1_RunWorkerCompleted(
    object sender,
    RunWorkerCompletedEventArgs e)
{
    this.textBox1.Text =
        "This text was set safely by BackgroundWorker.";
}
```

```vb
' This event handler starts the form's
' BackgroundWorker by calling RunWorkerAsync.
'
' The Text property of the TextBox control is set
' when the BackgroundWorker raises the RunWorkerCompleted
' event.
 Private Sub setTextBackgroundWorkerBtn_Click( _
 ByVal sender As Object, _
 ByVal e As EventArgs) Handles setTextBackgroundWorkerBtn.Click
     Me.backgroundWorker1.RunWorkerAsync()
 End Sub

' This event handler sets the Text property of the TextBox
' control. It is called on the thread that created the
' TextBox control, so the call is thread-safe.
'
' BackgroundWorker is the preferred way to perform asynchronous
' operations.
 Private Sub backgroundWorker1_RunWorkerCompleted( _
 ByVal sender As Object, _
 ByVal e As RunWorkerCompletedEventArgs) _
 Handles backgroundWorker1.RunWorkerCompleted
     Me.textBox1.Text = _
     "This text was set safely by BackgroundWorker."
 End Sub
```

```cpp
// This event handler starts the form's
    // BackgroundWorker by calling RunWorkerAsync.
    //
    // The Text property of the TextBox control is set
    // when the BackgroundWorker raises the RunWorkerCompleted
    // event.
private:
    void setTextBackgroundWorkerBtn_Click(Object^ sender, EventArgs^ e)
    {
        this->backgroundWorker1->RunWorkerAsync();
    }

    // This event handler sets the Text property of the TextBox
    // control. It is called on the thread that created the
    // TextBox control, so the call is thread-safe.
    //
    // BackgroundWorker is the preferred way to perform asynchronous
    // operations.

private:
    void backgroundWorker1_RunWorkerCompleted(
        Object^ sender,
        RunWorkerCompletedEventArgs^ e)
    {
        this->textBox1->Text =
            "This text was set safely by BackgroundWorker.";
    }
```

 <span data-ttu-id="63a31-142">Możesz zgłaszać także postępu zadania w tle za pomocą <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="63a31-142">You can also report the progress of a background task by using the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span> <span data-ttu-id="63a31-143">Na przykład, który zawiera zdarzenie, zobacz <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="63a31-143">For an example that incorporates that event, see <xref:System.ComponentModel.BackgroundWorker>.</span></span>

## <a name="example"></a><span data-ttu-id="63a31-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="63a31-144">Example</span></span>
 <span data-ttu-id="63a31-145">Poniższy przykład kodu jest kompletna aplikacja Windows Forms, która składa się z formularza przy użyciu trzech przycisków i jedno pole tekstowe.</span><span class="sxs-lookup"><span data-stu-id="63a31-145">The following code example is a complete Windows Forms application that consists of a form with three buttons and one text box.</span></span> <span data-ttu-id="63a31-146">Pierwszy pokazuje niebezpieczny dostęp między wątkami, drugi przycisk pokazuje bezpieczny dostęp za pomocą <xref:System.Windows.Forms.Control.Invoke%2A>, a trzeci przycisk pokazuje bezpieczny dostęp przy użyciu <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="63a31-146">The first button demonstrates unsafe cross-thread access, the second button demonstrates safe access by using <xref:System.Windows.Forms.Control.Invoke%2A>, and the third button demonstrates safe access by using <xref:System.ComponentModel.BackgroundWorker>.</span></span>

> [!NOTE]
> <span data-ttu-id="63a31-147">Aby uzyskać instrukcje na temat sposobu uruchamiania przykładu, zobacz [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/cc447f7e-4c3b-4397-9d05-aeba3ca49416).</span><span class="sxs-lookup"><span data-stu-id="63a31-147">For instructions on how to run the example, see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/cc447f7e-4c3b-4397-9d05-aeba3ca49416).</span></span> <span data-ttu-id="63a31-148">W tym przykładzie wymaga odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="63a31-148">This example requires references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

```csharp
using System;
using System.ComponentModel;
using System.Threading;
using System.Windows.Forms;

namespace CrossThreadDemo
{
    public class Form1 : Form
    {
        // This delegate enables asynchronous calls for setting
        // the text property on a TextBox control.
        delegate void StringArgReturningVoidDelegate(string text);

        // This thread is used to demonstrate both thread-safe and
        // unsafe ways to call a Windows Forms control.
        private Thread demoThread = null;

        // This BackgroundWorker is used to demonstrate the
        // preferred way of performing asynchronous operations.
        private BackgroundWorker backgroundWorker1;

        private TextBox textBox1;
        private Button setTextUnsafeBtn;
        private Button setTextSafeBtn;
        private Button setTextBackgroundWorkerBtn;

        private System.ComponentModel.IContainer components = null;

        public Form1()
        {
            InitializeComponent();
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing && (components != null))
            {
                components.Dispose();
            }
            base.Dispose(disposing);
        }

        // This event handler creates a thread that calls a
        // Windows Forms control in an unsafe way.
        private void setTextUnsafeBtn_Click(
            object sender,
            EventArgs e)
        {
            this.demoThread =
                new Thread(new ThreadStart(this.ThreadProcUnsafe));

            this.demoThread.Start();
        }

        // This method is executed on the worker thread and makes
        // an unsafe call on the TextBox control.
        private void ThreadProcUnsafe()
        {
            this.textBox1.Text = "This text was set unsafely.";
        }

        // This event handler creates a thread that calls a
        // Windows Forms control in a thread-safe way.
        private void setTextSafeBtn_Click(
            object sender,
            EventArgs e)
        {
            this.demoThread =
                new Thread(new ThreadStart(this.ThreadProcSafe));

            this.demoThread.Start();
        }

        // This method is executed on the worker thread and makes
        // a thread-safe call on the TextBox control.
        private void ThreadProcSafe()
        {
            this.SetText("This text was set safely.");
        }

        // This method demonstrates a pattern for making thread-safe
        // calls on a Windows Forms control.
        //
        // If the calling thread is different from the thread that
        // created the TextBox control, this method creates a
        // StringArgReturningVoidDelegate and calls itself asynchronously using the
        // Invoke method.
        //
        // If the calling thread is the same as the thread that created
        // the TextBox control, the Text property is set directly.

        private void SetText(string text)
        {
            // InvokeRequired required compares the thread ID of the
            // calling thread to the thread ID of the creating thread.
            // If these threads are different, it returns true.
            if (this.textBox1.InvokeRequired)
            {
                StringArgReturningVoidDelegate d = new StringArgReturningVoidDelegate(SetText);
                this.Invoke(d, new object[] { text });
            }
            else
            {
                this.textBox1.Text = text;
            }
        }

        // This event handler starts the form's
        // BackgroundWorker by calling RunWorkerAsync.
        //
        // The Text property of the TextBox control is set
        // when the BackgroundWorker raises the RunWorkerCompleted
        // event.
        private void setTextBackgroundWorkerBtn_Click(
            object sender,
            EventArgs e)
        {
            this.backgroundWorker1.RunWorkerAsync();
        }

        // This event handler sets the Text property of the TextBox
        // control. It is called on the thread that created the
        // TextBox control, so the call is thread-safe.
        //
        // BackgroundWorker is the preferred way to perform asynchronous
        // operations.

        private void backgroundWorker1_RunWorkerCompleted(
            object sender,
            RunWorkerCompletedEventArgs e)
        {
            this.textBox1.Text =
                "This text was set safely by BackgroundWorker.";
        }

        #region Windows Form Designer generated code

        private void InitializeComponent()
        {
            this.textBox1 = new System.Windows.Forms.TextBox();
            this.setTextUnsafeBtn = new System.Windows.Forms.Button();
            this.setTextSafeBtn = new System.Windows.Forms.Button();
            this.setTextBackgroundWorkerBtn = new System.Windows.Forms.Button();
            this.backgroundWorker1 = new System.ComponentModel.BackgroundWorker();
            this.SuspendLayout();
            //
            // textBox1
            //
            this.textBox1.Location = new System.Drawing.Point(12, 12);
            this.textBox1.Name = "textBox1";
            this.textBox1.Size = new System.Drawing.Size(240, 20);
            this.textBox1.TabIndex = 0;
            //
            // setTextUnsafeBtn
            //
            this.setTextUnsafeBtn.Location = new System.Drawing.Point(15, 55);
            this.setTextUnsafeBtn.Name = "setTextUnsafeBtn";
            this.setTextUnsafeBtn.TabIndex = 1;
            this.setTextUnsafeBtn.Text = "Unsafe Call";
            this.setTextUnsafeBtn.Click += new System.EventHandler(this.setTextUnsafeBtn_Click);
            //
            // setTextSafeBtn
            //
            this.setTextSafeBtn.Location = new System.Drawing.Point(96, 55);
            this.setTextSafeBtn.Name = "setTextSafeBtn";
            this.setTextSafeBtn.TabIndex = 2;
            this.setTextSafeBtn.Text = "Safe Call";
            this.setTextSafeBtn.Click += new System.EventHandler(this.setTextSafeBtn_Click);
            //
            // setTextBackgroundWorkerBtn
            //
            this.setTextBackgroundWorkerBtn.Location = new System.Drawing.Point(177, 55);
            this.setTextBackgroundWorkerBtn.Name = "setTextBackgroundWorkerBtn";
            this.setTextBackgroundWorkerBtn.TabIndex = 3;
            this.setTextBackgroundWorkerBtn.Text = "Safe BW Call";
            this.setTextBackgroundWorkerBtn.Click += new System.EventHandler(this.setTextBackgroundWorkerBtn_Click);
            //
            // backgroundWorker1
            //
            this.backgroundWorker1.RunWorkerCompleted += new System.ComponentModel.RunWorkerCompletedEventHandler(this.backgroundWorker1_RunWorkerCompleted);
            //
            // Form1
            //
            this.ClientSize = new System.Drawing.Size(268, 96);
            this.Controls.Add(this.setTextBackgroundWorkerBtn);
            this.Controls.Add(this.setTextSafeBtn);
            this.Controls.Add(this.setTextUnsafeBtn);
            this.Controls.Add(this.textBox1);
            this.Name = "Form1";
            this.Text = "Form1";
            this.ResumeLayout(false);
            this.PerformLayout();

        }

        #endregion

        [STAThread]
        static void Main()
        {
            Application.EnableVisualStyles();
            Application.Run(new Form1());
        }

    }
}
```

```vb
Imports System
Imports System.ComponentModel
Imports System.Threading
Imports System.Windows.Forms

Public Class Form1
   Inherits Form

   ' This delegate enables asynchronous calls for setting
   ' the text property on a TextBox control.
   Delegate Sub StringArgReturningVoidDelegate([text] As String)

   ' This thread is used to demonstrate both thread-safe and
   ' unsafe ways to call a Windows Forms control.
   Private demoThread As Thread = Nothing

   ' This BackgroundWorker is used to demonstrate the
   ' preferred way of performing asynchronous operations.
   Private WithEvents backgroundWorker1 As BackgroundWorker

   Private textBox1 As TextBox
   Private WithEvents setTextUnsafeBtn As Button
   Private WithEvents setTextSafeBtn As Button
   Private WithEvents setTextBackgroundWorkerBtn As Button

   Private components As System.ComponentModel.IContainer = Nothing

   Public Sub New()
      InitializeComponent()
    End Sub

   Protected Overrides Sub Dispose(disposing As Boolean)
      If disposing AndAlso (components IsNot Nothing) Then
         components.Dispose()
      End If
      MyBase.Dispose(disposing)
    End Sub

   ' This event handler creates a thread that calls a
   ' Windows Forms control in an unsafe way.
    Private Sub setTextUnsafeBtn_Click( _
    ByVal sender As Object, _
    ByVal e As EventArgs) Handles setTextUnsafeBtn.Click

        Me.demoThread = New Thread( _
        New ThreadStart(AddressOf Me.ThreadProcUnsafe))

        Me.demoThread.Start()
    End Sub

   ' This method is executed on the worker thread and makes
   ' an unsafe call on the TextBox control.
   Private Sub ThreadProcUnsafe()
      Me.textBox1.Text = "This text was set unsafely."
   End Sub

   ' This event handler creates a thread that calls a
   ' Windows Forms control in a thread-safe way.
    Private Sub setTextSafeBtn_Click( _
    ByVal sender As Object, _
    ByVal e As EventArgs) Handles setTextSafeBtn.Click

        Me.demoThread = New Thread( _
        New ThreadStart(AddressOf Me.ThreadProcSafe))

        Me.demoThread.Start()
    End Sub

   ' This method is executed on the worker thread and makes
   ' a thread-safe call on the TextBox control.
   Private Sub ThreadProcSafe()
      Me.SetText("This text was set safely.")
    End Sub

   ' This method demonstrates a pattern for making thread-safe
   ' calls on a Windows Forms control.
   '
   ' If the calling thread is different from the thread that
   ' created the TextBox control, this method creates a
   ' StringArgReturningVoidDelegate and calls itself asynchronously using the
   ' Invoke method.
   '
   ' If the calling thread is the same as the thread that created
    ' the TextBox control, the Text property is set directly.

    Private Sub SetText(ByVal [text] As String)

        ' InvokeRequired required compares the thread ID of the
        ' calling thread to the thread ID of the creating thread.
        ' If these threads are different, it returns true.
        If Me.textBox1.InvokeRequired Then
            Dim d As New StringArgReturningVoidDelegate(AddressOf SetText)
            Me.Invoke(d, New Object() {[text]})
        Else
            Me.textBox1.Text = [text]
        End If
    End Sub

   ' This event handler starts the form's
   ' BackgroundWorker by calling RunWorkerAsync.
   '
   ' The Text property of the TextBox control is set
   ' when the BackgroundWorker raises the RunWorkerCompleted
   ' event.
    Private Sub setTextBackgroundWorkerBtn_Click( _
    ByVal sender As Object, _
    ByVal e As EventArgs) Handles setTextBackgroundWorkerBtn.Click
        Me.backgroundWorker1.RunWorkerAsync()
    End Sub

   ' This event handler sets the Text property of the TextBox
   ' control. It is called on the thread that created the
   ' TextBox control, so the call is thread-safe.
   '
   ' BackgroundWorker is the preferred way to perform asynchronous
   ' operations.
    Private Sub backgroundWorker1_RunWorkerCompleted( _
    ByVal sender As Object, _
    ByVal e As RunWorkerCompletedEventArgs) _
    Handles backgroundWorker1.RunWorkerCompleted
        Me.textBox1.Text = _
        "This text was set safely by BackgroundWorker."
    End Sub

   #Region "Windows Form Designer generated code"

   Private Sub InitializeComponent()
      Me.textBox1 = New System.Windows.Forms.TextBox()
      Me.setTextUnsafeBtn = New System.Windows.Forms.Button()
      Me.setTextSafeBtn = New System.Windows.Forms.Button()
      Me.setTextBackgroundWorkerBtn = New System.Windows.Forms.Button()
      Me.backgroundWorker1 = New System.ComponentModel.BackgroundWorker()
      Me.SuspendLayout()
      '
      ' textBox1
      '
      Me.textBox1.Location = New System.Drawing.Point(12, 12)
      Me.textBox1.Name = "textBox1"
      Me.textBox1.Size = New System.Drawing.Size(240, 20)
      Me.textBox1.TabIndex = 0
      '
      ' setTextUnsafeBtn
      '
      Me.setTextUnsafeBtn.Location = New System.Drawing.Point(15, 55)
      Me.setTextUnsafeBtn.Name = "setTextUnsafeBtn"
      Me.setTextUnsafeBtn.TabIndex = 1
      Me.setTextUnsafeBtn.Text = "Unsafe Call"
      '
      ' setTextSafeBtn
      '
      Me.setTextSafeBtn.Location = New System.Drawing.Point(96, 55)
      Me.setTextSafeBtn.Name = "setTextSafeBtn"
      Me.setTextSafeBtn.TabIndex = 2
      Me.setTextSafeBtn.Text = "Safe Call"
      '
      ' setTextBackgroundWorkerBtn
      '
      Me.setTextBackgroundWorkerBtn.Location = New System.Drawing.Point(177, 55)
      Me.setTextBackgroundWorkerBtn.Name = "setTextBackgroundWorkerBtn"
      Me.setTextBackgroundWorkerBtn.TabIndex = 3
      Me.setTextBackgroundWorkerBtn.Text = "Safe BW Call"
      '
      ' backgroundWorker1
      '
      '
      ' Form1
      '
      Me.ClientSize = New System.Drawing.Size(268, 96)
      Me.Controls.Add(setTextBackgroundWorkerBtn)
      Me.Controls.Add(setTextSafeBtn)
      Me.Controls.Add(setTextUnsafeBtn)
      Me.Controls.Add(textBox1)
      Me.Name = "Form1"
      Me.Text = "Form1"
      Me.ResumeLayout(False)
      Me.PerformLayout()
   End Sub 'InitializeComponent

   #End Region

   <STAThread()>  _
   Shared Sub Main()
      Application.EnableVisualStyles()
      Application.Run(New Form1())
    End Sub
End Class
```

```cpp
#using <System.dll>
#using <System.Windows.Forms.dll>
#using <System.Drawing.dll>

using namespace System;
using namespace System::ComponentModel;
using namespace System::Threading;
using namespace System::Windows::Forms;

namespace CrossThreadDemo
{
    public ref class Form1 : public Form
    {
        // This delegate enables asynchronous calls for setting
        // the text property on a TextBox control.
        delegate void StringArgReturningVoidDelegate(String^ text);

        // This thread is used to demonstrate both thread-safe and
        // unsafe ways to call a Windows Forms control.
    private:
        Thread^ demoThread;

        // This BackgroundWorker is used to demonstrate the
        // preferred way of performing asynchronous operations.
    private:
        BackgroundWorker^ backgroundWorker1;

    private:
        TextBox^ textBox1;
    private:
        Button^ setTextUnsafeBtn;
    private:
        Button^ setTextSafeBtn;
    private:
        Button^ setTextBackgroundWorkerBtn;

    private:
        System::ComponentModel::IContainer^ components;

    public:
        Form1()
        {
            components = nullptr;
            InitializeComponent();
        }

    protected:
        ~Form1()
        {
            if (components != nullptr)
            {
                delete components;
            }
        }

        // This event handler creates a thread that calls a
        // Windows Forms control in an unsafe way.
    private:
        void setTextUnsafeBtn_Click(Object^ sender, EventArgs^ e)
        {
            this->demoThread =
                gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcUnsafe));

            this->demoThread->Start();
        }

        // This method is executed on the worker thread and makes
        // an unsafe call on the TextBox control.
    private:
        void ThreadProcUnsafe()
        {
            this->textBox1->Text = "This text was set unsafely.";
        }

        // This event handler creates a thread that calls a
        // Windows Forms control in a thread-safe way.
    private:
        void setTextSafeBtn_Click(Object^ sender, EventArgs^ e)
        {
            this->demoThread =
                gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcSafe));

            this->demoThread->Start();
        }

        // This method is executed on the worker thread and makes
        // a thread-safe call on the TextBox control.
    private:
        void ThreadProcSafe()
        {
            this->SetText("This text was set safely.");
        }

        // This method demonstrates a pattern for making thread-safe
        // calls on a Windows Forms control.
        //
        // If the calling thread is different from the thread that
        // created the TextBox control, this method creates a
        // StringArgReturningVoidDelegate and calls itself asynchronously using the
        // Invoke method.
        //
        // If the calling thread is the same as the thread that created
        // the TextBox control, the Text property is set directly.

    private:
        void SetText(String^ text)
        {
            // InvokeRequired required compares the thread ID of the
            // calling thread to the thread ID of the creating thread.
            // If these threads are different, it returns true.
            if (this->textBox1->InvokeRequired)
            {
                StringArgReturningVoidDelegate^ d =
                    gcnew StringArgReturningVoidDelegate(this, &Form1::SetText);
                this->Invoke(d, gcnew array<Object^> { text });
            }
            else
            {
                this->textBox1->Text = text;
            }
        }

        // This event handler starts the form's
        // BackgroundWorker by calling RunWorkerAsync.
        //
        // The Text property of the TextBox control is set
        // when the BackgroundWorker raises the RunWorkerCompleted
        // event.
    private:
        void setTextBackgroundWorkerBtn_Click(Object^ sender, EventArgs^ e)
        {
            this->backgroundWorker1->RunWorkerAsync();
        }

        // This event handler sets the Text property of the TextBox
        // control. It is called on the thread that created the
        // TextBox control, so the call is thread-safe.
        //
        // BackgroundWorker is the preferred way to perform asynchronous
        // operations.

    private:
        void backgroundWorker1_RunWorkerCompleted(
            Object^ sender,
            RunWorkerCompletedEventArgs^ e)
        {
            this->textBox1->Text =
                "This text was set safely by BackgroundWorker.";
        }

        #pragma region Windows Form Designer generated code

    private:
        void InitializeComponent()
        {
            this->textBox1 = gcnew System::Windows::Forms::TextBox();
            this->setTextUnsafeBtn = gcnew System::Windows::Forms::Button();
            this->setTextSafeBtn = gcnew System::Windows::Forms::Button();
            this->setTextBackgroundWorkerBtn =
                gcnew System::Windows::Forms::Button();
            this->backgroundWorker1 =
                gcnew System::ComponentModel::BackgroundWorker();
            this->SuspendLayout();
            //
            // textBox1
            //
            this->textBox1->Location = System::Drawing::Point(12, 12);
            this->textBox1->Name = "textBox1";
            this->textBox1->Size = System::Drawing::Size(240, 20);
            this->textBox1->TabIndex = 0;
            //
            // setTextUnsafeBtn
            //
            this->setTextUnsafeBtn->Location = System::Drawing::Point(15, 55);
            this->setTextUnsafeBtn->Name = "setTextUnsafeBtn";
            this->setTextUnsafeBtn->TabIndex = 1;
            this->setTextUnsafeBtn->Text = "Unsafe Call";
            this->setTextUnsafeBtn->Click +=
                gcnew System::EventHandler(
                this,&Form1::setTextUnsafeBtn_Click);
            //
            // setTextSafeBtn
            //
            this->setTextSafeBtn->Location = System::Drawing::Point(96, 55);
            this->setTextSafeBtn->Name = "setTextSafeBtn";
            this->setTextSafeBtn->TabIndex = 2;
            this->setTextSafeBtn->Text = "Safe Call";
            this->setTextSafeBtn->Click +=
                gcnew System::EventHandler(this,&Form1::setTextSafeBtn_Click);
            //
            // setTextBackgroundWorkerBtn
            //
            this->setTextBackgroundWorkerBtn->Location =
                System::Drawing::Point(177, 55);
            this->setTextBackgroundWorkerBtn->Name =
                "setTextBackgroundWorkerBtn";
            this->setTextBackgroundWorkerBtn->TabIndex = 3;
            this->setTextBackgroundWorkerBtn->Text = "Safe BW Call";
            this->setTextBackgroundWorkerBtn->Click +=
                gcnew System::EventHandler(
                this,&Form1::setTextBackgroundWorkerBtn_Click);
            //
            // backgroundWorker1
            //
            this->backgroundWorker1->RunWorkerCompleted +=
                gcnew System::ComponentModel::RunWorkerCompletedEventHandler(
                this,&Form1::backgroundWorker1_RunWorkerCompleted);
            //
            // Form1
            //
            this->ClientSize = System::Drawing::Size(268, 96);
            this->Controls->Add(this->setTextBackgroundWorkerBtn);
            this->Controls->Add(this->setTextSafeBtn);
            this->Controls->Add(this->setTextUnsafeBtn);
            this->Controls->Add(this->textBox1);
            this->Name = "Form1";
            this->Text = "Form1";
            this->ResumeLayout(false);
            this->PerformLayout();

        }

        #pragma endregion
    };
}

[STAThread]
int main()
{
    Application::EnableVisualStyles();
    Application::Run(gcnew CrossThreadDemo::Form1());
}
```

<span data-ttu-id="63a31-149">Po uruchomieniu aplikacji i kliknij przycisk **niebezpiecznych wywołań** przycisku można natychmiast zobaczyć "Written przez wątek główny" w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="63a31-149">When you run the application and click the **Unsafe Call** button, you immediately see "Written by the main thread" in the text box.</span></span> <span data-ttu-id="63a31-150">Dwóch sekund później, gdy podejmowana jest próba niebezpiecznych wywołań, debuger programu Visual Studio wskazuje, że wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="63a31-150">Two seconds later, when the unsafe call is attempted, the Visual Studio debugger indicates that an exception occurred.</span></span> <span data-ttu-id="63a31-151">Debuger zatrzymuje się w wierszu w wątku w tle, który podjął próbę zapisu bezpośrednio do pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="63a31-151">The debugger stops at the line in the background thread that attempted to write directly to the text box.</span></span> <span data-ttu-id="63a31-152">Trzeba będzie ponownie uruchomić aplikację, aby przetestować dwa przyciski.</span><span class="sxs-lookup"><span data-stu-id="63a31-152">You will have to restart the application to test the other two buttons.</span></span> <span data-ttu-id="63a31-153">Po kliknięciu **bezpieczne wywołanie** przycisku "Napisane przez wątek główny" pojawia się w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="63a31-153">When you click the **Safe Call** button, "Written by the main thread" appears in the text box.</span></span> <span data-ttu-id="63a31-154">Dwóch sekund później, w polu tekstowym jest ustawiona na "Written przez wątek w tle (Wywołaj)", który wskazuje, że <xref:System.Windows.Forms.Control.Invoke%2A> metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="63a31-154">Two seconds later, the text box is set to "Written by the background thread (Invoke)", which indicates that the <xref:System.Windows.Forms.Control.Invoke%2A> method was called.</span></span> <span data-ttu-id="63a31-155">Po kliknięciu **bezpieczne wywołanie BW** przycisku "Napisane przez wątek główny" pojawia się w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="63a31-155">When you click the **Safe BW Call** button, "Written by the main thread" appears in the text box.</span></span> <span data-ttu-id="63a31-156">Dwóch sekund później, w polu tekstowym jest ustawiona na "Written za główny wątek po wątku w tle", który wskazuje, że obsługa <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenia <xref:System.ComponentModel.BackgroundWorker> została wywołana.</span><span class="sxs-lookup"><span data-stu-id="63a31-156">Two seconds later, the text box is set to "Written by the main thread after the background thread completed", which indicates that the handler for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event of <xref:System.ComponentModel.BackgroundWorker> was called.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="63a31-157">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="63a31-157">Robust Programming</span></span>

> [!CAUTION]
> <span data-ttu-id="63a31-158">Kiedy używać wielowątkowości jakiegokolwiek rodzaju, Twój kod może być narażony na błędy bardzo poważne i złożone.</span><span class="sxs-lookup"><span data-stu-id="63a31-158">When you use multithreading of any sort, your code can be exposed to very serious and complex bugs.</span></span> <span data-ttu-id="63a31-159">Aby uzyskać więcej informacji, zobacz [zarządzana wątkowość najlepsze](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem dowolne rozwiązanie, który używa wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="63a31-159">For more information, see [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before you implement any solution that uses multithreading.</span></span>

## <a name="see-also"></a><span data-ttu-id="63a31-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63a31-160">See Also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="63a31-161">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="63a31-161">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="63a31-162">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="63a31-162">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="63a31-163">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="63a31-163">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="63a31-164">Formularze Windows Forms i niezarządzane aplikacje</span><span class="sxs-lookup"><span data-stu-id="63a31-164">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
