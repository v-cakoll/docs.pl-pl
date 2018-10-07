---
title: 'Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: c528e95b37abb230e761ce93e5f5c7bcb27d30d3
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837248"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Formularze Windows <xref:System.Windows.Forms.DataGrid> kontroli jest specjalnie przeznaczona do wyświetlania informacji ze źródła danych. Powiązywanie formantu w czasie projektowania, ustawiając <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości, lub w czasie wykonywania przez wywołanie metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody. Choć można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła są zestawy danych i widokami danych.  
  
 Jeśli źródło danych jest dostępna w czasie projektowania — na przykład, jeśli formularz zawiera wystąpienie zestawu danych lub widoku danych — Siatka można powiązać ze źródłem danych w czasie projektowania. Możesz przeglądać dane jak będzie wyglądał w siatce.  
  
 Możesz również powiązać siatki programowo, w czasie wykonywania. Jest to przydatne, jeśli chcesz ustawić źródło danych, w oparciu o informacje, które otrzymujesz w czasie wykonywania. Na przykład aplikacja może zezwolić użytkownikom na Określ nazwę tabeli, aby wyświetlić. Konieczne jest również w sytuacji, gdy źródło danych nie istnieje w czasie projektowania. W tym źródeł danych, takich jak tablice, kolekcje, nietypizowanych zbiorów danych oraz czytniki danych.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGrid> kontroli. Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). W programie Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> formantu nie znajduje się w **przybornika** domyślnie. Aby uzyskać informacje dotyczące dodawania go, zobacz [porady: Dodawanie elementów do przybornika](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0). Ponadto w programie Visual Studio 2005, można za pomocą **źródeł danych** okna dla powiązania danych w czasie projektowania. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Aby powiązanie danych kontrolki DataGrid z pojedynczej tabeli w Projektancie  
  
1.  Ustaw dla formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.  
  
2.  Jeśli źródło danych zestawu danych, ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwość na nazwę tabeli dla powiązania.  
  
3.  W przypadku zestawu danych lub widoku danych, na podstawie tabeli zestawu danych źródła danych należy dodać kod do formularza, aby wypełnić dataset.  
  
     Dokładne kod, który możesz użyć zależy od tego, gdzie zestaw danych jest wprowadzenie danych. Jeśli trwa wypełnianie zestawu danych bezpośrednio z bazy danych, zazwyczaj wywołujesz `Fill` metody w obrębie adaptera danych, jak w poniższym przykładzie kodu, który wypełnia zestaw danych o nazwie `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  (Opcjonalnie) Dodaj style odpowiedniej tabeli i kolumn do siatki.  
  
     Jeśli nie ma żadnych style tabeli, tabeli, zostanie wyświetlony, ale z minimalnym formatowania i widoczne dla wszystkich kolumn.  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Aby powiązanie danych kontrolki DataGrid z wielu tabel w zestawie danych w Projektancie  
  
1.  Ustaw dla formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.  
  
2.  Jeśli zestaw danych zawiera tabele powiązane (to znaczy, jeśli zawiera on obiektu relacji), ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwość na nazwę tabeli nadrzędnej.  
  
3.  Pisz kod, aby wypełnić dataset.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGrid, kontrolka — omówienie](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Wiązanie danych formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
