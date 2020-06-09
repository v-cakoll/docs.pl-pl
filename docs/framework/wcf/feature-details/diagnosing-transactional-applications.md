---
title: Diagnozowanie aplikacji transakcyjnych
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: fb3a83083e876cf697621ba70dcf7dd67636f83a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599220"
---
# <a name="diagnosing-transactional-applications"></a>Diagnozowanie aplikacji transakcyjnych
W tym temacie opisano, jak używać funkcji zarządzania i diagnostyki Windows Communication Foundation (WCF) do rozwiązywania problemów z aplikacją transakcyjną.  
  
## <a name="performance-counters"></a>Liczniki wydajności  
 Funkcja WCF oferuje standardowy zestaw liczników wydajności służący do mierzenia wydajności transakcyjnej aplikacji. Aby uzyskać więcej informacji, zobacz [liczniki wydajności](../diagnostics/performance-counters/index.md).  
  
 Liczniki wydajności są objęte zakresem trzech różnych poziomów: usługi, punktu końcowego i operacji, zgodnie z opisem w poniższych tabelach.  
  
### <a name="service-performance-counters"></a>Liczniki wydajności usługi  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|Przepływ transakcji|Liczba transakcji, które przepływają do operacji w tej usłudze. Ten licznik jest zwiększany za każdym razem, gdy transakcja jest obecna w wiadomości wysyłanej do usługi.|  
|Przepływ transakcji na sekundę|Liczba transakcji, które przepływają do operacji w tej usłudze w każdej sekundzie. Ten licznik jest zwiększany za każdym razem, gdy transakcja jest obecna w wiadomości wysyłanej do usługi.|  
|Potwierdzone operacje transakcyjne|Liczba wykonanych operacji transakcyjnych, których transakcja została ukończona z wynikiem zakontraktowanym w tej usłudze. Działanie wykonywane w ramach takich operacji zostało w pełni zatwierdzone. Zasoby są aktualizowane zgodnie z czynnościami wykonywanymi w ramach operacji.|  
|Zatwierdzone operacje transakcyjne na sekundę|Liczba wykonanych operacji transakcyjnych, których transakcja została ukończona z wynikiem zakontraktowanym w tej usłudze w każdej sekundzie. Działanie wykonywane w ramach takich operacji zostało w pełni zatwierdzone. Zasoby są aktualizowane zgodnie z czynnościami wykonywanymi w ramach operacji.|  
|Przerwane operacje transakcyjne|Liczba wykonanych operacji transakcyjnych, których transakcja została ukończona z wynikiem przerwania w tej usłudze. Zadania wykonywane w ramach takich operacji są wycofywane. Zasoby są przywracane do poprzedniego stanu.|  
|Przerwane operacje transakcyjne na sekundę|Liczba wykonanych operacji transakcyjnych, których transakcja została ukończona z wynikiem przerwania w tej usłudze w każdej sekundzie. Zadania wykonywane w ramach takich operacji są wycofywane. Zasoby są przywracane do poprzedniego stanu.|  
|Wątpliwe operacje transakcyjne|Liczba wykonanych operacji transakcyjnych, których transakcja została ukończona z wynikiem wątpliwości w tej usłudze. Działanie wykonane z wynikiem wątpliwości jest w stanie nieokreślonym. Zasoby są przechowywane w stanie oczekiwania.|  
|Wątpliwe operacje transakcyjne na sekundę|Liczba wykonanych operacji transakcyjnych, których transakcja została ukończona z wynikiem wątpliwości w tej usłudze w każdej sekundzie. Działanie wykonane z wynikiem wątpliwości jest w stanie nieokreślonym. Zasoby są przechowywane w stanie oczekiwania.|  
  
### <a name="endpoint-performance-counters"></a>Liczniki wydajności w punkcie końcowym  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|Przepływ transakcji|Liczba transakcji, które przepływają do operacji w tym punkcie końcowym. Ten licznik jest zwiększany w każdym momencie, gdy transakcja jest obecna w komunikacie wysyłanym do punktu końcowego.|  
|Przepływ transakcji na sekundę|Liczba transakcji, które przepływają do operacji w tym punkcie końcowym w ciągu każdej sekundy. Ten licznik jest zwiększany w każdym momencie, gdy transakcja jest obecna w komunikacie wysyłanym do punktu końcowego.|  
  
### <a name="operation-performance-counters"></a>Liczniki wydajności operacji  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|Przepływ transakcji|Liczba transakcji, które przepływają do operacji w tym punkcie końcowym. Ten licznik jest zwiększany w każdym momencie, gdy transakcja jest obecna w komunikacie wysyłanym do punktu końcowego.|  
|Przepływ transakcji na sekundę|Liczba transakcji, które przepływają do operacji w tym punkcie końcowym w ciągu każdej sekundy. Ten licznik jest zwiększany w każdym momencie, gdy transakcja jest obecna w komunikacie wysyłanym do punktu końcowego.|  
  
