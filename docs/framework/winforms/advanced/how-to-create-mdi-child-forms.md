---
title: 'Instrukcje: Tworzenie formularzy podrzędnych MDI'
ms.date: 03/30/2017
dev_langs:
- CSharp
- CPP
- VB
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: f5e8682caf658d159f044528f040b99676355448
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040115"
---
# <a name="how-to-create-mdi-child-forms"></a>Instrukcje: Tworzenie formularzy podrzędnych MDI

Formularze podrzędne MDI są ważnym elementem [aplikacji interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md), ponieważ stanowią one centrum interakcji z użytkownikiem.

W poniższej procedurze użyto programu Visual Studio do utworzenia formularza podrzędnego MDI, który wyświetla <xref:System.Windows.Forms.RichTextBox> kontrolkę podobną do większości aplikacji do przetwarzania tekstu. Podstawiając <xref:System.Windows.Forms> formant z innymi kontrolkami, takimi <xref:System.Windows.Forms.DataGridView> jak kontrolka, lub kombinacją formantów, można utworzyć okna podrzędne MDI (i przez rozszerzenie, aplikacje MDI) z różnymi możliwościami.

## <a name="create-mdi-child-forms"></a>Tworzenie formularzy podrzędnych MDI

1. Utwórz nowy projekt aplikacji Windows Forms w programie Visual Studio. W oknie **Właściwości** formularza ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwość na `true` , a jej `WindowsState` właściwość na `Maximized`.

   Oznacza to, że formularz jest kontenerem MDI dla okien podrzędnych.

2. `Toolbox`Na stronie <xref:System.Windows.Forms.MenuStrip> przeciągnij kontrolkę do formularza. Ustaw jej `Text` właściwość na **plik**.

3. Kliknij przycisk wielokropka (...) obok właściwości Items, a następnie kliknij przycisk **Dodaj** , aby dodać dwa podrzędne elementy menu pasków narzędzi. Ustaw właściwość dla tych elementów na **New** i **window.** `Text`

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Dodaj** > **nowy element**.

5. W oknie **dialogowym Dodaj nowy element** wybierz pozycję **formularz systemu Windows** (w Visual Basic lub w wizualizacji C#) lub **Windows Forms aplikacji (.NET)** (w C++wizualizacji) w okienku **Szablony** . W polu **Nazwa** wpisz **Form2**. Wybierz pozycję **Otwórz** , aby dodać formularz do projektu.

    > [!NOTE]
    > Formularz podrzędny MDI utworzony w tym kroku jest standardowym formularzem systemu Windows. W związku z tym ma <xref:System.Windows.Forms.Form.Opacity%2A> właściwość, która umożliwia kontrolowanie przejrzystości formularza. <xref:System.Windows.Forms.Form.Opacity%2A> Jednak właściwość została zaprojektowana dla okien najwyższego poziomu. Nie należy używać go z formularzami podrzędnymi MDI, ponieważ mogą wystąpić problemy z malowaniem.

     Ten formularz będzie szablonem dla formularzy podrzędnych MDI.

     Zostanie otwarty **Projektant formularzy systemu Windows** , który wyświetla **Form2**.

6. Z **przybornika**przeciągnij formant **RichTextBox** do formularza.

7. W oknie **Właściwości** Ustaw `Anchor` właściwość na `Dock` **Top, Left** i właściwość na wartość **Fill**.

   Powoduje to, <xref:System.Windows.Forms.RichTextBox> że formant wypełnia całkowicie obszar formularza podrzędnego MDI, nawet gdy zmieniany jest rozmiar formularza.

8. Kliknij dwukrotnie element menu **Nowy** , aby utworzyć <xref:System.Windows.Forms.Control.Click> dla niego procedurę obsługi zdarzeń.

9. Wstaw kod podobny do poniższego, aby utworzyć nowy formularz podrzędny MDI, gdy użytkownik kliknie **Nowy** element menu.

   > [!NOTE]
   > W poniższym przykładzie program obsługi zdarzeń obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenie dla. `MenuItem2` Należy pamiętać, że w zależności od konkretnej architektury aplikacji **Nowy** element menu może nie być `MenuItem2`.

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

   W C++programie Dodaj następującą `#include` dyrektywę w górnej części formularza Form1. h:

   ```cpp
   #include "Form2.h"
   ```

10. Z listy rozwijanej w górnej części okna **Właściwości** wybierz pasek menu, który odpowiada pasek menu **plik** <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> i ustaw właściwość na okno <xref:System.Windows.Forms.ToolStripMenuItem>.

    Dzięki temu menu **okno** będzie obsługiwać listę otwartych okien podrzędnych MDI ze znacznikiem wyboru obok aktywnego okna podrzędnego.

11. Naciśnij klawisz **F5** , aby uruchomić aplikację. Wybierając pozycję **Nowy** w menu **plik** , można utworzyć nowe formularze podrzędne MDI, które są śledzone w elemencie menu **okno** .

    > [!NOTE]
    > Gdy formularz podrzędny MDI ma <xref:System.Windows.Forms.MainMenu> składnik (z, zazwyczaj strukturę menu elementów menu) i jest otwarty w ramach formularza nadrzędnego MDI, który <xref:System.Windows.Forms.MainMenu> ma składnik (z, zazwyczaj strukturę menu elementów menu), elementy menu zostaną scalone automatycznie. Jeśli ustawiono <xref:System.Windows.Forms.MenuItem.MergeType%2A> Właściwość (i opcjonalnie <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> Właściwość). Ustaw właściwość obu <xref:System.Windows.Forms.MainMenu> składników i wszystkich elementów menu w formularzu podrzędnym na <xref:System.Windows.Forms.MenuMerge.MergeItems>. <xref:System.Windows.Forms.MenuItem.MergeType%2A> Ponadto ustaw <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> Właściwość tak, aby elementy menu z obu menu były wyświetlane w odpowiedniej kolejności. Ponadto należy pamiętać, że po zamknięciu formularza nadrzędnego MDI każdy z formularzy podrzędnych MDI zgłasza <xref:System.Windows.Forms.Form.Closing> zdarzenie, <xref:System.Windows.Forms.Form.Closing> zanim zostanie zgłoszone zdarzenie dla elementu nadrzędnego MDI. Anulowanie <xref:System.Windows.Forms.Form.Closing> zdarzenia elementu podrzędnego MDI nie uniemożliwi wypróbowania <xref:System.Windows.Forms.Form.Closing> zdarzenia elementu nadrzędnego MDI; jednak <xref:System.ComponentModel.CancelEventArgs> argument dla <xref:System.Windows.Forms.Form.Closing> zdarzenia elementu nadrzędnego MDI zostanie teraz ustawiony na `true`wartość. Można wymusić zamknięcie elementu nadrzędnego i wszystkich formularzy podrzędnych MDI przez ustawienie <xref:System.ComponentModel.CancelEventArgs> argumentu na. `false`

## <a name="see-also"></a>Zobacz także

- [Aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md)
- [Instrukcje: Tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)
- [Instrukcje: Określanie aktywnego elementu podrzędnego MDI](how-to-determine-the-active-mdi-child.md)
- [Instrukcje: Wyślij dane do aktywnego elementu podrzędnego MDI](how-to-send-data-to-the-active-mdi-child.md)
- [Instrukcje: Rozmieść formularze podrzędne MDI](how-to-arrange-mdi-child-forms.md)
