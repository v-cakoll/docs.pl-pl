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
# <a name="handling-dataset-events"></a><span data-ttu-id="27f45-102">Obsługa zdarzeń elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="27f45-102">Handling DataSet Events</span></span>
<span data-ttu-id="27f45-103">Obiekt zawiera trzy zdarzenia: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, i <xref:System.Data.DataSet.MergeFailed>. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="27f45-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="27f45-104">Zdarzenie MergeFailed</span><span class="sxs-lookup"><span data-stu-id="27f45-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="27f45-105">Najczęściej używane zdarzenie `DataSet` obiektu to `MergeFailed`, który jest wywoływany, `DataSet` gdy schemat scalonych obiektów jest w konflikcie.</span><span class="sxs-lookup"><span data-stu-id="27f45-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="27f45-106">Dzieje się tak, gdy element docelowy <xref:System.Data.DataRow> i źródło mają tę samą wartość klucza podstawowego <xref:System.Data.DataSet.EnforceConstraints%2A> i właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="27f45-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="27f45-107">Na przykład, jeśli kolumny klucza podstawowego Scalonej tabeli są takie same między tabelami w dwóch `DataSet` obiektach, zgłaszany jest wyjątek, `MergeFailed` a zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="27f45-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="27f45-108">`MergeFailed` <xref:System.Data.MergeFailedEventArgs.Conflict%2A> <xref:System.Data.MergeFailedEventArgs.Table%2A> Obiekt przesłany do zdarzenia ma właściwość, która identyfikuje konflikt w schemacie między tymi dwoma `DataSet` obiektami, i właściwość, która określa nazwę tabeli w konflikcie. <xref:System.Data.MergeFailedEventArgs></span><span class="sxs-lookup"><span data-stu-id="27f45-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="27f45-109">Poniższy fragment kodu pokazuje, jak dodać program obsługi zdarzeń dla `MergeFailed` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="27f45-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="27f45-110">Zainicjowane zdarzenie</span><span class="sxs-lookup"><span data-stu-id="27f45-110">The Initialized Event</span></span>  
 <span data-ttu-id="27f45-111">Zdarzenie <xref:System.Data.DataSet.Initialized> występuje, `DataSet` gdy Konstruktor inicjuje nowe wystąpienie obiektu `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="27f45-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="27f45-112"><xref:System.Data.DataSet.IsInitialized%2A> Właściwość zwraca `false`, jeśli `DataSet` zakończył inicjalizację; w `true` przeciwnym razie zwraca.</span><span class="sxs-lookup"><span data-stu-id="27f45-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="27f45-113">Metoda, która rozpoczyna inicjalizację `DataSet`, ustawia <xref:System.Data.DataSet.IsInitialized%2A> na `false`. <xref:System.Data.DataSet.BeginInit%2A></span><span class="sxs-lookup"><span data-stu-id="27f45-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="27f45-114">Metoda, która przerywa inicjalizację `DataSet`, ustawia ją na `true`. <xref:System.Data.DataSet.EndInit%2A></span><span class="sxs-lookup"><span data-stu-id="27f45-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="27f45-115">Te metody są używane przez środowisko projektowe programu Visual Studio do inicjowania `DataSet` , który jest używany przez inny składnik.</span><span class="sxs-lookup"><span data-stu-id="27f45-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="27f45-116">Nie są one często używane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="27f45-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="27f45-117">Usunięte zdarzenie</span><span class="sxs-lookup"><span data-stu-id="27f45-117">The Disposed Event</span></span>  
 <span data-ttu-id="27f45-118">`DataSet`pochodzi od <xref:System.ComponentModel.MarshalByValueComponent> klasy, która uwidacznia <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> zarówno metodę, jak i <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="27f45-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="27f45-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> Zdarzenie dodaje procedurę obsługi zdarzeń, która umożliwia nasłuchiwanie usuniętego zdarzenia w składniku.</span><span class="sxs-lookup"><span data-stu-id="27f45-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="27f45-120">Możesz użyć <xref:System.ComponentModel.MarshalByValueComponent.Disposed> zdarzenia `DataSet` , jeśli chcesz wykonać kod, gdy <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="27f45-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="27f45-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>Zwalnia zasoby używane przez <xref:System.ComponentModel.MarshalByValueComponent>program.</span><span class="sxs-lookup"><span data-stu-id="27f45-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27f45-122">Obiekty `DataSet` <xref:System.ComponentModel.MarshalByValueComponent> i `DataTable` dziedziczą z i obsługują interfejsna<xref:System.Runtime.Serialization.ISerializable> potrzeby komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="27f45-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="27f45-123">Są to jedyne ADO.NET obiekty, które można zdalnie.</span><span class="sxs-lookup"><span data-stu-id="27f45-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="27f45-124">Aby uzyskać więcej informacji, zobacz [komunikacja zdalna platformy .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="27f45-124">For more information, see [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="27f45-125">Aby uzyskać informacje o innych zdarzeniach dostępnych podczas pracy `DataSet`z usługą, zobacz [obsługiwanie zdarzeń DataTable](handling-datatable-events.md) i [Obsługa zdarzeń DataAdapter](../handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="27f45-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](handling-datatable-events.md) and [Handling DataAdapter Events](../handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f45-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27f45-126">See also</span></span>

- [<span data-ttu-id="27f45-127">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="27f45-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="27f45-128">[Sprawdzanie poprawności danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="27f45-128">[Validating Data](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="27f45-129">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="27f45-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="27f45-130">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="27f45-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
