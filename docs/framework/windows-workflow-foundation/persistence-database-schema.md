---
title: Schemat bazy danych stanów trwałych
ms.date: 03/30/2017
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
ms.openlocfilehash: 38df4b3d629840f1b5def2eafa0d074a2b2397a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864172"
---
# <a name="persistence-database-schema"></a>Schemat bazy danych stanów trwałych
W tym temacie opisano widoku publicznego obsługiwane przez Store wystąpienia przepływu pracy SQL.  
  
## <a name="instances-view"></a>Wyświetl wystąpienia  
 **Wystąpień** widok zawiera ogólne informacje o wszystkich wystąpień przepływu pracy w bazie danych.  
  
|Nazwa kolumny|Typ kolumny|Opis|  
|-----------------|-----------------|-----------------|  
|InstanceId|UniqueIdentifier|Identyfikator wystąpienia przepływu pracy.|  
|PendingTimer|DataGodzina|Wskazuje, że przepływ pracy jest zablokowany na działanie opóźnienie zostanie wznowione po upływie okresu działania czasomierza. Ta wartość może być wartość null, jeśli przepływ pracy nie jest zablokowany, trwa oczekiwanie na czasomierz wygaśnie.|  
|CreationTime|DataGodzina|Wskazuje, kiedy został utworzony przepływ pracy.|  
|LastUpdatedTime|DataGodzina|Wskazuje godzinę ostatniego, który przepływ pracy został zachowany w bazie danych.|  
|ServiceDeploymentId|BigInt|Działa jako klucza obcego w widoku [ServiceDeployments]. Jeśli bieżące wystąpienie przepływu pracy jest wystąpieniem usługi hostowanej w sieci web, ta kolumna zawiera wartości, w przeciwnym razie jest równa NULL.|  
|SuspensionExceptionName|Nvarchar(450)|Wskazuje typ wyjątku (np. InvalidOperationException), który spowodował wstrzymania przepływu pracy.|  
|SuspensionReason|Nvarchar(max)|Wskazuje, dlaczego wystąpienia przepływu pracy zostało wstrzymane. Jeśli wyjątek spowodowany wystąpieniem wstrzymania, ta kolumna zawiera komunikat skojarzony z wyjątkiem.<br /><br /> Jeśli wystąpienie ręcznie została wstrzymana, ta kolumna zawierała zawieszanie wystąpienie przyczynę określonych przez użytkownika.|  
|ActiveBookmarks|Nvarchar(max)|Jeśli wystąpienie przepływu pracy jest bezczynny, ta właściwość wskazuje zakładek, jakie wystąpienie została zablokowana na. Jeśli wystąpienie nie jest w stanie bezczynności, ta kolumna ma wartość NULL.|  
|CurrentMachine|Nvarchar(128)|Wskazuje, że nazwa komputera ma obecnie przepływu pracy, którego wystąpienie jest załadowany do pamięci.|  
|LastMachine|Nvarchar(450)|Wskazuje ostatni komputer, który załadować wystąpienia przepływu pracy.|  
|ExecutionStatus|Nvarchar(450)|Wskazuje bieżący stan wykonania przepływu pracy. Możliwe stany to **Executing**, **bezczynne**, **zamknięte**.|  
|IsInitialized|Bit|Wskazuje, czy wystąpienie przepływu pracy został zainicjowany. Wystąpienie zainicjowane przepływu pracy jest wystąpienie przepływu pracy, które zostały utrwalone w co najmniej raz.|  
|IsSuspended|Bit|Wskazuje, czy wystąpienie przepływu pracy zostało zawieszone.|  
|IsCompleted|Bit|Wskazuje, czy wystąpienie przepływu pracy zostało zakończone, wykonywanie. **Uwaga:**  IIf **InstanceCompletionAction** właściwość jest ustawiona na **DeleteAll**, wystąpienia są usuwane z widoku po jego ukończeniu.|  
|EncodingOption|TinyInt|W tym artykule opisano, kodowanie, służący do serializowania właściwości danych.<br /><br /> -0 — bez kodowania<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|Varbinary(max)|Zawiera właściwości danych Zserializowany wystąpienie, które będą dostarczane do środowiska uruchomieniowego przepływu pracy po załadowaniu wystąpienia.<br /><br /> Każda właściwość typu pierwotnego jest natywnego typu CLR, co oznacza, że żadne specjalne zestawy nie są potrzebne do deserializacji obiektu blob.|  
|WriteOnlyPrimitiveDataProperties|Varbinary(max)|Zawiera właściwości danych Zserializowany wystąpienie, które nie są dostarczane do środowiska wykonawczego przepływów pracy po załadowaniu wystąpienia.<br /><br /> Każda właściwość typu pierwotnego jest natywnego typu CLR, co oznacza, że żadne specjalne zestawy nie są potrzebne do deserializacji obiektu blob.|  
|ReadWriteComplexDataProperties|Varbinary(max)|Zawiera właściwości danych Zserializowany wystąpienie, które będą dostarczane do środowiska wykonawczego przepływów pracy po załadowaniu wystąpienia.<br /><br /> Deserializator wymaga znajomości wszystkich typów obiektów przechowywanych w tym obiekcie blob.|  
|WriteOnlyComplexDataProperties|Varbinary(max)|Zawiera właściwości danych Zserializowany wystąpienie, które nie są dostarczane do środowiska wykonawczego przepływów pracy po załadowaniu wystąpienia.<br /><br /> Deserializator wymaga znajomości wszystkich typów obiektów przechowywanych w tym obiekcie blob.|  
|IdentityName|Nvarchar(max)|Nazwa definicji przepływu pracy.|  
|IdentityPackage|Nvarchar(max)|Informacje o pakiecie, biorąc pod uwagę podczas tworzenia przepływu pracy (np. Nazwa zestawu).|  
|Kompilacja|BigInt|Numer kompilacji wersji przepływu pracy.|  
|Duży|BigInt|Główny numer wersji przepływu pracy.|  
|Mały|BigInt|Pomocnicza liczba wersji przepływu pracy.|  
|Poprawki|BigInt|Numer poprawki wersji przepływu pracy.|  
  
