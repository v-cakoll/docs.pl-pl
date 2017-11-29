---
title: "Obsługa zdarzeń zestawu danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cfe9d9c9f1442d3577772dde1ff33a7807394019
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="handling-dataset-events"></a>Obsługa zdarzeń zestawu danych
<xref:System.Data.DataSet> Obiektu zawiera trzy zdarzenia: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, i <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>Zdarzenie MergeFailed  
 Najczęściej używane zdarzenie `DataSet` obiekt jest `MergeFailed`, które jest wywoływane, gdy schemat `DataSet` obiektów scalane są w konflikcie. Ten błąd występuje podczas źródłowe i docelowe <xref:System.Data.DataRow> mieć tej samej wartości klucza podstawowego i <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość jest ustawiona na `true`. Na przykład, jeśli kolumn klucza podstawowego tabeli scalane są takie same, między tabelami w dwóch `DataSet` obiekty, jest zgłaszany wyjątek i `MergeFailed` zdarzenia. <xref:System.Data.MergeFailedEventArgs> Obiekt przekazywany do `MergeFailed` zdarzeń ma <xref:System.Data.MergeFailedEventArgs.Conflict%2A> właściwość, która identyfikuje konflikt w schemacie między tymi dwoma `DataSet` obiektów, a <xref:System.Data.MergeFailedEventArgs.Table%2A> właściwość, która identyfikuje nazwę tabeli w konflikcie.  
  
 Poniższy fragment kodu przedstawia sposób dodawania obsługi zdarzenia `MergeFailed` zdarzeń.  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a>Zainicjowane wydarzenie  
 <xref:System.Data.DataSet.Initialized> Po wystąpieniu zdarzenia `DataSet` Konstruktor inicjuje nowe wystąpienie klasy `DataSet`.  
  
 <xref:System.Data.DataSet.IsInitialized%2A> Zwraca `true` Jeśli `DataSet` ukończono inicjalizacji; w przeciwnym razie zwraca `false`. <xref:System.Data.DataSet.BeginInit%2A> — Metoda, która rozpoczyna inicjowanie `DataSet`, ustawia <xref:System.Data.DataSet.IsInitialized%2A> do `false`. <xref:System.Data.DataSet.EndInit%2A> Metodę, która kończy się inicjowanie `DataSet`, ustawia ją na `true`. Te metody są używane przez [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] środowisku projektowania zainicjować `DataSet` który jest używany przez inny składnik. Użytkownik nie będzie często używać ich w kodzie.  
  
## <a name="the-disposed-event"></a>Usunięte zdarzeń  
 `DataSet`jest pochodną <xref:System.ComponentModel.MarshalByValueComponent> klasy, która ujawnia zarówno <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> — metoda i <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzeń. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Zdarzenie dodaje do nasłuchiwania na zlikwidowanym zdarzenie dla składnika obsługi zdarzeń. Można użyć <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzenie `DataSet` Jeśli chcesz wykonać kodu, gdy <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda jest wywoływana. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>zwalnia zasoby używane przez <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  `DataSet` i `DataTable` obiekty dziedziczyć <xref:System.ComponentModel.MarshalByValueComponent> i obsługuje <xref:System.Runtime.Serialization.ISerializable> interfejs dla niego komunikację zdalną. Są to jedyne obiekty ADO.NET, które może zostać wykonana zdalnie. Aby uzyskać więcej informacji, zobacz [obiektów zdalnych](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58).  
  
 Aby uzyskać informacje na temat innych zdarzeń, które są dostępne podczas pracy z `DataSet`, zobacz [obsługi zdarzeń DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) i [obsługi zdarzeń element DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zbiory danych, DataTables i DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [Trwa pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
