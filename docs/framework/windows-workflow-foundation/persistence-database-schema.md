---
title: Schemat bazy danych stanów trwałych
ms.date: 03/30/2017
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
ms.openlocfilehash: 025e04acb0d9cf75ea54814274c1875f8661eb88
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802508"
---
# <a name="persistence-database-schema"></a>Schemat bazy danych stanów trwałych
W tym temacie opisano widoki publiczne obsługiwane przez magazyn wystąpień przepływu pracy SQL.  
  
## <a name="instances-view"></a>Widok wystąpień  
 Widok **wystąpienia** zawiera ogólne informacje o wszystkich wystąpieniach przepływu pracy w bazie danych.  
  
|Nazwa kolumny|Typ kolumny|Opis|  
|-----------------|-----------------|-----------------|  
|InstanceId|UniqueIdentifier|Identyfikator wystąpienia przepływu pracy.|  
|PendingTimer|DataGodzina|Wskazuje, że przepływ pracy jest blokowany na działanie opóźnienia i zostanie wznowiony po wygaśnięciu czasomierza. Ta wartość może być równa null, jeśli przepływ pracy nie zostanie zablokowany, oczekując na wygaśnięcie czasomierza.|  
|CreationTime|DataGodzina|Wskazuje, kiedy przepływ pracy został utworzony.|  
|LastUpdatedTime|DataGodzina|Wskazuje czas, w którym przepływ pracy został utrwalony w bazie danych.|  
|ServiceDeploymentId|BigInt|Działa jako klucz obcy w widoku [ServiceDeployments]. Jeśli bieżące wystąpienie przepływu pracy jest wystąpieniem usługi hostowanej w sieci Web, ta kolumna ma wartość, w przeciwnym razie jest ustawiona na wartość NULL.|  
|SuspensionExceptionName|Nvarchar(450)|Wskazuje typ wyjątku (np. InvalidOperationException), który spowodował wstrzymanie przepływu pracy.|  
|SuspensionReason|Nvarchar (max)|Wskazuje, dlaczego wystąpienie przepływu pracy zostało zawieszone. Jeśli wyjątek spowodował wstrzymanie wystąpienia, ta kolumna zawiera komunikat skojarzony z wyjątkiem.<br /><br /> Jeśli wystąpienie zostało wstrzymane ręcznie, ta kolumna zawiera powód określony przez użytkownika do zawieszania wystąpienia.|  
|ActiveBookmarks|Nvarchar (max)|Jeśli wystąpienie przepływu pracy jest bezczynne, ta właściwość wskazuje, w jakich zakładkach wystąpienie jest zablokowane. Jeśli wystąpienie nie jest bezczynne, ta kolumna ma wartość NULL.|  
|CurrentMachine|Nvarchar(128)|Wskazuje, że nazwa komputera ma obecnie załadowane wystąpienie przepływu pracy w pamięci.|  
|LastMachine|Nvarchar(450)|Wskazuje ostatni komputer, który załadował wystąpienie przepływu pracy.|  
|ExecutionStatus|Nvarchar(450)|Wskazuje bieżący stan wykonywania przepływu pracy. Możliwe stany to **wykonywanie**, **bezczynne**i **zamknięte**.|  
|IsInitialized|bit|Wskazuje, czy wystąpienie przepływu pracy zostało zainicjowane. Zainicjowane wystąpienie przepływu pracy to wystąpienie przepływu pracy, które zostało utrwalone co najmniej raz.|  
|Issuspended|bit|Wskazuje, czy wystąpienie przepływu pracy zostało zawieszone.|  
|IsCompleted|bit|Wskazuje, czy wystąpienie przepływu pracy zostało zakończone. **Uwaga:**  IIf Właściwość **InstanceCompletionAction** jest ustawiona na **DeleteAll**, wystąpienia są usuwane z widoku po zakończeniu.|  
|EncodingOption|TinyInt|Opisuje kodowanie używane do serializacji właściwości danych.<br /><br /> -0 — bez kodowania<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|Varbinary (max)|Zawiera serializowane właściwości danych wystąpienia, które zostaną dostarczone z powrotem do środowiska uruchomieniowego przepływu pracy po załadowaniu wystąpienia.<br /><br /> Każda właściwość pierwotna jest natywnym typem CLR, co oznacza, że żadne specjalne zestawy nie są konieczne do deserializacji obiektu BLOB.|  
|WriteOnlyPrimitiveDataProperties|Varbinary (max)|Zawiera serializowane właściwości danych wystąpienia, które nie są przekazywane z powrotem do środowiska uruchomieniowego przepływu pracy po załadowaniu wystąpienia.<br /><br /> Każda właściwość pierwotna jest natywnym typem CLR, co oznacza, że żadne specjalne zestawy nie są konieczne do deserializacji obiektu BLOB.|  
|ReadWriteComplexDataProperties|Varbinary (max)|Zawiera serializowane właściwości danych wystąpienia, które zostaną dostarczone z powrotem do środowiska uruchomieniowego przepływu pracy po załadowaniu wystąpienia.<br /><br /> Deserializator będzie wymagał znajomości wszystkich typów obiektów przechowywanych w tym obiekcie blob.|  
|WriteOnlyComplexDataProperties|Varbinary (max)|Zawiera serializowane właściwości danych wystąpienia, które nie są przekazywane z powrotem do środowiska uruchomieniowego przepływu pracy po załadowaniu wystąpienia.<br /><br /> Deserializator będzie wymagał znajomości wszystkich typów obiektów przechowywanych w tym obiekcie blob.|  
|IdentityName|Nvarchar (max)|Nazwa definicji przepływu pracy.|  
|IdentityPackage|Nvarchar (max)|Informacje o pakiecie, które zostały utworzone podczas tworzenia przepływu pracy (takie jak nazwa zestawu).|  
|{1&gt;Kompilacja&lt;1}|BigInt|Numer kompilacji wersji przepływu pracy.|  
|Ważna|BigInt|Numer główny przepływu pracy.|  
|Drobna|BigInt|Numer pomocniczy wersji przepływu pracy.|  
|Poprawki|BigInt|Numer poprawki wersji przepływu pracy.|  
  
