---
title: Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: 5ab829993b8f8faa6dcb91d3f23e8442b8aa95bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148416"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="083f7-102">Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="083f7-102">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>
<span data-ttu-id="083f7-103">Podczas serializacji obiektów jednostki, takich jak Klienci lub Zamówienia do klienta za pośrednictwem sieci, te jednostki są odłączane od ich kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="083f7-103">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="083f7-104">Kontekst danych nie śledzi już ich zmian lub ich skojarzeń z innymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="083f7-104">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="083f7-105">Nie jest to problem, o ile klienci czytają tylko dane.</span><span class="sxs-lookup"><span data-stu-id="083f7-105">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="083f7-106">Jest również stosunkowo proste, aby umożliwić klientom dodawanie nowych wierszy do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="083f7-106">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="083f7-107">Jeśli jednak aplikacja wymaga, aby klienci mogli aktualizować lub usuwać dane, przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>należy dołączyć encje do nowego kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="083f7-107">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="083f7-108">Ponadto jeśli używasz optymistyczne sprawdzanie współbieżności z oryginalnymi wartościami, a następnie będzie również potrzebny sposób, aby zapewnić bazy danych zarówno oryginalnej jednostki i jednostki jako zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="083f7-108">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="083f7-109">Metody `Attach` są dostarczane w celu umożliwienia wprowadzenia jednostek w nowym kontekście danych po ich odłączeniu.</span><span class="sxs-lookup"><span data-stu-id="083f7-109">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="083f7-110">Nawet jeśli szeregowanie obiektów serwera proxy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zamiast jednostek, nadal trzeba skonstruować jednostkę na warstwie dostępu <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>do danych (DAL) i dołączyć go do nowego programu , aby przesłać dane do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="083f7-110">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="083f7-111">jest całkowicie obojętny na sposób serializacji jednostek.</span><span class="sxs-lookup"><span data-stu-id="083f7-111">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="083f7-112">Aby uzyskać więcej informacji na temat używania narzędzi Object Relational Designer i SQLMetal do generowania klas, które można szeregować przy użyciu programu Windows Communication Foundation (WCF), zobacz [Jak: Tworzenie szeregowania jednostek](how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="083f7-112">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="083f7-113">Wywołaj `Attach` tylko metody na nowych lub deserializacji jednostek.</span><span class="sxs-lookup"><span data-stu-id="083f7-113">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="083f7-114">Jedynym sposobem, aby jednostka, która ma być odłączony od oryginalnego kontekstu danych jest dla niego do serializacji.</span><span class="sxs-lookup"><span data-stu-id="083f7-114">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="083f7-115">Jeśli spróbujesz dołączyć nieumożnioną jednostkę do nowego kontekstu danych, a ta [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jednostka nadal ma odroczone moduły ładune z poprzedniego kontekstu danych, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="083f7-115">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="083f7-116">Jednostka z odroczonymi modułami ładującego z dwóch różnych kontekstów danych może spowodować niepożądane wyniki podczas wykonywania operacji wstawiania, aktualizowania i usuwania w tej jednostce.</span><span class="sxs-lookup"><span data-stu-id="083f7-116">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="083f7-117">Aby uzyskać więcej informacji na temat modułów ładujące odroczone, zobacz [Odroczone i natychmiastowe ładowanie](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="083f7-117">For more information about deferred loaders, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="083f7-118">Pobieranie danych</span><span class="sxs-lookup"><span data-stu-id="083f7-118">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="083f7-119">Wywołanie metody klienta</span><span class="sxs-lookup"><span data-stu-id="083f7-119">Client Method Call</span></span>  
 <span data-ttu-id="083f7-120">Poniższe przykłady przedstawiają przykładowe wywołanie metody do warstwy DAL z klienta windows forms.</span><span class="sxs-lookup"><span data-stu-id="083f7-120">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="083f7-121">W tym przykładzie warstwa DAL jest implementowana jako biblioteka usług systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="083f7-121">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
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
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="083f7-122">Implementacja warstwy środkowej</span><span class="sxs-lookup"><span data-stu-id="083f7-122">Middle Tier Implementation</span></span>  
 <span data-ttu-id="083f7-123">W poniższym przykładzie przedstawiono implementację metody interfejsu w warstwie środkowej.</span><span class="sxs-lookup"><span data-stu-id="083f7-123">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="083f7-124">Poniżej znajdują się dwa główne punkty, na które należy zwrócić uwagę:</span><span class="sxs-lookup"><span data-stu-id="083f7-124">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="083f7-125">Jest <xref:System.Data.Linq.DataContext> zadeklarowany w zakresie metody.</span><span class="sxs-lookup"><span data-stu-id="083f7-125">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="083f7-126">Metoda zwraca <xref:System.Collections.IEnumerable> kolekcję rzeczywistych wyników.</span><span class="sxs-lookup"><span data-stu-id="083f7-126">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="083f7-127">Serializator wykona kwerendę, aby wysłać wyniki z powrotem do warstwy klienta/prezentacji.</span><span class="sxs-lookup"><span data-stu-id="083f7-127">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="083f7-128">Aby uzyskać dostęp do wyników kwerendy lokalnie w `ToList` warstwie środkowej, można wymusić wykonanie przez wywołanie lub `ToArray` zmienną kwerendy.</span><span class="sxs-lookup"><span data-stu-id="083f7-128">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="083f7-129">Następnie można zwrócić tę listę `IEnumerable`lub tablicę jako plik .</span><span class="sxs-lookup"><span data-stu-id="083f7-129">You can then return that list or array as an `IEnumerable`.</span></span>  
  
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
  
 <span data-ttu-id="083f7-130">Wystąpienie kontekstu danych powinno mieć okres istnienia jednej "jednostki pracy".</span><span class="sxs-lookup"><span data-stu-id="083f7-130">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="083f7-131">W luźno sprzężonych środowiskach jednostka pracy jest zazwyczaj mała, być może `SubmitChanges`jedna optymistyczna transakcja, w tym jedno wezwanie do .</span><span class="sxs-lookup"><span data-stu-id="083f7-131">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="083f7-132">W związku z tym kontekst danych jest tworzony i usuwany w zakresie metody.</span><span class="sxs-lookup"><span data-stu-id="083f7-132">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="083f7-133">Jeśli jednostka pracy zawiera wywołania logiki reguł biznesowych, ogólnie `DataContext` rzecz biorąc, należy zachować wystąpienie dla tej całej operacji.</span><span class="sxs-lookup"><span data-stu-id="083f7-133">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="083f7-134">W każdym `DataContext` przypadku wystąpienia nie są przeznaczone do utrzymywana przy życiu przez długi okres czasu w dowolnej liczbie transakcji.</span><span class="sxs-lookup"><span data-stu-id="083f7-134">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="083f7-135">Ta metoda zwróci Product obiektów, ale nie kolekcji Order_Detail obiektów, które są skojarzone z każdym Produkt.</span><span class="sxs-lookup"><span data-stu-id="083f7-135">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="083f7-136">Użyj <xref:System.Data.Linq.DataLoadOptions> obiektu, aby zmienić to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="083f7-136">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="083f7-137">Aby uzyskać więcej informacji, zobacz [Jak: Kontrolować ilość powiązanych danych](how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="083f7-137">For more information, see [How to: Control How Much Related Data Is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="083f7-138">Wstawianie danych</span><span class="sxs-lookup"><span data-stu-id="083f7-138">Inserting Data</span></span>  
 <span data-ttu-id="083f7-139">Aby wstawić nowy obiekt, warstwa prezentacji po prostu wywołuje odpowiednią metodę w interfejsie warstwy środkowej i przekazuje w nowym obiekcie do wstawienia.</span><span class="sxs-lookup"><span data-stu-id="083f7-139">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="083f7-140">W niektórych przypadkach może być bardziej wydajne dla klienta do przekazania tylko niektóre wartości i mają warstwy środkowej konstruowania pełnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="083f7-140">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="083f7-141">Implementacja warstwy środkowej</span><span class="sxs-lookup"><span data-stu-id="083f7-141">Middle Tier Implementation</span></span>  
 <span data-ttu-id="083f7-142">Na warstwie środkowej <xref:System.Data.Linq.DataContext> tworzony jest nowy, obiekt jest <xref:System.Data.Linq.DataContext> dołączony <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> do niej za pomocą metody, a obiekt jest wstawiany, gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="083f7-142">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="083f7-143">Wyjątki, wywołania zwrotne i warunki błędu mogą być obsługiwane tak samo, jak w każdym innym scenariuszu usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="083f7-143">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
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
  
## <a name="deleting-data"></a><span data-ttu-id="083f7-144">Usuwanie danych</span><span class="sxs-lookup"><span data-stu-id="083f7-144">Deleting Data</span></span>  
 <span data-ttu-id="083f7-145">Aby usunąć istniejący obiekt z bazy danych, warstwa prezentacji wywołuje odpowiednią metodę w interfejsie warstwy środkowej i przekazuje w swojej kopii, która zawiera oryginalne wartości obiektu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="083f7-145">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="083f7-146">Operacje usuwania obejmują optymistyczne kontrole współbieżności, a obiekt do usunięcia musi najpierw zostać dołączony do nowego kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="083f7-146">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="083f7-147">W tym przykładzie `Boolean` parametr `false` jest ustawiony, aby wskazać, że obiekt nie ma sygnatury czasowej (RowVersion).</span><span class="sxs-lookup"><span data-stu-id="083f7-147">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="083f7-148">Jeśli tabela bazy danych generuje sygnatury czasowe dla każdego rekordu, a następnie kontroli współbieżności są znacznie prostsze, szczególnie dla klienta.</span><span class="sxs-lookup"><span data-stu-id="083f7-148">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="083f7-149">Wystarczy przekazać oryginalny lub zmodyfikowany obiekt i `Boolean` ustawić `true`parametr na .</span><span class="sxs-lookup"><span data-stu-id="083f7-149">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="083f7-150">W każdym razie na poziomie środkowym zazwyczaj konieczne <xref:System.Data.Linq.ChangeConflictException>jest złapanie pliku .</span><span class="sxs-lookup"><span data-stu-id="083f7-150">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="083f7-151">Aby uzyskać więcej informacji na temat obsługi optymistycznych konfliktów współbieżności, zobacz [Optymistyczna współbieżność: Przegląd](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="083f7-151">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="083f7-152">Podczas usuwania jednostek, które mają ograniczenia klucza obcego w skojarzonych <xref:System.Data.Linq.EntitySet%601> tabelach, należy najpierw usunąć wszystkie obiekty w jego kolekcji.</span><span class="sxs-lookup"><span data-stu-id="083f7-152">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
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
  
## <a name="updating-data"></a><span data-ttu-id="083f7-153">Aktualizowanie danych</span><span class="sxs-lookup"><span data-stu-id="083f7-153">Updating Data</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="083f7-154">obsługuje aktualizacje w tych scenariuszach obejmujących optymistyczną współbieżność:</span><span class="sxs-lookup"><span data-stu-id="083f7-154">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="083f7-155">Optymistyczna współbieżność na podstawie sygnatur czasowych lub numerów RowVersion.</span><span class="sxs-lookup"><span data-stu-id="083f7-155">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="083f7-156">Optymistyczna współbieżność oparta na oryginalnych wartościach podzbioru właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="083f7-156">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="083f7-157">Optymistyczna współbieżność oparta na kompletnych oryginalnych i zmodyfikowanych jednostkach.</span><span class="sxs-lookup"><span data-stu-id="083f7-157">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="083f7-158">Można również wykonywać aktualizacje lub usuwa na jednostki wraz z jego relacji, na przykład Klient i kolekcji skojarzonych z Zamówienie obiektów.</span><span class="sxs-lookup"><span data-stu-id="083f7-158">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="083f7-159">Po wprowadzeniu zmian na kliencie do wykresu obiektów jednostki i ich kolekcji podrzędnych (`EntitySet`) i optymistyczne kontrole współbieżności <xref:System.Data.Linq.EntitySet%601> wymagają oryginalnych wartości, klient musi podać te oryginalne wartości dla każdej jednostki i obiektu.</span><span class="sxs-lookup"><span data-stu-id="083f7-159">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="083f7-160">Jeśli chcesz włączyć klientów do zestawu powiązanych aktualizacji, usuwa i wstawia w wywołaniu pojedynczej metody, należy podać klientowi sposób, aby wskazać, jaki typ operacji do wykonania na każdej jednostce.</span><span class="sxs-lookup"><span data-stu-id="083f7-160">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="083f7-161">Na warstwie środkowej należy następnie <xref:System.Data.Linq.ITable.Attach%2A> wywołać <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>odpowiednią <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>metodę, a następnie , lub <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach` <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, dla wstawień) dla każdej jednostki przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="083f7-161">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="083f7-162">Nie należy pobierać danych z bazy danych jako sposób uzyskania oryginalnych wartości przed wypróbowaniem aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="083f7-162">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="083f7-163">Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [Optymistyczna współbieżność: Przegląd](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="083f7-163">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="083f7-164">Aby uzyskać szczegółowe informacje na temat rozwiązywania konfliktów zmiany współbieżności optymistycznej, zobacz [Jak: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="083f7-164">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="083f7-165">Poniższe przykłady pokazują każdy scenariusz:</span><span class="sxs-lookup"><span data-stu-id="083f7-165">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="083f7-166">Optymistyczna współbieżność z sygnaturami czasowymi</span><span class="sxs-lookup"><span data-stu-id="083f7-166">Optimistic concurrency with timestamps</span></span>  
  
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
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="083f7-167">Z podzbiorem wartości oryginalnych</span><span class="sxs-lookup"><span data-stu-id="083f7-167">With Subset of Original Values</span></span>  
 <span data-ttu-id="083f7-168">W tym podejściu klient zwraca kompletny serializowany obiekt wraz z wartościami, które mają zostać zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="083f7-168">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
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
  
### <a name="with-complete-entities"></a><span data-ttu-id="083f7-169">Z kompletnymi jednostkami</span><span class="sxs-lookup"><span data-stu-id="083f7-169">With Complete Entities</span></span>  
  
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
  
 <span data-ttu-id="083f7-170">Aby zaktualizować kolekcję, <xref:System.Data.Linq.ITable.AttachAll%2A> zadzwoń `Attach`zamiast .</span><span class="sxs-lookup"><span data-stu-id="083f7-170">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="083f7-171">Oczekiwani członkowie jednostki</span><span class="sxs-lookup"><span data-stu-id="083f7-171">Expected Entity Members</span></span>  
 <span data-ttu-id="083f7-172">Jak wspomniano wcześniej, tylko niektóre elementy członkowskie obiektu jednostki są `Attach` wymagane do zestawu przed wywołaniem metod.</span><span class="sxs-lookup"><span data-stu-id="083f7-172">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="083f7-173">Elementy członkowskie jednostki, które muszą zostać ustawione, muszą spełniać następujące kryteria:</span><span class="sxs-lookup"><span data-stu-id="083f7-173">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="083f7-174">Bądź częścią tożsamości jednostki.</span><span class="sxs-lookup"><span data-stu-id="083f7-174">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="083f7-175">Należy się spodziewać, że zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="083f7-175">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="083f7-176">Bądź sygnaturą <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> czasową lub mieć `Never`jego atrybut ustawiony na coś poza .</span><span class="sxs-lookup"><span data-stu-id="083f7-176">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="083f7-177">Jeśli tabela używa sygnatury czasowej lub numeru wersji do optymistycznego sprawdzania <xref:System.Data.Linq.ITable.Attach%2A>współbieżności, należy ustawić tych członków przed wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="083f7-177">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="083f7-178">Element członkowski jest przeznaczony do sprawdzania współbieżności optymistyczne, gdy <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość jest ustawiona na true w tym atrybutu Column.</span><span class="sxs-lookup"><span data-stu-id="083f7-178">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="083f7-179">Wszelkie żądane aktualizacje zostaną przesłane tylko wtedy, gdy numer wersji lub wartości sygnatury czasowej są takie same w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="083f7-179">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="083f7-180">Element członkowski jest również używany w optymistycznym czeku współbieżności, o ile element członkowski nie ma <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ustawionego na `Never`.</span><span class="sxs-lookup"><span data-stu-id="083f7-180">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="083f7-181">Wartość domyślna `Always` jest, jeśli nie określono żadnej innej wartości.</span><span class="sxs-lookup"><span data-stu-id="083f7-181">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="083f7-182">Jeśli brakuje jednego z tych wymaganych <xref:System.Data.Linq.ChangeConflictException> elementów <xref:System.Data.Linq.DataContext.SubmitChanges%2A> członkowskich, a jest wyrzucany podczas ("Wiersz nie znaleziono lub zmieniono").</span><span class="sxs-lookup"><span data-stu-id="083f7-182">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="083f7-183">Stan</span><span class="sxs-lookup"><span data-stu-id="083f7-183">State</span></span>  
 <span data-ttu-id="083f7-184">Po dołączeniu obiektu jednostki <xref:System.Data.Linq.DataContext> do wystąpienia, obiekt jest `PossiblyModified` uważany za w stanie.</span><span class="sxs-lookup"><span data-stu-id="083f7-184">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="083f7-185">Istnieją trzy sposoby na zmuszenie do `Modified`rozważenia dołączonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="083f7-185">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="083f7-186">Dołącz go jako niezmodyfikowany, a następnie bezpośrednio zmodyfikuj pola.</span><span class="sxs-lookup"><span data-stu-id="083f7-186">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="083f7-187">Dołącz go <xref:System.Data.Linq.Table%601.Attach%2A> z przeciążeniem, które przyjmuje bieżące i oryginalne wystąpienia obiektów.</span><span class="sxs-lookup"><span data-stu-id="083f7-187">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="083f7-188">Dostarcza to modułowi śledzenia zmian ze starymi i nowymi wartościami, dzięki czemu automatycznie będzie wiedział, które pola uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="083f7-188">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="083f7-189">Dołącz go <xref:System.Data.Linq.Table%601.Attach%2A> z przeciążeniem, które przyjmuje drugi parametr logiczny (ustawiony na true).</span><span class="sxs-lookup"><span data-stu-id="083f7-189">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="083f7-190">Spowoduje to, że śledzenie zmian zostanie rozważone jako zmodyfikowany obiekt bez konieczności posyłania żadnych oryginalnych wartości.</span><span class="sxs-lookup"><span data-stu-id="083f7-190">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="083f7-191">W tym podejściu obiekt musi mieć pole sygnatury czasowej wersji/sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="083f7-191">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="083f7-192">Aby uzyskać więcej informacji, zobacz [Stany obiektów i Śledzenie zmian](object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="083f7-192">For more information, see [Object States and Change-Tracking](object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="083f7-193">Jeśli obiekt jednostki już występuje w pamięci podręcznej identyfikatorów o <xref:System.Data.Linq.DuplicateKeyException> tej samej tożsamości co obiekt, który jest dołączony, a jest generowany.</span><span class="sxs-lookup"><span data-stu-id="083f7-193">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="083f7-194">Po dołączeniu `IEnumerable` z zestawem <xref:System.Data.Linq.DuplicateKeyException> obiektów, a jest generowany, gdy już istniejący klucz jest obecny.</span><span class="sxs-lookup"><span data-stu-id="083f7-194">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="083f7-195">Pozostałe obiekty nie są dołączone.</span><span class="sxs-lookup"><span data-stu-id="083f7-195">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083f7-196">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="083f7-196">See also</span></span>

- [<span data-ttu-id="083f7-197">N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="083f7-197">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="083f7-198">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="083f7-198">Background Information</span></span>](background-information.md)
