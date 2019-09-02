---
title: Obsługa zdarzeń elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b3a1077bff9bf457b4aef0b05357d4a9260f8973
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204823"
---
# <a name="handling-dataview-events"></a>Obsługa zdarzeń elementu DataView
Aby określić, czy <xref:System.Data.DataView.ListChanged> widok został zaktualizowany, można użyć zdarzenia. <xref:System.Data.DataView> Aktualizacje, które powodują wygenerowanie zdarzenia, obejmują dodawanie, usuwanie lub modyfikowanie wiersza w tabeli źródłowej; Dodawanie lub usuwanie kolumny do schematu tabeli bazowej; i zmiana relacji nadrzędnej lub podrzędnej. Zdarzenie **ListChanged** powiadamia również o tym, czy lista wyświetlanych wierszy została znacząco zmieniona z powodu zastosowania nowej kolejności sortowania lub filtru.  
  
 Zdarzenie **ListChanged** implementuje <xref:System.ComponentModel> delegata **ListChangedEventHandler** <xref:System.ComponentModel.ListChangedEventArgs> przestrzeni nazw i przyjmuje jako obiekt wejściowy. Można określić, jakiego typu zmiany wystąpiły przy użyciu <xref:System.ComponentModel.ListChangedType> wartości wyliczenia we właściwości **ListChangedType** obiektu **ListChangedEventArgs** . W przypadku zmian, które obejmują dodawanie, usuwanie lub przenoszenie wierszy, nowy indeks dodanego lub przeniesionego wiersza i poprzedni indeks usuniętego wiersza są dostępne za pomocą właściwości **NewIndex** obiektu **ListChangedEventArgs** . W przypadku przenoszonego wiersza poprzedni indeks przenoszonego wiersza można uzyskać za pomocą właściwości **OldIndex** obiektu **ListChangedEventArgs** .  
  
 Element DataViewManager udostępnia również zdarzenie **ListChanged** w celu powiadomienia użytkownika o dodaniu lub usunięciu tabeli lub wprowadzeniu zmiany do kolekcji **relacji** bazowego **zestawu danych**.  
  
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
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
