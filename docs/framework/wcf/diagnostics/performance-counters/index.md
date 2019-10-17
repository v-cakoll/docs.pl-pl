---
title: Liczniki wydajności programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 73bb02379308fbfe507137e61ac8d84e6b9760b4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395892"
---
# <a name="wcf-performance-counters"></a>Liczniki wydajności programu WCF
Windows Communication Foundation (WCF) zawiera duży zestaw liczników wydajności, które ułatwiają pomiar wydajności aplikacji.  
  
## <a name="enabling-performance-counters"></a>Włączanie liczników wydajności  
 Liczniki wydajności dla usługi WCF można włączyć za pomocą pliku konfiguracji App. config usługi WCF w następujący sposób:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 Atrybut `performanceCounters` można ustawić, aby włączyć określony typ liczników wydajności. Prawidłowe wartości to  
  
- Wszystko: wszystkie liczniki kategorii (ServiceModelService, ServiceModelEndpoint i ServiceModelOperation) są włączone.  
  
- Tylko ServiceOnly: włączone są tylko liczniki kategorii ServiceModelService. Jest to wartość domyślna.  
  
- Wyłączone: ServiceModel * liczniki wydajności są wyłączone.  
  
 Jeśli chcesz włączyć liczniki wydajności dla wszystkich aplikacji WCF, możesz umieścić ustawienia konfiguracji w pliku Machine. config.  Więcej informacji na temat konfigurowania wystarczającej ilości pamięci dla liczników wydajności na komputerze znajduje się w sekcji **zwiększanie rozmiaru pamięci dla liczników wydajności** .  
  
 W przypadku używania punktów rozszerzalności WCF, takich jak niestandardowe wywołania operacji, należy również emitować własne liczniki wydajności. Wynika to z faktu, że w przypadku zaimplementowania punktu rozszerzalności usługa WCF nie będzie już emitować standardowych danych licznika wydajności w ścieżce domyślnej. Jeśli nie zostanie wdrożona ręczna obsługa licznika wydajności, może nie być widoczne oczekiwane dane licznika wydajności.  
  
 Liczniki wydajności można również włączyć w kodzie w następujący sposób:  
  
