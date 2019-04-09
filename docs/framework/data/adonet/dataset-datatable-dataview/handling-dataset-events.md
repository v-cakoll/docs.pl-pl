---
title: Obsługa zdarzeń elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 5e1de3effcae5700aa25f5dbb84f2dec3a0b20f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195289"
---
# <a name="handling-dataset-events"></a>Obsługa zdarzeń elementu DataSet
<xref:System.Data.DataSet> Obiekt zawiera trzy zdarzenia: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, i <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>Zdarzenie MergeFailed  
 Najczęściej stosowane zdarzenia `DataSet` obiekt jest `MergeFailed`, które jest wywoływane, gdy schemat `DataSet` obiektów scalane są w konflikcie. Ten błąd występuje podczas źródłowe i docelowe <xref:System.Data.DataRow> mieć tej samej wartości klucza podstawowego, a <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość jest ustawiona na `true`. Na przykład, jeśli scalana kolumny klucza podstawowego w tabeli są takie same, między tabelami w dwóch `DataSet` obiektów, zostanie zgłoszony wyjątek i `MergeFailed` zdarzenie jest wywoływane. <xref:System.Data.MergeFailedEventArgs> Obiekt przekazany do `MergeFailed` zdarzenia mają <xref:System.Data.MergeFailedEventArgs.Conflict%2A> właściwość, która identyfikuje konfliktów w schemacie między tymi dwoma `DataSet` obiektów, a <xref:System.Data.MergeFailedEventArgs.Table%2A> właściwości, który identyfikuje nazwę tabeli w konflikcie.  
  
 Poniższy fragment kodu pokazuje, jak dodać obsługę zdarzeń dla `MergeFailed` zdarzeń.  
  
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
 <xref:System.Data.DataSet.Initialized> Zdarzenie występuje po `DataSet` Konstruktor inicjuje nowe wystąpienie klasy `DataSet`.  
  
 <xref:System.Data.DataSet.IsInitialized%2A> Właściwość zwraca `true` Jeśli `DataSet` zakończeniu inicjalizacji; w przeciwnym razie zwraca `false`. <xref:System.Data.DataSet.BeginInit%2A> Metody, która rozpoczyna się inicjowanie `DataSet`, ustawia <xref:System.Data.DataSet.IsInitialized%2A> do `false`. <xref:System.Data.DataSet.EndInit%2A> Metody, która kończy się inicjowanie `DataSet`, ustawia ją na `true`. Te metody są używane w środowisku projektowym programu Visual Studio można zainicjować `DataSet` który jest używany przez inny składnik. Możesz nie będzie najczęściej używać ich w kodzie.  
  
## <a name="the-disposed-event"></a>Zdarzenie usunięte  
 `DataSet` jest tworzony na podstawie <xref:System.ComponentModel.MarshalByValueComponent> klasy, która ujawnia zarówno <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metody i <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzeń. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Zdarzenie dodaje procedurę obsługi zdarzeń do nasłuchiwania na zdarzenie usunięte w składniku. Możesz użyć <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzenia `DataSet` Jeśli chcesz wykonać kod, gdy <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda jest wywoływana. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> Zwalnia zasoby używane przez <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  `DataSet` i `DataTable` obiekty dziedziczyć <xref:System.ComponentModel.MarshalByValueComponent> i obsługa techniczna <xref:System.Runtime.Serialization.ISerializable> interfejs do komunikacji zdalnej. Są to jedyne obiekty ADO.NET, które mogą być w węzłach. Aby uzyskać więcej informacji, zobacz [wywołaniem funkcji zdalnych .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).  
  
 Aby uzyskać informacje na temat innych zdarzeń, które są dostępne w przypadku pracy z `DataSet`, zobacz [Obsługa zdarzeń elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) i [Obsługa zdarzeń elementu DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Sprawdzanie poprawności danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
