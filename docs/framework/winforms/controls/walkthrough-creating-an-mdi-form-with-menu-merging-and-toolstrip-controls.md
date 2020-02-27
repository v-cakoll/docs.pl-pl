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
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628790"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Wskazówki: tworzenie formularza MDI ze scalaniem menu i formantami ToolStrip

Przestrzeń nazw <xref:System.Windows.Forms?displayProperty=nameWithType> obsługuje aplikacje interfejsu wielu dokumentów (MDI), a kontrolka <xref:System.Windows.Forms.MenuStrip> obsługuje scalanie menu. Formularze MDI mogą również <xref:System.Windows.Forms.ToolStrip> kontrolki.

W tym instruktażu pokazano, jak używać formantów <xref:System.Windows.Forms.ToolStripPanel> z formularzem MDI. Formularz obsługuje również scalanie menu z menu podrzędnymi. W tym instruktażu przedstawiono następujące zadania:

- Tworzenie projektu Windows Forms.

- Tworzenie menu głównego formularza. Rzeczywista nazwa menu będzie się różnić.

- Dodawanie kontrolki <xref:System.Windows.Forms.ToolStripPanel> do **przybornika**.

- Tworzenie formularza podrzędnego.

- Rozmieszczanie kontrolek <xref:System.Windows.Forms.ToolStripPanel> według kolejności z.

Po zakończeniu będziesz mieć formularz MDI obsługujący scalanie menu i ruchome kontrolki <xref:System.Windows.Forms.ToolStrip>.

