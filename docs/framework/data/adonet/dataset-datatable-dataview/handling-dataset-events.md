---
title: Obsługa zdarzeń elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: ff684adcb4e23b91b3e59476299d277c90c22c51
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857774"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="da3fb-102">Obsługa zdarzeń elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="da3fb-102">Handling DataSet Events</span></span>
<span data-ttu-id="da3fb-103"><xref:System.Data.DataSet> Obiekt zawiera trzy zdarzenia: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, i <xref:System.Data.DataSet.MergeFailed>.</span><span class="sxs-lookup"><span data-stu-id="da3fb-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="da3fb-104">Zdarzenie MergeFailed</span><span class="sxs-lookup"><span data-stu-id="da3fb-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="da3fb-105">Najczęściej stosowane zdarzenia `DataSet` obiekt jest `MergeFailed`, które jest wywoływane, gdy schemat `DataSet` obiektów scalane są w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="da3fb-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="da3fb-106">Ten błąd występuje podczas źródłowe i docelowe <xref:System.Data.DataRow> mieć tej samej wartości klucza podstawowego, a <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="da3fb-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="da3fb-107">Na przykład, jeśli scalana kolumny klucza podstawowego w tabeli są takie same, między tabelami w dwóch `DataSet` obiektów, zostanie zgłoszony wyjątek i `MergeFailed` zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="da3fb-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="da3fb-108"><xref:System.Data.MergeFailedEventArgs> Obiekt przekazany do `MergeFailed` zdarzenia mają <xref:System.Data.MergeFailedEventArgs.Conflict%2A> właściwość, która identyfikuje konfliktów w schemacie między tymi dwoma `DataSet` obiektów, a <xref:System.Data.MergeFailedEventArgs.Table%2A> właściwości, który identyfikuje nazwę tabeli w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="da3fb-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="da3fb-109">Poniższy fragment kodu pokazuje, jak dodać obsługę zdarzeń dla `MergeFailed` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="da3fb-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="da3fb-110">Zainicjowane wydarzenie</span><span class="sxs-lookup"><span data-stu-id="da3fb-110">The Initialized Event</span></span>  
 <span data-ttu-id="da3fb-111"><xref:System.Data.DataSet.Initialized> Zdarzenie występuje po `DataSet` Konstruktor inicjuje nowe wystąpienie klasy `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="da3fb-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="da3fb-112"><xref:System.Data.DataSet.IsInitialized%2A> Właściwość zwraca `true` Jeśli `DataSet` zakończeniu inicjalizacji; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="da3fb-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="da3fb-113"><xref:System.Data.DataSet.BeginInit%2A> Metody, która rozpoczyna się inicjowanie `DataSet`, ustawia <xref:System.Data.DataSet.IsInitialized%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="da3fb-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="da3fb-114"><xref:System.Data.DataSet.EndInit%2A> Metody, która kończy się inicjowanie `DataSet`, ustawia ją na `true`.</span><span class="sxs-lookup"><span data-stu-id="da3fb-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="da3fb-115">Te metody są używane w środowisku projektowym programu Visual Studio można zainicjować `DataSet` który jest używany przez inny składnik.</span><span class="sxs-lookup"><span data-stu-id="da3fb-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="da3fb-116">Możesz nie będzie najczęściej używać ich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="da3fb-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="da3fb-117">Zdarzenie usunięte</span><span class="sxs-lookup"><span data-stu-id="da3fb-117">The Disposed Event</span></span>  
 <span data-ttu-id="da3fb-118">`DataSet` jest tworzony na podstawie <xref:System.ComponentModel.MarshalByValueComponent> klasy, która ujawnia zarówno <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metody i <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="da3fb-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="da3fb-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> Zdarzenie dodaje procedurę obsługi zdarzeń do nasłuchiwania na zdarzenie usunięte w składniku.</span><span class="sxs-lookup"><span data-stu-id="da3fb-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="da3fb-120">Możesz użyć <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzenia `DataSet` Jeśli chcesz wykonać kod, gdy <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="da3fb-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="da3fb-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> zwalnia zasoby używane przez <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="da3fb-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da3fb-122">`DataSet` i `DataTable` obiekty dziedziczyć <xref:System.ComponentModel.MarshalByValueComponent> i obsługa techniczna <xref:System.Runtime.Serialization.ISerializable> interfejs do komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="da3fb-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="da3fb-123">Są to jedyne obiekty ADO.NET, które mogą być w węzłach.</span><span class="sxs-lookup"><span data-stu-id="da3fb-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="da3fb-124">Aby uzyskać więcej informacji, zobacz [obiekty zdalne](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span><span class="sxs-lookup"><span data-stu-id="da3fb-124">For more information, see [Remote Objects](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span></span>  
  
 <span data-ttu-id="da3fb-125">Aby uzyskać informacje na temat innych zdarzeń, które są dostępne w przypadku pracy z `DataSet`, zobacz [Obsługa zdarzeń elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) i [Obsługa zdarzeń elementu DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="da3fb-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) and [Handling DataAdapter Events](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da3fb-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da3fb-126">See Also</span></span>  
 [<span data-ttu-id="da3fb-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="da3fb-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="da3fb-128">Sprawdzanie poprawności danych</span><span class="sxs-lookup"><span data-stu-id="da3fb-128">Validating Data</span></span>](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [<span data-ttu-id="da3fb-129">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="da3fb-129">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="da3fb-130">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="da3fb-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
