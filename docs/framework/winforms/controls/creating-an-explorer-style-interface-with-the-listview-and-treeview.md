---
title: "Wskazówki: tworzenie interfejsu w stylu Eksploratora Windows z kontrolkami ListView i TreeView za pomocą narzędzia Projektant"
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
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d8d7991f706f8098e4ac475ae057771de200197
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>Wskazówki: tworzenie interfejsu w stylu Eksploratora Windows z kontrolkami ListView i TreeView za pomocą narzędzia Projektant
Jedną z korzyści programu Visual Studio jest możliwość tworzenia profesjonalnych aplikacji formularzy systemu Windows w krótkim czasie. Typowy scenariusz tworzy interfejs użytkownika (UI) z <xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView> formantów, które pełni podobną funkcję Eksploratora Windows, systemów operacyjnych Windows. Eksplorator Windows wyświetla strukturę hierarchiczną plików i folderów na komputerze użytkownika.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Aby utworzyć formularz zawierający formant ListView i TreeView  
  
1.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, wykonaj następujące czynności:  
  
    1.  W kategorii, wybierz **Visual Basic** lub **Visual C#**.  
  
    2.  Na liście szablonów wybierz **aplikacji Windows Forms**.  
  
3.  Kliknij przycisk **OK**. Utworzono nowy projekt formularzy systemu Windows.  
  
4.  Dodaj <xref:System.Windows.Forms.SplitContainer> sterowania do formularza i ustawić jej <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Dodaj <xref:System.Windows.Forms.ImageList> o nazwie `imageList1` formularza i użyj okna właściwości, aby dodać dwa obrazy: Obraz folderu i obraz dokumentu w podanej kolejności.  
  
6.  Dodaj <xref:System.Windows.Forms.TreeView> formantu o nazwie `treeview1` do formularza i umieść go w lewej części <xref:System.Windows.Forms.SplitContainer> formantu. W oknie dialogowym właściwości `treeView1` wykonaj następujące czynności:  
  
    1.  Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Ustaw <xref:System.Windows.Forms.TreeView.ImageList%2A> właściwości`imagelist1.`  
  
7.  Dodaj <xref:System.Windows.Forms.ListView> formantu o nazwie `listView1` do formularza i umieść go w prawej części <xref:System.Windows.Forms.SplitContainer> formantu. W oknie dialogowym właściwości `listview1` wykonaj następujące czynności:  
  
    1.  Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwości <xref:System.Windows.Forms.View.Details>.  
  
    3.  Otwórz Edytor kolekcji ColumnHeader, klikając przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) w <xref:System.Windows.Forms.ListView.Columns%2A> właściwości**.** Dodaj trzy kolumny i ustawić ich <xref:System.Windows.Forms.ColumnHeader.Text%2A> właściwości `Name`, `Type`, i `Last Modified`odpowiednio. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
    4.  Ustaw <xref:System.Windows.Forms.ListView.SmallImageList%2A> właściwości`imageList1.`  
  
8.  Zaimplementuj kod, aby wypełnić <xref:System.Windows.Forms.TreeView> z węzłów i węzły podrzędne. Dodaj ten kod do `Form1` klasy.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. Ponieważ poprzedni kod używa przestrzeni nazw System.IO, Dodaj odpowiednie using lub zaimportować instrukcji w górnej części formularza.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. Wywołaj metodę konfiguracji z poprzedniego kroku w Konstruktorze formularza lub <xref:System.Windows.Forms.Form.Load> metoda obsługi zdarzeń. Dodaj ten kod do konstruktora formularza.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. Obsługa <xref:System.Windows.Forms.TreeView.NodeMouseClick> zdarzenia dla `treeview1` **,** i zaimplementuj kod, aby wypełnić `listview1` zawartością węzła, gdy węzeł zostanie kliknięty. Dodaj ten kod do `Form1` klasy.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     Jeśli używasz języka C#, upewnij się, masz <xref:System.Windows.Forms.TreeView.NodeMouseClick> zdarzenia skojarzonego z metody obsługi zdarzeń. Dodaj ten kod do konstruktora formularza.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
-   Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Zostanie wyświetlony formularz podziału zawierający <xref:System.Windows.Forms.TreeView> kontrolkę wyświetlającą katalogu projektu po lewej stronie, a <xref:System.Windows.Forms.ListView> kontroli po prawej stronie z trzech kolumn. Można przechodzić między nimi <xref:System.Windows.Forms.TreeView> , wybierając węzeł katalogu i <xref:System.Windows.Forms.ListView> jest wypełniana zawartość wybranego katalogu.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zawiera przykładowy sposób korzystania <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ListView> formanty razem. Aby uzyskać więcej informacji tych kontrolek zobacz następujące tematy:  
  
-   [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [Instrukcje: dodawanie funkcji wyszukiwania do kontrolki ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [Instrukcje: dołączanie menu ShortCut do węzła TreeView](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
