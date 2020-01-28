---
title: Tworzenie list wzorzec-szczegóły przy użyciu kontrolki DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: e8ab63d52d97a8a6e6f60da741186e3937350e1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730982"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Porady: tworzenie list wzorzec/szczegół za pomocą formantu DataGrid formularzy systemu Windows
> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Jeśli <xref:System.Data.DataSet> zawiera serię powiązanych tabel, można użyć dwóch kontrolek <xref:System.Windows.Forms.DataGrid> do wyświetlania danych w formacie głównym/szczegółowym. Jeden <xref:System.Windows.Forms.DataGrid> wyznaczono jako siatkę główną, a druga jest oznaczona jako siatka szczegółów. Po wybraniu wpisu na liście głównej wszystkie powiązane wpisy podrzędne zostaną wyświetlone na liście szczegóły. Na przykład jeśli <xref:System.Data.DataSet> zawiera tabelę Customers i powiązanej tabeli Orders, należy określić tabelę Customers jako siatkę główną oraz tabelę Orders, która będzie siatką szczegółów. Po wybraniu klienta z siatki głównej wszystkie zamówienia powiązane z tym klientem w tabeli Orders będą wyświetlane w siatce szczegółów.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Aby programowo ustawić relację wzorzec/szczegóły  
  
1. Utwórz dwie nowe <xref:System.Windows.Forms.DataGrid> kontrolki i ustaw ich właściwości.  
  
2. Dodaj tabele do zestawu danych.  
  
3. Zadeklaruj zmienną typu <xref:System.Data.DataRelation> reprezentującą relację, którą chcesz utworzyć.  
  
4. Utwórz wystąpienie relacji przez określenie nazwy relacji i określenie tabeli, kolumny i elementu, który będzie łączyć dwie tabele.  
  
5. Dodaj relację do kolekcji <xref:System.Data.DataSet.Relations%2A> obiektu <xref:System.Data.DataSet>.  
  
6. Użyj metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> <xref:System.Windows.Forms.DataGrid>, aby powiązać wszystkie siatki z <xref:System.Data.DataSet>.  
  
     Poniższy przykład pokazuje, jak ustawić relację wzorzec/szczegóły między tabelami Customers i Orders w wcześniej wygenerowanym <xref:System.Data.DataSet> (`ds`).  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [DataGrid, kontrolka — omówienie](datagrid-control-overview-windows-forms.md)
- [Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
