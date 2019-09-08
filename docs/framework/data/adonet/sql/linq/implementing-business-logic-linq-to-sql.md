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
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="b4875-102">Implementowanie logiki biznesowej (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="b4875-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="b4875-103">Termin "logika biznesowa" w tym temacie odnosi się do wszystkich reguł niestandardowych lub testów weryfikacyjnych, które są stosowane do danych, zanim zostaną wstawione, zaktualizowane lub usunięte z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b4875-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="b4875-104">Logika biznesowa jest również czasami określana jako "reguły biznesowe" lub "Logika domeny".</span><span class="sxs-lookup"><span data-stu-id="b4875-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="b4875-105">W aplikacjach n-warstwowych zwykle jest to warstwa logiczna, dzięki czemu można ją modyfikować niezależnie od warstwy prezentacji lub warstwy dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="b4875-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="b4875-106">Logika biznesowa może być wywoływana przez warstwę dostępu do danych przed dowolnymi aktualizacjami, wstawianiem lub usuwaniem danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="b4875-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="b4875-107">Logika biznesowa może być prosta jako Walidacja schematu, aby upewnić się, że typ pola jest zgodny z typem kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="b4875-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="b4875-108">Lub może składać się z zestawu obiektów, które współpracują w sposób arbitralnie skomplikowany.</span><span class="sxs-lookup"><span data-stu-id="b4875-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="b4875-109">Reguły mogą być implementowane jako procedury składowane w bazie danych lub jako obiekty w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b4875-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="b4875-110">Jednak logika biznesowa jest zaimplementowana, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umożliwia korzystanie z klas częściowych i metod częściowych w celu oddzielenia logiki biznesowej od kodu dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="b4875-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="b4875-111">Jak LINQ to SQL wywołuje logikę biznesową</span><span class="sxs-lookup"><span data-stu-id="b4875-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="b4875-112">Podczas generowania klasy jednostki w czasie projektowania, ręcznie lub przy użyciu Object Relational Designer lub SQLMetal, jest definiowana jako Klasa częściowa.</span><span class="sxs-lookup"><span data-stu-id="b4875-112">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="b4875-113">Oznacza to, że w osobnym pliku kodu można zdefiniować inną część klasy Entity, która zawiera niestandardową logikę biznesową.</span><span class="sxs-lookup"><span data-stu-id="b4875-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="b4875-114">W czasie kompilacji dwie części są scalane w jedną klasę.</span><span class="sxs-lookup"><span data-stu-id="b4875-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="b4875-115">Ale jeśli musisz ponownie wygenerować klasy jednostek przy użyciu Object Relational Designer lub SQLMetal, możesz to zrobić, a część klasy nie zostanie zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="b4875-115">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="b4875-116">Klasy częściowe, które definiują jednostki i <xref:System.Data.Linq.DataContext> zawierają metody częściowe.</span><span class="sxs-lookup"><span data-stu-id="b4875-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="b4875-117">Są to punkty rozszerzalności, których można użyć do zastosowania logiki biznesowej przed i po dowolnej aktualizacji, wstawieniu lub usunięciu dla właściwości jednostki lub jednostki.</span><span class="sxs-lookup"><span data-stu-id="b4875-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="b4875-118">Metody częściowe można traktować jako zdarzenia w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b4875-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="b4875-119">Generator kodu definiuje sygnaturę metody i wywołuje metody w metodach dostępu do właściwości get i Set, `DataContext` Konstruktor i w niektórych przypadkach w tle, gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b4875-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="b4875-120">Jednakże jeśli nie zaimplementowano konkretnej metody częściowej, wszystkie odwołania do niej i definicja zostaną usunięte w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b4875-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="b4875-121">W definicji implementującej zapisanej w osobnym pliku kodu można wykonać dowolną logikę niestandardową.</span><span class="sxs-lookup"><span data-stu-id="b4875-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="b4875-122">Możesz użyć swojej częściowej klasy jako warstwy domeny lub wywołać z definicji implementującej metody częściowej w oddzielnym obiekcie lub obiektach.</span><span class="sxs-lookup"><span data-stu-id="b4875-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="b4875-123">W obu przypadkach logika biznesowa jest czysto oddzielona od kodu dostępu do danych i kodu warstwy prezentacji.</span><span class="sxs-lookup"><span data-stu-id="b4875-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="b4875-124">Bliżej przeszukiwania punktów rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="b4875-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="b4875-125">Poniższy przykład przedstawia część kodu wygenerowanego przez Object Relational Designer dla `DataContext` klasy, która ma dwie tabele: `Customers` i `Orders`.</span><span class="sxs-lookup"><span data-stu-id="b4875-125">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="b4875-126">Należy zauważyć, że dla każdej tabeli w klasie są zdefiniowane metody INSERT, Update i DELETE.</span><span class="sxs-lookup"><span data-stu-id="b4875-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="b4875-127">W przypadku zaimplementowania metody INSERT, Update i DELETE w klasie częściowej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowisko uruchomieniowe wywoła je zamiast własnych metod domyślnych, gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b4875-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="b4875-128">Dzięki temu można zastąpić domyślne zachowanie operacji tworzenia/odczytywania/aktualizowania/usuwania.</span><span class="sxs-lookup"><span data-stu-id="b4875-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="b4875-129">Aby uzyskać więcej informacji, [zobacz Przewodnik: Dostosowywanie zachowania INSERT, Update i DELETE klas](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)jednostek.</span><span class="sxs-lookup"><span data-stu-id="b4875-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="b4875-130">`OnCreated` Metoda jest wywoływana w konstruktorze klasy.</span><span class="sxs-lookup"><span data-stu-id="b4875-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="b4875-131">Klasy jednostek mają trzy metody, które są wywoływane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowisko uruchomieniowe, gdy jednostka została utworzona, załadowana i sprawdzona (gdy `SubmitChanges` jest wywoływana).</span><span class="sxs-lookup"><span data-stu-id="b4875-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="b4875-132">Klasy jednostek mają również dwie metody częściowe dla każdej właściwości, jeden, który jest wywoływany przed ustawieniem właściwości, i jeden, który jest wywoływany po.</span><span class="sxs-lookup"><span data-stu-id="b4875-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="b4875-133">Poniższy przykład kodu pokazuje niektóre metody wygenerowane dla `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="b4875-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="b4875-134">Metody są wywoływane w akcesorze zestawu właściwości, jak pokazano w poniższym przykładzie dla `CustomerID` właściwości:</span><span class="sxs-lookup"><span data-stu-id="b4875-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="b4875-135">W Twojej części klasy napiszesz definicję implementującą metodę.</span><span class="sxs-lookup"><span data-stu-id="b4875-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="b4875-136">W programie Visual Studio, po wpisaniu `partial` , zobaczysz IntelliSense dla definicji metod w drugiej części klasy.</span><span class="sxs-lookup"><span data-stu-id="b4875-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="b4875-137">Aby uzyskać więcej informacji na temat dodawania logiki biznesowej do aplikacji przy użyciu metod częściowych, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="b4875-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="b4875-138">Instrukcje: Dodawanie walidacji do klas jednostek</span><span class="sxs-lookup"><span data-stu-id="b4875-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="b4875-139">Przewodnik: Dostosowywanie zachowania wstawiania, aktualizacji i usuwania dla klas jednostek</span><span class="sxs-lookup"><span data-stu-id="b4875-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="b4875-140">[Przewodnik: Dodawanie walidacji do klas jednostek](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="b4875-140">[Walkthrough: Adding Validation to Entity Classes](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4875-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4875-141">See also</span></span>

- [<span data-ttu-id="b4875-142">Klasy częściowe i metody</span><span class="sxs-lookup"><span data-stu-id="b4875-142">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="b4875-143">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="b4875-143">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="b4875-144">Narzędzia LINQ to SQL Tools w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b4875-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="b4875-145">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="b4875-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
