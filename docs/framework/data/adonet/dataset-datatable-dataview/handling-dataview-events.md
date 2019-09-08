---
title: Obsługa zdarzeń elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: c36c68b0375e7d03aac36de7d02b2c9579ea9316
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784589"
---
# <a name="handling-dataview-events"></a>Obsługa zdarzeń elementu DataView
Aby określić, czy <xref:System.Data.DataView.ListChanged> widok został zaktualizowany, można użyć zdarzenia. <xref:System.Data.DataView> Aktualizacje, które powodują wygenerowanie zdarzenia, obejmują dodawanie, usuwanie lub modyfikowanie wiersza w tabeli źródłowej; Dodawanie lub usuwanie kolumny do schematu tabeli bazowej; i zmiana relacji nadrzędnej lub podrzędnej. Zdarzenie **ListChanged** powiadamia również o tym, czy lista wyświetlanych wierszy została znacząco zmieniona z powodu zastosowania nowej kolejności sortowania lub filtru.  
  
 Zdarzenie **ListChanged** implementuje <xref:System.ComponentModel> delegata **ListChangedEventHandler** <xref:System.ComponentModel.ListChangedEventArgs> przestrzeni nazw i przyjmuje jako obiekt wejściowy. Można określić, jakiego typu zmiany wystąpiły przy użyciu <xref:System.ComponentModel.ListChangedType> wartości wyliczenia we właściwości **ListChangedType** obiektu **ListChangedEventArgs** . W przypadku zmian, które obejmują dodawanie, usuwanie lub przenoszenie wierszy, nowy indeks dodanego lub przeniesionego wiersza i poprzedni indeks usuniętego wiersza są dostępne za pomocą właściwości **NewIndex** obiektu **ListChangedEventArgs** . W przypadku przenoszonego wiersza poprzedni indeks przenoszonego wiersza można uzyskać za pomocą właściwości **OldIndex** obiektu **ListChangedEventArgs** .  
  
 Element **DataViewManager** udostępnia również zdarzenie **ListChanged** w celu powiadomienia użytkownika o dodaniu lub usunięciu tabeli lub wprowadzeniu zmiany do kolekcji **relacji** bazowego **zestawu danych**.  
  
 Poniższy przykład kodu pokazuje, jak dodać program obsługi zdarzeń **ListChanged** .  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [Elementy DataView](dataviews.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
