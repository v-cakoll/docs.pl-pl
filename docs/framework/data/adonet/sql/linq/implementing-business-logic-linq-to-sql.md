---
title: Implementowanie logiki biznesowej (LINQ do SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 51b92549a40d0e5121cc390f5dbdf726cc06404b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174553"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Implementowanie logiki biznesowej (LINQ do SQL)
Termin "logika biznesowa" w tym temacie odnosi się do wszelkich reguł niestandardowych lub testów sprawdzania poprawności, które mają zastosowanie do danych przed ich wstawieniem, zaktualizowaniem lub usunięciem z bazy danych. Logika biznesowa jest również czasami nazywana "regułami biznesowymi" lub "logiką domeny". W aplikacjach n-warstwowych jest zazwyczaj zaprojektowany jako warstwa logiczna, dzięki czemu można go modyfikować niezależnie od warstwy prezentacji lub warstwy dostępu do danych. Logika biznesowa może być wywoływana przez warstwę dostępu do danych przed lub po każdej aktualizacji, wstawieniu lub usunięciu danych w bazie danych.  
  
 Logika biznesowa może być tak prosta, jak sprawdzanie poprawności schematu, aby upewnić się, że typ pola jest zgodny z typem kolumny tabeli. Lub może składać się z zestawu obiektów, które współdziałają w dowolnie złożony sposób. Reguły mogą być implementowane jako procedury przechowywane w bazie danych lub jako obiekty w pamięci. Jednak logika biznesowa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest zaimplementowana, umożliwia użycie klas częściowych i metod częściowych, aby oddzielić logikę biznesową od kodu dostępu do danych.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Jak LINQ do SQL wywołuje logikę biznesową  
 Podczas generowania klasy jednostki w czasie projektowania, ręcznie lub przy użyciu Object Relational Designer lub SQLMetal, jest zdefiniowany jako klasa częściowa. Oznacza to, że w pliku kodu oddzielne, można zdefiniować inną część klasy jednostki, która zawiera niestandardową logikę biznesową. W czasie kompilacji dwie części są scalane w jedną klasę. Ale jeśli trzeba ponownie wygenerować klasy jednostki przy użyciu Object Relational Designer lub SQLMetal, można to zrobić, a część klasy nie zostaną zmodyfikowane.  
  
 Klasy częściowe, które definiują jednostki <xref:System.Data.Linq.DataContext> i zawierają metody częściowe. Są to punkty rozszerzalności, których można użyć do zastosowania logiki biznesowej przed i po każdej aktualizacji, wstawianiu lub usuwaniu właściwości jednostki lub jednostki. Metody częściowe można traktować jako zdarzenia w czasie kompilacji. Generator kodu definiuje podpis metody i wywołuje metody w get and set `DataContext` akcesorów właściwości, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> konstruktora, a w niektórych przypadkach w tle, gdy jest wywoływana. Jednak jeśli nie zaimplementujesz określonej metody częściowej, wszystkie odwołania do niej i definicja są usuwane w czasie kompilacji.  
  
 W definicji implementacji, który piszesz w pliku kodu oddzielne, można wykonać niezależnie od logiki niestandardowej jest wymagane. Klasę częściową można użyć jako warstwy domeny lub wywołać z implementującej definicji metody częściowej do oddzielnego obiektu lub obiektów. Tak czy inaczej logika biznesowa jest czysto oddzielona od kodu dostępu do danych i kodu warstwy prezentacji.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Bliższe spojrzenie na punkty rozszerzalności  
 W poniższym przykładzie przedstawiono część kodu wygenerowanego `DataContext` przez projektanta `Customers` relacyjnego obiektu dla klasy, która ma dwie tabele: i `Orders`. Należy zauważyć, że wstaw, aktualizacja i usuń metody są zdefiniowane dla każdej tabeli w klasie.  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 Jeśli zaimplementujesz Wstaw, Aktualizuj i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Usuń metody w klasie częściowej, środowisko <xref:System.Data.Linq.DataContext.SubmitChanges%2A> wykonawcze wywoła je zamiast własnych metod domyślnych, gdy jest wywoływana. Pozwala to zastąpić domyślne zachowanie dla operacji tworzenia / odczytu / aktualizacji / usuwania. Aby uzyskać więcej informacji, zobacz [Przewodnik: Dostosowywanie zachowania wstawiania, aktualizowania i usuwania klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
 Metoda `OnCreated` jest wywoływana w konstruktorze klasy.  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 Klasy jednostek mają trzy metody, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] które są wywoływane przez środowisko wykonawcze `SubmitChanges` podczas tworzenia, ładowania i sprawdzania poprawności jednostki (po wywołaniu). Klasy jednostki mają również dwie metody częściowe dla każdej właściwości, jedną, która jest wywoływana przed ustawieniem właściwości, i jedną, która jest wywoływana po. Poniższy przykład kodu pokazuje niektóre metody `Customer` generowane dla klasy:  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 Metody są wywoływane w akcesor zestawu właściwości, jak pokazano w poniższym przykładzie `CustomerID` dla właściwości:  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 W swojej części klasy piszesz implementującą definicję metody. W programie Visual Studio `partial` po wpisaniu zostanie wyświetlony IntelliSense dla definicji metod w drugiej części klasy.  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 Aby uzyskać więcej informacji na temat dodawania logiki biznesowej do aplikacji przy użyciu metod częściowych, zobacz następujące tematy:  
  
 [Instrukcje: dodawanie walidacji do klas jednostek](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [Przewodnik: dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Przewodnik: Dodawanie sprawdzania poprawności do klas encji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a>Zobacz też

- [Klasy częściowe i metody](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Metody częściowe](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [Narzędzia LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
