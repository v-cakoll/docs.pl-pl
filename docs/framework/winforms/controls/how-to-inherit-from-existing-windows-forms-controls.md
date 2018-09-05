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
ms.openlocfilehash: f19b207c840994ffa3aa364135583b5daeb26827
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542287"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Porady: dziedziczenie z istniejących formantów formularzy systemu Windows
Jeśli chcesz rozszerzyć funkcjonalność istniejącej kontrolki, można utworzyć formant pochodzące z istniejącej kontrolki przez dziedziczenie. Dziedziczy z istniejącej kontrolki, dziedziczenie, wszystkie funkcje i wizualne właściwości tej kontrolki. Na przykład, jeśli podczas tworzenia formant, który odziedziczone <xref:System.Windows.Forms.Button>nowego formantu będzie wyglądała i act dokładnie tak jak standardowy <xref:System.Windows.Forms.Button> kontroli. Można następnie rozszerzyć lub zmodyfikować funkcje nowego formantu poprzez wdrożenie niestandardowe metody i właściwości. W niektórych kontrolek można zmienić wygląd formantu dziedziczone przez zastąpienie jej <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-inherited-control"></a>Aby utworzyć odziedziczoną kontrolkę  
  
1.  Utwórz nową **aplikacja interfejsu Windows Forms** projektu.  
  
2.  Z **projektu** menu, wybierz **Dodaj nowy element**.  
  
     **Dodaj nowy element** pojawi się okno dialogowe.  
  
3.  W **Dodaj nowy element** okno dialogowe, kliknij dwukrotnie **kontrolkę niestandardową**.  
  
     Nowy formant niestandardowy zostanie dodany do projektu.  
  
4.  Jeśli używasz języka Visual Basic w górnej części **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**. Rozwiń CustomControl1.vb, a następnie otwórz CustomControl1.Designer.vb w edytorze kodu.  
  
5.  Jeśli używasz języka C#, należy otworzyć CustomControl1.cs w edytorze kodu.  
  
6.  Znajdź deklaracji klasy, która dziedziczy z <xref:System.Windows.Forms.Control>.  
  
7.  Zmień formant, który ma być dziedziczona z klasy bazowej.  
  
     Na przykład, jeśli ma być dziedziczona z <xref:System.Windows.Forms.Button>, zmień deklarację klasy następująco:  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Jeśli używasz języka Visual Basic, Zapisz i zamknij CustomControl1.Designer.vb. Otwórz CustomControl1.vb w edytorze kodu.  
  
9. Implementowanie niestandardowych metod dowolnej właściwości, które będą zawierały kontrolki.  
  
10. Jeśli chcesz zmodyfikować graficzny wygląd kontrolki, zastępują <xref:System.Windows.Forms.Control.OnPaint%2A> metody.  
  
    > [!NOTE]
    >  Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> nie umożliwia modyfikowania wyglądu wszystkich kontrolek. Te kontrolki, w których wszystkie ich malowania wykonywane przez Windows (na przykład <xref:System.Windows.Forms.TextBox>) nigdy nie wywołują metody ich <xref:System.Windows.Forms.Control.OnPaint%2A> metody i w związku z tym nigdy nie będzie użycie kodu niestandardowego. Można znaleźć w dokumentacji pomocy dla określonego formantu, który chcesz zmodyfikować, aby sprawdzić, czy <xref:System.Windows.Forms.Control.OnPaint%2A> metoda jest dostępna. Aby uzyskać listę wszystkich kontrolek formularza Windows, zobacz [kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Jeśli formant nie ma <xref:System.Windows.Forms.Control.OnPaint%2A> wymieniony jako metoda elementu członkowskiego, nie można zmieniać jego wygląd poprzez zastąpienie tej metody. Aby uzyskać więcej informacji na temat niestandardowych malowania zobacz [niestandardowe malowanie i renderowanie formantu](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
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
  
11. Zapisz i przetestuj formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Instrukcje: dziedziczenie z klasy kontrolek](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Instrukcje: dziedziczenie z klasy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
