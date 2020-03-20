---
title: dziedziczenie z istniejących kontrolek
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
ms.openlocfilehash: b0e0053816efde349c7e4d13d03bef5f8801c667
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849383"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Porady: dziedziczenie z istniejących formantów formularzy systemu Windows

Jeśli chcesz rozszerzyć funkcjonalność istniejącego formantu, można utworzyć formant pochodzący z istniejącego formantu poprzez dziedziczenie. Dziedzicząc z istniejącego formantu, dziedziczysz wszystkie funkcje i właściwości wizualne tego formantu. Na przykład, jeśli tworzysz formant, <xref:System.Windows.Forms.Button>który dziedziczył po, nowy formant <xref:System.Windows.Forms.Button> będzie wyglądać i działać dokładnie tak, jak standardowy formant. Następnie można rozszerzyć lub zmodyfikować funkcjonalność nowego formantu za pomocą implementacji metod i właściwości niestandardowych. W niektórych formantów można również zmienić wygląd odziedziczonego <xref:System.Windows.Forms.Control.OnPaint%2A> formantu, zastępując jego metody.

## <a name="to-create-an-inherited-control"></a>Aby utworzyć formant dziedziczony

1. W programie Visual Studio utwórz nowy projekt **aplikacji formularzy systemu Windows.**

1. Z menu **Projekt** wybierz polecenie **Dodaj nowy element**.

    Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

1. W oknie dialogowym **Dodawanie nowego elementu** kliknij dwukrotnie pozycję **Formant niestandardowy**.

    Nowy formant niestandardowy jest dodawany do projektu.

1. Jeśli używasz:

    - Visual Basic, u góry **Eksploratora rozwiązań,** kliknij pozycję **Pokaż wszystkie pliki**. Rozwiń pozycję CustomControl1.vb, a następnie otwórz plik CustomControl1.Designer.vb w Edytorze kodu.
    - C#, otwórz CustomControl1.cs w Edytorze kodu.

1. Znajdź deklarację klasy, która <xref:System.Windows.Forms.Control>dziedziczy po .

1. Zmień klasę podstawową na formant, z którego chcesz dziedziczyć.

     Na przykład, jeśli chcesz <xref:System.Windows.Forms.Button>dziedziczyć z , zmień deklarację klasy na następującą:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Jeśli używasz języka Visual Basic, zapisz i zamknij CustomControl1.Designer.vb. Otwórz CustomControl1.vb w Edytorze kodu.

1. Zaimplementuj wszystkie niestandardowe metody lub właściwości, które będzie zawierać formant.

1. Jeśli chcesz zmodyfikować wygląd graficzny formantu, należy <xref:System.Windows.Forms.Control.OnPaint%2A> zastąpić metodę.

    > [!NOTE]
    > Zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> nie pozwala na modyfikowanie wyglądu wszystkich formantów. Te formanty, które mają wszystkie ich <xref:System.Windows.Forms.TextBox>obraz wykonane <xref:System.Windows.Forms.Control.OnPaint%2A> przez system Windows (na przykład) nigdy nie wywołać ich metody, a tym samym nigdy nie będzie używać kodu niestandardowego. Zapoznaj się z dokumentacją Pomocy dla określonego formantu, który chcesz zmodyfikować, aby sprawdzić, <xref:System.Windows.Forms.Control.OnPaint%2A> czy metoda jest dostępna. Aby uzyskać listę wszystkich formantów formularza systemu Windows, zobacz [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md). Jeśli formant nie <xref:System.Windows.Forms.Control.OnPaint%2A> ma wymienione jako metoda elementu członkowskiego, nie można zmienić jego wygląd, zastępując tę metodę. Aby uzyskać więcej informacji na temat malowania niestandardowego, zobacz [Niestandardowe malowanie i renderowanie sterowania](custom-control-painting-and-rendering.md).

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

1. Zapisz i przetestuj swoją kontrolę.

## <a name="see-also"></a>Zobacz też

- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: dziedziczenie z klasy kontrolek](how-to-inherit-from-the-control-class.md)
- [Instrukcje: dziedziczenie z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Przewodnik: Dziedziczenie z formantu formularzy systemu Windows](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
