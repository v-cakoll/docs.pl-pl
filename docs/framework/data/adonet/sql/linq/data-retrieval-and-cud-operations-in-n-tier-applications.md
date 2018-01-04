---
title: Pobieranie danych i CUD operacje w aplikacjach warstwowych (LINQ to SQL)
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
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 84a72642636be2238a81f1b9c00e3ac4e7037272
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a>Pobieranie danych i CUD operacje w aplikacjach warstwowych (LINQ to SQL)
Podczas obiekty obiektów, takich jak klienci lub zamówienia klienta za pośrednictwem sieci, podmioty są odłączone od ich kontekstu danych. Kontekst danych śledzi już ich zmiany i ich powiązania z innych obiektów. Nie jest to problem, tak długo, jak klienci są tylko do odczytu danych. Jest również stosunkowo proste umożliwić klientom dodawać nowe wiersze do bazy danych. Jednak jeśli aplikacja wymaga, aby klienci mogli aktualizować lub usuwać dane, następnie należy dołączyć jednostek do nowy kontekst danych przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>. Ponadto jeśli sprawdzenie optymistycznej współbieżności korzystają z oryginalnych wartości, następnie należy również sposób zapewniające bazy danych oryginalna jednostka i jednostki zmienione. `Attach` Metody są dostarczane do umożliwiają poddane jednostek nowy kontekst danych po ich odłączony.  
  
 Nawet jeśli są serializacji obiektów pośredniczących zamiast [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jednostek, nadal jest konieczne utworzenia obiektu w warstwie dostępu do danych (DAL) i dołączenie go do nowego <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, aby przesłać dane do bazy danych.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]jest całkowicie Obojętność o jak jednostki są serializowane. Aby uzyskać więcej informacji o sposobie używania [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] i SQLMetal narzędzia do generowania klasy, które są do serializacji przy użyciu systemu Windows Communication Foundation (WCF), zobacz [jak: utworzyć serializacji jednostek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md).  
  
