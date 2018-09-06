---
title: Zachowanie debugowania usług
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: b87911426b6d4edf8a6f9b0172f4872fac7b9b6f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858889"
---
# <a name="service-debug-behavior"></a>Zachowanie debugowania usług
Niniejszy przykład pokazuje, jak można skonfigurować ustawienia zachowanie debugowania usług. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi. W tym przykładzie jawnie definiuje zachowanie debugowania usług w pliku konfiguracji. Ponadto możesz obowiązkowo w kodzie.  
  
 W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Plik Web.config dla serwera definiuje zachowanie debugowania usług, aby włączyć stronę pomocy i obsługi wyjątków, jak pokazano w następującym przykładzie.  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) jest elementem konfiguracji, który umożliwia zmianę właściwości zachowanie debugowania usług. Użytkownik może modyfikować tego zachowania do osiągnięcia następujących czynności:  
  
-   Dzięki temu zwracanej każdy wyjątek, który jest zgłaszany przez kod aplikacji, nawet jeśli wyjątek nie jest zadeklarowany za pomocą usługi <xref:System.ServiceModel.FaultContractAttribute>. Odbywa się przez ustawienie `includeExceptionDetailInFaults` do `true`. To ustawienie jest przydatne podczas debugowania przypadków, gdy serwer jest zgłaszanie nieoczekiwany wyjątek.  
  
    > [!IMPORTANT]
    >  Nie jest bezpieczne, aby włączyć to ustawienie w środowisku produkcyjnym. Serwer nieoczekiwany wyjątek może mieć pewne informacje, które nie są przeznaczone dla klienta i dlatego ustawienie `includeExceptionDetailsInFaults` do `true` może prowadzić do przecieków informacji.  
  
-   [ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) również pozwala użytkownikowi na włączanie lub wyłączanie strony pomocy. Każda usługa Opcjonalnie można ujawnić stronę pomocy, który zawiera informacje dotyczące usługi, w tym punkt końcowy, aby uzyskać WSDL usługi. To może być włączona `httpHelpPageEnabled` do `true`. Dzięki temu strony pomocy do zwrócenia na żądanie GET do podstawowego adresu usługi. Ten adres można zmienić przez ustawienie innego atrybutu `httpHelpPageUrl`. Umożliwia to bezpieczne przy użyciu protokołu HTTPS zamiast protokołu HTTP. Można to zrobić, ustawiając `httpsHelpPageEnabled` i `httpsHelpPageUrl`.  
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Pierwsze trzy operacje (dodawania, odejmowania i mnożenia) musi zakończyć się sukcesem. Ostatnia operacja ("dzielenie") kończy się niepowodzeniem z dzielenia przez zero wyjątek.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a>Zobacz też
