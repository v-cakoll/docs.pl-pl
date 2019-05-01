---
title: 'Instrukcje: Tworzenie list wzorzec / szczegół za pomocą kontrolki DataGrid formularzy Windows Forms'
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
ms.openlocfilehash: 92b4a7d9513ce0ec9b7c02f57c23fa4267fb26ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052173"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>Instrukcje: tworzenie list wzorzec/szczegół za pomocą kontrolki DataGrid formularzy systemu Windows
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Jeśli Twoje <xref:System.Data.DataSet> zawiera serię powiązane tabele, możesz użyć dwóch <xref:System.Windows.Forms.DataGrid> formantów do wyświetlania danych w formacie wzorzec/szczegół. Jeden <xref:System.Windows.Forms.DataGrid> wyznaczony jako główny siatki, a drugi jest wyznaczony jako siatka szczegółów. Po wybraniu wpisu na liście głównej wszystkich wpisów powiązanych podrzędnej liście są wyświetlane szczegółowe informacje. Na przykład jeśli Twoja <xref:System.Data.DataSet> zawiera tabelę Klienci i powiązanej tabeli z zamówieniami, należy określić tabelę Klienci do głównej siatki i na tabeli Orders siatka szczegółów. Po wybraniu odbiorcy z siatki głównej wszystkich zamówień skojarzonych z klientem w tabeli zamówienia będzie wyświetlana w siatce szczegółów.  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>Aby programowo ustawić relacji wzorzec/szczegół  
  
1. Utworzyć dwa nowe <xref:System.Windows.Forms.DataGrid> kontroluje i ustawiać ich właściwości.  
  
2. Dodawanie tabel do zestawu danych.  
  
3. Zadeklaruj zmienną typu <xref:System.Data.DataRelation> do reprezentowania relacji, którą chcesz utworzyć.  
  
4. Utwórz wystąpienie relacji, określając nazwę relacji i określenie tabeli, kolumny i element, który będzie łączyć dwóch tabel.  
  
5. Dodawanie relacji z elementem <xref:System.Data.DataSet> obiektu <xref:System.Data.DataSet.Relations%2A> kolekcji.  
  
6. Użyj <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody <xref:System.Windows.Forms.DataGrid> każdego siatki, aby powiązać <xref:System.Data.DataSet>.  
  
     Poniższy przykład pokazuje, jak ustawić relacji wzorzec/szczegół tabel Klienci i zamówienia w wcześniej wygenerowany <xref:System.Data.DataSet> (`ds`).  
  
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
- [Instrukcje: Powiązywanie formantu DataGrid formularzy Windows ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
