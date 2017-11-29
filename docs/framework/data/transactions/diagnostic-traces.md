---
title: "Dane śledzenia diagnostycznego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 59e91b76245c7bdfd40f6fc449edbbcd47449f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="diagnostic-traces"></a>Dane śledzenia diagnostycznego
Ślady są publikowania określonych komunikatów, które są generowane podczas wykonywania aplikacji. Jeśli śledzenie, musi mieć mechanizm do gromadzenia i rejestrowania wiadomości, które mają być wysyłane. Przez odbiorniki odbierania komunikatów śledzenia. Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.  
  
 Jedno takie odbiornik <xref:System.Diagnostics.DefaultTraceListener>, jest automatycznie tworzone i inicjowana, gdy śledzenie jest włączone. Jeśli chcesz, aby dane wyjściowe śledzenia kierować do żadnych dodatkowych źródeł, należy utworzyć i zainicjować odbiorniki śledzenia dodatkowe. Odbiorniki, tworzonych powinny odzwierciedlać Twoich potrzeb. Na przykład można rekordu tekstu zawierającego wszystkie dane wyjściowe śledzenia. W takim przypadku należy utworzyć odbiornik, który zapisano wszystkie dane wyjściowe w nowy PLik tekstowy, jeśli włączona. Z drugiej strony może być tylko chcesz wyświetlić dane wyjściowe podczas wykonywania aplikacji. W takim przypadku można utworzyć odbiornik, który przekierowanie wszystkie dane wyjściowe do okna konsoli. <xref:System.Diagnostics.EventLogTraceListener> Można skierować dane wyjściowe śledzenia do dziennika zdarzeń, a właściwość <xref:System.Diagnostics.TextWriterTraceListener> może zapisywać dane wyjściowe śledzenia w strumieniu.  
  
## <a name="enabling-tracing"></a>Włączenie debugowania  
 Aby włączyć śledzenie podczas przetwarzania transakcji, należy edytować plik konfiguracji aplikacji. Poniżej przedstawiono przykład.  
  
```xml  
<configuration>  
<system.diagnostics>  
     <sources>  
          <source name="System.Transactions" switchValue="Warning">  
               <listeners>  
                    <add name="tx"   
                     type="System.Diagnostics.XmlWriterTraceListener"   
                     initializeData= "tx.log" />  
               </listeners>  
          </source>  
     </sources>  
</system.diagnostics>  
</configuration>  
```  
  
 <xref:System.Transactions>zapisy są zapisywane w źródle o nazwie "System.Transactions". Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W naszym przykładzie konfiguracji, firma Microsoft o nazwie odbiornika "tx" i dodać standardowe nasłuchującego śledzenia .NET Framework (<xref:System.Diagnostics.XmlWriterTraceListener>) jako typ chcemy użyć. Użyj `initializeData` do ustawienia dla tego odbiornika nazwa PLiku dziennika. Ponadto można zastąpić pełną ścieżkę do nazwy pliku prostego.  
  
 Poszczególne typy komunikatów śledzenia przypisano poziomu, aby wskazać jej stopień ważności. Jeśli poziom śledzenia domeny aPLikacji jest równa lub mniejsza niż poziom typu zdarzenia, generowany jest ten komunikat. Poziom śledzenia jest kontrolowane przez `switchValue` ustawienia w PLiku konfiguracji. Poziomy, które są skojarzone z komunikatów śledzenia są zdefiniowane w poniższej tabeli.  
  
|Poziom śledzenia|Opis|  
|-----------------|-----------------|  
|Krytyczne|Wystąpiły błędy poważne, podobny do następującego:<br /><br /> — Wystąpił błąd, która powoduje natychmiastową utratę funkcjonalności użytkownika.<br />-Zdarzenie, które wymaga administratorowi na podjęcie działań w celu uniknięcia utraty funkcji.<br />— Zawiesza się kod.<br />— Ten poziom śledzenia może także udostępnić wystarczający kontekst interpretowanie inne krytyczne dane śledzenia. Może to ułatwić identyfikację sekwencji działań prowadzących do wystąpienia poważnego błędu.|  
|Błąd|Wystąpił błąd (na przykład nieprawidłowa konfiguracja lub sieci zachowanie) która może spowodować utratę funkcjonalności użytkownika.|  
|Ostrzeżenie|Istnieje warunek, który następnie może spowodować błąd lub błąd krytyczny (na przykład alokacji niepowodzeniem lub zbliża się limit). Normalnego przetwarzania błędów z kodu użytkownika (np. transakcja została przerwana, przekroczeń limitu czasu, uwierzytelnianie nie powiodło się), można również generować ostrzeżenia.|  
|Informacje|Komunikaty przydatne do monitorowania i diagnozowania stanu systemu, pomiaru wydajności lub profilowania są generowane. Może to dotyczyć transakcji i rejestracja zdarzenia okresu istnienia, na przykład tworzenia ani przydzielonej przekroczenia granicę znaczących lub alokacji zasobów znaczących transakcji. Deweloper może następnie korzystać z takie informacje dotyczące planowania i wydajności zarządzanie wydajnością.|  
  
