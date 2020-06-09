---
title: Weryfikacja zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 70408976469b1cbcf9c4679bd91d81872ec74ae1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599974"
---
# <a name="security-validation"></a>Weryfikacja zabezpieczeń
W tym przykładzie pokazano, jak za pomocą niestandardowego zachowania sprawdzić poprawność usług na komputerze, aby upewnić się, że spełniają one określone kryteria. W tym przykładzie usługi są weryfikowane przez zachowanie niestandardowe przez skanowanie poszczególnych punktów końcowych usługi i sprawdzanie, czy zawierają one bezpieczne elementy powiązania. Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="endpoint-validation-custom-behavior"></a>Niestandardowe zachowanie walidacji punktu końcowego  
 Dodając kod użytkownika do `Validate` metody zawartej w <xref:System.ServiceModel.Description.IServiceBehavior> interfejsie, do usługi lub punktu końcowego można przymieścić niestandardowe zachowanie w celu wykonania akcji zdefiniowanych przez użytkownika. Poniższy kod służy do zapętlenia między punktami końcowymi zawartymi w usłudze, które przeszukują kolekcje powiązań dla bezpiecznych powiązań.  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 Dodanie poniższego kodu do pliku Web. config dodaje `serviceValidate` rozszerzenie zachowania dla usługi do rozpoznania.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>
    ...
</system.serviceModel>
```  
  
 Po dodaniu rozszerzenia zachowania do usługi można teraz dodać `endpointValidate` zachowanie do listy zachowań w pliku Web. config i w ten sposób do usługi.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 Zachowania i ich rozszerzenia, które są dodawane do pliku Web. config, mają zastosowanie do poszczególnych usług, natomiast w przypadku dodania do pliku Machine. config należy zastosować zachowanie dla każdej usługi aktywnej na komputerze.  
  
> [!NOTE]
> Podczas dodawania zachowania do wszystkich usług zaleca się wykonanie kopii zapasowej pliku Machine. config przed wprowadzeniem jakichkolwiek zmian.  
  
 Teraz uruchom klienta dostarczonego w katalogu client\bin tego przykładu. Wystąpił wyjątek z następującym komunikatem: "nie można aktywować żądanej usługi" http://localhost/servicemodelsamples/service.svc ". Jest to oczekiwane, ponieważ punkt końcowy jest traktowany jako niezabezpieczony przez sprawdzanie poprawności zachowania punktu końcowego i uniemożliwia uruchomienie usługi. Zachowanie generuje również wyjątek wewnętrzny, który opisuje, który punkt końcowy jest niezabezpieczony i zapisuje komunikat do Podgląd zdarzeń systemu w ramach źródła "System. ServiceModel 4.0.0.0" i kategorii "WebHost". Możliwe jest również włączenie śledzenia usługi w tym przykładzie. Dzięki temu użytkownik może wyświetlić wyjątki zgłoszone przez sprawdzanie poprawności przez punkt końcowy, otwierając wynikowe ślady usługi za pomocą narzędzia Podgląd śledzenia usługi.  
  
### <a name="view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Wyświetlanie komunikatów o wyjątkach weryfikacji punktu końcowego zakończonych niepowodzeniem w Podgląd zdarzeń  
  
1. Kliknij menu **Start** i wybierz polecenie **Uruchom...**.  
  
2. Wpisz `eventvwr` , a następnie kliknij przycisk **OK**.  
  
3. W oknie Podgląd zdarzeń kliknij pozycję **aplikacja**.  
  
4. Kliknij dwukrotnie ostatnio dodane zdarzenie "System. ServiceModel 4.0.0.0" w kategorii "WebHost" w oknie **aplikacji** , aby wyświetlić komunikaty o niezabezpieczonym punkcie końcowym.  
  
## <a name="set-up-build-and-run-the-sample"></a>Konfigurowanie, kompilowanie i uruchamianie przykładu  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Zobacz też

- [Przykłady monitorowania oprogramowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