> [!CAUTION]
>  **Wystąpień** widok zawiera także wyzwalacza usuwania. Użytkownicy z odpowiednimi uprawnieniami mogą wykonywać instrukcji delete wykonywanych względem tego widoku, który wymusza spowoduje usunięcie wystąpienia przepływu pracy z bazy danych. Zaleca się usunięcie bezpośrednio z widoku tylko w ostateczności, ponieważ usunięcie wystąpienia z poniżej środowiska uruchomieniowego przepływu pracy może spowodować niezamierzone skutki. Zamiast tego należy użyć punkt końcowy zarządzania dla wystąpienia przepływu pracy, aby zakończyć wystąpienia środowiska uruchomieniowego przepływu pracy. Jeśli chcesz usunąć wielu wystąpień z widoku, upewnij się, że nie ma żadnych aktywnych środowisk uruchomieniowych może działać w tych wystąpieniach.  
  
## <a name="servicedeployments-view"></a>Widok ServiceDeployments  
 **ServiceDeployments** widok zawiera informacje na temat wdrażania dla wszystkich aplikacji sieci Web (IIS / WAS) hostowanych usług przepływu pracy. Każde wystąpienie przepływu pracy, która jest hostowana w sieci Web będzie zawierać **ServiceDeploymentId** odwołujący się do wiersza, w tym widoku.  
  
