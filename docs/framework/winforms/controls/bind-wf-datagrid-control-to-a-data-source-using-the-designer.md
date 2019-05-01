---
title: 'Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant'
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
ms.openlocfilehash: fe54c650e1d19f36d681053c7da47e12527c5827
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011759"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Formularze Windows <xref:System.Windows.Forms.DataGrid> kontroli jest specjalnie przeznaczona do wyświetlania informacji ze źródła danych. Powiązywanie formantu w czasie projektowania, ustawiając <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości, lub w czasie wykonywania przez wywołanie metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody. Choć można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła są zestawy danych i widokami danych.  
  
 Jeśli źródło danych jest dostępna w czasie projektowania — na przykład, jeśli formularz zawiera wystąpienie zestawu danych lub widoku danych — Siatka można powiązać ze źródłem danych w czasie projektowania. Możesz przeglądać dane jak będzie wyglądał w siatce.  
  
 Możesz również powiązać siatki programowo, w czasie wykonywania. Jest to przydatne, jeśli chcesz ustawić źródło danych, w oparciu o informacje, które otrzymujesz w czasie wykonywania. Na przykład aplikacja może zezwolić użytkownikom na Określ nazwę tabeli, aby wyświetlić. Konieczne jest również w sytuacji, gdy źródło danych nie istnieje w czasie projektowania. W tym źródeł danych, takich jak tablice, kolekcje, nietypizowanych zbiorów danych oraz czytniki danych.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGrid> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md). W programie Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> formantu nie znajduje się w **przybornika** domyślnie. Aby uzyskać informacje dotyczące dodawania go, zobacz [jak: Dodaj elementy do przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)). Ponadto w programie Visual Studio 2005, można za pomocą **źródeł danych** okna dla powiązania danych w czasie projektowania. Aby uzyskać więcej informacji, zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Aby powiązanie danych kontrolki DataGrid z pojedynczej tabeli w Projektancie  
  
1. Ustaw dla formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.  
  
2. Jeśli źródło danych zestawu danych, ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwość na nazwę tabeli dla powiązania.  
  
3. W przypadku zestawu danych lub widoku danych, na podstawie tabeli zestawu danych źródła danych należy dodać kod do formularza, aby wypełnić dataset.  
  
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
  
4. (Opcjonalnie) Dodaj style odpowiedniej tabeli i kolumn do siatki.  
  
     Jeśli nie ma żadnych style tabeli, tabeli, zostanie wyświetlony, ale z minimalnym formatowania i widoczne dla wszystkich kolumn.  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Aby powiązanie danych kontrolki DataGrid z wielu tabel w zestawie danych w Projektancie  
  
1. Ustaw dla formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> właściwości do obiektu zawierającego elementy danych, aby powiązać.  
  
2. Jeśli zestaw danych zawiera tabele powiązane (to znaczy, jeśli zawiera on obiektu relacji), ustaw <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwość na nazwę tabeli nadrzędnej.  
  
3. Pisz kod, aby wypełnić dataset.  
  
## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka — omówienie](datagrid-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
