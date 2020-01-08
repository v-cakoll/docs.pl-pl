---
title: 'Porady: tworzenie formularzy podrzędnych MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: b49d43e0e1123921cb3800f0d60193d0ea7b3924
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338594"
---
# <a name="how-to-create-mdi-child-forms"></a>Instrukcje: Tworzenie formularzy podrzędnych MDI

Formularze podrzędne MDI są ważnym elementem [aplikacji interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md), ponieważ stanowią one centrum interakcji z użytkownikiem.

W poniższej procedurze użyto programu Visual Studio do utworzenia formularza podrzędnego MDI, który wyświetla formant <xref:System.Windows.Forms.RichTextBox>, podobnie jak w przypadku większości aplikacji do przetwarzania tekstu. Podstawiając kontrolkę <xref:System.Windows.Forms> z innymi kontrolkami, takimi jak kontrolka <xref:System.Windows.Forms.DataGridView>, lub kombinacją formantów, można tworzyć podrzędne okna MDI (i przez rozszerzenie, aplikacje MDI) z różnymi możliwościami.

## <a name="create-mdi-child-forms"></a>Tworzenie formularzy podrzędnych MDI

1. Utwórz nowy projekt aplikacji Windows Forms w programie Visual Studio. W oknie **Właściwości** formularza ustaw jego właściwość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> na `true` i jej Właściwość `WindowsState` na `Maximized`.

   Oznacza to, że formularz jest kontenerem MDI dla okien podrzędnych.

2. W `Toolbox`przeciągnij kontrolkę <xref:System.Windows.Forms.MenuStrip> do formularza. Ustaw jej Właściwość `Text` na **plik**.

3. Kliknij przycisk wielokropka (...) obok właściwości **Items** , a następnie kliknij przycisk **Dodaj** , aby dodać dwa podrzędne elementy menu pasków narzędzi. Ustaw właściwość `Text` dla tych elementów na **New** i **window**.

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **nowy element**.

5. W oknie **dialogowym Dodaj nowy element** wybierz pozycję **formularz systemu Windows** (w Visual Basic lub w wizualizacji C#) lub **Windows Forms aplikacji (.NET)** (w C++wizualizacji) w okienku **Szablony** . W polu **Nazwa** wpisz **Form2**. Wybierz pozycję **Otwórz** , aby dodać formularz do projektu.

    > [!NOTE]
    > Formularz podrzędny MDI utworzony w tym kroku jest standardowym formularzem systemu Windows. W związku z tym ma właściwość <xref:System.Windows.Forms.Form.Opacity%2A>, która umożliwia kontrolowanie przejrzystości formularza. Jednak Właściwość <xref:System.Windows.Forms.Form.Opacity%2A> została zaprojektowana dla okien najwyższego poziomu. Nie należy używać go z formularzami podrzędnymi MDI, ponieważ mogą wystąpić problemy z malowaniem.

     Ten formularz będzie szablonem dla formularzy podrzędnych MDI.

     Zostanie otwarty **Projektant formularzy systemu Windows** , który wyświetla **Form2**.

6. Z **przybornika**przeciągnij formant **RichTextBox** do formularza.

7. W oknie **Właściwości** ustaw właściwość `Anchor` na wartość **Top, Left** i Właściwość `Dock` na wartość **Fill**.

   Powoduje to, że formant <xref:System.Windows.Forms.RichTextBox> do całkowitego wypełnienia obszaru formularza podrzędnego MDI, nawet gdy zmieniany jest rozmiar formularza.

8. Kliknij dwukrotnie **Nowy** element menu, aby utworzyć dla niego obsługę zdarzeń <xref:System.Windows.Forms.Control.Click>.

9. Wstaw kod podobny do poniższego, aby utworzyć nowy formularz podrzędny MDI, gdy użytkownik kliknie **Nowy** element menu.

   > [!NOTE]
   > W poniższym przykładzie program obsługi zdarzeń obsługuje zdarzenie <xref:System.Windows.Forms.Control.Click> dla `MenuItem2`. Należy pamiętać, że w zależności od konkretnej architektury aplikacji **Nowy** element menu może nie być `MenuItem2`.

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   W C++programie Dodaj następującą dyrektywę `#include` w górnej części formularza Form1. h:

   ```cpp
   #include "Form2.h"
   ```

10. Z listy rozwijanej w górnej części okna **Właściwości** wybierz pasek menu, który odpowiada paskowi menu **plik** i ustaw właściwość <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> na <xref:System.Windows.Forms.ToolStripMenuItem>okna.

    Dzięki temu menu **okno** będzie obsługiwać listę otwartych okien podrzędnych MDI ze znacznikiem wyboru obok aktywnego okna podrzędnego.

11. Naciśnij klawisz **F5**, aby uruchomić aplikację. Wybierając pozycję **Nowy** w menu **plik** , można utworzyć nowe formularze podrzędne MDI, które są śledzone w elemencie menu **okno** .

    > [!NOTE]
    > Gdy formularz podrzędny MDI ma składnik <xref:System.Windows.Forms.MainMenu> (z, zazwyczaj strukturę menu elementów menu) i jest otwarty w ramach formularza nadrzędnego MDI, który ma składnik <xref:System.Windows.Forms.MainMenu> (z, zazwyczaj strukturę menu elementów menu), elementy menu zostaną scalone automatycznie, jeśli ustawiono właściwość <xref:System.Windows.Forms.MenuItem.MergeType%2A> (i opcjonalnie Właściwość <xref:System.Windows.Forms.MenuItem.MergeOrder%2A>). Ustaw właściwość <xref:System.Windows.Forms.MenuItem.MergeType%2A> obu składników <xref:System.Windows.Forms.MainMenu> i wszystkich elementów menu w formularzu podrzędnym, aby <xref:System.Windows.Forms.MenuMerge.MergeItems>. Ponadto ustaw właściwość <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> tak, aby elementy menu z obu menu były wyświetlane w odpowiedniej kolejności. Ponadto należy pamiętać, że po zamknięciu formularza nadrzędnego MDI każdy z formularzy podrzędnych MDI zgłasza zdarzenie <xref:System.Windows.Forms.Form.Closing> przed wystąpieniem zdarzenia <xref:System.Windows.Forms.Form.Closing> dla elementu nadrzędnego MDI. Anulowanie zdarzenia <xref:System.Windows.Forms.Form.Closing> elementu podrzędnego MDI nie uniemożliwi podniesienia zdarzenia <xref:System.Windows.Forms.Form.Closing> elementu nadrzędnego MDI. jednak <xref:System.ComponentModel.CancelEventArgs> argument dla zdarzenia <xref:System.Windows.Forms.Form.Closing> elementu nadrzędnego MDI zostanie teraz ustawiony na `true`. Można wymusić zamknięcie elementu nadrzędnego i wszystkich formularzy podrzędnych MDI przez ustawienie argumentu <xref:System.ComponentModel.CancelEventArgs>, aby `false`.

## <a name="see-also"></a>Zobacz także

- [Aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md)
- [Instrukcje: tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)
- [Instrukcje: określanie elementu podrzędnego MDI Active](how-to-determine-the-active-mdi-child.md)
- [Instrukcje: wysyłanie danych do Active MDI Child](how-to-send-data-to-the-active-mdi-child.md)
- [Instrukcje: aranżowanie formularzy podrzędnych MDI](how-to-arrange-mdi-child-forms.md)
