---
title: Hierarchiczny model konfiguracji
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 233a8d4ba36835ab26e0c4a8cd044cf60d497a0b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="hierarchical-configuration-model"></a>Hierarchiczny model konfiguracji
W tym przykładzie pokazano, jak wdrożyć hierarchia pliki konfiguracji dla usług. Pokazuje też, jak powiązania zachowania usługi i zachowania punktu końcowego są dziedziczone z wyższego poziomu w hierarchii.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Jedną z funkcji opracowanych dla usług WCF w [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] ulepszenia w hierarchiczny model konfiguracji. Przykładem modelu hierarchiczna konfiguracji może być zdefiniowana w pliku Machine.config -> Rootweb.config -> pliku Web.config. W [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], tych powiązań i zachowania, które są zdefiniowane w górnym poziomów w hierarchii konfiguracji są dodawane do usługi z jawnym konfiguracji. W tym przykładzie pokazano, jak możliwe jest uproszczenie konfiguracji usługi przez jednostki uzależnionej w elementach konfiguracji zdefiniowanych w komputerze lub na poziomie aplikacji.  
  
 W tym przykładzie składa się z dziewięciu usług, określonych w trzech poziomach hierarchii. `Service1` znajduje się w folderze głównym. `Service2` i `Service3` dziedziczą domyślne elementy z `Service1`. `Service4`, `Service5`, `Service6` i `Service7` są definiowane na trzeci poziom hierarchii dziedziczenia domyślne elementy z `Service3`. Na koniec `Service10` i `Service11` są czwartego poziomu hierarchii.  
  
 Wszystkie usługi wdrożenia `IDesc` kontraktu. Poniżej znajduje się definicja `IDesc` interfejs, który zawiera metody ujawnione w tym interfejsie. `IDesc` Interfejsu jest zdefiniowany w Service1.cs.  
  
```  
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
  
 Implementacja metody te przez usługi jest prosta. `ListEndpoints` wykonuje iterację wszystkie punkty końcowe usługi i zwraca listę wszystkich punktów końcowych, które usługa ma. `ListServiceBehaviors` wykonuje iterację wszystkie zachowania dodane do usługi i zwraca listę wszystkich zachowań usługi związane z usługą. `ListEndpointBehaviors` działa w podobny sposób jak `ListServiceBehaviors`, ale zamiast tego zwraca listę zachowania punktu końcowego.  
  
 Ta implementacja umożliwia jest ujawniany przez klienta, aby wiedzieć, jak wiele punktów końcowych usługi i które zachowania usługi i zachowania punktu końcowego zostały dodane do usługi. Klient, który został zaimplementowany jako część próbki dodaje odwołania do usługi do wszystkich usług w rozwiązaniu i zawiera te elementy dla każdego z nich usługi.  
  
## <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
#### <a name="to-run-the-client"></a>Uruchom klienta  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik ConfigHierarchicalModel.sln.  
  
2.  Projekt klienta nie już ustawiono jako projekt rozruchu, wykonaj następujące kroki.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz **właściwości**.  
  
    2.  W **wspólne właściwości**, wybierz pozycję **projekt startowy**, a następnie kliknij przycisk **jednego projektu startowego**.  
  
    3.  Z **jednego projektu startowego** listy rozwijanej, wybierz pozycję **klienta**.  
  
    4.  Kliknij przycisk **OK** aby zamknąć okno dialogowe.  
  
3.  Aby samodzielnie tworzyć przykładowy, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
4.  Aby uruchomić klienta, naciśnij kombinację klawiszy Ctrl + F5.  
  
> [!NOTE]
>  Jeśli te kroki nie działają, następnie upewnij się, że środowiska nie został prawidłowo skonfigurowany, wykonując następujące kroki.  
>   
>  1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
> 3.  Aby uruchomić przykład w jednym lub wielu konfiguracji komputera, postępuj zgodnie z instrukcjami [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zarządzania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193960)
