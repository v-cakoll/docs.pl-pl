---
title: 'Instrukcje: dziedziczenie z istniejących kontrolek formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 9ac18fae126425126712dafeb80f05663dfc2ebc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966586"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Instrukcje: dziedziczenie z istniejących kontrolek formularzy systemu Windows
Jeśli chcesz zwiększyć funkcjonalność istniejącej kontrolki, można utworzyć kontrolkę pochodzącą od istniejącej kontrolki przez dziedziczenie. Podczas dziedziczenia z istniejącej kontrolki dziedziczą wszystkie funkcje i właściwości wizualne tej kontrolki. Na przykład jeśli tworzysz kontrolkę, która dziedziczy z <xref:System.Windows.Forms.Button>, Nowa kontrolka będzie wyglądać i działać tak samo jak w przypadku kontrolki standardowej. <xref:System.Windows.Forms.Button> Następnie można zwiększyć lub zmodyfikować funkcjonalność nowej kontrolki przez implementację niestandardowych metod i właściwości. W niektórych kontrolkach można także zmienić wygląd dziedziczonej kontrolki, zastępując jej <xref:System.Windows.Forms.Control.OnPaint%2A> metodę.

## <a name="to-create-an-inherited-control"></a>Aby utworzyć formant dziedziczony

1. Utwórz nowy projekt **aplikacji Windows Forms** .

2. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

     **Dodaj nowy element** pojawi się okno dialogowe.

3. W oknie dialogowym **Dodaj nowy element** kliknij dwukrotnie **kontrolkę**niestandardową.

     Do projektu zostanie dodany nowy formant niestandardowy.

4. Jeśli używasz Visual Basic, w górnej części **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki**. Rozwiń CustomControl1. vb, a następnie otwórz CustomControl1. Designer. vb w edytorze kodu.

5. Jeśli używasz programu C#, Otwórz CustomControl1.cs w edytorze kodu.

6. Znajdź deklarację klasy, która dziedziczy z <xref:System.Windows.Forms.Control>.

7. Zmień klasę bazową na kontrolkę, z której chcesz dziedziczyć.

     Na przykład, jeśli chcesz dziedziczyć z <xref:System.Windows.Forms.Button>, zmień deklarację klasy na następującą:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

8. Jeśli używasz Visual Basic, Zapisz i zamknij CustomControl1. Designer. vb. Otwórz CustomControl1. vb w edytorze kodu.

9. Zaimplementuj wszelkie niestandardowe metody lub właściwości, które zostaną dołączone do kontrolki.

10. Jeśli chcesz zmodyfikować wygląd graficzny formantu, Zastąp <xref:System.Windows.Forms.Control.OnPaint%2A> metodę.

    > [!NOTE]
    > Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> nie pozwala na modyfikowanie wyglądu wszystkich kontrolek. Te kontrolki, które mają wszystkie malowania wykonywane przez system Windows (na <xref:System.Windows.Forms.TextBox>przykład) nigdy nie <xref:System.Windows.Forms.Control.OnPaint%2A> wywołują metody, a tym samym nigdy nie będą używać kodu niestandardowego. Zapoznaj się z dokumentacją dotyczącą konkretnej kontrolki, która ma zostać zmodyfikowana <xref:System.Windows.Forms.Control.OnPaint%2A> , aby zobaczyć, czy metoda jest dostępna. Aby uzyskać listę wszystkich kontrolek formularzy systemu Windows, zobacz [kontrolki do użycia na Windows Forms](controls-to-use-on-windows-forms.md). Jeśli formant nie jest <xref:System.Windows.Forms.Control.OnPaint%2A> wymieniony jako metoda członkowska, nie można zmienić jego wyglądu poprzez zastąpienie tej metody. Aby uzyskać więcej informacji na temat rysowania niestandardowego, zobacz [malowanie i renderowanie kontrolek niestandardowych](custom-control-painting-and-rendering.md).

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

11. Zapisz i Przetestuj swój formant.

## <a name="see-also"></a>Zobacz także

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: Dziedzicz z klasy kontrolki](how-to-inherit-from-the-control-class.md)
- [Instrukcje: Dziedzicz z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Instrukcje: Kontrolki autora dla Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Przewodnik: Dziedziczenie z kontrolki Windows Forms z Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Przewodnik: Dziedziczenie z kontrolki Windows Forms za pomocą wizualizacjiC#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
