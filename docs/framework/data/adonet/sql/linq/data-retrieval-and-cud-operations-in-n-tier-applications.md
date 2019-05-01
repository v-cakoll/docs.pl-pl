---
title: Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: d55c85ae0af567c5af0fd421b612809eaf5bb789
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037924"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)
Podczas obiekty obiektów, takich jak klienci i zamówienia klienta za pośrednictwem sieci, te jednostki są odłączone od ich kontekstu danych. Kontekst danych śledzi już zmian lub ich skojarzenia z innymi obiektami. Nie jest to problem tak długo, jak klienci są tylko do odczytu danych. Jest również stosunkowo proste umożliwić klientom dodawanie nowych wierszy do bazy danych. Jednakże, jeśli aplikacja wymaga, aby klienci mogli aktualizować lub usuwać dane, następnie należy dołączyć jednostek do nowy kontekst danych przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>. Ponadto jeśli używasz kontroli optymistycznej współbieżności przy użyciu oryginalnych wartości, następnie należy również sposób zapewnienia bazy danych, jednostki i oryginalna jednostka zmodyfikowana. `Attach` Udostępniono metody umożliwiające umieść jednostek nowy kontekst danych po mają zostać odłączony.  
  
 Nawet wtedy, gdy są serializacji obiektów serwera proxy zamiast [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jednostek, nadal trzeba utworzyć jednostkę w warstwie dostępu do danych (DAL) i dołączyć go do nowego <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby przesłać dane do bazy danych.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest całkowicie Obojętność o jak jednostki są serializowane. Aby uzyskać więcej informacji o sposobie używania [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] i SQLMetal narzędzia do generowania klasy, które są możliwe do serializacji przy użyciu Windows Communication Foundation (WCF), zobacz [jak: Umożliwianie serializacji jednostek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).  
  
> [!NOTE]
>  Wywoływać tylko `Attach` metod na jednostkach nowych lub po deserializacji. Jedynym sposobem jednostki ma zostać odłączony od jego oryginalnego kontekstu danych jest dla niego serializacji. Jeśli próbujesz dołączyć undetached jednostki na nowy kontekst danych, a tej jednostki nadal ma być opóźniane modułów ładujących z jego poprzedniego kontekstu danych [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zostanie zgłoszony wyjątek. Jednostki z odroczonego modułów ładujących z dwóch kontekstów różnych danych może spowodować niepożądane wyniki, gdy wykonujesz insert, update i operacje usuwania tej jednostki. Aby uzyskać więcej informacji na temat odroczonego moduły ładujące przeznaczone zobacz [odroczone a ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Trwa pobieranie danych  
  
### <a name="client-method-call"></a>Wywołanie metody klienta  
 W poniższych przykładach pokazano przykładowe wywołanie metody z warstwą dal w kliencie Windows Forms. W tym przykładzie warstwy DAL jest implementowany jako biblioteka usług Windows:  
  
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
  
### <a name="middle-tier-implementation"></a>Implementacja warstwy środkowej  
 Poniższy przykład pokazuje implementację metody interfejsu w warstwie środkowej. Poniżej przedstawiono dwa główne punkty, należy pamiętać:  
  
- <xref:System.Data.Linq.DataContext> Jest zadeklarowana w zakresie metody.  
  
- Metoda ta zwraca <xref:System.Collections.IEnumerable> zbiór rzeczywiste wyniki. Serializator wykona zapytanie, aby wysłać wyniki do warstwy klienta/prezentacji. Aby uzyskać dostęp do wyników zapytania lokalnie w środkowej warstwie, można wymusić wykonanie przez wywołanie metody `ToList` lub `ToArray` w zmiennej zapytania. Możesz powrócić do tej listy lub tablicy jako `IEnumerable`.  
  
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
  
 Wystąpienie kontekstu danych powinny mieć okresu istnienia jeden "jednostka pracy". W środowisku luźno powiązane jednostki pracy jest zwykle małe, może być jedną optymistycznej transakcji, w tym jedno wywołanie `SubmitChanges`. Kontekst danych jest utworzony, a usuwane w zakresie metody. Jeśli jednostka pracy obejmuje wywołania do logiki reguły biznesowej, a następnie ogólnie można zachować `DataContext` wystąpienie dla tej całą operację. W każdym przypadku `DataContext` wystąpienia nie są przeznaczone do życiu przez długi okresy czasu dla dowolnej liczby transakcji.  
  
 Ta metoda zwróci obiekty produktu, ale nie zbiór Order_Detail obiekty, które są skojarzone z każdego produktu. Użyj <xref:System.Data.Linq.DataLoadOptions> obiekt, aby zmienić to zachowanie domyślne. Aby uzyskać więcej informacji, zobacz [jak: Kontrolowanie, ile powiązane dane są pobierane](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).  
  
## <a name="inserting-data"></a>Wstawianie danych  
 Aby wstawić nowy obiekt, Warstwa prezentacji po prostu wywołuje odpowiedniej metody w interfejsie warstwy środkowej i przekazuje nowy obiekt do wstawienia. W niektórych przypadkach może być bardziej wydajne dla klienta do przekazywania tylko niektóre wartości i mieć warstwy środkowej, utworzenia pełnej obiekt.  
  
### <a name="middle-tier-implementation"></a>Implementacja warstwy środkowej  
 W warstwie środkowej nową <xref:System.Data.Linq.DataContext> jest tworzony, obiekt jest dołączony do <xref:System.Data.Linq.DataContext> przy użyciu <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> metody i obiekt jest wstawiany gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nosi nazwę. Wyjątki, wywołania zwrotne i warunki błędu mogą być obsługiwane podobnie jak w przypadku każdej innej sytuacji usługi sieci Web.  
  
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
  
## <a name="deleting-data"></a>Usuwanie danych  
 Aby usunąć istniejący obiekt z bazy danych, warstwy prezentacji wywołuje odpowiedniej metody w interfejsie warstwy środkowej i przekazuje jego kopię, którą obejmuje oryginalnych wartości obiektu, który ma zostać usunięty.  
  
 Usuń operacje obejmują kontroli optymistycznej współbieżności, a obiekt do usunięcia, najpierw musi być dołączony do nowy kontekst danych. W tym przykładzie `Boolean` parametr ma wartość `false` do wskazania, że obiekt nie ma sygnatury czasowej (RowVersion). Jeśli w tabeli bazy danych wygenerować sygnatury czasowe dla każdego rekordu, kontroli współbieżności są dużo prostsze, szczególnie w przypadku klienta. Po prostu w oryginalnym lub modyfikacji obiektu i ustaw `Boolean` parametr `true`. W każdym przypadku w warstwie środkowej jest zazwyczaj konieczne catch <xref:System.Data.Linq.ChangeConflictException>. Aby uzyskać więcej informacji na temat obsługi konfliktów optymistycznej współbieżności, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Podczas usuwania obiektów, które mają ograniczenia klucza obcego w tabelach skojarzony, należy najpierw usunąć wszystkie obiekty w jego <xref:System.Data.Linq.EntitySet%601> kolekcji.  
  
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
  
## <a name="updating-data"></a>Aktualizowanie danych  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługiwane są aktualizacje w tych scenariuszach obejmująca optymistycznej współbieżności:  
  
- Na podstawie sygnatur czasowych lub numerów RowVersion optymistycznej współbieżności.  
  
- Optymistyczna współbieżność oparte na oryginalnych wartości podzbioru właściwości jednostki.  
  
- Optymistyczna współbieżność oparte na zakończenie jednostkach oryginalnego i modyfikacji.  
  
 Można również wykonać aktualizacji lub usuwania w jednostce wraz z jego relacji, na przykład klient i zbiór powiązane obiekty zamówienia. Po dokonaniu modyfikacji na komputerze klienckim do wykresu obiekty jednostki i ich podrzędnych (`EntitySet`) kolekcji i kontroli optymistycznej współbieżności wymagają oryginalnych wartości, klient musi podać te wartości początkowe dla każdej jednostki i <xref:System.Data.Linq.EntitySet%601> obiekt. Jeśli chcesz umożliwić klientom zestaw powiązanych aktualizacji, usunięcia i wstawienia w pojedynczym wywołaniu metody, musisz podać klienta sposób, aby wskazać typ operacji do wykonania dla każdej jednostki. W środkowej warstwie, następnie należy wywołać odpowiednie <xref:System.Data.Linq.ITable.Attach%2A> metody i następnie <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, lub <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach`, do wstawienia) dla każdej jednostki przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Nie pobierać dane z bazy danych jako sposobu uzyskania oryginalnych wartości, przed podjęciem próby aktualizacji.  
  
 Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md). Aby uzyskać szczegółowe informacje o rozwiązywaniu problemów z optymistycznej współbieżności zmian konfliktów, zobacz [jak: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 W poniższych przykładach pokazano poszczególnych scenariuszy:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Optymistycznej współbieżności przy użyciu sygnatur czasowych  
  
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
  
### <a name="with-subset-of-original-values"></a>Z podzbiorem oryginalnych wartości  
 W tym podejściu pełną Zserializowany obiekt, wraz z wartości, które mają być modyfikowane zwracane przez klienta.  
  
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
  
### <a name="with-complete-entities"></a>Przy użyciu jednostek ukończone  
  
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
  
 Aby zaktualizować kolekcję, należy wywołać <xref:System.Data.Linq.ITable.AttachAll%2A> zamiast `Attach`.  
  
### <a name="expected-entity-members"></a>Elementy członkowskie oczekiwanej jednostki  
 Jak wspomniano wcześniej, tylko niektóre elementy członkowskie obiektu jednostki są wymagane, należy ustawić przed wywołaniem `Attach` metody. Elementy członkowskie jednostki, które są wymagane do skonfigurowania musi spełniać następujące kryteria:  
  
- Być częścią tożsamości jednostki.  
  
- Można oczekiwać od tego, można zmodyfikować.  
  
- Mieć sygnaturę czasową lub jego <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> atrybut ustawiony wpisując oprócz `Never`.  
  
 Jeśli tabela używa wielu znacznika czasu lub wersji do kontroli optymistycznej współbieżności, należy ustawić te elementy Członkowskie przed wywołaniem <xref:System.Data.Linq.ITable.Attach%2A>. Element członkowski jest dedykowany do optymistycznej współbieżności, gdy sprawdzanie <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość jest ustawiona na wartość true dla atrybutu tej kolumny. Wszystkie żądane aktualizacje zostaną przesłane tylko wtedy, gdy wersja wartości liczby lub sygnatura czasowa są takie same, w bazie danych.  
  
 Element członkowski jest również używany w sprawdzenie optymistycznej współbieżności, tak długo, jak element członkowski nie ma <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> równa `Never`. Wartość domyślna to `Always` Jeśli wartość nie zostanie określona.  
  
 Jeśli jeden z tych elementów członkowskich Brak wymaganej, <xref:System.Data.Linq.ChangeConflictException> jest zgłaszany podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("wiersz nie można odnaleźć lub zmienić").  
  
### <a name="state"></a>Stan  
 Po jednostki obiekt jest dołączony do <xref:System.Data.Linq.DataContext> wystąpienie, obiekt jest uznawane za w `PossiblyModified` stanu. Istnieją trzy sposoby, aby wymusić przyłączonego obiektu, aby zostały uznane za `Modified`.  
  
1. Dołączyć go jako niezmodyfikowany, a następnie bezpośrednio modyfikować pola.  
  
2. Dołącz go za pomocą <xref:System.Data.Linq.Table%601.Attach%2A> przeciążenia przyjmującego bieżących i oryginalnych obiektów. Dostarcza śledzenie zmian przy użyciu starej i nowej wartości, dzięki czemu będzie automatycznie wiadomo, które pola zostały zmienione.  
  
3. Dołącz go za pomocą <xref:System.Data.Linq.Table%601.Attach%2A> przeciążenia przyjmującego drugi parametr logiczny (wartość true). Poinformuje to śledzenie zmian do uwzględnienia w obiekcie modyfikowane bez konieczności podać wszelkie oryginalnych wartości. W tym podejściu obiekt musi mieć pole wersji/sygnatura czasowa.  
  
 Aby uzyskać więcej informacji, zobacz [stany obiektów i śledzenie zmian](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).  
  
 Jeśli do obiektu jednostki występuje już w pamięci podręcznej identyfikator o tej samej tożsamości co obiekt dołączony, <xref:System.Data.Linq.DuplicateKeyException> zgłaszany.  
  
 Po dołączeniu z `IEnumerable` zestaw obiektów, <xref:System.Data.Linq.DuplicateKeyException> jest zgłaszany, gdy występuje już istniejącego klucza. Pozostałe obiekty nie są dołączone.  
  
## <a name="see-also"></a>Zobacz także

- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
