---
title: "Wskazówki: tworzenie formularza MDI ze scalaniem menu i formantami ToolStrip"
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
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bca5439f247951496d82c03b57ec1fa0e21a8271
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Wskazówki: tworzenie formularza MDI ze scalaniem menu i formantami ToolStrip
<xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw obsługuje wiele aplikacji dokumentu interfejsu (MDI) i <xref:System.Windows.Forms.MenuStrip> sterowanie obsługuje scalania menu. Formularze MDI może również <xref:System.Windows.Forms.ToolStrip> kontrolki.  
  
 W tym przewodniku przedstawiono sposób użycia <xref:System.Windows.Forms.ToolStripPanel> formantów z formularza MDI. Formularz obsługuje również menu scalanie z menu podrzędnego. Następujące zadania są przedstawione w tym przewodniku:  
  
-   Tworzenie projektu formularzy systemu Windows.  
  
-   Tworzenie menu główne formularza. Rzeczywista nazwa menu będą się różnić.  
  
-   Dodawanie <xref:System.Windows.Forms.ToolStripPanel> formant **przybornika**.  
  
-   Tworzenie formularza podrzędnego.  
  
-   Rozmieszczanie <xref:System.Windows.Forms.ToolStripPanel> formanty według kolejności.  
  
 Gdy skończysz, konieczne będzie formularza MDI, która obsługuje scalania menu i ruchome <xref:System.Windows.Forms.ToolStrip> kontrolki.  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: Tworzenie formularza MDI za pomocą scalania Menu i formantów ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Wystarczających uprawnień, aby można było utworzyć i uruchomić projektów aplikacji formularzy systemu Windows na komputerze, którym [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] jest zainstalowany.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie **MdiForm**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  W narzędziu Projektant dla formularzy systemu Windows wybierz formularza.  
  
3.  W oknie właściwości ustaw wartość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> do `true`.  
  
## <a name="creating-the-main-menu"></a>Tworzenie Menu głównego  
 Element nadrzędny MDI formularza zawiera menu głównego. Menu główne ma jeden element menu o nazwie **okna**. Z **okna** element menu, można utworzyć formularze podrzędne. Elementy menu z formularze podrzędne są scalane w menu głównym.  
  
#### <a name="to-create-the-main-menu"></a>Aby utworzyć menu główne  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> sterowania do formularza.  
  
2.  Dodaj <xref:System.Windows.Forms.ToolStripMenuItem> do <xref:System.Windows.Forms.MenuStrip> kontroli i nadaj mu nazwę **okna**.  
  
3.  Wybierz <xref:System.Windows.Forms.MenuStrip> formantu.  
  
4.  W oknie właściwości ustaw wartość <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwości `ToolStripMenuItem1`.  
  
5.  Dodaj podelementu do **okna** element menu, a następnie nazwę podelement **nowy**.  
  
6.  Kliknij w oknie właściwości **zdarzenia**.  
  
7.  Kliknij dwukrotnie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń.  
  
     Projektant formularzy systemu Windows generuje programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń.  
  
8.  Wstaw następujący kod do obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>Dodawanie do przybornika ToolStripPanel — formant  
 Jeśli używasz <xref:System.Windows.Forms.MenuStrip> formantów z formularza MDI muszą mieć <xref:System.Windows.Forms.ToolStripPanel> formantu. Należy dodać <xref:System.Windows.Forms.ToolStripPanel> formant **przybornika** Tworzenie formularza MDI w narzędziu Projektant dla formularzy systemu Windows.  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>Aby dodać do przybornika ToolStripPanel — formant  
  
1.  Otwórz **przybornika**, a następnie kliknij przycisk **wszystkich formularzy systemu Windows** kartę, aby wyświetlić dostępne formanty formularzy systemu Windows.  
  
2.  Kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów i wybierz **wybierz elementy**.  
  
