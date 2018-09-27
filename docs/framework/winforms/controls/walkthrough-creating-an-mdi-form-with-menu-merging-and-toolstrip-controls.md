---
title: 'Wskazówki: tworzenie formularza MDI ze scalaniem menu i formantami ToolStrip'
ms.date: 03/30/2017
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
ms.openlocfilehash: 6236190340833e3f8810387e51ad53e1cb10d37b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232875"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Wskazówki: tworzenie formularza MDI ze scalaniem menu i formantami ToolStrip
<xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw obsługuje wiele aplikacji interfejsu (MDI) dokumentu i <xref:System.Windows.Forms.MenuStrip> kontrolka obsługuje scalania menu. Formularze MDI może również <xref:System.Windows.Forms.ToolStrip> kontrolki.  
  
 W tym instruktażu przedstawiono sposób użycia <xref:System.Windows.Forms.ToolStripPanel> formanty z formularza MDI. Formularz obsługuje także menu scalanie z menu podrzędne. Następujące zadania są przedstawione w niniejszym przewodniku:  
  
-   Tworzenie projektu Windows Forms.  
  
-   Tworzenie menu głównego dla formularza użytkownika. Rzeczywista nazwa menu będą się różnić.  
  
-   Dodawanie <xref:System.Windows.Forms.ToolStripPanel> kontrolę **przybornika**.  
  
-   Tworzenie formularza podrzędnego.  
  
