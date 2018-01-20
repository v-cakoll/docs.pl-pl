---
title: "Porady: bezpieczne wątkowo wywołania formantów formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7cca363be57e5c5022c70c62d876f62cebc6e9c0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Porady: bezpieczne wątkowo wywołania formantów formularzy systemu Windows
Jeśli używasz wielowątkowość Aby zwiększyć wydajność aplikacji formularzy systemu Windows, należy się upewnić, wprowadź wywołania do formantów w sposób zapewniający obsługę wielowątkowości.  
  
 Dostęp do formantów formularzy systemu Windows nie jest z założenia bezpieczne dla wątków. Jeśli masz dwa lub więcej wątków manipulowanie stan formantu, istnieje możliwość wymusić formantu w niespójnym stanie. Inne błędy związane z wątku zostały możliwości, takie jak warunki wyścigu i zakleszczenie. Należy się upewnić, że dostęp do formantów jest wykonywane w sposób zapewniający obsługę wielowątkowości.  
  
 Nie jest bezpieczne wywołania formantu z wątku innego niż ten, który go utworzył bez użycia <xref:System.Windows.Forms.Control.Invoke%2A> metody. Oto przykład połączenia, który nie jest bezpieczne dla wątków.  
  
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
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Ułatwia wykrywanie, gdy uzyskujesz dostęp do formantów w taki sposób, który nie jest bezpieczne dla wątków. Podczas korzystania z aplikacji w debugerze i wątku innego niż ten, który utworzył formantu próba wywołania, że formant, debuger zgłasza <xref:System.InvalidOperationException> z komunikatem "kontroli *nazwa formantu* dostępne z wątku innego niż wątek, który został utworzony na".  
  
 Ten wyjątek występuje niezawodnie podczas debugowania, a w pewnych okolicznościach, w czasie wykonywania. Podczas debugowania aplikacji, które zostało napisane z napotkać tego wyjątku [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] przed [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Zdecydowanie zaleca się rozwiązać ten problem, gdy zostanie wyświetlony, ale można ją wyłączyć, ustawiając <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> właściwości `false`. Powoduje to, że formant do uruchomienia, takie jak aplikacja może działać w programie Visual Studio .NET 2003 i [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)].  
  
> [!NOTE]
>  Jeśli używasz kontrolki ActiveX na formularzu, może pojawić się między wątkami <xref:System.InvalidOperationException> podczas uruchamiania w debugerze. W takim przypadku formantu ActiveX nie obsługuje wielowątkowości. Aby uzyskać więcej informacji o użyciu kontrolki ActiveX formularzy systemu Windows, zobacz [formularzy systemu Windows i niezarządzanych aplikacji](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md). Jeśli używasz programu Visual Studio, możesz uniknąć tego wyjątku przez wyłączenie procesu hostingu Visual Studio, zobacz [porady: wyłączanie procesu hostingu](/visualstudio/ide/how-to-disable-the-hosting-process).  
  
## <a name="making-thread-safe-calls-to-windows-forms-controls"></a>Formanty formularzy bezpieczne wątkowo wywołania do systemu Windows  
  
#### <a name="to-make-a-thread-safe-call-to-a-windows-forms-control"></a>Aby nawiązać połączenie bezpieczne wątkowo do formantu formularzy systemu Windows  
  
1.  Zapytanie formantu <xref:System.Windows.Forms.Control.InvokeRequired%2A> właściwości.  
  
2.  Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `true`, wywołaj <xref:System.Windows.Forms.Control.Invoke%2A> z delegatem, która sprawia, że rzeczywiste wywołanie do formantu.  
  
3.  Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `false`, bezpośrednio wywołać formantu.  
  
 W poniższym przykładzie, wywołanie wątkowo jest zaimplementowana w `ThreadProcSafe` metodę, która jest wykonywana przez wątek w tle. Jeśli <xref:System.Windows.Forms.TextBox> formantu <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `true`, `ThreadProcSafe` metoda tworzy wystąpienie `StringArgReturningVoidDelegate` i który przekazuje do formularza <xref:System.Windows.Forms.Control.Invoke%2A> metody. Powoduje to `SetText` metodę można wywołać w wątku, który utworzony <xref:System.Windows.Forms.TextBox> kontrolki w tym kontekście wątku <xref:System.Windows.Forms.Control.Text%2A> bezpośrednio ustawiono właściwość.  
  
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
  
