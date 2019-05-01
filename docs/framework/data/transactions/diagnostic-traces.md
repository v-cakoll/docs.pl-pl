---
title: Dane śledzenia diagnostycznego
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 56f79fb9140785188996cc413eca4dd530037ccd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934800"
---
# <a name="diagnostic-traces"></a>Dane śledzenia diagnostycznego
Zapisy są publikowanie określonych wiadomości, które są generowane podczas wykonywania aplikacji. Jeśli śledzenie, musi mieć mechanizm do gromadzenia i rejestrowania wiadomości, które mają być wysyłane. Przez odbiorniki odbierania komunikatów śledzenia. Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.  
  
 Jedno takie odbiornik <xref:System.Diagnostics.DefaultTraceListener>, jest automatycznie tworzone i inicjowana, gdy śledzenie jest włączone. Jeśli chcesz, aby dane wyjściowe śledzenia kierować do żadnych dodatkowych źródeł, należy utworzyć i zainicjować odbiorniki śledzenia dodatkowe. Odbiorniki, tworzonych powinny odzwierciedlać Twoich potrzeb. Na przykład można rekord tekstu z wszystkich danych wyjściowych śledzenia. W takim przypadku należy utworzyć odbiornik, który zapisano wszystkie dane wyjściowe w nowy PLik tekstowy, jeśli włączona. Z drugiej strony może być tylko chcesz wyświetlić dane wyjściowe podczas wykonywania aplikacji. W takim przypadku można utworzyć odbiornik, który przekierowanie wszystkie dane wyjściowe do okna konsoli. <xref:System.Diagnostics.EventLogTraceListener> Można skierować dane wyjściowe śledzenia do dziennika zdarzeń, a właściwość <xref:System.Diagnostics.TextWriterTraceListener> może zapisywać dane wyjściowe śledzenia w strumieniu.  
  
## <a name="enabling-tracing"></a>Włączenie debugowania  
 Aby umożliwić śledzenie podczas przetwarzania transakcji, należy edytować plik konfiguracji aplikacji. Oto przykład.  
  
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
  
 <xref:System.Transactions>zapisy są zapisywane w źródle o nazwie "System.Transactions". Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W naszym przykładzie konfiguracji, firma Microsoft o nazwie "tx" odbiornik i dodać standardowy odbiornik śledzenia .NET Framework (<xref:System.Diagnostics.XmlWriterTraceListener>) jako typ chcemy do użycia. Użyj `initializeData` do ustawienia dla tego odbiornika nazwa PLiku dziennika. Ponadto można zastąpić w pełni kwalifikowana ścieżka dla nazwy pliku prostego.  
  
 Poszczególne typy komunikatów śledzenia przypisano poziomu, aby wskazać jej stopień ważności. Jeśli poziom śledzenia domeny aPLikacji jest równa lub mniejsza niż poziom typu zdarzenia, generowany jest ten komunikat. Poziom śledzenia jest kontrolowane przez `switchValue` ustawienia w PLiku konfiguracji. Poziomy, które są skojarzone z komunikatów śledzenia są zdefiniowane w poniższej tabeli.  
  
|Poziom śledzenia|Opis|  
|-----------------|-----------------|  
|Krytyczny|Wystąpiły błędy poważne, podobny do następującego:<br /><br /> -Błąd, który może spowodować utratę natychmiastowe w funkcji użytkownika.<br />-Zdarzenie, które wymaga podjąć działania w celu uniknięcia utraty funkcji przez administratora.<br />— Zawiesza się kod.<br />— Ten poziom śledzenia może również dostarczać kontekstu wystarczające do interpretacji inne krytyczne śledzenia. Może to ułatwić identyfikację sekwencji działań prowadzących do wystąpienia poważnego błędu.|  
|Błąd|Wystąpił błąd (na przykład nieprawidłowa konfiguracja lub sieci zachowanie) które może spowodować utratę funkcji użytkownika.|  
|Ostrzeżenie|Istnieje warunek, który następnie może spowodować błąd lub błąd krytyczny (na przykład alokacji się niepowodzeniem lub serwisowe limitu). Normalne przetwarzanie błędów z kodu użytkownika (na przykład transakcja została przerwana, limity czasu, uwierzytelnianie nie powiodło się) także może generować ostrzeżenie.|  
|Informacje|Komunikaty przydatne do monitorowania i diagnozowania stanu systemu, pomiaru wydajności lub profilowania są generowane. Może to dotyczyć transakcji i rejestracja zdarzenia okresu istnienia, na przykład tworzenia ani przydzielonej przekroczenia granicę znaczących lub alokacji zasobów znaczących transakcji. Deweloperzy mogą korzystać następnie takich informacji o pojemności planowanie i zarządzanie wydajnością.|  
  