```csharp
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
 Aby wyświetlić dane przechwycone przez liczniki wydajności, można użyć Monitora wydajności (Perfmon. exe), który jest dostarczany z systemem Windows. Można uruchomić to narzędzie, przechodząc do **menu Start**, a następnie klikając polecenie **uruchom** i wpisz `perfmon.exe` w oknie dialogowym.  
  
> [!NOTE]
> Wystąpienia licznika wydajności mogą zostać wydane przed przetworzeniem ostatnich komunikatów przez dyspozytora punktów końcowych. Może to spowodować, że dane wydajności nie zostaną przechwycone przez kilka komunikatów.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Zwiększanie rozmiaru pamięci dla liczników wydajności  
 Usługa WCF używa oddzielnej pamięci współdzielonej dla jej kategorii liczników wydajności.  
  
 Domyślnie dla oddzielnej pamięci współdzielonej jest ustawiony kwartał rozmiaru globalnej pamięci licznika wydajności. Domyślna globalna pamięć licznika wydajności to 524 288 bajtów. W związku z tym trzy kategorie liczników wydajności programu WCF mają domyślny rozmiar około 128 KB każdego z nich. W zależności od charakterystyk środowiska uruchomieniowego aplikacji WCF na komputerze można wyczerpaniu pamięci licznika wydajności. W takim przypadku usługa WCF zapisuje błąd w dzienniku zdarzeń aplikacji. Zawartość błędów wskazuje, że licznik wydajności nie został załadowany, a wpis zawiera wyjątek "System. InvalidOperationException: niestandardowy widok pliku liczników ma za mało pamięci". Jeśli śledzenie jest włączone na poziomie błędu, ten błąd jest również śledzony. W przypadku wyczerpania pamięci licznika wydajności kontynuowanie uruchamiania aplikacji programu WCF z włączonymi licznikami wydajności może skutkować obniżeniem wydajności. Jeśli jesteś administratorem maszyny, skonfiguruj ją w celu przydzielenia wystarczającej ilości pamięci, aby obsługiwać maksymalną liczbę liczników wydajności, które mogą istnieć w dowolnym momencie.  
  
 Można zmienić ilość pamięci licznika wydajności dla kategorii WCF w rejestrze. Aby to zrobić, należy dodać nową wartość DWORD o nazwie `FileMappingSize` do trzech następujących lokalizacji i ustawić ją na żądaną wartość w bajtach. Uruchom ponownie maszynę, aby zmiany zostały wprowadzone.  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0 \ wydajność  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0 \ wydajność  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0 \ wydajność  
  
 W przypadku usunięcia dużej liczby obiektów (na przykład ServiceHost), ale oczekujących na odtworzenie elementów bezużytecznych, licznik wydajności `PrivateBytes` będzie rejestrował nietypowo dużą liczbę. Aby rozwiązać ten problem, można dodać własne liczniki specyficzne dla aplikacji lub użyć atrybutu `performanceCounters` w celu włączenia tylko liczników poziomu usługi.  
  
## <a name="types-of-performance-counters"></a>Typy liczników wydajności  
 Liczniki wydajności są objęte zakresem trzech różnych poziomów: usługi, punktu końcowego i operacji.  
  
 Za pomocą usługi WMI można pobrać nazwę wystąpienia licznika wydajności. Na przykład  
  
- Nazwę wystąpienia licznika usługi można uzyskać za pomocą właściwości "CounterInstanceName" wystąpienia [usługi](../wmi/service.md) WMI.  
  
- Nazwę wystąpienia licznika punktu końcowego można uzyskać za pomocą właściwości "CounterInstanceName" wystąpienia [punktu końcowego](../wmi/endpoint.md) usługi WMI.  
  
- Nazwę wystąpienia licznika operacji można uzyskać za pomocą metody "GetOperationCounterInstanceName" wystąpienia [punktu końcowego](../wmi/endpoint.md) usługi WMI.  
  
 Aby uzyskać więcej informacji na temat usługi WMI, zobacz [używanie Instrumentacja zarządzania Windows do diagnostyki](../wmi/index.md).  
  
### <a name="service-performance-counters"></a>Liczniki wydajności usługi  
 Liczniki wydajności usługi mierzą zachowanie usługi jako całość i mogą służyć do diagnozowania wydajności całej usługi. Można je znaleźć w obiekcie wydajności `ServiceModelService 4.0.0.0` podczas wyświetlania z monitorem wydajności. Wystąpienia są nazwane przy użyciu następującego wzorca:  
  
`ServiceName@ServiceBaseAddress`
  
 Licznik w zakresie usługi jest agregowany z licznika w kolekcji punktów końcowych.  
  
 Liczniki wydajności dla tworzenia wystąpień usług są zwiększane, gdy tworzony jest nowy obiekt InstanceContext. Należy pamiętać, że tworzony jest nowy element InstanceContext, nawet jeśli otrzymujesz komunikat Nieaktywowany (z istniejącą usługą) lub po nawiązaniu połączenia z wystąpieniem z jednej sesji, zakończyć sesję, a następnie ponownie nawiązać połączenie z innej sesji.  
  
### <a name="endpoint-performance-counters"></a>Liczniki wydajności punktu końcowego  
 Liczniki wydajności punktu końcowego umożliwiają przeglądanie danych odzwierciedlających, w jaki sposób punkt końcowy akceptuje komunikaty. Można je znaleźć w obiekcie wydajności `ServiceModelEndpoint 4.0.0.0` podczas wyświetlania przy użyciu Monitora wydajności. Wystąpienia są nazwane przy użyciu następującego wzorca:  
  
`(ServiceName).(ContractName)@(endpoint listener address)`
  
 Dane są podobne do tego, co jest zbierane dla poszczególnych operacji, ale są agregowane w całym punkcie końcowym.  
  
 Licznik w zakresie punktu końcowego jest agregowany z liczników w kolekcji operacji.  
  
> [!NOTE]
> Jeśli dwa punkty końcowe mają identyczne nazwy i adresy kontraktu, są mapowane na to samo wystąpienie licznika.  
  
### <a name="operation-performance-counters"></a>Liczniki wydajności operacji  
 Liczniki wydajności operacji są dostępne pod obiektem wydajności `ServiceModelOperation 4.0.0.0` podczas wyświetlania z monitorem wydajności. Każda operacja ma pojedyncze wystąpienie. Oznacza to, że jeśli dany kontrakt zawiera 10 operacji, do tego kontraktu są skojarzone 10 wystąpień liczników operacji. Wystąpienia obiektów są nazwane przy użyciu następującego wzorca:  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 Ten licznik umożliwia pomiar sposobu użycia wywołania oraz sposobu wykonywania operacji.  
  
 Gdy liczniki są widoczne w wielu zakresach, dane zbierane z wyższego zakresu są agregowane przy użyciu danych z niższych zakresów. Na przykład `Calls` w punkcie końcowym reprezentuje sumę wszystkich wywołań operacji w punkcie końcowym; `Calls` w ramach usługi reprezentuje sumę wszystkich wywołań wszystkich punktów końcowych w ramach usługi.  
  
> [!NOTE]
> Jeśli na kontrakcie istnieją zduplikowane nazwy operacji, tylko jeden z nich jest odbierany dla obu operacji.  
  
## <a name="programming-the-wcf-performance-counters"></a>Programowanie liczników wydajności programu WCF  

Kilka plików jest zainstalowanych w folderze instalacyjnym zestawu SDK, dzięki czemu można programowo uzyskać dostęp do liczników wydajności programu WCF. Te pliki są wymienione w następujący sposób:
  
- *@no__t -1ServiceModelEndpointPerfCounters. VRG*
- *@no__t -1ServiceModelOperationPerfCounters. VRG*
- *@no__t -1ServiceModelServicePerfCounters. VRG*  
- *@no__t -1SMSvcHostPerfCounters. VRG*
- *@no__t -1TransactionBridgePerfCounters. VRG*
  
Aby uzyskać więcej informacji na temat programistycznego uzyskiwania dostępu do liczników, zobacz [Architektura programowania liczników wydajności](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90)).
  
## <a name="see-also"></a>Zobacz także

- [Administracja i diagnostyka](../index.md)