## <a name="trace-codes"></a>Kody śledzenia  
 Poniższa tabela zawiera listę kodów śledzenia generowanych przez <xref:System.Transactions> infrastruktury. W tabeli uwzględniono identyfikatora kod śledzenia <xref:System.Diagnostics.EventTypeFilter.EventType%2A> wyliczenie poziomu śledzenia i dodatkowe dane zawarte w **TraceRecord** śledzenia. Ponadto odpowiedniego poziomu śledzenia śledzenia także jest przechowywany w **TraceRecord**.  
  
|TraceCode|Typ zdarzenia|Dodatkowe dane w TraceRecord|  
|---------------|---------------|-------------------------------|  
|TransactionCreated|Informacje o|TransactionTraceId|  
|TransactionPromoted|Informacje o|TransactionTraceId lokalnego, TransactionTraceId rozproszonych|  
|EnlistmentCreated|Informacje o|TransactionTraceId, EnlistmentTraceId, EnlistmentType (trwałe/volatile) EnlistmentOptions|  
|EnlistmentCallbackNegative|Ostrzeżenie|TransactionTraceId, EnlistmentTraceId,<br /><br /> Wywołanie zwrotne (forcerollback/zostało przerwane/wątPLiwych)|  
|TransactionRollbackCalled|Ostrzeżenie|TransactionTraceId|  
|TransactionAborted|Ostrzeżenie|TransactionTraceId|  
|TransactionInDoubt|Ostrzeżenie|TransactionTraceId|  
|TransactionScopeCreated|Informacje o|TransactionScopeResult, które mogą być następujące:<br /><br /> -Nowej transakcji.<br />-Przekazana transakcja.<br />-Przekazana transakcja zależnych.<br />-Przy użyciu bieżącej transakcji.<br />-Brak transakcji.<br /><br /> nowe bieżącego TransactionTraceId|  
|TransactionScopeDisposed|Informacje o|TransactionTraceId zakresu "Oczekiwano" bieżącej transakcji.|  
|TransactionScopeIncomplete|Ostrzeżenie|TransactionTraceId zakresu "Oczekiwano" bieżącej transakcji.|  
|TransactionScopeNestedIncorrectly|Ostrzeżenie|TransactionTraceId zakresu "Oczekiwano" bieżącej transakcji.|  
|TransactionScopeCurrentTransactionChanged|Ostrzeżenie|Stary bieżącego TransactionTraceId, innych TransactionTraceId|  
|TransactionScopeTimeout|Ostrzeżenie|TransactionTraceId zakresu "Oczekiwano" bieżącej transakcji.|  
|DependentCloneCreated|Informacje o|TransactionTraceId, typ transakcji zależnych utworzony (RollbackIfNotComplete/BlockCommitUntilComplete)|  
|DependentCloneComplete|Informacje o|TransactionTraceId|  
|Metoda RecoveryComplete|Informacje o|Identyfikator GUID Menedżera zasobów (z base)|  
|Reenlist|Informacje o|Identyfikator GUID Menedżera zasobów (z base)|  
|TransactionSerialized|Informacje o|TransactionTraceId.|  
|TransactionException|Błąd|Komunikat wyjątku|  
|InvalidOperationException|Błąd|Komunikat wyjątku|  
|InternalError|Krytyczne|Komunikat wyjątku|  
|TransferEvent||Podczas deserializacji transakcji, lub promowane z <xref:System.Transactions> transakcja rozproszona jednego, bieżący identyfikator działania w kontekście wykonywania i identyfikator transakcji rozproszonych są zapisywane.<br /><br /> USŁUGI ponownie wywołuje kodu zarządzanego, identyfikator transakcja rozproszona jest ustawiana jako identyfikator działania w kontekście wykonywania na czas trwania wywołania zwrotnego.|  
|ConfiguredDefaultTimeoutAdjusted|Ostrzeżenie|Nie dodatkowe dane.|  
|TransactionTimeout|Ostrzeżenie|Upłynął limit czasu TransactionTraceId bycia transakcji.|  
  
 Schemat XML dla poszczególnych elementów dodatkowe dane ma następujący format.  
  
### <a name="transactiontraceidentifier"></a>TransactionTraceIdentifier  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a>EnlistmentTraceIdentifier  
 `<EnlistmentTraceIdentifier>`  
  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `<CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<EnlistmentIdentifier>`  
  
 `the enlistment id number`  
  
 `</EnlistmentIdentifier>`  
  
 `</EnlistmentTraceIdentifier>`  
  
### <a name="resource-manager-identifier"></a>Identyfikator Menedżera zasobów  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a>Problemy zabezpieczeń dla śledzenia  
 Gdy użytkownik z uprawnieniami administratora Włącz śledzenie poufne informacje mogą być zapisane w dzienniku śledzenia, który jest publicznie dostępnej domyślnie. Na uniknięcie wszelkich potencjalne zagrożenia, należy rozważyć przechowywania w bezpiecznej lokalizacji kontrolowane przez uprawnienia dostępu do systemu udziału i pliku dziennika śledzenia.