Aby skopiować kod w tym temacie jako pojedynczą listę, zobacz [How to: Create a MDI form with menu Scales and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, musisz mieć program Visual Studio.

## <a name="create-the-project"></a>Tworzenie projektu

1. W programie Visual Studio Utwórz projekt aplikacji systemu Windows o **nazwie MdiForm** (**plik** > **New** > **Project** > **Visual C#**  lub **Visual Basic** > **klasycznego pulpitu** > Windows Forms **aplikacji**).

2. W Projektant formularzy systemu Windows wybierz formularz.

3. W okno Właściwości ustaw wartość <xref:System.Windows.Forms.Form.IsMdiContainer%2A> do `true`.

## <a name="create-the-main-menu"></a>Utwórz menu główne

Nadrzędny formularz MDI zawiera menu główne. Menu główne ma jeden element menu o nazwie **window**. Za pomocą elementu menu **okno** można tworzyć formularze podrzędne. Elementy menu z formularzy podrzędnych są scalane z menu głównym.

1. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.MenuStrip> na formularz.

2. Dodaj <xref:System.Windows.Forms.ToolStripMenuItem> do kontrolki <xref:System.Windows.Forms.MenuStrip> i nadaj jej nazwę **okno**.

3. Wybierz kontrolkę <xref:System.Windows.Forms.MenuStrip>.

4. W okno Właściwości ustaw wartość właściwości <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> na `ToolStripMenuItem1`.

5. Dodaj element SubItem do elementu menu **okno** , a następnie nadaj mu nazwę **Nowy**.

6. W okno Właściwości kliknij pozycję **zdarzenia**.

7. Kliknij dwukrotnie zdarzenie <xref:System.Windows.Forms.ToolStripItem.Click>.

     Projektant formularzy systemu Windows generuje procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click>.

8. Wstaw następujący kod do programu obsługi zdarzeń.

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a>Dodaj kontrolkę ToolStripPanel do przybornika

W przypadku używania formantów <xref:System.Windows.Forms.MenuStrip> z formularzem MDI należy mieć kontrolkę <xref:System.Windows.Forms.ToolStripPanel>. Musisz dodać formant <xref:System.Windows.Forms.ToolStripPanel> do **przybornika** , aby skompilować formularz MDI w Projektant formularzy systemu Windows.

1. Otwórz **Przybornik**, a następnie kliknij kartę **wszystkie Windows Forms** , aby wyświetlić dostępne kontrolki Windows Forms.

2. Kliknij prawym przyciskiem myszy, aby otworzyć menu skrótów, a następnie wybierz pozycję **Wybierz elementy**.

3. W oknie dialogowym **Wybierz elementy przybornika** przewiń w dół kolumnę **Nazwa** do momentu znalezienia **ToolStripPanel**.

4. Zaznacz pole wyboru przez **ToolStripPanel**, a następnie kliknij przycisk **OK**.

     Kontrolka <xref:System.Windows.Forms.ToolStripPanel> zostanie wyświetlona w **przyborniku**.

## <a name="create-a-child-form"></a>Tworzenie formularza podrzędnego

W tej procedurze zdefiniujesz osobną klasę formularza podrzędnego, która ma własną kontrolkę <xref:System.Windows.Forms.MenuStrip>. Elementy menu dla tego formularza są scalone z formularzami nadrzędnymi.

1. Dodaj nowy formularz o nazwie `ChildForm` do projektu.

     Aby uzyskać więcej informacji, zobacz [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).

2. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.MenuStrip> na formularz podrzędny.

3. Kliknij symbol akcji projektanta <xref:System.Windows.Forms.MenuStrip> kontrolki (![małą czarną strzałkę](./media/designer-actions-glyph.gif)), a następnie wybierz pozycję **Edytuj elementy**.

4. W oknie dialogowym **Edytor kolekcji elementów** dodaj nowe <xref:System.Windows.Forms.ToolStripMenuItem> o nazwie **ChildMenuItem** do menu podrzędnego.

     Aby uzyskać więcej informacji, zobacz [Edytor kolekcji elementów ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).

## <a name="test-the-form"></a>Testowanie formularza

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić formularz.

2. Kliknij element menu **okno** , aby otworzyć menu, a następnie kliknij przycisk **Nowy**.

     W obszarze klienta MDI formularza zostanie utworzony nowy formularz podrzędny. Menu podrzędny formularz zostanie scalone z menu głównym.

3. Zamknij formularz podrzędny.

     Menu podrzędne formularza zostanie usunięte z menu głównego.

4. Kliknij przycisk **nowe** kilka razy.

     Formularze podrzędne są automatycznie wyświetlane w elemencie menu **okna** , ponieważ właściwość <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> formantu <xref:System.Windows.Forms.MenuStrip> jest przypisana.

## <a name="add-toolstrip-support"></a>Dodaj obsługę elementu ToolStrip

W ramach tej procedury dodasz cztery <xref:System.Windows.Forms.ToolStrip> kontrolki do formularza nadrzędnego MDI. Każda kontrolka <xref:System.Windows.Forms.ToolStrip> jest dodawana wewnątrz kontrolki <xref:System.Windows.Forms.ToolStripPanel>, która jest zadokowana do krawędzi formularza.

1. Z **przybornika**przeciągnij kontrolkę <xref:System.Windows.Forms.ToolStripPanel> na formularz.

2. Po wybraniu kontrolki <xref:System.Windows.Forms.ToolStripPanel> kliknij dwukrotnie kontrolkę <xref:System.Windows.Forms.ToolStrip> w **przyborniku**.

     Formant <xref:System.Windows.Forms.ToolStrip> jest tworzony w kontrolce <xref:System.Windows.Forms.ToolStripPanel>.

3. Wybierz kontrolkę <xref:System.Windows.Forms.ToolStripPanel>.

4. W okno Właściwości zmień wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> kontrolki na <xref:System.Windows.Forms.DockStyle.Left>.

     Formant <xref:System.Windows.Forms.ToolStripPanel> jest zadokowany do lewej strony formularza, pod menu głównym. Rozmiar obszaru klienta MDI dopasowuje się do kontrolki <xref:System.Windows.Forms.ToolStripPanel>.

5. Powtórz kroki od 1 do 4.

     Zadokuj nową kontrolkę <xref:System.Windows.Forms.ToolStripPanel> w górnej części formularza.

     Kontrolka <xref:System.Windows.Forms.ToolStripPanel> jest zadokowana pod menu głównym, ale z prawej strony pierwszej kontrolki <xref:System.Windows.Forms.ToolStripPanel>. Ten krok przedstawia ważność porządku osi z w prawidłowym rozmieszczeniem <xref:System.Windows.Forms.ToolStripPanel> kontrolek.

6. Powtórz kroki od 1 do 4 dla dwóch kolejnych kontrolek <xref:System.Windows.Forms.ToolStripPanel>.

     Zadokuj nowe kontrolki <xref:System.Windows.Forms.ToolStripPanel> w prawo i u dołu formularza.

## <a name="arrange-toolstrippanel-controls-by-z-order"></a>Rozmieść kontrolki ToolStripPanel według kolejności Z

Pozycja formantu <xref:System.Windows.Forms.ToolStripPanel> zadokowanego w formularzu MDI jest określana na podstawie położenia kontrolki w kolejności z. Można łatwo rozmieścić porządek osi z kontrolek w oknie konspektu dokumentu.

1. W menu **Widok** kliknij pozycję **inne okna**, a następnie kliknij pozycję **Konspekt dokumentu**.

     Układ formantów <xref:System.Windows.Forms.ToolStripPanel> z poprzedniej procedury jest niestandardowy. Wynika to z faktu, że porządek osi z jest niepoprawny. Użyj okna Konspekt dokumentu, aby zmienić porządek osi z kontrolek.

2. W oknie Konspekt dokumentu wybierz pozycję **ToolStripPanel4**.

3. Klikaj ponownie przycisk strzałki w dół, aż **ToolStripPanel4** znajduje się w dolnej części listy.

     Formant **ToolStripPanel4** jest zadokowany w dolnej części formularza, pod innymi kontrolkami.

4. Wybierz pozycję **ToolStripPanel2**.

5. Kliknij przycisk strzałki w dół, aby umieścić formant trzeci na liście.

     Kontrolka **ToolStripPanel2** jest zadokowana w górnej części formularza, pod menu głównym i nad innymi kontrolkami.

6. Wybierz różne kontrolki w oknie **konspektu dokumentu** i przenieś je do różnych pozycji w kolejności z. Zwróć uwagę na efekt porządku osi z na rozłożeniu zadokowanych kontrolek. Aby cofnąć zmiany, użyj klawiszy CTRL-Z lub **Cofnij** w menu **Edycja** .

## <a name="checkpoint---test-your-form"></a>Punkt kontrolny — testowanie formularza

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić formularz.

2. Kliknij uchwyt kontrolki <xref:System.Windows.Forms.ToolStrip> i przeciągnij formant do różnych pozycji w formularzu.

     Kontrolkę <xref:System.Windows.Forms.ToolStrip> można przeciągnąć z jednej kontrolki <xref:System.Windows.Forms.ToolStripPanel> do innej.

## <a name="next-steps"></a>Następne kroki

W tym instruktażu utworzono formularz nadrzędny MDI z kontrolkami <xref:System.Windows.Forms.ToolStrip> i scalaniem menu. W wielu innych celach można użyć <xref:System.Windows.Forms.ToolStrip>ej rodziny formantów:

- Utwórz menu skrótów dla kontrolek z <xref:System.Windows.Forms.ContextMenuStrip>. Aby uzyskać więcej informacji, zobacz temat [Omówienie składnika](contextmenu-component-overview-windows-forms.md)usługi.

- Utworzono formularz z automatycznie wypełnionym menu standardowym. Aby uzyskać więcej informacji, zobacz [Przewodnik: zapewnianie elementów menu standardowego w formularzu](walkthrough-providing-standard-menu-items-to-a-form.md).

- Nadaj <xref:System.Windows.Forms.ToolStrip> kontrolę nad profesjonalnym wyglądem. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie modułu renderowania ToolStrip dla aplikacji](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Instrukcje: tworzenie formularzy nadrzędnych MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Instrukcje: tworzenie formularzy podrzędnych MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Instrukcje: wstawianie kontrolki MenuStrip do menu rozwijanego MDI](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
