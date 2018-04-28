---
title: Implementowanie logiki biznesowej (LINQ to SQL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: f519162818739d04cbe66b107911a0e0c30d93bc
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="ec9fb-102">Implementowanie logiki biznesowej (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="ec9fb-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="ec9fb-103">Termin "logiki biznesowej" w tym temacie odnosi się do żadnych reguł niestandardowych lub testów sprawdzania poprawności, które są stosowane do danych, przed jego wstawiony, zaktualizowane lub usunięte z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="ec9fb-104">Logika biznesowa jest czasami nazywany "reguły biznesowe" lub "Logika domeny".</span><span class="sxs-lookup"><span data-stu-id="ec9fb-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="ec9fb-105">W aplikacjach warstwowych zwykle zaprojektowano go jako Warstwa logiczna tak, aby można było jej modyfikować niezależnie od warstwy prezentacji lub Warstwa dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="ec9fb-106">Logika biznesowa może być wywoływany przez Warstwa dostępu do danych, przed lub po żadnych aktualizowania, wstawiania lub usuwania danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="ec9fb-107">Logika biznesowa może być prosty jak sprawdzanie poprawności schematu, aby upewnić się, że typem pola jest niezgodny z typem kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="ec9fb-108">Lub też może składać się z zestawu obiektów wchodzących w interakcję w sposób arbitralnie złożonych.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="ec9fb-109">Zasady mogą być wykonywane jako procedury składowane w bazie danych lub obiektów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="ec9fb-110">Jednak zaimplementowano logiki biznesowej, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umożliwia Użyj klasy częściowe i metody częściowe do oddzielania logiki biznesowej z danych kodu dostępu.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="ec9fb-111">Jak wywołuje logiki biznesowej w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ec9fb-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="ec9fb-112">Podczas generowania klasy jednostki w czasie projektowania, ręcznie lub za pomocą [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub SQLMetal, jest on zdefiniowany jako klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-112">When you generate an entity class at design time, either manually or by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="ec9fb-113">Oznacza to, że w osobnym pliku kodu, można zdefiniować inną część klasę jednostki, która zawiera niestandardowej logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="ec9fb-114">W czasie kompilacji dwie części są scalane w jednej klasy.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="ec9fb-115">Ale jeśli masz można ponownie wygenerować klas jednostek przy użyciu [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] lub SQLMetal, możesz to zrobić, a Twoje część klasy nie zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-115">But if you have to regenerate your entity classes by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="ec9fb-116">Klasy częściowe, które definiują jednostek i <xref:System.Data.Linq.DataContext> zawiera metody częściowe.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="ec9fb-117">Są to punkty rozszerzeń, które można zastosować logiki biznesowej, przed i po nich żadnych aktualizacji, wstawiania lub usuwania jednostki lub właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="ec9fb-118">Metody częściowe mogą być uważane za zdarzenia w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="ec9fb-119">Generator kodu definiuje sygnatury metody i wywołuje metody w get i ustaw metod dostępu do właściwości, `DataContext` konstruktora, a w niektórych przypadkach w tle podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="ec9fb-120">Jednak jeśli nie implementuje określonej metody częściowej, wszystkie odwołania do go, jak i definicja są usuwane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="ec9fb-121">W definicji implementującej zapisu w pliku kodu oddzielnych możesz wykonać, jest wymagany niezależnie od niestandardowej logiki.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="ec9fb-122">Można używać z częściowa samej klasy jako warstwa domeny, lub można wywołać z definicja implementującej metody częściowej w oddzielnych obiektu lub obiektów.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="ec9fb-123">W obu przypadkach logiki biznesowej prawidłowo jest oddzielony od zarówno kod dostępu do danych i kodu warstwy prezentacji.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="ec9fb-124">Bliższe spojrzenie na punktów rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="ec9fb-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="ec9fb-125">W poniższym przykładzie przedstawiono część kod wygenerowany przez [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] dla `DataContext` klasy, która ma dwie tabele: `Customers` i `Orders`.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-125">The following example shows part of the code generated by the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="ec9fb-126">Należy pamiętać, że wstawiania, aktualizowania i usuwania metody są definiowane dla każdej tabeli w klasie.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="ec9fb-127">W przypadku zastosowania Insert, aktualizować i usuwać metody w klasie częściowej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowiska uruchomieniowego wywoła je zamiast metody domyślnej podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="ec9fb-128">Umożliwia zastąpienie zachowania domyślnego dla tworzenia / odczytu / aktualizacji / usuwanie operacji.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="ec9fb-129">Aby uzyskać więcej informacji, zobacz [wskazówki: dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="ec9fb-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="ec9fb-130">`OnCreated` Metoda jest wywoływana w konstruktorze klasy.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="ec9fb-131">Klas jednostek ma trzy metody, które są wywoływane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] środowiska uruchomieniowego podczas tworzenia, załadowane i zweryfikowane jednostki (gdy `SubmitChanges` jest nazywany).</span><span class="sxs-lookup"><span data-stu-id="ec9fb-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="ec9fb-132">Klasy jednostki mają również dwie metody częściowe dla każdej właściwości, który jest wywoływana przed skonfigurowaniem właściwości i jeden, które jest wywoływana po wykonaniu.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="ec9fb-133">Poniższy przykładowy kod przedstawia niektóre generowane dla metody `Customer` klasy:</span><span class="sxs-lookup"><span data-stu-id="ec9fb-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="ec9fb-134">Metody są wywoływane w metodzie dostępu set właściwości, jak pokazano w poniższym przykładzie dla `CustomerID` właściwości:</span><span class="sxs-lookup"><span data-stu-id="ec9fb-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="ec9fb-135">W Twojej część klasy pisania implementującej definicję metody.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="ec9fb-136">W programie Visual Studio po wpisaniu `partial` zostanie wyświetlone IntelliSense dla definicji metody w drugiej klasy.</span><span class="sxs-lookup"><span data-stu-id="ec9fb-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="ec9fb-137">Aby uzyskać więcej informacji na temat dodawania reguł biznesowych do aplikacji przy użyciu metody częściowe zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="ec9fb-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="ec9fb-138">Porady: Dodawanie walidacji do klas jednostek</span><span class="sxs-lookup"><span data-stu-id="ec9fb-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="ec9fb-139">Wskazówki: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek</span><span class="sxs-lookup"><span data-stu-id="ec9fb-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [<span data-ttu-id="ec9fb-140">Wskazówki: Dodawanie walidacji do klas jednostek</span><span class="sxs-lookup"><span data-stu-id="ec9fb-140">Walkthrough: Adding Validation to Entity Classes</span></span>](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a><span data-ttu-id="ec9fb-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec9fb-141">See Also</span></span>  
 [<span data-ttu-id="ec9fb-142">Klasy częściowe i metody</span><span class="sxs-lookup"><span data-stu-id="ec9fb-142">Partial Classes and Methods</span></span>](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)  
 [<span data-ttu-id="ec9fb-143">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="ec9fb-143">Partial Methods</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)  
 [<span data-ttu-id="ec9fb-144">LINQ do SQL narzędzia w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec9fb-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [<span data-ttu-id="ec9fb-145">SqlMetal.exe (narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="ec9fb-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