-   Rozmieszczanie <xref:System.Windows.Forms.ToolStripPanel> formanty według porządku osi z.  
  
 Po zakończeniu będziesz mieć formularza MDI, która obsługuje scalania menu i ruchome <xref:System.Windows.Forms.ToolStrip> kontrolki.  
  
 Aby skopiować kod, w tym temacie na jednej liście, zobacz [porady: Tworzenie formularza MDI za pomocą scalania Menu i formantów ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
-   Wystarczające uprawnienia, aby można było utworzyć i uruchomić projekty aplikacji Windows Forms na komputerze, w którym jest zainstalowany program Visual Studio.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest tworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji Windows, o nazwie **MdiForm** (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
2.  W programie Windows Forms Designer wybierz formularz.  
  
3.  W oknie właściwości ustaw wartość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> do `true`.  
  
## <a name="creating-the-main-menu"></a>Tworzenie Menu głównego  
 Formularza nadrzędnego MDI zawiera menu głównego. Menu główne ma jeden element menu o nazwie **okna**. Za pomocą **okna** element menu może tworzenie formularzy podrzędnych. Elementy menu z formularze podrzędne są scalane w menu głównym.  
  
#### <a name="to-create-the-main-menu"></a>Aby utworzyć menu głównego  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> formant na formularzu.  
  
2.  Dodaj <xref:System.Windows.Forms.ToolStripMenuItem> do <xref:System.Windows.Forms.MenuStrip> kontroli i nadaj mu nazwę **okna**.  
  
3.  Wybierz <xref:System.Windows.Forms.MenuStrip> kontroli.  
  
4.  W oknie właściwości ustaw wartość <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwość `ToolStripMenuItem1`.  
  
5.  Dodaj podelement do **okna** element menu, a następnie nazwę podelement **New**.  
  
6.  W oknie dialogowym właściwości kliknij **zdarzenia**.  
  
7.  Kliknij dwukrotnie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń.  
  
     Windows Forms Designer generuje moduł obsługi zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń.  
  
8.  Wstaw następujący kod do obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>Dodawanie ToolStripPanel, kontrolka do przybornika  
 Kiedy używasz <xref:System.Windows.Forms.MenuStrip> formanty z formularza MDI konieczne jest posiadanie <xref:System.Windows.Forms.ToolStripPanel> kontroli. Należy dodać <xref:System.Windows.Forms.ToolStripPanel> kontrolę **przybornika** Tworzenie formularza MDI w programie Windows Forms Designer.  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>Aby dodać ToolStripPanel, kontrolka do przybornika  
  
1.  Otwórz **przybornika**, a następnie kliknij przycisk **wszystkie formularze Windows** kartę, aby wyświetlić dostępne kontrolki Windows Forms.  
  
2.  Kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów i wybierz **wybierz elementy**.  
  
3.  W **wybierz elementy przybornika** okno dialogowe, przewiń w dół **nazwa** kolumny, aż znajdziesz **ToolStripPanel**.  
  
4.  Zaznacz pole wyboru przy **ToolStripPanel**, a następnie kliknij przycisk **OK**.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Formant jest widoczny w **przybornika**.  
  
## <a name="creating-a-child-form"></a>Tworzenie formularza podrzędnego  
 W tej procedurze, zdefiniujesz klasę formularza oddzielny podrzędną, który ma swój własny <xref:System.Windows.Forms.MenuStrip> kontroli. Elementy menu dla tego formularza są scalane z tymi z formularza nadrzędnego.  
  
#### <a name="to-define-a-child-form"></a>Aby zdefiniować formularz podrzędny  
  
1.  Dodaj nowy formularz o nazwie `ChildForm` do projektu.  
  
     Aby uzyskać więcej informacji, zobacz [porady: dodawanie formularzy Windows do projektu](https://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
2.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> formant na formularzu podrzędnym.  
  
3.  Kliknij przycisk <xref:System.Windows.Forms.MenuStrip> symbol tagu inteligentnego kontrolki (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), a następnie wybierz pozycję **Edytuj elementy**.  
  
4.  W **Edytor kolekcji elementów** okna dialogowego Dodaj nowy <xref:System.Windows.Forms.ToolStripMenuItem> o nazwie **ChildMenuItem** do menu podrzędne.  
  
     Aby uzyskać więcej informacji, zobacz [Edytor kolekcji elementów ToolStrip](https://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).  
  
## <a name="testing-the-form"></a>Testowanie formularza  
  
#### <a name="to-test-your-form"></a>Aby przetestować formularz  
  
1.  Naciśnij klawisz F5, aby skompilować i uruchomić formularz.  
  
2.  Kliknij przycisk **okna** element menu, aby otworzyć menu, a następnie kliknij przycisk **New**.  
  
     Nowy formularz podrzędny jest tworzony w obszar klienta MDI formularza. Menu formularz podrzędny jest scalany z menu głównego.  
  
3.  Zamknij formularz podrzędny.  
  
     Formularz podrzędny menu zostanie usunięty z menu głównego.  
  
4.  Kliknij przycisk **New** kilka razy.  
  
     Formularze podrzędne są automatycznie wyświetlane w obszarze **okna** element menu, ponieważ <xref:System.Windows.Forms.MenuStrip> kontrolki <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> właściwość jest przypisana.  
  
## <a name="adding-toolstrip-support"></a>Dodanie obsługi elementu ToolStrip  
 W ramach tej procedury dodasz cztery <xref:System.Windows.Forms.ToolStrip> formantów do formularza nadrzędnego MDI. Każdy <xref:System.Windows.Forms.ToolStrip> formant jest dodawany wewnątrz <xref:System.Windows.Forms.ToolStripPanel> formant, który jest zadokowany do krawędzi formularza.  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>Aby dodać kontrolki ToolStrip formularza nadrzędnego MDI  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ToolStripPanel> formant na formularzu.  
  
2.  Za pomocą <xref:System.Windows.Forms.ToolStripPanel> zaznaczony formant, kliknij dwukrotnie <xref:System.Windows.Forms.ToolStrip> w kontrolce **przybornika**.  
  
     A <xref:System.Windows.Forms.ToolStrip> formant zostanie utworzony w <xref:System.Windows.Forms.ToolStripPanel> kontroli.  
  
3.  Wybierz <xref:System.Windows.Forms.ToolStripPanel> kontroli.  
  
4.  W oknie Właściwości zmień wartość kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Left>.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Kontrolować doków do formularza, pod menu głównego po lewej stronie. Obszar klienta MDI dopasowuje się do rozmiaru <xref:System.Windows.Forms.ToolStripPanel> kontroli.  
  
5.  Powtórz kroki od 1 do 4.  
  
     Dokowanie nowy <xref:System.Windows.Forms.ToolStripPanel> kontrolki w górnej części formularza.  
  
     <xref:System.Windows.Forms.ToolStripPanel> Kontroli jest zadokowany pod menu głównego, ale po prawej stronie pierwszej <xref:System.Windows.Forms.ToolStripPanel> kontroli. W tym kroku przedstawiono znaczenie porządek poprawnie pozycjonowania <xref:System.Windows.Forms.ToolStripPanel> kontrolki.  
  
6.  Powtórz kroki od 1 do 4 dla dwóch więcej <xref:System.Windows.Forms.ToolStripPanel> kontrolki.  
  
     Dokowanie nowy <xref:System.Windows.Forms.ToolStripPanel> kontrolek w prawo i w dolnej części formularza.  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>Rozmieszczanie kontrolek ToolStripPanel według porządku osi Z  
 Położenie zadokowanego <xref:System.Windows.Forms.ToolStripPanel> kontrolkę w formularzu MDI jest określana przez położenie formantu w porządku osi z. Łatwo można rozmieścić porządek formantów w okno konspektu dokumentu.  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>Aby rozmieścić formanty ToolStripPanel według porządku osi Z  
  
1.  W **widoku** menu, kliknij przycisk **Windows inne**, a następnie kliknij przycisk **konspekt dokumentu**.  
  
     Rozmieszczenie swoje <xref:System.Windows.Forms.ToolStripPanel> kontrolek z poprzedniej procedury jest niestandardowy. Jest to spowodowane porządku osi jest nieprawidłowy. Okno konspektu dokumentu do zmiany kolejności z formantów.  
  
2.  W oknie konspekt dokumentu wybierz **ToolStripPanel4**.  
  
3.  Kliknij przycisk strzałki w dół wielokrotnie, dopóki **ToolStripPanel4** znajduje się w dolnej części listy.  
  
     **ToolStripPanel4** kontroli jest zadokowana do dolnej części formularza, poniżej innych kontrolek.  
  
4.  Wybierz **ToolStripPanel2**.  
  
5.  Kliknij jeden raz przycisk strzałki w dół, aby położenie formantu trzeci na liście.  
  
     **ToolStripPanel2** kontroli jest zadokowany do górnej części formularza, pod menu głównego i nowszych innych kontrolek.  
  
6.  Wybierz różne formanty w **konspekt dokumentu** okna i przenoszenia ich do różnych pozycji w porządku osi z. Należy pamiętać, efekt porządku osi z o rozmieszczaniu zadokowanych formantów. Użyj klawiszy CTRL-Z lub **Cofnij** na **Edytuj** menu, aby cofnąć zmiany.  
  
## <a name="checkpoint"></a>Punkt kontrolny  
  
#### <a name="to-test-your-form"></a>Aby przetestować formularz  
  
1.  Naciśnij klawisz F5, aby skompilować i uruchomić formularz.  
  
2.  Kliknij przycisk uchwyt zmiany z <xref:System.Windows.Forms.ToolStrip> kontroli i przeciągnij formant w różnych miejscach na formularzu.  
  
     Można przeciągnąć <xref:System.Windows.Forms.ToolStrip> formant z jednej <xref:System.Windows.Forms.ToolStripPanel> formantu do innego.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku zostały utworzone za pomocą formularza nadrzędnego MDI <xref:System.Windows.Forms.ToolStrip> kontrolek i scalanie menu. Możesz użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:  
  
-   Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>. Aby uzyskać więcej informacji, zobacz [— informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Formularz utworzony za pomocą automatycznie wypełnione standardowe menu. Aby uzyskać więcej informacji, zobacz [wskazówki: zapewnianie standardowych elementów Menu do formularza](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Nadaj swojej <xref:System.Windows.Forms.ToolStrip> profesjonalny wygląd kontrolki. Aby uzyskać więcej informacji, zobacz [porady: ustawienie modułu renderowania ToolStrip dla aplikacji](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Instrukcje: tworzenie formularzy nadrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Instrukcje: tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Instrukcje: wstawianie kontrolki MenuStrip do menu rozwijanego MDI](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [ToolStrip, kontrolka](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
