---
title: Implementowanie logiki biznesowej (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 7e24bf24785538863738fe2c006834a77f47e1ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496092"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Implementowanie logiki biznesowej (LINQ to SQL)
Termin "logikę biznesową" w tym temacie odnosi się do żadnych reguł niestandardowych lub testów sprawdzania poprawności, które są stosowane do danych, przed jego wstawione, zaktualizowane lub usunięte z bazy danych. Logika biznesowa jest również czasami określane jako "reguł biznesowych" lub "Logika domeny". W aplikacjach n warstwowych zazwyczaj służy jako logiczne warstwy tak, aby można było jej modyfikować niezależnie od warstwy prezentacji lub warstwy dostępu do danych. Logika biznesowa może być wywoływany przez warstwę dostępu do danych, przed lub po nim żadnych aktualizacji, wstawiania lub usuwania danych w bazie danych.  
  
 Logika biznesowa może być tak proste, jak sprawdzanie poprawności schematu, aby upewnić się, że typ pola jest zgodny z typem kolumny w tabeli. Lub też może składać się z zestawu obiektów, które wchodzić w interakcje w sposób dowolnie złożone. Zasady mogą być wykonywane jako procedur składowanych w bazie danych lub obiektów w pamięci. Jednak logika biznesowa jest implementowana, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umożliwia używasz klasy częściowe i metody częściowej, aby oddzielić logikę biznesową od kod dostępu do danych.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Jak wywołuje logikę biznesową w LINQ to SQL  
 Podczas generowania klasy jednostki w czasie projektowania, ręcznie lub za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub SQLMetal, jest on zdefiniowany jako klasy częściowej. Oznacza to, że w osobnym pliku kodu, można zdefiniować innej części klasy jednostki, która zawiera niestandardowej logiki biznesowej. W czasie kompilacji dwie części są scalane w jednej klasie. Ale jeśli musisz ponownie wygenerować z klas jednostek za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub SQLMetal, możesz to zrobić, a Twoja część klasy nie zostaną zmodyfikowane.  
  
 Częściowe klasy, które definiują jednostek i <xref:System.Data.Linq.DataContext> zawierają metody częściowej. Są to punkty rozszerzeń, które można zastosować logikę biznesową, przed i po nim żadnych update, insert czy delete dla jednostki lub właściwości jednostki. Metody częściowe mogą być uważane za zdarzenia w czasie kompilacji. Generator kodu definiuje podpis metody i wywołuje metody get i ustaw Akcesory właściwości `DataContext` konstruktora, a w niektórych przypadkach w tle podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana. Jednak jeśli nie należy implementować określonej metody częściowej, wszystkie odwołania do niej definicji są usuwane w czasie kompilacji.  
  
 W definicji implementującej zapisu w pliku osobnego kodu można wykonywać, niezależnie od logiki niestandardowej jest wymagana. Częściowe klasy sama służy jako warstwa Twojej domeny, lub można wywołać z definicji implementującej metody częściowej do oddzielnych obiektu lub obiektów. W obu przypadkach logiki biznesowej nie pozostawia żadnych śladów jest oddzielony od kodu dostępu do danych i kodzie warstwy prezentacji.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Bliższe spojrzenie na punkty rozszerzeń  
 W poniższym przykładzie przedstawiono część kod wygenerowany przez [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] dla `DataContext` klasy, która ma dwie tabele: `Customers` i `Orders`. Należy zauważyć, że wstawiania, aktualizowania i usuwania metody są zdefiniowane dla każdej tabeli w klasie.  
  
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
  
 W przypadku zastosowania Insert, aktualizowanie i usuwanie metody w klasie częściowej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowisko uruchomieniowe będzie wywoływać je zamiast własnej metody domyślne podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana. Dzięki temu można zastąpić domyślne zachowanie tworzenia / odczyt / aktualizowanie / usuwanie operacji. Aby uzyskać więcej informacji, zobacz [instruktażu: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
 `OnCreated` Metoda jest wywoływana w konstruktorze klasy.  
  
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
  
 Klasy jednostki mają trzy metody, które są wywoływane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowiska uruchomieniowego, gdy jednostka jest tworzone, ładowany i zweryfikować (gdy `SubmitChanges` nosi nazwę). Klas jednostek również mieć dwóch metod częściowych dla każdej właściwości: jeden, która jest wywoływana przed ustawieniem właściwości i jeden, które jest wywoływana po. Poniższy przykład kodu pokazuje niektóre metody generowane dla `Customer` klasy:  
  
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
  
 Metody są wywoływane w metodzie dostępu zestaw właściwości, jak pokazano w poniższym przykładzie dla `CustomerID` właściwości:  
  
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
  
 Twoja część klasy służy do pisania implementującej definicję metody. W programie Visual Studio po wpisaniu `partial` zobaczysz technologii IntelliSense dla definicji metody w innej części klasy.  
  
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
  
 Aby uzyskać więcej informacji o tym, jak dodać logikę biznesową do aplikacji przy użyciu metod częściowych zobacz następujące tematy:  
  
 [Instrukcje: Dodawanie walidacji do klas jednostek](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [Przewodnik: Dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Przewodnik: Dodawanie walidacji do klas jednostek](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a>Zobacz także
- [Klasy częściowe i metody](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Metody częściowe](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [Narzędzia LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
