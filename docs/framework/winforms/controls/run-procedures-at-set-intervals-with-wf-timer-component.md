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
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529017"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Porady: uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy systemu Windows
Czasami warto utworzyć procedurę, która działa w określonych odstępach czasu, aż do zakończenia pętli lub, które jest uruchamiane po upływie Ustaw interwał czasu. <xref:System.Windows.Forms.Timer> Składnika sprawia, że taka procedura jest możliwe.  
  
 Ten składnik jest przeznaczony dla środowiska Windows Forms. Jeśli potrzebujesz czasomierza, która jest odpowiednia w środowisku serwera, zobacz [wprowadzenie do serwerowych czasomierzy](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
> [!NOTE]
>  Istnieją pewne ograniczenia w przypadku korzystania z <xref:System.Windows.Forms.Timer> składnika. Aby uzyskać więcej informacji, zobacz [ograniczenia właściwości Interval składnika Timer formularzy Windows](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Do uruchamiania procedur w ustalonych odstępach czasu za pomocą składnika Timer  
  
1.  Dodaj <xref:System.Windows.Forms.Timer> do formularza. Zobacz w poniższej sekcji przykład ilustrację jak to zrobić programowo. Programu Visual Studio zapewnia również obsługę dodawania składników do formularza. Zobacz też [porady: dodawanie formantów bez interfejsu użytkownika do formularzy Windows Forms](https://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).  
  
2.  Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości (w milisekundach) dla czasomierza. Ta właściwość określa, ile czasu upłynie, zanim procedury po ponownym uruchomieniu.  
  
    > [!NOTE]
    >  Im częściej odbywa się zdarzenie czasomierza, większą ilość czasu procesora jest używany w zakresie reagowania na zdarzenia. Może to spowolnić ogólną wydajność. Nie należy ustawiać mniejszy przedział, niż potrzebujesz.  
  
3.  Wpisz odpowiedni kod w <xref:System.Windows.Forms.Timer.Tick> programu obsługi zdarzeń. Kod pisany w tym przypadku będzie uruchamiany w momencie z interwałem określonym w <xref:System.Windows.Forms.Timer.Interval%2A> właściwości.  
  
4.  Ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `true` do uruchomienia czasomierza. <xref:System.Windows.Forms.Timer.Tick> Zdarzenie zostanie uruchomiony występuje, procedura w określonych interwałach.  
  
5.  W odpowiednim czasie, należy ustawić <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość `false` przestanie procedury z ponownym uruchomieniem. Ustawienie interwału `0` nie spowoduje zatrzymania czasomierza.  
  
## <a name="example"></a>Przykład  
 W pierwszym przykładzie kodu będzie śledził porę dnia zastosowaniem jednosekundowych przyrostów. Używa ona <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>, a <xref:System.Windows.Forms.Timer> składnika w formularzu. <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość jest ustawiona na 1000 (równe 1 sekundy). W <xref:System.Windows.Forms.Timer.Tick> zdarzenia podpis etykiety jest ustawiona na bieżącą godzinę. Po kliknięciu przycisku <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość jest ustawiona na `false`, zatrzymania czasomierza aktualizowania podpis etykiety. Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.Button> formantu o nazwie `Button1`, <xref:System.Windows.Forms.Timer> formantu o nazwie `Timer1`, a <xref:System.Windows.Forms.Label> formantu o nazwie `Label1`.  
  
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
  
## <a name="example"></a>Przykład  
 Ten drugi przykładowy kod uruchamia procedurę co 600 milisekund do momentu zakończenia pętli. Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.Button> formantu o nazwie `Button1`, <xref:System.Windows.Forms.Timer> formantu o nazwie `Timer1`, a <xref:System.Windows.Forms.Label> formantu o nazwie `Label1`.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Timer>  
 [Timer, składnik](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Timer, składnik — omówienie](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
