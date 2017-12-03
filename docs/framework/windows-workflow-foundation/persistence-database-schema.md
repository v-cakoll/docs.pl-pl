---
title: "Schemat bazy danych trwałości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a363cc8f43e4d2c4126d4287a3c998e9b8adecf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="persistence-database-schema"></a>Schemat bazy danych trwałości
W tym temacie opisano publicznie obsługiwane przez Magazyn wystąpienia przepływu pracy SQL.  
  
## <a name="instances-view"></a>Widok wystąpień  
 **Wystąpień** zawiera ogólne informacje o wszystkich wystąpień przepływu pracy w bazie danych.  
  
|Nazwa kolumny|Typ kolumny|Opis|  
|-----------------|-----------------|-----------------|  
|Identyfikator wystąpienia|Unikatowy identyfikator|Identyfikator wystąpienia przepływu pracy.|  
|PendingTimer|DataGodzina|Wskazuje, że przepływ pracy jest zablokowany na działaniu Delay i zostanie wznowione po wygaśnięciu czasomierza. Ta wartość może być zerowy, jeśli przepływ pracy nie zostanie zablokowany, oczekiwanie na czasomierz wygaśnie.|  
|CreationTime|DataGodzina|Wskazuje, kiedy przepływ pracy został utworzony.|  
|LastUpdatedTime|DataGodzina|Wskazuje godzinę ostatniego przepływ pracy został utrwalonego do bazy danych.|  
|ServiceDeploymentId|BigInt|Działa jako klucz obcy do widoku [ServiceDeployments]. Jeśli bieżące wystąpienie przepływu pracy jest wystąpieniem usługi hostowanej w sieci web, ta kolumna zawiera wartość, w przeciwnym razie jest ustawiona na wartość NULL.|  
|SuspensionExceptionName|Nvarchar(450)|Wskazuje typ wyjątku (np. InvalidOperationException), który spowodował Aby wstrzymać przepływ pracy.|  
|SuspensionReason|nvarchar(max)|Wskazuje, dlaczego wystąpienia przepływu pracy zostało zawieszone. Jeśli wyjątek spowodował wystąpienie wstrzymania, ta kolumna zawiera komunikat skojarzony z wyjątkiem.<br /><br /> Jeśli wystąpienie ręcznie zostało zawieszone, ta kolumna zawiera określone przez użytkownika przyczynę wstrzymanie tego wystąpienia.|  
|ActiveBookmarks|nvarchar(max)|Jeśli wystąpienie przepływu pracy jest bezczynny, ta właściwość wskazuje zakładki, jakie wystąpienie jest zablokowana na. Jeśli wystąpienie nie jest bezczynny, ta kolumna ma wartość NULL.|  
|CurrentMachine|Nvarchar(128)|Wskazuje, że nazwa komputera ma obecnie przepływu pracy, które wystąpienie załadowanych do pamięci.|  
|LastMachine|Nvarchar(450)|Wskazuje ostatni komputer, który załadować wystąpienia przepływu pracy.|  
|ExecutionStatus|Nvarchar(450)|Wskazuje bieżący stan wykonania przepływu pracy. Możliwe stany zawierają **Executing**, **bezczynny**, **zamknięte**.|  
|IsInitialized|bitowe|Wskazuje, czy wystąpienie przepływu pracy zostało zainicjowane. Wystąpienie przepływu pracy zainicjowane jest co najmniej raz utrwalonego wystąpienia przepływu pracy.|  
|IsSuspended|bitowe|Wskazuje, czy wystąpienie przepływu pracy zostało zawieszone.|  
|IsCompleted|bitowe|Wskazuje, czy wystąpienie przepływu pracy zakończono wykonywanie. **Uwaga:** Iif **InstanceCompletionAction** właściwość jest ustawiona na **DeleteAll**, wystąpienia są usuwane z widoku po zakończeniu.|  
|EncodingOption|TinyInt|Opis kodowania służący do serializowania danych właściwości.<br /><br /> -0 – bez kodowania<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|Varbinary(max)|Zawiera właściwości danych serializowanym wystąpieniu dostarczane do środowiska uruchomieniowego przepływu pracy po załadowaniu wystąpienie.<br /><br /> Każda właściwość pierwotna jest natywny typ CLR, co oznacza, że nie specjalne zestawy są niezbędne do deserializacji obiektu blob.|  
|WriteOnlyPrimitiveDataProperties|Varbinary(max)|Zawiera właściwości danych serializowanym wystąpieniu, które nie są dostarczane do środowiska uruchomieniowego przepływu pracy po załadowaniu tego wystąpienia.<br /><br /> Każda właściwość pierwotna jest natywny typ CLR, co oznacza, że nie specjalne zestawy są niezbędne do deserializacji obiektu blob.|  
|ReadWriteComplexDataProperties|Varbinary(max)|Zawiera właściwości danych serializowanym wystąpieniu dostarczane do środowiska uruchomieniowego przepływu pracy po załadowaniu tego wystąpienia.<br /><br /> Deserializator wymaga znajomości wszystkich typów obiektów przechowywanych w tym obiekcie blob.|  
|WriteOnlyComplexDataProperties|Varbinary(max)|Zawiera właściwości danych serializowanym wystąpieniu, które nie są dostarczane do środowiska uruchomieniowego przepływu pracy po załadowaniu tego wystąpienia.<br /><br /> Deserializator wymaga znajomości wszystkich typów obiektów przechowywanych w tym obiekcie blob.|  
|IdentityName|nvarchar(max)|Nazwa definicji przepływu pracy.|  
|IdentityPackage|nvarchar(max)|Pakiet informacje podane podczas tworzenia przepływu pracy (np. Nazwa zestawu).|  
|Kompilacja|BigInt|Numer kompilacji wersji przepływu pracy.|  
|Główne|BigInt|Główny numer wersji przepływu pracy.|  
|Pomocnicza|BigInt|Drobne numer wersji przepływu pracy.|  
|Poprawki|BigInt|Numer poprawki wersji przepływu pracy.|  
  