> [!NOTE]
>  Wywoływać tylko `Attach` metody w nowych lub zdeserializowany jednostek. Jedynym sposobem dla jednostki odłączenia od jego oryginalnej kontekst danych jest dla niego do serializacji. Jeśli próby dołączenia undetached jednostkę do nowego kontekstu danych, a jednostkę nadal wstrzymał ładowarki z jego poprzedni kontekst danych [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zostanie zgłoszony wyjątek. Jednostka z opóźnieniem ładowarki z dwóch kontekstów danych może spowodować niepożądane wyniki podczas wykonywania insert, update i operacji usuwania dla tej jednostki. Aby uzyskać więcej informacji na temat odroczonego ładowarki zobacz [odroczone i ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="retrieving-data"></a>Pobieranie danych  
  
### <a name="client-method-call"></a>Wywołanie metody klienta  
 W poniższych przykładach pokazano przykład wywołanie metody z warstwą dal w kliencie formularzy systemu Windows. W tym przykładzie warstwa DAL jest zaimplementowany jako Biblioteka usługi systemu Windows:  
  
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
 Poniższy przykład przedstawia implementację metody interfejsu w warstwy środkowej. Poniżej przedstawiono dwa główne punkty należy pamiętać:  
  
-   <xref:System.Data.Linq.DataContext> Jest zadeklarowany w zakresie metody.  
  
-   Metoda zwraca <xref:System.Collections.IEnumerable> kolekcji rzeczywiste wyniki. Serializator wykona zapytania do odesłania do klienta/prezentacji warstwy wyniki. Aby uzyskać dostęp do wyników zapytania lokalnie na warstwy środkowej, możesz wymusić wykonanie przez wywołanie metody `ToList` lub `ToArray` na zmienną zapytania. Możesz powrócić do tej listy lub tablicy jako `IEnumerable`.  
  
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
  
 Wystąpienie kontekstu danych powinny mieć okresu istnienia jednej "jednostka pracy". W środowisku luźno połączonych jednostka pracy jest zwykle małe, możliwe, że jeden optymistycznej transakcji, w tym wywołanie `SubmitChanges`. Kontekst danych jest utworzony, a usunięty w zakresie metody. Jeśli jednostka pracy obejmuje wywołań logikę reguł biznesowych, to zwykle można zachować `DataContext` wystąpienia tej całej operacji. W każdym przypadku `DataContext` wystąpień nie mają być aktywne przez dłuższy czas między dowolne liczby transakcji.  
  
 Ta metoda zwróci obiekty produktu, ale nie kolekcję obiektów Order_Detail, które są skojarzone z każdego produktu. Użyj <xref:System.Data.Linq.DataLoadOptions> obiekt, aby zmienić to zachowanie domyślne. Aby uzyskać więcej informacji, zobacz [porady: kontrolki jak dużo powiązane dane są pobierane](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md).  
  
## <a name="inserting-data"></a>Wstawianie danych  
 Aby wstawić nowy obiekt, warstwy prezentacji po prostu wywołuje odpowiedniej metody w interfejsie warstwy środkowej i przekazuje w nowy obiekt do wstawienia. W niektórych przypadkach może być bardziej wydajny klienta do przekazywania tylko niektóre wartości i warstwy środkowej konstruowania obiektu pełna.  
  
### <a name="middle-tier-implementation"></a>Implementacja warstwy środkowej  
 W warstwie środkowej nowy <xref:System.Data.Linq.DataContext> jest utworzony, obiekt jest dołączony do <xref:System.Data.Linq.DataContext> za pomocą <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> — metoda i obiektu są wstawiane po <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana. Wyjątki, wywołania zwrotne i warunki błędów mogą zostać obsłużone tak jak w przypadku każdej innej sytuacji usługi sieci Web.  
  
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
 Aby usunąć istniejący obiekt z bazy danych, warstwy prezentacji wymaga odpowiedniej metody w interfejsie warstwy środkowej i przekazuje w jego kopii, która zawiera wartości początkowe obiektu do usunięcia.  
  
 Usuń operacje obejmują sprawdzenie optymistycznej współbieżności i obiektu, który ma zostać usunięty, najpierw musi być dołączony do nowej kontekstu danych. W tym przykładzie `Boolean` ustawiono parametr `false` aby wskazać, że obiekt nie ma sygnatury czasowej (RowVersion). Jeśli w tabeli bazy danych wygenerować sygnatury czasowe dla każdego rekordu, kontrolach współbieżności są znacznie prostsza, szczególnie dla klienta. Wystarczy przekazać w oryginalnym lub modyfikacji obiektu i ustawić `Boolean` parametr `true`. W każdym przypadku na warstwy środkowej należy zwykle catch <xref:System.Data.Linq.ChangeConflictException>. Aby uzyskać więcej informacji na temat obsługi konfliktów optymistycznej współbieżności, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
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
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje aktualizacje w tych scenariuszach obejmujących optymistycznej współbieżności:  
  
-   Na podstawie sygnatury czasowe lub numery RowVersion optymistycznej współbieżności.  
  
-   Optymistycznej współbieżności na podstawie oryginalnej wartości podzbioru właściwości jednostki.  
  
-   Oparte na pełną jednostek oryginalnego i zmodyfikowanych optymistycznej współbieżności.  
  
 Można również wykonywać aktualizacji lub usuwania w jednostce wraz z jego relacji, na przykład jeśli klient i kolekcja powiązane obiekty kolejności. Podczas wprowadzania zmian na kliencie do wykresu jednostki obiektów i ich podrzędnych (`EntitySet`) kolekcje i sprawdzenie optymistycznej współbieżności wymagają oryginalnych wartości, klient musi dostarczyć te oryginalnych wartości dla każdej jednostki i <xref:System.Data.Linq.EntitySet%601> obiekt. Jeśli chcesz umożliwić klientom zestaw powiązane aktualizacje, usunięcia i wstawienia w wywołaniu metody pojedynczego, musisz podać klienta sposób, aby wskazać, jaki typ operacji do wykonania dla każdej jednostki. Na warstwy środkowej, następnie należy wywołać odpowiednie <xref:System.Data.Linq.ITable.Attach%2A> metody, a następnie <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, lub <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (bez `Attach`, do wstawienia) dla każdego obiektu przed wywołaniem <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Nie pobierać dane z bazy danych jako sposobu uzyskania oryginalnych wartości, przed przystąpieniem do aktualizacji.  
  
 Aby uzyskać więcej informacji na temat optymistycznej współbieżności, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md). Aby uzyskać szczegółowe informacje o rozwiązywaniu optymistycznej współbieżności zmian konfliktów, zobacz [porady: Zarządzanie konflikty zmienić](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 W poniższych przykładach pokazano poszczególnych scenariuszy:  
  
### <a name="optimistic-concurrency-with-timestamps"></a>Optymistycznej współbieżności z sygnaturami czasowymi  
  
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
 W takie podejście klient zwraca pełną Zserializowany obiekt, wraz z wartości, które mają być modyfikowane.  
  
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
  
### <a name="with-complete-entities"></a>Z pełną jednostek  
  
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
  
 Aby zaktualizować kolekcję, wywołaj <xref:System.Data.Linq.ITable.AttachAll%2A> zamiast `Attach`.  
  
### <a name="expected-entity-members"></a>Elementy członkowskie jednostki oczekiwany  
 Jak wspomniano wcześniej, tylko niektóre elementy członkowskie obiektu jednostki są wymagane, należy ustawić przed wywołaniem `Attach` metody. Elementy członkowskie jednostki, które są wymagane określone musi spełniać następujące kryteria:  
  
-   Być częścią tożsamości jednostki.  
  
-   Można powinien być modyfikowany.  
  
-   Być sygnaturę czasową lub jego <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> atrybut ustawioną coś oprócz `Never`.  
  
 Tabela używa sygnatury czasowej ani numeru wersji na sprawdzenie optymistycznej współbieżności, należy ustawić te elementy Członkowskie przed wywołaniem <xref:System.Data.Linq.ITable.Attach%2A>. Element członkowski jest dedykowany do optymistycznej współbieżności podczas sprawdzania <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość jest ustawiona na wartość true dla atrybutu tej kolumny. Wszystkie żądane aktualizacje zostaną przesłane tylko wtedy, gdy wersja wartości liczby lub sygnatury czasowej są takie same, w bazie danych.  
  
 Element członkowski jest również używana w sprawdzenie optymistycznej współbieżności, jak długo element członkowski nie ma <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ustawioną `Never`. Wartość domyślna to `Always` Jeśli wartość nie zostanie określona.  
  
 Jeśli jeden z tych elementów członkowskich Brak wymaganej, <xref:System.Data.Linq.ChangeConflictException> jest generowany podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("wiersza nie można odnaleźć lub zmienić").  
  
### <a name="state"></a>Stan  
 Po jednostki obiekt jest dołączony do <xref:System.Data.Linq.DataContext> wystąpienie, obiekt jest traktowany jako w `PossiblyModified` stanu. Istnieją trzy sposoby, aby wymusić przyłączonego obiektu wziąć pod uwagę `Modified`.  
  
1.  Dołącz je jako zostały zmodyfikowane, a następnie bezpośrednio zmodyfikuj pola.  
  
2.  Dołączenie go z <xref:System.Data.Linq.Table%601.Attach%2A> przeciążenia, które przyjmuje bieżących i oryginalnych obiektów. Udostępnia śledzący zmiany z starych i nowych wartości, dzięki czemu automatycznie wiedzą, pola, które zostały zmienione.  
  
3.  Dołączenie go z <xref:System.Data.Linq.Table%601.Attach%2A> przeciążenia, które przyjmuje drugi parametr logiczna (wartość true). Dzięki temu zostanie poinformowany śledzący zmiany wziąć pod uwagę obiektu modyfikowana bez konieczności podać wszelkie oryginalnych wartości. W takie podejście obiekt musi mieć pole wersji/sygnatura czasowa.  
  
 Aby uzyskać więcej informacji, zobacz [stanów obiektów i śledzenie zmian](../../../../../../docs/framework/data/adonet/sql/linq/object-states-and-change-tracking.md).  
  
 Jeśli do obiektu jednostki występuje już w pamięci podręcznej identyfikator o tej samej tożsamości jako obiekt dołączony, <xref:System.Data.Linq.DuplicateKeyException> jest generowany.  
  
 Po dołączeniu z `IEnumerable` zestaw obiektów, <xref:System.Data.Linq.DuplicateKeyException> jest generowany, gdy istnieje już istniejącego klucza. Pozostałe obiekty nie są dołączone.  
  
## <a name="see-also"></a>Zobacz też  
 [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
