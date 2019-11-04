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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 063f5bb87b6348ee83573cf1506c9fabdaf651ee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460567"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Porady: dziedziczenie z istniejących formantów formularzy systemu Windows

Jeśli chcesz zwiększyć funkcjonalność istniejącej kontrolki, można utworzyć kontrolkę pochodzącą od istniejącej kontrolki przez dziedziczenie. Podczas dziedziczenia z istniejącej kontrolki dziedziczą wszystkie funkcje i właściwości wizualne tej kontrolki. Na przykład, jeśli tworzysz kontrolkę, która dziedziczy po <xref:System.Windows.Forms.Button>, Nowa kontrolka będzie wyglądać i działać tak samo jak w przypadku standardowego formantu <xref:System.Windows.Forms.Button>. Następnie można zwiększyć lub zmodyfikować funkcjonalność nowej kontrolki przez implementację niestandardowych metod i właściwości. W niektórych kontrolkach można także zmienić wygląd dziedziczonej kontrolki, zastępując jej metodę <xref:System.Windows.Forms.Control.OnPaint%2A>.

## <a name="to-create-an-inherited-control"></a>Aby utworzyć formant dziedziczony

1. W programie Visual Studio Utwórz nowy projekt **aplikacji Windows Forms** .

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

    Pojawi się okno dialogowe **Dodaj nowy element** .

1. W oknie dialogowym **Dodaj nowy element** kliknij dwukrotnie **kontrolkę niestandardową**.

    Do projektu zostanie dodany nowy formant niestandardowy.

1. Jeśli używasz:

    - Visual Basic w górnej części **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki**. Rozwiń CustomControl1. vb, a następnie otwórz CustomControl1. Designer. vb w edytorze kodu.
    - C#Otwórz CustomControl1.cs w edytorze kodu.

1. Znajdź deklarację klasy, która dziedziczy z <xref:System.Windows.Forms.Control>.

1. Zmień klasę bazową na kontrolkę, z której chcesz dziedziczyć.

     Na przykład jeśli chcesz dziedziczyć z <xref:System.Windows.Forms.Button>, zmień deklarację klasy na następującą:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Jeśli używasz Visual Basic, Zapisz i zamknij CustomControl1. Designer. vb. Otwórz CustomControl1. vb w edytorze kodu.

1. Zaimplementuj wszelkie niestandardowe metody lub właściwości, które zostaną dołączone do kontrolki.

1. Jeśli chcesz zmodyfikować wygląd graficzny formantu, Zastąp metodę <xref:System.Windows.Forms.Control.OnPaint%2A>.

    > [!NOTE]
    > Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> nie pozwoli na modyfikowanie wyglądu wszystkich kontrolek. Te kontrolki, które mają wszystkie malowanie wykonywane przez system Windows (na przykład <xref:System.Windows.Forms.TextBox>) nigdy nie wywołują metody <xref:System.Windows.Forms.Control.OnPaint%2A> i w ten sposób nigdy nie będą używać kodu niestandardowego. Zapoznaj się z dokumentacją dotyczącą konkretnej kontrolki, która ma zostać zmodyfikowana, aby zobaczyć, czy metoda <xref:System.Windows.Forms.Control.OnPaint%2A> jest dostępna. Aby uzyskać listę wszystkich kontrolek formularzy systemu Windows, zobacz [kontrolki do użycia na Windows Forms](controls-to-use-on-windows-forms.md). Jeśli kontrolka nie ma <xref:System.Windows.Forms.Control.OnPaint%2A> na liście jako metoda członkowska, nie można zmienić jej wyglądu poprzez zastąpienie tej metody. Aby uzyskać więcej informacji na temat rysowania niestandardowego, zobacz [malowanie i renderowanie kontrolek niestandardowych](custom-control-painting-and-rendering.md).

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

1. Zapisz i Przetestuj swój formant.

## <a name="see-also"></a>Zobacz także

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: dziedziczenie z klasy kontrolek](how-to-inherit-from-the-control-class.md)
- [Instrukcje: dziedziczenie z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Przewodnik: dziedziczenie z kontrolki Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