> [!CAUTION]
> Widok **wystąpień** zawiera również wyzwalacz usuwania. Użytkownicy z odpowiednimi uprawnieniami mogą wykonywać instrukcje usuwania względem tego widoku, który wymusił wymuszenie usunięcia wystąpień przepływu pracy z bazy danych. Zalecamy usunięcie bezpośrednio z widoku tylko w ostatnim przypadku, ponieważ usunięcie wystąpienia z poniżej środowiska uruchomieniowego przepływu pracy może spowodować niezamierzone konsekwencje. Zamiast tego należy użyć punktu końcowego zarządzania wystąpieniem przepływu pracy, aby zakończyć działanie wystąpienia przepływu pracy. Jeśli chcesz usunąć dużą liczbę wystąpień z widoku, upewnij się, że nie ma aktywnych środowisk uruchomieniowych, które mogą działać na tych wystąpieniach.  
  
## <a name="servicedeployments-view"></a>Widok ServiceDeployments  
 Widok **ServiceDeployments** zawiera informacje o wdrożeniu dla wszystkich hostowanych usług przepływu pracy w sieci Web (IIS/was). Każde wystąpienie przepływu pracy, które jest hostowane w sieci Web, będzie zawierało element **ServiceDeploymentId** , który odwołuje się do wiersza w tym widoku.  
  
