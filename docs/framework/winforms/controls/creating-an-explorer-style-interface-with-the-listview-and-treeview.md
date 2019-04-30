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
ms.openlocfilehash: 8192151aa7cd5eddd99d39adb485e460074fdb99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768592"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>Przewodnik: tworzenie interfejsu w stylu Eksploratora Windows z kontrolkami ListView i TreeView za pomocą narzędzia Projektant
Jedną z zalet programu Visual Studio jest możliwość tworzenia profesjonalnych aplikacji Windows Forms w krótki czas. Typowym scenariuszem jest tworzenie interfejsu użytkownika (UI) za pomocą <xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView> formantów, które przypomina funkcji Eksploratora Windows, systemów operacyjnych Windows. Eksplorator Windows wyświetla hierarchiczną strukturę plików i folderów na komputerze użytkownika.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Aby utworzyć formularz zawierający kontrolki ListView i TreeView  
  
1. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
2. W **nowy projekt** okna dialogowego pole, wykonaj następujące czynności:  
  
    1. Do kategorii wybierz **języka Visual Basic** lub **Visual C#**.  
  
    2. Z listy szablonów wybierz **aplikacja interfejsu Windows Forms**.  
  
3. Kliknij przycisk **OK**. Utworzono nowy projekt Windows Forms.  
  
4. Dodaj <xref:System.Windows.Forms.SplitContainer> do formularza i ustaw jego <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5. Dodaj <xref:System.Windows.Forms.ImageList> o nazwie `imageList1` formularza i użyj okna właściwości, aby dodać dwa obrazy: Obraz folderu i obraz dokumentu w tej kolejności.  
  
6. Dodaj <xref:System.Windows.Forms.TreeView> formantu o nazwie `treeview1` do formularza i umieść ją w lewej części <xref:System.Windows.Forms.SplitContainer> kontroli. W oknie dialogowym właściwości `treeView1` wykonaj następujące czynności:  
  
    1. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2. Ustaw <xref:System.Windows.Forms.TreeView.ImageList%2A> właściwości `imagelist1.`  
  
7. Dodaj <xref:System.Windows.Forms.ListView> formantu o nazwie `listView1` do formularza i umieść ją na prawej krawędzi <xref:System.Windows.Forms.SplitContainer> kontroli. W oknie dialogowym właściwości `listview1` wykonaj następujące czynności:  
  
    1. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2. Ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwość <xref:System.Windows.Forms.View.Details>.  
  
    3. Otwórz ColumnHeader — Edytor kolekcji, klikając przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) w <xref:System.Windows.Forms.ListView.Columns%2A> właściwość **.** Dodaj trzy kolumny i ustaw ich <xref:System.Windows.Forms.ColumnHeader.Text%2A> właściwości `Name`, `Type`, i `Last Modified`, odpowiednio. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
    4. Ustaw <xref:System.Windows.Forms.ListView.SmallImageList%2A> właściwości `imageList1.`  
  
8. Implementowania kodu służącego do wypełnienia <xref:System.Windows.Forms.TreeView> z węzłów i węzłów podrzędnych. Dodaj następujący kod do `Form1` klasy.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. Ponieważ w poprzednim kodzie używa przestrzeni nazw System.IO, Dodaj odpowiedni using lub Importuj instrukcję w górnej części formularza.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. Wywołaj metodę konfiguracji z poprzedniego kroku w Konstruktorze formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń. Dodaj następujący kod do konstruktora formularza.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. Obsługa <xref:System.Windows.Forms.TreeView.NodeMouseClick> zdarzenia dla `treeview1` **,** i zaimplementuj kod, aby wypełnić `listview1` z zawartością węzła po kliknięciu węzła. Dodaj następujący kod do `Form1` klasy.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     Jeśli używasz języka C#, upewnij się, że masz <xref:System.Windows.Forms.TreeView.NodeMouseClick> zdarzenie skojarzone z jego metody obsługi zdarzeń. Dodaj następujący kod do konstruktora formularza.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
- Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Zostanie wyświetlony, zawierający formularz podziału <xref:System.Windows.Forms.TreeView> formant, który wyświetla katalogu projektu po lewej stronie i <xref:System.Windows.Forms.ListView> kontroli po prawej stronie przy użyciu trzech kolumnach. Mogą przechodzić <xref:System.Windows.Forms.TreeView> , wybierając węzłów katalogu i <xref:System.Windows.Forms.ListView> jest wypełniana przy użyciu zawartość wybranego katalogu.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zawiera przykładowy sposób korzystania <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ListView> kontroluje ze sobą. Aby uzyskać więcej informacji na temat tych kontrolek zobacz następujące tematy:  
  
- [Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)](add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
- [Instrukcje: Dodawanie możliwości wyszukiwania do formantu ListView](how-to-add-search-capabilities-to-a-listview-control.md)  
  
- [Instrukcje: Dołączanie ShortCut Menu do węzła TreeView](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą formantu ListView formularzy Windows](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows](how-to-add-columns-to-the-windows-forms-listview-control.md)
