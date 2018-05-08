---
title: 'Porady: dziedziczenie z istniejących formantów formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 6f35881bdb7a781d817c9f671962d0445bfd8e27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Porady: dziedziczenie z istniejących formantów formularzy systemu Windows
Jeśli chcesz rozszerzyć funkcjonalność istniejącego formantu, można utworzyć formantu pochodzące z istniejącej kontrolce przez dziedziczenie. Podczas dziedziczenia z istniejącego formantu, dziedziczą wszystkich funkcji i właściwości tego formantu. Na przykład, jeśli zostały Tworzenie formantu odziedziczone <xref:System.Windows.Forms.Button>, będzie wyglądać nowego formantu i działanie dokładnie tak jak standard <xref:System.Windows.Forms.Button> formantu. Następnie można rozszerzyć lub modyfikowanie funkcjonalności nowego formantu za pomocą implementacji niestandardowych metod i właściwości. W niektórych formantów, można zmienić wygląd formantu dziedziczone przez zastąpienie jej <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-inherited-control"></a>Aby utworzyć kontrolkę dziedziczonych  
  
1.  Utwórz nową **aplikacji Windows Forms** projektu.  
  
2.  Z **projektu** menu, wybierz **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
3.  W **Dodaj nowy element** okno dialogowe, kliknij dwukrotnie **formant niestandardowy**.  
  
     Formant niestandardowy jest dodawany do projektu.  
  
4.  Jeśli używasz języka Visual Basic w górnej części **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**. Rozwiń węzeł CustomControl1.vb, a następnie otwórz CustomControl1.Designer.vb w edytorze kodu.  
  
5.  Jeśli używasz języka C#, otwórz CustomControl1.cs w edytorze kodu.  
  
6.  Zlokalizuj deklaracji klasy, która dziedziczy od <xref:System.Windows.Forms.Control>.  
  
7.  Zmień formant, który ma być dziedziczona z klasy podstawowej.  
  
     Na przykład, jeśli ma być dziedziczona z <xref:System.Windows.Forms.Button>, zmień deklaracji klasy następująco:  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Jeśli używasz programu Visual Basic, Zapisz i zamknij CustomControl1.Designer.vb. Otwórz CustomControl1.vb w edytorze kodu.  
  
9. Implementowanie niestandardowych metod ani właściwości zawierające formantu.  
  
10. Jeśli chcesz zmodyfikować graficznego wygląd formantu, Zastąp <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
    > [!NOTE]
    >  Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> nie umożliwia modyfikowanie wyglądu wszystkich kontrolek. Te kontrolki, których wszystkie ich malowania wykonywanej przez system Windows (na przykład <xref:System.Windows.Forms.TextBox>) nigdy wywoływać ich <xref:System.Windows.Forms.Control.OnPaint%2A> metody i w związku z tym nigdy nie będzie używany niestandardowy kod. Zapoznaj się z dokumentacją pomocy dla określonego formantu, który chcesz zmodyfikować, aby sprawdzić, czy <xref:System.Windows.Forms.Control.OnPaint%2A> metoda jest dostępna. Aby uzyskać listę wszystkich kontrolek formularzy systemu Windows, zobacz [formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Jeśli formant nie ma <xref:System.Windows.Forms.Control.OnPaint%2A> wymieniony jako metodą member, nie można zmienić jego wygląd przez zastąpienie tej metody. Aby uzyskać więcej informacji o rysowania niestandardowych, zobacz [niestandardowych malowanie i renderowanie formantu](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
    ```vb  
    Protected Overrides Sub OnPaint(ByVal e As _  
       System.Windows.Forms.PaintEventArgs)  
       MyBase.OnPaint(e)  
       ' Insert code to do custom painting.   
       ' If you want to completely change the appearance of your control,  
       ' do not call MyBase.OnPaint(e).  
    End Sub  
    ```  
  
    ```csharp  
    protected override void OnPaint(PaintEventArgs pe)  
    {  
       base.OnPaint(pe);  
       // Insert code to do custom painting.  
       // If you want to completely change the appearance of your control,  
       // do not call base.OnPaint(pe).  
    }  
    ```  
  
11. Zapisz i przetestować formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Instrukcje: dziedziczenie z klasy kontrolek](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Instrukcje: dziedziczenie z klasy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