|Nazwa kolumny|Typ kolumny|Opis|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|Klucz podstawowy dla tego widoku.|  
|SiteName|Nvarchar (max)|Reprezentuje nazwę witryny zawierającej usługę przepływu pracy (np. **Domyślna witryna sieci Web**).|  
|RelativeServicePath|Nvarchar (max)|Reprezentuje ścieżkę wirtualną względem lokacji, która wskazuje usługę przepływu pracy. tj.  **/APP1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|Nvarchar (max)|Reprezentuje ścieżkę wirtualną względem lokacji, która wskazuje na aplikację, która zawiera usługę przepływu pracy. (np. **/APP1**).|  
|ServiceName|Nvarchar (max)|Reprezentuje nazwę usługi przepływu pracy. (np. **PurchaseOrderService**).|  
|ServiceNamespace|Nvarchar (max)|Reprezentuje przestrzeń nazw usługi przepływu pracy. (np. **firma firmy**).|  
  
 Widok ServiceDeployments zawiera również wyzwalacz Delete. Użytkownicy z odpowiednimi uprawnieniami mogą wykonywać instrukcje usuwania względem tego widoku w celu usunięcia wpisów ServiceDeployment z bazy danych. Należy pamiętać o następujących kwestiach:  
  
1. Usuwanie wpisów z tego widoku jest kosztowne, ponieważ cała baza danych musi być zablokowana przed wykonaniem tej operacji. Jest to konieczne, aby uniknąć scenariusza, w którym wystąpienie przepływu pracy może odwoływać się do nieistniejącego wpisu ServiceDeployment. Usuń z tego widoku tylko w oknach czasu lub obsługi.  
  
2. Każda próba usunięcia wiersza ServiceDeployment, do którego odwołuje się wpisy w widoku **wystąpień** , spowoduje, że nie będzie to miało znaczenia. Można usunąć tylko wiersze ServiceDeployment z odwołaniami do zera.  
  
## <a name="instancepromotedproperties-view"></a>Widok InstancePromotedProperties  
 Widok **InstancePromotedProperties** zawiera informacje o wszystkich podwyższonych właściwościach, które są określone przez użytkownika. Awansowana funkcja właściwości jako właściwość pierwszej klasy, której użytkownik może używać w zapytaniach do pobierania wystąpień.  Na przykład użytkownik może dodać promocję PurchaseOrder, która zawsze przechowuje koszt zamówienia w kolumnie **wartość1** . Umożliwi to użytkownikowi wykonywanie zapytań dotyczących wszystkich zamówień zakupu, których koszt przekracza określoną wartość.  
  
|Typ kolumny|Typ kolumny|Opis|  
|-|-|-|  
|InstanceId|UniqueIdentifier|Identyfikator wystąpienia przepływu pracy|  
|EncodingOption|TinyInt|Opisuje kodowanie używane do serializacji wyróżnionych właściwości binarnych.<br /><br /> -0 — bez kodowania<br />-1 – GZipStream|  
|Podwyższanie poziomu|Nvarchar(400)|Nazwa promocji skojarzonej z tym wystąpieniem. Do dodania kontekstu do kolumn ogólnych w tym wierszu jest wymagana podwyższanie poziomu.<br /><br /> Na przykład PurchaseOrder Promocjaname może wskazywać, że wartość1 zawiera koszt zamówienia, wartość2 zawiera nazwę klienta, który złożył zamówienie, wartość 3 zawiera adres klienta itd.|  
|Wartość [1 – 32]|Element sqlvariant|Wartość [1-32] zawiera wartości, które mogą być przechowywane w kolumnie sqlvariant. Pojedyncze podwyższanie poziomu nie może zawierać więcej niż 32 wariantów.|  
|Wartość [33-64]|Varbinary (max)|Wartość [33-64] zawiera zserializowane wartości. Na przykład Value33 może zawierać JPEG zakupionego elementu. Pojedyncze podwyższanie poziomu nie może zawierać więcej niż 32 właściwości binarnych|  
  
 Widok InstancePromotedProperties jest powiązany ze schematem, co oznacza, że użytkownicy mogą dodawać indeksy w co najmniej jednej kolumnie, aby zoptymalizować zapytania względem tego widoku.  
  
> [!NOTE]
> Widok indeksowany wymaga większej ilości miejsca do magazynowania i dodaje dodatkowe obciążenie związane z przetwarzaniem. Aby uzyskać więcej informacji, zapoznaj się z tematem [poprawa wydajności w widokach indeksowanych SQL Server 2008](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd171921(v=sql.100)) .