## <a name="windows-management-instrumentation"></a>Instrumentacja zarządzania Windows  
 Funkcja WCF udostępnia dane inspekcji usługi w czasie wykonywania za pomocą dostawcy usług WCF Instrumentacja zarządzania Windows (WMI). Aby uzyskać więcej informacji na temat uzyskiwania dostępu do danych usługi WMI, zobacz [używanie Instrumentacja zarządzania Windows do diagnostyki](../diagnostics/wmi/index.md).  
  
 Wiele właściwości usługi WMI tylko do odczytu wskazuje zastosowane ustawienia transakcji dla usługi. W poniższej tabeli wymieniono wszystkie te ustawienia.  
  
 W usłudze `ServiceBehaviorAttribute` ma następujące właściwości.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|Ustawion|Boolean|Określa, czy obiekt usługi jest odtwarzany po zakończeniu bieżącej transakcji.|  
|TransactionAutoCompleteOnSessionClose|Boolean|Określa, czy oczekujące transakcje są kończone podczas zamykania bieżącej sesji.|  
|TransactionIsolationLevel|Ciąg, który zawiera prawidłową wartość <xref:System.Transactions.IsolationLevel> wyliczenia.|Określa poziom izolacji transakcji obsługiwanej przez tę usługę.|  
|TransactionTimeout|<xref:System.DateTime>|Określa okres, w którym transakcja musi zostać zakończona.|  
  
 `ServiceTimeoutsBehavior`Ma następującą właściwość.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|Określa okres, w którym transakcja musi zostać zakończona.|  
  
 Na oprawie `TransactionFlowBindingElement` ma następujące właściwości.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|Element TransactionProtocol|Ciąg, który zawiera prawidłową wartość <xref:System.ServiceModel.TransactionProtocol> typu.|Określa protokół transakcji do użycia w przepływie transakcji.|  
|TransactionFlow|Boolean|Określa, czy przepływ transakcji przychodzących jest włączony.|  
  
 W przypadku operacji `OperationBehaviorAttribute` ma następujące właściwości:  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|Wartość|Boolean|Określa, czy bieżąca transakcja ma być automatycznie przekazywana, jeśli nie wystąpią żadne Nieobsłużone wyjątki.|  
|Ustawione|Boolean|Określa, czy operacja wymaga transakcji.|  
  
 W przypadku operacji `TransactionFlowAttribute` ma następujące właściwości.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|Parametru TransactionFlowOption|Ciąg, który zawiera prawidłową wartość <xref:System.ServiceModel.TransactionFlowOption> wyliczenia.|Określa zakres, do którego jest wymagany przepływ transakcji.|  
  
## <a name="tracing"></a>Śledzenie  
 Ślady umożliwiają monitorowanie i analizowanie błędów w aplikacjach transakcyjnych. Śledzenie można włączyć, korzystając z następujących sposobów:  
  
- Standardowe śledzenie WCF  
  
     Ten typ śledzenia jest taki sam jak śledzenie dowolnej aplikacji WCF. Aby uzyskać więcej informacji, zobacz [Konfigurowanie śledzenia](../diagnostics/tracing/configuring-tracing.md).  
  
- Śledzenie WS-AtomicTransaction  
  
     Śledzenie WS-AtomicTransaction można włączyć za pomocą [Narzędzia konfiguracji protokołu WS-AtomicTransaction (wsatConfig. exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Takie śledzenie zapewnia wgląd w stan transakcji i uczestników w ramach systemu. Aby włączyć również śledzenie wewnętrznego modelu usług, można ustawić `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` klucz rejestru na prawidłową wartość <xref:System.Diagnostics.SourceLevels> wyliczenia. Rejestrowanie komunikatów można włączyć w taki sam sposób, jak w przypadku innych aplikacji WCF.  
  
- `System.Transactions`pochodzenia  
  
     W przypadku korzystania z protokołu OleTransactions komunikaty protokołu nie mogą być śledzone. Funkcja śledzenia zapewnia obsługę <xref:System.Transactions> infrastruktury (która używa OleTransactions) umożliwia użytkownikom wyświetlanie zdarzeń, które wystąpiły w transakcjach. Aby włączyć śledzenie dla <xref:System.Transactions> aplikacji, Dołącz następujący kod w `App.config` pliku konfiguracji.  
  
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
  
     Umożliwia to również śledzenie WCF, ponieważ usługa WCF wykorzystuje również <xref:System.Transactions> infrastrukturę.  
  
## <a name="see-also"></a>Zobacz też

- [Administracja i Diagnostyka](../diagnostics/index.md)
- [Konfigurowanie śledzenia](../diagnostics/tracing/configuring-tracing.md)
- [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
