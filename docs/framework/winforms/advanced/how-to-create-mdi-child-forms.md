---
title: 'Porady: tworzenie formularzy podrzędnych MDI'
description: Dowiedz się, jak za pomocą programu Visual Studio utworzyć formularz podrzędny interfejsu wielu dokumentów (MDI), który wyświetla formant RichTextBox.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 7fe5cde342f0f5ee078f888b7492cd4618bea5c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903184"
---
# <a name="how-to-create-mdi-child-forms"></a>Instrukcje: Tworzenie formularzy podrzędnych MDI

Formularze podrzędne MDI są ważnym elementem [aplikacji interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md), ponieważ stanowią one centrum interakcji z użytkownikiem.

W poniższej procedurze użyto programu Visual Studio do utworzenia formularza podrzędnego MDI, który wyświetla <xref:System.Windows.Forms.RichTextBox> kontrolkę podobną do większości aplikacji do przetwarzania tekstu. Podstawiając <xref:System.Windows.Forms> formant z innymi kontrolkami, takimi jak <xref:System.Windows.Forms.DataGridView> kontrolka, lub kombinacją formantów, można utworzyć okna podrzędne MDI (i przez rozszerzenie, aplikacje MDI) z różnymi możliwościami.

## <a name="create-mdi-child-forms"></a>Tworzenie formularzy podrzędnych MDI

1. Utwórz nowy projekt aplikacji Windows Forms w programie Visual Studio. W oknie **Właściwości** formularza ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> Właściwość na `true` , a jej `WindowsState` Właściwość na `Maximized` .

   Oznacza to, że formularz jest kontenerem MDI dla okien podrzędnych.

2. Na stronie `Toolbox` przeciągnij <xref:System.Windows.Forms.MenuStrip> kontrolkę do formularza. Ustaw jej `Text` Właściwość na **plik**.

3. Kliknij przycisk wielokropka (...) obok właściwości **Items** , a następnie kliknij przycisk **Dodaj** , aby dodać dwa podrzędne elementy menu pasków narzędzi. Ustaw `Text` Właściwość dla tych elementów na **New** i **window**.

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj**  >  **nowy element**.

5. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **formularz systemu Windows** (w Visual Basic lub w języku Visual C#) lub **Windows Forms aplikacji (.NET)** (w Visual C++) w okienku **Szablony** . W polu **Nazwa** wpisz **Form2**. Wybierz pozycję **Otwórz** , aby dodać formularz do projektu.

    > [!NOTE]
    > Formularz podrzędny MDI utworzony w tym kroku jest standardowym formularzem systemu Windows. W związku z tym ma <xref:System.Windows.Forms.Form.Opacity%2A> Właściwość, która umożliwia kontrolowanie przejrzystości formularza. Jednak <xref:System.Windows.Forms.Form.Opacity%2A> Właściwość została zaprojektowana dla okien najwyższego poziomu. Nie należy używać go z formularzami podrzędnymi MDI, ponieważ mogą wystąpić problemy z malowaniem.

     Ten formularz będzie szablonem dla formularzy podrzędnych MDI.

     Zostanie otwarty **Projektant formularzy systemu Windows** , który wyświetla **Form2**.

6. Z **przybornika**przeciągnij formant **RichTextBox** do formularza.

7. W oknie **Właściwości** Ustaw `Anchor` Właściwość na **Top, Left** i `Dock` Właściwość na wartość **Fill**.

   Powoduje to <xref:System.Windows.Forms.RichTextBox> , że formant wypełnia całkowicie obszar formularza podrzędnego MDI, nawet gdy zmieniany jest rozmiar formularza.

8. Kliknij dwukrotnie element menu **Nowy** , aby utworzyć <xref:System.Windows.Forms.Control.Click> dla niego procedurę obsługi zdarzeń.

9. Wstaw kod podobny do poniższego, aby utworzyć nowy formularz podrzędny MDI, gdy użytkownik kliknie **Nowy** element menu.

   > [!NOTE]
   > W poniższym przykładzie program obsługi zdarzeń obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenie dla `MenuItem2` . Należy pamiętać, że w zależności od konkretnej architektury aplikacji **Nowy** element menu może nie być `MenuItem2` .

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

   W języku C++ Dodaj następującą `#include` dyrektywę w górnej części formularza Form1. h:

   ```cpp
   #include "Form2.h"
   ```

10. Z listy rozwijanej w górnej części okna **Właściwości** wybierz pasek menu, który odpowiada pasek menu **plik** i ustaw <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> Właściwość na okno <xref:System.Windows.Forms.ToolStripMenuItem> .

    Dzięki temu menu **okno** będzie obsługiwać listę otwartych okien podrzędnych MDI ze znacznikiem wyboru obok aktywnego okna podrzędnego.

11. Naciśnij klawisz **F5** , aby uruchomić aplikację. Wybierając pozycję **Nowy** w menu **plik** , można utworzyć nowe formularze podrzędne MDI, które są śledzone w elemencie menu **okno** .

    > [!NOTE]
    > Gdy formularz podrzędny MDI ma <xref:System.Windows.Forms.MainMenu> składnik (z, zazwyczaj strukturę menu elementów menu) i jest otwarty w ramach formularza nadrzędnego MDI, który ma <xref:System.Windows.Forms.MainMenu> składnik (z, zazwyczaj strukturę menu elementów menu), elementy menu zostaną scalone automatycznie, jeśli ustawisz <xref:System.Windows.Forms.MenuItem.MergeType%2A> Właściwość (i opcjonalnie <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> Właściwość). Ustaw <xref:System.Windows.Forms.MenuItem.MergeType%2A> Właściwość obu <xref:System.Windows.Forms.MainMenu> składników i wszystkich elementów menu w formularzu podrzędnym na <xref:System.Windows.Forms.MenuMerge.MergeItems> . Ponadto ustaw <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> Właściwość tak, aby elementy menu z obu menu były wyświetlane w odpowiedniej kolejności. Ponadto należy pamiętać, że po zamknięciu formularza nadrzędnego MDI każdy z formularzy podrzędnych MDI zgłasza <xref:System.Windows.Forms.Form.Closing> zdarzenie <xref:System.Windows.Forms.Form.Closing> , zanim zostanie zgłoszone zdarzenie dla elementu nadrzędnego MDI. Anulowanie zdarzenia elementu podrzędnego MDI <xref:System.Windows.Forms.Form.Closing> nie uniemożliwi <xref:System.Windows.Forms.Form.Closing> wypróbowania zdarzenia elementu nadrzędnego MDI; jednak <xref:System.ComponentModel.CancelEventArgs> argument dla zdarzenia elementu nadrzędnego MDI <xref:System.Windows.Forms.Form.Closing> zostanie teraz ustawiony na wartość `true` . Można wymusić zamknięcie elementu nadrzędnego i wszystkich formularzy podrzędnych MDI przez ustawienie <xref:System.ComponentModel.CancelEventArgs> argumentu na `false` .

## <a name="see-also"></a>Zobacz też

- [Aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md)
- [Porady: tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)
- [Instrukcje: określanie elementu podrzędnego MDI Active](how-to-determine-the-active-mdi-child.md)
- [Instrukcje: wysyłanie danych do Active MDI Child](how-to-send-data-to-the-active-mdi-child.md)
- [Porady: aranżowanie formularzy podrzędnych MDI](how-to-arrange-mdi-child-forms.md)
