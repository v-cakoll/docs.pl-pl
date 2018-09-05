---
title: 'Porady: uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
ms.openlocfilehash: bf0e22eab3b6517521dbe06a73f63af232746df1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540552"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a><span data-ttu-id="22bb7-102">Porady: uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="22bb7-102">How to: Run Procedures at Set Intervals with the Windows Forms Timer Component</span></span>
<span data-ttu-id="22bb7-103">Czasami warto utworzyć procedurę, która działa w określonych odstępach czasu, aż do zakończenia pętli lub, które jest uruchamiane po upływie Ustaw interwał czasu.</span><span class="sxs-lookup"><span data-stu-id="22bb7-103">You might sometimes want to create a procedure that runs at specific time intervals until a loop has finished or that runs when a set time interval has elapsed.</span></span> <span data-ttu-id="22bb7-104"><xref:System.Windows.Forms.Timer> Składnika sprawia, że taka procedura jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="22bb7-104">The <xref:System.Windows.Forms.Timer> component makes such a procedure possible.</span></span>  
  
 <span data-ttu-id="22bb7-105">Ten składnik jest przeznaczony dla środowiska Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="22bb7-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="22bb7-106">Jeśli potrzebujesz czasomierza, która jest odpowiednia w środowisku serwera, zobacz [wprowadzenie do serwerowych czasomierzy](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="22bb7-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22bb7-107">Istnieją pewne ograniczenia w przypadku korzystania z <xref:System.Windows.Forms.Timer> składnika.</span><span class="sxs-lookup"><span data-stu-id="22bb7-107">There are some limitations when using the <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="22bb7-108">Aby uzyskać więcej informacji, zobacz [ograniczenia właściwości Interval składnika Timer formularzy Windows](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).</span><span class="sxs-lookup"><span data-stu-id="22bb7-108">For more information, see [Limitations of the Windows Forms Timer Component's Interval Property](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).</span></span>  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a><span data-ttu-id="22bb7-109">Do uruchamiania procedur w ustalonych odstępach czasu za pomocą składnika Timer</span><span class="sxs-lookup"><span data-stu-id="22bb7-109">To run a procedure at set intervals with the Timer component</span></span>  
  
