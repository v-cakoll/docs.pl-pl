---
title: Implementowanie logiki biznesowej (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 3dcc6f763acfff076bb03076a17e3a8f8916267c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097255"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="4c025-102">Implementowanie logiki biznesowej (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="4c025-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="4c025-103">Termin "logikę biznesową" w tym temacie odnosi się do żadnych reguł niestandardowych lub testów sprawdzania poprawności, które są stosowane do danych, przed jego wstawione, zaktualizowane lub usunięte z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4c025-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="4c025-104">Logika biznesowa jest również czasami określane jako "reguł biznesowych" lub "Logika domeny".</span><span class="sxs-lookup"><span data-stu-id="4c025-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="4c025-105">W aplikacjach n warstwowych zazwyczaj służy jako logiczne warstwy tak, aby można było jej modyfikować niezależnie od warstwy prezentacji lub warstwy dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="4c025-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="4c025-106">Logika biznesowa może być wywoływany przez warstwę dostępu do danych, przed lub po nim żadnych aktualizacji, wstawiania lub usuwania danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="4c025-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="4c025-107">Logika biznesowa może być tak proste, jak sprawdzanie poprawności schematu, aby upewnić się, że typ pola jest zgodny z typem kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="4c025-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="4c025-108">Lub też może składać się z zestawu obiektów, które wchodzić w interakcje w sposób dowolnie złożone.</span><span class="sxs-lookup"><span data-stu-id="4c025-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="4c025-109">Zasady mogą być wykonywane jako procedur składowanych w bazie danych lub obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="4c025-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="4c025-110">Jednak logika biznesowa jest implementowana, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umożliwia używasz klasy częściowe i metody częściowej, aby oddzielić logikę biznesową od kod dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="4c025-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="4c025-111">Jak wywołuje logikę biznesową w LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4c025-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="4c025-112">Podczas generowania klasy jednostki w czasie projektowania, ręcznie lub za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub SQLMetal, jest on zdefiniowany jako klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="4c025-112">When you generate an entity class at design time, either manually or by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="4c025-113">Oznacza to, że w osobnym pliku kodu, można zdefiniować innej części klasy jednostki, która zawiera niestandardowej logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="4c025-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="4c025-114">W czasie kompilacji dwie części są scalane w jednej klasie.</span><span class="sxs-lookup"><span data-stu-id="4c025-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="4c025-115">Ale jeśli musisz ponownie wygenerować z klas jednostek za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub SQLMetal, możesz to zrobić, a Twoja część klasy nie zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="4c025-115">But if you have to regenerate your entity classes by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="4c025-116">Częściowe klasy, które definiują jednostek i <xref:System.Data.Linq.DataContext> zawierają metody częściowej.</span><span class="sxs-lookup"><span data-stu-id="4c025-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="4c025-117">Są to punkty rozszerzeń, które można zastosować logikę biznesową, przed i po nim żadnych update, insert czy delete dla jednostki lub właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="4c025-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="4c025-118">Metody częściowe mogą być uważane za zdarzenia w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4c025-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="4c025-119">Generator kodu definiuje podpis metody i wywołuje metody get i ustaw Akcesory właściwości `DataContext` konstruktora, a w niektórych przypadkach w tle podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="4c025-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="4c025-120">Jednak jeśli nie należy implementować określonej metody częściowej, wszystkie odwołania do niej definicji są usuwane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4c025-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="4c025-121">W definicji implementującej zapisu w pliku osobnego kodu można wykonywać, niezależnie od logiki niestandardowej jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="4c025-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="4c025-122">Częściowe klasy sama służy jako warstwa Twojej domeny, lub można wywołać z definicji implementującej metody częściowej do oddzielnych obiektu lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="4c025-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="4c025-123">W obu przypadkach logiki biznesowej nie pozostawia żadnych śladów jest oddzielony od kodu dostępu do danych i kodzie warstwy prezentacji.</span><span class="sxs-lookup"><span data-stu-id="4c025-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="4c025-124">Bliższe spojrzenie na punkty rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="4c025-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="4c025-125">W poniższym przykładzie przedstawiono część kod wygenerowany przez [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] dla `DataContext` klasy, która ma dwie tabele: `Customers` i `Orders`.</span><span class="sxs-lookup"><span data-stu-id="4c025-125">The following example shows part of the code generated by the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="4c025-126">Należy zauważyć, że wstawiania, aktualizowania i usuwania metody są zdefiniowane dla każdej tabeli w klasie.</span><span class="sxs-lookup"><span data-stu-id="4c025-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="4c025-127">W przypadku zastosowania Insert, aktualizowanie i usuwanie metody w klasie częściowej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowisko uruchomieniowe będzie wywoływać je zamiast własnej metody domyślne podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="4c025-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="4c025-128">Dzięki temu można zastąpić domyślne zachowanie tworzenia / odczyt / aktualizowanie / usuwanie operacji.</span><span class="sxs-lookup"><span data-stu-id="4c025-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="4c025-129">Aby uzyskać więcej informacji, zobacz [instruktażu: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="4c025-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="4c025-130">`OnCreated` Metoda jest wywoływana w konstruktorze klasy.</span><span class="sxs-lookup"><span data-stu-id="4c025-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="4c025-131">Klasy jednostki mają trzy metody, które są wywoływane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowiska uruchomieniowego, gdy jednostka jest tworzone, ładowany i zweryfikować (gdy `SubmitChanges` nosi nazwę).</span><span class="sxs-lookup"><span data-stu-id="4c025-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="4c025-132">Klas jednostek również mieć dwóch metod częściowych dla każdej właściwości: jeden, która jest wywoływana przed ustawieniem właściwości i jeden, które jest wywoływana po.</span><span class="sxs-lookup"><span data-stu-id="4c025-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="4c025-133">Poniższy przykład kodu pokazuje niektóre metody generowane dla `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="4c025-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="4c025-134">Metody są wywoływane w metodzie dostępu zestaw właściwości, jak pokazano w poniższym przykładzie dla `CustomerID` właściwości:</span><span class="sxs-lookup"><span data-stu-id="4c025-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="4c025-135">Twoja część klasy służy do pisania implementującej definicję metody.</span><span class="sxs-lookup"><span data-stu-id="4c025-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="4c025-136">W programie Visual Studio po wpisaniu `partial` zobaczysz technologii IntelliSense dla definicji metody w innej części klasy.</span><span class="sxs-lookup"><span data-stu-id="4c025-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="4c025-137">Aby uzyskać więcej informacji o tym, jak dodać logikę biznesową do aplikacji przy użyciu metod częściowych zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="4c025-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="4c025-138">Instrukcje: Dodawanie walidacji do klas jednostek</span><span class="sxs-lookup"><span data-stu-id="4c025-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="4c025-139">Przewodnik: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek</span><span class="sxs-lookup"><span data-stu-id="4c025-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [<span data-ttu-id="4c025-140">Przewodnik: Dodawanie walidacji do klas jednostek</span><span class="sxs-lookup"><span data-stu-id="4c025-140">Walkthrough: Adding Validation to Entity Classes</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))  
  
## <a name="see-also"></a><span data-ttu-id="4c025-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c025-141">See also</span></span>

- [<span data-ttu-id="4c025-142">Klasy częściowe i metody</span><span class="sxs-lookup"><span data-stu-id="4c025-142">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="4c025-143">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="4c025-143">Partial Methods</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="4c025-144">LINQ to SQL Tools w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4c025-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="4c025-145">SqlMetal.exe (Narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="4c025-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
