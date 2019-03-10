---
title: 'Instrukcje: Tworzenie formularzy podrzędnych MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 02e19470aaac76e7bcab5a324138bb50dedb212f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720202"
---
# <a name="how-to-create-mdi-child-forms"></a>Instrukcje: Tworzenie formularzy podrzędnych MDI
Formularze podrzędne MDI jest podstawowym elementem [aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md), jak te formularze są środek interakcji z użytkownikiem.  
  
 W poniższej procedurze utworzysz formularz podrzędny MDI, która wyświetla <xref:System.Windows.Forms.RichTextBox> kontrolki, podobne do innych aplikacji. Podstawianie <xref:System.Windows.Forms> kontrolką inne formanty, takie jak <xref:System.Windows.Forms.DataGridView> formantu lub kombinację kontrolki pozwala na tworzenie elementu podrzędnego MDI systemu windows (a w konsekwencji, aplikacje MDI) z różnych możliwości.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-mdi-child-forms"></a>Umożliwia tworzenie formularzy podrzędnych MDI  
  
1.  Utwórz nowy projekt Windows Forms. W **Windows właściwości** formularza, ustaw jego <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`, a jego `WindowsState` właściwość `Maximized`.  
  
     Określa formularza jako kontenera okien podrzędnych MDI.  
  
2.  Z `Toolbox`, przeciągnij <xref:System.Windows.Forms.MenuStrip> formantu do formularza. Ustaw jego `Text` właściwości **pliku**.  
  
3.  Kliknij przycisk z wielokropkiem (...) obok pozycji **elementów** właściwości, a następnie kliknij przycisk **Dodaj** można dodać dwa elementy menu paska narzędzi podrzędnych. Ustaw `Text` właściwości dla tych elementów do **New** i **okna**.  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, wskaż **Dodaj**, a następnie wybierz pozycję **Dodaj nowy element**.  
  
5.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **formularza Windows** (w języku Visual Basic lub języka Visual C#) lub **Windows Forms aplikacji (.NET)** (w [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) z  **Szablony** okienka. W **nazwa** pola, określ nazwę formularza **formularz2**. Kliknij przycisk **Otwórz** przycisk, aby dodać formularz do projektu.  
  
    > [!NOTE]
    >  Formularz podrzędny MDI, który został utworzony w tym kroku jest standardowy formularz Windows. W efekcie ma <xref:System.Windows.Forms.Form.Opacity%2A> właściwość, która umożliwia kontrolowanie przezroczystości formularza. Jednak <xref:System.Windows.Forms.Form.Opacity%2A> właściwość została zaprojektowana dla okien najwyższego poziomu. Nie używaj go za pomocą formularzy podrzędnych MDI, jak mogą wystąpić problemy malowania.  
  
     Ten formularz będzie szablonu dla formularzy podrzędnych MDI.  
  
     **Windows Forms Designer** otwiera się i wyświetla **formularz2**.  
  
6.  Z **przybornika**, przeciągnij **RichTextBox** formantu do formularza.  
  
7.  W **właściwości** oknie `Anchor` właściwości **, lewa górna** i `Dock` właściwości **wypełnienia**.  
  
     Powoduje to, że <xref:System.Windows.Forms.RichTextBox> sterowania, aby całkowicie wypełnić obszaru formularz podrzędny MDI, nawet w przypadku, gdy zmieniany jest rozmiar formularza.  
  
8.  Kliknij dwukrotnie **New** element menu, aby utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.  
  
9. Wstawianie kodu podobne do następujących czynności, aby utworzyć nowy formularz podrzędny MDI, gdy użytkownik kliknie **New** elementu menu.  
  
    > [!NOTE]
    >  W poniższym przykładzie obsługuje program obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> zdarzenie `MenuItem2`. Należy pamiętać, w zależności od specyfiki architektury aplikacji, usługi **New** element menu może nie być `MenuItem2`.  
  
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
  
     W [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Dodaj następujący kod `#include` dyrektywę w górnej części Form1.h:  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. Na liście rozwijanej w górnej części **właściwości** okna, wybierz pasek menu, który odpowiada **pliku** paska menu i ustaw <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwości w oknie <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
     Spowoduje to włączenie **okna** menu, aby utrzymywać listę otwartych okien podrzędnych MDI znacznik wyboru obok okna podrzędnego active.  
  
11. Naciśnij klawisz F5, aby uruchomić aplikację. Wybierając **New** z **pliku** menu, można utworzyć nowych formularzy podrzędnych MDI, które są przechowywane informacje o w **okna** elementu menu.  
  
    > [!NOTE]
    >  Jeśli formularz podrzędny MDI ma <xref:System.Windows.Forms.MainMenu> składnika (z, zwykle struktury menu elementów menu) i jest otwarty w ramach formularza nadrzędnego MDI, która ma <xref:System.Windows.Forms.MainMenu> składnik (z, zwykle struktury menu elementów menu), menu, automatycznie scali elementów Jeśli ustawiono <xref:System.Windows.Forms.MenuItem.MergeType%2A> właściwości (i ewentualnie <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> właściwości). Ustaw <xref:System.Windows.Forms.MenuItem.MergeType%2A> właściwość obu <xref:System.Windows.Forms.MainMenu> składników i wszystkie elementy menu formularza podrzędnego <xref:System.Windows.Forms.MenuMerge.MergeItems>. Ponadto, ustawić <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> właściwość tak, aby elementy menu, zarówno menu są wyświetlane w odpowiedni sposób. Ponadto należy pamiętać o tym, że po zamknięciu formularza nadrzędnego MDI każdego elementu podrzędnego MDI formularzy zgłasza <xref:System.Windows.Forms.Form.Closing> zdarzenie przed <xref:System.Windows.Forms.Form.Closing> jest wywoływane zdarzenie nadrzędnego MDI. Anulowanie podrzędnym MDI <xref:System.Windows.Forms.Form.Closing> zdarzeń nie zapobiega nadrzędny MDI <xref:System.Windows.Forms.Form.Closing> zdarzenia wywoływane; jednak <xref:System.ComponentModel.CancelEventArgs> argumentu dla elementu nadrzędnego MDI <xref:System.Windows.Forms.Form.Closing> zdarzenie zostanie teraz ustawiony na `true`. Można wymusić nadrzędnych MDI i wszystkie formularze podrzędne MDI, aby zamknąć, ustawiając <xref:System.ComponentModel.CancelEventArgs> argument `false`.  
  
## <a name="see-also"></a>Zobacz także
- [Aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md)
- [Instrukcje: Tworzenie formularzy nadrzędnych MDI](how-to-create-mdi-parent-forms.md)
- [Instrukcje: Określanie elementu podrzędnego Active MDI](how-to-determine-the-active-mdi-child.md)
- [Instrukcje: Wysyłanie danych do Active MDI Child](how-to-send-data-to-the-active-mdi-child.md)
- [Instrukcje: Aranżowanie formularzy podrzędnych MDI](how-to-arrange-mdi-child-forms.md)
