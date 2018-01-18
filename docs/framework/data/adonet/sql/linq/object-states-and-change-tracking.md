---
title: "Stanów obiektów i śledzenie zmian"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f7eb1a8afe87caece18432c66a8d8a268ce9fbd2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="object-states-and-change-tracking"></a>Stanów obiektów i śledzenie zmian
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obiekty zawsze uczestniczyć w niektórych *stanu*. Na przykład, jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy nowy obiekt, gdy obiekt jest w `Unchanged` stanu. Możesz samodzielnie utworzyć nowy obiekt jest nieznany w <xref:System.Data.Linq.DataContext> i znajduje się w `Untracked` stanu. Po pomyślnym wykonaniu <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, wszystkie obiekty znane [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w `Unchanged` stanu. (Jedynym wyjątkiem jest reprezentowana przez te, które zostały pomyślnie usunięte z bazy danych, które znajdują się w `Deleted` stanu i korzystanie z niej w tym <xref:System.Data.Linq.DataContext> wystąpienia.)  
  
## <a name="object-states"></a>Stanów obiektów  
 W poniższej tabeli przedstawiono możliwe stany [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektów.  
  
|Stan|Opis|  
|-----------|-----------------|  
|`Untracked`|Nie są śledzone przez obiekt [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Przykłady obejmują następujące czynności:<br /><br /> -Nie tworzyć zapytania za pomocą bieżącego obiektu <xref:System.Data.Linq.DataContext> (na przykład nowo utworzony obiekt).<br />-Został utworzony za pomocą deserializacji obiektu<br />-Tworzyć zapytania za pomocą innego obiektu <xref:System.Data.Linq.DataContext>.|  
|`Unchanged`|Obiekt pobrany przy użyciu bieżącej <xref:System.Data.Linq.DataContext> , nie wiadomo, został zmodyfikowany od czasu jej utworzenia.|  
|`PossiblyModified`|Obiekt, który jest *dołączony* do <xref:System.Data.Linq.DataContext>. Aby uzyskać więcej informacji, zobacz [pobierania danych i CUD operacje w aplikacjach warstwowych (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).|  
|`ToBeInserted`|Obiekt nie pobrać przy użyciu bieżącej <xref:System.Data.Linq.DataContext>. Powoduje to, że bazy danych `INSERT` podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeUpdated`|Obiekt znane został zmodyfikowany od czasu jej pobrania. Powoduje to, że bazy danych `UPDATE` podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeDeleted`|Obiekt oznaczona do usunięcia, co powoduje bazy danych `DELETE` podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`Deleted`|Obiekt, który został usunięty w bazie danych. Ten stan jest ostateczny i nie zezwala na dodatkowe przejścia.|  
  
## <a name="inserting-objects"></a>Wstawianie obiektów  
 Można jawnie żądania `Inserts` przy użyciu <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>. Alternatywnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można wywnioskować `Inserts` przez wyszukiwanie obiektów połączony z jednym z znane obiekty, które muszą zostać zaktualizowane. Na przykład, jeśli dodasz `Untracked` do obiektu <xref:System.Data.Linq.EntitySet%601> lub ustaw <xref:System.Data.Linq.EntityRef%601> do `Untracked` obiektu o wprowadzeniu `Untracked` obiekt jest dostępny i śledzonych obiektów na wykresie. Podczas przetwarzania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przesyłane za pośrednictwem śledzonych obiektów i odnajduje dostępny obiekty trwałe, które nie są śledzone. Takie obiekty nadają się do wstawienia do bazy danych.  
  
 Dla klas w hierarchii dziedziczenia <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>(`o`) określa również wartość elementu członkowskiego, wyznaczony jako *rozróżniacza* odpowiada typowi obiektu `o`. W przypadku typu pasującego domyślną wartość dyskryminatora ta akcja powoduje, że wartość dyskryminatora zostaną zastąpione z wartością domyślną. Aby uzyskać więcej informacji, zobacz [Obsługa dziedziczenia](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
> [!IMPORTANT]
>  Obiekt, który został dodany do `Table` nie znajduje się w pamięci podręcznej tożsamości. Pamięć podręczna tożsamości odzwierciedla co pobrane z bazy danych. Po wywołaniu <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>, dodano jednostki nie jest wyświetlany w kwerendy do bazy danych do <xref:System.Data.Linq.DataContext.SubmitChanges%2A> zakończy się pomyślnie.  
  
## <a name="deleting-objects"></a>Usuwanie obiektów  
 Oznacz śledzonych obiektu `o` do usunięcia przez wywołanie metody <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(IE) na odpowiednie <xref:System.Data.Linq.Table%601>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]uwzględnia usunięcie obiektu z <xref:System.Data.Linq.EntitySet%601> jako aktualizacja operacji i odpowiednie wartości klucza obcego jest ustawiona na wartość null. Obiekt docelowy operacji (`o`) nie zostanie usunięty z tabeli. Na przykład `cust.Orders.DeleteOnSubmit(ord)` oznacza, że aktualizacja gdzie relacji między `cust` i `ord` jest Przerwano ustawiając klucz obcy `ord.CustomerID` na wartość null. Nie powoduje usunięcia wiersza odpowiadający `ord`.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wykonuje następujące przetwarzania po usunięciu obiektu (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) z tabeli:  
  
-   Gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest nazywany `DELETE` operacja została wykonana dla tego obiektu.  
  
-   Usuwanie nie są propagowane do obiektów powiązanych niezależnie od tego, czy zostały załadowane. W szczególności powiązane obiekty nie są ładowane do aktualizacji właściwości relacji.  
  
-   Po pomyślnym wykonaniu <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, obiekty są ustawione na `Deleted` stanu. W związku z tym nie można użyć obiektu lub jego `id` w tym <xref:System.Data.Linq.DataContext>. Wewnętrznej pamięci podręcznej obsługiwanego przez <xref:System.Data.Linq.DataContext> wystąpienia nie powoduje usunięcia obiektów, które są pobierane lub dodany jako nowy, nawet po usunięciu obiektów w bazie danych.  
  
 Możesz wywołać <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> tylko na śledzone przez obiekt <xref:System.Data.Linq.DataContext>. Aby uzyskać `Untracked` obiektu, należy wywołać <xref:System.Data.Linq.Table%601.Attach%2A> przed wywołaniem <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>. Wywoływanie <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> na `Untracked` obiektu zgłasza wyjątek.  
  
> [!NOTE]
>  Usuwanie obiektu z tabeli informuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] do generowania odpowiednich SQL `DELETE` polecenia w czasie <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Ta akcja nie usunąć obiekt z pamięci podręcznej lub propagacji do usunięcia powiązanych obiektów.  
>   
>  Aby odzyskać `id` usuniętego obiektu, użyj nowego <xref:System.Data.Linq.DataContext> wystąpienia. Oczyszczania powiązane obiekty, można użyć *usuwanie kaskadowe* funkcji bazy danych, w przeciwnym razie ręcznie usunąć powiązanych obiektów.  
>   
>  Nie trzeba go usunąć w dowolnej kolejności specjalne powiązane obiekty (w przeciwieństwie do bazy danych).  
  
## <a name="updating-objects"></a>Aktualizowanie obiektów  
 Można wykryć `Updates` obserwując powiadomień o zmianach. Powiadomienia są realizowane za pośrednictwem <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> zdarzenia w metody ustawiające właściwości. Gdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest powiadamiany o pierwszej zmianie do obiektu, tworzy kopię obiektu i traktuje jako obiekt kandydatem do generowania `Update` instrukcji.  
  
 Dla obiektów, które nie implementują <xref:System.ComponentModel.INotifyPropertyChanging>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przechowuje kopię wartości, które obiekty mają, jeśli zostały one najpierw zmaterializowany. Podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] porównuje bieżące i oryginalne wartości można zdecydować, czy obiekt został zmieniony.  
  
 Aktualizacje do relacji odwołanie z podrzędnych do elementu nadrzędnego (to znaczy odwołanie odpowiadający klucz obcy) jest traktowany jako urząd. Odwołania w kierunku odwrotnym (czyli z nadrzędnych do podrzędnych) jest opcjonalna. Klasy relacji (<xref:System.Data.Linq.EntitySet%601> i <xref:System.Data.Linq.EntityRef%601>) gwarantuje, że odwołania dwukierunkowego są zgodne w przypadku relacji jeden do wielu oraz jeden do jednego. Jeśli nie są używane w modelu obiektu <xref:System.Data.Linq.EntitySet%601> lub <xref:System.Data.Linq.EntityRef%601>, i jeśli odwrotnej odwołania, jest obowiązek zachowania ich spójności z odwołaniem w przód po zaktualizowaniu relacji.  
  
 Jeśli zaktualizujesz zarówno wymaganego odwołania i odpowiedniego klucza obcego, należy się upewnić, że użytkownik wyrazi zgodę. <xref:System.InvalidOperationException> Jest zgłaszany wyjątek, jeśli dwa nie są zsynchronizowane w momencie wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Mimo że wartości klucza obcego zmiany są wystarczające dla wpływających na aktualizację wiersza źródłowego, należy zmienić odwołania, który zapewnia łączność obiektu spójności wykres i dwukierunkowe relacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Operacje wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)
