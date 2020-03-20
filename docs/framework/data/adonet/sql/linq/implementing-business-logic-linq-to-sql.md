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
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="3103a-102">Implementowanie logiki biznesowej (LINQ do SQL)</span><span class="sxs-lookup"><span data-stu-id="3103a-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="3103a-103">Termin "logika biznesowa" w tym temacie odnosi się do wszelkich reguł niestandardowych lub testów sprawdzania poprawności, które mają zastosowanie do danych przed ich wstawieniem, zaktualizowaniem lub usunięciem z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3103a-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="3103a-104">Logika biznesowa jest również czasami nazywana "regułami biznesowymi" lub "logiką domeny".</span><span class="sxs-lookup"><span data-stu-id="3103a-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="3103a-105">W aplikacjach n-warstwowych jest zazwyczaj zaprojektowany jako warstwa logiczna, dzięki czemu można go modyfikować niezależnie od warstwy prezentacji lub warstwy dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="3103a-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="3103a-106">Logika biznesowa może być wywoływana przez warstwę dostępu do danych przed lub po każdej aktualizacji, wstawieniu lub usunięciu danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="3103a-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="3103a-107">Logika biznesowa może być tak prosta, jak sprawdzanie poprawności schematu, aby upewnić się, że typ pola jest zgodny z typem kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="3103a-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="3103a-108">Lub może składać się z zestawu obiektów, które współdziałają w dowolnie złożony sposób.</span><span class="sxs-lookup"><span data-stu-id="3103a-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="3103a-109">Reguły mogą być implementowane jako procedury przechowywane w bazie danych lub jako obiekty w pamięci.</span><span class="sxs-lookup"><span data-stu-id="3103a-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="3103a-110">Jednak logika biznesowa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest zaimplementowana, umożliwia użycie klas częściowych i metod częściowych, aby oddzielić logikę biznesową od kodu dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="3103a-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="3103a-111">Jak LINQ do SQL wywołuje logikę biznesową</span><span class="sxs-lookup"><span data-stu-id="3103a-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="3103a-112">Podczas generowania klasy jednostki w czasie projektowania, ręcznie lub przy użyciu Object Relational Designer lub SQLMetal, jest zdefiniowany jako klasa częściowa.</span><span class="sxs-lookup"><span data-stu-id="3103a-112">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="3103a-113">Oznacza to, że w pliku kodu oddzielne, można zdefiniować inną część klasy jednostki, która zawiera niestandardową logikę biznesową.</span><span class="sxs-lookup"><span data-stu-id="3103a-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="3103a-114">W czasie kompilacji dwie części są scalane w jedną klasę.</span><span class="sxs-lookup"><span data-stu-id="3103a-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="3103a-115">Ale jeśli trzeba ponownie wygenerować klasy jednostki przy użyciu Object Relational Designer lub SQLMetal, można to zrobić, a część klasy nie zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="3103a-115">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="3103a-116">Klasy częściowe, które definiują jednostki <xref:System.Data.Linq.DataContext> i zawierają metody częściowe.</span><span class="sxs-lookup"><span data-stu-id="3103a-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="3103a-117">Są to punkty rozszerzalności, których można użyć do zastosowania logiki biznesowej przed i po każdej aktualizacji, wstawianiu lub usuwaniu właściwości jednostki lub jednostki.</span><span class="sxs-lookup"><span data-stu-id="3103a-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="3103a-118">Metody częściowe można traktować jako zdarzenia w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3103a-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="3103a-119">Generator kodu definiuje podpis metody i wywołuje metody w get and set `DataContext` akcesorów właściwości, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> konstruktora, a w niektórych przypadkach w tle, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3103a-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="3103a-120">Jednak jeśli nie zaimplementujesz określonej metody częściowej, wszystkie odwołania do niej i definicja są usuwane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3103a-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="3103a-121">W definicji implementacji, który piszesz w pliku kodu oddzielne, można wykonać niezależnie od logiki niestandardowej jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="3103a-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="3103a-122">Klasę częściową można użyć jako warstwy domeny lub wywołać z implementującej definicji metody częściowej do oddzielnego obiektu lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="3103a-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="3103a-123">Tak czy inaczej logika biznesowa jest czysto oddzielona od kodu dostępu do danych i kodu warstwy prezentacji.</span><span class="sxs-lookup"><span data-stu-id="3103a-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="3103a-124">Bliższe spojrzenie na punkty rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="3103a-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="3103a-125">W poniższym przykładzie przedstawiono część kodu wygenerowanego `DataContext` przez projektanta `Customers` relacyjnego obiektu dla klasy, która ma dwie tabele: i `Orders`.</span><span class="sxs-lookup"><span data-stu-id="3103a-125">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="3103a-126">Należy zauważyć, że wstaw, aktualizacja i usuń metody są zdefiniowane dla każdej tabeli w klasie.</span><span class="sxs-lookup"><span data-stu-id="3103a-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="3103a-127">Jeśli zaimplementujesz Wstaw, Aktualizuj i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Usuń metody w klasie częściowej, środowisko <xref:System.Data.Linq.DataContext.SubmitChanges%2A> wykonawcze wywoła je zamiast własnych metod domyślnych, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3103a-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="3103a-128">Pozwala to zastąpić domyślne zachowanie dla operacji tworzenia / odczytu / aktualizacji / usuwania.</span><span class="sxs-lookup"><span data-stu-id="3103a-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="3103a-129">Aby uzyskać więcej informacji, zobacz [Przewodnik: Dostosowywanie zachowania wstawiania, aktualizowania i usuwania klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="3103a-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="3103a-130">Metoda `OnCreated` jest wywoływana w konstruktorze klasy.</span><span class="sxs-lookup"><span data-stu-id="3103a-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="3103a-131">Klasy jednostek mają trzy metody, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] które są wywoływane przez środowisko wykonawcze `SubmitChanges` podczas tworzenia, ładowania i sprawdzania poprawności jednostki (po wywołaniu).</span><span class="sxs-lookup"><span data-stu-id="3103a-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="3103a-132">Klasy jednostki mają również dwie metody częściowe dla każdej właściwości, jedną, która jest wywoływana przed ustawieniem właściwości, i jedną, która jest wywoływana po.</span><span class="sxs-lookup"><span data-stu-id="3103a-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="3103a-133">Poniższy przykład kodu pokazuje niektóre metody `Customer` generowane dla klasy:</span><span class="sxs-lookup"><span data-stu-id="3103a-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="3103a-134">Metody są wywoływane w akcesor zestawu właściwości, jak pokazano w poniższym przykładzie `CustomerID` dla właściwości:</span><span class="sxs-lookup"><span data-stu-id="3103a-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="3103a-135">W swojej części klasy piszesz implementującą definicję metody.</span><span class="sxs-lookup"><span data-stu-id="3103a-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="3103a-136">W programie Visual Studio `partial` po wpisaniu zostanie wyświetlony IntelliSense dla definicji metod w drugiej części klasy.</span><span class="sxs-lookup"><span data-stu-id="3103a-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="3103a-137">Aby uzyskać więcej informacji na temat dodawania logiki biznesowej do aplikacji przy użyciu metod częściowych, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="3103a-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="3103a-138">Instrukcje: dodawanie walidacji do klas jednostek</span><span class="sxs-lookup"><span data-stu-id="3103a-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="3103a-139">Przewodnik: dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek</span><span class="sxs-lookup"><span data-stu-id="3103a-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="3103a-140">[Przewodnik: Dodawanie sprawdzania poprawności do klas encji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="3103a-140">[Walkthrough: Adding Validation to Entity Classes](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3103a-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3103a-141">See also</span></span>

- [<span data-ttu-id="3103a-142">Klasy częściowe i metody</span><span class="sxs-lookup"><span data-stu-id="3103a-142">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="3103a-143">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="3103a-143">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="3103a-144">Narzędzia LINQ to SQL Tools w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3103a-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="3103a-145">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="3103a-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
