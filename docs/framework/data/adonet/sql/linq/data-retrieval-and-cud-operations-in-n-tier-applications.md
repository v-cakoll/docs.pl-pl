---
title: Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: d55c85ae0af567c5af0fd421b612809eaf5bb789
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318432"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="12a8c-102">Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="12a8c-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="12a8c-103">Podczas obiekty obiektów, takich jak klienci i zamówienia klienta za pośrednictwem sieci, te jednostki są odłączone od ich kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="12a8c-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="12a8c-104">Kontekst danych śledzi już zmian lub ich skojarzenia z innymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="12a8c-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="12a8c-105">Nie jest to problem tak długo, jak klienci są tylko do odczytu danych.</span><span class="sxs-lookup"><span data-stu-id="12a8c-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="12a8c-106">Jest również stosunkowo proste umożliwić klientom dodawanie nowych wierszy do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="12a8c-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="12a8c-107">Jednakże, jeśli aplikacja wymaga, aby klienci mogli aktualizować lub usuwać dane, następnie należy dołączyć jednostek do nowy kontekst danych przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12a8c-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="12a8c-108">Ponadto jeśli używasz kontroli optymistycznej współbieżności przy użyciu oryginalnych wartości, następnie należy również sposób zapewnienia bazy danych, jednostki i oryginalna jednostka zmodyfikowana.</span><span class="sxs-lookup"><span data-stu-id="12a8c-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="12a8c-109">`Attach` Udostępniono metody umożliwiające umieść jednostek nowy kontekst danych po mają zostać odłączony.</span><span class="sxs-lookup"><span data-stu-id="12a8c-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="12a8c-110">Nawet wtedy, gdy są serializacji obiektów serwera proxy zamiast [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jednostek, nadal trzeba utworzyć jednostkę w warstwie dostępu do danych (DAL) i dołączyć go do nowego <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby przesłać dane do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="12a8c-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="12a8c-111">jest całkowicie Obojętność o jak jednostki są serializowane.</span><span class="sxs-lookup"><span data-stu-id="12a8c-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="12a8c-112">Aby uzyskać więcej informacji o sposobie używania [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] i SQLMetal narzędzia do generowania klasy, które są możliwe do serializacji przy użyciu Windows Communication Foundation (WCF), zobacz [jak: Umożliwianie serializacji jednostek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="12a8c-112">For more information about how to use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12a8c-113">Wywoływać tylko `Attach` metod na jednostkach nowych lub po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="12a8c-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="12a8c-114">Jedynym sposobem jednostki ma zostać odłączony od jego oryginalnego kontekstu danych jest dla niego serializacji.</span><span class="sxs-lookup"><span data-stu-id="12a8c-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="12a8c-115">Jeśli próbujesz dołączyć undetached jednostki na nowy kontekst danych, a tej jednostki nadal ma być opóźniane modułów ładujących z jego poprzedniego kontekstu danych [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="12a8c-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="12a8c-116">Jednostki z odroczonego modułów ładujących z dwóch kontekstów różnych danych może spowodować niepożądane wyniki, gdy wykonujesz insert, update i operacje usuwania tej jednostki.</span><span class="sxs-lookup"><span data-stu-id="12a8c-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="12a8c-117">Aby uzyskać więcej informacji na temat odroczonego moduły ładujące przeznaczone zobacz [odroczone a ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="12a8c-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="12a8c-118">Trwa pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="12a8c-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="12a8c-119">Wywołanie metody klienta</span><span class="sxs-lookup"><span data-stu-id="12a8c-119">Client Method Call</span></span>  
 <span data-ttu-id="12a8c-120">W poniższych przykładach pokazano przykładowe wywołanie metody z warstwą dal w kliencie Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="12a8c-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="12a8c-121">W tym przykładzie warstwy DAL jest implementowany jako biblioteka usług Windows:</span><span class="sxs-lookup"><span data-stu-id="12a8c-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =   
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =   
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,   
    // the client needs to store them and pass them back to the   
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="12a8c-122">Implementacja warstwy środkowej</span><span class="sxs-lookup"><span data-stu-id="12a8c-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="12a8c-123">Poniższy przykład pokazuje implementację metody interfejsu w warstwie środkowej.</span><span class="sxs-lookup"><span data-stu-id="12a8c-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="12a8c-124">Poniżej przedstawiono dwa główne punkty, należy pamiętać:</span><span class="sxs-lookup"><span data-stu-id="12a8c-124">The following are the two main points to note:</span></span>  
  
-   <span data-ttu-id="12a8c-125"><xref:System.Data.Linq.DataContext> Jest zadeklarowana w zakresie metody.</span><span class="sxs-lookup"><span data-stu-id="12a8c-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
-   <span data-ttu-id="12a8c-126">Metoda ta zwraca <xref:System.Collections.IEnumerable> zbiór rzeczywiste wyniki.</span><span class="sxs-lookup"><span data-stu-id="12a8c-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="12a8c-127">Serializator wykona zapytanie, aby wysłać wyniki do warstwy klienta/prezentacji.</span><span class="sxs-lookup"><span data-stu-id="12a8c-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="12a8c-128">Aby uzyskać dostęp do wyników zapytania lokalnie w środkowej warstwie, można wymusić wykonanie przez wywołanie metody `ToList` lub `ToArray` w zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="12a8c-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="12a8c-129">Możesz powrócić do tej listy lub tablicy jako `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="12a8c-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =   
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();   
}  
```  
  
 <span data-ttu-id="12a8c-130">Wystąpienie kontekstu danych powinny mieć okresu istnienia jeden "jednostka pracy".</span><span class="sxs-lookup"><span data-stu-id="12a8c-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="12a8c-131">W środowisku luźno powiązane jednostki pracy jest zwykle małe, może być jedną optymistycznej transakcji, w tym jedno wywołanie `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="12a8c-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="12a8c-132">Kontekst danych jest utworzony, a usuwane w zakresie metody.</span><span class="sxs-lookup"><span data-stu-id="12a8c-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="12a8c-133">Jeśli jednostka pracy obejmuje wywołania do logiki reguły biznesowej, a następnie ogólnie można zachować `DataContext` wystąpienie dla tej całą operację.</span><span class="sxs-lookup"><span data-stu-id="12a8c-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="12a8c-134">W każdym przypadku `DataContext` wystąpienia nie są przeznaczone do życiu przez długi okresy czasu dla dowolnej liczby transakcji.</span><span class="sxs-lookup"><span data-stu-id="12a8c-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="12a8c-135">Ta metoda zwróci obiekty produktu, ale nie zbiór Order_Detail obiekty, które są skojarzone z każdego produktu.</span><span class="sxs-lookup"><span data-stu-id="12a8c-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="12a8c-136">Użyj <xref:System.Data.Linq.DataLoadOptions> obiekt, aby zmienić to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="12a8c-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="12a8c-137">Aby uzyskać więcej informacji, zobacz [jak: Kontrolowanie, ile powiązane dane są pobierane](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="12a8c-137">For more information, see [How to: Control How Much Related Data Is Retrieved](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="12a8c-138">Wstawianie danych</span><span class="sxs-lookup"><span data-stu-id="12a8c-138">Inserting Data</span></span>  
 <span data-ttu-id="12a8c-139">Aby wstawić nowy obiekt, Warstwa prezentacji po prostu wywołuje odpowiedniej metody w interfejsie warstwy środkowej i przekazuje nowy obiekt do wstawienia.</span><span class="sxs-lookup"><span data-stu-id="12a8c-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="12a8c-140">W niektórych przypadkach może być bardziej wydajne dla klienta do przekazywania tylko niektóre wartości i mieć warstwy środkowej, utworzenia pełnej obiekt.</span><span class="sxs-lookup"><span data-stu-id="12a8c-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="12a8c-141">Implementacja warstwy środkowej</span><span class="sxs-lookup"><span data-stu-id="12a8c-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="12a8c-142">W warstwie środkowej nową <xref:System.Data.Linq.DataContext> jest tworzony, obiekt jest dołączony do <xref:System.Data.Linq.DataContext> przy użyciu <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> metody i obiekt jest wstawiany gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nosi nazwę.</span><span class="sxs-lookup"><span data-stu-id="12a8c-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="12a8c-143">Wyjątki, wywołania zwrotne i warunki błędu mogą być obsługiwane podobnie jak w przypadku każdej innej sytuacji usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="12a8c-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a><span data-ttu-id="12a8c-144">Usuwanie danych</span><span class="sxs-lookup"><span data-stu-id="12a8c-144">Deleting Data</span></span>  
 <span data-ttu-id="12a8c-145">Aby usunąć istniejący obiekt z bazy danych, warstwy prezentacji wywołuje odpowiedniej metody w interfejsie warstwy środkowej i przekazuje jego kopię, którą obejmuje oryginalnych wartości obiektu, który ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="12a8c-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="12a8c-146">Usuń operacje obejmują kontroli optymistycznej współbieżności, a obiekt do usunięcia, najpierw musi być dołączony do nowy kontekst danych.</span><span class="sxs-lookup"><span data-stu-id="12a8c-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="12a8c-147">W tym przykładzie `Boolean` parametr ma wartość `false` do wskazania, że obiekt nie ma sygnatury czasowej (RowVersion).</span><span class="sxs-lookup"><span data-stu-id="12a8c-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="12a8c-148">Jeśli w tabeli bazy danych wygenerować sygnatury czasowe dla każdego rekordu, kontroli współbieżności są dużo prostsze, szczególnie w przypadku klienta.</span><span class="sxs-lookup"><span data-stu-id="12a8c-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="12a8c-149">Po prostu w oryginalnym lub modyfikacji obiektu i ustaw `Boolean` parametr `true`.</span><span class="sxs-lookup"><span data-stu-id="12a8c-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="12a8c-150">W każdym przypadku w warstwie środkowej jest zazwyczaj konieczne catch <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="12a8c-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="12a8c-151">Aby uzyskać więcej informacji na temat obsługi konfliktów optymistycznej współbieżności, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="12a8c-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="12a8c-152">Podczas usuwania obiektów, które mają ograniczenia klucza obcego w tabelach skojarzony, należy najpierw usunąć wszystkie obiekty w jego <xref:System.Data.Linq.EntitySet%601> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="12a8c-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a><span data-ttu-id="12a8c-153">Aktualizowanie danych</span><span class="sxs-lookup"><span data-stu-id="12a8c-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="12a8c-154">obsługiwane są aktualizacje w tych scenariuszach obejmująca optymistycznej współbieżności:</span><span class="sxs-lookup"><span data-stu-id="12a8c-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
-   <span data-ttu-id="12a8c-155">Na podstawie sygnatur czasowych lub numerów RowVersion optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="12a8c-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
-   <span data-ttu-id="12a8c-156">Optymistyczna współbieżność oparte na oryginalnych wartości podzbioru właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="12a8c-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
-   <span data-ttu-id="12a8c-157">Optymistyczna współbieżność oparte na zakończenie jednostkach oryginalnego i modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="12a8c-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="12a8c-158">Można również wykonać aktualizacji lub usuwania w jednostce wraz z jego relacji, na przykład klient i zbiór powiązane obiekty zamówienia.</span><span class="sxs-lookup"><span data-stu-id="12a8c-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="12a8c-159">Po dokonaniu modyfikacji na komputerze klienckim do wykresu obiekty jednostki i ich podrzędnych (`EntitySet`) kolekcji i kontroli optymistycznej współbieżności wymagają oryginalnych wartości, klient musi podać te wartości początkowe dla każdej jednostki i <xref:System.Data.Linq.EntitySet%601> obiekt.</span><span class="sxs-lookup"><span data-stu-id="12a8c-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="12a8c-160">Jeśli chcesz umożliwić klientom zestaw powiązanych aktualizacji, usunięcia i wstawienia w pojedynczym wywołaniu metody, musisz podać klienta sposób, aby wskazać typ operacji do wykonania dla każdej jednostki.</span><span class="sxs-lookup"><span data-stu-id="12a8c-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="12a8c-161">W środkowej warstwie, następnie należy wywołać odpowiednie <xref:System.Data.Linq.ITable.Attach%2A> metody i następnie <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, lub <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach`, do wstawienia) dla każdej jednostki przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="12a8c-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="12a8c-162">Nie pobierać dane z bazy danych jako sposobu uzyskania oryginalnych wartości, przed podjęciem próby aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="12a8c-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="12a8c-163">Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="12a8c-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="12a8c-164">Aby uzyskać szczegółowe informacje o rozwiązywaniu problemów z optymistycznej współbieżności zmian konfliktów, zobacz [jak: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="12a8c-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="12a8c-165">W poniższych przykładach pokazano poszczególnych scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="12a8c-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="12a8c-166">Optymistycznej współbieżności przy użyciu sygnatur czasowych</span><span class="sxs-lookup"><span data-stu-id="12a8c-166">Optimistic concurrency with timestamps</span></span>  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="12a8c-167">Z podzbiorem oryginalnych wartości</span><span class="sxs-lookup"><span data-stu-id="12a8c-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="12a8c-168">W tym podejściu pełną Zserializowany obiekt, wraz z wartości, które mają być modyfikowane zwracane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="12a8c-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a><span data-ttu-id="12a8c-169">Przy użyciu jednostek ukończone</span><span class="sxs-lookup"><span data-stu-id="12a8c-169">With Complete Entities</span></span>  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }   
    }  
}  
```  
  
 <span data-ttu-id="12a8c-170">Aby zaktualizować kolekcję, należy wywołać <xref:System.Data.Linq.ITable.AttachAll%2A> zamiast `Attach`.</span><span class="sxs-lookup"><span data-stu-id="12a8c-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="12a8c-171">Elementy członkowskie oczekiwanej jednostki</span><span class="sxs-lookup"><span data-stu-id="12a8c-171">Expected Entity Members</span></span>  
 <span data-ttu-id="12a8c-172">Jak wspomniano wcześniej, tylko niektóre elementy członkowskie obiektu jednostki są wymagane, należy ustawić przed wywołaniem `Attach` metody.</span><span class="sxs-lookup"><span data-stu-id="12a8c-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="12a8c-173">Elementy członkowskie jednostki, które są wymagane do skonfigurowania musi spełniać następujące kryteria:</span><span class="sxs-lookup"><span data-stu-id="12a8c-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
-   <span data-ttu-id="12a8c-174">Być częścią tożsamości jednostki.</span><span class="sxs-lookup"><span data-stu-id="12a8c-174">Be part of the entity’s identity.</span></span>  
  
-   <span data-ttu-id="12a8c-175">Można oczekiwać od tego, można zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="12a8c-175">Be expected to be modified.</span></span>  
  
-   <span data-ttu-id="12a8c-176">Mieć sygnaturę czasową lub jego <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> atrybut ustawiony wpisując oprócz `Never`.</span><span class="sxs-lookup"><span data-stu-id="12a8c-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="12a8c-177">Jeśli tabela używa wielu znacznika czasu lub wersji do kontroli optymistycznej współbieżności, należy ustawić te elementy Członkowskie przed wywołaniem <xref:System.Data.Linq.ITable.Attach%2A>.</span><span class="sxs-lookup"><span data-stu-id="12a8c-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="12a8c-178">Element członkowski jest dedykowany do optymistycznej współbieżności, gdy sprawdzanie <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość jest ustawiona na wartość true dla atrybutu tej kolumny.</span><span class="sxs-lookup"><span data-stu-id="12a8c-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="12a8c-179">Wszystkie żądane aktualizacje zostaną przesłane tylko wtedy, gdy wersja wartości liczby lub sygnatura czasowa są takie same, w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="12a8c-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="12a8c-180">Element członkowski jest również używany w sprawdzenie optymistycznej współbieżności, tak długo, jak element członkowski nie ma <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> równa `Never`.</span><span class="sxs-lookup"><span data-stu-id="12a8c-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="12a8c-181">Wartość domyślna to `Always` Jeśli wartość nie zostanie określona.</span><span class="sxs-lookup"><span data-stu-id="12a8c-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="12a8c-182">Jeśli jeden z tych elementów członkowskich Brak wymaganej, <xref:System.Data.Linq.ChangeConflictException> jest zgłaszany podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("wiersz nie można odnaleźć lub zmienić").</span><span class="sxs-lookup"><span data-stu-id="12a8c-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="12a8c-183">Stan</span><span class="sxs-lookup"><span data-stu-id="12a8c-183">State</span></span>  
 <span data-ttu-id="12a8c-184">Po jednostki obiekt jest dołączony do <xref:System.Data.Linq.DataContext> wystąpienie, obiekt jest uznawane za w `PossiblyModified` stanu.</span><span class="sxs-lookup"><span data-stu-id="12a8c-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="12a8c-185">Istnieją trzy sposoby, aby wymusić przyłączonego obiektu, aby zostały uznane za `Modified`.</span><span class="sxs-lookup"><span data-stu-id="12a8c-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="12a8c-186">Dołączyć go jako niezmodyfikowany, a następnie bezpośrednio modyfikować pola.</span><span class="sxs-lookup"><span data-stu-id="12a8c-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="12a8c-187">Dołącz go za pomocą <xref:System.Data.Linq.Table%601.Attach%2A> przeciążenia przyjmującego bieżących i oryginalnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="12a8c-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="12a8c-188">Dostarcza śledzenie zmian przy użyciu starej i nowej wartości, dzięki czemu będzie automatycznie wiadomo, które pola zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="12a8c-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="12a8c-189">Dołącz go za pomocą <xref:System.Data.Linq.Table%601.Attach%2A> przeciążenia przyjmującego drugi parametr logiczny (wartość true).</span><span class="sxs-lookup"><span data-stu-id="12a8c-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="12a8c-190">Poinformuje to śledzenie zmian do uwzględnienia w obiekcie modyfikowane bez konieczności podać wszelkie oryginalnych wartości.</span><span class="sxs-lookup"><span data-stu-id="12a8c-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="12a8c-191">W tym podejściu obiekt musi mieć pole wersji/sygnatura czasowa.</span><span class="sxs-lookup"><span data-stu-id="12a8c-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="12a8c-192">Aby uzyskać więcej informacji, zobacz [stany obiektów i śledzenie zmian](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="12a8c-192">For more information, see [Object States and Change-Tracking](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="12a8c-193">Jeśli do obiektu jednostki występuje już w pamięci podręcznej identyfikator o tej samej tożsamości co obiekt dołączony, <xref:System.Data.Linq.DuplicateKeyException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="12a8c-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="12a8c-194">Po dołączeniu z `IEnumerable` zestaw obiektów, <xref:System.Data.Linq.DuplicateKeyException> jest zgłaszany, gdy występuje już istniejącego klucza.</span><span class="sxs-lookup"><span data-stu-id="12a8c-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="12a8c-195">Pozostałe obiekty nie są dołączone.</span><span class="sxs-lookup"><span data-stu-id="12a8c-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a8c-196">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12a8c-196">See also</span></span>

- [<span data-ttu-id="12a8c-197">N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="12a8c-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="12a8c-198">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="12a8c-198">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
