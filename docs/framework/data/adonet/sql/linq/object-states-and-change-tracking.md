---
title: Stany obiektów i śledzenie zmian
ms.date: 03/30/2017
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
ms.openlocfilehash: a9df200f4d2e5f64bf5883c7bc513ba7129dcaad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781278"
---
# <a name="object-states-and-change-tracking"></a>Stany obiektów i śledzenie zmian

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obiekty zawsze uczestniczą w pewnym *stanie*. Na przykład podczas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzenia nowego obiektu obiekt jest w `Unchanged` stanie. Nowy obiekt tworzony przez siebie jest nieznany dla <xref:System.Data.Linq.DataContext> i jest w `Untracked` stanie. Po pomyślnym <xref:System.Data.Linq.DataContext.SubmitChanges%2A>wykonaniu elementu wszystkie obiekty [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] znane jako `Unchanged` są w stanie. (Pojedynczy wyjątek jest reprezentowany przez te, które zostały pomyślnie usunięte z bazy danych, które są w `Deleted` stanie i nie mogą być używane w tym <xref:System.Data.Linq.DataContext> wystąpieniu).

## <a name="object-states"></a>Stany obiektów

Poniższa tabela zawiera listę możliwych stanów [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektów.

|Stan|Opis|
|-----------|-----------------|
|`Untracked`|Obiekt, który nie jest [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]śledzony przez. Przykłady obejmują następujące elementy:<br /><br /> -Obiekt nie jest wysyłany do zapytania za <xref:System.Data.Linq.DataContext> pomocą bieżącego (na przykład nowo utworzonego obiektu).<br />-Obiekt utworzony przy użyciu deserializacji<br />-Obiekt odpytany za pomocą innego <xref:System.Data.Linq.DataContext>elementu.|
|`Unchanged`|Obiekt pobrany przy użyciu bieżącego <xref:System.Data.Linq.DataContext> i nieznanego elementu został zmodyfikowany od czasu jego utworzenia.|
|`PossiblyModified`|Obiekt, który jest *dołączony* do <xref:System.Data.Linq.DataContext>. Aby uzyskać więcej informacji, zobacz [operacje pobierania i cud danych w aplikacjach N-warstwowych (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md).|
|`ToBeInserted`|Nie pobrano obiektu przy użyciu bieżącego <xref:System.Data.Linq.DataContext>elementu. Powoduje to, że `INSERT` baza <xref:System.Data.Linq.DataContext.SubmitChanges%2A>danych jest w trakcie.|
|`ToBeUpdated`|Wiadomo, że obiekt został zmodyfikowany od czasu jego pobrania. Powoduje to, że `UPDATE` baza <xref:System.Data.Linq.DataContext.SubmitChanges%2A>danych jest w trakcie.|
|`ToBeDeleted`|Obiekt oznaczony do usunięcia, który powoduje wystąpienie bazy `DELETE` danych <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|
|`Deleted`|Obiekt, który został usunięty z bazy danych. Ten stan jest końcowy i nie zezwala na dodatkowe przejścia.|

## <a name="inserting-objects"></a>Wstawianie obiektów

Można jawnie zażądać `Inserts` przy użyciu <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>. Alternatywnie można wnioskować `Inserts` o znalezienie obiektów podłączonych do jednego z znanych obiektów, które muszą zostać zaktualizowane. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Na przykład, jeśli dodasz `Untracked` obiekt <xref:System.Data.Linq.EntitySet%601> do `Untracked` obiektu lub ustawisz <xref:System.Data.Linq.EntityRef%601> obiekt jako, `Untracked` obiekt jest dostępny w drodze śledzenia obiektów na grafie. Podczas przetwarzania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przechodzą śledzone obiekty i odnajduje wszystkie dostępne trwałe obiektów trwałych, które nie są śledzone. Takie obiekty są kandydatami do wstawienia do bazy danych programu.

W przypadku <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>klas w hierarchii dziedziczenia (`o`) ustawia również wartość elementu członkowskiego wyznaczono jako *rozróżniacz* do dopasowania do typu obiektu. `o` W przypadku typu zgodnego z domyślną wartością rozróżniacza ta akcja powoduje nadpisanie wartości rozróżniacza wartością domyślną. Aby uzyskać więcej informacji, zobacz [Obsługa dziedziczenia](inheritance-support.md).

> [!IMPORTANT]
> Obiekt dodany do `Table` nie znajduje się w pamięci podręcznej tożsamości. Pamięć podręczna tożsamości odzwierciedla tylko te dane, które są pobierane z bazy danych. Po wywołaniu, dodana <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>jednostka nie pojawia się w zapytaniach dotyczących bazy danych, dopóki <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nie zostanie ukończona pomyślnie.

## <a name="deleting-objects"></a>Usuwanie obiektów

Można oznaczyć śledzony obiekt `o` do usunięcia przez wywołanie <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(o) odpowiednie <xref:System.Data.Linq.Table%601>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traktuje usunięcie obiektu z programu <xref:System.Data.Linq.EntitySet%601> jako operacji aktualizacji, a odpowiednia wartość klucza obcego jest ustawiona na wartość null. Element docelowy operacji (`o`) nie jest usuwany z tabeli. Na przykład `cust.Orders.DeleteOnSubmit(ord)` wskazuje aktualizację, w której relacja między `cust` i `ord` jest poważna przez ustawienie klucza `ord.CustomerID` obcego na null. Nie powoduje usunięcia wiersza odpowiadającego `ord`elementowi.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wykonuje następujące przetwarzanie po usunięciu obiektu (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) z tabeli:

- Gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana `DELETE` , wykonywana jest operacja dla tego obiektu.

- Usunięcie nie jest propagowane do powiązanych obiektów, niezależnie od tego, czy są one załadowane. W konkretnym przypadku powiązane obiekty nie są ładowane do aktualizacji właściwości relacji.

- Po pomyślnym <xref:System.Data.Linq.DataContext.SubmitChanges%2A>wykonaniu obiektu są ustawiane `Deleted` stan. W związku z tym nie można użyć obiektu ani jego `id` w tym <xref:System.Data.Linq.DataContext>elemencie. Wewnętrzna pamięć podręczna obsługiwana przez <xref:System.Data.Linq.DataContext> wystąpienie nie eliminuje obiektów, które są pobierane lub dodawane jako nowe, nawet po usunięciu obiektów w bazie danych.

Można wywołać <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> tylko dla obiektu śledzonego <xref:System.Data.Linq.DataContext>przez. Dla obiektu należy wywołać <xref:System.Data.Linq.Table%601.Attach%2A> przed wywołaniem <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>. `Untracked` Wywołanie <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>obiektuzgłaszawyjątek `Untracked` .

> [!NOTE]
> Usunięcie obiektu z tabeli informuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o wygenerowaniu odpowiedniego <xref:System.Data.Linq.DataContext.SubmitChanges%2A>polecenia SQL `DELETE` w czasie. Ta akcja nie powoduje usunięcia obiektu z pamięci podręcznej ani propagowania usuwania do powiązanych obiektów.
>
> Aby odzyskiwać `id` usunięty obiekt, Użyj nowego <xref:System.Data.Linq.DataContext> wystąpienia. W celu oczyszczenia obiektów pokrewnych można użyć funkcji *kaskadowego usuwania* bazy danych lub ręcznie usunąć powiązane obiekty.
>
> Powiązane obiekty nie muszą być usuwane w żadnej specjalnej kolejności (w przeciwieństwie do bazy danych).

## <a name="updating-objects"></a>Aktualizowanie obiektów

Możesz wykryć `Updates` , obserwując powiadomienia o zmianach. Powiadomienia są udostępniane za pomocą <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> zdarzenia w metodach ustawiających właściwości. Gdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest powiadamiany o pierwszej zmianie do obiektu, tworzy kopię obiektu i traktuje obiekt jako kandydat do `Update` wygenerowania instrukcji.

W przypadku obiektów, które nie <xref:System.ComponentModel.INotifyPropertyChanging>implementują, program [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zachowuje kopię wartości, które obiekty miały po raz pierwszy. Po wywołaniu <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, porównuje bieżące i oryginalne wartości, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aby zdecydować, czy obiekt został zmieniony.

W przypadku aktualizacji relacji odwołanie od elementu podrzędnego do elementu nadrzędnego (czyli odwołanie odpowiadające kluczowi obcemu) jest uznawane za urząd. Odwołanie w odwrotnym kierunku (czyli z elementu nadrzędnego do elementu podrzędnego) jest opcjonalne. Klasy relacji (<xref:System.Data.Linq.EntitySet%601> i <xref:System.Data.Linq.EntityRef%601>) gwarantują, że odwołania dwukierunkowe są spójne dla relacji jeden-do-wielu i jeden-do-jednego. Jeśli model obiektu nie używa <xref:System.Data.Linq.EntitySet%601> lub <xref:System.Data.Linq.EntityRef%601>, a jeśli istnieje odwołanie wsteczne, jest on odpowiedzialny za zachowanie zgodności z odwołaniem do przodu podczas aktualizowania relacji.

W przypadku zaktualizowania zarówno wymaganego odwołania, jak i odpowiedniego klucza obcego należy upewnić się, że zgadzają się. Wyjątek jest zgłaszany, jeśli dwa nie są zsynchronizowane w momencie wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. <xref:System.InvalidOperationException> Chociaż zmiany wartości klucza obcego są wystarczające do wpływu na aktualizację wiersza bazowego, należy zmienić odwołanie, aby zachować łączność z wykresem obiektów i dwukierunkową spójnością relacji.

## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
- [Operacje wstawiania, aktualizowania i usuwania](insert-update-and-delete-operations.md)
