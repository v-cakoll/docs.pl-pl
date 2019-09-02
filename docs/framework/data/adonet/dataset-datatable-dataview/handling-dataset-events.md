---
title: Obsługa zdarzeń elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 88f35d90f02b44b88f4bb7c6fac6a94a09afe81a
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204841"
---
# <a name="handling-dataset-events"></a>Obsługa zdarzeń elementu DataSet
Obiekt zawiera trzy zdarzenia: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, i <xref:System.Data.DataSet.MergeFailed>. <xref:System.Data.DataSet>  
  
## <a name="the-mergefailed-event"></a>Zdarzenie MergeFailed  
 Najczęściej używane zdarzenie `DataSet` obiektu to `MergeFailed`, który jest wywoływany, `DataSet` gdy schemat scalonych obiektów jest w konflikcie. Dzieje się tak, gdy element docelowy <xref:System.Data.DataRow> i źródło mają tę samą wartość klucza podstawowego <xref:System.Data.DataSet.EnforceConstraints%2A> i właściwość jest ustawiona na `true`. Na przykład, jeśli kolumny klucza podstawowego Scalonej tabeli są takie same między tabelami w dwóch `DataSet` obiektach, zgłaszany jest wyjątek, `MergeFailed` a zdarzenie jest zgłaszane. `MergeFailed` <xref:System.Data.MergeFailedEventArgs.Conflict%2A> <xref:System.Data.MergeFailedEventArgs.Table%2A> Obiekt przesłany do zdarzenia ma właściwość, która identyfikuje konflikt w schemacie między tymi dwoma `DataSet` obiektami, i właściwość, która określa nazwę tabeli w konflikcie. <xref:System.Data.MergeFailedEventArgs>  
  
 Poniższy fragment kodu pokazuje, jak dodać program obsługi zdarzeń dla `MergeFailed` zdarzenia.  
  
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
  
## <a name="the-initialized-event"></a>Zainicjowane zdarzenie  
 Zdarzenie <xref:System.Data.DataSet.Initialized> występuje, `DataSet` gdy Konstruktor inicjuje nowe wystąpienie obiektu `DataSet`.  
  
 <xref:System.Data.DataSet.IsInitialized%2A> Właściwość zwraca `false`, jeśli `DataSet` zakończył inicjalizację; w `true` przeciwnym razie zwraca. Metoda, która rozpoczyna inicjalizację `DataSet`, ustawia <xref:System.Data.DataSet.IsInitialized%2A> na `false`. <xref:System.Data.DataSet.BeginInit%2A> Metoda, która przerywa inicjalizację `DataSet`, ustawia ją na `true`. <xref:System.Data.DataSet.EndInit%2A> Te metody są używane przez środowisko projektowe programu Visual Studio do inicjowania `DataSet` , który jest używany przez inny składnik. Nie są one często używane w kodzie.  
  
## <a name="the-disposed-event"></a>Usunięte zdarzenie  
 `DataSet`pochodzi od <xref:System.ComponentModel.MarshalByValueComponent> klasy, która uwidacznia <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> zarówno metodę, jak i <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzenie. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Zdarzenie dodaje procedurę obsługi zdarzeń, która umożliwia nasłuchiwanie usuniętego zdarzenia w składniku. Możesz użyć <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzenia `DataSet` , jeśli chcesz wykonać kod, gdy <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> wywoływana jest metoda. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>Zwalnia zasoby używane przez <xref:System.ComponentModel.MarshalByValueComponent>program.  
  
> [!NOTE]
> Obiekty `DataSet` <xref:System.ComponentModel.MarshalByValueComponent> i `DataTable` dziedziczą z i obsługują interfejsna<xref:System.Runtime.Serialization.ISerializable> potrzeby komunikacji zdalnej. Są to jedyne ADO.NET obiekty, które można zdalnie. Aby uzyskać więcej informacji, zobacz [komunikacja zdalna platformy .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).  
  
 Aby uzyskać informacje o innych zdarzeniach dostępnych podczas pracy `DataSet`z usługą, zobacz [obsługiwanie zdarzeń DataTable](handling-datatable-events.md) i [Obsługa zdarzeń DataAdapter](../handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](index.md)
- [Sprawdzanie poprawności danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [Pobieranie i modyfikowanie danych ADO.NET](../retrieving-and-modifying-data.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
