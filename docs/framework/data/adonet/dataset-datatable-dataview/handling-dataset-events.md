---
title: Obsługa zdarzeń zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 486f38e2900eb85dbffbb4f9a9d0e6753267e32b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="handling-dataset-events"></a><span data-ttu-id="60238-102">Obsługa zdarzeń zestawu danych</span><span class="sxs-lookup"><span data-stu-id="60238-102">Handling DataSet Events</span></span>
<span data-ttu-id="60238-103"><xref:System.Data.DataSet> Obiektu zawiera trzy zdarzenia: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, i <xref:System.Data.DataSet.MergeFailed>.</span><span class="sxs-lookup"><span data-stu-id="60238-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="60238-104">Zdarzenie MergeFailed</span><span class="sxs-lookup"><span data-stu-id="60238-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="60238-105">Najczęściej używane zdarzenie `DataSet` obiekt jest `MergeFailed`, które jest wywoływane, gdy schemat `DataSet` obiektów scalane są w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="60238-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="60238-106">Ten błąd występuje podczas źródłowe i docelowe <xref:System.Data.DataRow> mieć tej samej wartości klucza podstawowego i <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="60238-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="60238-107">Na przykład, jeśli kolumn klucza podstawowego tabeli scalane są takie same, między tabelami w dwóch `DataSet` obiekty, jest zgłaszany wyjątek i `MergeFailed` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="60238-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="60238-108"><xref:System.Data.MergeFailedEventArgs> Obiekt przekazywany do `MergeFailed` zdarzeń ma <xref:System.Data.MergeFailedEventArgs.Conflict%2A> właściwość, która identyfikuje konflikt w schemacie między tymi dwoma `DataSet` obiektów, a <xref:System.Data.MergeFailedEventArgs.Table%2A> właściwość, która identyfikuje nazwę tabeli w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="60238-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="60238-109">Poniższy fragment kodu przedstawia sposób dodawania obsługi zdarzenia `MergeFailed` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="60238-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="60238-110">Zainicjowane wydarzenie</span><span class="sxs-lookup"><span data-stu-id="60238-110">The Initialized Event</span></span>  
 <span data-ttu-id="60238-111"><xref:System.Data.DataSet.Initialized> Po wystąpieniu zdarzenia `DataSet` Konstruktor inicjuje nowe wystąpienie klasy `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="60238-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="60238-112"><xref:System.Data.DataSet.IsInitialized%2A> Zwraca `true` Jeśli `DataSet` ukończono inicjalizacji; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="60238-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="60238-113"><xref:System.Data.DataSet.BeginInit%2A> — Metoda, która rozpoczyna inicjowanie `DataSet`, ustawia <xref:System.Data.DataSet.IsInitialized%2A> do `false`.</span><span class="sxs-lookup"><span data-stu-id="60238-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="60238-114"><xref:System.Data.DataSet.EndInit%2A> Metodę, która kończy się inicjowanie `DataSet`, ustawia ją na `true`.</span><span class="sxs-lookup"><span data-stu-id="60238-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="60238-115">Te metody są używane w środowisku projektowania programu Visual Studio można zainicjować `DataSet` który jest używany przez inny składnik.</span><span class="sxs-lookup"><span data-stu-id="60238-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="60238-116">Użytkownik nie będzie często używać ich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="60238-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="60238-117">Usunięte zdarzeń</span><span class="sxs-lookup"><span data-stu-id="60238-117">The Disposed Event</span></span>  
 <span data-ttu-id="60238-118">`DataSet` jest pochodną <xref:System.ComponentModel.MarshalByValueComponent> klasy, która ujawnia zarówno <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> — metoda i <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="60238-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="60238-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> Zdarzenie dodaje do nasłuchiwania na zlikwidowanym zdarzenie dla składnika obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="60238-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="60238-120">Można użyć <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzenie `DataSet` Jeśli chcesz wykonać kodu, gdy <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="60238-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="60238-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> zwalnia zasoby używane przez <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="60238-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60238-122">`DataSet` i `DataTable` obiekty dziedziczyć <xref:System.ComponentModel.MarshalByValueComponent> i obsługuje <xref:System.Runtime.Serialization.ISerializable> interfejs dla niego komunikację zdalną.</span><span class="sxs-lookup"><span data-stu-id="60238-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="60238-123">Są to jedyne obiekty ADO.NET, które może zostać wykonana zdalnie.</span><span class="sxs-lookup"><span data-stu-id="60238-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="60238-124">Aby uzyskać więcej informacji, zobacz [obiektów zdalnych](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span><span class="sxs-lookup"><span data-stu-id="60238-124">For more information, see [Remote Objects](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span></span>  
  
 <span data-ttu-id="60238-125">Aby uzyskać informacje na temat innych zdarzeń, które są dostępne podczas pracy z `DataSet`, zobacz [obsługi zdarzeń DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) i [obsługi zdarzeń element DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="60238-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) and [Handling DataAdapter Events](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60238-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60238-126">See Also</span></span>  
 [<span data-ttu-id="60238-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="60238-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="60238-128">Sprawdzanie poprawności danych</span><span class="sxs-lookup"><span data-stu-id="60238-128">Validating Data</span></span>](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [<span data-ttu-id="60238-129">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="60238-129">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="60238-130">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="60238-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
