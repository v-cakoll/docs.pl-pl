---
title: 'Przewodnik: tworzenie interfejsu w stylu Eksploratora Windows z kontrolkami ListView i TreeView za pomocą narzędzia Projektant'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: 540226dbbada0373854144ac874d2164208ad943
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039911"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>Przewodnik: tworzenie interfejsu w stylu Eksploratora Windows z kontrolkami ListView i TreeView za pomocą narzędzia Projektant

Jedną z zalet programu Visual Studio jest możliwość tworzenia profesjonalnych aplikacji Windows Forms w krótkim czasie. Typowy scenariusz polega na tworzeniu interfejsu użytkownika z <xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView> kontrolkami, które przypominają funkcję Eksploratora Windows w systemach operacyjnych Windows. Eksplorator Windows wyświetla hierarchiczną strukturę plików i folderów na komputerze użytkownika.


### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Aby utworzyć formularz zawierający formant ListView i widok TreeView

1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** wykonaj następujące czynności:

    1. W kategorii wybierz opcję **Visual Basic** lub wizualizacji **C#** .

    2. Z listy szablonów wybierz **Windows Forms aplikacji**.

3. Kliknij przycisk **OK**. Tworzony jest nowy projekt Windows Forms.

4. Dodaj kontrolkę do formularza i ustaw jej <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość na <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.SplitContainer>

5. <xref:System.Windows.Forms.ImageList> Dodaj nazwę `imageList1` do formularza i użyj okno właściwości, aby dodać dwa obrazy: obraz folderu i obraz dokumentu w tej kolejności.

6. Dodaj kontrolkę o `treeview1` nazwie do formularza i umieść ją po lewej stronie <xref:System.Windows.Forms.SplitContainer> kontrolki. <xref:System.Windows.Forms.TreeView> W okno właściwości `treeView1` wykonaj następujące czynności:

    1. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.

    2. <xref:System.Windows.Forms.TreeView.ImageList%2A> Ustaw właściwość na`imagelist1.`

7. Dodaj kontrolkę o `listView1` nazwie do formularza i umieść ją po prawej stronie <xref:System.Windows.Forms.SplitContainer> kontrolki. <xref:System.Windows.Forms.ListView> W okno właściwości `listview1` wykonaj następujące czynności:

    1. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.

    2. Ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwość <xref:System.Windows.Forms.View.Details>.

    3. Otwórz Edytor kolekcji ColumnHeader,![klikając wielokropek (przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) we <xref:System.Windows.Forms.ListView.Columns%2A> właściwości **.** Dodaj trzy kolumny i ustaw ich <xref:System.Windows.Forms.ColumnHeader.Text%2A> właściwość na `Name`, `Type`, i `Last Modified`, odpowiednio. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.

    4. <xref:System.Windows.Forms.ListView.SmallImageList%2A> Ustaw właściwość na`imageList1.`

8. Zaimplementuj kod, aby wypełnić <xref:System.Windows.Forms.TreeView> węzły węzłami i podrzędnymi. Dodaj ten kod do `Form1` klasy.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. Ponieważ poprzedni kod używa przestrzeni nazw System.IO, Dodaj odpowiednią instrukcję using lub import w górnej części formularza.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. Wywołaj metodę Set z poprzedniego kroku w konstruktorze lub <xref:System.Windows.Forms.Form.Load> metodzie obsługi zdarzeń. Dodaj ten kod do konstruktora formularzy.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. Obsłuż `treeview1`zdarzeniedlai zaimplementuj kod, aby wypełnić `listview1` zawartość węzła po kliknięciu węzła. <xref:System.Windows.Forms.TreeView.NodeMouseClick> Dodaj ten kod do `Form1` klasy.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     Jeśli używasz C#programu, upewnij się, że masz <xref:System.Windows.Forms.TreeView.NodeMouseClick> zdarzenie skojarzone z jego metodą obsługi zdarzeń. Dodaj ten kod do konstruktora formularzy.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a>Testowanie aplikacji

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

- Naciśnij klawisz F5, aby uruchomić aplikację.

     Zobaczysz formularz podzielony zawierający <xref:System.Windows.Forms.TreeView> kontrolkę wyświetlającą katalog projektu po lewej stronie <xref:System.Windows.Forms.ListView> i kontrolkę po prawej stronie z trzema kolumnami. Możesz przejść <xref:System.Windows.Forms.TreeView> przez wybranie węzłów katalogów, <xref:System.Windows.Forms.ListView> a zostanie wypełniony zawartość wybranego katalogu.

## <a name="next-steps"></a>Następne kroki

Ta aplikacja stanowi przykład sposobu użycia <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ListView> kontroli razem. Aby uzyskać więcej informacji na temat tych kontrolek, zobacz następujące tematy:

- [Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [Instrukcje: Dodawanie funkcji wyszukiwania do formantu ListView](how-to-add-search-capabilities-to-a-listview-control.md)

- [Instrukcje: Dołącz menu skrótów do węzła TreeView](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie węzłów za pomocą kontrolki TreeView Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie kolumn do kontrolki ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
