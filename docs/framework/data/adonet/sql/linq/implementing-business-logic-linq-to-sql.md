---
title: Implementowanie logiki biznesowej (LINQ to SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d905f34c29fbd8a15cb8225a4a547490a5c14efd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="implementing-business-logic-linq-to-sql"></a>Implementowanie logiki biznesowej (LINQ to SQL)
Termin "logiki biznesowej" w tym temacie odnosi się do żadnych reguł niestandardowych lub testów sprawdzania poprawności, które są stosowane do danych, przed jego wstawiony, zaktualizowane lub usunięte z bazy danych. Logika biznesowa jest czasami nazywany "reguły biznesowe" lub "Logika domeny". W aplikacjach warstwowych zwykle zaprojektowano go jako Warstwa logiczna tak, aby można było jej modyfikować niezależnie od warstwy prezentacji lub Warstwa dostępu do danych. Logika biznesowa może być wywoływany przez Warstwa dostępu do danych, przed lub po żadnych aktualizowania, wstawiania lub usuwania danych w bazie danych.  
  
 Logika biznesowa może być prosty jak sprawdzanie poprawności schematu, aby upewnić się, że typem pola jest niezgodny z typem kolumny tabeli. Lub też może składać się z zestawu obiektów wchodzących w interakcję w sposób arbitralnie złożonych. Zasady mogą być wykonywane jako procedury składowane w bazie danych lub obiektów w pamięci. Jednak zaimplementowano logiki biznesowej, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umożliwia Użyj klasy częściowe i metody częściowe do oddzielania logiki biznesowej z danych kodu dostępu.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Jak wywołuje logiki biznesowej w składniku LINQ to SQL  
 Podczas generowania klasy jednostki w czasie projektowania, ręcznie lub za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub SQLMetal, jest on zdefiniowany jako klasy częściowej. Oznacza to, że w osobnym pliku kodu, można zdefiniować inną część klasę jednostki, która zawiera niestandardowej logiki biznesowej. W czasie kompilacji dwie części są scalane w jednej klasy. Ale jeśli masz można ponownie wygenerować klas jednostek przy użyciu [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub SQLMetal, możesz to zrobić, a Twoje część klasy nie zostaną zmodyfikowane.  
  
 Klasy częściowe, które definiują jednostek i <xref:System.Data.Linq.DataContext> zawiera metody częściowe. Są to punkty rozszerzeń, które można zastosować logiki biznesowej, przed i po nich żadnych aktualizacji, wstawiania lub usuwania jednostki lub właściwości jednostki. Metody częściowe mogą być uważane za zdarzenia w czasie kompilacji. Generator kodu definiuje sygnatury metody i wywołuje metody w get i ustaw metod dostępu do właściwości, `DataContext` konstruktora, a w niektórych przypadkach w tle podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana. Jednak jeśli nie implementuje określonej metody częściowej, wszystkie odwołania do go, jak i definicja są usuwane w czasie kompilacji.  
  
 W definicji implementującej zapisu w pliku kodu oddzielnych możesz wykonać, jest wymagany niezależnie od niestandardowej logiki. Można używać z częściowa samej klasy jako warstwa domeny, lub można wywołać z definicja implementującej metody częściowej w oddzielnych obiektu lub obiektów. W obu przypadkach logiki biznesowej prawidłowo jest oddzielony od zarówno kod dostępu do danych i kodu warstwy prezentacji.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Bliższe spojrzenie na punktów rozszerzalności  
 W poniższym przykładzie przedstawiono część kod wygenerowany przez [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] dla `DataContext` klasy, która ma dwie tabele: `Customers` i `Orders`. Należy pamiętać, że wstawiania, aktualizowania i usuwania metody są definiowane dla każdej tabeli w klasie.  
  
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
  
 W przypadku zastosowania Insert, aktualizować i usuwać metody w klasie częściowej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowiska uruchomieniowego wywoła je zamiast metody domyślnej podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana. Umożliwia zastąpienie zachowania domyślnego dla tworzenia / odczytu / aktualizacji / usuwanie operacji. Aby uzyskać więcej informacji, zobacz [wskazówki: dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
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
  
 Klas jednostek ma trzy metody, które są wywoływane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowiska uruchomieniowego podczas tworzenia, załadowane i zweryfikowane jednostki (gdy `SubmitChanges` jest nazywany). Klasy jednostki mają również dwie metody częściowe dla każdej właściwości, który jest wywoływana przed skonfigurowaniem właściwości i jeden, które jest wywoływana po wykonaniu. Poniższy przykładowy kod przedstawia niektóre generowane dla metody `Customer` klasy:  
  
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
  
 Metody są wywoływane w metodzie dostępu set właściwości, jak pokazano w poniższym przykładzie dla `CustomerID` właściwości:  
  
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
  
 W Twojej część klasy pisania implementującej definicję metody. W [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)]po wpisaniu `partial` zostanie wyświetlone IntelliSense dla definicji metody w drugiej klasy.  
  
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
  
 Aby uzyskać więcej informacji na temat dodawania reguł biznesowych do aplikacji przy użyciu metody częściowe zobacz następujące tematy:  
  
 [Porady: Dodawanie walidacji do klas jednostek](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [Wskazówki: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Wskazówki: Dodawanie walidacji do klas jednostek](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy częściowe i metody](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)  
 [Metody częściowe](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)  
 [LINQ do SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
