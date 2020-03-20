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
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Pobieranie danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)
Podczas serializacji obiektów jednostki, takich jak Klienci lub Zamówienia do klienta za pośrednictwem sieci, te jednostki są odłączane od ich kontekstu danych. Kontekst danych nie śledzi już ich zmian lub ich skojarzeń z innymi obiektami. Nie jest to problem, o ile klienci czytają tylko dane. Jest również stosunkowo proste, aby umożliwić klientom dodawanie nowych wierszy do bazy danych. Jeśli jednak aplikacja wymaga, aby klienci mogli aktualizować lub usuwać dane, przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>należy dołączyć encje do nowego kontekstu danych. Ponadto jeśli używasz optymistyczne sprawdzanie współbieżności z oryginalnymi wartościami, a następnie będzie również potrzebny sposób, aby zapewnić bazy danych zarówno oryginalnej jednostki i jednostki jako zmodyfikowane. Metody `Attach` są dostarczane w celu umożliwienia wprowadzenia jednostek w nowym kontekście danych po ich odłączeniu.  
  
 Nawet jeśli szeregowanie obiektów serwera proxy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zamiast jednostek, nadal trzeba skonstruować jednostkę na warstwie dostępu <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>do danych (DAL) i dołączyć go do nowego programu , aby przesłać dane do bazy danych.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]jest całkowicie obojętny na sposób serializacji jednostek. Aby uzyskać więcej informacji na temat używania narzędzi Object Relational Designer i SQLMetal do generowania klas, które można szeregować przy użyciu programu Windows Communication Foundation (WCF), zobacz [Jak: Tworzenie szeregowania jednostek](how-to-make-entities-serializable.md).  
  
