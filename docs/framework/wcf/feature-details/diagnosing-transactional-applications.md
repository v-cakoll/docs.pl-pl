---
title: Diagnozowanie aplikacji transakcyjnych
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: aca5f95e2085dfadf06da35dfd86af72c0b6092d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101715"
---
# <a name="diagnosing-transactional-applications"></a>Diagnozowanie aplikacji transakcyjnych
W tym temacie opisano rozwiązywanie problemów aplikacji transakcyjnej przy użyciu funkcji diagnostyki i zarządzania usługi Windows Communication Foundation (WCF).  
  
## <a name="performance-counters"></a>Liczniki wydajności  
 Usługi WCF zawiera standardowy zestaw liczników wydajności, które umożliwiają mierzenie wydajności aplikacji transakcyjnych. Aby uzyskać więcej informacji, zobacz [liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
 Liczniki wydajności są ograniczone do trzech różnych poziomach: Usługa punktu końcowego i operacji, zgodnie z opisem w poniższych tabelach.  
  
### <a name="service-performance-counters"></a>Liczniki wydajności usługi  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|Przepływ transakcji|Liczba transakcji przekazanych do operacji w tej usłudze. Ten licznik jest zwiększany każdym razem, gdy transakcja jest w wiadomości, które są wysyłane do usługi.|  
|Przepływ transakcji na sekundę|Liczba transakcji przekazanych do operacji w tej usłudze w ciągu każdej sekundy. Ten licznik jest zwiększany każdym razem, gdy transakcja jest w wiadomości, które są wysyłane do usługi.|  
|Potwierdzone operacje transakcyjne|Liczba operacji transakcyjnych, wykonywane, którego transakcja została ukończona z wynik w tej usłudze. Praca wykonana w takich operacji jest w pełni zatwierdzić. Zasoby są aktualizowane zgodnie z pracy wykonanej w ramach operacji.|  
|Zatwierdzone operacje transakcyjne na sekundę|Liczba operacji transakcyjnych, wykonywane, którego transakcja została ukończona z wyniku zatwierdzone w tej usłudze w ciągu każdej sekundy. Praca wykonana w takich operacji jest w pełni zatwierdzić. Zasoby są aktualizowane zgodnie z pracy wykonanej w ramach operacji.|  
|Przerwane operacje transakcyjne|Liczba operacji transakcyjnych wykonać, którego transakcja została ukończona z wyniku zostało przerwane w tej usłudze. Praca wykonana w takich operacji jest wycofywana. Zasoby są przywracane do poprzedniego stanu.|  
|Przerwane operacje transakcyjne na sekundę|Liczba operacji transakcyjnych wykonać, którego transakcja została ukończona z wyniku zostało przerwane w tej usłudze w ciągu każdej sekundy. Praca wykonana w takich operacji jest wycofywana. Zasoby są przywracane do poprzedniego stanu.|  
|Wątpliwe operacje transakcyjne|Liczba operacji transakcyjnych wykonać, których transakcji zostało ukończone z wynikami w stanie wątpliwości, w tej usłudze. Praca wykonana w w stanie wątpliwości jest w stanie nieokreślonym. Zasoby są wstrzymane do czasu wyniku.|  
|Wątpliwe operacje transakcyjne na sekundę|Liczba operacji transakcyjnych wykonać, których transakcji została ukończona z wynikami w stanie wątpliwości, w tej usłudze w ciągu każdej sekundy. Praca wykonana w w stanie wątpliwości jest w stanie nieokreślonym. Zasoby są wstrzymane do czasu wyniku.|  
  
### <a name="endpoint-performance-counters"></a>Liczniki wydajności w punkcie końcowym  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|Przepływ transakcji|Liczba transakcji przekazanych do operacji w tym punkcie końcowym. Ten licznik jest zwiększany każdym razem, gdy transakcja jest w wiadomości, które są wysyłane do punktu końcowego.|  
|Przepływ transakcji na sekundę|Liczba transakcji przekazanych do operacji w tym punkcie końcowym w ciągu każdej sekundy. Ten licznik jest zwiększany każdym razem, gdy transakcja jest w wiadomości, które są wysyłane do punktu końcowego.|  
  
### <a name="operation-performance-counters"></a>Liczniki wydajności operacji  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|Przepływ transakcji|Liczba transakcji przekazanych do operacji w tym punkcie końcowym. Ten licznik jest zwiększany każdym razem, gdy transakcja jest w wiadomości, które są wysyłane do punktu końcowego.|  
|Przepływ transakcji na sekundę|Liczba transakcji przekazanych do operacji w tym punkcie końcowym w ciągu każdej sekundy. Ten licznik jest zwiększany każdym razem, gdy transakcja jest w wiadomości, które są wysyłane do punktu końcowego.|  
  
## <a name="windows-management-instrumentation"></a>Instrumentacja zarządzania Windows  
 Usługa WCF umożliwia dane inspekcji usługi w czasie wykonywania za pośrednictwem dostawcy Instrumentacji zarządzania Windows (WMI) WCF. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do danych usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 Liczba tylko do odczytu właściwości WMI wskazują ustawień zastosowanych transakcji usługi. W poniższej tabeli wymieniono wszystkie te ustawienia.  
  
 W usłudze `ServiceBehaviorAttribute` ma następujące właściwości.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boolean|Określa, czy obiekt usługi zostanie odtworzony po zakończeniu bieżącej transakcji.|  
|TransactionAutoCompleteOnSessionClose|Boolean|Określa, czy oczekujące transakcje są wykonywane po zamknięciu bieżącej sesji.|  
|TransactionIsolationLevel|Ciąg, który zawiera prawidłową wartość <xref:System.Transactions.IsolationLevel> wyliczenia.|Określa poziom izolacji transakcji, który obsługuje tę usługę.|  
|TransactionTimeout|<xref:System.DateTime>|Określa okres, w którym należy wykonać transakcję.|  
  
 `ServiceTimeoutsBehavior` Ma następującą właściwość.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|Określa okres, w którym należy wykonać transakcję.|  
  
 W powiązaniu `TransactionFlowBindingElement` ma następujące właściwości.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|TransactionProtocol|Ciąg, który zawiera prawidłową wartość <xref:System.ServiceModel.TransactionProtocol> typu.|Określa protokół transakcji do użycia w przepływu transakcji.|  
|transactionFlow|Boolean|Określa, czy ruch przychodzący transakcji jest włączone.|  
  
 W przypadku operacji `OperationBehaviorAttribute` ma następujące właściwości:  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|TransactionAutoComplete|Boolean|Określa, czy można zatwierdzić bieżącej transakcji automatycznie, jeśli wystąpi żaden nieobsługiwany wyjątek.|  
|TransactionScopeRequired|Boolean|Określa, czy operacja wymaga transakcji.|  
  
 W przypadku operacji `TransactionFlowAttribute` ma następujące właściwości.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|TransactionFlowOption|Ciąg, który zawiera prawidłową wartość <xref:System.ServiceModel.TransactionFlowOption> wyliczenia.|Określa zakres przepływu transakcji, która jest to konieczne.|  
  
## <a name="tracing"></a>Śledzenie  
 Ślady umożliwiają monitorowanie i analizowanie błędów w aplikacji transakcyjnych. Można włączyć śledzenie z użyciem następujących sposobów:  
  
-   Standardowe śledzenia WCF  
  
     Tego rodzaju śledzenia jest taka sama jak śledzenie dowolnej aplikacji WCF. Aby uzyskać więcej informacji, zobacz [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Śledzenie WS-AtomicTransaction  
  
     Śledzenie WS-AtomicTransaction można włączyć za pomocą [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Takie śledzenie zapewnia wgląd w stan transakcji i uczestników w systemie. Umożliwia również wewnętrznego śledzenia Model usług, można ustawić `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` klucz rejestru prawidłową wartością <xref:System.Diagnostics.SourceLevels> wyliczenia. Można włączyć rejestrowanie w taki sam sposób jak inne aplikacje WCF komunikatów.  
  
-   `System.Transactions` śledzenie  
  
     Podczas korzystania z protokołu OleTransactions, komunikatach protokołów nie może być śledzony. Obsługa śledzenia <xref:System.Transactions> zapewnia infrastrukturę (które wykorzystuje OleTransactions) pozwala użytkownikom na wyświetlanie zdarzeń, które nastąpiły w transakcji. Aby włączyć śledzenie dla <xref:System.Transactions> aplikacji, zawrzyj następujący kod w `App.config` pliku konfiguracji.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     Umożliwia także śledzenie programu WCF, jak również korzysta z usługi WCF <xref:System.Transactions> infrastruktury.  
  
## <a name="see-also"></a>Zobacz także

- [Administracja i diagnostyka](../../../../docs/framework/wcf/diagnostics/index.md)
- [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
