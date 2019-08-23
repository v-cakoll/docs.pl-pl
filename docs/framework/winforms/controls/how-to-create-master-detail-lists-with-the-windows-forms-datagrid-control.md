---
title: 'Instrukcje: Tworzenie list wzorzec-szczegół za pomocą kontrolki DataGrid Windows Forms'
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
ms.openlocfilehash: f0fd95cf0cd66e9a5105c0b8ff77d8c536a5822d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914765"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Instrukcje: tworzenie list wzorzec/szczegół za pomocą kontrolki DataGrid formularzy systemu Windows
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Jeśli zawiera serię powiązanych tabel, można użyć dwóch <xref:System.Windows.Forms.DataGrid> kontrolek do wyświetlania danych w formacie wzorzec/szczegóły. <xref:System.Data.DataSet> <xref:System.Windows.Forms.DataGrid> Wyznaczono ją jako siatkę główną, a druga wyznaczono jako siatkę szczegółów. Po wybraniu wpisu na liście głównej wszystkie powiązane wpisy podrzędne zostaną wyświetlone na liście szczegóły. Na przykład, jeśli <xref:System.Data.DataSet> zawiera tabelę Customers i powiązanej tabeli Orders, należy określić tabelę Customers jako siatkę główną oraz tabelę Orders, która będzie siatką szczegółów. Po wybraniu klienta z siatki głównej wszystkie zamówienia powiązane z tym klientem w tabeli Orders będą wyświetlane w siatce szczegółów.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Aby programowo ustawić relację wzorzec/szczegóły  
  
1. Utwórz dwie nowe <xref:System.Windows.Forms.DataGrid> kontrolki i ustaw ich właściwości.  
  
2. Dodaj tabele do zestawu danych.  
  
3. Zadeklaruj zmienną typu <xref:System.Data.DataRelation> reprezentującą relację, którą chcesz utworzyć.  
  
4. Utwórz wystąpienie relacji przez określenie nazwy relacji i określenie tabeli, kolumny i elementu, który będzie łączyć dwie tabele.  
  
5. Dodaj relację do <xref:System.Data.DataSet> <xref:System.Data.DataSet.Relations%2A> kolekcji obiektów.  
  
6. Użyj metody, <xref:System.Windows.Forms.DataGrid> aby powiązać wszystkie siatki z <xref:System.Data.DataSet>. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>  
  
     Poniższy przykład pokazuje, jak ustawić relację wzorzec/szczegóły między tabelami Customers i Orders w wcześniej <xref:System.Data.DataSet> wygenerowanym`ds`().  
  
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
- [Instrukcje: Powiązywanie kontrolki DataGrid Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
