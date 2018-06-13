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
ms.openlocfilehash: 5e04aa1a1d209074dbdadcb1df089e31efa84ded
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556721"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a><span data-ttu-id="b4187-102">Jak utworzyć i powiązać z ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="b4187-102">How to: Create and Bind to an ObservableCollection</span></span>
<span data-ttu-id="b4187-103">W tym przykładzie pokazano, jak utworzyć i powiązania z kolekcją, która jest pochodną <xref:System.Collections.ObjectModel.ObservableCollection%601> klasy, która jest klasę kolekcji, która zawiera powiadomienia elementów uzyskać dodania lub usunięcia.</span><span class="sxs-lookup"><span data-stu-id="b4187-103">This example shows how to create and bind to a collection that derives from the <xref:System.Collections.ObjectModel.ObservableCollection%601> class, which is a collection class that provides notifications when items get added or removed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4187-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4187-104">Example</span></span>  
 <span data-ttu-id="b4187-105">Poniższy przykład przedstawia implementację `NameList` kolekcji:</span><span class="sxs-lookup"><span data-stu-id="b4187-105">The following example shows the implementation of a `NameList` collection:</span></span>  
  
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
  
 <span data-ttu-id="b4187-106">Można udostępnić kolekcji dla powiązania taki sam sposób jak inne [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiekty, zgodnie z opisem w [upewnij dostępnych danych dla powiązania w języku XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b4187-106">You can make the collection available for binding the same way you would with other [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects, as described in [Make Data Available for Binding in XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span></span> <span data-ttu-id="b4187-107">Na przykład można utworzyć wystąpienia kolekcji w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i określ kolekcję jako zasób, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="b4187-107">For example, you can instantiate the collection in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and specify the collection as a resource, as shown here:</span></span>  
  
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
  
 <span data-ttu-id="b4187-108">Następnie możesz powiązać do kolekcji:</span><span class="sxs-lookup"><span data-stu-id="b4187-108">You can then bind to the collection:</span></span>  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 <span data-ttu-id="b4187-109">Definicja `NameItemTemplate` nie są wyświetlane tutaj.</span><span class="sxs-lookup"><span data-stu-id="b4187-109">The definition of `NameItemTemplate` is not shown here.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4187-110">Obiekty z kolekcji muszą spełniać wymagania opisane w [powiązanie Przegląd źródeł](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b4187-110">The objects in your collection must satisfy the requirements described in the [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span></span> <span data-ttu-id="b4187-111">W szczególności, jeśli używasz <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> (na przykład chcesz Twojej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] można zaktualizować właściwości źródła zmiany dynamicznie), musisz zaimplementować mechanizm powiadamiania odpowiednie zmiany właściwości, takie jak <xref:System.ComponentModel.INotifyPropertyChanged>interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b4187-111">In particular, if you are using <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> (for example, you want your [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to update when the source properties change dynamically), you must implement a suitable property changed notification mechanism such as the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span>  
  
 <span data-ttu-id="b4187-112">Aby uzyskać więcej informacji, zobacz powiązania w kolekcji sekcji [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b4187-112">For more information, see the Binding to Collections section in the [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4187-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4187-113">See Also</span></span>  
 [<span data-ttu-id="b4187-114">Sortowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="b4187-114">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="b4187-115">Filtrowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="b4187-115">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="b4187-116">Sortowanie i grupowanie danych przy użyciu widoku w XAML</span><span class="sxs-lookup"><span data-stu-id="b4187-116">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)  
 [<span data-ttu-id="b4187-117">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="b4187-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="b4187-118">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="b4187-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
