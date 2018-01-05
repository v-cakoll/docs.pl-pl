---
title: "Porady: tworzenie formularzy podrzędnych MDI"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2bbbe8dbbfa6b2aebd3834314f0f56b7c7643c21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-mdi-child-forms"></a>Porady: tworzenie formularzy podrzędnych MDI
Formularze podrzędne MDI jest podstawowym elementem [aplikacje interfejsu wielu dokumentów (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), jak te są Centrum interakcji z użytkownikiem.  
  
 W poniższej procedurze utworzysz formularz podrzędny MDI, który wyświetla <xref:System.Windows.Forms.RichTextBox> kontroli podobna do innych aplikacji. Zastępowanie <xref:System.Windows.Forms> sterować za pomocą inne formanty, takie jak <xref:System.Windows.Forms.DataGridView> kontroli oraz ich kombinacjami formantów umożliwia tworzenie okien podrzędnych MDI (a przez rozszerzenie, aplikacje MDI) z różnych możliwości.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-mdi-child-forms"></a>Do tworzenia formularzy podrzędnych MDI  
  
1.  Utwórz nowy projekt formularzy systemu Windows. W **okna właściwości** formularza, ustaw jej <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości `true`i jego `WindowsState` właściwości `Maximized`.  
  
     Określa formularza jako kontenera okien podrzędnych MDI.  
  
2.  Z `Toolbox`, przeciągnij <xref:System.Windows.Forms.MenuStrip> sterowania do formularza. Ustaw jego `Text` właściwości **pliku**.  
  
3.  Kliknij przycisk wielokropka (...) obok pozycji **elementów** właściwości, a następnie kliknij przycisk **Dodaj** można dodać dwóch elementów menu paska narzędzia podrzędnych. Ustaw `Text` właściwości dla tych elementów do **nowy** i **okna**.  
  
4.  W **Eksploratora rozwiązań**, kliknij projekt prawym przyciskiem myszy, wskaż polecenie **Dodaj**, a następnie wybierz **Dodaj nowy element**.  
  
5.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **formularza systemu Windows** (w [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) lub **aplikacji formularzy systemu Windows (.NET)** (w [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) z **szablony** okienka. W **nazwa** pozycję Nazwa formularza **formularz2**. Kliknij przycisk **Otwórz** przycisk, aby dodać formularza do projektu.  
  
    > [!NOTE]
    >  Formularz podrzędny MDI utworzone w tym kroku jest standardowe formularza systemu Windows. W efekcie ma <xref:System.Windows.Forms.Form.Opacity%2A> właściwość, która umożliwia kontrolowanie przezroczystości formularza. Jednak <xref:System.Windows.Forms.Form.Opacity%2A> właściwość została zaprojektowana dla systemu windows najwyższego poziomu. Nie należy używać go z formularzy podrzędnych MDI, jak mogą wystąpić problemy rysowania.  
  
     Ten formularz będzie szablonu dla formularzy podrzędnych MDI.  
  
     **Projektant formularzy systemu Windows** otwiera wyświetlanie **formularz2**.  
  
6.  Z **przybornika**, przeciągnij **RichTextBox** sterowania do formularza.  
  
7.  W **właściwości** ustaw `Anchor` właściwości **, lewa górna** i `Dock` właściwości **wypełnienia**.  
  
     Powoduje to <xref:System.Windows.Forms.RichTextBox> sterowania, aby wypełnić obszar formularz podrzędny MDI, nawet wtedy, gdy zmieni się rozmiar formularza.  
  
8.  Kliknij dwukrotnie **nowy** element menu, aby utworzyć <xref:System.Windows.Forms.Control.Click> obsługi zdarzenia.  
  
9. Wstawianie kodu podobne do następujących czynności, aby utworzyć nowy formularz podrzędny MDI, gdy użytkownik kliknie **nowy** elementu menu.  
  
    > [!NOTE]
    >  W poniższym przykładzie obsługuje program obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> zdarzenia dla `MenuItem2`. Należy pamiętać, że, w zależności od specyfiki architektury aplikacji, z **nowy** element menu nie mogą być `MenuItem2`.  
  
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
  
     W [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], Dodaj następujący `#include` dyrektywy w górnej części Form1.h:  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. Na liście rozwijanej na górze **właściwości** okna, wybierz paska menu, która odpowiada **pliku** paska menu i zestaw <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwości do okna <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
     Spowoduje to włączenie **okna** menu, aby utrzymywać listę okien podrzędnych MDI znacznik wyboru obok okna podrzędnego active.  
  
11. Naciśnij klawisz F5, aby uruchomić aplikację. Wybierając **nowy** z **pliku** menu, można utworzyć nowego formularzy podrzędnych MDI, które są przechowywane informacje o w **okna** elementu menu.  
  
    > [!NOTE]
    >  Gdy formularz podrzędny MDI ma <xref:System.Windows.Forms.MainMenu> składnik (z, zazwyczaj struktury menu elementów menu) i jest otwarty w formularza nadrzędnego MDI, który ma <xref:System.Windows.Forms.MainMenu> składnik (z, zazwyczaj struktury menu elementów menu), automatycznie scali elementów menu Jeśli ustawiono <xref:System.Windows.Forms.MenuItem.MergeType%2A> właściwości (i opcjonalnie <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> właściwości). Ustaw <xref:System.Windows.Forms.MenuItem.MergeType%2A> właściwość obu <xref:System.Windows.Forms.MainMenu> składników i wszystkich elementów menu do formularza podrzędnego <xref:System.Windows.Forms.MenuMerge.MergeItems>. Ponadto, ustawić <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> właściwości, aby elementów menu z obu menu są wyświetlane w odpowiedni sposób. Ponadto należy pamiętać, że po zamknięciu formularza nadrzędnego MDI każdego elementu podrzędnego MDI formularzy zgłasza <xref:System.Windows.Forms.Form.Closing> zdarzeń przed <xref:System.Windows.Forms.Form.Closing> nadrzędnego MDI zdarzenia. Anulowanie podrzędnych MDI <xref:System.Windows.Forms.Form.Closing> zdarzeń nie zapobiega element nadrzędny MDI <xref:System.Windows.Forms.Form.Closing> zdarzenia z zgłaszanych; jednak <xref:System.ComponentModel.CancelEventArgs> argument element nadrzędny MDI <xref:System.Windows.Forms.Form.Closing> zdarzeń zostanie teraz ustawiony na `true`. Możesz wymusić element nadrzędny MDI i wszystkie formularze podrzędne MDI, aby zamknąć przez ustawienie <xref:System.ComponentModel.CancelEventArgs> argument `false`.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje interfejsu wielu dokumentów (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Instrukcje: tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Instrukcje: określanie elementu podrzędnego MDI Active](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Instrukcje: wysyłanie danych do Active MDI Child](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Instrukcje: aranżowanie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
