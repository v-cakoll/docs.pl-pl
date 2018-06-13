---
title: Diagnozowanie aplikacji transakcyjnych
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: 4fa85fea0651d7a31c5a50bbc9c1226421b976b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497003"
---
# <a name="diagnosing-transactional-applications"></a>Diagnozowanie aplikacji transakcyjnych
W tym temacie opisano, jak korzystać z zarządzania usługi Windows Communication Foundation (WCF) i funkcja diagnostyki rozwiązywać transakcyjnych aplikacji.  
  
## <a name="performance-counters"></a>Liczniki wydajności  
 Usługi WCF zawiera standardowy zestaw liczników wydajności można mierzyć wydajność aplikacji transakcyjnej. Aby uzyskać więcej informacji, zobacz [liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
 Liczniki wydajności są ograniczone do trzech różnych poziomów: Usługa punktu końcowego, a działanie, zgodnie z opisem w poniższych tabelach.  
  
### <a name="service-performance-counters"></a>Liczniki wydajności usługi  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|Przepływ transakcji|Liczba transakcji przekazanych do operacji w tej usłudze. Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do usługi.|  
|Przepływ transakcji na sekundę|Liczba transakcji przekazanych do operacji w tej usłudze w ciągu każdej sekundy. Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do usługi.|  
|Zatwierdzone operacje transakcyjne|Liczba operacji transakcyjnych, którego transakcja została zakończona z wynikami zatwierdzone w tej usłudze. Praca wykonana w takich operacjach jest w pełni zatwierdzana. Zasoby są aktualizowane zgodnie z wynikami wykonanej operacji.|  
|Zatwierdzone operacje transakcyjne na sekundę|Liczba operacji transakcyjnych, którego transakcja została zakończona z wynikami zatwierdzone w tej usłudze w ciągu każdej sekundy. Praca wykonana w takich operacjach jest w pełni zatwierdzana. Zasoby są aktualizowane zgodnie z wynikami wykonanej operacji.|  
|Przerwane operacje transakcyjne|Liczba operacji transakcyjnych wykonać, którego transakcja została zakończona z wynikami przerwane w tej usłudze. Praca wykonana w takich operacjach jest wycofywana. Zasoby są przywracane do poprzedniego stanu.|  
|Przerwane operacje transakcyjne na sekundę|Liczba operacji transakcyjnych wykonać, którego transakcja została zakończona z wynikami przerwane w tej usłudze w ciągu każdej sekundy. Praca wykonana w takich operacjach jest wycofywana. Zasoby są przywracane do poprzedniego stanu.|  
|Wątpliwe operacje transakcyjne|Liczba operacji transakcyjnych wykonać, którego transakcja została zakończona z wynikami, które są wątpliwe, w tej usłudze. Pracować z wynikami, które są wątpliwe jest w stanie nieokreślonym. Zasoby są wstrzymane w oczekiwaniu na wynik.|  
|Wątpliwe operacje transakcyjne na sekundę|Liczba operacji transakcyjnych wykonać, którego transakcja została zakończona z wynikami, które są wątpliwe, w tej usłudze w ciągu każdej sekundy. Pracować z wynikami, które są wątpliwe jest w stanie nieokreślonym. Zasoby są wstrzymane w oczekiwaniu na wynik.|  
  
### <a name="endpoint-performance-counters"></a>Liczniki wydajności w punkcie końcowym  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|Przepływ transakcji|Liczba transakcji przekazanych do operacji w tym punkcie końcowym. Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do punktu końcowego.|  
|Przepływ transakcji na sekundę|Liczba transakcji przekazanych do operacji w tym punkcie końcowym w ciągu każdej sekundy. Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do punktu końcowego.|  
  
### <a name="operation-performance-counters"></a>Liczniki wydajności operacji  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|Przepływ transakcji|Liczba transakcji przekazanych do operacji w tym punkcie końcowym. Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do punktu końcowego.|  
|Przepływ transakcji na sekundę|Liczba transakcji przekazanych do operacji w tym punkcie końcowym w ciągu każdej sekundy. Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do punktu końcowego.|  
  
## <a name="windows-management-instrumentation"></a>Instrumentacja zarządzania Windows  
 Usługa WCF umożliwia danych inspekcji usługi w czasie wykonywania za pośrednictwem dostawcy usług WCF Instrumentacji zarządzania Windows (WMI). Aby uzyskać więcej informacji na temat uzyskiwania dostępu do danych usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 Wiele-do-odczytu właściwości WMI wskazują ustawienia zastosowane transakcji dla usługi. W poniższych tabelach przedstawiono wszystkie te ustawienia.  
  
 W usłudze `ServiceBehaviorAttribute` ma następujące właściwości.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boolean|Określa, czy obiekt usługi jest ponownie przetwarzany po zakończeniu bieżącej transakcji.|  
|TransactionAutoCompleteOnSessionClose|Boolean|Określa, czy transakcje oczekujące są kończone podczas zamykania bieżącej sesji.|  
|TransactionIsolationLevel|Ciąg, który znajduje się nieprawidłowa wartość <xref:System.Transactions.IsolationLevel> wyliczenia.|Określa poziom izolacji transakcji, która obsługuje tę usługę.|  
|TransactionTimeout|<xref:System.DateTime>|Określa okres, w ramach którego transakcja musi zostać zakończona.|  
  
 `ServiceTimeoutsBehavior` Ma następującą właściwość.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|Określa okres, w ramach którego transakcja musi zostać zakończona.|  
  
 W powiązaniu `TransactionFlowBindingElement` ma następujące właściwości.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|Element TransactionProtocol|Ciąg, który znajduje się nieprawidłowa wartość <xref:System.ServiceModel.TransactionProtocol> typu.|Określa protokół transakcji używany do transmisji.|  
|TransactionFlow|Boolean|Określa, czy ruch przychodzący transakcji jest włączony.|  
  
 W przypadku operacji `OperationBehaviorAttribute` ma następujące właściwości:  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|Wartość TransactionAutoComplete|Boolean|Określa, czy ma być automatycznie przekazywana bieżącej transakcji, jeśli wystąpi żaden nieobsługiwany wyjątek.|  
|Właściwości TransactionScopeRequired|Boolean|Określa, czy operacja wymaga transakcji.|  
  
 W przypadku operacji `TransactionFlowAttribute` ma następujące właściwości.  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|Właściwość TransactionFlowOption|Ciąg, który znajduje się nieprawidłowa wartość <xref:System.ServiceModel.TransactionFlowOption> wyliczenia.|Określa zakres przepływu transakcji, które jest to konieczne.|  
  
## <a name="tracing"></a>Śledzenie  
 Ślady umożliwiają monitorowanie i analizowanie błędów w transakcyjnych aplikacji. Można włączyć śledzenie przy użyciu następujących sposobów:  
  
-   Standardowa śledzenia WCF  
  
     Ten rodzaj śledzenia jest taka sama jak śledzenie dowolnej aplikacji WCF. Aby uzyskać więcej informacji, zobacz [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Śledzenie protokołu WS-AtomicTransaction  
  
     WS-AtomicTransaction śledzenie można włączyć za pomocą [narzędzia konfiguracji WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Takie śledzenie zapewnia wgląd w stan transakcji i uczestników w systemie. Należy również włączyć wewnętrznego śledzenia modelu usługi, można ustawić `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` klucza rejestru na prawidłową wartość <xref:System.Diagnostics.SourceLevels> wyliczenia. Można włączyć rejestrowanie w taki sam sposób jak inne aplikacje WCF komunikatów.  
  
-   `System.Transactions` Śledzenie  
  
     Podczas korzystania z protokołu OleTransactions, nie może być śledzony wiadomości protokołu. Obsługa śledzenia <xref:System.Transactions> zapewnia infrastrukturę (który używa OleTransactions) umożliwia użytkownikom wyświetlanie zdarzenia do transakcji. Aby włączyć śledzenie dla <xref:System.Transactions> aplikacji, zawierać następujący kod w `App.config` pliku konfiguracji.  
  
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
  
     Dzięki temu śledzenia WCF, jak również korzysta z usługi WCF <xref:System.Transactions> infrastruktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Administracja i diagnostyka](../../../../docs/framework/wcf/diagnostics/index.md)  
 [Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
