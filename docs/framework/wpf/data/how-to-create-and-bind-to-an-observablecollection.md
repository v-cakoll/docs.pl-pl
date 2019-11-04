---
title: Jak utworzyć i powiązać z ObservableCollection
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
ms.openlocfilehash: 596f6ae71e83c5aa3b2b80764f68a8abf08cdb7b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453517"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>Jak utworzyć i powiązać z ObservableCollection
Ten przykład pokazuje, jak utworzyć i powiązać z kolekcją, która dziedziczy z klasy <xref:System.Collections.ObjectModel.ObservableCollection%601>, która jest klasą kolekcji, która udostępnia powiadomienia, gdy elementy zostaną dodane lub usunięte.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono implementację kolekcji `NameList`:  
  
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
  
 Kolekcję można udostępnić w taki sam sposób, jak w przypadku innych obiektów środowiska uruchomieniowego języka wspólnego (CLR), zgodnie z opisem w temacie [udostępnianie danych do powiązania w języku XAML](how-to-make-data-available-for-binding-in-xaml.md). Można na przykład utworzyć wystąpienie kolekcji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i określić kolekcję jako zasób, jak pokazano poniżej:  
  
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
  
 Następnie można powiązać z kolekcją:  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 Definicja `NameItemTemplate` nie jest wyświetlana w tym miejscu.  
  
> [!NOTE]
> Obiekty w kolekcji muszą spełniać wymagania opisane w [Przegląd źródeł powiązań](binding-sources-overview.md). W szczególności, jeśli używasz <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> (na przykład chcesz, aby [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aktualizować, gdy właściwości źródłowe ulegną zmianie dynamicznie), należy zaimplementować odpowiedni mechanizm powiadamiania o zmianie właściwości, taki jak interfejs <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Aby uzyskać więcej informacji, zobacz sekcję Powiązywanie z kolekcjami w temacie [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Sortowanie danych w widoku](how-to-sort-data-in-a-view.md)
- [Filtrowanie danych w widoku](how-to-filter-data-in-a-view.md)
- [Sortowanie i grupowanie danych przy użyciu widoku w XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