1.  <span data-ttu-id="22bb7-110">Dodaj <xref:System.Windows.Forms.Timer> do formularza.</span><span class="sxs-lookup"><span data-stu-id="22bb7-110">Add a <xref:System.Windows.Forms.Timer> to your form.</span></span> <span data-ttu-id="22bb7-111">Zobacz w poniższej sekcji przykład ilustrację jak to zrobić programowo.</span><span class="sxs-lookup"><span data-stu-id="22bb7-111">See the following Example section for an illustration of how to do this programmatically.</span></span> <span data-ttu-id="22bb7-112">Programu Visual Studio zapewnia również obsługę dodawania składników do formularza.</span><span class="sxs-lookup"><span data-stu-id="22bb7-112">Visual Studio also has support for adding components to a form.</span></span> <span data-ttu-id="22bb7-113">Zobacz też [porady: dodawanie formantów bez interfejsu użytkownika do formularzy Windows Forms](https://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="22bb7-113">Also see [How to: Add Controls Without a User Interface to Windows Forms](https://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).</span></span>  
  
2.  <span data-ttu-id="22bb7-114">Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości (w milisekundach) dla czasomierza.</span><span class="sxs-lookup"><span data-stu-id="22bb7-114">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property (in milliseconds) for the timer.</span></span> <span data-ttu-id="22bb7-115">Ta właściwość określa, ile czasu upłynie, zanim procedury po ponownym uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="22bb7-115">This property determines how much time will pass before the procedure is run again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="22bb7-116">Im częściej odbywa się zdarzenie czasomierza, większą ilość czasu procesora jest używany w zakresie reagowania na zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="22bb7-116">The more often a timer event occurs, the more processor time is used in responding to the event.</span></span> <span data-ttu-id="22bb7-117">Może to spowolnić ogólną wydajność.</span><span class="sxs-lookup"><span data-stu-id="22bb7-117">This can slow down overall performance.</span></span> <span data-ttu-id="22bb7-118">Nie należy ustawiać mniejszy przedział, niż potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="22bb7-118">Do not set a smaller interval than you need.</span></span>  
  
3.  <span data-ttu-id="22bb7-119">Wpisz odpowiedni kod w <xref:System.Windows.Forms.Timer.Tick> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="22bb7-119">Write appropriate code in the <xref:System.Windows.Forms.Timer.Tick> event handler.</span></span> <span data-ttu-id="22bb7-120">Kod pisany w tym przypadku będzie uruchamiany w momencie z interwałem określonym w <xref:System.Windows.Forms.Timer.Interval%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="22bb7-120">The code you write in this event will run at the interval specified in the <xref:System.Windows.Forms.Timer.Interval%2A> property.</span></span>  
  
4.  <span data-ttu-id="22bb7-121">Ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `true` do uruchomienia czasomierza.</span><span class="sxs-lookup"><span data-stu-id="22bb7-121">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true` to start the timer.</span></span> <span data-ttu-id="22bb7-122"><xref:System.Windows.Forms.Timer.Tick> Zdarzenie zostanie uruchomiony występuje, procedura w określonych interwałach.</span><span class="sxs-lookup"><span data-stu-id="22bb7-122">The <xref:System.Windows.Forms.Timer.Tick> event will begin to occur, running your procedure at the set interval.</span></span>  
  
5.  <span data-ttu-id="22bb7-123">W odpowiednim czasie, należy ustawić <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość `false` przestanie procedury z ponownym uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="22bb7-123">At the appropriate time, set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `false` to stop the procedure from running again.</span></span> <span data-ttu-id="22bb7-124">Ustawienie interwału `0` nie spowoduje zatrzymania czasomierza.</span><span class="sxs-lookup"><span data-stu-id="22bb7-124">Setting the interval to `0` does not cause the timer to stop.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22bb7-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="22bb7-125">Example</span></span>  
 <span data-ttu-id="22bb7-126">W pierwszym przykładzie kodu będzie śledził porę dnia zastosowaniem jednosekundowych przyrostów.</span><span class="sxs-lookup"><span data-stu-id="22bb7-126">This first code example tracks the time of day in one-second increments.</span></span> <span data-ttu-id="22bb7-127">Używa ona <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>, a <xref:System.Windows.Forms.Timer> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="22bb7-127">It uses a <xref:System.Windows.Forms.Button>, a <xref:System.Windows.Forms.Label>, and a <xref:System.Windows.Forms.Timer> component on a form.</span></span> <span data-ttu-id="22bb7-128"><xref:System.Windows.Forms.Timer.Interval%2A> Właściwość jest ustawiona na 1000 (równe 1 sekundy).</span><span class="sxs-lookup"><span data-stu-id="22bb7-128">The <xref:System.Windows.Forms.Timer.Interval%2A> property is set to 1000 (equal to one second).</span></span> <span data-ttu-id="22bb7-129">W <xref:System.Windows.Forms.Timer.Tick> zdarzenia podpis etykiety jest ustawiona na bieżącą godzinę.</span><span class="sxs-lookup"><span data-stu-id="22bb7-129">In the <xref:System.Windows.Forms.Timer.Tick> event, the label's caption is set to the current time.</span></span> <span data-ttu-id="22bb7-130">Po kliknięciu przycisku <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość jest ustawiona na `false`, zatrzymania czasomierza aktualizowania podpis etykiety.</span><span class="sxs-lookup"><span data-stu-id="22bb7-130">When the button is clicked, the <xref:System.Windows.Forms.Timer.Enabled%2A> property is set to `false`, stopping the timer from updating the label's caption.</span></span> <span data-ttu-id="22bb7-131">Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.Button> formantu o nazwie `Button1`, <xref:System.Windows.Forms.Timer> formantu o nazwie `Timer1`, a <xref:System.Windows.Forms.Label> formantu o nazwie `Label1`.</span><span class="sxs-lookup"><span data-stu-id="22bb7-131">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)     
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,    
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,   
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a><span data-ttu-id="22bb7-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="22bb7-132">Example</span></span>  
 <span data-ttu-id="22bb7-133">Ten drugi przykładowy kod uruchamia procedurę co 600 milisekund do momentu zakończenia pętli.</span><span class="sxs-lookup"><span data-stu-id="22bb7-133">This second code example runs a procedure every 600 milliseconds until a loop has finished.</span></span> <span data-ttu-id="22bb7-134">Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.Button> formantu o nazwie `Button1`, <xref:System.Windows.Forms.Timer> formantu o nazwie `Timer1`, a <xref:System.Windows.Forms.Label> formantu o nazwie `Label1`.</span><span class="sxs-lookup"><span data-stu-id="22bb7-134">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)     
{  
   if (counter >= 10)   
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)   
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="22bb7-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22bb7-135">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="22bb7-136">Timer, składnik</span><span class="sxs-lookup"><span data-stu-id="22bb7-136">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="22bb7-137">Timer, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="22bb7-137">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
