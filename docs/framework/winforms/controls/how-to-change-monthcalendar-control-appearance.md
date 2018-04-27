---
title: 'Porady: Zmienianie formantu MonthCalendar formularzy systemu Windows&#39;wygląd s'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d2a3f12368d5215f7fe7611aa2f06e6b0fb1192
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a>Porady: Zmienianie formantu MonthCalendar formularzy systemu Windows&#39;wygląd s
Formularze systemu Windows <xref:System.Windows.Forms.MonthCalendar> formant umożliwia dostosowanie wyglądu kalendarza na wiele sposobów. Na przykład można ustawić schemat kolorów i wybierz wyświetlić lub ukryć numery tygodni i bieżącą datę.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Aby zmienić schemat kolorów kalendarza miesięcznego  
  
-   Ustaw właściwości, takie jak <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> i <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Właściwość również określa kolor czcionki dni tygodnia. <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Właściwość określa kolor daty, dla których przed i po wyświetlany miesiąc lub miesiące.  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  Uruchamianie z systemem Windows Vista i w zależności od motywu, niektóre właściwości mogą pozostać bez zmian wyglądu kalendarza. Na przykład, jeśli system Windows jest skonfigurowany używać kompozycji Aero, ustawienie <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, lub <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> właściwości nie ma wpływu. Jest to spowodowane zaktualizowaną wersję kalendarza jest odwzorowywany z wrażenie, że jest określana w czasie wykonywania na podstawie bieżącego motywu systemu operacyjnego. Jeśli chcesz użyć tych właściwości i Włącz starszą wersję kalendarza, można wyłączyć style wizualne dla aplikacji. Wyłączanie style wizualne mogą mieć wpływ na wygląd i zachowanie innych formantów w aplikacji. Aby wyłączyć style wizualne w języku Visual Basic, Otwórz w Projektancie projektu i usuń zaznaczenie pola wyboru **style wizualne XP włącz** pole wyboru. Aby wyłączyć style wizualne w języku C#, otwórz plik Program.cs i Oznacz jako komentarz `Application.EnableVisualStyles();`. Aby uzyskać więcej informacji na temat stylów wizualnych, zobacz [jak: włączyć style wizualne XP Windows](http://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Aby wyświetlić bieżącą datę w dolnej części kontrolki  
  
-   Ustaw <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> właściwości `true`. W poniższym przykładzie przełącza między wyświetlaniem i pominięcie dzisiejszej daty, gdy formularz zostanie dwukrotnie kliknięty.  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Aby wyświetlać numery tygodni  
  
-   Ustaw <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> właściwości `true`. W kodzie lub w oknie właściwości można ustawić tej właściwości.  
  
     Numery tygodni pojawiają się w oddzielnej kolumnie na lewo od pierwszego dnia tygodnia.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [MonthCalendar, kontrolka](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy Windows Forms](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [Instrukcje: wyświetlanie więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
