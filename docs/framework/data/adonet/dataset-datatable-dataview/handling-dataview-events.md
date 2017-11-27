---
title: "Obsługa zdarzeń widoku danych."
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
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2abade8bbbf5ab8a9d2cf146271e89703ec34cb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="handling-dataview-events"></a><span data-ttu-id="27b0d-102">Obsługa zdarzeń widoku danych.</span><span class="sxs-lookup"><span data-stu-id="27b0d-102">Handling DataView Events</span></span>
<span data-ttu-id="27b0d-103">Można użyć <xref:System.Data.DataView.ListChanged> zdarzenie <xref:System.Data.DataView> ustalenie, jeśli widok został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="27b0d-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="27b0d-104">Aktualizacje, które uruchamiają zdarzenia obejmują dodawanie, usuwanie lub modyfikowanie wiersza w tabeli podstawowej; dodanie lub usunięcie kolumny tabeli podstawowej; w schemacie i zmian w nadrzędnym lub podrzędnym relacji.</span><span class="sxs-lookup"><span data-stu-id="27b0d-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="27b0d-105">**ListChanged** zdarzeń również powiadamia użytkownika, jeśli lista wierszy jest wyświetlana zmienił znacząco z powodu stosowania nowych kolejności sortowania ani filtru.</span><span class="sxs-lookup"><span data-stu-id="27b0d-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="27b0d-106">**ListChanged** implementuje zdarzeń **ListChangedEventHandler** delegować z <xref:System.ComponentModel> przestrzeni nazw i przyjmuje jako dane wejściowe <xref:System.ComponentModel.ListChangedEventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="27b0d-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="27b0d-107">Można określić, jakiego rodzaju zmiany wystąpił przy użyciu <xref:System.ComponentModel.ListChangedType> wartość wyliczenia w **ListChangedType** właściwość **ListChangedEventArgs** obiektu.</span><span class="sxs-lookup"><span data-stu-id="27b0d-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="27b0d-108">Zmiany, które obejmują dodawanie, usuwanie lub przenoszenie wierszy, nowy indeks wiersza dodany lub przenoszenia i poprzedniego indeksu usuniętym wierszu są dostępne przy użyciu **NewIndex** właściwość **ListChangedEventArgs** obiektu.</span><span class="sxs-lookup"><span data-stu-id="27b0d-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="27b0d-109">W przypadku przeniesionego wiersza poprzedniego indeksu przeniesionego wiersza jest możliwy za pomocą **OldIndex** właściwość **ListChangedEventArgs** obiektu.</span><span class="sxs-lookup"><span data-stu-id="27b0d-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="27b0d-110">**DataViewManager** udostępnia również **ListChanged** zdarzeń informujący, czy dodano lub usunięto tabelę, czy wprowadzono zmiany do **relacji** kolekcji bazowy **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="27b0d-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="27b0d-111">W poniższym przykładzie przedstawiono sposób dodawania **ListChanged** obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="27b0d-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new   
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,   
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="27b0d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27b0d-112">See Also</span></span>  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [<span data-ttu-id="27b0d-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="27b0d-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="27b0d-114">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="27b0d-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
