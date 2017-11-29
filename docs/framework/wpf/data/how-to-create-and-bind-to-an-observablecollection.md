---
title: "Jak utworzyć i powiązać z ObservableCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7918d97f2f1bcd521e7e7e38231c999d2fbda53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>Jak utworzyć i powiązać z ObservableCollection
W tym przykładzie pokazano, jak utworzyć i powiązania z kolekcją, która jest pochodną <xref:System.Collections.ObjectModel.ObservableCollection%601> klasy, która jest klasę kolekcji, która zawiera powiadomienia elementów uzyskać dodania lub usunięcia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia implementację `NameList` kolekcji:  
  
```csharp  
public class NameList : ObservableCollection<PersonName>  
{  
    public NameList() : base()  
    {  
        Add(new PersonName("Willa", "Cather"));  
        Add(new PersonName("Isak", "Dinesen"));  
        Add(new PersonName("Victor", "Hugo"));  
        Add(new PersonName("Jules", "Verne"));  
    }  
  }  
  
  public class PersonName  
  {  
      private string firstName;  
      private string lastName;  
  
      public PersonName(string first, string last)  
      {  
          this.firstName = first;  
          this.lastName = last;  
      }  
  
      public string FirstName  
      {  
          get { return firstName; }  
          set { firstName = value; }  
      }  
  
      public string LastName  
      {  
          get { return lastName; }  
          set { lastName = value; }  
      }  
  }  
```  
  
```vb  
Public Class NameList  
    Inherits ObservableCollection(Of PersonName)  
  
    ' Methods  
    Public Sub New()  
        MyBase.Add(New PersonName("Willa", "Cather"))  
        MyBase.Add(New PersonName("Isak", "Dinesen"))  
        MyBase.Add(New PersonName("Victor", "Hugo"))  
        MyBase.Add(New PersonName("Jules", "Verne"))  
    End Sub  
  
End Class  
  
Public Class PersonName  
    ' Methods  
    Public Sub New(ByVal first As String, ByVal last As String)  
        Me._firstName = first  
        Me._lastName = last  
    End Sub  
  
    ' Properties  
    Public Property FirstName() As String  
        Get  
            Return Me._firstName  
        End Get  
        Set(ByVal value As String)  
            Me._firstName = value  
        End Set  
    End Property  
  
    Public Property LastName() As String  
        Get  
            Return Me._lastName  
        End Get  
        Set(ByVal value As String)  
            Me._lastName = value  
        End Set  
    End Property  
  
    ' Fields  
    Private _firstName As String  
    Private _lastName As String  
End Class  
```  
  
 Można udostępnić kolekcji dla powiązania taki sam sposób jak inne [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiekty, zgodnie z opisem w [upewnij dostępnych danych dla powiązania w języku XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md). Na przykład można utworzyć wystąpienia kolekcji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i określ kolekcję jako zasób, jak pokazano poniżej:  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:c="clr-namespace:SDKSample"  
  x:Class="SDKSample.Window1"  
  Width="400"  
  Height="280"  
  Title="MultiBinding Sample">  
  
  <Window.Resources>  
    <c:NameList x:Key="NameListData"/>  
  
...  
  
</Window.Resources>  
```  
  
 Następnie możesz powiązać do kolekcji:  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 Definicja `NameItemTemplate` nie są wyświetlane tutaj.  
  
> [!NOTE]
>  Obiekty z kolekcji muszą spełniać wymagania opisane w [powiązanie Przegląd źródeł](../../../../docs/framework/wpf/data/binding-sources-overview.md). W szczególności, jeśli używasz <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> (na przykład chcesz Twojej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] można zaktualizować właściwości źródła zmiany dynamicznie), musisz zaimplementować mechanizm powiadamiania odpowiednie zmiany właściwości, takie jak <xref:System.ComponentModel.INotifyPropertyChanged>interfejsu.  
  
 Aby uzyskać więcej informacji, zobacz powiązania w kolekcji sekcji [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Sortowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [Filtrowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [Sortowanie i grupowanie danych przy użyciu widoku w języku XAML](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