|Nazwa kolumny|Typ kolumny|Opis|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|Klucz podstawowy dla tego widoku.|  
|SiteName|Nvarchar(max)|Reprezentuje nazwę lokacji, który zawiera usługi przepływu pracy (np. **domyślna witryna sieci Web**).|  
|RelativeServicePath|Nvarchar(max)|Reprezentuje ścieżkę wirtualną względem lokacji, który wskazuje Usługa przepływu pracy. (e.g.  **/app1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|Nvarchar(max)|Reprezentuje ścieżkę wirtualną względem lokacji, który wskazuje na aplikację, która zawiera usługę przepływu pracy. (np. **/app1**).|  
|ServiceName|Nvarchar(max)|Przedstawia nazwę przepływu pracy usługi. (np. **PurchaseOrderService**).|  
|ServiceNamespace|Nvarchar(max)|Reprezentuje obszar nazw usługi przepływu pracy. (np. **Moja firma**).|  
  
 Widok ServiceDeployments zawiera również wyzwalacza usuwania. Użytkownicy z odpowiednimi uprawnieniami mogą wykonywać instrukcji delete wykonywanych względem tego widoku, aby usunąć wpisy ServiceDeployment z bazy danych. Należy pamiętać o następujących kwestiach:  
  
1. Usuwanie wpisów z tego widoku jest kosztowne, ponieważ cała baza danych musi być zablokowane przed wykonaniem tej operacji. Jest to konieczne uniknąć sytuacji, gdy wystąpienie przepływu pracy można odnoszą się do nieistniejącego wpisu ServiceDeployment. Usuń z tego widoku tylko w dół razy / okna obsługi.  
  
2. Dowolne próba usunięcia wiersza ServiceDeployment, który odwołuje się do wpisów w **wystąpień** widoku, wynikiem będzie pusta. Usunąć można tylko ServiceDeployment wiersze z odwołaniami, zerowego.  
  
## <a name="instancepromotedproperties-view"></a>Widok InstancePromotedProperties  
 **InstancePromotedProperties** widok zawiera informacje dla wszystkich właściwości o podwyższonym poziomie, które są określone przez użytkownika. Właściwości z podwyższonym poziomem działa jako właściwość pierwszej klasy, które użytkownik może używać w zapytaniach można pobrać wystąpień.  Na przykład użytkownik może dodać PurchaseOrder podwyższania poziomu, która zawsze przechowuje koszt kolejności, w **wartość1** kolumny. Umożliwi użytkownikowi zapytania dla wszystkich zamówień zakupu, w których koszt przekracza określoną wartość.  
  
|Typ kolumny|Typ kolumny|Opis|  
|-|-|-|  
|InstanceId|UniqueIdentifier|Identyfikator wystąpienia przepływu pracy|  
|EncodingOption|TinyInt|W tym artykule opisano, kodowanie, używany do serializacji o podwyższonym poziomie właściwości binarnych.<br /><br /> -0 — bez kodowania<br />-1 – GZipStream|  
|PromotionName|Nvarchar(400)|Nazwa podwyższania poziomu skojarzony z tym wystąpieniem. PromotionName jest potrzebny, aby dodać kontekst do ogólnego kolumn, w tym wierszu.<br /><br /> Na przykład PromotionName PurchaseOrder może wskazywać, że wartość1 zawiera koszt kolejność wartość2 zawiera nazwę klienta, który złożył zamówienie, wartość 3 zawiera adres odbiorcy i tak dalej.|  
|Wartość [1-32]|Element SqlVariant|Wartość [1-32] zawiera wartości, które mogą być przechowywane w kolumnie element SqlVariant. Pojedynczy podwyższania poziomu nie może zawierać więcej niż 32 SqlVariants.|  
|Wartość [33-64]|Varbinary(max)|Wartość [33-64] zawiera serializacji wartości. Na przykład Value33 może zawierać JPEG elementu w trakcie kupowania. Pojedynczy podwyższania poziomu nie może zawierać więcej niż 32 właściwości binarnych|  
  
 Widok InstancePromotedProperties jest schematu powiązane, co oznacza, że użytkownicy mogą dodawać indeksów na co najmniej jedną kolumnę, w celu optymalizacji zapytań dla tego widoku.  
  
> [!NOTE]
>  Widok indeksowany wymaga więcej pamięci masowej i dodaje dodatkowe obciążenie. Zapoznaj się [poprawę wydajności przy użyciu programu SQL Server 2008 indeksowanych widoków](https://go.microsoft.com/fwlink/?LinkId=179529) Aby uzyskać więcej informacji.
