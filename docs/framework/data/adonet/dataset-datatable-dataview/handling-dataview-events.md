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
# <a name="handling-dataview-events"></a>Obsługa zdarzeń elementu DataView
Można użyć <xref:System.Data.DataView.ListChanged> zdarzenia, <xref:System.Data.DataView> aby ustalić, czy widok został zaktualizowany. Aktualizacje, które podnoszą zdarzenie obejmują dodawanie, usuwanie lub modyfikowanie wiersza w tabeli źródłowej; dodawanie lub usuwanie kolumny do schematu tabeli źródłowej; oraz zmiany relacji rodzica lub dziecka. **Zdarzenie ListChanged** powiadamia również, jeśli lista przeglądanych wierszy uległa znacznej zmianie ze względu na zastosowanie nowej kolejności sortowania lub filtru.  
  
 **Zdarzenie ListChanged** implementuje **listChangedEventHandler** delegata obszaru <xref:System.ComponentModel> nazw i <xref:System.ComponentModel.ListChangedEventArgs> przyjmuje jako dane wejściowe obiektu. Można określić, jaki typ zmiany <xref:System.ComponentModel.ListChangedType> wystąpił przy użyciu wartości wyliczenia we właściwości **ListChangedType** obiektu **ListChangedEventArgs.** W przypadku zmian, które obejmują dodawanie, usuwanie lub przenoszenie wierszy, nowy indeks dodanego lub przeniesionego wiersza i poprzedniego indeksu usuniętego wiersza można uzyskać za pomocą właściwości **NewIndex** obiektu **ListChangedEventArgs.** W przypadku przeniesiony wiersz, poprzedni indeks przeniesiony wiersz można uzyskać za pomocą **OldIndex** właściwości **ListChangedEventArgs** obiektu.  
  
 **DataViewManager** udostępnia również **ListChanged** zdarzenia, aby powiadomić, jeśli tabela została dodana lub usunięta, lub jeśli wprowadzono zmianę do **relacji** kolekcji podstawowej **DataSet**.  
  
 Poniższy przykład kodu pokazuje, jak dodać program obsługi zdarzeń **ListChanged.**  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [Elementy DataView](dataviews.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
