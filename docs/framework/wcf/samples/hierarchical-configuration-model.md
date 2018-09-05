---
title: Hierarchiczny model konfiguracji
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 8ca9b01eb022e2e2ab940866a6230e8227ceb2dc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499344"
---
# <a name="hierarchical-configuration-model"></a>Hierarchiczny model konfiguracji
Ten przykład demonstruje sposób implementacji hierarchii plików konfiguracji usługi. Pokazuje również, jak powiązania, zachowań usługi i zachowań punktu końcowego są dziedziczone z poziomu w hierarchii.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Jedna z funkcji opracowanych dla usług WCF w [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] jest poprawę hierarchiczny model konfiguracji. Przykładem hierarchiczny model konfiguracji jest zdefiniowana w pliku Machine.config -> Rootweb.config -> pliku Web.config. W [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], te powiązania i zachowań, które są zdefiniowane w wyższe poziomy w hierarchii konfiguracji, które są dodawane do usługi bez jawnej konfiguracji. Ten przykład pokazuje, jak można uproszczenie konfiguracji usługi, opierając się na elementy konfiguracji, zdefiniowanych na komputerze lub na poziomie aplikacji.  
  
 W tym przykładzie składa się z dziewięciu usługi, zdefiniowane w trzech poziomów hierarchii. `Service1` jest w katalogu głównym. `Service2` i `Service3` dziedziczą domyślne elementy z `Service1`. `Service4`, `Service5`, `Service6` i `Service7` są definiowane na trzeci poziom w hierarchii dziedziczenia domyślne elementy z `Service3`. Na koniec `Service10` i `Service11` znajdują się na czwartego poziomu w hierarchii.  
  
 Wszystkie usługi implementują `IDesc` kontraktu. Poniżej przedstawiono definicję `IDesc` interfejs, który zawiera metody, dostępne w tym interfejsie. `IDesc` Interfejsu jest zdefiniowany w plikach Service1.cs.  
  
```csharp  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 Implementacja metody te przez usługi jest bardzo proste. `ListEndpoints` wykonuje iterację przez wszystkie punkty końcowe usługi i zwraca listę wszystkich punktów końcowych, które usługa ma. `ListServiceBehaviors` wykonuje iterację przez wszystkie zachowania, które są dodawane do usługi i zwraca listę wszystkich zachowań usługi związane z usługą. `ListEndpointBehaviors` zachowuje się w podobny sposób jak `ListServiceBehaviors`, ale zamiast tego zwraca listę zachowań punktu końcowego.  
  
 Ta implementacja umożliwia, jest ujawniany przez klienta, aby wiedzieć, ile punktów końcowych usługi i które zachowania usług i zachowań punktu końcowego zostały dodane do usługi. Klient, który został zaimplementowany jako części przykładu dodaje odwołanie usługi do wszystkich usług w rozwiązaniu i pokazuje te elementy, dla każdej z nich usługi.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
#### <a name="to-run-the-client"></a>Aby uruchomić klienta  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik ConfigHierarchicalModel.sln.  
  
2.  Projekt klienta nie już skonfigurowano jako projekt startowy, wykonaj następujące kroki.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz **właściwości**.  
  
    2.  W **wspólne właściwości**, wybierz opcję **projekt startowy**, a następnie kliknij przycisk **pojedynczy projekt startowy**.  
  
    3.  Z **pojedynczy projekt startowy** listę rozwijaną, wybierz opcję **klienta**.  
  
    4.  Kliknij przycisk **OK** aby zamknąć okno dialogowe.  
  
3.  Aby stworzyć próbkę, naciśnij klawisze CTRL + SHIFT + B.  
  
4.  Aby uruchomić klienta, naciśnij kombinację klawiszy Ctrl + F5.  
  
> [!NOTE]
>  Jeśli te kroki nie działa, upewnij się, czy środowiska prawidłowo skonfigurowano, wykonując następujące czynności:  
>   
> 1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](building-the-samples.md).  
> 3.  Do uruchomienia przykładu w jednej lub wielu konfiguracji komputera, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładami dotyczącymi zarządzania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193960)
