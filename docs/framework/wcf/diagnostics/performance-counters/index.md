---
title: Liczniki wydajności programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: d0ad7ee0bc3ea1d15197e6b8d9888d60b21a2f15
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365280"
---
# <a name="wcf-performance-counters"></a>Liczniki wydajności programu WCF
Windows Communication Foundation (WCF) zawiera duży zestaw liczników wydajności, aby ułatwić mierzyć wydajność aplikacji.  
  
## <a name="enabling-performance-counters"></a>Włączanie liczników wydajności  
 Liczniki wydajności dla usługi WCF można włączyć za pomocą pliku konfiguracji app.config usługi WCF w następujący sposób:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 `performanceCounters` Atrybut można ustawić tak, aby włączyć liczniki wydajności dla określonego typu. Prawidłowe wartości to:  
  
-   Wszystko: Wszystkie liczniki kategorii (ServiceModelService i ServiceModelEndpoint ServiceModelOperation) są włączone.  
  
-   ServiceOnly: Tylko ServiceModelService kategorii liczników są włączone. Jest to wartość domyślna.  
  
-   Wyłączony: ServiceModel *, liczniki wydajności są wyłączone.  
  
 Jeśli chcesz włączyć liczniki wydajności dla wszystkich aplikacji WCF, ustawienia konfiguracji można umieścić w pliku Machine.config.  Zobacz **zwiększenie rozmiaru pamięci dla liczników wydajności** sekcji poniżej, aby uzyskać więcej informacji na temat konfigurowania wystarczającą ilość pamięci dla liczników wydajności na komputerze.  
  
 Jeśli używasz usługi WCF punkty rozszerzeń, takich jak invokers operacji niestandardowej, powinny również wysyłać liczniki wydajności. Jest to spowodowane w przypadku zaimplementowania punktu rozszerzalności WCF, mogą nie są już emitowane dane licznika wydajności warstwy standardowa w domyślnej ścieżce. Jeśli obsługa licznika wydajności ręczne nie jest zaimplementowane, może być niewidoczna dane licznika wydajności, których oczekujesz.  
  
 Można również włączyć liczniki wydajności w kodzie w następujący sposób,  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a>Wyświetlanie danych wydajności  
 Aby wyświetlić dane przechwycone przez liczniki wydajności, można użyć Monitora wydajności (Perfmon.exe), który jest dostarczany z Windows. Możesz uruchomić to narzędzie, przechodząc do **Start**i kliknij przycisk **Uruchom** i typ `perfmon.exe` w oknie dialogowym.  
  
> [!NOTE]
>  Wystąpienia liczników wydajności mogą zostać zwolnione, zanim ostatnie komunikaty są przetwarzane przez dyspozytora punktu końcowego. Może to spowodować, że dane wydajności nie przechwycone kilka komunikatów.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Zwiększenie rozmiaru pamięci dla liczników wydajności  
 Usługi WCF używa oddzielnych pamięci współużytkowanej dla jego kategorii licznika wydajności.  
  
 Domyślnie oddzielne Pamięć współużytkowana jest równa kwartału ogólnych parametrów liczników pamięci. Domyślny ogólnych parametrów liczników pamięci to 524,288 bajtów. Trzy kategorie liczników wydajności programu WCF więc domyślny rozmiar około 128KB. W zależności od charakterystyki środowiska uruchomieniowego aplikacji WCF na komputerze, mogą się wyczerpać pamięci licznika wydajności. W takim przypadku WCF zapisuje błąd w dzienniku zdarzeń aplikacji. Zawartość błąd stwierdza, że licznika wydajności, który nie został załadowany, a wpis zawiera wyjątek "System.InvalidOperationException: za mało pamięci dla widoku pliku liczników niestandardowych." Jeśli śledzenie jest włączone na poziomie błędu, śledzona jest również tego błędu. Jeśli wyczerpaniu pamięci licznika wydajności w dalszym ciągu uruchamiać aplikacje programu WCF za pomocą liczników wydajności, włączone może spowodować obniżenie wydajności. Jeśli jesteś administratorem na komputerze, należy skonfigurować ją przydzielić wystarczającej ilości pamięci do obsługi maksymalną liczbę liczników wydajności, które może znajdować się w dowolnym momencie.  
  
 Można zmienić ilość pamięci licznika wydajności dla kategorii WCF w rejestrze. Aby to zrobić, należy dodać nową wartość DWORD o nazwie `FileMappingSize` do trzech następujących lokalizacji i ustaw ją na żądaną wartość w bajtach. Tak, aby te zmiany są wykonywane w życie, należy ponownie uruchomić maszynę.  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 Gdy dużą liczbę obiektów (na przykład ServiceHost) będą usuwane, ale oczekujące na zebranych elementów bezużytecznych `PrivateBytes` licznika wydajności będą rejestrować się wyjątkowo dużą liczbą. Aby rozwiązać ten problem, możesz dodać własne liczniki specyficzne dla aplikacji, lub użyj `performanceCounters` atrybutu, aby włączyć liczniki tylko poziomu usługi.  
  
