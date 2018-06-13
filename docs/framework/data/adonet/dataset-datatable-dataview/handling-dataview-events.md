---
title: Obsługa zdarzeń widoku danych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 9e67aef2a39a04adfdcc036c008aa80c9151c14b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762562"
---
# <a name="handling-dataview-events"></a>Obsługa zdarzeń widoku danych.
Można użyć <xref:System.Data.DataView.ListChanged> zdarzenie <xref:System.Data.DataView> ustalenie, jeśli widok został zaktualizowany. Aktualizacje, które uruchamiają zdarzenia obejmują dodawanie, usuwanie lub modyfikowanie wiersza w tabeli podstawowej; dodanie lub usunięcie kolumny tabeli podstawowej; w schemacie i zmian w nadrzędnym lub podrzędnym relacji. **ListChanged** zdarzeń również powiadamia użytkownika, jeśli lista wierszy jest wyświetlana zmienił znacząco z powodu stosowania nowych kolejności sortowania ani filtru.  
  
 **ListChanged** implementuje zdarzeń **ListChangedEventHandler** delegować z <xref:System.ComponentModel> przestrzeni nazw i przyjmuje jako dane wejściowe <xref:System.ComponentModel.ListChangedEventArgs> obiektu. Można określić, jakiego rodzaju zmiany wystąpił przy użyciu <xref:System.ComponentModel.ListChangedType> wartość wyliczenia w **ListChangedType** właściwość **ListChangedEventArgs** obiektu. Zmiany, które obejmują dodawanie, usuwanie lub przenoszenie wierszy, nowy indeks wiersza dodany lub przenoszenia i poprzedniego indeksu usuniętym wierszu są dostępne przy użyciu **NewIndex** właściwość **ListChangedEventArgs** obiektu. W przypadku przeniesionego wiersza poprzedniego indeksu przeniesionego wiersza jest możliwy za pomocą **OldIndex** właściwość **ListChangedEventArgs** obiektu.  
  
 **DataViewManager** udostępnia również **ListChanged** zdarzeń informujący, czy dodano lub usunięto tabelę, czy wprowadzono zmiany do **relacji** kolekcji bazowy **zestawu danych**.  
  
 W poniższym przykładzie przedstawiono sposób dodawania **ListChanged** obsługi zdarzeń.  
  
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
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
