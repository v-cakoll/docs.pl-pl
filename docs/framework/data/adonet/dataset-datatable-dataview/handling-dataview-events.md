---
title: Obsługa zdarzeń elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 6c2e554b7e6bde3e82190f70723f272b0d39a18a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152415"
---
# <a name="handling-dataview-events"></a>Obsługa zdarzeń elementu DataView
Możesz użyć <xref:System.Data.DataView.ListChanged> zdarzenia <xref:System.Data.DataView> do określenia, czy widok zostały zaktualizowane. Aktualizacje, które zgłaszają zdarzenia obejmują dodawanie, usuwanie lub modyfikowanie wiersza w tabeli podstawowej; Dodawanie lub usuwanie kolumn do schematu tabeli podstawowej; i zmiany w relacji nadrzędnej lub podrzędnej. **ListChanged** zdarzeń również powiadamia użytkownika, jeśli lista wierszy wyświetlanych zmienił się znacznie ze względu na stosowanie nowych kolejność sortowania lub filtrowania.  
  
 **ListChanged** implementuje zdarzeń **ListChangedEventHandler** delegowanie z <xref:System.ComponentModel> przestrzeni nazw i przyjmuje jako dane wejściowe <xref:System.ComponentModel.ListChangedEventArgs> obiektu. Można określić, jakiego rodzaju zmian wystąpił, za pomocą <xref:System.ComponentModel.ListChangedType> wartości wyliczenia w **ListChangedType** właściwość **ListChangedEventArgs** obiektu. Do zmiany, które obejmują dodawanie, usuwanie lub przenoszenie wierszy, nowy indeks wiersza dodano lub które zostały przeniesione i poprzedniej indeks wiersza usuniętego są dostępne przy użyciu **NewIndex** właściwość **ListChangedEventArgs** obiektu. W przypadku przeniesione wiersz poprzedniego indeks wiersza przeniesionych można uzyskać dostęp za pomocą **OldIndex** właściwość **ListChangedEventArgs** obiektu.  
  
 **DataViewManager** udostępnia również **ListChanged** zdarzeń, aby otrzymywać powiadomienia, jeśli dodano lub usunięto tabelę lub zmiana została wprowadzona do **relacji** kolekcji bazowy **zestawu danych**.  
  
 W poniższym przykładzie kodu przedstawiono sposób dodawania **ListChanged** programu obsługi zdarzeń.  
  
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
- [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
