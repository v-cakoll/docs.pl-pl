---
title: Obsługa zdarzeń elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b625fad846c4c6cf008843bff1f6b0eabe0e1de4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151107"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="70308-102">Obsługa zdarzeń elementu DataView</span><span class="sxs-lookup"><span data-stu-id="70308-102">Handling DataView Events</span></span>
<span data-ttu-id="70308-103">Można użyć <xref:System.Data.DataView.ListChanged> zdarzenia, <xref:System.Data.DataView> aby ustalić, czy widok został zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="70308-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="70308-104">Aktualizacje, które podnoszą zdarzenie obejmują dodawanie, usuwanie lub modyfikowanie wiersza w tabeli źródłowej; dodawanie lub usuwanie kolumny do schematu tabeli źródłowej; oraz zmiany relacji rodzica lub dziecka.</span><span class="sxs-lookup"><span data-stu-id="70308-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="70308-105">**Zdarzenie ListChanged** powiadamia również, jeśli lista przeglądanych wierszy uległa znacznej zmianie ze względu na zastosowanie nowej kolejności sortowania lub filtru.</span><span class="sxs-lookup"><span data-stu-id="70308-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="70308-106">**Zdarzenie ListChanged** implementuje **listChangedEventHandler** delegata obszaru <xref:System.ComponentModel> nazw i <xref:System.ComponentModel.ListChangedEventArgs> przyjmuje jako dane wejściowe obiektu.</span><span class="sxs-lookup"><span data-stu-id="70308-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="70308-107">Można określić, jaki typ zmiany <xref:System.ComponentModel.ListChangedType> wystąpił przy użyciu wartości wyliczenia we właściwości **ListChangedType** obiektu **ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="70308-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="70308-108">W przypadku zmian, które obejmują dodawanie, usuwanie lub przenoszenie wierszy, nowy indeks dodanego lub przeniesionego wiersza i poprzedniego indeksu usuniętego wiersza można uzyskać za pomocą właściwości **NewIndex** obiektu **ListChangedEventArgs.**</span><span class="sxs-lookup"><span data-stu-id="70308-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="70308-109">W przypadku przeniesiony wiersz, poprzedni indeks przeniesiony wiersz można uzyskać za pomocą **OldIndex** właściwości **ListChangedEventArgs** obiektu.</span><span class="sxs-lookup"><span data-stu-id="70308-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="70308-110">**DataViewManager** udostępnia również **ListChanged** zdarzenia, aby powiadomić, jeśli tabela została dodana lub usunięta, lub jeśli wprowadzono zmianę do **relacji** kolekcji podstawowej **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="70308-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="70308-111">Poniższy przykład kodu pokazuje, jak dodać program obsługi zdarzeń **ListChanged.**</span><span class="sxs-lookup"><span data-stu-id="70308-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70308-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70308-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="70308-113">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="70308-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="70308-114">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="70308-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