> [!CAUTION]
>  **Wystąpień** widok zawiera także wyzwalacza Delete. Użytkownicy z odpowiednimi uprawnieniami mogą wykonywać instrukcje usuwania tego widoku, który wymusza spowoduje usunięcie wystąpienia przepływu pracy z bazy danych. Zaleca się usunięcie bezpośrednio z widoku tylko w ostateczności, ponieważ usunięcie wystąpienia z pod środowiska uruchomieniowego przepływu pracy może spowodować niezamierzone skutki. Zamiast tego użyj punkt końcowy zarządzania wystąpienia przepływu pracy, aby zakończyć wystąpienia środowiska uruchomieniowego przepływu pracy. Jeśli chcesz usunąć dużą liczbę wystąpień z widoku, upewnij się, że nie ma żadnych aktywnych środowisk uruchomieniowych może działać w tych wystąpieniach.  
  
## <a name="servicedeployments-view"></a>Widok ServiceDeployments  
 **ServiceDeployments** widok zawiera informacje na temat wdrażania dla wszystkich aplikacji sieci Web (IIS / WAS) hostowanych usług przepływu pracy. Każde wystąpienie przepływu pracy, która jest hostowana w sieci Web będzie zawierać **ServiceDeploymentId** odwołujący się do wiersza, w tym widoku.  
  
