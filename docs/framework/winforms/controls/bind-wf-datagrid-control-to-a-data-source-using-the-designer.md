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
ms.openlocfilehash: 1be8a31957bc439c140c1b6c5fc24e3221860c80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529512"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Formularze systemu Windows <xref:System.Windows.Forms.DataGrid> kontrolki przeznaczone do wyświetlania informacji ze źródła danych. Powiązywanie formantu w czasie projektowania, ustawiając <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości, lub w czasie wykonywania, wywołując <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody. Choć można wyświetlać danych z różnych źródeł danych, najbardziej typowe źródła są widoków danych i zestawów danych.  
  
 Jeśli źródło danych jest dostępne w czasie projektowania — na przykład, jeśli formularz zawiera wystąpienia wartość dataset lub widok danych — siatki można powiązać źródła danych w czasie projektowania. Następnie możesz przeglądać dane wyglądu w siatce.  
  
 Siatka może także powiązać programowo, w czasie wykonywania. Jest to przydatne, jeśli chcesz ustawić źródło danych na podstawie informacji, które pojawia się w czasie wykonywania. Na przykład aplikacja może pozwolić użytkownika, określ nazwę tabeli, aby wyświetlić. Konieczne jest również w sytuacji, gdy źródło danych nie istnieje w czasie projektowania. W tym źródeł danych, takich jak tablic, kolekcje nietypizowane zbiory danych i czytniki danych.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGrid> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). W [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> formant nie ma na liście **przybornika** domyślnie. Uzyskać informacje dotyczące dodawania go, zobacz [porady: Dodawanie elementów do przybornika](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0). Ponadto w [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], można użyć **źródeł danych** okna dla powiązania danych czasu projektowania. Aby uzyskać więcej informacji, zobacz [powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Do wiązania danych formantu DataGrid do pojedynczej tabeli w Projektancie  
  
1.  Ustawianie formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.  
  
2.  Jeśli źródło danych jest zestawu danych, ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości do nazwy tabeli, aby powiązać.  
  
3.  Jeśli źródło danych jest wartość dataset lub widok danych na podstawie tabeli zestawu danych, należy dodać kodu do formularza, aby wypełnić dataset.  
  
     Dokładnego kodu, używanego zależy od tego, gdzie zestawu danych jest pobieranie danych. Jeśli jest on wypełnione zestawu danych bezpośrednio z bazy danych, należy zwykle wywołują `Fill` metody adapter danych, jak w poniższym przykładzie kodu, który wypełnia zestawu danych o nazwie `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  (Opcjonalnie) Dodaj style właściwe tabeli i Style kolumn do tabeli.  
  
     Jeśli nie ma żadnych stylów tabeli, zobaczysz tabeli, ale z minimalnym formatowanie i widoczne wszystkie kolumny.  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Do wiązania danych formantu DataGrid z wieloma tabelami w zestawie danych w Projektancie  
  
1.  Ustawianie formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.  
  
2.  Jeśli zestaw danych zawiera tabele powiązane (to znaczy, jeśli zawiera obiekt relacji), ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości do nazwy tabeli nadrzędnej.  
  
3.  Napisać kod, aby wypełnić dataset.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGrid, kontrolka — omówienie](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Wiązanie danych formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
