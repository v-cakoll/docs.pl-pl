---
title: 'Porady: dodawanie tabel i kolumn do formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: 4b29a3040415cce8fad27abf9bf46aa3d3e14b4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528419"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Porady: dodawanie tabel i kolumn do formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Dane można wyświetlać w formularzach systemu Windows <xref:System.Windows.Forms.DataGrid> kontrolki tabele i kolumny, tworząc <xref:System.Windows.Forms.DataGridTableStyle> obiektów oraz dodanie ich do <xref:System.Windows.Forms.GridTableStylesCollection> obiektu, który jest dostępny za pośrednictwem <xref:System.Windows.Forms.DataGrid> formantu <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości. Każdy styl tabeli Wyświetla zawartość niezależnie od tabeli danych jest określona w <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość <xref:System.Windows.Forms.DataGridTableStyle>. Domyślny styl tabeli bez kolumn style określone będą wyświetlane wszystkie kolumny w tabeli danych. Można ograniczyć, które kolumny z tabeli są wyświetlane przez dodanie <xref:System.Windows.Forms.DataGridColumnStyle> obiekty do <xref:System.Windows.Forms.GridColumnStylesCollection>, który jest dostępny za pośrednictwem <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości każdego <xref:System.Windows.Forms.DataGridTableStyle>.  
  
 Wykonanie poniższych procedur wymaga **aplikacji systemu Windows** projektu z formularza, który zawiera <xref:System.Windows.Forms.DataGrid> formantu. Informacje dotyczące sposobu konfigurowania tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Domyślnie w [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> formant nie ma na liście **przybornika**. Uzyskać informacje dotyczące dodawania go, zobacz [porady: Dodawanie elementów do przybornika](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Aby dodać tabelę z formantem DataGrid w Projektancie  
  
1.  Aby wyświetlić dane w tabeli, należy najpierw powiązać <xref:System.Windows.Forms.DataGrid> formantu do zestawu danych. Aby uzyskać więcej informacji, zobacz [porady: powiązywanie formantu DataGrid formularzy systemu Windows do źródła danych przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).  
  
2.  Wybierz <xref:System.Windows.Forms.DataGrid> formantu <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości w oknie właściwości, a następnie kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji Właściwość do wyświetlenia **edytora kolekcji Element DataGridTableStyle**.  
  
3.  W oknie Edytor kolekcji kliknij przycisk **Dodaj** do wstawienia styl tabeli.  
  
4.  Kliknij przycisk **OK** Zamknij okno Edytor kolekcji i otwórz go ponownie, klikając przycisk wielokropka obok <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości.  
  
     Po ponownym otwarciu edytora kolekcji, wszystkie tabele danych powiązane z formantem pojawi się na liście rozwijanej <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwości stylu tabeli.  
  
5.  W **członków** okno edytora kolekcji, kliknij odpowiedni styl tabeli.  
  
6.  W **właściwości** okno Edytor kolekcji, wybierz opcję <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> wartość dla tabeli, które mają być wyświetlane.  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Aby dodać kolumnę z formantem DataGrid w Projektancie  
  
1.  W **członków** pole **edytora kolekcji Element DataGridTableStyle**, wybierz styl odpowiedniej tabeli. W **właściwości** okno Edytor kolekcji, wybierz opcję <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekcji, a następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) obok właściwości do wyświetlenia **edytora kolekcji DataGridColumnStyle**.  
  
2.  W edytorze kolekcji, kliknij przycisk **Dodaj** wstawić styl kolumny lub kliknij strzałkę w dół obok pozycji **Dodaj** do określenia typu kolumny.  
  
     W polu listy rozwijanej można wybrać dowolną <xref:System.Windows.Forms.DataGridTextBoxColumn> lub <xref:System.Windows.Forms.DataGridBoolColumn> typu.  
  
3.  Kliknij przycisk OK, aby zamknąć **edytora kolekcji DataGridColumnStyle**, a następnie otwórz go ponownie, klikając przycisk wielokropka obok <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości.  
  
     Po ponownym Edytor kolekcji kolumn danych w tabeli danych powiązanej pojawi się na liście rozwijanej <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> właściwości stylu kolumny.  
  
4.  W **członków** okno edytora kolekcji, kliknij odpowiedni styl kolumny.  
  
5.  W **właściwości** okno Edytor kolekcji, wybierz opcję <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> wartość dla kolumny, która ma być wyświetlany.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