|Nazwa kolumny|Typ kolumny|Opis|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|Klucz podstawowy dla tego widoku.|  
|Nazwa witryny|nvarchar(max)|Reprezentuje nazwę lokacji, który zawiera usługi przepływu pracy (np. **domyślna witryna sieci Web**).|  
|RelativeServicePath|nvarchar(max)|Reprezentuje ścieżkę wirtualną względem lokacji, który wskazuje usługi przepływu pracy. (np.  **/app1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|nvarchar(max)|Reprezentuje ścieżkę wirtualną względem lokacji, która wskazuje aplikacji, która zawiera usługi przepływu pracy. (np. **/App1**).|  
|ServiceName|nvarchar(max)|Reprezentuje nazwę usługi przepływu pracy. (np. **PurchaseOrderService**).|  
|ServiceNamespace|nvarchar(max)|Reprezentuje przestrzeni nazw usługi przepływu pracy. (np. **Moja firma**).|  
  
 Widok ServiceDeployments zawiera również wyzwalacza Delete. Użytkownicy z odpowiednimi uprawnieniami mogą wykonywać instrukcje usuwania tego widoku, aby usunąć wpisy ServiceDeployment z bazy danych. Należy pamiętać o następujących kwestiach:  
  
1.  Usuwanie wpisów z tego widoku jest kosztowne, ponieważ cała baza danych musi być zablokowany przed wykonaniem tej operacji. Jest to konieczne uniknąć scenariusz, w którym może odnosić się do nieistniejącego wpisu ServiceDeployment wystąpienia przepływu pracy. Usuń z tego widoku tylko w dół razy / okna obsługi.  
  
2.  Próby usunięcia wiersza ServiceDeployment, który odwołuje się do wpisów w **wystąpień** widoku wynikiem będzie pusta. Można usunąć tylko wiersze ServiceDeployment z odwołania zerowego.  
  
## <a name="instancepromotedproperties-view"></a>Widok InstancePromotedProperties  
 **InstancePromotedProperties** widok zawiera informacje o wszystkich awansowanej właściwości, które są określone przez użytkownika. Awansowanej właściwości działa jako najwyższej jakości właściwości, które użytkownik może używać w zapytaniach można pobrać wystąpień.  Na przykład użytkownik może dodawać PurchaseOrder podwyższania poziomu, który zawsze przechowuje koszt kolejności, w **wartość1** kolumny. Umożliwi użytkownikowi zapytania dla wszystkich zakupów, których koszt przekracza określoną wartość.  
  
|Typ kolumny|Typ kolumny|Opis|  
|-|-|-|  
|Identyfikator wystąpienia|Unikatowy identyfikator|Identyfikator wystąpienia przepływu pracy|  
|EncodingOption|TinyInt|Opisuje, kodowanie, używany do serializacji awansowanej właściwości binarnych.<br /><br /> -0 – bez kodowania<br />-1 – GZipStream|  
|PromotionName|Nvarchar(400)|Nazwa promocji skojarzony z tym wystąpieniem. PromotionName jest potrzebne do dodania kontekstu do ogólnego kolumny w tym wierszu.<br /><br /> Na przykład PromotionName PurchaseOrder może wskazywać, że wartość1 zawiera koszt kolejności, wartość2 zawiera nazwę odbiorcy, dla którego złożone zamówienie, wartość 3 zawiera adres odbiorcy i tak dalej.|  
|Wartość [1-32]|Element SqlVariant|Wartość [1-32] zawiera wartości, które mogą być przechowywane w kolumnie SqlVariant. Pojedynczy podwyższania poziomu nie może zawierać więcej niż 32 SqlVariants.|  
|Wartość [33 64]|Varbinary(max)|Wartość [33 64] zawiera seryjnych wartości. Na przykład Value33 mogą zawierać JPEG zostały zakupione elementu. Pojedynczy podwyższania poziomu nie może zawierać więcej niż 32 właściwości binarnych|  
  
 Widok InstancePromotedProperties jest schematem, co oznacza, że użytkownicy mogą dodawać indeksów na co najmniej jedną kolumnę w celu zoptymalizowania zapytań dotyczących tego widoku.  
  
> [!NOTE]
>  Widok indeksowany wymaga więcej pamięci masowej i dodaje dodatkowe obciążenie. Zapoznaj się z [poprawę wydajności przy użyciu programu SQL Server 2008 indeksowanych widoków](http://go.microsoft.com/fwlink/?LinkId=179529) Aby uzyskać więcej informacji.
