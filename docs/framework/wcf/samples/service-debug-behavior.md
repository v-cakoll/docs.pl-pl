---
title: Zachowanie debugowania usług
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 6a0a1c5d9f9741da978c633d35ea1e39664bed5b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716305"
---
# <a name="service-debug-behavior"></a>Zachowanie debugowania usług

Ten przykład pokazuje, jak można skonfigurować ustawienia zachowania debugowania usługi. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje kontrakt usługi `ICalculator`. Ten przykład jawnie definiuje zachowanie debugowania usługi w pliku konfiguracji. Można go również wykonać bezwzględnie w kodzie.

W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Plik Web. config dla serwera definiuje zachowanie debugowania usługi, aby włączyć stronę pomocy i obsługę wyjątków, jak pokazano w poniższym przykładzie.

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

[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) to element konfiguracji, który umożliwia zmianę właściwości zachowania debugowania usługi. Użytkownik może zmodyfikować to zachowanie, aby osiągnąć następujące czynności:

- Dzięki temu usługa zwróci wyjątek, który jest generowany przez kod aplikacji, nawet jeśli wyjątek nie został zadeklarowany przy użyciu <xref:System.ServiceModel.FaultContractAttribute>. Jest to wykonywane przez ustawienie `includeExceptionDetailInFaults` `true`. To ustawienie jest przydatne w przypadku debugowania, gdy serwer zgłasza nieoczekiwany wyjątek.

  > [!IMPORTANT]
  > Włączenie tego ustawienia w środowisku produkcyjnym nie jest bezpieczne. Nieoczekiwany wyjątek serwera może mieć pewne informacje, które nie są przeznaczone dla klienta i dlatego ustawienie `includeExceptionDetailsInFaults` do `true` może spowodować przeciek informacji.

- [\<serviceDebug](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) umożliwia użytkownikowi włączenie lub wyłączenie strony pomocy. Każda usługa może opcjonalnie uwidocznić stronę pomocy, która zawiera informacje o usłudze, w tym punkt końcowy do pobrania WSDL dla usługi. Można to włączyć, ustawiając `httpHelpPageEnabled` `true`. Dzięki temu strona pomocy ma zostać zwrócona do żądania GET na adres podstawowy usługi. Możesz zmienić ten adres, ustawiając inny `httpHelpPageUrl`atrybutu. Można to zabezpieczyć przy użyciu protokołu HTTPS zamiast protokołu HTTP. Można to zrobić, ustawiając `httpsHelpPageEnabled` i `httpsHelpPageUrl`.

Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Pierwsze trzy operacje (Dodaj, Odejmij i pomnóż) muszą się powieść. Ostatnia operacja ("dzielenie") kończy się niepowodzeniem z wyjątkiem dzielenia przez zero.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
