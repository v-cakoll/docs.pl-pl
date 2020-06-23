---
title: Dane śledzenia diagnostycznego
description: Informacje na temat śladów diagnostycznych w programie .NET. Ślady to publikowanie określonych komunikatów, które są generowane podczas wykonywania aplikacji.
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 5de8fdf7b95cf01b119118dac75d373c32949dcd
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141814"
---
# <a name="diagnostic-traces"></a>Dane śledzenia diagnostycznego
Ślady to publikowanie określonych komunikatów, które są generowane podczas wykonywania aplikacji. Jeśli śledzenie, musi mieć mechanizm do gromadzenia i rejestrowania wiadomości, które mają być wysyłane. Przez odbiorniki odbierania komunikatów śledzenia. Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.  
  
 Jedno takie odbiornik <xref:System.Diagnostics.DefaultTraceListener>, jest automatycznie tworzone i inicjowana, gdy śledzenie jest włączone. Jeśli chcesz, aby dane wyjściowe śledzenia kierować do żadnych dodatkowych źródeł, należy utworzyć i zainicjować odbiorniki śledzenia dodatkowe. Odbiorniki, tworzonych powinny odzwierciedlać Twoich potrzeb. Na przykład może być potrzebny rekord tekstowy wszystkich danych wyjściowych śledzenia. W takim przypadku należy utworzyć odbiornik, który zapisano wszystkie dane wyjściowe w nowy PLik tekstowy, jeśli włączona. Z drugiej strony możesz chcieć tylko wyświetlać dane wyjściowe podczas wykonywania aplikacji. W takim przypadku można utworzyć odbiornik, który przekierowanie wszystkie dane wyjściowe do okna konsoli. <xref:System.Diagnostics.EventLogTraceListener> Można skierować dane wyjściowe śledzenia do dziennika zdarzeń, a właściwość <xref:System.Diagnostics.TextWriterTraceListener> może zapisywać dane wyjściowe śledzenia w strumieniu.  
  
## <a name="enabling-tracing"></a>Włączenie debugowania  
 Aby włączyć ślady podczas przetwarzania transakcji, należy edytować plik konfiguracji aplikacji. Poniżej przedstawiono przykład.  
  
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
  
 <xref:System.Transactions>zapisy są zapisywane w źródle o nazwie "System.Transactions". Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W naszej przykładowej konfiguracji nazywamy odbiornik "TX" i dodano odbiornik standardowego .NET Framework śledzenia ( <xref:System.Diagnostics.XmlWriterTraceListener> ) jako typ, który ma być używany. Użyj `initializeData` do ustawienia dla tego odbiornika nazwa PLiku dziennika. Ponadto można zastąpić w pełni kwalifikowaną ścieżkę dla prostej nazwy pliku.  
  
 Poszczególne typy komunikatów śledzenia przypisano poziomu, aby wskazać jej stopień ważności. Jeśli poziom śledzenia domeny aPLikacji jest równa lub mniejsza niż poziom typu zdarzenia, generowany jest ten komunikat. Poziom śledzenia jest kontrolowane przez `switchValue` ustawienia w PLiku konfiguracji. Poziomy, które są skojarzone z komunikatów śledzenia są zdefiniowane w poniższej tabeli.  
  
|Poziom śledzenia|Opis|  
|-----------------|-----------------|  
|Krytyczne|Wystąpiły błędy poważne, podobny do następującego:<br /><br /> -Błąd, który może spowodować natychmiastowe utratę funkcjonalności użytkownika.<br />-Zdarzenie, które wymaga od administratora podjęcia działań w celu uniknięcia utraty funkcjonalności.<br />— Zawiesza się kod.<br />— Ten poziom śledzenia może także zapewnić wystarczający kontekst interpretacji innych krytycznych śladów. Może to ułatwić identyfikację sekwencji działań prowadzących do wystąpienia poważnego błędu.|  
|Błąd|Wystąpił błąd (na przykład Nieprawidłowa konfiguracja lub zachowanie sieciowe), co może spowodować utratę funkcjonalności użytkownika.|  
|Ostrzeżenie|Istnieje warunek, który może spowodować błąd lub krytyczny błąd (na przykład alokacja kończy się niepowodzeniem lub zbliża się do limitu). Normalne przetwarzanie błędów z kodu użytkownika (na przykład przerwanie transakcji, przekroczenie limitu czasu, uwierzytelnienie nie powiodło się) może również generować ostrzeżenie.|  
|Informacje|Komunikaty przydatne do monitorowania i diagnozowania stanu systemu, pomiaru wydajności lub profilowania są generowane. Może to dotyczyć transakcji i rejestracja zdarzenia okresu istnienia, na przykład tworzenia ani przydzielonej przekroczenia granicę znaczących lub alokacji zasobów znaczących transakcji. Deweloper może następnie wykorzystać takie informacje do planowania pojemności i zarządzania wydajnością.|  
  
