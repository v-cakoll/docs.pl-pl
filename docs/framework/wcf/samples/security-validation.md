---
title: Walidacja zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
author: BrucePerlerMS
ms.openlocfilehash: 4b80457fb551c2ee99f910710c5f30fa59c53a01
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48776377"
---
# <a name="security-validation"></a>Walidacja zabezpieczeń
W tym przykładzie pokazano, jak umożliwia zachowanie niestandardowe sprawdzanie poprawności usługi na komputerze, aby upewnić się, że spełniają określone kryteria. W tym przykładzie usług są weryfikowane przez niestandardowe zachowanie przez skanowanie za pomocą każdego punktu końcowego w usłudze i sprawdzanie, czy zawierają one elementy bezpiecznego powiązania. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
## <a name="endpoint-validation-custom-behavior"></a>Niestandardowe zachowanie weryfikacji punktu końcowego  
 Dodając kod użytkownika do `Validate` metoda zawarte w <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu, niestandardowe zachowanie można nadać usługi lub punktu końcowego do wykonywania akcji zdefiniowane przez użytkownika. Poniższy kod umożliwia jednoczesne każdy punkt końcowy znajdujących się w usłudze wyszukiwania za pomocą ich kolekcji powiązania dla bezpiecznych powiązań.  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
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
  
 Dodając następujący kod do pliku Web.config dodaje `serviceValidate` rozszerzenia zachowania dla usługi, rozpoznawał.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Po dodaniu rozszerzenia zachowania do usługi jest teraz można dodać `endpointValidate` zachowanie na liście zachowań w pliku Web.config, a w związku z usługą.  
  
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
  
 Zachowania i ich rozszerzeń, które są dodawane do pliku Web.config, zachowanie mają zastosowanie do poszczególnych usług, podczas gdy po dodaniu do pliku Machine.config zastosować zachowanie do każdej usługi, które są aktywne na komputerze.  
  
> [!NOTE]
>  Podczas dodawania zachowanie do wszystkich usług, zalecane jest aby utworzyć kopię zapasową pliku Machine.config przed wprowadzeniem zmiany.  
  
 Teraz z klientem w katalogu client\bin tego przykładu. Wyjątek występuje z następującym komunikatem: "żądanej usługi"http://localhost/servicemodelsamples/service.svc"nie można aktywować." Oczekuje się, ponieważ punkt końcowy jest uznawana za niebezpieczne przez punkt końcowy, sprawdzanie poprawności zachowanie i uniemożliwia uruchomienie usługi. Zachowanie zgłasza również wyjątek wewnętrzny, opisujący którym punktem końcowym jest niebezpieczne i zapisuje komunikat do systemu Podglądu zdarzeń w źródle "System.ServiceModel 4.0.0.0" oraz kategorii "Hostem sieci Web". Użytkownik może również włączyć śledzenie usługi w tym przykładzie. Dzięki temu można wyświetlić wyjątki generowane przez działanie sprawdzania poprawności punktu końcowego, otwierając wynikowy śladów usługi za pomocą narzędzia przeglądarki danych śledzenia usługi.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Aby wyświetlić nie powiodło się komunikaty o wyjątkach weryfikacji punktu końcowego w Podglądzie zdarzeń  
  
1.  Kliknij przycisk **Start** menu, a następnie wybierz **uruchamianie...** .  
  
2.  Typ `eventvwr` i kliknij przycisk **OK**.  
  
3.  W oknie podglądu zdarzeń kliknij **aplikacji**.  
  
4.  Kliknij dwukrotnie zdarzenie ostatnio dodane "System.ServiceModel 4.0.0.0" w kategorii "WebHost" w **aplikacji** okna, aby wyświetlić komunikaty niezabezpieczone punktu końcowego.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
