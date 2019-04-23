---
title: Stany obiektów i śledzenie zmian
ms.date: 03/30/2017
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
ms.openlocfilehash: 63b04d3a4b6e48594e9664833a6e539d62bbab0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191158"
---
# <a name="object-states-and-change-tracking"></a>Stany obiektów i śledzenie zmian
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiekty zawsze wziąć udział w niektórych *stanu*. Na przykład, gdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy nowy obiekt, obiekt jest w `Unchanged` stanu. Nowy obiekt, który samodzielnie tworzenia jest nieznany <xref:System.Data.Linq.DataContext> i znajduje się w `Untracked` stanu. Po pomyślnym wykonaniu <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, wszystkie obiekty znane [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] znajdują się w `Unchanged` stanu. (Jednym wyjątek jest reprezentowany przez te, które zostały pomyślnie usunięte z bazy danych, które znajdują się w `Deleted` stanu i nienadające się do użytku w tym <xref:System.Data.Linq.DataContext> wystąpienia.)  
  
## <a name="object-states"></a>Stany obiektów  
 W poniższej tabeli przedstawiono możliwe stany [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektów.  
  
|Stan|Opis|  
|-----------|-----------------|  
|`Untracked`|Obiekt nie jest śledzone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Przykłady obejmują następujące czynności:<br /><br /> -Nie obsługują zapytań, za pośrednictwem bieżącego obiektu <xref:System.Data.Linq.DataContext> (np. nowo utworzony obiekt).<br />-Utworzone za pomocą deserializacji obiektu<br />-Odpytywana za pomocą innego obiektu <xref:System.Data.Linq.DataContext>.|  
|`Unchanged`|Pobrać przy użyciu bieżącego obiektu <xref:System.Data.Linq.DataContext> , nie wiadomo, został zmodyfikowany od czasu jej utworzenia.|  
|`PossiblyModified`|Obiekt, który jest *dołączone* do <xref:System.Data.Linq.DataContext>. Aby uzyskać więcej informacji, zobacz [pobierania danych i operacje CUD w aplikacjach N-warstwowych (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).|  
|`ToBeInserted`|Obiekt nie są pobierane przy użyciu bieżącego <xref:System.Data.Linq.DataContext>. Powoduje to, że bazy danych `INSERT` podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeUpdated`|Obiekt, który wiadomo, że zostały zmienione od czasu ich odebrania. Powoduje to, że bazy danych `UPDATE` podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeDeleted`|Obiekt jest oznaczony do usunięcia, co powoduje bazy danych `DELETE` podczas <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`Deleted`|Obiekt, który został usunięty w bazie danych. Ten stan jest ostateczne i nie zezwala na dodatkowe przejścia.|  
  
## <a name="inserting-objects"></a>Wstawianie obiektów  
 Jawne zażądanie `Inserts` przy użyciu <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>. Alternatywnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] może wywnioskować `Inserts` , wyszukując obiekty połączone z jedną znane obiekty, które muszą zostać zaktualizowane. Na przykład jeśli dodasz `Untracked` do obiektu <xref:System.Data.Linq.EntitySet%601> lub ustaw <xref:System.Data.Linq.EntityRef%601> do `Untracked` obiektu wprowadzeniu `Untracked` obiektu osiągalne za pomocą obiektów śledzonych na wykresie. Podczas przetwarzania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przesyłane za pośrednictwem obiektów śledzonych i odnajduje wszystkie osiągalne trwałe obiekty, które nie są śledzone. Takie obiekty są kandydatami do wstawienia do bazy danych.  
  
 Dla klas w hierarchii dziedziczenia <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>(`o`) także ustawia wartość elementu członkowskiego, wyznaczony jako *dyskryminatora* będzie pasował do typu obiektu `o`. W przypadku typu pasującego domyślną wartość dyskryminatora ta akcja powoduje, że wartość dyskryminatora zostaną zastąpione wartością domyślną. Aby uzyskać więcej informacji, zobacz [Obsługa dziedziczenia](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
> [!IMPORTANT]
>  Obiekt, który został dodany do `Table` nie znajduje się w pamięci podręcznej tożsamości. Pamięci podręcznej tożsamości odzwierciedla tylko co to są pobierane z bazy danych. Po wywołaniu <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>, dodano jednostki nie jest widoczna w kwerendy do bazy danych do momentu <xref:System.Data.Linq.DataContext.SubmitChanges%2A> została pomyślnie ukończona.  
  
## <a name="deleting-objects"></a>Usuwanie obiektów  
 Oznaczanie obiektów śledzonych `o` do usunięcia przez wywołanie metody <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(o) w odpowiednim <xref:System.Data.Linq.Table%601>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uwzględnia usunięcie obiektu z <xref:System.Data.Linq.EntitySet%601> jako aktualizacja operacji, a wartość odpowiedniego klucza obcego jest ustawiona na wartość null. Obiekt docelowy operacji (`o`) nie zostanie usunięty z tabeli. Na przykład `cust.Orders.DeleteOnSubmit(ord)` oznacza, że aktualizacja gdzie relacji między `cust` i `ord` jest oddzielone, ustawiając klucz obcy `ord.CustomerID` na wartość null. Nie powoduje usunięcia wiersz odpowiadający `ord`.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykonuje następujące przetwarzania, gdy obiekt zostanie usunięty (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) z jego tabeli:  
  
-   Gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana, `DELETE` operacja została wykonana dla tego obiektu.  
  
-   Usunięcie nie są propagowane do powiązanych obiektów, niezależnie od tego, czy są one załadowane. W szczególności obiekty powiązane nie są ładowane do aktualizacji właściwości relacji.  
  
-   Po pomyślnym wykonaniu <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, obiekty są ustawione na `Deleted` stanu. W rezultacie nie można użyć obiektu lub jego `id` , <xref:System.Data.Linq.DataContext>. Wewnętrznej pamięci podręcznej, obsługiwane przez <xref:System.Data.Linq.DataContext> wystąpienia nie powoduje usunięcia obiektów, które są pobierane lub dodać jako nowy, mimo zostały usunięte obiekty w bazie danych.  
  
 Możesz wywołać <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> tylko na obiekcie śledzone przez <xref:System.Data.Linq.DataContext>. Aby uzyskać `Untracked` obiektu, należy wywołać <xref:System.Data.Linq.Table%601.Attach%2A> przed wywołaniem <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>. Wywoływanie <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> na `Untracked` obiektu zgłasza wyjątek.  
  
> [!NOTE]
>  Usuwanie obiektu z tabelą informuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] do wygenerowania odpowiedniego SQL `DELETE` polecenia w czasie <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Ta akcja nie usunąć obiekt z pamięci podręcznej lub propagowane do usunięcia powiązanych obiektów.  
>   
>  Aby odzyskać `id` usuniętego obiektu, użyj nowego <xref:System.Data.Linq.DataContext> wystąpienia. Oczyszczanie powiązane obiekty, można użyć *usuwanie kaskadowe* funkcji bazy danych, w przeciwnym razie ręcznie usunąć powiązane obiekty.  
>   
>  Nie masz powiązanych obiektów do usunięcia w dowolnej kolejności specjalne (w przeciwieństwie do bazy danych).  
  
## <a name="updating-objects"></a>Aktualizowanie obiektów  
 Można wykryć `Updates` przez obserwację powiadomienia o zmianach. Powiadomienia są realizowane za pośrednictwem <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> zdarzenia w metod ustawiających właściwości. Gdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest powiadamiany o pierwszej zmianie do obiektu, tworzy kopię obiektu i rozważa obiekt kandydat do generowania `Update` instrukcji.  
  
 Dla obiektów, które nie implementują <xref:System.ComponentModel.INotifyPropertyChanging>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przechowuje kopię wartości, które obiektów, których dotyczy, jeśli zostały one najpierw zmaterializowany. Gdy wywołujesz <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] porównuje bieżące i oryginalne wartości, aby zdecydować, czy obiekt został zmieniony.  
  
 Aktualizacje do relacji odwołanie z element podrzędny do elementu nadrzędnego (czyli odwołanie odpowiadający klucz obcy) są uznawane za urzędu. Odniesienia w odwrotnym kierunku (czyli z elementu nadrzędnego do elementu podrzędnego) jest opcjonalny. Klasy relacji (<xref:System.Data.Linq.EntitySet%601> i <xref:System.Data.Linq.EntityRef%601>) gwarantuje, że odwołania dwukierunkowych są spójne dla relacji jeden do wielu i jeden do jednego. Jeśli nie korzysta z modelu obiektów <xref:System.Data.Linq.EntitySet%601> lub <xref:System.Data.Linq.EntityRef%601>, a jeśli występuje odwołanie wsteczne jest odpowiedzialny za Utrzymaj spójne z odwołaniem do przodu po zaktualizowaniu relacji.  
  
 Jeśli zaktualizujesz zarówno wymagane odwołania, jak i odpowiedniego klucza obcego, upewnij się, że użytkownik wyrazi zgodę. <xref:System.InvalidOperationException> Wyjątek jest generowany, jeśli dwa nie są zsynchronizowane w czasie, który można wywoływać <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Mimo, że zmiany wartości klucza obcego są wystarczające do wywierania wpływu na aktualizację wiersz podstawowy, należy zmienić odwołania, który zapewnia łączność obiektu spójności wykresu i dwukierunkowe relacje.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Operacje wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)
