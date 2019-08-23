---
title: Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: ccd30e3d1b0d716b6393fdb093d47cddf7302f8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963272"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)
Podczas serializacji obiektów jednostek, takich jak klienci lub zamówienia, do klienta za pośrednictwem sieci, te jednostki są odłączone od kontekstu danych. W kontekście danych nie są już śledzone zmiany ani ich skojarzenia z innymi obiektami. Nie jest to problem, o ile klienci odczytują tylko dane. Umożliwia to również stosunkowo proste umożliwienie klientom dodawania nowych wierszy do bazy danych. Jeśli jednak aplikacja wymaga, aby klienci mogli zaktualizować lub usunąć dane, należy dołączyć jednostki do nowego kontekstu danych przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>. Ponadto, jeśli używasz optymistycznej kontroli współbieżności z oryginalnymi wartościami, konieczne będzie również udostępnienie bazy danych zarówno oryginalnej jednostki, jak i jednostki jako zmienionej. Dostępne `Attach` są metody umożliwiające umieszczenie jednostek w nowym kontekście danych po odłączeniu.  
  
 Nawet w przypadku serializowania obiektów proxy zamiast [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jednostek nadal trzeba utworzyć jednostkę w warstwie dostępu do danych (dal) i dołączyć ją do nowej <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby przesłać dane do bazy danych.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie różni się w zależności od tego, jak jednostki są serializowane. Aby uzyskać więcej informacji na temat używania Object Relational Designer i narzędzi SQLMetal do generowania klas, które można serializować przy użyciu Windows Communication Foundation (WCF), zobacz [How to: Utwórz obiekty do](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)serializacji.  
  
> [!NOTE]
> Wywołaj `Attach` metody tylko dla nowych lub deserializowanych jednostek. Jedynym sposobem odłączenia jednostki od jej oryginalnego kontekstu danych jest jego Serializowanie. Jeśli spróbujesz dołączyć odłączoną jednostkę do nowego kontekstu danych, a jednostka nadal ma odroczone ładowarki z poprzedniego kontekstu danych, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] program wygeneruje wyjątek. Jednostka z odroczonymi ładowarkami z dwóch różnych kontekstów danych może spowodować niepożądane wyniki podczas wykonywania operacji INSERT, Update i DELETE na tej jednostce. Aby uzyskać więcej informacji na temat odroczonych modułów ładujących, zobacz odroczone względem [natychmiastowego ładowania](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Trwa pobieranie danych  
  
### <a name="client-method-call"></a>Wywołanie metody klienta  
 W poniższych przykładach pokazano przykładowe wywołanie metody do DAL z klienta Windows Forms. W tym przykładzie DAL jest zaimplementowana jako biblioteka usługi systemu Windows:  
  
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
 W poniższym przykładzie przedstawiono implementację metody interfejsu w warstwie środkowej. Poniżej przedstawiono dwa główne punkty, do których należy zwrócić uwagę:  
  
- <xref:System.Data.Linq.DataContext> Jest zadeklarowany w zakresie metody.  
  
- Metoda zwraca <xref:System.Collections.IEnumerable> kolekcję rzeczywistych wyników. Serializator wykona zapytanie w celu wysłania wyników z powrotem do warstwy klienta/prezentacji. Aby uzyskać dostęp do wyników zapytania lokalnie w warstwie środkowej, można wymusić wykonanie, `ToList` wywołując `ToArray` lub na zmiennej zapytania. Następnie można zwrócić tę listę lub tablicę jako `IEnumerable`.  
  
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
  
 Wystąpienie kontekstu danych powinno mieć okres istnienia jednego "jednostki pracy". W przypadku luźno powiązanego środowiska jednostka pracy jest zwykle mała, być może jedną optymistyczną transakcję, łącznie z pojedynczym wywołaniem do `SubmitChanges`. W związku z tym, kontekst danych jest tworzony i usuwany w zakresie metody. Jeśli jednostka pracy obejmuje wywołania logiki reguł firmy, a następnie należy zachować to `DataContext` wystąpienie dla całej operacji. W każdym przypadku `DataContext` wystąpienia nie są przeznaczone do utrzymania przez długi okres czasu między dowolnymi liczbami transakcji.  
  
 Ta metoda zwróci obiekty produktu, ale nie zbiera obiektów Order_Detail, które są skojarzone z poszczególnymi produktami. Użyj obiektu <xref:System.Data.Linq.DataLoadOptions> , aby zmienić to zachowanie domyślne. Aby uzyskać więcej informacji, zobacz [jak: Kontrolowanie ilości pobieranych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md)powiązanych danych.  
  
## <a name="inserting-data"></a>Wstawianie danych  
 Aby wstawić nowy obiekt, warstwa prezentacji po prostu wywołuje odpowiednią metodę w interfejsie warstwy środkowej i przekazuje nowy obiekt do wstawienia. W niektórych przypadkach może być bardziej wydajne, aby klient mógł przekazać tylko niektóre wartości i utworzyć pełny obiekt dla warstwy środkowej.  
  
### <a name="middle-tier-implementation"></a>Implementacja warstwy środkowej  
 W warstwie środkowej <xref:System.Data.Linq.DataContext> tworzony jest nowy obiekt, który jest dołączany <xref:System.Data.Linq.DataContext> do przy użyciu <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> metody, a obiekt jest wstawiany, gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana. Wyjątki, wywołania zwrotne i warunki błędów mogą być obsługiwane tak samo jak w każdym innym scenariuszu usługi sieci Web.  
  
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
 Aby usunąć istniejący obiekt z bazy danych, warstwa prezentacji wywołuje odpowiednią metodę w interfejsie warstwy środkowej i przekazuje jej kopię zawierającą oryginalne wartości obiektu do usunięcia.  
  
 Operacje usuwania obejmują optymistyczne sprawdzanie współbieżności, a obiekt, który ma zostać usunięty, musi być najpierw dołączony do nowego kontekstu danych. W tym przykładzie `Boolean` parametr jest ustawiony na `false` , aby wskazać, że obiekt nie ma sygnatury czasowej (rowversion). Jeśli tabela bazy danych generuje sygnatury czasowe dla każdego rekordu, kontrole współbieżności są znacznie prostsze, szczególnie dla klienta. Po prostu przekaż obiekt oryginalny lub zmodyfikowany, a następnie ustaw `Boolean` parametr na. `true` W każdym przypadku w warstwie środkowej zwykle konieczne jest przechwycenie <xref:System.Data.Linq.ChangeConflictException>. Aby uzyskać więcej informacji o sposobie obsługi optymistycznych konfliktów współbieżności, [Zobacz optymistyczne współbieżność: Przegląd](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Podczas usuwania jednostek, które mają ograniczenia klucza obcego dla skojarzonych tabel, należy najpierw usunąć wszystkie obiekty z <xref:System.Data.Linq.EntitySet%601> kolekcji.  
  
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
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje aktualizacje w tych scenariuszach obejmujących optymistyczną współbieżność:  
  
- Optymistyczne współbieżność na podstawie znaczników czasu lub RowVersion.  
  
- Optymistyczna współbieżność oparta na oryginalnych wartościach podzbioru właściwości jednostki.  
  
- Optymistyczna współbieżność oparta na kompletnych i zmodyfikowanych jednostkach.  
  
 Można również wykonywać aktualizacje lub usunięcia w jednostce wraz z jej relacjami, na przykład klienta i kolekcji skojarzonych z nimi obiektów Order. Po wprowadzeniu modyfikacji klienta do grafu obiektów jednostki i ich kolekcji podrzędnych (`EntitySet`), a optymistyczne kontrole współbieżności wymagają oryginalnych wartości, klient musi podać te oryginalne wartości dla każdej jednostki i <xref:System.Data.Linq.EntitySet%601> Stream. Jeśli chcesz umożliwić klientom tworzenie zestawu powiązanych aktualizacji, usunięć i wstawek w jednym wywołaniu metody, musisz zapewnić klientowi możliwość wskazania, jaki typ operacji ma być wykonywany dla każdej jednostki. W warstwie środkowej należy wywołać odpowiednią <xref:System.Data.Linq.ITable.Attach%2A> metodę, a <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>następnie <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, lub <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach`, dla wstawek) dla każdej jednostki przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Nie pobieraj danych z bazy danych jako metody uzyskiwania oryginalnych wartości przed rozpoczęciem aktualizacji.  
  
 Aby uzyskać więcej informacji na temat współbieżności optymistycznej, zobacz [optymistyczne współbieżność: Przegląd](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md). Aby uzyskać szczegółowe informacje dotyczące rozpoznawania optymistycznych konfliktów zmian współbieżności, [zobacz How to: Zarządzanie konfliktami](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)zmian.  
  
 W poniższych przykładach pokazano każdy scenariusz:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Optymistyczne współbieżność z sygnaturami czasowymi  
  
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
 W tym podejściu klient zwraca kompletny serializowany obiekt wraz z wartościami do zmodyfikowania.  
  
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
  
### <a name="with-complete-entities"></a>Z kompletnymi jednostkami  
  
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
  
 Aby zaktualizować kolekcję, należy wywołać <xref:System.Data.Linq.ITable.AttachAll%2A> `Attach`zamiast.  
  
### <a name="expected-entity-members"></a>Oczekiwane elementy członkowskie jednostki  
 Jak wspomniano wcześniej, należy ustawić tylko pewne elementy członkowskie obiektu Entity przed wywołaniem `Attach` metod. Elementy członkowskie jednostki, które są wymagane do ustawienia, muszą spełniać następujące kryteria:  
  
- Należy do tożsamości jednostki.  
  
- Powinien być modyfikowany.  
  
- Być sygnaturą czasową lub <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> mieć jej atrybut ustawiony na `Never`coś poza.  
  
 Jeśli w tabeli jest używany znacznik czasu lub numer wersji dla optymistycznej kontroli współbieżności, należy ustawić tych członków przed wywołaniem <xref:System.Data.Linq.ITable.Attach%2A>. Element członkowski jest przeznaczony do sprawdzania współbieżności optymistycznej, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> gdy właściwość ma wartość true dla tego atrybutu kolumny. Wszelkie wymagane aktualizacje zostaną przesłane tylko wtedy, gdy numer wersji lub wartości sygnatury czasowej są takie same w bazie danych.  
  
 Członek jest również używany w jednooptymistycznej kontroli współbieżności, tak długo, jak element członkowski nie <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ma `Never`ustawionej wartości. Wartość domyślna to `Always` Jeśli nie określono żadnej innej wartości.  
  
 Jeśli brakuje któregokolwiek z tych wymaganych składowych, <xref:System.Data.Linq.ChangeConflictException> zostanie zgłoszony w trakcie <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("nie znaleziono wiersza lub zmieniono").  
  
### <a name="state"></a>Stan  
 Po dołączeniu obiektu jednostki do <xref:System.Data.Linq.DataContext> wystąpienia obiekt jest uznawany za `PossiblyModified` w stanie. Istnieją trzy sposoby wymuszenia przyłączonego obiektu `Modified`.  
  
1. Dołącz go jako niemodyfikowany, a następnie bezpośrednio zmodyfikuj pola.  
  
2. Dołącz ją z <xref:System.Data.Linq.Table%601.Attach%2A> przeciążeniem, które pobiera bieżące i oryginalne wystąpienia obiektu. Umożliwia to śledzenie zmian za pomocą starych i nowych wartości, dzięki czemu automatycznie będzie wiadomo, które pola zostały zmienione.  
  
3. Dołącz ją z <xref:System.Data.Linq.Table%601.Attach%2A> przeciążeniem, które przyjmuje drugi parametr Boolean (wartość true). Spowoduje to wyświetlenie śledzenia zmian w celu uwzględnienia zmodyfikowanego obiektu bez konieczności podawania oryginalnych wartości. W tym podejściu obiekt musi mieć pole Version/timestamp.  
  
 Aby uzyskać więcej informacji, zobacz temat [Stany obiektów i śledzenie zmian](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).  
  
 Jeśli obiekt jednostki <xref:System.Data.Linq.DuplicateKeyException> znajduje się już w pamięci podręcznej identyfikatorów z tą samą tożsamością co obiekt, który jest dołączany, jest zgłaszany.  
  
 Po dołączeniu z `IEnumerable` zestawem obiektów <xref:System.Data.Linq.DuplicateKeyException> jest generowane, gdy istnieje już istniejący klucz. Pozostałe obiekty nie są dołączone.  
  
## <a name="see-also"></a>Zobacz także

- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