3.  W **wybierz elementy przybornika** okno dialogowe, przewiń w dół **nazwa** kolumny do momentu znalezienia **ToolStripPanel**.  
  
4.  Zaznacz pole wyboru przy **ToolStripPanel**, a następnie kliknij przycisk **OK**.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Formant jest widoczny w **przybornika**.  
  
## <a name="creating-a-child-form"></a>Tworzenie formularza podrzędnego  
 W tej procedurze zostanie Definiowanie klasy formularza podrzędnego oddzielne, która ma własną <xref:System.Windows.Forms.MenuStrip> formantu. Elementy menu dla tego formularza są łączone z tymi formularza nadrzędnego.  
  
#### <a name="to-define-a-child-form"></a>Aby zdefiniować formularz podrzędny  
  
1.  Dodaj nowy formularz o nazwie `ChildForm` do projektu.  
  
     Aby uzyskać więcej informacji, zobacz [porady: dodawanie formularzy systemu Windows z projektem](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
2.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> sterowania do formularza podrzędnego.  
  
3.  Kliknij przycisk <xref:System.Windows.Forms.MenuStrip> symbolu tagu formantu (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), a następnie wybierz **edytowanie elementów**.  
  
4.  W **edytora kolekcji elementy** okno dialogowe Dodaj nowy <xref:System.Windows.Forms.ToolStripMenuItem> o nazwie **ChildMenuItem** do menu podrzędnego.  
  
     Aby uzyskać więcej informacji, zobacz [edytora kolekcji elementów ToolStrip](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).  
  
## <a name="testing-the-form"></a>Testowanie formularza  
  
#### <a name="to-test-your-form"></a>Aby przetestować formularz  
  
1.  Naciśnij klawisz F5, aby skompilować i uruchomić formularza.  
  
2.  Kliknij przycisk **okna** element menu, aby otworzyć menu, a następnie kliknij przycisk **nowy**.  
  
     Nowy formularz podrzędny jest tworzony w obszarze klienta MDI formularza. Formularz podrzędny menu jest scalany z poziomu menu głównego.  
  
3.  Zamknij formularz podrzędny.  
  
     Formularz podrzędny menu zostanie usunięty z menu głównego.  
  
4.  Kliknij przycisk **nowy** kilka razy.  
  
     Formularze podrzędne są automatycznie wyświetlane w obszarze sz**indow** elementu menu, ponieważ <xref:System.Windows.Forms.MenuStrip> formantu <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> przypisano właściwości.  
  
## <a name="adding-toolstrip-support"></a>Dodawanie obsługi ToolStrip  
 W tej procedurze spowoduje dodanie czterech <xref:System.Windows.Forms.ToolStrip> formantów do formularza nadrzędnego MDI. Każdy <xref:System.Windows.Forms.ToolStrip> formant został dodany wewnątrz <xref:System.Windows.Forms.ToolStripPanel> kontroli, która jest zadokowany do krawędzi formularza.  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>Aby dodać formantów ToolStrip do formularza nadrzędnego MDI  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ToolStripPanel> sterowania do formularza.  
  
2.  Z <xref:System.Windows.Forms.ToolStripPanel> zaznaczony formant, kliknij dwukrotnie <xref:System.Windows.Forms.ToolStrip> kontroli w **przybornika**.  
  
     A <xref:System.Windows.Forms.ToolStrip> formant jest tworzony w <xref:System.Windows.Forms.ToolStripPanel> formantu.  
  
3.  Wybierz <xref:System.Windows.Forms.ToolStripPanel> formantu.  
  
4.  W oknie Właściwości zmień wartość formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Left>.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Kontrolować doków do lewej strony w postaci pod menu głównego. Aby dopasować zmienia rozmiar obszaru klienckiego MDI <xref:System.Windows.Forms.ToolStripPanel> formantu.  
  
5.  Powtórz kroki od 1 do 4.  
  
     Dokowanie nowe <xref:System.Windows.Forms.ToolStripPanel> kontroli do górnej części formularza.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Kontroli jest zadokowany pod menu głównego, ale do prawej pierwszego <xref:System.Windows.Forms.ToolStripPanel> formantu. W tym kroku przedstawiono znaczenie kolejności poprawne pozycjonowania <xref:System.Windows.Forms.ToolStripPanel> kontrolki.  
  
6.  Powtórz kroki od 1 do 4 dla dwóch więcej <xref:System.Windows.Forms.ToolStripPanel> kontrolki.  
  
     Dokowanie nowe <xref:System.Windows.Forms.ToolStripPanel> formantów w prawo i w dolnej części formularza.  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>Rozmieszczanie formantów ToolStripPanel przez porządek osi z  
 Pozycja zadokowanych <xref:System.Windows.Forms.ToolStripPanel> kontrolkę w formularzu MDI jest określany za pomocą pozycji formantu w kolejności. Można łatwo rozmieścić porządek osi z formantów w oknie konspektu dokumentu.  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>Aby zorganizować formantów ToolStripPanel przez porządek osi z  
  
1.  W **widoku** menu, kliknij przycisk **inne okna**, a następnie kliknij przycisk **konspekt dokumentu**.  
  
     Układ sieci <xref:System.Windows.Forms.ToolStripPanel> jest niestandardowe formanty z poprzedniej procedury. To dlatego porządek osi jest nieprawidłowy. Umożliwia zmianę kolejności formantów okno konspektu dokumentu.  
  
2.  Okno konspektu dokumentu, wybierz **ToolStripPanel4**.  
  
3.  Kliknij przycisk strzałki w dół, dopóki **ToolStripPanel4** jest w dolnej części listy.  
  
     **ToolStripPanel4** kontroli jest zadokowany do dolnej części formularza, poniżej innych kontrolek.  
  
4.  Wybierz **ToolStripPanel2**.  
  
5.  Kliknij przycisk strzałki w dół jeden raz, aby umieść formantu trzeci na liście.  
  
     **ToolStripPanel2** kontroli jest zadokowany do góry formularza, pod menu głównego i powyżej innych kontrolek.  
  
6.  Wybierz różne formantów w **konspekt dokumentu** okna i przenieść je do różnych miejscach w porządku osi z. Należy pamiętać, efekt porządek umieszczanie formantów dokowanych. Użyj klawiszy CTRL-Z lub **Cofnij** na **Edytuj** menu, aby cofnąć zmiany.  
  
## <a name="checkpoint"></a>Punkt kontrolny  
  
#### <a name="to-test-your-form"></a>Aby przetestować formularz  
  
1.  Naciśnij klawisz F5, aby skompilować i uruchomić formularza.  
  
2.  Kliknij przycisk uchwytu elementu <xref:System.Windows.Forms.ToolStrip> kontroli i przeciągnij formant w inne miejsca w formularzu.  
  
     Możesz przeciągnąć <xref:System.Windows.Forms.ToolStrip> formantu z jedną <xref:System.Windows.Forms.ToolStripPanel> formantu do innego.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku zostały utworzone formularza nadrzędnego MDI z <xref:System.Windows.Forms.ToolStrip> kontrolek i scalanie menu. Można użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:  
  
-   Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>. Aby uzyskać więcej informacji, zobacz [informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Formularz utworzony automatycznie wypełnione standardowe menu. Aby uzyskać więcej informacji, zobacz [wskazówki: zapewnianie standardowe elementy Menu do formularza](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Nadaj Twojej <xref:System.Windows.Forms.ToolStrip> profesjonalny wygląd kontrolki. Aby uzyskać więcej informacji, zobacz [porady: ustawienie modułu renderowania ToolStrip dla aplikacji](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Porady: tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Porady: tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Porady: Wstawianie elementu MenuStrip do Menu rozwijanego MDI](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [ToolStrip — formant](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
