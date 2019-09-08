---
title: Implementowanie logiki biznesowej (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 5261aab1ef6641651f856b8ebb024f64ad32ee59
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781430"
---
# <a name="implementing-business-logic-linq-to-sql"></a>Implementowanie logiki biznesowej (LINQ to SQL)
Termin "logika biznesowa" w tym temacie odnosi się do wszystkich reguł niestandardowych lub testów weryfikacyjnych, które są stosowane do danych, zanim zostaną wstawione, zaktualizowane lub usunięte z bazy danych. Logika biznesowa jest również czasami określana jako "reguły biznesowe" lub "Logika domeny". W aplikacjach n-warstwowych zwykle jest to warstwa logiczna, dzięki czemu można ją modyfikować niezależnie od warstwy prezentacji lub warstwy dostępu do danych. Logika biznesowa może być wywoływana przez warstwę dostępu do danych przed dowolnymi aktualizacjami, wstawianiem lub usuwaniem danych w bazie danych.  
  
 Logika biznesowa może być prosta jako Walidacja schematu, aby upewnić się, że typ pola jest zgodny z typem kolumny tabeli. Lub może składać się z zestawu obiektów, które współpracują w sposób arbitralnie skomplikowany. Reguły mogą być implementowane jako procedury składowane w bazie danych lub jako obiekty w pamięci. Jednak logika biznesowa jest zaimplementowana, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umożliwia korzystanie z klas częściowych i metod częściowych w celu oddzielenia logiki biznesowej od kodu dostępu do danych.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Jak LINQ to SQL wywołuje logikę biznesową  
 Podczas generowania klasy jednostki w czasie projektowania, ręcznie lub przy użyciu Object Relational Designer lub SQLMetal, jest definiowana jako Klasa częściowa. Oznacza to, że w osobnym pliku kodu można zdefiniować inną część klasy Entity, która zawiera niestandardową logikę biznesową. W czasie kompilacji dwie części są scalane w jedną klasę. Ale jeśli musisz ponownie wygenerować klasy jednostek przy użyciu Object Relational Designer lub SQLMetal, możesz to zrobić, a część klasy nie zostanie zmodyfikowana.  
  
 Klasy częściowe, które definiują jednostki i <xref:System.Data.Linq.DataContext> zawierają metody częściowe. Są to punkty rozszerzalności, których można użyć do zastosowania logiki biznesowej przed i po dowolnej aktualizacji, wstawieniu lub usunięciu dla właściwości jednostki lub jednostki. Metody częściowe można traktować jako zdarzenia w czasie kompilacji. Generator kodu definiuje sygnaturę metody i wywołuje metody w metodach dostępu do właściwości get i Set, `DataContext` Konstruktor i w niektórych przypadkach w tle, gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana. Jednakże jeśli nie zaimplementowano konkretnej metody częściowej, wszystkie odwołania do niej i definicja zostaną usunięte w czasie kompilacji.  
  
 W definicji implementującej zapisanej w osobnym pliku kodu można wykonać dowolną logikę niestandardową. Możesz użyć swojej częściowej klasy jako warstwy domeny lub wywołać z definicji implementującej metody częściowej w oddzielnym obiekcie lub obiektach. W obu przypadkach logika biznesowa jest czysto oddzielona od kodu dostępu do danych i kodu warstwy prezentacji.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Bliżej przeszukiwania punktów rozszerzalności  
 Poniższy przykład przedstawia część kodu wygenerowanego przez Object Relational Designer dla `DataContext` klasy, która ma dwie tabele: `Customers` i `Orders`. Należy zauważyć, że dla każdej tabeli w klasie są zdefiniowane metody INSERT, Update i DELETE.  
  
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
  
 W przypadku zaimplementowania metody INSERT, Update i DELETE w klasie częściowej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowisko uruchomieniowe wywoła je zamiast własnych metod domyślnych, gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana. Dzięki temu można zastąpić domyślne zachowanie operacji tworzenia/odczytywania/aktualizowania/usuwania. Aby uzyskać więcej informacji, [zobacz Przewodnik: Dostosowywanie zachowania INSERT, Update i DELETE klas](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)jednostek.  
  
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
  
 Klasy jednostek mają trzy metody, które są wywoływane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowisko uruchomieniowe, gdy jednostka została utworzona, załadowana i sprawdzona (gdy `SubmitChanges` jest wywoływana). Klasy jednostek mają również dwie metody częściowe dla każdej właściwości, jeden, który jest wywoływany przed ustawieniem właściwości, i jeden, który jest wywoływany po. Poniższy przykład kodu pokazuje niektóre metody wygenerowane dla `Customer` klasy:  
  
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
  
 Metody są wywoływane w akcesorze zestawu właściwości, jak pokazano w poniższym przykładzie dla `CustomerID` właściwości:  
  
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
  
 W Twojej części klasy napiszesz definicję implementującą metodę. W programie Visual Studio, po wpisaniu `partial` , zobaczysz IntelliSense dla definicji metod w drugiej części klasy.  
  
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
  
 [Instrukcje: Dodawanie walidacji do klas jednostek](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [Przewodnik: Dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Przewodnik: Dodawanie walidacji do klas jednostek](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a>Zobacz także

- [Klasy częściowe i metody](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [Metody częściowe](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [Narzędzia LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [SqlMetal.exe (narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