## <a name="trace-codes"></a>Kody śledzenia  
 Poniższa tabela zawiera listę kodów śledzenia generowanych przez <xref:System.Transactions> infrastruktury. W tabeli znajdują się identyfikatory kodu śledzenia, <xref:System.Diagnostics.EventTypeFilter.EventType%2A> poziom wyliczenia dla śladu i dodatkowe dane zawarte w **TraceRecord** dla śledzenia. Ponadto odpowiedni poziom śledzenia śledzenia jest również przechowywany w **TraceRecord**.  
  
|TraceCode|Typ zdarzenia|Dodatkowe dane w TraceRecord|  
|---------------|---------------|-------------------------------|  
|TransactionCreated|Info|TransactionTraceId|  
|TransactionPromoted|Info|TransactionTraceId lokalnego, TransactionTraceId rozproszonych|  
|EnlistmentCreated|Info|TransactionTraceId, EnlistmentTraceId, EnlistmentType (trwałe/volatile) EnlistmentOptions|  
|EnlistmentCallbackNegative|Ostrzeżenie|TransactionTraceId, EnlistmentTraceId,<br /><br /> Wywołanie zwrotne (forcerollback/zostało przerwane/wątPLiwych)|  
|TransactionRollbackCalled|Ostrzeżenie|TransactionTraceId|  
|TransactionAborted|Ostrzeżenie|TransactionTraceId|  
|TransactionInDoubt|Ostrzeżenie|TransactionTraceId|  
|TransactionScopeCreated|Info|TransactionScopeResult, które mogą być następujące:<br /><br /> — Nowa transakcja.<br />-Transakcja została przeniesiona.<br />Transakcja zależna została przeniesiona.<br />— Przy użyciu bieżącej transakcji.<br />-Brak transakcji.<br /><br /> nowe bieżącego TransactionTraceId|  
|TransactionScopeDisposed|Info|TransactionTraceId "oczekiwana" bieżącej transakcji.|  
|TransactionScopeIncomplete|Ostrzeżenie|TransactionTraceId "oczekiwana" bieżącej transakcji.|  
|TransactionScopeNestedIncorrectly|Ostrzeżenie|TransactionTraceId "oczekiwana" bieżącej transakcji.|  
|TransactionScopeCurrentTransactionChanged|Ostrzeżenie|Stary bieżącego TransactionTraceId, innych TransactionTraceId|  
|TransactionScopeTimeout|Ostrzeżenie|TransactionTraceId "oczekiwana" bieżącej transakcji.|  
|DependentCloneCreated|Info|TransactionTraceId, typ transakcji zależnej utworzona (RollbackIfNotComplete/BlockCommitUntilComplete)|  
|DependentCloneComplete|Info|TransactionTraceId|  
|RecoveryComplete|Info|Identyfikator GUID Menedżera zasobów (z base)|  
|Reenlist|Info|Identyfikator GUID Menedżera zasobów (z base)|  
|TransactionSerialized|Info|TransactionTraceId.|  
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
 Po włączeniu śledzenia przez administratora informacje poufne mogą być zapisywane w dzienniku śledzenia, który jest domyślnie widoczny. Aby wyeliminować ewentualne zagrożenia bezpieczeństwa, należy rozważyć przechowywanie dziennika śledzenia w bezpiecznej lokalizacji kontrolowanej przez udział i uprawnienia dostępu do systemu plików.