> [!NOTE]
> Wywołaj `Attach` tylko metody na nowych lub deserializacji jednostek. Jedynym sposobem, aby jednostka, która ma być odłączony od oryginalnego kontekstu danych jest dla niego do serializacji. Jeśli spróbujesz dołączyć nieumożnioną jednostkę do nowego kontekstu danych, a ta [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jednostka nadal ma odroczone moduły ładune z poprzedniego kontekstu danych, zostanie zgłoszony wyjątek. Jednostka z odroczonymi modułami ładującego z dwóch różnych kontekstów danych może spowodować niepożądane wyniki podczas wykonywania operacji wstawiania, aktualizowania i usuwania w tej jednostce. Aby uzyskać więcej informacji na temat modułów ładujące odroczone, zobacz [Odroczone i natychmiastowe ładowanie](deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Pobieranie danych  
  
### <a name="client-method-call"></a>Wywołanie metody klienta  
 Poniższe przykłady przedstawiają przykładowe wywołanie metody do warstwy DAL z klienta windows forms. W tym przykładzie warstwa DAL jest implementowana jako biblioteka usług systemu Windows:  
  
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
 W poniższym przykładzie przedstawiono implementację metody interfejsu w warstwie środkowej. Poniżej znajdują się dwa główne punkty, na które należy zwrócić uwagę:  
  
- Jest <xref:System.Data.Linq.DataContext> zadeklarowany w zakresie metody.  
  
- Metoda zwraca <xref:System.Collections.IEnumerable> kolekcję rzeczywistych wyników. Serializator wykona kwerendę, aby wysłać wyniki z powrotem do warstwy klienta/prezentacji. Aby uzyskać dostęp do wyników kwerendy lokalnie w `ToList` warstwie środkowej, można wymusić wykonanie przez wywołanie lub `ToArray` zmienną kwerendy. Następnie można zwrócić tę listę `IEnumerable`lub tablicę jako plik .  
  
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
  
 Wystąpienie kontekstu danych powinno mieć okres istnienia jednej "jednostki pracy". W luźno sprzężonych środowiskach jednostka pracy jest zazwyczaj mała, być może `SubmitChanges`jedna optymistyczna transakcja, w tym jedno wezwanie do . W związku z tym kontekst danych jest tworzony i usuwany w zakresie metody. Jeśli jednostka pracy zawiera wywołania logiki reguł biznesowych, ogólnie `DataContext` rzecz biorąc, należy zachować wystąpienie dla tej całej operacji. W każdym `DataContext` przypadku wystąpienia nie są przeznaczone do utrzymywana przy życiu przez długi okres czasu w dowolnej liczbie transakcji.  
  
 Ta metoda zwróci Product obiektów, ale nie kolekcji Order_Detail obiektów, które są skojarzone z każdym Produkt. Użyj <xref:System.Data.Linq.DataLoadOptions> obiektu, aby zmienić to zachowanie domyślne. Aby uzyskać więcej informacji, zobacz [Jak: Kontrolować ilość powiązanych danych](how-to-control-how-much-related-data-is-retrieved.md).  
  
## <a name="inserting-data"></a>Wstawianie danych  
 Aby wstawić nowy obiekt, warstwa prezentacji po prostu wywołuje odpowiednią metodę w interfejsie warstwy środkowej i przekazuje w nowym obiekcie do wstawienia. W niektórych przypadkach może być bardziej wydajne dla klienta do przekazania tylko niektóre wartości i mają warstwy środkowej konstruowania pełnego obiektu.  
  
### <a name="middle-tier-implementation"></a>Implementacja warstwy środkowej  
 Na warstwie środkowej <xref:System.Data.Linq.DataContext> tworzony jest nowy, obiekt jest <xref:System.Data.Linq.DataContext> dołączony <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> do niej za pomocą metody, a obiekt jest wstawiany, gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływany. Wyjątki, wywołania zwrotne i warunki błędu mogą być obsługiwane tak samo, jak w każdym innym scenariuszu usługi sieci Web.  
  
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
 Aby usunąć istniejący obiekt z bazy danych, warstwa prezentacji wywołuje odpowiednią metodę w interfejsie warstwy środkowej i przekazuje w swojej kopii, która zawiera oryginalne wartości obiektu do usunięcia.  
  
 Operacje usuwania obejmują optymistyczne kontrole współbieżności, a obiekt do usunięcia musi najpierw zostać dołączony do nowego kontekstu danych. W tym przykładzie `Boolean` parametr `false` jest ustawiony, aby wskazać, że obiekt nie ma sygnatury czasowej (RowVersion). Jeśli tabela bazy danych generuje sygnatury czasowe dla każdego rekordu, a następnie kontroli współbieżności są znacznie prostsze, szczególnie dla klienta. Wystarczy przekazać oryginalny lub zmodyfikowany obiekt i `Boolean` ustawić `true`parametr na . W każdym razie na poziomie środkowym zazwyczaj konieczne <xref:System.Data.Linq.ChangeConflictException>jest złapanie pliku . Aby uzyskać więcej informacji na temat obsługi optymistycznych konfliktów współbieżności, zobacz [Optymistyczna współbieżność: Przegląd](optimistic-concurrency-overview.md).  
  
 Podczas usuwania jednostek, które mają ograniczenia klucza obcego w skojarzonych <xref:System.Data.Linq.EntitySet%601> tabelach, należy najpierw usunąć wszystkie obiekty w jego kolekcji.  
  
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
  
- Optymistyczna współbieżność na podstawie sygnatur czasowych lub numerów RowVersion.  
  
- Optymistyczna współbieżność oparta na oryginalnych wartościach podzbioru właściwości jednostki.  
  
- Optymistyczna współbieżność oparta na kompletnych oryginalnych i zmodyfikowanych jednostkach.  
  
 Można również wykonywać aktualizacje lub usuwa na jednostki wraz z jego relacji, na przykład Klient i kolekcji skojarzonych z Zamówienie obiektów. Po wprowadzeniu zmian na kliencie do wykresu obiektów jednostki i ich kolekcji podrzędnych (`EntitySet`) i optymistyczne kontrole współbieżności <xref:System.Data.Linq.EntitySet%601> wymagają oryginalnych wartości, klient musi podać te oryginalne wartości dla każdej jednostki i obiektu. Jeśli chcesz włączyć klientów do zestawu powiązanych aktualizacji, usuwa i wstawia w wywołaniu pojedynczej metody, należy podać klientowi sposób, aby wskazać, jaki typ operacji do wykonania na każdej jednostce. Na warstwie środkowej należy następnie <xref:System.Data.Linq.ITable.Attach%2A> wywołać <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>odpowiednią <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>metodę, a następnie , lub <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach` <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, dla wstawień) dla każdej jednostki przed wywołaniem . Nie należy pobierać danych z bazy danych jako sposób uzyskania oryginalnych wartości przed wypróbowaniem aktualizacji.  
  
 Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [Optymistyczna współbieżność: Przegląd](optimistic-concurrency-overview.md). Aby uzyskać szczegółowe informacje na temat rozwiązywania konfliktów zmiany współbieżności optymistycznej, zobacz [Jak: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md).  
  
 Poniższe przykłady pokazują każdy scenariusz:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Optymistyczna współbieżność z sygnaturami czasowymi  
  
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
  
### <a name="with-subset-of-original-values"></a>Z podzbiorem wartości oryginalnych  
 W tym podejściu klient zwraca kompletny serializowany obiekt wraz z wartościami, które mają zostać zmodyfikowane.  
  
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
  
 Aby zaktualizować kolekcję, <xref:System.Data.Linq.ITable.AttachAll%2A> zadzwoń `Attach`zamiast .  
  
### <a name="expected-entity-members"></a>Oczekiwani członkowie jednostki  
 Jak wspomniano wcześniej, tylko niektóre elementy członkowskie obiektu jednostki są `Attach` wymagane do zestawu przed wywołaniem metod. Elementy członkowskie jednostki, które muszą zostać ustawione, muszą spełniać następujące kryteria:  
  
- Bądź częścią tożsamości jednostki.  
  
- Należy się spodziewać, że zostaną zmodyfikowane.  
  
- Bądź sygnaturą <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> czasową lub mieć `Never`jego atrybut ustawiony na coś poza .  
  
 Jeśli tabela używa sygnatury czasowej lub numeru wersji do optymistycznego sprawdzania <xref:System.Data.Linq.ITable.Attach%2A>współbieżności, należy ustawić tych członków przed wywołaniem . Element członkowski jest przeznaczony do sprawdzania współbieżności optymistyczne, gdy <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość jest ustawiona na true w tym atrybutu Column. Wszelkie żądane aktualizacje zostaną przesłane tylko wtedy, gdy numer wersji lub wartości sygnatury czasowej są takie same w bazie danych.  
  
 Element członkowski jest również używany w optymistycznym czeku współbieżności, o ile element członkowski nie ma <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ustawionego na `Never`. Wartość domyślna `Always` jest, jeśli nie określono żadnej innej wartości.  
  
 Jeśli brakuje jednego z tych wymaganych <xref:System.Data.Linq.ChangeConflictException> elementów <xref:System.Data.Linq.DataContext.SubmitChanges%2A> członkowskich, a jest wyrzucany podczas ("Wiersz nie znaleziono lub zmieniono").  
  
### <a name="state"></a>Stan  
 Po dołączeniu obiektu jednostki <xref:System.Data.Linq.DataContext> do wystąpienia, obiekt jest `PossiblyModified` uważany za w stanie. Istnieją trzy sposoby na zmuszenie do `Modified`rozważenia dołączonego obiektu.  
  
1. Dołącz go jako niezmodyfikowany, a następnie bezpośrednio zmodyfikuj pola.  
  
2. Dołącz go <xref:System.Data.Linq.Table%601.Attach%2A> z przeciążeniem, które przyjmuje bieżące i oryginalne wystąpienia obiektów. Dostarcza to modułowi śledzenia zmian ze starymi i nowymi wartościami, dzięki czemu automatycznie będzie wiedział, które pola uległy zmianie.  
  
3. Dołącz go <xref:System.Data.Linq.Table%601.Attach%2A> z przeciążeniem, które przyjmuje drugi parametr logiczny (ustawiony na true). Spowoduje to, że śledzenie zmian zostanie rozważone jako zmodyfikowany obiekt bez konieczności posyłania żadnych oryginalnych wartości. W tym podejściu obiekt musi mieć pole sygnatury czasowej wersji/sygnatury czasowej.  
  
 Aby uzyskać więcej informacji, zobacz [Stany obiektów i Śledzenie zmian](object-states-and-change-tracking.md).  
  
 Jeśli obiekt jednostki już występuje w pamięci podręcznej identyfikatorów o <xref:System.Data.Linq.DuplicateKeyException> tej samej tożsamości co obiekt, który jest dołączony, a jest generowany.  
  
 Po dołączeniu `IEnumerable` z zestawem <xref:System.Data.Linq.DuplicateKeyException> obiektów, a jest generowany, gdy już istniejący klucz jest obecny. Pozostałe obiekty nie są dołączone.  
  
## <a name="see-also"></a>Zobacz też

- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
- [Informacje uzupełniające](background-information.md)