## <a name="types-of-performance-counters"></a>Typy liczników wydajności  
 Liczniki wydajności są ograniczone do trzech różnych poziomach: usługi, punkt końcowy i operacji.  
  
 WMI umożliwia pobieranie nazwy wystąpienia licznika wydajności. Na przykład  
  
-   Nazwa wystąpienia licznika usługi można uzyskać za pomocą usługi WMI [usługi](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) właściwość "CounterInstanceName" instancji.  
  
-   Nazwa wystąpienia licznika punktu końcowego można uzyskać za pomocą usługi WMI [punktu końcowego](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) właściwość "CounterInstanceName" instancji.  
  
-   Nazwa wystąpienia licznika operacji można uzyskać za pomocą usługi WMI [punktu końcowego](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) metodę "GetOperationCounterInstanceName" instancji.  
  
 Aby uzyskać więcej informacji na temat usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### <a name="service-performance-counters"></a>Liczniki wydajności usługi  
 Liczniki wydajności usługi zmierzyć zachowanie usługi jako całość i może służyć do diagnozowania wydajności całą usługę. Można go znaleźć w `ServiceModelService 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności. Wystąpienia są nazywane przy użyciu następującego wzorca:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Licznik w zakresie usługi jest agregowana od licznika w kolekcji punktów końcowych.  
  
 Liczniki wydajności do tworzenia wystąpienia usług są zwiększane, gdy zostanie utworzony nowy obiekt InstanceContext. Należy pamiętać o tym, czy nowy obiekt InstanceContext został utworzony, nawet gdy — Aktywacja komunikat o błędzie (z istniejącą usługę) lub podczas nawiązywania połączenia z wystąpieniem z jednej sesji, zakończyć sesję i ponownego połączenia z innej sesji.  
  
### <a name="endpoint-performance-counters"></a>Liczniki wydajności w punkcie końcowym  
 Liczniki wydajności w punkcie końcowym umożliwiają wyszukiwanie danych w czasie wykonywania odbicia, jak punkt końcowy jest akceptowanie komunikatów. Można go znaleźć w `ServiceModelEndpoint 4.0.0.0` obiekt wydajności podczas przeglądania, korzystanie z Monitora wydajności. Wystąpienia są nazywane przy użyciu następującego wzorca:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Dane są podobne do są zbierane dla poszczególnych działań, ale tylko jest agregowana dla punktu końcowego.  
  
 Licznik w zakresie punktu końcowego są agregowane z liczników w to kolekcja operacji.  
  
> [!NOTE]
>  Jeśli dwa punkty końcowe mają identyczne nazwy i adresy, są mapowane do tego samego wystąpienia licznika.  
  
### <a name="operation-performance-counters"></a>Liczniki wydajności operacji  
 Liczniki wydajności operacji znajdują się w obszarze `ServiceModelOperation 4.0.0.0` obiekt wydajności podczas wyświetlania przy użyciu Monitora wydajności. Każda operacja ma poszczególnych wystąpień. Oznacza to jeśli danego kontraktu operacje 10, 10 wystąpień licznika operacji skojarzonych z tej Umowy. Wystąpienia obiektu są nazywane przy użyciu następującego wzorca:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Ten licznik umożliwia pomiar sposobu używania wywołania i jak dobrze działa operacja.  
  
 Liczniki są widoczne w wielu zakresach, danych zebranych z wyższym zakresie są agregowane z danymi z niższe zakresy. Na przykład `Calls` w punkcie końcowym reprezentuje sumę wszystkich wywołań operacji w ramach punktu końcowego; `Calls` powinna być usługa reprezentuje sumę wszystkich wywołań do wszystkich punktów końcowych w ramach usługi.  
  
> [!NOTE]
>  Jeśli masz nazwy zduplikowanych operacji na kontrakt, tylko otrzymasz jednego wystąpienia liczników dla obu operacji.  
  
## <a name="programming-the-wcf-performance-counters"></a>Programowanie liczniki wydajności programu WCF  
 Kilka plików są instalowane w folderze instalacji zestawu SDK, tak aby programowy dostęp liczniki wydajności programu WCF. Te pliki są wymienione w następujący sposób.  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 Aby uzyskać więcej informacji na temat sposobu programowego dostępu do liczników, zobacz [Architektura programowania licznika wydajności](https://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Zobacz też  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