## <a name="trace-codes"></a>Kody śledzenia  
 Poniższa tabela zawiera listę kodów śledzenia generowanych przez <xref:System.Transactions> infrastruktury. Uwzględnione w tabeli są identyfikator śledzenia kodu <xref:System.Diagnostics.EventTypeFilter.EventType%2A> wyliczenie poziomu śledzenia i dodatkowe dane zawarte w **TraceRecord** śledzenia. Ponadto odpowiedniego poziomu śledzenia śledzenia również są przechowywane w **TraceRecord**.  
  
|TraceCode|Typ zdarzenia|Dodatkowe dane w TraceRecord|  
|---------------|---------------|-------------------------------|  
|TransactionCreated|Informacje o|TransactionTraceId|  
|TransactionPromoted|Informacje o|TransactionTraceId lokalnego, TransactionTraceId rozproszonych|  
|EnlistmentCreated|Informacje o|TransactionTraceId, EnlistmentTraceId, EnlistmentType (trwałe/volatile) EnlistmentOptions|  
|EnlistmentCallbackNegative|Ostrzeżenie|TransactionTraceId, EnlistmentTraceId,<br /><br /> Wywołanie zwrotne (forcerollback/zostało przerwane/wątPLiwych)|  
|TransactionRollbackCalled|Ostrzeżenie|TransactionTraceId|  
|TransactionAborted|Ostrzeżenie|TransactionTraceId|  
|TransactionInDoubt|Ostrzeżenie|TransactionTraceId|  
|TransactionScopeCreated|Informacje o|TransactionScopeResult, które mogą być następujące:<br /><br /> -Nowej transakcji.<br />-Transakcja przekazana.<br />-Przekazywany zależne transakcji.<br />-Przy użyciu bieżącej transakcji.<br />-Brak transakcji.<br /><br /> nowe bieżącego TransactionTraceId|  
|TransactionScopeDisposed|Informacje o|TransactionTraceId w zakresie "Oczekiwano" bieżącej transakcji.|  
|TransactionScopeIncomplete|Ostrzeżenie|TransactionTraceId w zakresie "Oczekiwano" bieżącej transakcji.|  
|TransactionScopeNestedIncorrectly|Ostrzeżenie|TransactionTraceId w zakresie "Oczekiwano" bieżącej transakcji.|  
|TransactionScopeCurrentTransactionChanged|Ostrzeżenie|Stary bieżącego TransactionTraceId, innych TransactionTraceId|  
|TransactionScopeTimeout|Ostrzeżenie|TransactionTraceId w zakresie "Oczekiwano" bieżącej transakcji.|  
|DependentCloneCreated|Informacje o|TransactionTraceId, typ transakcji zależne utworzone (RollbackIfNotComplete/BlockCommitUntilComplete)|  
|DependentCloneComplete|Informacje o|TransactionTraceId|  
|RecoveryComplete|Informacje o|Identyfikator GUID Menedżera zasobów (z base)|  
|Reenlist|Informacje o|Identyfikator GUID Menedżera zasobów (z base)|  
|TransactionSerialized|Informacje o|TransactionTraceId.|  
|TransactionException|Błąd|Komunikat wyjątku|  
|InvalidOperationException|Błąd|Komunikat wyjątku|  
|InternalError|Krytyczny|Komunikat wyjątku|  
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
 Gdy jako administrator włączone śledzenie, poufne informacje mogą być zapisane w dzienniku śledzenia, które są dostępne publicznie domyślnie. Aby zmniejszyć wszelkie potencjalne zagrożenie, należy rozważyć przechowywanie dziennik śledzenia w bezpiecznej lokalizacji kontrolowane przez udziału i pliku uprawnień dostępu do systemu.