## <a name="making-thread-safe-calls-by-using-backgroundworker"></a>Bezpieczne wątkowo wywołania przy użyciu BackgroundWorker  
 Preferowany sposób wdrażania wielowątkowości w aplikacji jest użycie <xref:System.ComponentModel.BackgroundWorker> składnika. <xref:System.ComponentModel.BackgroundWorker> Składnik używa modelu sterowane zdarzeniami dla wielowątkowości. Wątek w tle jest uruchamiana z <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń i wątku, który tworzy sekwencji formantów z <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> procedury obsługi zdarzeń. Możesz wywołać formantów z Twojej <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> procedury obsługi zdarzeń.  
  
#### <a name="to-make-thread-safe-calls-by-using-backgroundworker"></a>Aby utworzyć bezpieczne wątkowo wywołania przy użyciu BackgroundWorker  
  
1.  Tworzenie metody pracy, który ma w wątku w tle. Nie wywołuj formanty utworzone przez wątku głównego w ramach tej metody.  
  
2.  Tworzenie metody, aby zgłosić wyników Praca w tle po jej zakończeniu. Formanty utworzone przez wątku głównego w ramach tej metody można wywołać.  
  
3.  Metoda utworzonego w kroku 1, aby powiązać <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzenia wystąpienia <xref:System.ComponentModel.BackgroundWorker>i metodę utworzony w kroku 2, w tym samym wystąpieniu powiązania <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń.  
  
4.  Aby rozpocząć wątku w tle, należy wywołać <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody <xref:System.ComponentModel.BackgroundWorker> wystąpienia.  
  
 W poniższym przykładzie kodu <xref:System.ComponentModel.BackgroundWorker.DoWork> korzysta z programu obsługi zdarzeń <xref:System.Threading.Thread.Sleep%2A> symulowanie pracy, który wymaga pewnego czasu. Nie wywołuje formularza <xref:System.Windows.Forms.TextBox> formantu. <xref:System.Windows.Forms.TextBox> Formantu <xref:System.Windows.Forms.Control.Text%2A> ustawiono właściwość bezpośrednio w <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obsługi zdarzeń.  
  
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
  
 Możesz również zgłosić postęp zadania w tle przy użyciu <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń. Na przykład, która będzie zawierała tego zdarzenia, zobacz <xref:System.ComponentModel.BackgroundWorker>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod jest kompletna aplikacja formularzy systemu Windows, która składa się z formularza z trzech przycisków i jedno pole tekstowe. Pierwszy przycisk pokazuje niebezpieczny dostęp między wątkami, drugi przycisk pokazuje bezpieczny dostęp za pomocą <xref:System.Windows.Forms.Control.Invoke%2A>, i trzeci przycisk prezentuje bezpieczny dostęp przy użyciu <xref:System.ComponentModel.BackgroundWorker>.  
  
> [!NOTE]
>  Aby uzyskać instrukcje, jak uruchomić przykład, zobacz [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/cc447f7e-4c3b-4397-9d05-aeba3ca49416). W tym przykładzie wymaga odwołania do zestawów System.Drawing i System.Windows.Forms.  
  
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
  
 Po uruchomieniu aplikacji i kliknij przycisk **niebezpiecznych wywołań** przycisku, możesz od razu zobacz "Written przez wątku głównego" w polu tekstowym. Dwie sekundy później, podczas próby wywołania niebezpieczny debuger programu Visual Studio wskazuje, że wystąpił wyjątek. Zatrzymuje debuger w wierszu w wątku w tle, który próbowano zapisać bezpośrednio do pola tekstowego. Użytkownik będzie musiał ponownie uruchomić aplikację do testowania dwóch przycisków. Po kliknięciu **bezpieczne wywołania** przycisku "Napisane przez wątku głównego" pojawia się w polu tekstowym. Dwie sekundy później, pola tekstowego ma ustawioną wartość "Written przez wątek w tle (Invoke)", co oznacza, że <xref:System.Windows.Forms.Control.Invoke%2A> wywołano metodę. Po kliknięciu **bezpieczne wywołania BW** przycisku "Napisane przez wątku głównego" pojawia się w polu tekstowym. Dwie sekundy później, pola tekstowego ma ustawioną wartość "Written przez wątku głównego po zakończeniu wątku w tle", co oznacza, że program obsługi dla <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenia <xref:System.ComponentModel.BackgroundWorker> została wywołana.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
> [!CAUTION]
>  Jeśli używasz wielowątkowość jakiegokolwiek rodzaju kodu może być narażony na bardzo poważne i złożone usterki. Aby uzyskać więcej informacji, zobacz [zarządzanych wątków najlepsze rozwiązania w zakresie](../../../../docs/standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem rozwiązania, w którym używane wielowątkowości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Instrukcje: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Formularze Windows Forms i niezarządzane aplikacje](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
